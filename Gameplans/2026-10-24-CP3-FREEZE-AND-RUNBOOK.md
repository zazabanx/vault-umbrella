# CP3 freeze list, night runbook and readiness preflight (docs only)
Stamp: Auto-clip Engineer (box only), 2026-10-23 ~11:30 PM ET, main 698c04dcf2e325c7cee8a243cf43c8c0f60b7b6b. Source of the wording: GAMEPLAN-2026-10-23-NIGHT.md item 1 (the confirmed plan). Every code fact below was read from the repo at that SHA. The Proxy confirms the list and lands this as docs. Nothing here was run on the Mac or PC.

**Umbrella copy, Oct 24 (Saturday gameplan task 4a):** the box file `CP3-FREEZE-AND-RUNBOOK.md` with the lines marked "Added Oct 24" added (the three of task 4a, then the 2 AM addendum: the pre-stream gap checks and the over-reservation guard-stop note). Where the plan gives no repo fact I say "plan" or "not verified". **Updated 2026-10-24 ~12:50 AM ET with the Proxy's answers** (section 5 now records them; nothing is open there). **Updated 2026-10-24 ~11:30 AM ET: the user moved the CP3 start from Oct 27 to Oct 26** (Decisions 2026-10-24 11:03 AM ET; counted streams Oct 26, 27, 28; code PR #174 and docs PR #169 in one final batch; the flow is section 6). Older dated lines below that say Oct 27 are changed in place where they are rules; the 2026-10-24 history lines keep what was true then.

## 1. Freeze list
**Frozen from the first CP3 render until CP3 is scored** (plan item 1; PLAN-POST-CP2-v2 section 8: "Ranker and editor frozen during CP3"):
1. `editor/*`: **all of it**, `render_picks.py`, `render_queue.py`, `render_guard.py` and `puller.py` included. No plumbing carve-out (Proxy).
2. `detector/rank_windows.py`
3. `detector/detection_heuristics.py`
4. The ranker kinds in `shared/spoken_triggers.py`: `CLIP_THAT`, `WHERE_ARE_YOU`, `I_SUCK`, `WHAT_ARE_YOU_DOING`, `SPOKEN_TRIGGER_KINDS` and `find_spoken_triggers` (what `rank_windows.py` and `detection_heuristics.py` import and what the editor calls). "Ranker kinds" means these and nothing else (Proxy). Not frozen: the T2 cutter and its trigger-hit matcher in the same file (`TRIGGER_PHRASES`, `find_trigger_hits`, the classes and folders), because they only set raw moments aside; only the T2 cutter and its audit use it, and its own header says the detector and ranker do not. **Any change to the trigger LIST itself needs the user's OK**, frozen or not.
5. `DETECTOR_FEATURES_VERSION` (`detector/detection_heuristics.py:199`, now 3). Changing it makes the watcher rescan every VOD scanned by an older detector.

**Not frozen (plumbing outside `editor/`, merges only outside streams):** `detector/cp3_run.py`, `export_picks.py`, `cp1_replay.py`, `trigger_cuts.py`, `transcribe_new.py`, `auto_start.py`, `feeder.py`, `chat_capture.py`, `shared/*` except the ranker kinds in item 4, `scripts/`, `ops/`, docs and the vault.

**What does not freeze but changes spend:** `shared/llm_cost.py`. The parked over-reservation fix would change when the editor's guard refuses a call, not what the editor renders. It stays parked unless the preflight's `over_reservation` line fails (section 4).

**When the freeze starts (Proxy):** at the first `render_picks --night` on Oct 26 or later. A Mac `cp3_run --send` alone does not start it.

**Break-fix during CP3 (Proxy):** a fix to anything frozen is a Proxy + Claude call, the user is told, and it **restarts the CP3 count** (the 3-stream average starts again).

