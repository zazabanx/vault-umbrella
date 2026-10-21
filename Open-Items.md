# Open items

Live once this PR is on main.

Due dates are the latest acceptable deadlines, not targets. Every item is worked on as soon as it is unblocked and marked done the moment it finishes, even if its due date is days away. Never hold finished work for a date. (User, 2026-10-20)

This is the only list of owners and due dates.

Columns stay `ID | Item | Owner | Due | State | Source`. No Bot column. The section is the bot. Owner is Engineer, user, Proxy, Long-form, `Renders & Review`, or `Research`.

States are `open`, `waiting on user since YYYY-MM-DD`, or `done YYYY-MM-DD`. Due `—` means no date. A done item moves to Done and is pruned 14 days after the done date. An item that misses its due date twice is marked `flagged` in State. The nightly vault note and Sunday dreaming keep this file current.

A bot edits the rows it owns, including inherited `OI-` ids, and appends only its own prefix. Prefixes: `OI-` Auto-clip, `CR-` Renders & Review, `RS-` Research, `LF-` Long-form, `PE-` Personal, `PX-` Proxy. Not one shared counter. `RR-` is a rating-round file id, not an open-item prefix. Next OI is OI-042. Do not fill gaps. CR rows are CR-001 to CR-004. Next CR is CR-005. Future Research rows start at `RS-001`. Next Personal id is `PE-001`.

On 2026-11-01 mark OI-015 done; PX-001 stays open.

Research output format is `plans/SPEC-RATING-ROUND-v1.md`. Turning a round into detector code stays OI-027, Engineer.

### Reference clip library

