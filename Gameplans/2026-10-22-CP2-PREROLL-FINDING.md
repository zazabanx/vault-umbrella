> Copy of `CP2-PREROLL-FINDING-2026-10-22.md` (box handoffs), added 2026-10-22. Read-only CP2 analysis. See [[Roadmap]]. Text below is unchanged.
> Note: a slur quoted from stream audio is masked in this copy.

# CP2 pre-roll finding: "moment right before" drafts (2026-10-22)

This is a read-only analysis. Nothing was rendered, and no rating, checklist, key or G-DRIVE file was changed.
**The official CP2 score stays exactly as it was rated at 10:10 PM ET: PASS, 40% Moment=yes per ranked moment on Oct 9, Oct 14 and Oct 15 (2 of 5 each).**

Sources (read only):
- PC `%USERPROFILE%\.auto-clip\ratings\scorecards.csv` (18 rows) and the checklist copies in `%LOCALAPPDATA%\Temp\grokbot-cp2\checklists-cp2\`
- PC `.auto-clip\track1\cp2\<date>\.key\cp2-key.json`, `render-picks-*.log` and `track1\cp2\render-2026-10-15-1945.log`
- PC `Videos\RL_Clips\<date>\*.json` (pick sidecars) and `Videos\RL_Clips_Output\<clip>\` (`*_post.txt`, `last_generate_raw.json`, `*_transcript.json`, `.srt`)
- Mac `~/.auto-clip/track1/cp1/2026-10-21/replay.json` (ranker order and reasons). This file names the transcript the ranker used: `~/.auto-clip/scout-replay-2026-10-21/<stem>.transcript.json`, a full-VOD mlx-whisper large-v3-turbo transcript. A copy also sits in `~/Movies`.
- Mac `~/Movies/clip_candidates/<date>/<stem>/<stem>.detect.json` (events, 5 s `audio_delta_db` grid, candidates) and `<stem>.scout.json`

## Verdict mapping
`editor/ratings_writer.py` maps the verdicts like this: **1 = discard**, 2 = needs work, 3 = ready, 4 = perfect.
So "Verdict 1" means **discard**, not needs work. The two drafts this section is about are stored as `Verdict=discard` (`verdict_raw __discard__`), which is consistent with the user rating them "1". No row in the CSV has Verdict=needs work together with Moment=no.

## 1. The "moment right before" drafts

**Inclusion rule:** Moment = `no`, AND the Note or Main problem contains one of: start, earlier, before, missed, (too) late, residual.

| Stream | Hook | Rank (path) | Verdict | Moment | Note (verbatim) |
|---|---|---|---|---|---|
| 2026-10-09 | none | n/a | n/a | n/a | No Moment=no row has any note or problem text. All 4 Moment=no drafts are blank. |
| 2026-10-14 | none | n/a | n/a | n/a | No Moment=no row has any note or problem text. All 3 are blank. |
| 2026-10-15 | **CAN YOU JUST LEAVE THE BALL, BRO?** | R2 (thin) | discard (1) | no | "earlier start might have captured a moment, this clip is the residuals of the potentially clippable moment" |
| 2026-10-15 | **WE HAD ONE JOB: GET TO THE TREE** | R4 (thin) | discard (1) | no | "earlier start might have captured a moment, this clip is the residuals of the potentially clippable moment" |

**Borderline rows.** These are not in the list because Moment=yes, but they show the same late-start pattern and are used below as evidence for the start offset:

| Stream | Hook | Rank (path) | Verdict | Moment | Main problem | Note (verbatim) |
|---|---|---|---|---|---|---|
| 2026-10-09 | THAT WAS THE RUN, DUDE | R3 (thin) | needs work | yes | start | (blank) |
| 2026-10-14 | THE ROBOT'S RECOIL KNOCKED ITSELF OUT, BRO | R1 (old) | needs work | yes | start | "needs earlier start, some cuts for dead air/punchlines" |
| 2026-10-14 | WHY DID BRO FALL OVER? | R1 (thin) | needs work | yes | start | "needs earlier start" |
| 2026-10-14 | HIS TAG SAYS DAD, WE'RE ALL DOOMED | R4 (thin) | needs work | yes | start | "needs earlier start for context" |
| 2026-10-15 | I'VE BEEN PUNISHED FOR MY SINS | R3 (thin) | yes | yes | start | "begins too late (by 8 seconds), ends too early(maybe able to pull funny lines from the following 1-2 minutes), could use more total length of moment and cuts to trim dead air and make a full clip" (the CSV outcome for this row is `unclear` / `not understood`) |

The other Moment=no rows have no note, so there is no evidence either way about the start. On Oct 9 these are R1 old and thin, R2 and R5. On Oct 14 they are R2, R3 and R5. On Oct 15 they are R1 old and thin.

## 2. Secondary view: NOT THE OFFICIAL SCORE
This view re-counts the two Oct 15 drafts as "right area, late start". The official CP2 score is unchanged.

| Stream | Official per ranked moment | Secondary per ranked moment | Official per draft | Secondary per draft |
|---|---|---|---|---|
| 2026-10-09 | 2/5 = 40% | 2/5 = 40% | 2/6 = 33% | 2/6 = 33% |
| 2026-10-14 | 2/5 = 40% | 2/5 = 40% | 3/6 = 50% | 3/6 = 50% |
| 2026-10-15 | 2/5 = 40% | **4/5 = 80%** (R2 and R4 added) | 2/6 = 33% | **4/6 = 67%** |
| All three | 6/15 = 40% | 8/15 = 53% | 7/18 = 39% | 9/18 = 50% |

## 3. Per-draft check: what happened in the 60 s before the draft start
Every time below is a VOD time (h:mm:ss) from the ranker's full-VOD transcript. A negative number is seconds before the draft's first frame.
Draft window = pick start + the variation's in-clip start and end, from `*_post.txt` and `last_generate_raw.json`.
Detector context for both streams: Oct 15 `spike_threshold_db` is 8.22 and the stream's p99 active delta is 13.56 dB.

### 3a. 2026-10-15 R2, "CAN YOU JUST LEAVE THE BALL, BRO?"
- **Pick (ranker and export):** 6589.0-6670.0 (1:49:49-1:51:10)
- **Draft v1 "full-rant":** in-clip 50.5-82.9, which is VOD **6639.5-6670.0 (1:50:39.5-1:51:10)**. That is 50.5 s after the pick start.
- **Ranker reason:** "Clear Rocket League swing: 'it's over', then 'Oh shit, I'm him! The greatest to have ever done it.' A genuine reaction any viewer gets; the teammate rant runs a bit long." The ranker picked the "I'm him" swing, and the draft starts **after** it.
- **Transcript in the prior 60 s:**
  - 1:50:00.6 (-38.9) "Yeah, I don't know either, dude." / 1:50:02.0 (-37.5) "I shouldn't have gone for that." / 1:50:03.0 (-36.5) "Fuck me." / 1:50:03.5 (-36.0) "It's over."
  - 1:50:05.8 (-33.7) "Wow." / 1:50:08.7 (-30.8) "Wow."
  - 1:50:22.3 (-17.2) "Ooh." / 1:50:25.3 (-14.2) "Oh, shit!" / 1:50:28.3 (-11.2) "Oh, shit, I'm him!"
  - 1:50:30.8 (-8.7) "The greatest to have ever done it." / 1:50:32.8 (-6.7) "The greatest to have ever done it, dude." / 1:50:35.1 (-4.4) "You're looking at the fucking Rewas of Champ 3, bro."
  - 1:50:38.2 (-1.3) "Holy fucking shit, what a save." The draft opens here, and the rest of the draft is the rant.
- **Detector:** `audio_spike` at 1:50:27.5-1:50:30.5 (-12.0 s), +14.1 dB over baseline, strength 0.79, above the stream's p99. The 5 s grid at -14 s is **+14.12 dB**, the highest value in the 60 s window. The grid at -30 and -24 s is about -45 and -35 dB (a quiet gameplay gap).
- **Why the editor skipped it:** the per-clip editor transcript (`*_transcript.json`, re-transcribed on the PC) has **no words from 19.7 s to 51.1 s in-clip**. The render log says: "Loud audio with no words in the transcript (laughs, airy words?) at: 35.38-35.88s, 37.82-39.4s, 40.16-43.44s, 44.04-45.04s, 45.92-46.46s, 46.52-47.62s, 48.78-49.42s, 49.92-50.42s". In VOD time that is 1:50:24.4-1:50:39.4, exactly the "Oh shit, I'm him / greatest to ever do it" run. The plan then says it "skips ... the silent 20-34 s stretch" and starts at 50.5.
- **Judgment: YES.** A comeback hype peak with a clear setup sits inside the pick window but before the draft start. The setup is "It's over" (-36 s). The payoff is "Oh shit, I'm him! The greatest to have ever done it" (-14 to -4 s), and it lines up with the loudest detector spike in the window.
  - Latest start that catches the moment: about **-17 s** ("Ooh", 1:50:22). A start at -14 s ("Oh, shit!") works at a minimum.
  - Start with the full setup: about **-38 s** (1:50:02).

### 3b. 2026-10-15 R4, "WE HAD ONE JOB: GET TO THE TREE"
- **Pick (ranker main segment):** 20500.0-20719.5 (5:41:40-5:45:19.5). The detector score is 77.38, confidence 0.99, with signals audio_spike, spoken_what_are_you_doing and sustained_audio.
- **Draft v1 "sidetracked":** in-clip 103.4-157.2, which is VOD **20603.4-20657.2 (5:43:23.4-5:44:17.2)**.
- **Ranker reason:** "Bug comedy: 'Am I invisible now? Can you see me?' ..." This is the clip's ending. The editor instead skipped "the invisible-bug ending because it is a rambling bug report with no punchline".
- **Transcript in the prior 60 s:**
  - 5:42:22.8 (-60.6) "Okay, okay, Vietnam, Vietnam." / (-59.2) "Let's go get them." / (-58.3) "Let's go intervene, dude."
  - 5:42:34.7 (-48.7) "These guys have clubs just like me, dude." / (-46.0) "This is my kinfolk, dude." / 5:42:42.6 (-40.8) "Oh, my God."
  - 5:42:44.1 (-39.3) "What's the name of our group?" ... (-35.5) "i'm the only one who came up with with a scripted lower for my character"
  - 5:42:57.0 (-26.4) "did you die did he die oh i got a shield i got a rickety shield bro"
  - 5:43:11.1 (-12.3) "try to hit me see if you can do any damage i got this shield now"
  - 5:43:18.4 (-5.0) "HAHAHAHA" / 5:43:21.0 (-2.4) "HAHAHAHA" / 5:43:22.9 (-0.5) "YOOOOO"
  - 5:43:23.4 (0.0) "What the hell?" The draft opens here with "Why are you in the way? What are you doing?"
- **Detector:** `audio_spike` at 5:43:19.5-5:43:21.5 (-3.9 s), +14.7 dB, strength 0.81. The grid at -3 s is **+15.46 dB**, the peak of the whole 60 s window and above the stream's p99 of 13.56. The grid at -8 s is +10.93 dB. `sustained_audio` covers 5:43:00-5:44:00 (strength 0.68).
- **Why the editor skipped it:** the per-clip transcript has no laugh words. The render log flags "Loud audio with no words ... at: 101.54-102.02s, 103.94-105.2s" (VOD 5:43:21.5-5:43:25.2), right on the cut.
- **Judgment: YES.** The real beat is the "rickety shield" dare: he gets the shield (-26 s), says "try to hit me, see if you can do any damage" (-12 s), then bursts into a laughing fit and "YOOOOO" (-5 to -0.5 s, the window's audio peak). The draft opens on the tail of it ("What the hell? Why are you in the way?"), which matches the user's "residuals" note.
  - Latest start that catches the moment: about **-12 s** (5:43:11).
  - Start with the full setup: about **-26 s** (5:42:57).
  - Caveat: what happens on screen (who hit whom) was not verified, because no frames were checked and nothing was rendered.

### 3c. Borderline Moment=yes start-problem drafts (evidence only)

| Stream / hook | Draft start (VOD) | What is in the prior 60 s | Latest start that catches the beat | Start with full setup | Detector |
|---|---|---|---|---|---|
| 10-09 THAT WAS THE RUN, DUDE (R3) | 1:41:36.4 | (-19.8) "i got two pots left yeah we're going nice"; (-9.4) "good good good"; (-2.5) "Oh no fire. Oh, I just used"; the payoff "that was the run" at +3 is already in the draft | about -9 s | about -20 s | video_burst at -19.9 s; audio_spike at +3.6 s (+14.0 dB) |
| 10-14 THE ROBOT'S RECOIL... (R1 old) | 1:31:41.3 | (-75.4) "what the fuck"; (-66.0) "That poor guy dude!"; (-44.1) "Yo! That is fucking... hilarious ..."; (-31.8) "...oh man that's good bro this is a clip bro this is a clip"; the draft opens on the follow-up "Why is he on the ground like that" | about -44 s | about -75 s | audio_spike at -35.8 s; video_bursts at -60, -37, -34 s |
| 10-14 WHY DID BRO FALL OVER? (R1 thin) | 1:31:15.5 | (-49.6) "what the fuck"; (-40.2) "That poor guy dude!"; (-18.3) "Yo! That is fucking... hilarious"; (-5.9) "this is a clip bro" | about -18 s | about -50 s | audio_spikes at -38.0 and -10.0 s |
| 10-14 HIS TAG SAYS DAD... (R4) | 2:31:20.0 | (-24.9) "Actually a r***** for a teammate, bro." (-23.0, repeated); then silence until the draft | about -25 s | about -25 s | audio_spike at -25.0 s, +15.8 dB (strength 0.91). **This setup is before the pick window** (the pick starts at 2:31:10) |
| 10-15 I'VE BEEN PUNISHED FOR MY SINS (R3) | 6:29:07.0 | (-19.5) "Oh, dude." (-16.6) "Dude." (-14.1) "Look at that."; the user says "too late by 8 seconds" | -8 s (the user's number) | about -14 s | grid +10.6 and +11.4 dB at -22 and -17 s |

## 4. Start-window / pre-roll finding for the post-CP2 plan

**How far back the real moments started.** This covers all 7 late-start drafts: the 2 primary drafts plus the 5 borderline ones.
- **Latest start that still catches the beat:** 17.2, 12.3, 9.4, 44.1, 18.3, 24.9 and 8.0 s. **Median 17 s, range 8-44 s.**
  - The two primary drafts alone: 17 s and 12 s (median about 15 s).
- **Start with the full setup:** 37.5, 26.4, 19.8, 75.4, 49.6, 24.9 and 14.1 s. **Median 26 s, range 14-75 s.**
  - The two primary drafts alone: 38 s and 26 s (median about 32 s).

**Where the time is lost.** In 6 of the 7 drafts the missed beat is **inside the ranker's pick window**. The editor chose a later in-clip start (R2 starts 50.5 s into the clip, R4 starts 103.4 s in). Only DAD has its setup before the pick window, 15 s before it.

So the main problem is the editor's start choice, not the ranker window. Two causes show in the data:
1. **Transcript gap.** The editor re-transcribes each clip, and that per-clip transcript dropped the loud, shouted or laughing lines ("Oh shit, I'm him!", "HAHAHAHA", "YOOOOO"). The ranker's full-VOD transcript has them. The editor then treats the hype peak as silence or dead air. Its own warning ("Loud audio with no words") fired on exactly those spans in both primary drafts.
2. **No look-back.** No rule stops a start from landing just after the strongest audio event in the window. In both primary drafts, the 5 s grid peak of the prior 60 s sits 3-14 s before the cut.

**Suggested changes to test.** These are proposals only: nothing was changed, and none of them affect the CP2 score.
- **A. Look-back guard (editor):** if a detector `audio_spike` (≥ the stream's spike threshold), or a "loud audio with no words" span, falls within **20 s** before the planned start, move the start back to about 2 s before that event's onset, capped at 30 s and at the pick start.
  - On this data it fixes LEAVE THE BALL (spike at -12 s, so the start moves to about -14 s), DAD (needs the pick window widened), and the ROBOT thin draft (spike at -10 s).
  - It only partly fixes TREE: the spike at -4 s catches the laugh but not the "try to hit me" dare at -12 s.
- **B. Default pre-roll / start-window floor:** never start a draft more than about 20-25 s after the first voiced line inside the pick unless that stretch is truly silent. Alternatively, give the planner a default **pre-roll of about 15-20 s** to trim from instead of a hard start.
  - A 20 s look-back covers 5 of the 7 latest-start offsets. 25 s covers 6 of 7. Only ROBOT old (44 s) is left out.
- **C. Feed the editor the ranker's full-VOD words** for the pick span, or merge them into the per-clip `*_transcript.json` where the clip transcript has loud-no-word gaps. That way the hype lines can be seen and quoted.
- **D. Export:** widen picks by about 15-20 s at the front (the DAD case: the setup is 25 s before the draft and 15 s before the pick start).
- **How to test (no rating change):** re-plan only, with no render, for the 7 drafts above under A+C and under B (20 s). Check that the new starts land at or before the "latest start" offsets in the table. Then do a blind re-rate in a later checkpoint.

## What's missing / caveats
- No frames were checked and nothing was rendered, so on-screen events (the save in R2, the shield hit in R4) are inferred from the transcript and audio only.
- The full-VOD transcript segments are coarse, about ±1-2 s against the per-clip word times. For example, "Yo, what the hell" is at 5:43:23.4 in the VOD transcript and 5:43:24.9 in the clip transcript.
- The latest-start and full-setup offsets are this analyst's reading of the transcript. Only PUNISHED has a number from the user (8 s).
- A read-only helper script was written on the Mac at `/tmp/cp2_preroll_probe.py`. It only reads files. No other files were created on the PC or the Mac.
