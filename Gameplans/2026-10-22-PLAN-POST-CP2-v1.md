> Copy of `PLAN-POST-CP2-v1.md` (box handoffs), added 2026-10-22. See [[Roadmap]]. Text below is unchanged.

<!-- RECOVERED Oct 22 2026 ~10:45 PM ET: the box restarted at 10:36 PM and the final file was lost. Body below = Opus's last full draft (rev3, claude-opus-5-5 xhigh on Max, session total $11.03 notional), recovered from the Claude Code session log. The 'Addendum (recovered)' at the end restates addendum 2 and the engineer's fact-check fixes from the engineer's report; the original wording of those is lost. -->

# Post-CP2 plan v1

Oct 22, 2026, ~11:55 PM ET. Revised for the user's two scope updates. Docs only; base main `506bf8b`. Sources: T1-PROGRESS (up to 10:10 PM ET), CP2-PREROLL-FINDING, PR-PLAN-RENDER-NO-IDLE-v3, CLAUDE-QUEUE-AND-PHASES-REVIEW-2026-10-20, the other handoffs, the vault and the code.

## Summary: Claude's read
- **CP2 is a bare pass on its official marks.**
  - Each stream hit exactly 40% Moment=yes per ranked moment.
  - No draft is ready to post: 11 discard, 7 needs work.
  - The 3 blind pairs tied, and 2 of those pairs were both discards.
  - It shows the ranker finds some real moments. It does not show the pipeline makes postable clips.
- **Under the original Oct 20 CP2 marks, CP2 fails.**
  - 0 streams had a postable clip; the mark needed 2 of 3.
  - The moment-grade mark can't be scored from a yes/no field.
  - Review time and cost pass.
- **Odds of the Oct 20 "done" (my judgment).** On Oct 20 they were 35/55/60. Now:
  - about 15% by Nov 25;
  - about 35% by end of December;
  - about 25% for the looser version by Nov 25.
- **Where it loses.** 7 of the 9 Moment=no moments were picking misses. The other 2 were the editor starting too late. So detector and ranker quality is the main track. The start fix runs alongside it and comes before any new feature.
- **Freeze.** Lift it, as the gate for new features. Keep one-in-one-out for rules and keep the review cap. Fixes don't wait for it.
- **CP3.** Keep its pass marks, and read "postable" strictly (ready or perfect). Render CP3 only after the start fix and after a ranker change has beaten the baseline offline, or after testing shows no variant can.
- **Backup plan verdict: yes, as a hybrid now.** The auto top 3-5 keep rendering. A "more candidates" list sits beside them, and the user ticks it on the PC in about 3 minutes. Switch to pick-first only if CP3 misses its detector target.
- **Detector end goal verdict: a quality bar, not a fixed count.** Surface every moment worth posting, which can be 0 on a dead stream. Auto-render at most 5 and list the rest. Score it by precision plus recall. This changes a goal, so it needs the user's OK.

## CP2 against the original Oct 20 marks

| Mark | Oct 20 original | Official (revised) | CP2 result | Under Oct 20 | Under official |
|---|---|---|---|---|---|
| Moment | ≥40% of drafts graded 4-5 | ≥40% of each stream's top 3-5 rated Moment=yes | 40/40/40 per ranked moment; 7/18 drafts (39%) | Not scorable; fails if counted by drafts | PASS |
| Thin vs old | (none) | Thin ≥ old, blind | 3/3 ties | n/a | PASS |
| Postable | ≥2 of 3 streams with 1+ postable | (none) | 0 ready or perfect | FAIL (0 of 3) | n/a |
| Review | ≤15 min per stream | ≤15 min per stream | 13 / 6 / 10 min | PASS | PASS |
| Editor cost | Measured and <$0.20 per clip | (none) | $0.089 (17 drafts); $0.105 (all 18) | PASS | n/a |
| **Overall** | | | | **FAIL** | **PASS (knife edge)** |

- **Moment.** A yes/no field doesn't map cleanly to a grade of 4-5. A "yes" means "worth clipping", which can include a middling 3. So 40% "yes" is an upper bound on the share graded 4-5 (to confirm with the user).
- **Postable.** The Oct 20 definition (line 39) also counts a needs-work draft that one re-render fixes from a one-line note, or that the user can fix in 5 minutes.
  - Two drafts plausibly qualify: Oct 14 "WHY DID BRO FALL OVER?" (note: "needs earlier start") and Oct 9 "THAT WAS THE RUN" (problem: start).
  - The others don't: DAD needs a re-cut, and PUNISHED and ROBOT each have several notes.
  - The same definition also requires at least half of postable clips to be ready as is, and none were.
  - So the official count is 0 postable unless the user rules otherwise.
