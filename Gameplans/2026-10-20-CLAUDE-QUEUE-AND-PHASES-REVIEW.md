> Copy of `CLAUDE-QUEUE-AND-PHASES-REVIEW-2026-10-20.md` (box handoffs), added 2026-10-22. Claude's Oct 20 roadmap review. Summary and current state: [[Roadmap]]. Text below is unchanged.

# Queue and phases review, 2026-10-20 (written 11:55 PM ET)

> **Your fear:** "My main fear is that this project will not complete its intention and won't give me a reliable auto-clipping pipeline."

## Short version
1. The fear is fair. Today the pipeline makes 0 ready clips per stream. Since Oct 19, 24 of the 26 merged PRs were notes and docs; only 2 were code.
2. "Done" should mean: at least 1 postable clip from every stream, 2 per stream on average, 4 streams in a row, 10 minutes of your review per stream, and drafts waiting by 10 AM with nobody touching anything.
3. The shortest path is Track 1 (rank first, render the top 5, simpler timing). After that, connect the parts so they run on their own. Nothing else is on the path.
4. Pause about 20 queue items. That includes the 7 four-outcomes PRs, the folder guards, the stall alerts, any-game detection, the archive script, the clip-polish rows, and creating the Publishing bot. Pause, not close.
5. Checkpoints: Sat Oct 24 (does the ranker find the good moments?), Fri Oct 30 (rendered picks rated), Fri Nov 6 (new streams), Fri Nov 13 (two hands-off streams), Wed Nov 25 (4 in a row = done).
6. Odds, my honest estimate: about 35% to be done by Nov 25, and about 55% by end of December. The biggest unknown is whether every stream even has 2 good moments.
7. If a checkpoint fails, the fix is never "add a rule." Switch to a stronger model, or have you tick 2–3 one-line cards per stream on your phone before rendering. Or drop any clip that needs more than one re-render.
8. Biggest bloat: 56 plan files (~192,000 words), 9 versions of the four-outcomes plan (61,000 words) for sorting clips into folders, 6 review folders, and 2 Sunday "dreaming" jobs at the same hour.
9. Biggest risks: the editor's paid calls aren't under the spend cap yet. Test runs ran without machine.lock tonight. Mac disk may fill in about 2 weeks of streams. 6–7 bots compete for the same PC hours and your attention.

---

## Part 1. Your fear, answered head-on

### 1.1 What "a reliable auto-clip pipeline" means, with numbers

**What the data says today.** You rated 39 drafts from Oct 9 and Oct 15:
- 0 ready.
- 11 needs work (28%).
- 28 discard (72%).

Every discard with a note blamed the moment ("mediocre moment", "bad moment"), not the edit. On Oct 15 alone, 26 drafts gave 0 ready and 7 needs work. Reviewing 26 drafts takes you roughly 30–45 minutes.

The earlier streams look a little better, but only after many hand rounds:
- **Oct 9:** 3 truly good clips: "I'm literally the best", the controller clip ("My controller killed him, okay"), and "WHY DID I FOLLOW YOU" (the bridge jump).
- **Oct 14:** 1 postable ("SOLAR'S APOLOGY TWEET DID NOT FOOL") and 4 almost, out of 12.

So the good moments exist, but they're buried, and nothing digs them out.

**Proposed definition of done.** All five must hold at once:

| # | Check | Number |
|---|---|---|
| X | Postable clips per stream | **At least 1 on every stream, and at least 2 per stream on average** across the streak. "Postable" means ready to post as is, or needs work that one re-render fixes from a one-line note like "end 4 s later" (or that you can fix yourself in 5 minutes). At least half of them must be ready as is. |
| Y | Streams in a row | **4** (about 1.5 weeks at three streams a week). A miss restarts the count. |
| Z | Your review time | **10 minutes or less per stream.** That's at most 5 drafts, each about 1 minute to watch plus a 3-line rating. |
| H | Hands-off | Drafts plus a "clips ready" message **by 10 AM after a stream**. **0** manual steps by you or a bot. **0** heavy jobs while OBS, a game or Resolve is running (checked in the logs). |
| C | Cost | **$1 or less per stream**, inside the $10 per month cap, with every paid call counted. |

