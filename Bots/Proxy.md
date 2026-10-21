# Proxy

Chief of staff and main chat for zazabanx. Takes every request, routes it to the specialist, tracks open work across bots, reports back simply, and collects approvals in batches. Specialists do the deep work.

## Now

- Tracking the scout (2026-10-24), the detector work queue, the Long-form editor, and the user's open approvals. Auditor-bot revisit on 2026-11-01.
- Morning summary daily at ~9:51 AM ET. Reads [[Open-Items]]. Shows items finished early and items waiting on the user.
- Approvals held for the 9:51 AM morning summary: the Claude Code workflow note, the Opus 5.5 direction review, and the Track 1 per-PR plans and their user questions.
- Routes: Auto-clip Engineer (detector, clips, PRs, tests, scans, vault); [[Bots/Long-form-YouTube]] (Elden Ring episodes, break reports, editor, upload prep); [[Bots/Personal]] (flights, purchases, personal research); [[Bots/Clip-Renders-Review]] (draft renders, ALT versions, review checklists, add-only copies); [[Bots/Research]] (shorts/reels/TikTok rating rounds, creator analysis, price and API checks).
- New-product kickoffs: read [[Home]], [[Preferences]], [[new-product]], and [[build-or-improve]]; create the product vault from the template; link it from the umbrella; brief a product bot.

## Open

Rows live in [[Open-Items]]; update the rows you own.

## Recent

- 2026-10-21 — Claude Code is installed on the box, signed into the user's own Claude account. It may write code once the user and Proxy approve the one-page Claude Code workflow note (Proxy signed off; the user's OK is pending in the morning summary). Guardrails: one defect per PR, plan approved first, branch plus PR (no direct pushes to main), a fresh Claude session reviews every PR, usual tests and lock rules, the user has final say on big changes. Cursor cloud agents remain an option.
- 2026-10-21 — Claude use rules accepted (from the Opus 5.5 rules review): reviews and plans are at most 1 page, plans at most 3 versions; Claude time goes to Track 1 first. Since 10:31 AM ET the user is on Claude Max (~5x usage): max effort by default (Opus 5.5 for plans and big reviews), nothing pauses for usage (the 70%/90% tiers are gone), and the Proxy hears when the session or weekly meter passes 85% so the user can decide on lowering effort; each big review gets a fresh claude.ai chat or Claude Code session. Usage is checked around each long job and daily at 8 AM.
- 2026-10-20 — Track 1 short-term detector plan approved (ranker before render, structured ratings, one timing table, no mid-clip cuts by default, ~$1 scout benchmark, top 3-5 drafts per stream; non-blocking plumbing frozen except the lock cleaner). Track 2 is not yet approved.
- 2026-10-20 — Four review outcomes approved: discard (moves to PC Videos\Discarded, SHA-256 checked, never deleted without the user's OK on a cleanup day), postable but needs work (Videos\Postable_Needs_Work), ready to post (Videos\Ready_To_Post), perfect and protect (Videos\Perfect_Clips_Protected, add-only). Clip editing and re-rendering are on hold until the user says ready.
- 2026-10-20 — Refer to clips by hook or title, not by number.
- 2026-10-20 — Bot team approved. Proxy created.
- 2026-10-20 — No Dreamer bot. Proxy owns the 2026-11-01 auditor-bot revisit.
- 2026-10-20 — Due dates are latest-acceptable deadlines, not targets. Work starts when unblocked and is delivered when done.
- 2026-10-20 — Full speed whenever the user isn't streaming or gaming, overnight included. Independent work runs in parallel. Approvals go in batches.
- 2026-10-20 — The "only fix problems in clips worth posting" rule (2026-10-14) covers only re-editing individual clips, not background or plumbing code.

Newest first. Prune after 14 days.

## Read first

- [[Home]]
- [[Preferences]]
- [[README]]

Shared rules: never post or send anything without the user's OK; never delete VODs without explicit approval; Claude reviews big changes and the user has final say; cloud agents write code, one defect per PR, plan approved first; heavy jobs take the lock file and nothing heavy runs while OBS or a game is running.