**Merge rule around the first render** (plan): **the last auto-clip-system merge is the one final batch (#174 then #169, Sat Oct 24 or Sun Oct 25, before Monday; Proxy, 2026-10-24 11:03 AM ET); there are none until the Oct 28 `cp3_run` finishes** (Monday Oct 26 is a live stream day: no merges, nothing heavy). The earlier wording was "after the Oct 26 reload until the Oct 27 `cp3_run`". The watcher, feeder and puller exit between pieces of work when `git rev-parse HEAD` changes (docs/SETUP.md, docs/autoupdate.md), so a merge during a stream restarts them.

## 2. CP3 night runbook (from Oct 26; counted streams Oct 26, 27, 28)
**Marks** (Decisions 2026-10-22 11:36 PM, decision C; CLAUDE-BRIEF): CP3 runs on fresh streams from Oct 26 (counted: Oct 26, 27, 28; the user, 2026-10-24 11:03 AM ET), before the OI-036 overview. Postable = ready or perfect. **PASS = at least 1.5 postable per stream on average over at least 3 streams** (unchanged; here the three counted streams). Tracked alongside: the 1(d) target, pick-list recall, late starts, review minutes, cost. Oct 21-25 scans and old re-scans stay held. CP4 follows back to back (2 streams, 0 manual steps, $2 per stream).

**Before the stream (Oct 26; changed 2026-10-24 11:03 AM ET):** no reload and no merge that day. The one final batch lands Sat or Sun and ends with ONE manual `git pull --ff-only` on the Mac and PC (the watcher, chat and feeder restart themselves on the new HEAD); `auto_start --status` must then show `Scan floor: 2026-10-26`, `Held (before floor): 1` (the Oct 23 recording) and `Clip export: off`; confirm the Twitch check is clean; run the preflight (section 4) on both machines with `--night 2026-10-26`. Chat LaunchAgent `com.clipautogenerator.chat` loaded; watcher `com.autoclip.detector-watcher` (detect-only: `WATCHER_EXPORT_CLIPS=0`).

**Added Oct 24 (preflight shell):** run the PC preflight in the same shell that then runs `render_picks`. A reused shell with `CLAUDE_OFFLINE=1` set blocked every call in a CP2 session on Oct 22, and the preflight's `claude_offline` line only sees the shell it runs in.

**Added Oct 24 (credit balance):** if `render_picks` exits 4 and its message mentions "credit balance", stop and tell the Proxy. It is an empty Claude credit balance, not a spend cap, and a rerun will not help until it is topped up.

**Who runs what (Proxy):** the Engineer runs the Mac and PC commands by hand, under `machine.lock`, with the OBS, game and Resolve check, and nothing heavy while the user records. The Engineer reports the gates to the Proxy. The Proxy and Claude confirm and merge. The user reviews the drafts and rates them.

**Steps, Mac, after OBS closes** (plan item 1):
| # | Step | Command and flags (from the files) | Gate, lock, output |
|---|---|---|---|
| 1 | Watcher detects | `com.autoclip.detector-watcher` runs on the closed recording. It scans nothing named before 2026-10-26 (`SCAN_FLOOR`). | Writes `~/Movies/clip_candidates/<night>/<stem>.done.json` and `<stem>/<stem>.detect.json`. A stream that ends after midnight files under the next day's folder. |
| 2 | `transcribe_new` | `detector/.venv/bin/python detector/transcribe_new.py [--since 2026-10-26] [--run] [--wait-for-obs-close [--max-wait-h 8]] [--folder PATH]`. No `--run` = dry run (writes nothing, takes no lock). | Exit 3 while OBS, Resolve, a game or the watcher's detector runs, or while any recording since `--since` has no watcher done note. Takes `~/.auto-clip/machine.lock` (O_EXCL, never broken) and `~/auto-clip-system-rescan/transcribe.lock`. One recording at a time, audio track 0, `CLAUDE_OFFLINE=1`: **$0**. Output `~/Movies/<stem>.transcript.json`; log `~/.auto-clip/logs/transcribe_new.log`. Run by hand (no LaunchAgent, by plan). |
| 3 | `trigger_cuts` per stream | `python detector/trigger_cuts.py run "<stem>" [--vod PATH] [--transcript PATH] [--detect PATH] [--pc-copy skim720\|full] [--accept-short-transcript "<reason>"]`, then `python detector/trigger_cuts.py audit "<stem>"`. | Refuses (exit 3) while OBS, Resolve or a game runs; takes machine.lock; needs free disk of the largest `~/Movies` recording (61 GB minimum) + 20 GB. Transcript must be whole (last word within 5 min of the VOD end, 2,000+ words an hour) or `--accept-short-transcript`. $0. Output `~/Movies/trigger_cuts/<date>/<stem>/rage/` and `hits/`, `<stem> - cuts.json`, `- index.csv`, `- index.md`, `- run.json`; unfinished work in `~/.auto-clip/trigger_cuts/pending/<stem>.json`. Exit 0 = every hit covered by a verified cut. |
| 4 | `cp3_run` dry run, then `--send` | `python detector/cp3_run.py --night YYYY-MM-DD` (dry run, writes nothing), then `python detector/cp3_run.py --night YYYY-MM-DD --send`. `--night` is the date the stream STARTED. | See below. |
| 5 | Feeder check | Read `FEEDER_START_DATE` and `feeder-status.json` (`before_start` note), beside the feeder ledger. | See below. |
| 6 | PC | `python -m editor.render_picks --night <night> [--limit N] [--dry-run] [--verbose]` from the repo folder with the editor venv. | See below. |

**No VOD is archived without a green `trigger_cuts audit <stem>`** (plan; `archive_allowed(stem)` is the call). No archive script exists in the repo: VODs are archived by hand, and never deleted.

**Step 4, `cp3_run`:**
- A stream is used only when all exist: `~/Movies/<stem>.mkv`, `<stem>.done.json`, `<stem>/<stem>.detect.json`, `~/Movies/<stem>.transcript.json`, `~/.auto-clip/chat/raw/<date>.jsonl`. Anything missing is listed and left out. A night or stem before 2026-10-26 is refused (exit 3). A file that resolves under /Volumes (the G-DRIVE) is refused.
- The dry run lists streams and prints "ranker ceiling $X" (under the lock). It lists cuts only when an earlier `--send` left `replay.json`.
- `--send` ranks (one Opus ranker call per stream, ranker budget, reply cache, no retry), then cuts the top 5 per stream with front pad and sidecars.
- Exit 0 done or dry run; 1 no usable stream, a cut failed or the cost guard stopped it; 2 offline send (`CLAUDE_OFFLINE=1` with `--send`, before the lock); 3 refused or stopped.
- Locks: replay and export each take and release `~/.auto-clip/machine.lock` themselves. If another job takes it between them, the export exits 3, and a rerun replays the cache for $0 and skips clips already cut. Both steps refuse while OBS or Resolve runs; the export also while a game runs; re-checked under the lock and before each call or cut.
- Caps (Mac): month $10 (`LLM_MAX_USD_PER_MONTH=10` in `detector/.env`, decision D), run $1, ranker budget $1; `cp3_run` loads only the four spend-cap keys from that file. Plan: about $0.20 per stream, 3 streams take the Mac to about $5.09 of $10 (Mac Oct total after M3 was $4.489161).
- Outputs: `~/.auto-clip/track1/cp3/<night>/replay.json` and `manifest.json`; clips in `~/Movies/clip_candidates/<night>-t1r3/<stem>/`.

**Step 5, feeder:** the feeder sends `<night>-t1r3` only when `FEEDER_START_DATE` (or, if blank, the date in `feeder-start.json`, the Mac's local date minus 1 recorded on its first run) is the night or earlier. Lowering it also queues every unsent night after the new date, including the watcher's own `<night>/` exports (OI-036): read `feeder-status.json` `before_start` first. The feeder waits while OBS is busy, and treats Raw as full when the PC puller's `space.json` is missing or over 6 h old. Newest night goes first, then confidence.

**Step 6, `render_picks`:**
- Top 5 per stream render on the thin path, and rank 1 also on the old path: 6 drafts per stream. One session renders at most `--limit` 10 drafts; a second run does the rest, and a failed draft is retried next session.
- Gates in order: `CLAUDE_OFFLINE=1` refuses (exit 3); render guard (game, OBS, fullscreen GPU app, pause switch, GPU use) or DaVinci Resolve (exit 3); cost preflight (month ledger spent + open + one $1 editor run must stay under the month cap, else exit 4); `%USERPROFILE%\.auto-clip\machine.lock` (O_EXCL, never broken); every pulled clip's SHA-256 must match its sidecar. Guard, Resolve and cost are re-checked before each draft. `env_sources` refuses a shell cap looser than `editor/.env`.
- Caps (PC): month $20 (`LLM_MAX_USD_PER_MONTH=20` in `editor/.env`, decision D); one editor guard per stream per session = one $1 run budget (`min(LLM_EDITOR_MAX_USD, LLM_MAX_USD_PER_RUN)`). Plan: about $0.50 per stream, 3 streams take the PC to about $5.71 of $20 (PC Oct was $4.207552 after the TREE re-plan).
- Exit 0 done, nothing left or dry run; 1 a draft failed; 3 refused or stopped; 4 cost preflight or guard (also an empty Claude credit balance); 130 Ctrl+C.
- Outputs: `%USERPROFILE%\Videos\Clips_To_Review\Needs_Your_Review\<date>\T1 R<rank> - <hook>.mp4` plus `.stamp.json`, `REVIEW_CHECKLIST - <date> T1.txt` (then ` T1 2`); the blind key `%USERPROFILE%\.auto-clip\track1\cp2\<date>\.key\cp2-key.json` and the log `render-picks-<timestamp>.log` beside it. Needs_Your_Review is add-only.

**What to check afterwards:**
1. `cp3_run`: "Cut N clip(s), 0 failed", and the line naming `<night>-t1r3`.
2. `trigger_cuts audit <stem>` exit 0 for every stream before any VOD is archived.
3. `feeder-status.json`: no unexpected `before_start` night; clips reached the PC inbox.
4. `render_picks` exit 0, checklist written, `llm_spend.json` totals on both machines against the caps.
5. Score: postable per stream (needs at least 3 streams, mean at least 1.5), plus the five tracked numbers above.

## 3. Hold rules that apply
Nothing merges while the user is live. No work during OBS. Old re-scans and Oct 21-25 stay held. Never delete VODs, drafts or backups. CP3 needs chat logging live (Decisions 10-22 11:37 PM); chat stays out of the ranker until after CP3.

## 4. $0 readiness preflight (replaces the `cp3_run --night 2026-10-26` dry run)
**Why it replaces the dry run.** Before the first stream there are no Oct 26 files, so `cp3_run` has nothing to find. It only proves the night is accepted (the Oct 23 run proved the refusal, exit 3). The preflight checks the things that actually decide whether the night runs.

**Spec: one run on each machine right after the final batch's pull (Sat or Sun; no reload), and again Monday Oct 26 morning before the stream.** Read-only, no network, no model call, no lock, nothing written. It prints PASS, WARN, FAIL or INFO per line and exits 1 on any FAIL.

Both machines:
| Line | PASS when |
|---|---|
| `head` and `tree` | `git rev-parse HEAD` equals the SHA given with `--expect-head` (run both machines with the same SHA) and no tracked file is changed |
| `claude_offline` | `CLAUDE_OFFLINE` is not `1` (`--send` and `render_picks` refuse it) |
| `machine.lock` | `~/.auto-clip/machine.lock` is absent |

Mac:
| Line | PASS when |
|---|---|
| `scan_floor` | `auto_start.py --status` prints `Scan floor: 2026-10-26` (prints the held count and the watcher process and `Clip export` lines as INFO; Oct 23 should be held) |
| `chat_loaded` | `launchctl list com.clipautogenerator.chat` succeeds; `chat_raw` INFO shows the newest file and its age |
| `feeder_start` | the effective start date (`FEEDER_START_DATE` in `detector/.env`, else `feeder-start.json`) is on or before the night; `feeder_before_start` INFO shows the note |
| `mac_disk` | free space on `~/Movies` is at least the largest `*.mkv` there (61 GB minimum) + 20 GB (`trigger_cuts.required_free`) |
| `mac_caps` and `mac_month_room` | the month ledger's spent + open + streams x ranker budget stays at or under the month cap (default 3 streams) |

PC:
| Line | PASS when |
|---|---|
| `pc_caps` INFO, `pc_model` | caps read from `editor/.env` (month, run, editor budget); the editor model has a price in `llm_cost.MODEL_PRICES` (any other id makes the guard refuse every request) |
| `pc_disk` | the Videos drive has at least 55 GB free (`shared/trigger_lane.VIDEOS_FLOOR_GB`; the plan's floor, 186.2 GB at 10:35 PM) |
| `pc_month_room` | spent + open + streams x editor budget fits the month cap |
| `over_reservation` | see below |
| `pc_python` | `cv2` and `rapidocr_onnxruntime` import (the Oct 14 wrong-Python check; WARN, not FAIL) |

**The $0 over-reservation line (the parked idea, as a check only).** The cost guard reserves a call's ceiling, not its cost: input bound + `max_tokens` of output, with each of the 10 keyframes counted at `IMAGE_TOKEN_BOUND` 5,000 tokens. The preflight builds a synthetic plan request (10 image blocks, about 19 KB of text, `max_tokens` 16,000, then the 20,000 retry), prices it with `llm_cost.request_ceiling_usd` at the editor model's price, and checks that the **sixth** draft's plan retry still fits the run budget: `5 x (spend per draft) + retry ceiling <= editor budget`. One editor guard serves a stream's 6 drafts. The pass check uses **$0.08 a draft** (the plan's $0.50 a stream / 6; Proxy). On the box it gives: plan reserved $0.300 (the figure in PLAN-RESERVATION-v2), retry $0.340, need $0.40 + $0.34 = $0.74 of $1.00, and the largest average spend per draft that still fits is $0.132. **Reading the result:** the check passes at $0.08 a draft. The same line also prints the $0.38 Oct 22 smoke figure (one draft that included one plan retry; SMOKE-DRAFT-COST-BREAKDOWN) as a **WARN, never a FAIL**: at $0.38 the guard would refuse the plan call of the third draft (2 x $0.38 + $0.30 > $1.00). No caps change (Proxy). **After the first real CP3 stream**, run the script with `--per-draft-usd` set to that stream's measured per-draft average (from the key log and `llm_spend.json`). If it is above **$0.132** (the largest average that fits at the current caps), the script prints a `tell_proxy` WARN and the Engineer tells the Proxy **before the next stream**. If the line FAILs, the options are the parked fix (PLAN-RESERVATION-v2, count images by real patches; Opus plan check OK WITH CHANGES) or higher editor caps; both are a Proxy decision, and the first is a `shared/llm_cost.py` change, outside the freeze list.

**Preflight v2 (Oct 24, 1:05 AM ET; supersedes the month check and the OCR check described above).** After the first real run on both machines (PREFLIGHT-PC-CAP-NOTE.md) three fixes went in, still a proposal and not a PR (backup `cp3_preflight.py.bak-005306`):
- The PC reads `editor/.env` last-duplicate-wins, like python-dotenv (what the editor uses), and prints a `duplicate_cap_lines` WARN (key names and numbers only) when a cap repeats. `editor/.env` today has `LLM_MAX_USD_PER_MONTH` three times (5, 5, 20): the editor uses 20, a first-line-wins reader sees 5. The Mac keeps the first-wins read (`llm_cost.load_spend_caps`).
- The `*_month_room` check is the guard's own rule: spent + open + ONE run budget <= month cap (PASS/FAIL). A new INFO line `*_month_projection` shows the 3-stream total at the measured cost (PC: 6 drafts x per-draft) and at a full budget per stream. The old "3 x budget must fit" FAIL is gone.
- The OCR import check is `rapidocr` (the repo's package), not `rapidocr_onnxruntime`.
Run on the real machines at main `39bfb717b8687a8e60ce753e0aff92fa9b19ffee`: Mac 0 FAIL, 0 WARN; PC 0 FAIL, 2 WARN (the duplicate cap lines, and the $0.38 smoke information line). Synthetic-home tests: 5,5,20 gives the WARN and cap $20; a real $5-only file FAILs `pc_month_room` ($4.21 + $1.00 = $5.21 > $5.00); 20 only is clean. Cleaning the duplicate lines to one is a user-owned `.env` edit and was not done.

**Added Oct 24 (where the preflight lives):** draft PR #170 merged on Oct 24 1:47 AM ET as `62f46d5e336f4b40e343f608bed7fa9dfd2d6086` (main was `c0692c18b8908bb3f8c80061bfc94b5e772c068c` then; main is now `d4a122795cdc98fd53d7e9d308af895b7e3d598e` after the 2026-10-24 final batch): the preflight is `scripts/cp3_preflight.py` with `scripts/test_cp3_preflight.py`; run it as `python scripts/cp3_preflight.py --repo <repo folder> --expect-head <full sha>` from the repo's own Python (on the PC in the same shell that runs `render_picks`).

**Added Oct 24 (pre-stream gap checks; SAT2 task 1, all read-only, $0, no lock):** run these after the preflight, the evening before and again right before the stream. (1) PC `editor\logs\puller-task.log`: the newest "Started at commit" line is the final main (Oct 24 2:00 AM ET showed `c0692c1`); the "Could not open the puller log" and "Two review notes name Oct 14 clip 04" warnings are known and harmless. (2) Mac `space.json` (Dropbox `Apps/ClipAutoGenerator/Clips/Receipts/space.json`): `checked_at` under 6 hours old, and no new "No fresh space report" line in `~/Library/Logs/clip-feeder.log` (the last one was Oct 22 2:00 AM ET; without a fresh report the feeder treats Raw as full and sends nothing). (3) Twitch status only: `TwitchHelix.status()` from `detector/auto_start.py` with `detector/.env` loaded in that process prints `offline` (print the result only, never a value), and no new "Twitch status check failed" line in `~/.auto-clip/watcher.log` (169 in total, the last Oct 23 07:59 AM ET). (4) `python detector/transcribe_new.py` (dry run, default `--since 2026-10-26`): "model in the local cache: yes" and 0 to transcribe. (5) PC, in a fresh shell with no `LLM_*` or `CLAUDE_OFFLINE`: `python -m editor.render_picks --night <night> --dry-run` names the puller's inbox `Videos\RL_Clips` and exits 0 (before the stream it says there are no t1r3 picks). (6) Disk margin from the preflight (free GB minus the need; Oct 24 2 AM ET: Mac +261.5 GB, PC +142.7 GB; `trigger_cuts` needs the largest mkv plus 20 GB, and a Monday recording uses some). Oct 24 about 2:05-2:10 AM ET: all six were clean.

**Added Oct 24 (after an over-reservation guard stop):** if a `render_picks` session stops with a run-budget message (a plan call reserves its ceiling, $0.30, or $0.34 on the retry), tell the Proxy. The run budget is counted inside the process (`CostGuard.run_usd` and the reservations); only the month ledger carries over. So a second `render_picks` session for the same night starts with a fresh $1 editor budget, tries the drafts that failed again, and is still held to the $20 month cap by the same rule as the preflight (spent + open + one run budget). Tell the Proxy before starting it. Change no cap.

**The script.** `/workspace/handoffs/cp3_preflight.py` is a **proposal, not a PR**. If the Proxy lands it, the natural place is `scripts/cp3_preflight.py`, with a small test. It uses only the standard library plus `shared.llm_cost`, reads only allowlisted keys from `detector/.env` / `editor/.env` (the spend caps, `LLM_SPEND_PATH`, `FEEDER_START_DATE`, `FEEDER_LEDGER`, `WATCHER_SCAN_FLOOR`, `CLAUDE_MODEL`) and prints numbers and names only. Box test with a synthetic home (`--role pc` and `--role mac`; re-run after the $0.08/WARN update, also at `--per-draft-usd 0.15` to see the FAIL and `tell_proxy` lines): it ran, the Mac lines that need launchctl, chat files or a real feeder failed or warned as expected there, and the plan call reservation came out at $0.300. It has not run on a real Mac or PC.

## 5. Proxy answers (2026-10-24, recorded here; no open questions)
1. All of `editor/*` freezes, no plumbing carve-out. A break-fix is a Proxy + Claude call, the user is told, and the CP3 count restarts.
2. Ranker kinds = `SPOKEN_TRIGGER_KINDS` and `find_spoken_triggers` only. The T2 cutter and trigger-hit matcher are not frozen; any change to the trigger list needs the user's OK.
3. The freeze starts at the first `render_picks --night` on Oct 26 or later (changed 2026-10-24 11:03 AM ET; it was Oct 27). A Mac `cp3_run --send` alone does not start it.
4. The Engineer runs the Mac and PC commands under `machine.lock` with the OBS/game/Resolve check, nothing heavy while the user records, and reports the gates to the Proxy.
5. The over-reservation pass check uses $0.08 a draft; $0.38 is a WARN line. No caps change. After the first CP3 stream use its measured average; above $0.132, tell the Proxy before the next stream.

## 6. Oct 26 / 27 / 28 flow (CP3 starts Oct 26; added 2026-10-24 ~11:30 AM ET from PLAN-CP3-START-OCT26-v1.md section 7)
**Monday Oct 26 is a live stream day: nothing heavy, no merges, no machine jobs while OBS runs.**
- Morning, read-only only, $0: the preflight on both machines with the final SHA (PC in the render shell) and `--night 2026-10-26`, the `auto_start --status` line, chat daemon loaded and its Oct 26 file appearing, disk margin, `space.json` fresh, Twitch offline, the credit balance answer from the user (a low balance stopped CP2 on Oct 22).
- **Ask the user: no OBS test recordings named Oct 26 before the stream.** Any `2026-10-26 ...mkv` is scannable, transcribed by `transcribe_new` and taken by `cp3_run --night 2026-10-26` as one of the night's streams (one more ranker call, a pointless clip, a skewed count). A test recording on Oct 25 or earlier is held and harmless.
- After the stream stops (OBS closed, Twitch offline, `machine.lock` free, no game or Resolve): (1) the live watcher detects by itself 10 minutes after the file stops growing (a stream that ends after midnight is filed under Oct 27); confirm the `.done.json` and `detect.json`; (2) `transcribe_new.py --run --wait-for-obs-close` (default since is now 2026-10-26; about 20-25 min for 7 h, $0); (3) `trigger_cuts.py run "<stem>"` then `audit` ($0; required before any VOD is archived by hand); (4) `cp3_run.py --night 2026-10-26` dry run, then `--send` (one Opus ranker call about $0.25, then the top 5 cut; under `machine.lock`, OBS gate); (5) check `feeder-status.json` `before_start` (`FEEDER_START_DATE` 2026-10-07 is earlier than the night, so `2026-10-26-t1r3` is sent); (6) PC `render_picks --night 2026-10-26`: **this first render starts the freeze**. Run all of it overnight if the user is not streaming Oct 27 morning; the Mac heavy steps refuse while OBS runs, so a stream starting Oct 27 midday would pause them (they resume after).
- Oct 27 and Oct 28 repeat the same steps for their own night. Counted streams are Oct 26, 27, 28; the Oct 28 `cp3_run` lifts the auto-clip-system merge hold.
- Not decided, ask the user via the Proxy: what happens if the user does not stream one of those nights, or streams twice in one. Default: the three counted streams are the first three nights with a stream on or after Oct 26.
- The Oct 23 recording stays held, with no rehearsal on it (the user, 2026-10-24 11:03 AM ET).
- Final batch landed 2026-10-24 ~11:35 AM ET: main is now `d4a122795cdc98fd53d7e9d308af895b7e3d598e` on the Mac and PC (use it for `--expect-head`); watcher floor 2026-10-26.
