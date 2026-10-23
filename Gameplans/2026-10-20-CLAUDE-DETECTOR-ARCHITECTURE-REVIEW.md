> Copy of `CLAUDE-DETECTOR-ARCHITECTURE-REVIEW-2026-10-20.md` (box handoffs), added 2026-10-22. Claude's Oct 20 architecture review. See [[Roadmap]]. Text below is unchanged.

**Verdict: the pipeline is sound, but effort is aimed at the wrong problem, and your fear of rule bloat is real and already visible in the editor.**

- **What's sound:** the Mac/PC split, the transcripts, and the test discipline.
- **The weak link:** what decides which moments get clipped. On main it scores loudness, motion and four trigger phrases. It can't tell a good moment from a mediocre one.
- **Where effort has gone instead:** mostly plumbing (locks, folders, vault rules) and polishing the edits of moments that weren't worth posting.
- **No learning:** ratings don't flow back into anything automatically.

You don't need a rewrite. Move the effort to ranking and feedback, and remove rules instead of adding them.

## The system today

- **Finding moments.** `detector/detection_heuristics.py` scores loudness, motion and spoken triggers ("clip that" plus three scream lines). It exports up to 24 clips per stream, while Decisions asks for "a few pure moments, not about 30 a night." On the labeled Oct 9 and Oct 14 clips, its main list holds 6 of the 9 strong moments. You need main plus overflow (192 clips) to get all 9. The good moments are usually in the pile; they just aren't ranked to the top.
- **Ranking.** Nothing ranks by content on main. The Claude judge is draft #16, 38 commits behind main. The transcript scout is draft #78, waiting on the cost guard in #75.
- **Editing.** Claude Sonnet 5.5 picks start, end, cuts and hook. Then a large layer of code reworks its answer (counted below).
- **Infrastructure.** The flow is Mac watcher, feeder, Dropbox (about 1.5 GB), PC puller, then a render you start by hand. No code on main creates `machine.lock`; bots write it by hand. A crash leaves a file nobody may remove, which stalled the Oct 15 batch at 9 of 24.
- **Cost.** Spend is cents per stream: scout about $0.02–0.06, recorded judge runs $0.03–0.34, under a $1 per stream and $10 per month cap. The editor's Sonnet calls sit outside any cost guard I could find.
- **Learning.** None is automatic. `vault/scorecards.csv` is an empty header, and ratings live as prose. `labels.csv` has 31 rows, used only for the recall benchmark. Hook likes and dislikes are hand-copied into `editor/channel_profile.json`.

## Are we over-ruled? Yes in the editor and in project rules; moderately in the detector

**How I counted:**
- Numeric thresholds are module-level CAPITALS constants set to a number, found with ripgrep, plus numeric config fields and numbers in the game-profile JSON files.
- For prompts, I rendered the real planner and cut-check prompts offline for each game. A "directive" is a sentence containing never, must, do not, always, only, at most, at least, keep, prefer, avoid or "no". The planner prompt also gets the channel profile pasted in, which isn't included in those counts.
- Post-model fixers are functions in `editor/content_generator.py` whose names contain trim, cut, guard, fit, restore, snap, clamp, shorten, advance, pad, drop, force, hold, extend or narrow.

These are grep counts, so treat them as close, not exact.

| Where | Count |
|---|---|
| Detector numeric constants | 31 module constants, 19 numeric config fields, 16 lead-in/tail numbers (8 event types) |
| Game profiles (shared by detector and editor) | 55 numbers across Rocket League, Elden Ring and generic |
| Editor numeric constants | 120 (74 in `content_generator.py`, the rest in subtitles, ffmpeg, scene and audio-mask files) |
| Editor planner prompt | Rocket League: 1,337 words, 113 sentences, 42 directives, 16 numeric limits. Elden Ring: 1,897 words, 57 directives, 28 numeric limits |
| Other editor prompt text | Cut-check prompt: 9–10 directives. Channel profile: 7 preferences (296 words) and 3 banned-hook regexes |
| Post-model fixers in the editor | 83 functions; `content_generator.py` is 13,888 lines |
| Behavior switches | 7 in the editor and 8 in the detector; `START_WINDOW` and `FIT_MODE` keep old behavior alive |
| Scout plan v3 | 12 "must/never" lines, about 15 numeric thresholds |
| Judge | Rubric of 203 words; main doesn't load it |
| Project rules | 120 lines in `Decisions.md`, 30 rules and checklist items in `AGENTS.md`, 55 plan files totaling about 184,000 words |