- **Cost correction.** The Proxy's "$1.51 for 18 drafts, $0.084 each" is off.
  - The ledger read $1.381398 after the smoke draft (5:28 PM ET) and $2.891016 after all 18 (8:54 PM ET).
  - The $1.00 before the smoke draft was the October seed, not CP2 spend.
  - So $1.51 covers the 17 drafts after the smoke ($0.089 each). All 18 cost $1.89 ($0.105 each).
- **Distance from the Oct 20 done definition** (lines 7, 35-43). One of the five checks is met:
  - Postable: 0 per stream. Needed: ≥1 on every stream, 2 on average.
  - Streak: 0 of 4.
  - Review ≤10 min: met on 2 of 3 streams.
  - Hands-off: not built.
  - Cost: about $0.65-0.90 per stream. Met.
- **Why the odds fell.**
  - 0 ready out of 18 is no better than the 0 out of 39 on Oct 20.
  - A 4-stream streak by Nov 25 needs hands-off working by about Nov 17.
- **What keeps them from falling further.**
  - The late-start cause is known.
  - With correct starts, the unofficial count is 53%.
  - If the pick list becomes the product (one pick of 3 minutes or less per stream, instead of 0 manual steps), I'd put the looser "done" by end of December at about 60%.

## House rules
- One defect per PR, plan first, draft PRs.
- Claude review (2-round cap plus one short extra) and a PC test before merge.
- Never delete VODs or clips. Never post.
- The paid API key runs only inside the pipeline, under the $5 PC and $15 Mac caps. Reviews and plans run on Max.
- The user's OK is needed for: anything public, deletes, G-DRIVE beyond read-only, paid spend past the caps or any new paid API use, changes to goals, checkpoints or pass marks, the freeze lift, and the trigger list.

## 1. Main track: detector and ranker quality
The user's steer fits the data and sets the queue order: "if the detector can just find the right clips, the editing will be a breeze."

**(a) The 9 Moment=no ranked moments**

| Moment | Box evidence | Cause |
|---|---|---|
| Oct 9 R1 pair, "TWITCH, CLIP THAT SOLO PLAY" / "HEY TWITCH" | The smoke-test pick; both discard; the hook suggests a spoken "clip that" (inference) | Smoke test; rest to confirm |
| Oct 9 R2, R5; Oct 14 R2, R3 | No note; hooks not on the box | To confirm |
| Oct 14 R5, "NICE, BRO…" | Silent game audio logged (-91 dB) | To confirm |
| Oct 15 R1 pair, "I DIDN'T KNOW YOU COULD KILL HIM" / "5 AND I KILLED THE DRAGON" | No note; both discard | To confirm |
| Oct 15 R2 "LEAVE THE BALL", R4 "GET TO THE TREE" | The peak is 4-14 s before the draft start, inside the pick | Editor started late |

**(b) Signals to test,** one at a time, offline:
- **Loudness size.** The ranker only sees the words "loud spike" or "loud stretch" (`rank_windows.py:127-132, 329-333`). Add how far above the stream's 99th percentile the moment is, in dB.
- **Peak-centred excerpt.** The transcript excerpt stops at 160 words (`:120`), so it can miss the peak. Centre it on the loudest point.
- **Export pre-roll.** DAD's setup started 15 s before the pick.
- **Trigger phrases as ranker cues** (`:133-138`). This one waits behind the gate.
- **Chat.** Not wired today.
  - Only two config fields exist (`detector/config.py:26-27`), and the detector says it works "from the OBS recording alone" (`detection_heuristics.py:4`).
  - Live chat could be logged for free during streams. Chat for old VODs is only available through unofficial routes (to confirm).
  - Chat is a new data source, so it needs the user's OK.
- **Gemini video+audio.** New paid API use: it needs a blind test and the user's OK, after OI-036.

**(c) Offline evaluation, before any rendering**
- **M1 comes first** (read-only, $0, Mac + PC).
  - For each miss, read the pick, the ranker's reason, the detector events, the full-VOD transcript and the rating row.
  - Assign one cause: no real moment, low-energy chatter, wrong peak, duplicate, weak setup, or smoke test.
  - For any unclear row, ask the user (about 2 minutes).
