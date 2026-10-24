Stamp: claude-opus-5-5 (Claude Code, effort xhigh, plan mode, read-only), main 39bfb717, 2026-10-24 Sat

**A. Verdict**
Yes. Nothing is left to build for Oct 27. What remains is landing the preflight, one merge batch, re-checks and docs. The thing most likely to spoil CP3 is the night running on state nobody re-checked after the last change. The biggest case is the Anthropic credit balance: a low balance stopped CP2 on Oct 22, and neither the box nor the preflight can read it.

**B. Priorities**
Every PR gets a v1 plan (3 versions at most), at most 2 review rounds plus 1 short extra, and one defect.

| # | Task · defect · Done when | Owner | Mark | Machine | Time | Cost | Slot | Depends |
|---|---|---|---|---|---|---|---|---|
| 1 | **Land the preflight** as `scripts/cp3_preflight.py` plus `scripts/test_cp3_preflight.py`. Defect: the CP3 readiness check is an unreviewed box file, copied by hand to each machine. Port v2 unchanged. Tests come first, on a synthetic home: 5,5,20 gives a WARN at $20; $5 only FAILs; a wrong head, `CLAUDE_OFFLINE=1` or a held lock FAILs; $0.15/draft FAILs and prints `tell_proxy`. Subprocess calls mocked, pathlib, offline. Plan approved by Grok Bot; Opus r1; Sonnet r2 if needed. Done when: Claude APPROVE and PC PASS at the head. If it misses the batch, the night uses the box v2 copy. | Engineer | NEEDS-WINDOW | box→PC | 3 h + PC run | $0 | Sat day; PC run Sat night | — |
| 2 | **Send the F asks** so the answers land before the batch. Done when: answers are recorded, or the defaults apply at 7 PM Sun. | Proxy | NEEDS-USER | — | 15 min | $0 | Sat day | — |
| 3 | **Tests at 39bfb71** (no post-merge run is recorded there): the PC runner and a Mac separate-copy run, plus the one `test_transfer` command in PLAN-ISSUE48 §2, which turns #48's guess into a fact. Done when: PC 51+2, 0 new; every Mac detector suite passes. | Engineer | UNATTENDED-OK | PC, Mac | 1 h | $0 | Sat night | — |
| 4 | **Two vault-umbrella docs PRs** (nightly; no Mac restart). (a) `Gameplans/2026-10-24-CP3-FREEZE-AND-RUNBOOK.md` plus this task set, with three runbook lines added: run the PC preflight in the same shell that then runs `render_picks` (a reused `CLAUDE_OFFLINE=1` shell blocked every call in a CP2 session on Oct 22); an exit 4 that mentions "credit balance" means stop and tell the Proxy; the preflight's path once task 1 merges. (b) Open-Items: OI-064 done (#166 `44d5f15`); OI-012, OI-058 (6 green, 4 refused) and OI-059 updated; OI-063's OBS half closed (Claude agrees; the Proxy confirms). | Proxy | UNATTENDED-OK | vault | 1 h | $0 | Sat night | — |
| 5 | **Weekend reading list.** Until the auto-clip-system catch-up merges, every Claude manifest lists after the brief: USER-CONTEXT-SAT, WINDOW-STATE, T1-PROGRESS-last80, the runbook, PREFLIGHT-PC-CAP-NOTE and this task set, with the line "Status, Current-Holds and the brief are stale since 10:41 PM Oct 23". | Proxy | UNATTENDED-OK | box | 5 min | $0 | Sat day | — |
| 6 | **Current-Holds watcher line**, the only docs piece that goes early: it is the hold text every session obeys. Defect: it says the watcher stays unloaded until the Oct 26 check, but it has run detect-only since 12:38 AM Oct 24. Sonnet check. It joins the batch only with the user's OK (F3); otherwise it goes in the catch-up. | Engineer | NEEDS-USER | vault | 20 min | $0 | Sun day | 2 |
| 7 | **The #49 half of OI-012** (due Oct 26). Check whether the "weak second half" of `test_overflow` is still real at 39bfb71 (#54 rewrote that test). If real: one test-only PR for the defect the check names, Sonnet, PC PASS, then the batch. If moot: note it in OI-012. | Engineer | NEEDS-WINDOW | box→PC | 1-2 h | $0 | Sat night | — |
| 8 | **ffmpeg-python pin**, the one parked idea that fits as BACKGROUND. Defect: `detector/requirements-mac-detector.txt:1` pins 0.2.1, which PyPI lacks, so a fresh Mac install fails. Test first: each pin in that file matches `requirements.lock`. In the batch only if green by Sun 5 PM. | Engineer | NEEDS-WINDOW | box→PC | 1 h | $0 | Sun day | — |
| 9 | **auto-clip-system docs catch-up draft**: Status, the brief, Known-Problems (the `.env` duplicate-line trap; the 4 refused T2 streams), and the Daily notes for Oct 25-27 as held drafts. It merges after the cp3_run. | Proxy | NEEDS-WINDOW | vault | 1 h | $0 | Sun day | — |
| 10 | **Merge batch**, Sun 7-9 PM ET, in this order: 1 → 7 → 8 → 6 → the Oct 24 Daily note. Each is squashed with `--match-head-commit` at the head that passed on the PC. Then fast-forward pull the Mac and the PC. The Proxy and Claude confirm. | Engineer | NEEDS-WINDOW | Mac, PC | 30 min | $0 | Sun night | 1, 6-8 |
| 11 | **Post-batch check.** It replaces the Oct 26 ~6 PM routine and needs the Proxy's confirmation. Both HEADs on the final main. `--status` shows floor 2026-10-27 with Oct 23 held. The watcher runs detect-only (re-bootstrap only if it didn't come back). No new "Twitch status check failed" lines. Chat is loaded and its file is fresh. The preflight with `--expect-head <final>` shows 0 FAIL on both machines. Then the PC runner and a Mac separate-copy run overnight. | Engineer | NEEDS-WINDOW | Mac, PC | 45 min + runs | $0 | Sun night | 10 |
| 12 | **Monday:** no merges, nothing heavy. If the user streams, read `--status` after OBS closes; it should show "held 2". | Engineer | NEEDS-WINDOW | Mac | 5 min | $0 | Mon | 11 |
| 13 | **The CP3 night.** Before the stream: the preflight on both machines, same SHA; on the PC, in the render shell. After OBS closes: runbook steps 1-6. Done when: cp3_run reports "Cut N clip(s), 0 failed", every audit exits 0, `render_picks` exits 0 and writes its checklist, and both ledgers are under the caps. | Engineer | NEEDS-WINDOW | Mac, PC | the night | ~$0.20 Mac + ~$0.50 PC, approved (C, D) | Oct 27 | 11, F5 |
| 14 | **Item 17, plan v1 only** (test-runner heartbeat; plumbing, not frozen). Built after the cp3_run. Optional, only with the Max meter under 70%. | Engineer | UNATTENDED-OK | box | 1 h | $0 | Sun night | — |