**Rules that conflict or overlap:**

1. **Length has three different sources.**
   - The channel profile says "about 28 s, never over 32 s, err short."
   - Decisions (2026-10-15) says target about 45 s, up to 60 s for a payoff.
   - The code fits to 32 s with a 45 s hard cap.

   The rated references had a median of 43 s. Your notes go both ways ("ends too early", "needs to be about half the length").
2. **The start time passes through four layers.** The detector's lead-in (21 s on audio spikes, 30 s before "clip that"), then the scout's +6/+2 s pad, then the planner's "5–10 s before the payoff, talk bits at most 1.5 s," then code that moves the start to fit and trims leading dead air. A legacy "start at 0 s" prompt is one switch away. Four of the five needs-work notes are about timing.
3. **Cuts contradict each other.** The prompt says "no mid-gameplay jump cut unless it is the only way." But up to 4 cuts are allowed, and the dead-air fitter cuts to reach the 32 s target. That matches your note "too many unnesacery cuts."
4. **There are three hourly caps.** Settings default to 5 per hour, the cap function defaults to 12, and the recording cap is 4 per hour (8–24 total). On top of those sit a total cap, a per-game-section share and a two-piece limit per run. That many caps is what you get without a ranker.
5. **Hook rules overlap.** "Quote him only when absurd," "a hook can be a line he didn't say," three banned regexes, and a liked/disliked list. Tonight's set still has hooks the profile lists as disliked ("WHAT IS THAT POSITIONING", "IS IT LUNCH OR DINNER", "WHO SOLD ME NO PANTS"). Either those drafts predate the rule or the rule isn't followed. The files don't say which, and that itself is the problem: nobody checks whether a rule works.

**Never shown to help.** No threshold has ever been tested against your ratings, because there is no keep-rate metric. The benchmark only checks whether 9 strong moments are still somewhere in the output. That includes the trigger bonuses, the loudness gate, the peak and loudness weights, and the 32 s target. There is also dead weight: an unused Claude model setting in `detector/config.py`, an old placeholder watcher (`mac_detector.py`), and a judge rubric that nothing loads.

**What to simplify or remove:**
- **One length and timing table per clip type** in the game profile (target, maximum, lead-in). Delete the 28/32 s text from the channel profile and the legacy start and fit switches.
- **Let the model choose start and end on word timestamps.** After it answers, the code should only check hard limits: inside the source, snapped to word boundaries, under the hard cap. Default to no cuts; retire the cut-to-32 s fitter. Most of the 83 fixers exist to override the model.
- **Shrink the planner prompt** to the hard limits plus 10–20 rated examples (loved and discarded, with your own notes). Examples replace most of the 42 directives and the hook regexes.
- **In the detector,** replace the stacked caps with "rank everything, keep the top N." Trigger and loudness bonuses become inputs to the ranker, not hand-set weights.
- **Remove the dead code** above.

**Guardrail against future bloat:**
1. **A frozen labeled test set** (Oct 9, 14 and 15 to start) with a scorer that replays picks and edit decisions offline. Every new rule, prompt line or threshold names the clips it fixes. It must improve the test score, or at least not lower it, or it isn't merged.
2. **One in, one out.** Today's counts are the ceiling: planner-prompt words, editor constants, detector caps. Adding one means removing one.
3. **Sunset and ablation.** Every rule carries why, evidence and date. Periodically remove each rule and re-run the test set; if the score doesn't drop, delete it.

Today's 2026-10-14 rule ("change a rule only when it shows up in 2+ postable clips") only limits adding rules. It never removes one.

**What models handle on their own, and where rules help:**
- **Models do well:** judging whether a line is funny, relatable or has a payoff; finding the setup a punchline depends on; ending on the reaction; writing hooks in your style from examples; generalizing from a dozen rated examples. Long rule lists make them drop instructions, so examples beat rules here.
- **Rules help:** timing arithmetic and word snapping; hard length caps; cost caps; facecam and layout geometry; never deleting files; the slur mask; name spellings ("boost" never plural, Dimmy); loudness targets.
- **Inputs, not rules:** what only the video shows. A text model can't see a Rocket League goal, so pass detector events and on-screen cues in as data rather than writing more rules.