- **M2: the labeled set.**
  - Sources: the CP1 cards, CP2's 15 ranked moments, `frozen_set.json`, and later the pick-list ticks.
  - Extend `detector/cp1_replay.py` (`replay` :351, `score_run` :667) to report precision@5, plus recall once ticks exist.
  - The baseline replays from the reply cache for $0 and should reproduce 6/15.
- **Cost.**
  - Each ranker variant costs about $0.50 for 3 streams, on the Mac ranker budget.
  - Cap the experiments at $5 in total. Reruns come from the cache for $0.
  - Don't run them through `claude -p` on Max: that changes the request being tested.
  - Oct 9, 14 and 15 never supply prompt examples, so the test stays blind.
- **Win rule.** A ranker variant counts as a win only if it:
  - gains at least 2 of the 15 moments;
  - loses on no stream;
  - holds the frozen-set agreement (14/20);
  - passes a blind card.

**(d) Tracked CP3 detection target:** top-5 Moment=yes ≥60% on average, no stream under 40%, and no moment the user says was missed.

## 2. Detector end goal
**Recommendation: every clip worth posting, by a quality bar.** Auto-render at most 5 per stream and list the rest. Not a fixed 3-5.
- **Review time.**
  - A fixed count pads dead streams: 11 of CP2's 18 drafts were discards, at about a minute of review each.
  - A quality bar shows 0-2 drafts on a dead stream.
  - The cap of 5 keeps a great stream inside 15 minutes. Its extras go to the pick list.
- **Editor cost.** Each padded draft wastes about $0.09 and 3-4 PC minutes.
- **Posting cadence.**
  - The target is 6-7 postable per week (Opus call 2). At 3-4 streams a week, that is about 2 per stream on average.
  - A great stream should bank its extras for slow weeks. A fixed 5 throws them away.
- **Triggers and rage clips.** Those lanes already run without a count. They stay outside the bar and the pass marks, each with its own review cap.
- **Pass marks under a bar.**
  - Precision: the Moment=yes share of what's surfaced.
  - Recall: the share of moments the user would have picked that the system surfaced.
  - The pick list supplies the recall labels: a tick outside the auto set is a miss.
  - Opus call 1's honest "nothing strong tonight" fits this naturally.
- **What it needs.**
  - Today the ranker only puts candidates in order and forbids numbers (`rank_windows.py:31-33`).
  - It would need a "worth posting: yes/maybe/no" label for each candidate, tested offline first.
  - The Oct 20 review already proposed "only grade 4 and up" after CP2 (its decision 6).
- **Approval.** Changing a goal or a pass mark needs the user's OK. Default: CP3 keeps its official marks, with precision and recall tracked beside them.

## 3. Backup plan: user picks from a candidate list
- **What already exists.**
  - The ranker already orders every candidate with a one-line reason (`rank_windows.py:1-27`). That covers up to 24 main picks, up to 40 overflow picks, and the scout's finds.
  - `export_picks --top` defaults to 5 (`export_picks.py:78, 493`) and cuts clips by stream copy (`:314-321`).
  - `cp1_replay cards` (`:490`) already builds blind one-line cards.
  - Needs_Your_Review, the checklist and the ratings writer are all in place.
- **Hybrid (recommended now).**
  - The auto top 3-5 render as they do today.
  - Ranks 6-20, plus 2 random lower ranks, go into a "more candidates" checklist. Each row gets the quote, the ranker's reason, a thumbnail and an 8-second preview.
  - Ticked rows render.
- **Pick time.** Target 3 minutes or less per stream, on the PC. Picking plus draft review stays within 15 minutes.
- **Cost.**
  - Previews are made with ffmpeg on the Mac after OBS closes: $0 API.
  - Previews add about 100-150 MB of Dropbox per stream (estimate). Thumbnails only would be about 2 MB.
  - In pick-first mode, rendering 2-3 picks instead of 5-6 automatic drafts saves about $0.25 and 10 PC minutes per stream.
- **Labels.**
  - Every tick and every rating feeds M2.
  - At about 15 labels per stream, the ~100 labels the Oct 20 review wanted arrive in about 7 streams.
- **Trigger to switch to pick-first.** After CP3 is scored, switch if any of these holds:
  - top-5 Moment=yes averages under 50%;
  - 2 or more streams are under 40%;
  - the user ticks, on average, 2 or more moments per stream that the auto set missed;
  - M3 finds no ranker change that beats 6/15.
