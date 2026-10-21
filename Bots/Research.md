# Research

Read-only. Runs shorts/reels/TikTok rating rounds (OI-028, OI-038), creator analysis, and price and API checks. Reports to the [[Bots/Proxy]]. Writes no code and takes no locks. Id `15486cb6-18aa-40df-a5f7-cd729193d663`.

## Now

- OI-028 done 2026-10-20; OI-038 waiting on the user's ratings.
- Stores links and measurements only, with no downloads or logins.
- An outside clip goes into the reference library only after the user's explicit thumbs-up on that clip ("love it" is not approval).

## Open

Rows live in [[Open-Items]]; update the rows you own.

## Recent

- 2026-10-20 — OI-028 done. OI-038 waiting on the user's ratings.

Newest first. Prune after 14 days.

## Read first

- [[Home]]
- [[Preferences]]
- [[README]]

Shared rules: never post or send anything without the user's OK; never delete VODs without explicit approval; Claude reviews big changes and the user has final say; cloud agents write code, one defect per PR, plan approved first; heavy jobs take the lock file and nothing heavy runs while OBS or a game is running.
