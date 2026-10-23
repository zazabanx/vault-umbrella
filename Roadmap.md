# Roadmap

AutoClip's goal and checkpoints from Claude's plans, plus every saved plan in the `Gameplans/` folder (index at the bottom). Owners and due dates stay in [[Open-Items]]. Pipeline facts stay in the product vault.

Stamp: Grok Bot executor, 2026-10-22 ~10:30 PM ET. Sources: `CLAUDE-QUEUE-AND-PHASES-REVIEW-2026-10-20.md`, `PLAN-TRACK1-v3.md`, `T1-PROGRESS.md` (CP2 scoring 10:10 PM ET and the user ruling at 10:09 PM ET on Oct 22), [[Open-Items]] OI-046 and OI-047, all on the box at `/workspace/handoffs/` except Open-Items.

## CURRENT (newest version, as of 2026-10-22)

Track 1 plan: [[Gameplans/2026-10-21-PLAN-TRACK1-v3]] (approved by the user 2026-10-21 12:12 PM ET). For CP1 and CP2 it replaces the Oct 20 marks in HISTORY. It sets no new CP3 or CP4 marks, so the Oct 20 ones in HISTORY are the latest written.

**Done.** At least 1 postable clip per stream, or an honest "nothing strong tonight" that the user confirms in a 2-minute look at the top cards (a missed moment = FAIL). 6–7 per week tracked separately. Stop rule: if done isn't met by Dec 4, the 2-minute phone pick becomes the product. (PLAN-TRACK1-v3)

| Checkpoint | Marks (PLAN-TRACK1-v3) | State |
|---|---|---|
| CP1 (was Oct 24–26) | Blind ranker vs detector top 5. PASS: ranker wins at least 2 of 3 streams, at most 1 known "no". Loses at least 2 of 3 = halt; a split means CP2 decides. | **SPLIT** (not halt), 2026-10-22 |
| CP2 (moved by the user from Oct 30 to **Oct 22**) | Thin path top 3–5, 3 also on the old path, unlabeled, at most 10 per session. PASS: thin ≥ old; at least 40% of each stream's ranked moments rated Moment=yes; at most 15 minutes of review per stream. | **PASS (official)**, scored 10:10 PM ET Oct 22 |
| CP3 (was Nov 6) | Fresh streams. No newer marks written; see HISTORY. | Back to back with CP4, as soon as ready (OI-046) |
| CP4 (was Nov 13) | Hands-off. No newer marks written; see HISTORY. | Back to back with CP3, as soon as ready (OI-046) |

**CP2 result (official): PASS on all 3 marks.**
- Moment=yes, counted per ranked moment: Oct 9 2/5 = 40% (R3, R4), Oct 14 2/5 = 40% (R1, R4), Oct 15 2/5 = 40% (R3, R5). Exactly at the 40% mark each night.
- Thin ≥ old: 3 of 3 (all three blind pairs tied).
- Review minutes: Oct 9 13, Oct 14 6, Oct 15 10 (all within 15).
- Per-moment counting is official. The per-draft view (6 drafts each: 33% / 50% / 33%) is a footnote only.
- User ruling 10:09 PM ET: Oct 15 R3 "I'VE BEEN PUNISHED FOR MY SINS" verdict "yes" = needs work. CP2 PASS stands.
- Follow-up finding: [[Gameplans/2026-10-22-CP2-PREROLL-FINDING]] (2 Oct 15 drafts start after a stronger moment 12–17 s earlier; fed into the post-CP2 plan).

