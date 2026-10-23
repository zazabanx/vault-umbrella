> Copy of `PLAN-POST-CP2-v2.md` (box handoffs), added 2026-10-22. See [[Roadmap]]. Text below is unchanged.

# Post-CP2 plan v2

Oct 22, 2026, ~11 PM ET. Docs only; base main `506bf8b`. This is v1 (`PLAN-POST-CP2-v1.md`) with the Opus r1 review (`REVIEW-POST-CP2-v1-r1.md`, APPROVE WITH CHANGES) folded in by hand. No new Claude run. v1's sources still apply: T1-PROGRESS, CP2-PREROLL-FINDING, PR-PLAN-RENDER-NO-IDLE-v3, CLAUDE-QUEUE-AND-PHASES-REVIEW-2026-10-20, the other handoffs, the vault and the code.

*v1 recovery note:* v1 is Opus's rev3 draft plus a recovered addendum, rebuilt from the Claude session log after the box restarted at 10:36 PM ET. Addendum facts are folded into the body below.

## Changes from v1 (Opus r1)

| Area | v1 | v2 |
|---|---|---|
| Start fix | PR 1 at item 11, PR 2 at item 14 | PR 1 right after no-idle 3a, then PR 2 |
| Critical path | M2 at 12, M3 at 19, OI-059 wrapper at 20 | M2, then M3 (Mac, alongside the PC fixes), then the OI-059 wrapper, straight after PR 2 |
| Post-pack docs | Before the gate (item 10) | Behind the gate |
| CP3 depends on | 14, 20, 22, 28 | Also the thin-path banned-line gap (v1 #18) |
| Chat logging | Behind the gate, box or PC | On the Mac, started before Oct 27 |
| v1 #30-32 (rulebook, overlap check, Float trial, Clip Renders upgrades) | Behind the gate | Cut, pending renewal decision E. Kept: one prompt line, "never invent a quote, speaker or timestamp" |
| New items | none | Turn off Grok auto-renew (user's call); list box dependencies (read-only) |
| v1 #34 CP4 build | Fix OK, box→PC+Mac | Built as local launchd / Task Scheduler scripts; this is the migration; out of the fix OK |
| Guard test bar | All 7 drafts must reach their latest-start offsets | PR 1: BALL at −14 s or earlier, locked clips stay green. 7-draft bar only after PR 2 plus a ~15 s export front pad |
| Decisions | 15 | 5 user decisions (A-E), 4 ask-if-triggered, 6 for Proxy + Claude |
| Scream triggers | Default: also always-clip | Rage collection only |
| CP3 pass mark | Left "to confirm" | Set in decision C |
| Renewals | Keep both a month; Grok decided Nov 10 "unless CP4 passed" | One dated plan (decision E) |
| "7 of 9 were picking misses" | Stated as fact | Unproven until M1 |
| Addendum, §7, §11 | Separate | Folded in or replaced |

## What runs before the user answers
**Nothing gated is built until the user answers A-E.** That includes no-idle PR 3a and the look-back guard. Only two read-only, $0 prep jobs run now:
1. **M1:** classify the 7 unnoted misses (Mac + PC, read-only).
2. **Editor-model confirm** (PC, read-only).

## Summary
- **CP2 is a bare pass on its official marks.** Each stream hit exactly 40% Moment=yes per ranked moment. No draft is ready to post: 11 discard, 7 needs work. The 3 blind pairs tied, and 2 of those pairs were both discards. The ranker finds some real moments. The pipeline doesn't yet make postable clips.
- **Under the original Oct 20 marks, CP2 fails.** 0 streams had a postable clip against a mark of 2 of 3. The moment-grade mark can't be scored from a yes/no field. Review time and cost pass.
- **Odds of the Oct 20 "done" (Opus's judgment).** They were 35/55/60 on Oct 20. Now about 15% by Nov 25, about 35% by end of December, and about 25% for the looser version by Nov 25.
- **Where it loses.** 2 of the 9 Moment=no moments were the editor starting too late. v1 called the other 7 picking misses. **That is unproven:** those 7 rows have no notes, and M1 decides. Until then, treat detector and ranker quality as the likely main track, with the start fix running alongside it before any new feature.
- **Freeze.** Lift it as the gate for new features (decision A). Dreaming stays log-only. Keep one-in-one-out for rules and keep the review cap.
- **CP3.** Read "postable" strictly (ready or perfect). Render CP3 only after the start fix, the banned-line gap fix, and a ranker change has beaten the baseline offline (or testing shows no variant can).
- **Backup plan: a hybrid now.** The auto top 3-5 keep rendering. A "more candidates" list sits beside them, and the user ticks it on the PC in about 3 minutes. Switch to pick-first only if CP3 misses its detector target.
- **Detector end goal: a quality bar, not a fixed count.** This changes a goal, so it is asked when CP3 is scored, not now.

## CP2 against the original Oct 20 marks

| Mark | Oct 20 original | Official (revised) | CP2 result | Under Oct 20 | Under official |
|---|---|---|---|---|---|
| Moment | ≥40% of drafts graded 4-5 | ≥40% of each stream's top 3-5 rated Moment=yes | 40/40/40 per ranked moment | Not scorable | PASS |
| Thin vs old | (none) | Thin ≥ old, blind | 3/3 ties | n/a | PASS |
| Postable | ≥2 of 3 streams with 1+ postable | (none) | 0 ready or perfect | FAIL (0 of 3) | n/a |
| Review | ≤15 min per stream | ≤15 min per stream | 13 / 6 / 10 min | PASS | PASS |
| Editor cost | Measured and <$0.20 per clip | (none) | $0.089 (17 drafts); $0.105 (all 18) | PASS | n/a |
| **Overall** | | | | **FAIL** | **PASS (knife edge)** |

- **Moment.** A "yes" means "worth clipping", which can include a middling 3, so 40% is an upper bound on the share graded 4-5. The per-ranked-moment count is official; the per-draft count (7/18, 39%) is a footnote. Oct 15 R3 is ruled needs work, which makes Oct 15's average 0.33.
- **Postable.** The Oct 20 definition (line 39) also counts a needs-work draft that one re-render fixes from a one-line note. Oct 14 "WHY DID BRO FALL OVER?" and Oct 9 "THAT WAS THE RUN" plausibly qualify; DAD, PUNISHED and ROBOT don't. The definition also needs at least half of postable clips ready as is, and none were. So the count is 0 under the strict reading (decision C).
- **Cost correction.** The ledger read $1.381398 after the smoke draft (5:28 PM ET) and $2.891016 after all 18 (8:54 PM ET). The $1.00 before the smoke draft was the October seed. So $1.51 covers the 17 drafts after the smoke ($0.089 each); all 18 cost $1.89 ($0.105 each).
- **Distance from the Oct 20 done definition** (lines 7, 35-43). One of five checks is met: postable 0 per stream (needed ≥1 on every stream, 2 on average); streak 0 of 4; review ≤10 min on 2 of 3 streams; hands-off not built; cost about $0.65-0.90 per stream (met).
- **Why the odds fell.** 0 ready of 18 is no better than 0 of 39 on Oct 20. A 4-stream streak by Nov 25 needs hands-off by about Nov 17. **What holds them up:** the late-start cause is known; with correct starts the unofficial count is 53%; if the pick list becomes the product, the looser "done" by end of December is about 60%.

## House rules
- One defect per PR, plan first, draft PRs. Claude review (2-round cap plus one short extra) and a PC test before merge.
- Never delete VODs or clips. Never post.
- The paid API key runs only inside the pipeline, under the monthly caps (decision D). Reviews and plans run on Max.
- The user's OK is needed for anything public, deletes, G-DRIVE beyond read-only, paid spend past the caps or new paid API use, and changes to goals, checkpoints or pass marks.

## 1. Main track: detector and ranker quality
The user's steer: "if the detector can just find the right clips, the editing will be a breeze." M1 confirms how much of the loss is picking.

**(a) The 9 Moment=no ranked moments**

| Moment | Box evidence | Cause |
|---|---|---|
| Oct 9 R1 pair, "TWITCH, CLIP THAT SOLO PLAY" / "HEY TWITCH" | The smoke-test pick; both discard; the hook suggests a spoken "clip that" (inference) | Smoke test; rest to confirm |
| Oct 9 R2, R5; Oct 14 R2, R3 | No note; hooks not on the box | To confirm (M1) |
| Oct 14 R5, "NICE, BRO…" | Silent game audio logged (−91 dB) | To confirm (M1) |
| Oct 15 R1 pair, "I DIDN'T KNOW YOU COULD KILL HIM" / "5 AND I KILLED THE DRAGON" | No note; both discard | To confirm (M1) |
| Oct 15 R2 "LEAVE THE BALL", R4 "GET TO THE TREE" | The peak is 4-14 s before the draft start, inside the pick | Editor started late |

**(b) Signals to test,** one at a time, offline:
- **Loudness size.** The ranker only sees "loud spike" or "loud stretch" (`rank_windows.py:127-132, 329-333`). Add dB above the stream's 99th percentile.
- **Peak-centred excerpt.** The excerpt stops at 160 words (`:120`) and can miss the peak. Centre it on the loudest point.
- **Export pre-roll.** DAD's setup started 15 s before the pick.
- **Trigger phrases as ranker cues** (`:133-138`). Behind the gate.
- **Chat.** Not wired today (`detector/config.py:26-27`; `detection_heuristics.py:4` says "from the OBS recording alone"). Live chat logging on the Mac starts before Oct 27 (item 16) so CP3 streams have it. Chat for old VODs is only available through unofficial routes (to confirm).
- **Gemini video+audio.** New paid API use: ask only if triggered, after OI-036.

**(c) Offline evaluation, before any rendering**
- **M1** (read-only, $0, runs now). For each miss, read the pick, the ranker's reason, the detector events, the full-VOD transcript and the rating row. Assign one cause: no real moment, low-energy chatter, wrong peak, duplicate, weak setup, or smoke test. Ask the user about unclear rows (about 2 minutes).
- **M2: the labeled set.** Sources: the CP1 cards, CP2's 15 ranked moments, `frozen_set.json`, later the pick-list ticks. Extend `detector/cp1_replay.py` (`replay` :351, `score_run` :667) to report precision@5, plus recall once ticks exist. The baseline replays from the reply cache for $0 and should reproduce 6/15.
- **M3: signal tests** on the Mac, alongside the PC fixes. About $0.50 per variant for 3 streams on the Mac ranker budget; $5 total cap; reruns from cache at $0. Not through `claude -p` on Max (it changes the request under test). Oct 9, 14 and 15 never supply prompt examples, so the test stays blind.
- **Win rule.** A variant wins only if it gains at least 2 of the 15 moments, loses on no stream, holds frozen-set agreement (14/20), and passes a blind card.

**(d) Tracked CP3 detection target:** top-5 Moment=yes ≥60% on average, no stream under 40%, and no moment the user says was missed.

## 2. Detector end goal (ask when CP3 is scored)
**Recommendation: every clip worth posting, by a quality bar.** Auto-render at most 5 per stream and list the rest.
- **Why.** A fixed count pads dead streams: 11 of CP2's 18 drafts were discards, at about a minute of review and $0.09 plus 3-4 PC minutes each. A bar shows 0-2 drafts on a dead stream; the cap of 5 keeps a great stream inside 15 minutes, and its extras go to the pick list and bank for slow weeks. The target is 6-7 postable a week (Opus call 2), about 2 per stream at 3-4 streams a week.
- **Triggers and rage clips** stay outside the bar and the pass marks, each with its own review cap.
- **Scoring.** Precision is the Moment=yes share of what's surfaced. Recall is the share of the user's picks that the system surfaced; a tick outside the auto set is a miss. Opus call 1's honest "nothing strong tonight" fits.
- **What it needs.** The ranker only orders candidates and forbids numbers (`rank_windows.py:31-33`). It would need a "worth posting: yes/maybe/no" label, tested offline first (item 28). The Oct 20 review proposed "only grade 4 and up" after CP2 (its decision 6).

## 3. Backup plan: user picks from a candidate list
- **Exists already.** The ranker orders every candidate with a one-line reason (`rank_windows.py:1-27`): up to 24 main picks, 40 overflow, and the scout's finds. `export_picks --top` defaults to 5 (`export_picks.py:78, 493`) and stream-copies (`:314-321`). `cp1_replay cards` (`:490`) builds blind cards. Needs_Your_Review, the checklist and the ratings writer are in place.
- **Hybrid (for CP3).** The auto top 3-5 render as today. Ranks 6-20 plus 2 random lower ranks go into a "more candidates" checklist with quote, reason, thumbnail and an 8-second preview. Ticked rows render. Target ≤3 minutes per stream on the PC, inside the 15-minute review.
- **Cost.** Previews are ffmpeg on the Mac after OBS closes ($0 API), about 100-150 MB of Dropbox per stream (estimate; thumbnails only about 2 MB). Pick-first would save about $0.25 and 10 PC minutes per stream.
- **Labels.** Every tick and rating feeds M2; about 15 labels per stream gets the ~100 the Oct 20 review wanted in about 7 streams.
- **Switch to pick-first** (ask only if triggered), after CP3 is scored, if any holds: top-5 Moment=yes under 50% on average; 2+ streams under 40%; the user ticks 2+ auto-set misses per stream on average; M3 finds nothing that beats 6/15.
- **Fit.** The hybrid stays hands-off because picking is optional. Pick-first is the Dec 4 stop rule ("the 2-minute phone pick is the product", `vault/CLAUDE-BRIEF.md`), brought forward only on the trigger.

## 4. Start too late: the look-back guard and full-VOD words (PC)
**Root cause.** The editor's per-clip transcript has no words for shouts and laughs, so it treats the peak as silence (`editor/windows_editor_skeleton.py:1581-1588`). The thin path keeps the late start (`editor/thin_path.py:169-181`). Late starts are the main problem on 5 of the 7 needs-work drafts, the ones closest to postable.
- **PR 1: look-back guard (thin path only), right after no-idle 3a.** If an audio spike or a wordless loud span falls within 20 s before the planned start, move the start to 2 s before it. At most 30 s back, never before the pick start. PC only, $0 on cached plans.
  - **Test bar: BALL at −14 s or earlier, and the locked clips stay green.**
  - What the guard can't do, per the preroll numbers: BRO lands about −12 (its offset is 18.3), TREE about −6 (12.3); RUN likely doesn't move (only a video burst precedes it); DAD can't go earlier than the pick start.
- **PR 2: full-VOD words for the editor** (root-cause fix). Fill loud gaps with the ranker's mlx-whisper words, which are timed only to ±1-2 s, so gap-fill only. Re-plans cost about $0.60 for the 7 drafts.
- **Export front pad, ~15 s,** so DAD's setup (before the pick window) is reachable.
- **7-draft bar, only after PR 2 plus the front pad.** Re-plan only, no render. Each start lands at or before its latest-start offset: 17.2, 12.3, 9.4, 44.1, 18.3, 24.9 and 8.0 s. ROBOT (old path, needs 44 s) stays out of reach. Locked clips stay green.
- **Follow-ups.** Dead air: after CP3, at most 1 reasoned cut, blind-tested. Thin stays the only path for new plans; old-path pairs stop; clips 01 and 14 stay on the old path.

## 5. OI-058 triggers, always-clip and the rage collection (decision B)

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
| WHAT ARE YOU DOING | already a trigger (`shared/spoken_triggers.py:178`) | no | yes |
| WHERE ARE YOU | already a trigger (`:177`) | no | yes |
| I suck I suck I suck | already a trigger; fires on 2+ repeats (`:38`) | no | yes |

- **Scream triggers go to the rage collection only.** "What are you doing" and "where are you" likely fire constantly in team games.
- **Auto-demote:** a phrase that fires more than twice a stream drops to a ranker cue. "Oh my god" will probably trip it. This avoids a second ask.
- **Rules.** Triggers are clipped separately from the ranker's best 3-5; every rage occurrence goes to its own collection; neither lane counts toward the pass marks.
- **Matching** on the Mac's full-VOD transcript, exact tokens (`spoken_triggers.py:34, 127-140`). Loudness may sort rage clips, never gate them.
- **Order.** New streams need the OI-059 wrapper or Fix B first. Measure fire rates before building. Close the thin path's banned-line gap first: `exclude_banned_speech` (`content_generator.py:5269`) runs only on the old path (`windows_editor_skeleton.py:519`).
- **Detector version.** New kinds bump `DETECTOR_FEATURES_VERSION` (now 3) and need the Mac test run (AGENTS.md rule 8).
- **Rage clips** are stream-copy cuts at $0 API, in `Videos\Rage_Collection\<date>` (Proxy + Claude). The compilation comes later, planned first, never posted.

## 6. Cost per clip after Max
- **Baseline.** $0.089 per draft (17 after the smoke) or $0.105 (all 18). Ranker $0.12-0.23 per stream.
- **Target.** ≤$0.10 per draft; ≤$1 per stream for the auto set; ≤$2 per stream with triggers and picks (the CP4 mark, decision C). Rage clips and previews $0.
- **Caps.** About 17 streams a month costs $17-34. October has about $1.10 of PC room left (decision D).
- **Max credit.** About $100 a month of API credit from about Oct 28, once linked to the one org holding both keys.
- **Editor model.** The code default is Sonnet (`editor/config.py:80, 196`). The "Opus" stamp is probably the ranker's: `render_picks.py:556-557` copies `pick.get("model")`, filled by the ranker (`export_picks.py:358`). **Confirm (prep, runs now):** load `.env` as render_picks does (`review_inbox.py:940-945`); print only `config.claude.model`, `trends_model`, and yes/no for whether `CLAUDE_MODEL` was set. Never print the key.
- **Cost cuts, in order.** (1) Per-call usage log (`shared/llm_cost.py:588`). (2) Malformed-answer retry fix: 7 drafts retried (`content_generator.py:13990-13999`). (3) Cached trends 72-168 h instead of 24 h (`config.py:83, 199`; Proxy + Claude). (4) Leaner editor, blind-tested. (5) Environment preflight, which also stops the paid face-location fallback (`content_generator.py:13846-13875`).

## 7. Reliability
- **No-idle v3** (referenced, not redone): 3a → 1 → 2 → 3 → 4 → 5 → 7 → 6 → O1. 3a fixes the CLAUDE_OFFLINE leak (`scripts/run_tests_pc.ps1:63-65`); PR 4 makes cost_check load `editor/.env` (`render_picks.py:258-279`). PRs 5, 7, 6 and O1 belong to the CP4 build.
- **watcher.lock flake** (`detector/test_auto_start.py:1433`), failing about 25-50% of PC runs.
- **Heartbeat.** The runner has 20 minutes (`run_tests_pc.py:30`). Add a 60-second heartbeat, and the same in `run_one.ps1`, which lives on the PC, not in the repo. Check for the missing `cublas64_12.dll` at the same time.
- **Oct 14 wrong Python.** A preflight that refuses to render when `rapidocr` or `cv2` won't import.

## 8. CP3 and CP4 (decision C)
- **CP3.** Fresh streams from Oct 27, by one command, before the OI-036 overview. Postable = ready or perfect. **Pass: ≥1.5 postable per stream on average over ≥3 streams.** Tracked alongside: the 1(d) target, pick-list recall, late starts, review minutes, cost. Ranker and editor frozen during CP3. The Oct 20 "done criteria" need hands-off, which won't exist by CP3, so they are not the CP3 mark.
- **CP4.** 2 streams, 0 manual steps, drafts plus a morning report by 10 AM. Cost mark $2 per stream. Built as local launchd (Mac) / Task Scheduler (PC) scripts: the report, automatic scout and rank, then the overnight render (no-idle 5, 7, 6 + O1). This is also the migration off the box.

## 9. Renewals (decision E)
Grok Bot Pro+ renews Nov 12. Claude Max ends Nov 21.
- **Today:** turn off Grok auto-renew (the user's call; it can be undone).
- **Oct 23-Nov 2:** no migration work. Build any new automation on the Mac/PC, not the box.
- **Nov 3-9:** migrate, capped at 2 days (Tailscale/SSH, flock, run_pipeline, CLAUDE.md files, memory export). Run at least one CP3 stream locally, with Grok as fallback.
- **Nov 10 go/no-go:** if the local run worked, let Grok lapse Nov 12. If not, renew one month; $60 beats a broken CP4.
- **Nov 18:** renew Max 5x for one month. Pro limits during CP4, right after losing Grok, is the wrong week to save; the $60 Grok saving mostly covers it.
- **Dec 4 stop check:** if the project continues, move to Pro on Dec 21. Go back to Max if the limit is hit more than twice a week (tooling.md's rule).
- **Realistic.** Before Nov 12: fixes merged, M1-M3 in, CP3 probably scored. Before Nov 21: a CP4 run likely; the backlog target (success rate) about 50/50.

## 10. The queue
Format: item — machine · OK needed · runs after. v1 numbers in brackets. The PC runs one heavy job at a time, never while the user is live.

**Runs now (read-only, $0)**
1. M1: classify the 7 misses — Mac + PC · — · none [v1 3]
2. Confirm the editor model — PC · — · none [v1 2]

**Waits on the user's A-E answers**
3. Turn off Grok auto-renew — the user · E · none [new]
4. List what depends on the box (read-only) — box · E · none [new]
5. Measure trigger fire rates — Mac, $0 · B · none [v1 4]
6. Link the Max API credit (~Oct 28) — the user's billing · user · none [v1 5]
7. PC cleanup leftovers — PC · user OK per item · none [v1 6]
8. watcher.lock flake fix — box→PC · test-only · none [v1 7]
9. No-idle v3 PR 3a — box→PC · Proxy + Claude · none [v1 8]
10. Start fix PR 1, look-back guard — box→PC · Proxy + Claude · 9 [v1 11]
11. Start fix PR 2, full-VOD words, plus the ~15 s export front pad — box→Mac+PC · Proxy + Claude · 10 [v1 14]
12. M2: labeled set, eval tool, baseline — box→Mac · Proxy + Claude · none [v1 12]
13. M3: offline signal tests, alongside the PC fixes — Mac · within the $5 cap · 12 [v1 19]
14. OI-059 Mac prep and transcription wrapper — Mac · already approved · never during streams [v1 20]
15. Close the thin path's banned-line gap — box→PC · Proxy + Claude · 11 [v1 18]
16. Live chat logging, before Oct 27 — Mac · A, Proxy + Claude · none [v1 26]
17. Test-runner heartbeat and timeout — box→PC · test tooling · 9 [v1 9]
18. No-idle v3 PRs 1→2→3→4, then the wrong-Python preflight — box→PC · Proxy + Claude · 9 [v1 13]
19. Usage log, then an editor-model stamp — box→PC · Proxy + Claude · 2, 18 [v1 15]
20. Malformed-answer retry fix — box→PC · Proxy + Claude · 18, 11 [v1 16]
21. Cached-trends default — box · Proxy + Claude · 19 [v1 17]

**Behind the gate (A = yes)**
22. Post-pack docs PR — box · A · none [v1 10]. Point `vault/Jobs/post-pack.md:5` at the PC's `scorecards.csv`: rows with `outcome` ready or perfect, newest per clip by `written_at`, draft found by `file` + `stream_date`, read as utf-8-sig, flagged rows skipped; fix the ratings_writer text and review-batch step 2.
23. Merge a winning ranker change, frozen for CP3 — box→Mac · A · 13 [v1 22]
24. New trigger kinds and ranker cues — box→Mac · A + B · 5, 14 [v1 23]
25. Always-clip pin, separate from the top 3-5 — box→Mac+PC · A + B · 15, 24 [v1 24]
26. Rage collection, then the compilation plan — box→Mac+PC · A + B · 24 [v1 25]
27. Hybrid candidate list — box→Mac+PC · A, Proxy + Claude · 14 [v1 28]
28. Quality-bar label, tested offline; merge after CP3 — box→Mac · A; goal asked at CP3 · 12 [v1 27]
29. CP3: new-stream top picks by one command — box→Mac+PC · C · 11, 14, 15, 23, 27 [v1 29]
30. CP4 build as local launchd / Task Scheduler scripts (the migration) — Mac + PC · A + E · 18, 29 [v1 34]
31. CP4 on 2 streams; pick-first only if triggered — PC + Mac · ask if triggered · 30 [v1 35]
32. Leaner editor and local models; dead-air cut — box→PC · A, blind tests · 19, CP3 [v1 33]
33. OI-036 overview, then the backlog once the target holds — Mac + PC · user OK · main track, Fix B, OI-022 [v1 36]
34. Gemini blind test — ask if triggered (new paid API) · 33 [v1 37]

**Cut, pending renewal decision E:** shared rulebook and overlap check [v1 30]; Float read-only trial [v1 31]; Clip Renders upgrades [v1 32]. Kept from them as a single editor prompt line: "never invent a quote, speaker or timestamp."

## Decisions for the user (5)
- **A.** Lift the call-6 freeze; dreaming stays log-only. One-in-one-out for Decisions lines and the 2-round review cap stay. *Default: yes.*
- **B.** Approve the trigger list (§5) with the auto-demote rule (more than 2 fires a stream → ranker cue only). Scream triggers go to the rage collection only. *Default: yes.*
- **C.** CP3 runs on fresh streams from Oct 27, before the OI-036 overview. Postable = ready or perfect. Pass: ≥1.5 postable per stream on average over ≥3 streams. CP4 cost mark: $2 per stream. *Default: yes.*
- **D.** Monthly caps from now: PC $20, Mac $10 (October has $1.10 left). *Default: yes.*
- **E.** The renewal plan in §9: Grok auto-renew off today, migrate Nov 3-9, go/no-go Nov 10, renew Max 5x Nov 18, Dec 4 stop check, Pro from Dec 21 if continuing. *Default: yes.*

**Ask only if triggered**
- The quality-bar end goal (§2), when CP3 is scored.
- The pick-first switch (§3 trigger).
- Any deletion. Default: delete nothing.
- Gemini (new paid API).

**Proxy + Claude decide** (after Nov 12, Claude alone, with a decision log)
- v1 1: the fix-lane build OK (item 30, the CP4 build, is out of it).
- v1 6: build the hybrid candidate list.
- v1 7: the pick-first switch trigger as written.
- v1 10: live chat logging.
- v1 13: the rage folder `Videos\Rage_Collection\<date>`.
- Cached-trends default.