- **Fit with earlier decisions.**
  - The Float/templates review dropped approve-before-render. The hybrid stays hands-off, because picking is optional.
  - Pick-first is the Dec 4 stop rule ("the 2-minute phone pick is the product", `vault/CLAUDE-BRIEF.md`), brought forward to the PC and used only on the trigger.
  - Opus call 1 already gives the user a 2-minute look at the top cards.
- **Queue position.** Behind the gate, before the CP3 renders (item 28). It needs the user's OK. Switching to pick-first needs a second OK.
- **Verdict: worth it.** Build the hybrid for CP3. Hold pick-first until the trigger fires.

## 4. Start too late: the editor quick fix (parallel, on the PC)
**Root cause.** The editor's per-clip transcript has no words for shouts and laughs, so it treats the peak as silence (`editor/windows_editor_skeleton.py:1581-1588`). The thin path then keeps the late start (`editor/thin_path.py:169-181`).
- **PR 1: a look-back guard (thin path only).**
  - The rule: if an audio spike or a loud span with no words falls within 20 s before the planned start, move the start to 2 s before it.
  - The start moves back at most 30 s, and never before the pick start.
  - It runs only on the PC and costs $0 to test on cached plans.
  - Failing test first: LEAVE THE BALL must start at -14 s or earlier.
- **PR 2: full-VOD words for the editor.** Fill the loud gaps with the ranker's mlx-whisper words. This is the root-cause fix.
  - Those words are timed only to ±1-2 s, so use them only to fill gaps.
  - Re-plans cost about $0.60 for the 7 drafts.
- **Test.**
  - Re-plan only, with no render, on the 7 late-start drafts.
  - Each new start must land at or before its "latest start" offset: 17.2, 12.3, 9.4, 44.1, 18.3, 24.9 and 8.0 s.
  - DAD and ROBOT (old path, needs 44 s) are out of the guard's reach.
  - The locked clips stay green.
- **Other editor follow-ups.**
  - Dead air: after CP3, allow at most 1 reasoned cut, blind-tested against no-cut.
  - Thin stays the only path for new plans, and old-path comparison pairs stop.
  - Clips 01 and 14 stay on the old path.

## 5. OI-058 triggers, always-clip and the rage collection (the user reviews the list before it goes live)

| Phrase | Spoken variants (proposed) | Always-clip | Rage collection |
|---|---|---|---|
| OH MY GOD | oh my god, omg, oh my fucking god | yes | yes |
| I'm the best | i'm / im / i am the best; I'm literally the best | yes | no |
| I'm him | i'm / im / i am him | yes | no |
| the greatest | the greatest; I'm the greatest | yes | no |
| best ever | (the) best ever | yes | no |
| greatest of all time | greatest of all time | yes | no |
| get out of the way | get out of / outta / out the way | yes | yes |
| f-word version | get the fuck out of / outta the way; get out of the fucking way | yes | yes |
| WHAT ARE YOU DOING | already a trigger (`shared/spoken_triggers.py:178`) | detector bonus only today | yes |
| WHERE ARE YOU | already a trigger (`:177`) | detector bonus only today | yes |
| I suck I suck I suck | already a trigger; fires on 2+ repeats (`:38`) | detector bonus only today | yes |

- **Rules.**
  - Triggers always get clipped, separately from the ranker's best 3-5.
  - Every rage occurrence goes into its own collection.
  - Neither lane counts toward the pass marks.
- **Matching.**
  - Match on the Mac's full-VOD transcript, which kept the shouts.
  - Tokens must match exactly (`spoken_triggers.py:34, 127-140`).
  - Loudness may sort rage clips but must never gate them.
- **Order.** New streams need the transcription wrapper or Fix B first. Measure how often each phrase fires before building.
- **Banned-line filter.** `exclude_banned_speech` (`content_generator.py:5269`) runs only on the old path (`windows_editor_skeleton.py:519`). Close that gap on the thin path first.
- **Detector version.** New trigger kinds bump `DETECTOR_FEATURES_VERSION` (now 3) and need the Mac test run (AGENTS.md rule 8).
- **Rage clips** are stream-copy cuts at $0 API. The compilation comes later, is planned first, and is never posted.

