> Copy of `PR-PLAN-RENDER-NO-IDLE-v3.md` (box handoffs), added 2026-10-22. Plan only; build waits for the user's OK. See [[Roadmap]]. Text below is unchanged.

# PR plan v3: render with no idle gaps and no silent 0/6

Oct 22, 2026, ~10:05 PM ET. Plan only: no code, no PR, nothing touched on the PC or Mac.
Base: fresh clone of `zazabanx/auto-clip-system`, main `506bf8b`. Every file:line below was checked there.
Applies all 9 required changes, decisions 1-8, ship order, sizing, factual fixes and Missing items from Opus r1.
v3 applies Opus r2 (APPROVE WITH CHANGES): PR 6 waits only on puller-ledger entries; PR count 8 accepted (decision 1 resolved); PR 3a saves `$code` and exits after `finally`, ships first; PR 5 defaults to a run-once task and `run()` wraps `run_session()`; O1 alerts on `partial`, not the sweep wait.

**House rules:** one defect per PR; draft PRs; Claude review plus a PC test (`scripts\run_tests_pc.ps1`) before merge; never delete VODs or clips; never post; the paid key only inside the pipeline. The blind surfaces are the console, `render-status.json` and alerts. The key log is not blind.

**Order:** 3a → 1 → 2 → 3 → 4 → 5 → 7 → 6 → O1. PR 3a ships first: it only touches `scripts/` and is not in the serial `run()` chain. PRs 1-4 are serial (all edit `run()`/`main()`); **7 before 6**. None change editor output; only `draft_commit` differs.

## PR 1: guard pauses reach the key log
- **Defect:** `RenderGuard._say()` logs at INFO (`render_guard.py:688-693`); `main()` sets WARNING (`render_picks.py:807`), so "Render paused" is dropped.
- **Approach:** set logger `"render_guard"` to INFO in `main()`. Both module copies use that name (`render_guard.py:45`).
- **Test:** a stub pause lands in the key log at default level, not on the console.
- **Done when:** a PC run with a forced GPU block logs the pause.
- **Risks:** none to output. **Files:** `editor/render_picks.py`, `editor/test_render_picks.py`.

## PR 2: stop the session on a credit-balance error
- **Defect:** a billing failure returns `status: failed`, `render_one()` returns None (`render_picks.py:540-545`) and `run()` moves on (`:741-743`). Hooks and posted copy swallow billing errors and fall back (`content_generator.py:13646, 13728`), so the draft is added and can bias a rank-1 pair.
- **Approach:** new `ClaudeBillingError`, raised from those two branches and passed through `process_local_clip` like `CostGuardError`. `render_one()` also checks a failed result's `error`; nit: `is_billing_error()` (`:13189`) expects an exception but gets a string, so wrap it. `run()` stops before `add_draft`, says "Claude credit balance is empty" (distinct from the cap text), exit 4.
- **Test:** billing on draft 1 by return, by raise, and from the hook step: exit 4, draft 2 never called, nothing added.
- **Done when:** PC tests pass. **Risks:** an `except Exception` on the way out; the hook test runs end to end.
- **Files:** `editor/content_generator.py`, `editor/windows_editor_skeleton.py` (re-raise), `editor/render_picks.py`, tests.

## PR 3: refuse real renders when CLAUDE_OFFLINE=1
- **Defect:** nothing checks it; tonight ended as "did not render" lines and exit 1.
- **Approach:** in `main()` after `_load_editor_env()` (`:801`), exit 3 with a plain message. `--dry-run` passes.
- **Test:** offline plus real factory exits 3 before the lock; dry run passes; stub tests still run offline.
- **Done when:** a PC run in an offline shell refuses at once. **Risks:** none. **Files:** `editor/render_picks.py`, tests.

## PR 3a (new, tiny): test runner leaks env into the caller's shell
- **Defect:** `scripts/run_tests_pc.ps1:63-65` sets `AUTOCLIP_TEST_PYTHON`, `CLAUDE_OFFLINE`, `PYTHONUTF8` in the caller's session (line 64 is the likely source of tonight's flag).
- **Verified:** Python already sets the first two for children (`run_tests_pc.py:161-163, 614`) and passes `AUTOCLIP_TEST_PYTHON` to the copy (`:567`). But `PYTHONUTF8` only affects the outer interpreter if set before it starts, so removal is riskier.
- **Approach:** save, then set and run in `try`, storing `$code = $LASTEXITCODE` there (no `exit` inside `try`); `finally` restores each variable or removes it if it was unset; then `exit $code`. Alternative: pass `-X utf8` on line 66 instead of setting `PYTHONUTF8`.
- **Ships first:** touches only `scripts/`, outside the serial `run()` chain.
- **Test:** update `scripts/test_run_tests_pc.py:210-216` to require the restore; on the PC, after a run, `Test-Path env:CLAUDE_OFFLINE` is False.
- **Done when:** that PC check passes. **Risks:** none (exit happens after `finally`).
- **Files:** `scripts/run_tests_pc.ps1`, `scripts/test_run_tests_pc.py`.