## Biggest bottlenecks to clip quality, ranked

1. **Moment choice and ranking.** All 15 discards with a note blame the moment (12 "mediocre," 3 "bad"); the other 13 have no note. Oct 15 produced 26 drafts and none was ready. Some streams may simply have few good moments, and the system should say so instead of padding.
2. **No feedback loop.** The same moment gets opposite ratings: Oct 9 clip 09 was "moment 4–5" on Oct 13 and "mediocre moment" tonight. Nothing records which version was rated.
3. **Start and end timing,** made worse by the conflicting layers above.
4. **Rule and process bloat:** 83 fixers, 120 Decisions lines, 19 open PRs.
5. **Edit details:** cuts, and subtitle timing (#33 failed the phone check).

## Alternatives, with tradeoffs

- **A transcript-first Claude ranker as the main picker,** with the heuristic as a candidate source. Cheap. It can miss wordless plays unless detector events go into the prompt.
- **Pick before render.** You tick 2–3 of about 10 one-line cards per stream. Highest keep rate for the least compute, but less hands-off.
- **A video model judge (Gemini) on the top 5.** It sees gameplay, but costs more. Already parked as a later test.
- **A learned ranker** trained on your ratings. The right end state, but it needs a few hundred structured labels.
- **Off-the-shelf clippers.** Only useful as a comparison point; they won't follow your facecam layout.

## Track 1: short term, raising the keep rate with the current setup (ranked by impact against effort)

1. **Put a content ranker in front of the render, and render fewer clips.** Merge #75 and #78. Replay the scout over the existing Oct 9, 14 and 15 transcripts, ranking the detector's windows and its own finds together. Render only the top 3–5 per stream. Highest impact, medium effort. It needs your OK on the ~$1 benchmark, and on whether those picks may become drafts under the scan hold.
2. **Structured ratings:** moment grade, verdict, one main problem. Near-zero effort.
3. **Simplify timing instead of adding to it.** One length and timing table per clip type, end on the last strong beat, retire the 32 s fitter. Medium effort; the clip 01 and 14 locks must stay green.
4. **Default to no mid-clip cuts.** Low effort.
5. **Freeze plumbing that doesn't block renders.** Keep only the lock-cleaner fix.

Skip for now: more trigger phrases, loudness tuning, and new editor rules.

## Track 2: long term, a detector that keeps improving

- **A labels table written automatically from every review checklist.** Each row: stream, times, version rated, source, features version, moment grade, verdict, main problem.
- **A held-out set** (Oct 9, 14 and 15 frozen).
  - **Main number:** precision at 5, meaning of the top 5 picks per stream, how many you grade a good moment.
  - **Batch number:** keep rate per batch, meaning ready plus perfect over clips rendered.
  - **Success:** the existing bet, 1–2 postable clips per stream, several streams in a row.
  - Rate a few scout-only picks now and then, so the labels aren't only clips the detector already exported.
- **Re-tuning on that set.** Test new prompt and example versions and keep a change only if the score improves. Train a small ranker once 50–100 rated clips exist (the existing energy rule), and more seriously at a few hundred.
- **Architecture:** heuristic and transcript propose, a ranker that learns picks, render the few, ratings flow back. The editor slims down toward examples plus hard checks.

**Keep:** the Mac/PC split, the Dropbox trickle, transcripts, the PC test runner, the clip locks, the heuristic as a recall net.
**Change:** merge the judge and the scout into one re-ranker; put the editor's Claude calls under the cost guard; give `machine.lock` an owner process plus the approved stale cleaner.
**Drop:** 24 renders per stream; the separate Mac Scout folder (a second review queue off the PC); the hook regexes; legacy switches; plan chains that run to v9 for plumbing.

## How the tracks connect

Track 1's ranker is the same component Track 2 tunes. Its replay results become the first baseline, and the structured ratings are the label format. The Track 1 simplifications (one timing table, no default cuts, a shorter prompt) are the first things the bloat guardrail measures. To avoid undoing work later:
- add ranking without removing candidates;
- put any new limit in the profile tables, not code branches;
- skip the Mac Scout folder delivery;
- treat the loudness gate as one ranker input, not the main lever.

**The one thing I'd ask of you:** on each needs-work clip, note roughly how many seconds early or late the start and end are. That makes timing measurable instead of another rule.