## 6. The freeze lift is the gate
- **What the freeze is.** Call 6. Until the CP2 review: dreaming is log-only, the 2-round review cap applies, and no new Decisions lines go in except checkpoint results.
- **Ruling: I agree with the Proxy, with one correction.** The lift belongs early, as the gate. Behind it sit:
  - the triggers;
  - new detector features;
  - the candidate list;
  - Float and the templates.
- **The correction: the freeze doesn't hold fixes.** These run before the gate:
  - defect fixes and reliability work;
  - test-only and docs PRs;
  - read-only investigations;
  - the offline evaluation.

  They need only the build OK for the fix lane (decision 1), because the Engineer hold still covers code outside Track 1.
- **Risks.**
  - Rule growth: Decisions went from 125 to 139 lines since Oct 21.
  - More review load.
  - Chasing a knife-edge result.
  - Collisions between parallel jobs (as on #112).
- **Exact question:** "CP2 passed at the minimum (40/40/40 per ranked moment). May we lift the call-6 freeze now? That would mean:
  - new Decisions lines are allowed again, under one-in-one-out;
  - dreaming writes proposals again (at most 3 a week);
  - the gated queue items start in order (triggers, the rage collection, the candidate list, ranker changes that won offline, Float and the templates).

  The 2-round review cap (plus one short extra) stays as a standing rule. Yes / no / yes with changes?"

## 7. Rulebook, overlap check, Float, Clip Renders; post-pack fix
- **Behind the gate, in this order:**
  1. One shared rulebook owned by the Proxy.
  2. A monthly overlap check, which decides whether to run a 2-week read-only Float trial.
  3. A "ping only when blocked, ready or done" rule.
  4. Clip Renders bot upgrades: a rule never to invent a quote, speaker or timestamp, and a critic rubric tuned on the CP2 ratings. Later, a sync/glitch check.
- **Float trial use case:** read-only, propose-first housekeeping, like tonight's Needs_Your_Review tidy-up. The Proxy cancelled that one at 9:52 PM ET, and nothing was moved. Any move or delete needs the user's OK.
- **Post-pack fix** (plan first, then a docs PR). `vault/Jobs/post-pack.md:5` still reads the frozen vault scorecards file. Point it at the PC's `scorecards.csv`, and:
  - keep only rows whose `outcome` is ready or perfect;
  - use the newest row per clip, by `written_at`;
  - find the draft by `file` + `stream_date`.

## 8. Cost per clip after Max
- **Baseline.** $0.089 per draft (the 17 after the smoke draft), or $0.105 counting all 18. The ranker costs $0.12-0.23 per stream.
- **Target.**
  - ≤$0.10 per draft.
  - ≤$1 per stream for the auto set.
  - ≤$2 per stream including triggers and picks.
  - Rage clips and previews: $0.
- **Caps.**
  - About 17 streams a month costs $17-34.
  - October has only about $1.10 of PC room left, so CP3 needs a cap decision.
- **Max credit.** From about Oct 28, the Max plan's API credit pays first, once it is linked to the one org that holds both keys.
- **Editor model.**
  - The code default is Sonnet (`editor/config.py:80, 196`).
  - The "Opus" stamp on the drafts is probably the ranker's model, not the editor's: `render_picks.py:556-557` copies `pick.get("model")`, which comes from the ranker (`export_picks.py:358`).
  - To confirm on the PC:
    1. Load `.env` the way render_picks does (`review_inbox.py:940-945`).
    2. Print only `config.claude.model` and `trends_model`, plus yes/no for whether `CLAUDE_MODEL` was set in the session.
    3. Never print the key.
- **Cost cuts, in order.**
  1. A per-call usage log (`shared/llm_cost.py:588`).
  2. The malformed-answer retry fix (the variations bug): 7 drafts needed a retry (`content_generator.py:13990-13999`).
  3. Cached trends: keep them 72-168 h instead of 24 h (`config.py:83, 199`).
  4. A leaner editor, blind-tested: Claude on the hard calls, and Haiku or local models for simple steps like hooks and post text.
  5. The environment preflight, which also stops the paid face-location fallback (`content_generator.py:13846-13875`).

## 9. Reliability
- **No-idle v3** (referenced here, not redone). Order: 3a → 1 → 2 → 3 → 4 → 5 → 7 → 6 → O1.
  - PR 3a fixes the CLAUDE_OFFLINE leak (`scripts/run_tests_pc.ps1:63-65`).
  - PR 4 makes cost_check load `editor/.env` (`render_picks.py:258-279`).
- **watcher.lock flake** in `detector/test_auto_start.py:1433`: it fails in about 25-50% of PC runs.
- **Per-suite timeout.** The runner already has 20 minutes (`run_tests_pc.py:30`). Add a 60-second heartbeat, and do the same in run_one (to confirm).
- **Oct 14 wrong Python.** Add a preflight that refuses to render when `rapidocr` or `cv2` won't import.

## 10. CP3 and CP4 (pass marks unchanged)
- **CP3.** Fresh streams from Oct 27, run by one command. This renders new streams before the OI-036 overview, so it needs the user's OK.
  - Pass mark: the done criteria on at least 3 streams. The Oct 20 text says ≥1.5 postable per stream on average; which one applies is to confirm.
  - Tracked alongside: the 1(d) detection target, pick-list recall, late starts, review minutes and cost.
  - The ranker and editor stay frozen during CP3.
- **CP4.** 2 streams with 0 manual steps, and drafts plus a morning report by 10 AM.
  - Build order: the report, then automatic scout and rank, then the overnight render (no-idle PRs 5, 7, 6 + O1).
  - The Oct 20 text's "≤$1 per stream" conflicts with the user's ~$2.

## 11. Schedule and renewals (dates aren't targets)
Grok Bot Pro+ renews Nov 12 (21 days away). Claude Max ends Nov 21 (30 days away).
- **Likely flow.**
  - Oct 23-26: items 1-13.
  - Oct 27-Nov 2: items 14-23.
  - Nov 3-12: CP3 scored, plus the trigger work and the CP4 build.
  - Nov 12-21: CP4 runs.
- **Realistic before Nov 12:** the fixes merged, M1-M3 results in, and CP3 probably scored. CP4 passing and the backlog target being proven are not realistic by then.
- **Realistic before Nov 21:** a CP4 run is likely. Hitting the backlog target is about 50/50.
- **Recommendation: keep both plans one more month.**
  - Grok: decide Nov 10. Keep it unless CP4 has passed.
  - Max: decide Nov 18. Keep it if CP4 or the backlog target is still open. It costs about $45-60 a month more than Pro plus pay-as-you-go API, and the extra month covers the Dec 4 stop check.

## 12. The queue
Format: item — machine · OK needed · runs after. "Fix OK" means decision 1. The PC runs one heavy job at a time, never while the user is live.

**Before the gate**
1. Claude review of this plan → Proxy → user decisions — box · — · none
2. Confirm the editor model — PC, read-only · — · none
3. M1: classify the 7 misses — Mac + PC, read-only · — · none
4. Measure trigger fire rates — Mac, read-only, $0 · — · none
5. Link the Max API credit (~Oct 28) — the user's billing · user · none
6. PC cleanup leftovers — PC · user OK per item · none
7. watcher.lock flake fix — box→PC · test-only · none
8. No-idle v3 PR 3a — box→PC · fix OK · none
9. Test-runner heartbeat and timeout — box→PC · test tooling · 8
10. Post-pack docs PR — box · docs · none
11. Start fix PR 1, the look-back guard — box→PC · fix OK · none
12. M2: labeled set, eval tool, baseline — box→Mac · fix OK · none
13. No-idle v3 PRs 1→2→3→4, then the wrong-Python preflight — box→PC · fix OK · 8
14. Start fix PR 2, full-VOD words — box→Mac+PC · fix OK · 11
15. Usage log, then an editor-model stamp — box→PC · fix OK · 2, 13
16. Malformed-answer retry fix — box→PC · fix OK · 13, 14
17. Cached-trends default — box · Proxy + Claude · 15
18. Close the thin path's banned-line gap — box→PC · fix OK · 16
19. M3: offline signal tests — Mac · within the cap · 12
20. OI-059 Mac prep and the transcription wrapper — Mac · already approved · never during streams

**21. GATE F: the freeze lift (user OK).** Ask it in item 1's decision batch.
- Items 1-20 don't wait for it.
- Items 22-33 and 37 do.
- Items 34-36 and 38 are listed here only for order.

**Behind the gate**
22. Merge a winning ranker change, frozen for CP3 — box→Mac · gate · 19
23. New trigger kinds and ranker cues — box→Mac · gate + trigger-list OK · 4, 20
24. Always-clip pin, kept separate from the top 3-5 — box→Mac+PC · gate · 18, 23
25. Rage side collection, then the compilation plan — box→Mac+PC · gate + folder OK · 23
26. Live chat logging — box or PC · user OK (new data source) · 21
27. Quality-bar label in the ranker, tested offline; merge after CP3 — box→Mac · gate + goal OK · 12
28. Hybrid candidate list — box→Mac+PC · user OK · 20
29. New-stream top picks by one command → CP3 — box→Mac+PC · user OK · 14, 20, 22, 28
30. Shared rulebook, then the overlap check — box · gate · 21
31. Float read-only trial (housekeeping) — box · user OK for any move · 30
32. Clip Renders upgrades — box→PC · gate · 30, CP3
33. Leaner editor and local models; dead-air cut — box→PC · gate, blind tests · 15, CP3
34. CP4 build: no-idle v3 PRs 5→7→6 + O1, report, automatic ranking — box→PC+Mac · fix OK · 13, 29
35. CP4 on 2 streams; pick-first switch only if the trigger fires — PC + Mac · OK for the switch · 34
36. OI-036 overview, then the backlog once the target holds — Mac + PC · user OK · main track, Fix B, OI-022
37. Gemini blind test — user OK (new paid API) · 36
38. Renewal calls: Grok Nov 10, Max Nov 18 — user

## Decisions for the user
1. Build OK for the fix lane (items 8, 11-16 and 18, plus the no-idle PRs in item 34)? **Default: yes.**
2. Lift the freeze (the exact question in section 6)? **Default: yes, and keep the review cap.**
3. Approve the trigger list as tabled? **Default: yes, with per-stream caps set after the fire-rate check.**
4. Should the existing scream triggers also always get clipped? **Default: yes.**
5. Read "postable" strictly, which keeps CP2 at 0 postable? **Default: yes.**
6. Build the hybrid candidate list for CP3? **Default: yes.**
7. Adopt the switch trigger in section 3? **Default: yes, applied after CP3 is scored.**
8. Make a quality bar with an auto-render cap of 5 the detector's end goal? **Default: yes as the direction. CP3 keeps its official marks.**
9. Render new streams before the OI-036 overview, for CP3? **Default: yes.**
10. Log live Twitch chat? **Default: yes, after the gate.**
11. Set the caps from now at PC $20 and Mac $10 a month? **Default: yes.**
12. CP4 cost mark: $1 or $2 per stream? **Default: $2.**
13. Put rage clips in `Videos\Rage_Collection\<date>`? **Default: yes.**
14. PC cleanup: what to clear? **Default: only the group (a) items you pick.**
15. Plan renewals? **Default: keep both one more month, unless the tests in section 11 say otherwise.**
---

## Addendum (recovered): CP2 vs Opus's ORIGINAL Oct 20 marks, and fact-check fixes

**CP2 against the original Oct 20 marks:**

| Original mark | CP2 | Result |
|---|---|---|
| ≥40% moment grade 4-5 | Moment=yes 40/40/40 per ranked moment; a yes/no Moment can't be scored as "grade 4-5" | Can't be scored cleanly |
| ≥2 of 3 streams with 1+ postable | 0 of 3 (the best verdict was needs work; Oct 15 R3 "yes" was ruled needs work) | FAIL |
| Review ≤15 min | 13 / 6 / 10 min | PASS |
| Editor spend per clip <$0.20 | about $0.105 per draft (all 18 cost about $1.89) | PASS |

**Opus's odds:** down from 35% / 55% / 60% to about 15% done by Nov 25, about 35% by the end of December, and about 25% for the looser version.

**Fact-check fixes from the engineer:**
- The CP2 cost: $1.51 covers the 17 drafts after the smoke draft ($0.089 each). All 18 cost about $1.89 ($0.105 each).
- The "Opus" model stamp on the drafts is probably the ranker's model. render_picks.py:556-557 copies the model from the pick, and export_picks.py:358 fills it from the ranker. The editor's code default is Sonnet. The read-only editor-model check settles it.
- Oct 15 R3 is ruled needs work, which makes Oct 15's average 0.33. The per-ranked-moment count is official, and the per-draft count is a footnote only.
- run_one.ps1 lives on the PC, not in the repo. Check for the missing CUDA library (cublas64_12.dll) during the test-runner heartbeat work.
- Post-pack details: utf-8-sig, flagged rows skipped, the ratings_writer text, and review-batch step 2.
- The Max plan gives about $100 a month of API credit, to be linked around Oct 28.
- Backlog success-rate target: about 50/50 by Nov 21.