## PR 4: cap from editor/.env; shadowed variables printed
- **Defect:** `cost_settings()` reads only `os.environ` (`shared/llm_cost.py:145-154`) and `load_dotenv` never overrides (`review_inbox.py:945`), so session values silently win and a bare `cost_check()` sees the $10 default.
- **Approach:** read `.env` with `dotenv_values` (no `os.environ` change) and track each value's source. Decision 6: **refuse** (exit 3) if a session value loosens `LLM_MAX_USD_PER_MONTH`, `LLM_MAX_USD_PER_RUN` or `LLM_EDITOR_MAX_USD`, or sets a different `LLM_SPEND_PATH`; **warn** if tighter. Print "cap $X (editor/.env | session)", list shadowed `LLM_*`/`RENDER_*` names, and say whether `ANTHROPIC_API_KEY` comes from session or `.env`. Never print values.
- **Test:** `.env` cap 5: session 10 refuses, session 3 warns and applies, other spend path refuses; output holds no values.
- **Done when:** the PC dry run shows cap, source and shadowed names. **Risks:** legit overrides now refuse (intended).
- **Files:** `editor/render_picks.py`, `shared/llm_cost.py`, tests.

## PR 5: `editor/render_nights.py`, nights back to back
- **Defect:** `main()` takes one `--night`; nothing chains nights or outlives the agent's turn.
- **Approach:** `python -m editor.render_nights --nights A,B,C`. No state file, no `--resume`: re-running resumes from each `cp2-key.json`; runner state lives in PR 7's `render-status.json`.
  - **Exit reasons:** `run_session()` returns `(code, reason, added, failed)`; `run()` becomes a thin wrapper over `run_session()` and keeps its int (not the reverse, or the reasons are lost: `run()` returns 0 for both no picks and all done, and 3 for five reasons). Wait: `busy`, `lock_held`, `tasklist_failed` (`:247-248, 676-679, 686-689`). Stop night and alert: `sha_mismatch` (`:693-698`), `key_unreadable` (`:652-656`), `cp2_inside_review` (`:649-651`). `no_picks` (`:657-660`) is `waiting_inputs`, never done. `cost_cap`/`billing` stop everything.
  - **Failing session:** 0 added and ≥1 failure marks the night `failed` and alerts; no re-run until the final sweep.
  - **Robustness:** key log per night (reuse `KeyLog`); `try/except` per session; record `repo_commit()` at start and warn if HEAD moves.
  - **Disk:** ≥40 GB (`RENDER_MIN_FREE_GB`) on each drive holding output, work, Needs_Your_Review and cp2; shown in `--dry-run`; never clean up.
  - **Sleep:** `SetThreadExecutionState(ES_CONTINUOUS|ES_SYSTEM_REQUIRED)` while running (none exists today).
  - **Launch:** default is a run-once scheduled task (console to a blind runner log under `cp2\`), since `Start-Process` from an OpenSSH session likely stays in sshd's job object and dies with the session; tested once on the PC by closing the shell mid-run.
  - **`ops/pull_main.py`** sees only `editor.lock`/`windows_editor_skeleton.py` (`pull_main.py:31-33, 241-243`). Explicit follow-up **F1** (treat a held `machine.lock` as busy); the HEAD warning covers it meanwhile.
- **Test:** stubs: 3 nights in a row; busy then clear; each reason → its action; failing session not retried; a crash in night 1 still runs night 2; HEAD move warns; per-drive disk; sleep call mocked.
- **Done when:** tests pass and the detached run survives closing the shell.
- **Risks:** the detached log must stay blind. **Files:** `editor/render_nights.py`, `editor/render_picks.py`, `editor/test_render_nights.py`, `docs/SETUP.md`.

## PR 7: status file, pause source, alerts (before PR 6)
- **Defect:** no outside view of pauses, stalls or crashes. And `-m editor.render_picks` loads `editor.render_guard` (`render_picks.py:101`) while the editor imports top-level `render_guard` (`windows_editor_skeleton.py:125`; also `ffmpeg_tools.py`, `transcriber.py`). I confirmed in the clone: two modules, two guards.
- **Approach:** `RenderGuard.current_pause()` with its own reason and start time (not `_announced`), read from the **top-level** module. A heartbeat thread rewrites `...\.auto-clip\track1\cp2\render-status.json` every 60 s and on events: `state` (running, paused, waiting_inputs, partial, done, failed, stopped), `reason` (quotes guard or lock line; credit vs cap), `since`, `night`, `drafts_done/left`, `last_draft_at`, `commit`, `heartbeat`. Temp file plus `os.replace`, retried on `PermissionError`. Move `EDIT_PATH_WORDS` from `test_render_picks.py:52` into code and check all text: no path, no `__oldpath`, no editor error text. This fixes the format O1 reads.
- **Test:** a top-level guard pause shows `paused`, in a test importing `editor.render_nights` and plain `render_guard` the way `-m` does; atomic writes; locked-file retry; blind check on every field.
- **Done when:** a PC forced GPU block shows `paused` with the guard line within 60 s.
- **Risks:** `stay_below_normal()` targets the wrong guard (follow-up **F2**). **Files:** `editor/render_guard.py`, `editor/render_nights.py`, `editor/render_picks.py`, tests.

## PR 6: final sweep for late inputs
- **Defect:** only synced clips render. `t1r3.top` is the export's `--top` (`detector/export_picks.py:362`); ranks skip (`:371-383`); a failed cut leaves no sidecar (`:462-468`).
- **Approach (decision 4):** never hold a night. After all nights run once, sweep all nights (the key skips done drafts). Expected per stem = ranks seen, capped by `min(top, 5)` (`MAX_RANK`, `render_picks.py:113`). Wait up to 30 min only in the sweep, and only while the puller ledger has `pending`/`failed`/`needs_review` entries for that night (`editor/puller.py:685`), named in the wait reason; then mark `partial` and alert. A night that is only under the cap renders what it has, with no wait and no alert.
- **Test:** ranks 1,2,4 of top 5 with no ledger entries render at once, no wait, no alert; a late file renders in the sweep; timeout gives `partial` plus puller reason.
- **Done when:** tests pass; PC dry run lists the sweep. **Risks:** a 30-min tail. **Files:** `editor/render_nights.py`, tests.

## Ops task O1 (box)
Every 10 min the box routine reads `render-status.json` over the remote shell. It alerts on done, failed, partial or stopped; on paused or busy for 20 min or more; on `waiting_inputs` only when the state becomes `partial` (so PR 6's 30-min sweep wait raises no false alert); on a heartbeat older than 5 min; on 60 min with no finished draft while running; and when the file can't be read. Each alert quotes `reason`. Vault line in `vault/Pipeline.md`: "Render status poll: box, 10 min, cp2\render-status.json (format: PR 7)."

## Changes from v2 (Opus r2)

| r2 change | Landed |
|---|---|
| PR 6 waits only on puller-ledger pending/failed/needs_review; under-cap night renders, no wait, no alert | PR 6 |
| Count 8 accepted, none merged | Decision 1 |
| `$code = $LASTEXITCODE` in `try`, restore in `finally`, `exit $code`; `-X utf8` alt; ships first | PR 3a, Order |
| Run-once task default; `run()` wraps `run_session()` | PR 5 |
| Alert on `partial`, not sweep wait | O1 |

## Changes from v1

| Required change | Landed |
|---|---|
| 1 PR 6 ranks seen, min(top,5), decision 4, puller reason | PR 6 |
| 2 Exit reasons | PR 5 |
| 3 Failing session = night failed | PR 5 |
| 4 Detached launch, sleep | PR 5 |
| 5 Key log per night, per-session catch, HEAD | PR 5 |
| 6 Billing in hooks/copy | PR 2 |
| 7 `dotenv_values`, decision 6 | PR 4 |
| 8 Top-level guard, `-m` test, alerts, blind, retry | PR 7, O1 |
| 9 No state file/`--resume`; PR 8 → ops | PR 5, O1 |
| Missing 1 env leak / 6 pull_main | PR 3a / F1 |

## Open decisions (defaults in bold)
1. Count: **resolved, 8 repo PRs + O1**. Opus r2 accepts 8 (its "6" was a counting mistake); none merged.
2. PR 3a: **scoped restore** (vs. remove).
3. pull_main: **follow-up F1** (vs. inside PR 5).
4. HEAD moved mid-run: **warn** (vs. stop).
5. Sweep wait: **30 min, once**.