Not in this task set, flagged for the Proxy: OI-014, the first independent Claude audit, due Sun Oct 25 (the 11 AM dreaming run, PX-001).

**C. Mac service restarts, batched**
- **What restarts the Mac:**
  - Task 10. Each squash merge plus the pull restarts the watcher, the chat daemon (which writes a gap row) and the feeder.
  - Task 11's re-bootstrap, only if the watcher doesn't come back.
- **What doesn't:** umbrella merges, box files, test runs in throwaway copies, the preflight and `--status`.
- **The batch:** one, Sun Oct 25 7-9 PM ET. Rerun the preflight right after it (task 11) and again before the Oct 27 stream.
- **Fallback:** if task 1 misses the batch, it alone may merge Mon before 6 PM, only with OBS and the game closed, followed by a preflight rerun.

**D. The Oct 27 merge hold**
- **No auto-clip-system merges from 9 PM Sun** until `cp3_run --send` finishes and that night's clips are on the PC. That covers task 9, the Daily notes for Oct 25-27, anything that missed the batch, item 17, and all code.
- **After that:** plumbing may merge outside streams, never during `render_picks`. `editor/*` and the ranker kinds stay frozen.
- **vault-umbrella keeps merging nightly:** Open-Items, Roadmap, Daily, Gameplans.
- **Last merge window:** Sun Oct 25, 7:00-9:00 PM ET. Hard stop Mon Oct 26, 6:00 PM ET, for the task 1 fallback only.

