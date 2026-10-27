# Proxy

Chief of staff and main chat for zazabanx. Takes every request, routes it to the specialist, tracks open work across bots, reports back simply, and collects approvals in batches. Specialists do the deep work.

## Now

- **CP3:** night 1 (Oct 26) is done: 0 of 6 postable, $0.885. Night 2 is tonight (Oct 27), night 3 is Oct 28; together they need 5+ postable. Scoring is Thu Oct 29 ~8 AM. The editor has been frozen since 9:09 PM Oct 26. No auto-clip-system merges until the Oct 28 `cp3_run` finishes, except one test-first plumbing break-fix on night 1 or 2 (Proxy and Claude decide). Main is `d4a1227`. Held drafts: #175 nightly notes and #176 brief refresh (frozen as they are, no more pushes), #177 no-idle PR 5 (never PC-tested), #178 CP4 P1 morning report (Sonnet r2 APPROVE).
- **Today (Oct 27):** approve CP4 plan v3 (final, 3 of 3) and catch up the P1/P2 approvals. Confirm the Engineer's PR auto-review fires only on non-draft code PRs. Send the user ONE batched message: the Grok trim to Thu noon, whether the VOD yes covers the nightly G-DRIVE copy, CP4 v3 §7 Q3/Q4/Q5/Q8, the API balance (top up only under ~$3) and the stream end times. Gate night 2: the $0 preflight on both machines before OBS, then the chain in batched turns (Grok ≤6), and stop and report on any surprise.
- **Usage:** Grok Bot weekly usage is at 95%. It resets Thu Oct 29 11:59 AM ET, and on-demand is off: at 100% every bot and routine stops, night 3 included. The Engineer uses 86% of it (77% bot-to-bot). The proposed trim (one hand-off file and one message per task, no acks or polls) waits on the user. Claude Max is the cheap lane; the gameplan sends box work to headless `claude -p`.
- **Standing (the user, Oct 26):** each night's Mac VOD is deleted only after its drafts are in the review folder, the `trigger_cuts` audit is green and the G-DRIVE SHA-256 matches; the Oct 21-23 recordings stay. The pipeline starts right after each stream, and both machines stay on overnight. The CP4 morning report is a file folded into the 8 AM summary. The Oct 29 and 30 streams are CP4 attempts if P1+P2+P3 are live at the 11:15 AM go/no-go. Also standing: overnight work every night and full weekend days; no merges while live; nothing heavy while OBS, a game or Resolve runs; clips are named by hook or title.
- **Dates and routes:** claim the Max API credit Oct 28 10 AM. Nonstop CP4 work runs from the Oct 28 stream end (~4 PM) to the Oct 29 stream (~noon). Grok Pro+ renews 2026-11-12 (no step-down before then). Claude Max ends 2026-11-21. Auditor revisit 2026-11-01. Routines: gameplan ~3 AM, 8 AM summary, Sunday 11 AM dreaming, Monday ~6:30 AM plan check. Routes: Auto-clip Engineer; [[Bots/Long-form-YouTube]] (on hold); [[Bots/Personal]]; [[Bots/Clip-Renders-Review]]; [[Bots/Research]] (paused). New-product kickoffs: [[Home]], [[Preferences]], [[new-product]], [[build-or-improve]].

## Open

Rows live in [[Open-Items]]; update the rows you own.

## Recent

- 2026-10-27 — 12:05-3:45 AM ET: CP4 v3 got its Oct 28-29 schedule note (no v4). vault-umbrella #50 merged (Oct 26 daily note). P1 #178 (`616ece2`) got Sonnet r2 APPROVE at 12:19 AM after an `--out` guard fix. The P2 writer started at 12:21 AM and died mid-run with partial, uncommitted edits; restart today. The daily summary and GAMEPLAN-2026-10-27 were saved.
- 2026-10-26 — 11:20-11:55 PM ET: the user did the T2 ear check (1 yes, "I'm the greatest", kept in `clips_keep`; 3 no; 1 unverified; queued as Decisions lines 2-3). They answered the weekly plan: standing VOD delete yes; Oct 29/30 as CP4 attempts; the detector goal as a quality bar at scoring; no Grok step-down before Nov 12; narrow the PR auto-review now and close stale drafts after scoring. They also made the CP4 report a file in the 8 AM summary, OK'd the one G-DRIVE write (11:33 PM) and flagged Grok at 95%. First verified VOD delete: the Oct 26 VOD was copied to the G-DRIVE and the SHA-256 matched; the Mac copy was deleted at 11:49 PM (377.7 GiB free). CP4 plan v3 final at ~11:55 PM, not yet approved.
- 2026-10-26 — 5:43-11:00 PM ET: CP3 night 1 ran end to end. `cp3_run --send` failed once on a missing key ($0); the Proxy said GO at 8:21 and the rerun ranked 45 for $0.1229. The PC rendered 6 drafts 9:09-9:58 PM. Total $0.885. The user rated at 11 PM: 0 of 6 postable (3 needs work, 3 discard); hooks are the top problem.
- 2026-10-26 — 3:03 AM-12:39 PM ET: vault-umbrella #48 and #49 merged. Readiness checks passed on `d4a1227` (PC 0 fail + 2 known warnings, Mac 0/0). 12:37 PM: the pipeline starts right after each stream, and both machines stay on overnight.
- 2026-10-25 — 8:22-8:26 AM ET: the user answered the Sunday gameplan: yes to the break-fix exception, the two-stream counting rule, rating before the next stream and a Monday API balance check. Long-form stays on hold and the Sanibel task is ended. Sunday: CP4 plan v1 written, no-idle PR 5 built as held draft #177, dreaming logged 14 findings.

Newest first. Prune after 14 days.

## Read first

- [[Home]]
- [[Preferences]]
- [[README]]

Shared rules: never post or send anything without the user's OK; never delete VODs without explicit approval; Claude reviews big changes and the user has final say; cloud agents write code, one defect per PR, plan approved first; heavy jobs take the lock file and nothing heavy runs while OBS or a game is running.