- **Research** finds, link-checks and rates clips from outside creators, and keeps the library list and its notes. It stores links and measurements only, with no downloads or logins. An outside clip goes into the reference library only after the user gives that clip an explicit thumbs up (user, 2026-10-20 7:43 PM ET). Until then it stays a candidate in a rating round. A 'love it' rating is not approval. Location: its own store, plus the umbrella vault under `Research/Ratings/` (ROUND-<ID>.md and .csv) once the team vault is live. The creator list and notes go in umbrella `Research/Reference-Library.md`.
- **Renders & Review** adds the user's own perfect clips to PC `Videos\Perfect_Clips_Protected` (protected, add-only, SHA-256 and a LOG line, only with the user's OK for each clip). It can also add to PC `Videos\Approved_References` (the editor's must-reproduce targets: Oct 9 clip 01 and Oct 14 clip 14), but only when the user names a clip as a reference. In both folders nothing is overwritten, moved or deleted.
Clips in PC `Videos\Ready_To_Post` feed the Publishing bot (PX-005). Renders & Review never posts. Nothing is posted without the user's OK.
Clips in PC `Videos\Postable_Needs_Work` are postable but need work (normal folder, not protected).
- **Engineer** owns how the detector and editor learn from both: features, judge and scout prompts, OI-027 taste data from rated rounds, editor targets measured from references (hook timing, cut length, pacing, text timing), and all code. It reads both PC folders and the Research CSVs and never writes to the protected folders. In the auto-clip repo, `reference-notes/` (README only today) is where the Engineer's measured targets go.

## [Auto-clip](https://github.com/zazabanx/auto-clip-system)

### Open

| ID | Item | Owner | Due | State | Source |
|---|---|---|---|---|---|
| OI-001 | #58 Fix A code PR (transcript_used plus coverage check) | Engineer | 2026-10-21 (U) | open | PR #61 (plan: PR #58; auto-clip-system vault/Daily/2026-10-18.md P1) |
| OI-002 | #58 Fix B (transcribe stage before detect) | Engineer | 2026-10-22 (U) | open | PR #58 (auto-clip-system vault/Daily/2026-10-18.md P1) |
| OI-003 | 3.1 PC auto-render watcher plan | Engineer | 2026-10-22 (U) | open (no clip example needed, 2026-10-20; PR after plan approval) | auto-clip-system vault/Status.md |
| OI-004 | Clips-ready alert | Engineer | 2026-10-28 (U) | open (no clip example needed, 2026-10-20; PR after plan approval) | auto-clip-system vault/Decisions.md |
| OI-006 | Mac transcribe.lock done: an empty file from the Oct 17 9:59 AM re-scan transcription, no process holding it, removed 2026-10-20 6:36 PM. PC puller and git-pull locks stay open (report first) | Engineer | 2026-10-21 (U) | open | user, 2026-10-20 |
| OI-009 | Review the drafts in Clips_To_Review\Needs_Your_Review (15 Oct 9 drafts now; Oct 15 drafts are added after the batch) using REVIEW_CHECKLIST.txt | user | 2026-10-24 (suggested) (U) | waiting on user since 2026-10-20 | auto-clip-system vault/Daily/2026-10-20.md |
| OI-011 | Archive plan for VODs not yet on the G-DRIVE (old .mov files, and confirm whether the Oct 11 Twitch download exists) | Engineer | 2026-10-22 | open | Engineer, 2026-10-20 (Mac disk review) |
| OI-012 | Issue #48 and the #49 follow-ups | Engineer | 2026-10-26 | open | auto-clip-system vault/Daily/2026-10-16.md |
| OI-013 | Project pack (Resolve stems) | user | — | waiting on user since 2026-10-16 (paused after Claude's REVISE) | auto-clip-system vault/Daily/2026-10-16.md |
| OI-014 | First independent Claude audit in Sunday dreaming | Engineer | 2026-10-25 | open | auto-clip-system vault/Decisions.md |
| OI-017 | Fix Oct 14 clips 07 and 10 (still not perfect after #38) | Engineer | 2026-10-25 (U) | open | auto-clip-system vault/Status.md |
| OI-018 | P3 trigger vs mic-loudness report (read-only, Mac) | Engineer | 2026-10-21 | open | user via Proxy, 2026-10-20 |
| OI-019 | Optional code guard: shared protected-paths deny-list in editor/review_inbox.py plus any future cleanup (approved by user 2026-10-20; next step PR A) | Engineer | 2026-10-24 (with OI-020) | open | user via Proxy, 2026-10-20 |
| OI-020 | PR A: protected-folder path guard (after #61 and Fix B) | Engineer | 2026-10-24 (U) | open | user, 2026-10-20 |
| OI-021 | PR B (B1 copy on ready to post) approved by the user 2026-10-20; code after the loudness gate and PR A | Engineer | 2026-10-25 (U) | open | user, 2026-10-20 |
| OI-022 | Loudness gate v3 approved by the user 2026-10-20; code after #61 merges | Engineer | 2026-10-23 (U) | open | plan in Claude review |
| OI-023 | PR B2: named clips into Perfect_Clips_Protected, after PR A | Engineer | 2026-10-27 (U) | open | auto-clip-system vault/Decisions.md |
| OI-024 | Maybe folder for near-miss clips (cap 3 per stream) | Engineer | 2026-11-03 (U) | open (no clip example needed, 2026-10-20; PR after plan approval; after OI-022 and OI-035 (merge order, PLAN-OI-024-v3)) | approved by the user 2026-10-20 via the Proxy's weekend audit (dropped from Oct 16) |
| OI-025 | Gemini extra-judge test, run regardless of the energy score. After OI-036, the user tests it. | Engineer | after OI-036, user tests | open | approved by the user 2026-10-20 via the Proxy's weekend audit (dropped from Oct 16) |
| OI-026 | Phone review copies back on Dropbox (check they play with AirPods) | Engineer | 2026-10-23 (U) | open | approved by the user 2026-10-20 via the Proxy's weekend audit (dropped from Oct 16) |
| OI-027 | Learn from the user's ratings (use auto-clip-system vault/Clip-Ratings.md and checklist verdicts to tune scoring) | Engineer | 2026-11-03 for design plus analysis (U) | open | approved by the user 2026-10-20 via the Proxy's weekend audit (dropped from Oct 16) |
| OI-029 | Stall alerts (tell the Proxy when a render, scan or transfer job stops making progress) | Engineer | 2026-10-28 (U) | open (no clip example needed, 2026-10-20; PR after plan approval) | approved by the user 2026-10-20 via the Proxy's weekend audit (dropped from Oct 16) |
| OI-031 | After all detector work and the OI-036 overview, and only on the user's OK to resume scans: re-score the Oct 7, 8, 9, 13 and 15 streams detect-only on features version 4 (the OI-022 loudness gate). The first hands-off scan is at this same later point. | Engineer | — | waiting on user since 2026-10-20 (scan hold; after all detector work and OI-036, on the user's OK) | approved by the user 2026-10-20 via the Proxy's weekend audit (dropped from Oct 16) |
| OI-032 | Auto-resume PR 1. Paused heavy jobs resume on their own after a 180 s grace once no game or OBS is running. It uses the machine.lock convention. Leftover machine.lock is report-only: the watcher shows who left it and how long ago, and the lock is cleared only with the user's OK (the cleaner follows in OI-040). Comes after OI-022 (the loudness gate) and before OI-021 (B1). Plan: /cursor/stores/bot/IDLE-RESUME-PLAN-v3.md | Engineer | 2026-10-23 (U) | open | approved by user 2026-10-20 via Proxy |
| OI-033 | Auto-resume PR 2, any-game detection (launcher library folders, games.txt plus games-ignore.txt, and a fullscreen high-GPU backstop that excludes browsers). Comes after OI-032. Plan: /cursor/stores/bot/IDLE-RESUME-PLAN-v3.md | Engineer | 2026-10-25 (U) | open | approved by user 2026-10-20 via Proxy |
| OI-034 | Claude judge (draft PR #16) rebuilt as a re-ranker plus a "judge's picks" tag that never removes clips from main or overflow; JUDGE_ENABLED stays 0 until switched on; fix the --transcripts-dir month-cap gap and the Haiku price; ~$1 paid benchmark on Oct 9 and Oct 14 against labels.csv. Steps: rebase plan Oct 22, code Oct 23–24, Claude re-review Oct 25, benchmark Oct 26, merge with default off Oct 27, shadow Oct 27–29, switch on in the Mac .env. Plan: /cursor/stores/bot/plans/JUDGE.md | Engineer | 2026-10-30 | open | approved by user 2026-10-20 6:27 PM via Proxy |
| OI-035 | Claude transcript scout: plan, Claude review, build into the detector (top priority; cost guard (PR #75) and S1a writer now, with S1a merging after the cost guard; S1b hook after #61 and Fix B; then S2 Scout folder (up to 10 drafts per stream, 40-row sidecar); the scout creates shared/llm_cost.py (CostGuard), which OI-034 imports; only the judge-seats stage waits on OI-034 (PLAN-TRANSCRIPT-SCOUT-v3)). Cost guard and the S1a writer started coding on 2026-10-20. After all detector work and the OI-036 overview, the user decides whether scans resume. | Engineer | 2026-10-30 (U) | open | user 2026-10-20 6:32 PM via Proxy |
| OI-036 | Full detector overview for the user: a big-picture revisit with each facet's inner workings and an improvement list (additions and removals). Depends on OI-035, Fix A #61, Fix B, OI-022, OI-034, peak-bonus, OI-024, and anything else that touches the detector. The scan hold continues until the overview; the user then decides whether scans resume. | Engineer | ~2026-11-01, latest 2026-11-03 (big-picture revisit plus additions/removals list) | open | user 2026-10-20 6:32 PM via Proxy |
| OI-039 | Four review outcomes: discard or "no" moves the clip from `Clips_To_Review\Needs_Your_Review\<date>\` into `Videos\Discarded` (normal folder; SHA-256 checked and logged; never deleted; deleting from Discarded needs the user's OK on a cleanup day; PLAN-FOUR-OUTCOMES-v9, which Claude approved on 2026-10-20 at 10:29 PM ET as the final plan); postable but needs work (new normal PC folder Videos\Postable_Needs_Work, not protected); ready to post (Videos\Ready_To_Post); perfect and protect (Videos\Perfect_Clips_Protected, protected, add-only). Write a plan for changing the code that maps checklist verdicts to folders; code changes only after the user approves the plan. | Engineer | — | open (plan approved 2026-10-20 10:06 PM ET; discard move approved 2026-10-20 10:09 PM ET; code queued after B2: needs-work copy, then discard move) | user 2026-10-20 9:10 PM ET via Proxy; plan approved user 2026-10-20 10:06 PM ET via Proxy; discard move approved user 2026-10-20 10:09 PM ET |
| OI-040 | machine.lock owner record and automatic stale-lock cleaner (PLAN-LOCK-CLEANER-v6): lock Fix A (owner PID, start time, heartbeat, release on exit), then lock Fix B (cleaner on the PC and Mac). Replaces the report-only leftover-lock rule once lock Fix B merges. | Engineer | — | open (approved; queued after #76 merges) | user 2026-10-20 9:11 PM ET via Proxy; plan approved 10:08 PM ET |
| OI-041 | Rule-sanctioned Decisions archive plan. auto-clip-system vault/Decisions.md is 123 of 200 lines and gains about 8 to 28 lines a day, so it fills around Oct 27 to Nov 3. The user approved PLAN-DECISIONS-ARCHIVE-v3 on 2026-10-20 at 10:49 PM ET: trigger at 180 lines, trim to 120, keep the last 7 days live, stop-and-ask fallback; the no-lines-lost check committed as a script plus a test run by run_tests_pc.ps1; AGENTS.md step 1 also checks Decisions-archive, with a stamp bump; the undated line stays in Decisions.md; the nightly routine starts the move PR at 180 lines. The 200 cap stays. | Engineer | 2026-10-26 | open (the build has started: auto-clip-system PR 1 rule, PR 2 readers, then the check script PR) | user 2026-10-20 10:13 PM ET via Proxy; PLAN-DECISIONS-ARCHIVE-v3 approved by the user 2026-10-20 at 10:49 PM ET |

### Done

| ID | Item | Owner | Due | State | Source |
|---|---|---|---|---|---|
| OI-010 | Dreaming proposal P3 yes/no | user | — | done 2026-10-20 (user approved) | auto-clip-system vault/Daily/2026-10-18.md |
| OI-030 | P6 (from dreaming/2026-10-18/PROPOSALS.md): (a) put the trigger phrase list into the detector features fingerprint so editing the list forces a re-scan; (b) Twitch credentials in detector/.env so the watcher can confirm the stream is offline. (b) is already done: .env set 2026-10-20 with channel zazabanx. | Engineer | 2026-10-24 | done 2026-10-20 | approved by the user 2026-10-20 via the Proxy's weekend audit (dropped from Oct 16) |
| OI-016 | PR review routine also fires on pr-opened | Engineer | 2026-10-20 | done 2026-10-20 | auto-clip-system vault/Known-Problems.md (fixed 2026-10-20); auto-clip-system vault/Daily/2026-10-20.md |
| OI-007 | Oct 13–15 G-DRIVE archive copy: 12/12 files SHA-256 verified, copy only | Engineer | 2026-10-21 | done 2026-10-20 | auto-clip-system vault/Status.md |

## Renders & Review

| ID | Item | Owner | Due | State | Source |
|---|---|---|---|---|---|
| OI-005 | Re-render Oct 14 clips 04 and 11 (clip 05 moved to CR-003). Done: closed by the user 2026-10-20 9:08 PM ET with no re-render. "One missed boost and I quit the game" is postable but needs work (user, 2026-10-20 9:10 PM ET; goes to Videos\Postable_Needs_Work); "Xbox's new website is 100% vibe coded" is dropped. Neither clip had a payoff moment for the #38 ending fix, so a re-render could not change them. | Renders & Review | 2026-10-22 | done 2026-10-20 | auto-clip-system vault/Known-Problems.md |
| OI-008 | Finish the Oct 15 draft renders into Clips_To_Review. Done: Oct 15 batch 24/24 rendered and checklist written 2026-10-20 7:11 PM ET. | Renders & Review | 2026-10-21 | done 2026-10-20 | user, 2026-10-20 (chat approval; paused at 9/24) |
| OI-037 | Subtitle fix for Oct 9 clip 13 "WHY DID I FOLLOW YOU" (group bridge jump, VOD 2026-10-09 14-39-39 ~2:49:36–2:50:04), which the user named perfect on 2026-10-20 and qualifies under the postable-clip rule. Fixes: drop late hook subtitles; sync "somewhere in the / water, okay?"; sync "die" (~0:16–0:17); check the stray "did" at ~0:21. Optional: sfx (fahh/vine boom), trim the start. Output: a NEW draft render in Needs_Your_Review only; the protected copy in Perfect_Clips_Protected is never altered. Gate: user re-review first. The user re-watches the clip and gives fresh notes before any work starts. When this reaches the front of the queue, Renders & Review pings the Proxy with the render path and the known issues. That ping starts PX-003. Work starts only after the Proxy relays the user's notes. | Renders & Review | 2026-10-23 (may move because of the gate) | open | user 2026-10-20 6:56 PM via Proxy |
| CR-001 | render, as new drafts, the trigger-built main picks that were not in the original batches (23 on v3: Oct 7 3, Oct 8 3, Oct 9 6, Oct 13 2, Oct 15 9; the count may change on v4) into `Videos\Clips_To_Review\Needs_Your_Review\<date>\`, with a new Notepad checklist. New files only. No Dropbox changes to existing clips. Starts only after OI-031's re-score, the OI-036 overview, and the user's OK to resume scans. | Renders & Review | — | waiting on user since 2026-10-20 (scan hold; after OI-031's re-score and OI-036) | PLAN-TEAM-OPEN-ITEMS-v2 |
| CR-002 | AirPods check of the phone review copies. New files only. Starts after OI-026 merges. No Dropbox changes to existing clips. | Renders & Review | — | open | PLAN-TEAM-OPEN-ITEMS-v2 |
| CR-003 | start fix for Oct 14 clip 05 "THE ROBOT THREW ONE PUNCH AND LOST THE" (VOD 2026-10-14 13-42-23, detector clip_05 at 1:30:19). The user rated it ALMOST / moment YES BIG YES, "starts too early (doesn't show full clip I'm reacting to)". Fix the start so the full video being reacted to is shown. Output is a NEW draft render in `Needs_Your_Review` only. The protected copy in `Perfect_Clips_Protected` (copied 2026-10-20, SHA-256 dbb94543…) is never altered. Gate, like OI-037: when this reaches the front of the queue, Renders & Review pings the Proxy so the user re-reviews the clip and gives notes first. Work starts only after the Proxy relays them. | Renders & Review | — | open | user 2026-10-20 7:47 PM ET via Proxy |
| CR-004 | Parked: start-time improvement for Oct 9 "My controller killed him, okay". The user said 2026-10-20 9:16 PM ET that neither ALT (earlier start, club-hit start) beats the original; the protected copy stays the version. No new ALTs, and both ALT files stay in `Needs_Your_Review`. Revisit at a later date of the user's choosing. | Renders & Review | — | waiting on user since 2026-10-20 (parked; user picks a later date) | user 2026-10-20 9:16 PM ET via Proxy |

## Research

| ID | Item | Owner | Due | State | Source |
|---|---|---|---|---|---|
| OI-028 | Reference-creator viral-clip analysis (the creators list in the reference library). Done: analysis 2026-10-20 (62 Shorts, 19 creators); RL round rated by the user 2026-10-20 8:15 PM ET (10 love it, 1 meh, 1 not me). Ratings only, no clip reference-approved; using them stays OI-027 (Engineer). Files: Research store ratings/OI-028/. | Research | 2026-10-27 | done 2026-10-20 | approved by the user 2026-10-20 via the Proxy's weekend audit (dropped from Oct 16) |
| OI-038 | Shorts rating round for other games and streamers. Same format as OI-028: top shorts/TikToks/Reels for Elden Ring and the user's other streamed games, plus the reference-library streamers (xQc, Asmongold, Kai Cenat, caseoh, shroud and the rest), for the user to rate love it / meh / not me. Round built 2026-10-20: 50 rows, all links checked live (7 Elden Ring, 5 How to Fish, 3 Where Winds Meet, 35 reference streamers; 46 YouTube Shorts and 4 TikToks), sent to the Proxy for the user to rate. | Research | — (queued right after the transcript scout, OI-035; research may run in parallel) | waiting on user since 2026-10-20 | user 2026-10-20 7:20 PM via the Proxy |

### Done

| ID | Item | Owner | Due | State | Source |
|---|---|---|---|---|---|

## Long-form YouTube

| ID | Item | Owner | Due | State | Source |
|---|---|---|---|---|---|
| LF-001 | PR #70 merge (https://github.com/zazabanx/auto-clip-system/pull/70, head f23c62b; Claude approved) | Long-form | 2026-10-21 | open: waiting on PC run_tests_pc.ps1 SUMMARY | user via Proxy, Oct 20 6:19 PM |
| LF-002 | PR2 break-report changes (plan approved) | Long-form | 2026-10-21 | open: code starts when #70 merges | user via Proxy, Oct 20 |
| LF-003 | PR3 review/apply changes (plan approved) | Long-form | 2026-10-21 | open: code starts when #70 merges | user via Proxy, Oct 20 |
| LF-004 | Person-detection PR for Oct 15 (plan approved) | Long-form | 2026-10-22 | open: code starts when #70 merges | user via Proxy, Oct 20 6:19 PM |
| LF-005 | Break report: Oct 9 recut | Long-form | 2026-10-22 | open: needs #70, PR2, PR3 | user via Proxy |
| LF-006 | Break report: Oct 7 | Long-form | 2026-10-22 | open: after Oct 9 | user via Proxy |
| LF-007 | Break report: Oct 8 | Long-form | 2026-10-22 | open: after Oct 9 | user via Proxy |
| LF-008 | Break report: Oct 15 | Long-form | 2026-10-23 | open: needs the person PR | user via Proxy |
| LF-009 | Editor PR5 (plan v1 approved Oct 20 6:59 PM) | Long-form | 2026-10-24 | open: code after #70, PR2, PR3, person PR | user via Proxy, Oct 20 6:39 PM |
| LF-010 | DaVinci Resolve test clip (60 s, 4 tracks, plus a timeline file). Mac path ~/longform-check/resolve-smoke/ | Long-form | 2026-10-21 | done 2026-10-20 | user via Proxy, Oct 20 7:00 PM |
| LF-011 | DaVinci editing package PR6 | Long-form | 2026-10-26 | open: queued after editor PR5; no longer blocked on the user | user via Proxy, Oct 20 6:53 PM |
| LF-012 | YouTube upload prep (finals plus titles/descriptions for review) | Long-form | 2026-10-26 | open: needs editor plus the user's break ticks; nothing posted without the user's explicit OK | standing rule |
| LF-013 | DaVinci smoke test on the PC. Done: passed 2026-10-20 8:24 PM ET (mkv shows 4 audio tracks; fcpxml timeline imported with 2 clips and 4 audio tracks). | Long-form | 2026-10-22 | done 2026-10-20 | user via Proxy |

## Personal

Next id `PE-001`. No rows.

## Proxy

| ID | Item | Owner | Due | State | Source |
|---|---|---|---|---|---|
| OI-015 | Auditor-bot revisit check (after 2 weeks of the new tracking) | Proxy | 2026-11-01 | open | auto-clip-system vault/Decisions.md |
| PX-001 | Weekly team dreaming, Sundays 11 AM ET. First run 2026-10-25. Includes the auditor-bot call on 2026-11-01. | Proxy | 2026-10-25 | open | user, 2026-10-20 7:20 PM ET |
| PX-002 | Nightly bot-pages refresh around 1 AM ET. | Proxy | — | open | user, 2026-10-20 7:20 PM ET |
| PX-003 | Relay the bridge clip (Oct 9 clip 13) re-review to the user before OI-037 starts. The ping that starts this row comes from Renders & Review (OI-037). | Proxy | — | open | user, 2026-10-20 7:20 PM ET |
| PX-004 | Take the bot-split proposal (Renders & Review, Research) to the user once the Engineer sends it. | Proxy | — | done 2026-10-20 | user, 2026-10-20 7:20 PM ET |
| PX-005 | Create the Publishing bot (approved by the user 2026-10-20 7:34 PM ET). It writes titles, descriptions, thumbnails and captions, and schedules posts for long-form and approved shorts. It posts only with the user's OK and never edits videos. Trigger: Long-form's first '(final).mkv' is ready for the user's review (Long-form pings the Proxy), or approved shorts are ready to post, whichever comes first. | Proxy | 2026-10-26 | open | user via Proxy, 2026-10-20 7:34 PM ET |