**Next.** The post-CP2 plan (planned file `PLAN-POST-CP2-v1.md`; not done yet; the Engineer drafts it by Oct 31). The 3:23 AM Oct 22 gameplan scoped it as "a one-command path for CP3, and CP4 with the morning report first". Requirements added later on Oct 22 (T1-PROGRESS): the success-rate target before the full backlog goes in (CP2's 40% is the baseline), the Oct 30 → Nov 6 steps, OI-058 triggers and the rage side collection, the Float and templates order, what's realistic before the plan-renewal dates (Nov 12, Nov 21), and a cost-per-clip-after-Max target. The render no-idle plan [[Gameplans/2026-10-22-PR-PLAN-RENDER-NO-IDLE-v3]] waits for the user's OK.

## HISTORY: Claude's Oct 20 roadmap (original marks)

From [[Gameplans/2026-10-20-CLAUDE-QUEUE-AND-PHASES-REVIEW]] (Claude, 2026-10-20, written 11:55 PM ET). Condensed here; the full text is in the copy. CURRENT above wins where they differ.

**Done definition.** All five at once:

| # | Check | Number |
|---|---|---|
| X | Postable clips per stream | At least 1 on every stream, and at least 2 per stream on average across the streak. "Postable" = ready as is, or needs work that one re-render fixes from a one-line note (or the user fixes in 5 minutes). At least half ready as is. |
| Y | Streams in a row | 4. A miss restarts the count. |
| Z | Review time | 10 minutes or less per stream (at most 5 drafts). |
| H | Hands-off | Drafts plus a "clips ready" message by 10 AM after a stream. 0 manual steps. 0 heavy jobs while OBS, a game or Resolve runs. |
| C | Cost | $1 or less per stream, inside the $10 per month cap, every paid call counted. |

**Checkpoints (all ET).**

| Date | Checkpoint | Numbers |
|---|---|---|
| Wed Oct 21 | Freeze recorded, finished PRs merged | One Decisions line records Track 1 plus the pauses. #78, #83, #80, #61 merged with PC SUMMARY PASS. Open PRs 16 → 12 or fewer, paused ones labeled. |
| Sat Oct 24 | CP1: ranker finds the good moments (replay, no renders) | On labeled Oct 9 and Oct 14 moments, at least 3 of each stream's top 5 are known-strong, at most 1 known "no". Spend $0.45 or less. User ticks the top 10 Oct 15 cards; at least 2 ticks in the ranker's top 5. |
| Fri Oct 30 | CP2: rendered picks, rated | 9–15 new drafts from Oct 9, 14, 15 (new windows only), on the new timing path. At least 40% moment grade 4 or 5. At least 2 of 3 streams with 1+ postable. Review 15 minutes or less per stream. Editor spend per clip measured and under $0.20. |
| Fri Nov 6 | CP3: fresh streams | Oct 27–29 and Nov 3–5 streams on the new path (one command if hands-off isn't ready; needs the user's OK to lift the scan hold). On at least 3 fresh streams: average 1.5+ postable, at least 1 each, 10 minutes or less of review. |
| Fri Nov 13 | CP4: hands-off works | Nov 10–12 streams have drafts plus an alert by 10 AM next day. 0 manual steps, 0 heavy jobs during OBS or games, $1 or less per stream in the ledger. |
| Wed Nov 25 | DONE: 4 in a row | 4 consecutive streams meet X, Z, H and C. If the streak breaks, the next try ends Thu Dec 3. |
| Fri Dec 4 | Hard rethink | If done isn't met, use the pivot. Don't add rules. |

**Phases.**

| Order | Phase | Done when |
|---|---|---|
| 1 | Ranking proven (Track 1), Oct 21–30 | CP1 and CP2 numbers. |
| 2 | Fresh-stream quality, Oct 27–Nov 6 | CP3. |
| 3 | Hands-off wiring, after CP1, finished by Nov 13: Fix B, live hook, auto-render of the top 5, alert, lock owner and cleaner, runner takes the lock | CP4. |
| 4 | The streak (product done), by Nov 25 | 4 in a row meeting X, Z, H, C. |
| 5 | Posting starts, Publishing bot created | Trigger: 5+ clips in Ready_To_Post or the first long-form final. Done: the user approves the first post pack; nothing posts without the user's OK. |
| 6 | Learning (Track 2, not approved) | Starts at about 100 structured ratings (around mid-December). Done: precision at 5 rises on a frozen test set. |
| — | Long-form lane, parallel, lower PC priority | Oct 9 re-cut approved; then Oct 7, 8, 15; then the DaVinci package imports. No upload without the user's OK. |
| — | Templates and new product | Nothing to do until a second product exists. Fix the drifted stamps. |
| — | Project pack | Paused (OI-013). Revisit after phase 4. |

**Odds (Claude's judgment, not a measurement).** About 35% for the full definition by Nov 25; about 55% by end of December; about 60% for a looser version by Nov 25 (1 postable on every stream, 4 in a row, 10 minutes of review). Biggest unknown: whether every stream has 2 good moments.

**Why it could fail.** Thin streams; the ranker reads only words; timing (4 of 5 needs-work notes are start or end); attention drain to plumbing and notes; noisy ratings; silent stops (stale lock, spend cap, full Mac disk).

**Pivots.**

| Miss | What changes | What stops |
|---|---|---|
| CP1 | Re-run once with Sonnet (new spend OK, about $1 or less); detector events into the prompt as data. Still missing: the user ticks 2–3 of 10 phone cards and only those render. | New trigger phrases, loudness weights or caps. |
| CP2, moments good, edits not | One-note re-render ("end 4 s later"), once. | A clip needing a second re-render is dropped. No new editor rules. |
| CP2, moments bad | Same as CP1. If cards show nothing good, the stream passes with 0, reported honestly. | Rendering 24 per stream. |
| CP3 | Swap in fresh prompt examples (Oct 9/14/15 ratings may have leaked). | Treating replay scores as proof. |
| CP4 | Fix only the stage that broke; "one command per stream" fallback. | New plumbing features. |
| DONE missed twice (by Dec 4) | Phone cards become permanent (2-minute pick, then hands-off render). Revisit full automation at about 100 structured ratings (Track 2). | Editor polishing of single clips. |

## Pointers

- Track 1 plan (approved): [[Gameplans/2026-10-21-PLAN-TRACK1-v3]]. Earlier Track 1 versions: [[Gameplans/2026-10-21-PLAN-TRACK1-v2]], [[Gameplans/2026-10-21-PLAN-TRACK1-v3-opus48-draft]], [[Gameplans/2026-10-21-PLAN-TRACK1-v3-round1]].
- Claude's architecture review: [[Gameplans/2026-10-20-CLAUDE-DETECTOR-ARCHITECTURE-REVIEW]].
- Claude's Oct 20 roadmap review (full text): [[Gameplans/2026-10-20-CLAUDE-QUEUE-AND-PHASES-REVIEW]].

## Gameplans index (newest first)

- 2026-10-22 — post-CP2 plan v1 (placeholder, no file yet: not done; due Oct 31).
- 2026-10-22 — [[Gameplans/2026-10-22-CP2-PREROLL-FINDING]]: CP2 pre-roll finding (read-only).
- 2026-10-22 — [[Gameplans/2026-10-22-PR-PLAN-RENDER-NO-IDLE-v3]]: render no-idle plan v3 (build waits for the user's OK).
- 2026-10-22 — [[Gameplans/2026-10-22-GAMEPLAN]]: nightly gameplan (Claude, 3:23 AM ET).
- 2026-10-22 — [[Gameplans/2026-10-22-GAMEPLAN-PROXY-DRAFT]]: Proxy draft of the same gameplan, not Claude-reviewed.
- 2026-10-21 — [[Gameplans/2026-10-21-PLAN-TRACK1-v3]]: Track 1 plan v3, approved.
- 2026-10-21 — [[Gameplans/2026-10-21-PLAN-TRACK1-v3-round1]]: v3 round 1, not approved.
- 2026-10-21 — [[Gameplans/2026-10-21-PLAN-TRACK1-v3-opus48-draft]]: v3 draft, not approved.
- 2026-10-21 — [[Gameplans/2026-10-21-PLAN-TRACK1-v2]]: Track 1 plan v2, superseded.
- 2026-10-20 — [[Gameplans/2026-10-20-CLAUDE-QUEUE-AND-PHASES-REVIEW]]: Claude's roadmap review.
- 2026-10-20 — [[Gameplans/2026-10-20-CLAUDE-DETECTOR-ARCHITECTURE-REVIEW]]: Claude's architecture review.

Add a new plan as `Gameplans/YYYY-MM-DD-<NAME>.md` and add a line at the top of this index.
