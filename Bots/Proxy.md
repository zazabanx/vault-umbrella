# Proxy

Chief of staff and main chat for zazabanx. Takes every request, routes it to the specialist, tracks open work across bots, reports back simply, and collects approvals in batches. Specialists do the deep work.

## Now

- Tracking the auto-clip queue toward CP3 (fresh streams from Oct 27): the late-start fixes (PR 2 #155), no-idle PRs 1-2 (#145, #146), item 29, and the chat load test's OBS half. The Claude-only setup stays parked and Grok stays through CP4 (the user, 7:40 AM ET Oct 23); a switch happens only if Proxy and Claude are both confident it is seamless (CLAUDE-ONLY-USER-CONCERNS-2026-10-23).
- Outside dates: Oct 28 claim the Max API credit; Grok Pro+ renews 2026-11-12; Claude Max ends 2026-11-21. CP3 on fresh streams from Oct 27. Auditor-bot revisit 2026-11-01. Weekly team dreaming Sundays 11 AM ET (first run 2026-10-25).
- Morning summary daily at ~9:51 AM ET. Reads [[Open-Items]]. Shows items finished early and items waiting on the user. Since 2026-10-23 the nightly routine writes daily notes for both vaults.
- Routes: Auto-clip Engineer (detector, clips, PRs, tests, scans, vault); [[Bots/Long-form-YouTube]] (Elden Ring episodes, break reports, editor, upload prep); [[Bots/Personal]] (flights, purchases, personal research); [[Bots/Clip-Renders-Review]] (draft renders, ALT versions, review checklists, add-only copies); [[Bots/Research]] (shorts/reels/TikTok rating rounds, creator analysis, price and API checks).
- New-product kickoffs: read [[Home]], [[Preferences]], [[new-product]], and [[build-or-improve]]; create the product vault from the template; link it from the umbrella; brief a product bot.

## Open

Rows live in [[Open-Items]]; update the rows you own.

## Recent

- 2026-10-23 — 11:45 AM ET: Mac capture proven (#151, Twitch HTTPS via certifi): the test recording got detect and transcript files. M3 found no winner, so the ranker is frozen as is. CP3 top picks from Oct 27+ streams may render before OI-036 (decision C, 7:40 AM); old re-scans and Oct 21-26 scans stay held.
- 2026-10-23 — Nightly routine writes daily notes for both vaults. Posted clips stay full 1080p (720p only as review skim copies).
- 2026-10-23 — 12:20 AM ET: Claude-only stays an open question. The user switches only if Proxy and Claude are both confident it is seamless. Concerns note: CLAUDE-ONLY-USER-CONCERNS-2026-10-23 ([[Gameplans/2026-10-23-CLAUDE-ONLY-USER-CONCERNS]]). Engineer is drafting PLAN-CLAUDE-ONLY-SETUP-v1 with Opus on Max.
- 2026-10-23 — 12:16 AM ET: Trigger/rage plan approved. Always-clip + rage: WHAT ARE YOU DOING, WHERE ARE YOU, I suck I suck. Rage only: get out of the way (both versions). OH MY GOD is a demoted hint + rage. I'm the greatest / greatest of all time added as always-clip; bare "the greatest" is loudness-gated; "best ever" dropped. Non-rage trigger clips go to Trigger_Hits\<date>. Ranker keeps its own top 5; trigger moments are set aside raw, not auto-rendered.
- 2026-10-22 — 11:54 PM ET: Chat-logging plan approved (PLAN-CHAT-LOGGING-v2, Claude-approved). Backfill via TwitchDownloaderCLI only for Oct 7-22 recordings. Anonymous IRC live capture on every stream from Oct 27. 30-min load test. Chat stays out of the ranker until after CP3. "LOL" and "LO" are strong chat cues.
- 2026-10-22 — 11:50 PM ET: Proxy created the Auto-clip queue page. Docs merged as vault #30 (7f1b0cf); auto-clip #125 and #126. User OK'd the whole proposed queue.
- 2026-10-22 — 11:49 PM ET: Team rule: work goes task to task by objective, back to back. No scheduling around fixed dates. Only real outside dates (billing renewals, actual streams) gate anything.
- 2026-10-22 — 11:36 PM ET: User approved post-CP2 decisions A-E. Freeze lifted. Trigger list approved with over-2-per-stream auto-demote. Rage collection is Videos\Rage_Collection\<date>: raw cuts, and the user picks what goes to the editor. CP3 runs on fresh streams from Oct 27.
- 2026-10-22 — 10:10 PM ET: CP2 official PASS (40/40/40% per ranked moment). Top problem: clips start too late (editor start-point defect). A 20 s look-back guard is proposed.
- 2026-10-22 — 9:44 PM ET: auto-clip #120 merged (dd1f489); docs #121 (506bf8b). Render no-idle fix plan written (PR-PLAN-RENDER-NO-IDLE-v1, 8 one-defect PRs) and sent to Opus on Max for review before building.
- 2026-10-22 — 8:54 PM ET: All 18 CP2 drafts landed in Needs_Your_Review (6 each for Oct 9, Oct 14, and Oct 15). Run cost about $1.51 (October total $2.89). PC editor cap confirmed at $5.
- 2026-10-21 — Claude Code workflow note approved (OI-042). Opus direction review settled (OI-048). Track 1 plan approved; Track 2 is not yet approved. Claude Code may write code: plan first, branch plus PR, no direct push to main, a fresh Claude session reviews every PR. Claude use: Opus 5.5 at xhigh by default, max only with the user's OK each time; flag the user via Proxy above 85% session or weekly usage; reviews and plans at most 1 page, plans at most 3 versions; Claude time goes to Track 1 first. Cursor cloud agents remain an option.
- 2026-10-20 — Standing: refer to clips by hook or title, not number. No Dreamer bot; Proxy owns the 2026-11-01 auditor revisit. Full speed when the user is not streaming or gaming; independent work in parallel; approvals in batches. Four review folders: Discarded, Postable_Needs_Work, Ready_To_Post, Perfect_Clips_Protected. The "only fix problems in clips worth posting" rule covers re-editing clips, not plumbing.

Newest first. Prune after 14 days.

## Read first

- [[Home]]
- [[Preferences]]
- [[README]]

Shared rules: never post or send anything without the user's OK; never delete VODs without explicit approval; Claude reviews big changes and the user has final say; cloud agents write code, one defect per PR, plan approved first; heavy jobs take the lock file and nothing heavy runs while OBS or a game is running.