**E. Waits until CP3 is scored**
- T3, T4, T5. Chat C1m, C2, B, E and R (the download is done; the converter and alignment wait).
- Items 19, 20 and 22a sit inside `editor/`. Land none of them before CP3: none moves the CP3 mark, none can get a paid render test before Oct 27, and a defect found on the night becomes a break-fix that restarts the count. Items 21 and 27 are plan-first.
- #161 nit 3, #153, the hook/description fix, no-idle 5/7/6/O1, and the detector-only runner mode (#48 bullet 2, as its own row).
- The over-reservation fix, unless the preflight rerun after stream 1 shows more than $0.132 per draft. In that case, tell the Proxy before stream 2.
- The override for the 4 refused T2 streams.

**F. Asks for the user**
1. **Ear check** of the 5 Mac cuts (EAR-CHECK-T2-CUTS.md): OK, wrong phrase, or bad edges. Why: it's the only human check on the cutter before T3 and T4 build on it. No answer: CP3 is unaffected.
2. **#48 closing comment** (PLAN-ISSUE48 §6, plus task 3's result): OK to post? Why: it's public. No answer: the issue stays open and OI-012 is re-dated.
3. **Early watcher reload:** confirm the Current-Holds change. Why: it's a [user] hold. No answer: the watcher stays loaded (the floor holds Oct 21-26 recordings anyway), and the line waits for the catch-up.
4. **`editor/.env`:** delete the two `LLM_MAX_USD_PER_MONTH=5` lines and keep the `=20` line (a user edit). Why: any reader that takes the first line sees $5, and the guard would refuse the first CP3 stream. No answer: the editor still reads $20, and the preflight keeps printing the WARN. FYI: the preflight only reads the cap and model lines.
5. **API credit balance:** does it cover about $3 of CP3 spend, on both keys, until the Max credit links (~Oct 28)? Why: a low balance stopped CP2 on Oct 22. No answer: the night runs; if billing stops it, the Engineer tells the Proxy and reruns after a top-up (the Mac replays its ranker cache for $0).
6. **Stream nights, Oct 26-31?** Why: they set the CP3 nights and the end of the hold. No answer: Monday counts as live, and the first stream on or after Oct 27 is CP3 night 1.

**G. Cost and risk**
- **Max (notional):** 1 Opus call ($1-3) and about 7 Sonnet checks ($1.4-4.2), roughly $2.4-7.2 in total. Task 14 adds one more Opus call ($1-3). Flag to the Proxy past 85%.
- **API:** $0 Saturday through Monday.
  - **Oct 27:** the Mac goes from $4.49 to about $4.69 of $10 (guard check $5.49, PASS); the PC from $4.21 to about $4.71 of $20 (guard check $5.21, PASS).
  - **Three October streams:** about $5.09 on the Mac and $5.71 on the PC.
- **Risks:**
  1. A defect on the first real run of the chain that lands in `editor/*` or the ranker kinds is a break-fix that restarts the CP3 count.
  2. The credit balance (F5).

**H. Unknown / not read:** all Mac and PC state since 12:57 AM Oct 24, whether the Mac pulls main by itself, the stream schedule from Monday, the Max meter, the API credit balance, and Long-form's weekend use of the machines.