Why these numbers:
- **X:** you said "1-2 postable clips from every stream." A floor of 1 with an average of 2 admits that some streams are thin, without letting the system pad.
- **Y = 4:** "several" is still marked TBD in Decisions. Four is the smallest streak that isn't luck.
- **Z = 10:** a 72% discard rate is what makes review slow today. Ranking is what fixes it.

Today the pipeline passes **none** of the five checks. Hands-off isn't built either: the scan hold is on, there's no auto-render, and there's no alert.

### 1.2 The shortest path

There are only two jobs left that matter:
- **Quality:** pick the right 5 moments and stop over-editing them. This is Track 1.
- **Hands-off:** connect the existing parts so a stream flows to drafts on its own.

**ON the path, now** (Track 1, already approved):
1. Finish and merge the transcript scout (#78).
2. Build the content ranker (Track 1 item T1-2). It grades every detector window and every scout find 1–5 on one list. It replaces the separate judge (OI-034), the Maybe folder (OI-024) and the Mac Scout folder (scout stage S2).
3. Replay the scout and ranker on the Oct 9, 14 and 15 transcripts. Cost is about $0.45 at most.
4. Put the editor's paid calls under the spend cap (T1-3). Merge #83 first.
5. Add one timing and length table, let the model pick start and end on word times, and use no mid-clip cuts by default (T1-6, T1-7, T1-8).
6. Add structured ratings to the checklist: moment grade, verdict, main problem, and how many seconds early or late (T1-5).
7. Render the top 3–5 picks per stream (T1-R3).
8. Fix the flaky test that turns good runs into FAIL (#80).
9. Keep the two approved exceptions: #76 and the lock cleaner. Fold "the test runner takes machine.lock" into the lock cleaner's first PR.

**ON the path, later** (start once the first checkpoint passes, not before):
- Transcribe before detecting (#58's Fix B, OI-002), and #61 (already finished).
- A live hook that runs the scout and ranker after each stream.
- The PC auto-render watcher (OI-003), rendering only the top 5.
- The clips-ready alert (OI-004).
- Lifting the scan hold. That's your decision.

**OFF the path.** Pause these:
- The four-outcomes PRs 1–7 (folder moves), plus PR A, B1 and B2. Folder plumbing for clips that don't exist yet.
- Stall alerts (#77 and OI-029).
- Any-game detection (OI-033).
- The Decisions archive script (#88).
- The loudness gate (OI-022) and the v4 re-score (OI-031 and CR-001).
- Phone review copies (OI-026 and CR-002).
- Polishing individual clips: OI-017, OI-037, CR-003, CR-004.
- The Gemini judge test (OI-025).
- The other-streamers rating round (OI-038).
- The project pack (OI-013).
- Creating the Publishing bot (PX-005).
- The old drafts #16, #18, #25, #29 and #33.

Long-form runs in its own lane. It's not on this path, and it must not take PC time or review time from it (see Part 4).

### 1.3 Dated checkpoints

Assumes you stream Tue, Wed and Thu afternoons and evenings (from the history), and that agents code at the current pace. All dates are ET.

| Date | Checkpoint | Numbers to check |
|---|---|---|
| **Wed Oct 21** | Freeze recorded and finished PRs merged | One Decisions line records Track 1 plus the pauses. #78, #83, #80 and #61 merged, each with a PC SUMMARY PASS. Open PRs go from 16 to 12 or fewer, and every paused one is labeled. |
| **Sat Oct 24** | **CP1: the ranker finds the good moments (replay, no renders)** | On the labeled Oct 9 and Oct 14 moments, at least 3 of each stream's top 5 are known-strong moments, and at most 1 is a known "no". Spend is $0.45 or less. Plus a 3-minute check for you: read the top 10 one-line cards for Oct 15 and tick the ones worth clipping. At least 2 of your ticks should be in the ranker's top 5. |
| **Fri Oct 30** | **CP2: rendered picks, rated** | 9–15 new drafts from Oct 9, 14 and 15 (new windows only), on the new timing path. At least 40% get a moment grade of 4 or 5. At least 2 of the 3 streams have 1 or more postable clips. Your review is 15 minutes or less per stream. Editor spend per clip is measured and under $0.20. |
| **Fri Nov 6** | **CP3: fresh streams** | The Oct 27–29 and Nov 3–5 streams go through the new path, started by one command if hands-off isn't ready yet. That needs your OK to lift the scan hold for them. On at least 3 fresh streams: average 1.5 or more postable per stream, at least 1 on each, and 10 minutes or less of review. |
| **Fri Nov 13** | **CP4: hands-off works** | The Nov 10–12 streams have drafts plus an alert by 10 AM the next day. 0 manual steps, 0 heavy jobs during OBS or games, and $1 or less per stream in the spend ledger. |
| **Wed Nov 25** | **DONE: 4 in a row** | 4 consecutive streams (for example Nov 12, 17, 18, 19) meet X, Z, H and C. If the streak breaks, the next try ends Thu Dec 3. |
| **Fri Dec 4** | Hard rethink date | If done still isn't met, use the pivot in 1.4. Don't add more rules. |

### 1.4 Honest odds, why it could fail, and the pivot for each miss

**Odds (my judgment, not a measurement):**
- About **35%** to meet the full definition by Nov 25.
- About **55%** by end of December.
- About **60%** for a looser version by Nov 25: 1 postable on every stream, 4 in a row, 10 minutes of review.

Ranking is likely to work, because the good moments are in the detector's pile: all 9 labeled strong ones are in main plus overflow. The big unknown is whether every stream has 2 good moments at all.

**Main reasons it could fail:**
1. **Thin streams.** Oct 15 may just not have 2 good moments. No code fixes that.
2. **The ranker reads only words.** A wordless Rocket League play is invisible to a text model unless the detector's events go in as data.
3. **Timing.** Needs-work clips stay needs-work: 4 of the 5 needs-work notes are about start or end.
4. **Attention drain.** The bots keep producing plumbing, plans and notes, and your approvals and the PC's idle hours go there instead (24 of the last 26 merges were docs).
5. **Noisy ratings.** "IS THE BOSS BUGGED OR AM I?" was rated "moment 4–5" on Oct 13 and "mediocre" tonight. Without the version and the grade recorded, you can't measure progress.
6. **Silent stops.** A stale lock (it already stalled the Oct 15 batch at 9 of 24), a hit spend cap, or a full Mac disk stops a hands-off night with nobody noticing.

**Pivot for each missed checkpoint:**

| Miss | What changes | What stops |
|---|---|---|
| CP1 (ranker can't find the known-good moments) | Re-run once with the stronger model (Sonnet; a new spend OK of about $1 or less). Put the detector's events (goal, trigger, loudness peak) in the prompt as data. If it still misses, make the cards the design: you tick 2–3 of 10 one-line cards on your phone (about 2 minutes), and only those get rendered. | No new trigger phrases, loudness weights or caps. |
| CP2, moments good but edits not | Turn needs-work into a one-note re-render ("end 4 s later" goes back to the editor once). | Any clip that needs a second re-render gets dropped. No new editor rules. |
| CP2, moments bad | Same pivot as CP1. Also check whether the stream was just thin: if the cards show nothing good, the stream "passes" with 0 and is reported honestly. | Rendering 24 per stream. |
| CP3 (fresh streams worse than replay) | Ratings from Oct 9, 14 and 15 may have leaked into the prompt examples. Swap in fresh examples from the new streams. | Treating replay scores as proof. |
| CP4 (hands-off breaks) | Fix only the stage that broke. Keep "one command per stream" as the fallback; it's 90% of reliable. | New plumbing features. |
| DONE missed twice (by Dec 4) | Make the cards permanent: a 2-minute phone pick per stream, then hands-off render. It's a fine product and much more likely to hold. Revisit full automation once about 100 structured ratings exist (Track 2). | Editor polishing of individual clips. |

---

## Part 2. Earlier question 1: keep, reorder, pause or drop

KEEP = do it now. REORDER = do it, but later or in a different place in line. PAUSE = stop and leave it open, untouched. DROP = don't build it (the PR or row stays open until you say otherwise).

Tonight's PC runs: every open PR tested **PASS** with only the known failures. #77 and #83 needed one rerun each for the watcher.lock flake, which also fails on main.

### Open PRs (auto-clip-system)

| Item | Current state | Call | Why |
|---|---|---|---|
| #78 transcript scout S1a | Draft, PC PASS at fd048ef (51 scout tests) | **KEEP** | It's Track 1's first step. |
| #83 renormalize makes no paid calls | Draft, PASS on rerun | **KEEP** | Cost safety, and T1-3 builds on it. |
| #76 auto-resume plus `machine_lock.py` | Draft, PASS | **KEEP** | An approved exception. The renders need it. |
| #80 held-lock test flake | Draft, PASS 3 of 3 | **KEEP** | The flake turned 2 good runs into FAIL tonight. Every rerun costs 30–45 PC minutes. |
| #61 transcript_used on the done note | Draft, PASS, code finished | **KEEP (merge as is)** | Zero work left, and it's needed before hands-off. Leaving finished code open only creates rebase work. |
| #58 Fix A and Fix B plan | Draft (plan) | **REORDER** | Fix B is on the hands-off path. Start it after CP1. |
| #77 stall checker | Draft, PASS | **PAUSE** | Plumbing. Revisit at CP4. |
| #88 Decisions archive check | Draft, PASS (7 tests) | **PAUSE** | Decisions.md is 125 lines. Write fewer lines instead (Part 3). |
| #89 person segmentation (Long-form) | Draft, PASS | **KEEP, last detection PR** | Already built and tested. It's used for 1 episode (Oct 15) and adds a 6 MB model file to git. No more detection work after it. |
| #90 breaks.json (Long-form) | Draft, PASS | **KEEP** | The Long-form lane. |
| #91 break report (Long-form) | Draft, PASS | **KEEP** | The Long-form lane. |
| #70 empty facecam (Long-form) | Merged tonight (a9aa562) | done | Nothing left to decide. |
| #16 chat plus two-stage judge | Draft since Oct 13, 38 commits behind | **PAUSE** | The ranker replaces it. Keep it as a parts source. |
| #33 subtitle CTC starts | Draft, failed the phone check | **PAUSE** | An editor rule. Off the path. |
| #29 phone-file retries | Draft since Oct 13 | **PAUSE** | Goes with phone copies (paused). |
| #25 short review names | Draft since Oct 14 | **PAUSE** | Plumbing. |
| #18 rules audit (Oct 10) | Draft, docs | **DROP** | Tonight's architecture review counted the rules more recently and more completely. |

### Approved but unstarted, and Open-Items rows

| Item | Current state | Call | Why |
|---|---|---|---|
| Track 1, T1-0 to T1-8 plus R1–R3 (PLAN-TRACK1-v1) | Plan written, not yet reviewed | **KEEP** | It's the path. Add the 3-minute card check to CP1, before any render. |
| Ranker T1-2 (absorbs OI-034 judge, OI-024 Maybe folder, scout S2 and S3) | Planned | **KEEP** | One component instead of four. |
| Lock cleaner Fix A then Fix B (OI-040, PLAN-LOCK-CLEANER-v6) | Approved | **KEEP, plus one line** | Fix A should also make `run_tests_pc.ps1` take machine.lock. Tonight a second runner didn't. |
| Fix B transcribe-then-detect (OI-002) | Approved | **REORDER** | After CP1. Needed before any hands-off stream. |
| Live scout and ranker hook (scout S1b) | Approved | **REORDER** | After CP1. Simplest form: one call after detection. |
| PC auto-render watcher (OI-003) | Plan v2 on disk | **REORDER** | After CP1. It renders only the top 5. |
| Clips-ready alert (OI-004) | Plan v3 on disk | **REORDER** | After OI-003. |
| Structured ratings (part of OI-027) | Not started | **KEEP (T1-5 only)** | Near-zero effort. The rest of OI-027 waits for about 100 ratings. |
| Detector overview (OI-036) | Due Nov 1–3 | **REORDER, shrink** | Tonight's review plus the CP1 and CP2 reports are the overview. Use those to decide on resuming scans. |
| Four-outcomes PRs 1–7 (OI-039) | Plan v9 approved | **PAUSE** | 0 ready clips today. Renders & Review can do the few moves by hand (SHA-checked, logged) until there are about 10 ready clips a week. |
| PR A path guard (OI-020) | Approved | **PAUSE** | No job touches the protected folders today (Decisions, Oct 20). |
| Optional guard (OI-019) | Duplicate row | **DROP (fold into OI-020)** | The schedule review already said they're the same work. |
| B1 copy on "ready to post" (OI-021) and B2 named copy to Perfect (OI-023) | Approved | **PAUSE** | Same reason as four-outcomes. |
| Loudness gate v4 (OI-022) | Approved | **PAUSE** | On the Track 1 skip list. It returns later as one ranker input. |
| v4 re-score plus 23 renders (OI-031, CR-001) | Waiting (scan hold) | **PAUSE** | The ranker covers Oct 9 and Oct 15. |
| Any-game detection (OI-033) | Approved | **PAUSE** | Revisit at CP4. A simple game list is enough for hands-off. |
| Stall alerts (OI-029) | Plan v3 | **PAUSE** | Revisit at CP4. |
| Phone copies (OI-026, CR-002) | Approved | **PAUSE** | Not on the path. |
| Gemini judge test (OI-025) | After OI-036 | **PAUSE** | It's the pivot if the text ranker misses visual plays. Keep it ready, don't build it. |
| Fix "One missed boost…" and the Oct 14 clips 07/10 (OI-017) | Open | **PAUSE** | Polishing single clips. |
| Bridge-jump subtitle fix (OI-037), "THE ROBOT THREW ONE PUNCH" start (CR-003), controller-clip start (CR-004) | Open, user-gated | **PAUSE** | Polish. These clips are already protected. |
| P3 trigger-vs-loudness report (OI-018) | Open | **PAUSE** | On the skip list. |
| Mac and PC lock report (OI-006) | Open | **KEEP** | 5 minutes. A leftover lock blocks renders. |
| VOD archive plan (OI-011) | Open | **KEEP** | The Mac disk may run short (Part 4). |
| #48 and #49 follow-ups (OI-012) | Open | **PAUSE** | Test and docs plumbing. |
| Project pack (OI-013) | Paused | **PAUSE** | Stays inside auto-clip-system, as you decided. |
| Sunday Claude audit (OI-014) and team dreaming (PX-001) | Two Sunday 11 AM jobs | **REORDER** | Make them one Sunday run (Part 3). |
| Shorts rating round (OI-038), 50 rows | Waiting on you | **PAUSE** | Spend your rating minutes on your own drafts until CP2. |
| Publishing bot (PX-005), due Oct 26 | Approved | **PAUSE until its own trigger** | Its trigger is "first long-form final or approved shorts ready." Neither exists yet, so the Oct 26 date contradicts its own trigger. |
| Long-form LF-002 to LF-009 and LF-012 | Open | **KEEP** | Its own lane. Done means one episode (the Oct 9 re-cut) approved by you. |
| Long-form DaVinci package PR6 (LF-011) | Queued | **REORDER** | After you approve the first final file. |
| Nightly bot-pages refresh (PX-002) | Routine | **PAUSE** | A third summary on top of the daily note and the morning summary. |

---

## Part 3. Earlier question 2: overcomplicated, duplicated, or likely to bloat

1. **Plans that keep growing.**
   - The plans store holds **56 files, about 192,000 words**, plus about 16,000 more in the store root.
   - **Four-outcomes:** 9 versions, about **61,000 words**, to decide which folder a reviewed clip goes in. Today 0 clips are ready.
   - **Lock cleaner:** 6 versions, about 30,000 words.
   - **Decisions archive:** 3 versions (about 8,000 words), plus a 20-line rules section in VAULT-RULES and a 7-test script (#88), all for a 125-line file.
   - Suggested cap: a plumbing plan fits on one page and stops at version 3. If it isn't approved by then, the scope is wrong.
2. **Docs outrun code.** Since Oct 19, **24 vault or docs PRs** merged (#56–#92) and **2 code PRs** (#70 and #75). This is the clearest sign of effort going to plumbing.
3. **Decisions.md:** 125 lines, and **32 of them are dated Oct 20 alone**. Many correct an earlier correction. The Ready_To_Post and Perfect folder rules alone take 6 lines (#64, #65, #66, #68 and two more), and each says what it replaces. Agents have to read the whole history to find today's rule. Suggested rule: one line per real decision, never a line for a clarification. Fix the old line's meaning in Status instead.
4. **Six review folders for 0 ready clips:** Needs_Your_Review, Postable_Needs_Work, Ready_To_Post, Perfect_Clips_Protected, Approved_References and Discarded. Plus the top of Clips_To_Review and its "older versions" subfolders. Four of them have special rules.
5. **Locks and watchers:** machine.lock, watcher.lock, transcribe.lock, the puller lock, the git-pull lock and the spend lock. Lock, idle and stall work is spread over 5 items (#76, OI-033, lock Fix A, lock Fix B, #77 and OI-029, which is 3 PRs). Even so, a test runner ignored the lock tonight. One owner process for heavy PC jobs beats more lock types.
6. **Too many trackers say "what's next":**
   - umbrella Open-Items (63 rows),
   - Status.md,
   - daily notes,
   - each bot page's "Now",
   - SCHEDULE.md,
   - PLAN-TRACK1 Part A.

   Some of them are stale. Status still says #61's "PC tests pending" and "Mac runtime main a8e5a59". AutoClip.md's "Current focus" still lists a review-folder sort that's already done. Keep Open-Items as the only "next" list, and keep Status for facts.
7. **Copies that have drifted:**
   - `vault/_umbrella-draft/` (7 files) still sits in auto-clip-system, but the real umbrella repo exists.
   - The build-loop stamp says v2 on umbrella Home, v1 on the umbrella template, and v3 in AGENTS.md.
   - Umbrella Open-Items says Approved_References holds "Oct 14 clip 14". The lock test is the **Oct 9** controller clip, so that line is wrong.
8. **Split rows for the same work:** OI-019 and OI-020; OI-031 and CR-001; the judge exists three times (OI-034, #16 and T1-2); the Maybe folder (OI-024) versus the ranker; scout S2 versus the ranker.
9. **Routines:** daily note at 11:30 PM, Proxy morning summary at 9:51 AM, bot-pages refresh at 1 AM, nightly drift checks, the PR-review routine, the weekly Claude audit, and **two Sunday dreaming jobs at 11 AM**: auto-clip dreaming (Decisions, Oct 16) and team dreaming (PX-001). That's 3 daily summaries and 2 Sunday ones. Merge the two Sunday jobs into one.
10. **Bots:** 6 today (Proxy, Engineer, Renders & Review, Research, Long-form, Personal), plus Publishing planned, plus Grok Bot doing daily notes and PC tests. The Publishing bot would duplicate the editor's existing Claude "post copy" step (task 4.4 in the game plan).
11. **Code:**
    - **Editor:** `editor/content_generator.py` is 13,888 lines, with 83 fixer functions and 120 constants (from tonight's review).
    - **Long-form:** about 3,100 code lines and 2,800 test lines across 4 PRs just to find breaks in 4 episodes, plus a 6 MB model checked straight into git. The person check is for 1 episode (Oct 15), where ticking breaks by hand would take about 10 minutes.
12. **Open PRs:** 16. Five of them are drafts older than 5 days (#16, #18, #25, #29 and #33).

Guardrail I'd adopt (it matches tonight's architecture review):
- **One in, one out:** a new rule, folder, routine or bot removes one.
- Plans are capped at one page and 3 versions.
- Nothing goes in the queue unless it names the checkpoint it moves.

---

## Part 4. Earlier question 3: the remaining phases in order, with "done" checks

Where things are written down:
- The auto-clip roadmap is `docs/Phase0-Game-Plan.md` (phases 1–7, no dates) plus the hands-off order in Status.
- The build loop is AGENTS.md (`build-loop v3`).
- The Templates and new-product approach is umbrella `Templates/new-product.md` and `Templates/build-or-improve.md`.
- The Long-form roadmap is the LF-001 to LF-013 rows and `Bots/Long-form-YouTube.md`. Its plan files are on that bot's own computer (`/workspace/longform-youtube/plans/`), which I couldn't read.

**Not written down anywhere:**
- a plan for the Publishing bot (only the PX-005 row),
- a number for "several streams",
- a review-time budget,
- dates for the auto-clip phases.

| Order | Phase | Done when (measurable) |
|---|---|---|
| 1 | **Ranking proven (Track 1)**, Oct 21–30 | CP1 and CP2 numbers above. |
| 2 | **Fresh-stream quality**, Oct 27–Nov 6 | CP3: 3 or more new streams, average 1.5 or more postable, 1 or more on each, 10 minutes or less of review. |
| 3 | **Hands-off wiring**, starting after CP1 and finished by Nov 13: Fix B, live hook, auto-render of the top 5, alert, lock owner and cleaner, runner takes the lock | CP4: 2 streams with 0 manual steps, drafts by 10 AM, 0 heavy jobs during OBS or games, $1 or less per stream. |
| 4 | **The streak (product done)**, by Nov 25 | 4 in a row meeting X, Z, H and C. |
| 5 | **Posting starts** (your existing gate) and the **Publishing bot** is created | Trigger: 5 or more clips in Ready_To_Post, or the first long-form final, whichever comes first. Done: you approve the first post pack, and nothing posts without your OK. Reuse the editor's post copy; don't add a second writer. |
| 6 | **Learning (Track 2, not approved)** | Starts at about 100 structured ratings (about 20 streams at 5 drafts each, around mid-December). Done: precision at 5 rises on a frozen test set. Precision at 5 means: of the top 5 picks per stream, how many you grade a good moment. |
| — | **Long-form lane**, in parallel and lower priority on the PC | Done 1: the Oct 9 re-cut `(final).mkv` is approved by you. Done 2: Oct 7, 8 and 15 are approved. Done 3: the DaVinci package imports in Resolve. No upload without your OK. |
| — | **Templates and new product** | Written, but no second product exists, so there's nothing to do. Fix the drifted stamps. The next product uses Claude Code (Decisions, Oct 16). |
| — | **Project pack** | Stays inside auto-clip-system, paused (OI-013). Revisit after phase 4. |

The build loop itself is fine for code (plan, failing test, review, PC run). It's too heavy for docs and vault PRs. Let docs-only PRs skip the plan step.

---

## Part 5. Earlier question 4: risks

**Cost** (caps: $1 per run, $10 per month, $0.25 for the scout):
- The editor's Sonnet calls aren't under the cost guard yet, so the $10 cap doesn't see them. T1-3 must merge before any Track 1 render.
- The month ledger has never seen October's earlier editor spend, so it reads low.
- Nobody has measured editor cost per clip. If it's around $0.10 and hands-off renders 5 clips on about 13 streams a month, that's about $6.50. Add the scout and ranker and you're close to $10.
- A hit cap stops a night silently.
- Fix: an alert at $7, seed the ledger, and decide on raising the cap only after measuring.

**PC and Mac contention:**
- Streams take 1–10 PM Tue–Thu, and Rocket League also blocks the PC. Idle time is mostly overnight and Fri–Mon.
- Tonight's PC runs needed about 15 test runs, each 30–45 minutes, plus the hourly puller.
- Long-form suites now run inside every auto-clip test run (34 suites), and Long-form's scans and renders want the same hours.
- **Tonight a second runner tested #75 without machine.lock**, so two runs could overlap.
- Old worktrees from other agents (acs-pr27, 28, 54, 63, 70, 75, 78 and pr61_wt) are still taking PC disk.
- Fix: one owner for heavy PC jobs, including test runs. The runner takes the lock itself. Auto-clip renders come before Long-form jobs.

**Mac disk:**
- 416 GiB free on Oct 20, and streams are 77–118 GB each (game plan).
- Three streams a week is about 250–350 GB. Free space could drop under 200 GiB in about one week and close to zero in about two, unless VODs move to the G-DRIVE.
- The Oct 13–15 copies are verified on the G-DRIVE, but the Mac copies weren't deleted.
- Decide this before Oct 27.

**Bot overlap:**
- **Auto-clip Engineer vs Clip Renders & Review:** both have rendered and written checklists, and both take machine.lock by hand. Rule: the Engineer writes code only; Renders & Review is the only bot that runs heavy jobs on the PC.
- **Engineer vs Research:** rating rounds (OI-038) compete with your own-clip ratings, which feed the Engineer's ranker (OI-027).
- **Long-form vs Engineer:** same repo, same runner (#89 edits `run_tests_pc.py`), same lock, same PC hours. A Long-form test failure turns an auto-clip SUMMARY into FAIL.
- **Proxy vs Grok Bot vs nightly refresh:** three summaries.
- **Publishing (planned) vs the editor's post copy:** two writers for captions.
- **Research vs Engineer** on reference measurements (`reference-notes/`).
- Fix: one owner per verb. Code is the Engineer, heavy PC jobs are Renders & Review, summaries are the Proxy, captions are the editor's post copy (Publishing only schedules).

**Process risk:** new approvals arrive faster than code merges. That's 32 Decisions lines in one day. Every new line is another thing an agent can trip on.

---

## Part 6. Earlier question 5: decisions only you can make

1. **Adopt the done definition?** At least 1 postable per stream and 2 on average, 4 in a row, 10 minutes or less of review, drafts by 10 AM hands-off, $1 or less per stream. *Recommended: yes.*
2. **Freeze the off-path items in Part 2?** That's four-outcomes PRs 1–7, PR A, B1, B2, stall alerts, any-game detection, the archive script, clip polishing, OI-038 and the Publishing bot. *Recommended: yes. Pause, don't close.*
3. **Merge the finished PRs now?** #61, #80 and #83 all passed tonight. *Recommended: yes.*
4. **Lift the scan hold for the Oct 27–29 and Nov 3–5 streams, on the new path only?** It's one command per stream, rendering the top 5, after Fix B. *Recommended: yes. Without fresh streams, CP3 can't happen.*
5. **The ~$1 replay spend for the scout and ranker?** *Recommended: yes. The ceiling is about $0.45.*
6. **Picks floor?** Render 3 always, or only grade 4 and up? *Recommended: 3 always until CP2 (the measurement needs data), then only grade 4 and up, with "this stream had fewer" reported.*
7. **Length table?** *Recommended: target 40 s, hard cap 60 s, payoff may run longer.* Your loved reference shorts have a median of 43 s, and your notes say both "ends too early" and "half the length". No mid-clip cuts except Elden Ring boss fights.
8. **Spend cap?** *Recommended: keep $10 a month for now. Seed the ledger with October's console total, add an alert at $7, and raise it only if editor cost is measured above $0.15 per clip.*
9. **Who runs heavy PC jobs, including tests?** *Recommended: only Renders & Review, and the test runner takes machine.lock itself.*
10. **Stop rule?** *Recommended: a clip that needs a second re-render is dropped. If done isn't met by Dec 4, the phone cards (you tick 2–3 of 10, about 2 minutes) become the product.*
11. **Long-form scope?** *Recommended: no more detection PRs after #89. Ship the Oct 9 re-cut episode first, and do the DaVinci package after you approve that file.*
12. **Mac disk?** *Recommended: before Oct 27, OK deleting the Mac copies of VODs already SHA-verified on the G-DRIVE (Oct 13–15), or have new VODs move there after each stream.*
13. **Bloat guardrail?** *Recommended: yes to one in, one out, plans of one page or less and 3 versions or less, and docs-only PRs skip the plan step.*

---

Sources read:
- auto-clip-system `origin/main` at a9aa562: vault/ (Decisions, Status, Open-Items pointer, VAULT-RULES, Daily, Jobs, Ideas, _umbrella-draft), AGENTS.md, `docs/Phase0-Game-Plan.md`.
- The 16 open PRs (files and bodies) and the last 25 merged.
- vault-umbrella `main` at 00ebd17: README, Home, Open-Items, Bots/*, Templates/*, Preferences, Research.
- Plans store: PLAN-TRACK1-v1, SCHEDULE, file and word counts for every plan file, LONGFORM-OI-ROWS.
- The architecture review, tonight's PC test report and your 39 ratings.

No code changed, no PR opened, nothing pushed, no paid calls.
