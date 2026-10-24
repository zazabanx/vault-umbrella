Stamp: claude-opus-5-5 (Claude Code, effort xhigh, plan mode, read-only), main c0692c18, 2026-10-24 Sat 2

**A. Verdict**
No. Nothing valuable is left to build before CP3. What's worth doing is the open items, a few $0 read-only checks that the 01:52 post-batch check skipped, docs, and one baseline test run. The PC and the Mac should mostly sit idle; heavy work there would only put the holds at risk. **Main risk:** the first real run of the chain at c0692c1, meaning the `cp3_run --send` own-recordings export and a real `render_picks` plan plus render. A defect in `editor/*` found there is a break-fix that restarts the CP3 count.

**B. Priority table**

| # | Task | Owner | Mark | Machine | Time | Cost | Slot | Done when | Depends |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Post-batch gap checks (no lock): PC `puller-task.log` tail; Mac `space.json` age and feeder log; status-only Twitch check (as at 9:21 AM Oct 23); `transcribe_new.py` dry run; `render_picks --night 2026-10-27 --dry-run` in a fresh PC shell; Mac disk margin from the preflight | Engineer | UNATTENDED-OK | PC, Mac | 15 min | $0 | Sat day (now) | Puller "Started at commit c0692c1"; space.json under 6 h, no "No fresh space report" line; Twitch offline; "model in the local cache: yes", 0 todo; render_picks names the puller's inbox; free GB minus need recorded | — |
| 2 | Task 2: send the asks in E in the morning summary | Proxy | NEEDS-USER | — | 15 min | $0 | Sat day | Answers recorded, or defaults apply | — |
| 3 | Runbook addendum (vault-umbrella CP3 runbook note): #1's lines as pre-stream checks; after an over-reservation guard stop, a second `render_picks` session gets a fresh $1 budget (tell the Proxy) | Proxy | UNATTENDED-OK | vault | 30 min | $0 | Sat day | Sonnet OK, merged | 1 |
| 4 | ONE PC runner run and ONE Mac separate-copy run at c0692c1 | Engineer | UNATTENDED-OK | PC, Mac | ~10 min each | $0 | Sat day (now) | PC: 55 suites, 53 + 2 known, 0 new. Mac: every detector suite passes, six known baseline failures | Lock free, OBS/game/Resolve check |
| 5 | If the user streams Monday: `--status` shows "held 2"; the Oct 26 chat file grows; held line in the watcher log; no new Twitch failure; disk margin | Engineer | UNATTENDED-OK | Mac | 10 min | $0 | Mon, after OBS closes | All seen (a free rehearsal of runbook step 1) | E2 |
| 6 | Open-Items: OI-012 (#172 `2e2529c`), OI-046 (c0692c1), OI-059 (done after #1's Twitch check), OI-063 (rest after CP3), **OI-062 re-date** (its PR 5 is `editor/render_nights.py`, frozen, so Oct 31 can't hold; Proxy call). Plus a Roadmap index line, and the box's IDEAS-PARKED ffmpeg row marked done (#171) | Proxy | UNATTENDED-OK | vault, box | 45 min | $0 | Sat night | Sonnet OK, merged | 1 |
| 7 | Refresh held #169 onto c0692c1. Head 4d3d3b4 predates the batch and edits Current-Holds, which #173 changed. Add the batch and the Oct 24–26 Daily notes | Proxy | UNATTENDED-OK | box | 45 min | $0 | Sun day | Mergeable, still draft | — |
| 8 | OI-014: first independent Claude audit in the Sun 11 AM dreaming run, log-only | Proxy | UNATTENDED-OK | box | 1 h | Max ~$1–3 | Sun day | Audit logged | — |
| 9 | OI-012's unchecked #49 "benchmark wording" follow-up (due Oct 26) | Engineer | UNATTENDED-OK | box | 30 min | $0 | Sun day | Moot: noted. Real: plan v1, draft held | — |
| 10 | Approve heartbeat plan v1 (Grok Bot, or one Sonnet check) | Engineer | UNATTENDED-OK | box | 20 min | $0–0.5 Max | Sun night | v1/v2 approved | Max meter under 70% |
| 11 | Build the heartbeat | Engineer | WAIT-FOR-CP3 | box→PC, Mac | 2 h + runs | $0 | After `cp3_run --send` | Opus APPROVE, PC PASS, Mac six baseline | 10 |

**Overnight runs (#4):** worth doing once, not nightly. The 1:21–1:52 AM runs tested each PR head and main on 39bfb71. Nobody has tested the merged tree as a whole: #171 was carried onto a moved main after only a trial merge. One run proves c0692c1 passes with 55 suites (two new test files) and sets the one baseline for the whole hold. Expect nothing new; skip it if a machine is needed for something else.

**Not proposed:**
- A `cp3_run` dry run: it refuses nights before Oct 27, and Oct 27 has no files yet (runbook §4).
- Re-running `trigger_cuts audit`: the files haven't changed.
- A paid rehearsal: the night refusal and the scan hold block it by design.
- Post-CP3 plans beyond #10: CP3's result sets that order (Roadmap pivots).

**C. Hold and freeze check**
- 1, 5: read-only; no lock, scan or restart. The dry run keeps `--since 2026-10-27`.
- 2: items reserved for the user are asked, not done.
- 3, 6: vault-umbrella merges are allowed. The OI-062 date is the Proxy's call.
- 4: a throwaway copy under the standing OK. Run it in its own shell, never the render shell (`CLAUDE_OFFLINE`).
- 7: a push to a draft branch only; main doesn't move.
- 8: dreaming stays log-only.
- 9: any PR stays a draft. If it touches detection or the version, it waits until CP3 is scored.
- 10–11: `scripts/` is not frozen. Merge after cp3_run, never during `render_picks`.

**D. Waits for CP3**
- After cp3_run: the #169 merge and the heartbeat.
- After scoring: T3/T4/T5, chat C1m/C2/B/E/R, items 19/20/22a, #161 nit 3, #153, the detector-only runner mode, no-idle 5/7/6/O1, and the 4 refused T2 streams.
- The over-reservation fix, only if stream 1 averages more than $0.132 a draft.

**E. Asks for the user**
1. Does the API credit cover ~$3 on both keys until the Max credit links (~Oct 28)? Default: run anyway. On a credit stop, tell the Proxy and rerun after a top-up (the Mac replays its cache for $0).
2. Which nights will you stream, Oct 26–31? Default: Monday counts as live; CP3 night 1 is the first stream on or after Oct 27.
3. Ear check of the 5 T2 cuts. Default: CP3 is unaffected.
4. Delete the two `=5` lines in `editor/.env`? Default: leave them; the WARN stays.
5. Post the closing comment on #48? Default: not posted, and OI-012 is re-dated.

**F. Cost**
- Max (notional): ~$1.5–5 (#8 on Opus, plus 2–3 Sonnet checks).
- API: $0 through Monday.
- Oct 27: Mac $4.49 → ~$4.69 of $10 (guard check $5.49, PASS); PC $4.21 → ~$4.71 of $20 (guard check $5.21, PASS).

**G. Risks to a clean CP3**
1. The first real chain run. Run the dry run first, read every exit code, and stop and tell the Proxy rather than patching.
2. Changes on the machines that nobody sees: the credit balance, the puller, and Mac disk. The T2 cuts added 39 GB, the Oct 23 recording stays, and a Monday recording would add more. `trigger_cuts` needs free space of the largest mkv plus 20 GB.

Right before the stream, run the preflight on both machines with `--expect-head c0692c18b8908bb3f8c80061bfc94b5e772c068c` (on the PC, in the render shell): expect 0 FAIL and the 2 known WARN. Then repeat #1's checks and have the answer to E1.

**H. Unknown / not read:** Mac and PC state since 01:52 (puller, `space.json`, disk margin); whether #169 conflicts with #173; the #49 benchmark-wording text; the Max meter; the credit balance; the stream schedule; whether Long-form uses the machines this weekend.
