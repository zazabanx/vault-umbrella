# Long-form YouTube

Long-form Elden Ring YouTube episodes from the 2026-10-07, 2026-10-08, 2026-10-09, and 2026-10-15 stream VODs. Episode cuts are stored on the ArmorATD drive.

## Now

- On hold (the user, 2026-10-25 8:22 AM ET): do not run long-form work until the user lifts the hold. LF-005 to LF-012 wait on the user.
- When the hold lifts: break reports LF-005 (Oct 9 recut), LF-006 and LF-007 (Oct 7, Oct 8), LF-008 (Oct 15), then editor PR5 (LF-009) and the DaVinci package PR6 (LF-011). Upload prep (LF-012) needs the user's OK.
- Plans folder: `/workspace/longform-youtube/plans/` on the bot computer.

## Open

Rows live in [[Open-Items]]; update the rows you own.

## Recent

- 2026-10-25 — Long-form put on hold by the user; nothing runs until it lifts.
- 2026-10-20 — PRs #70, #89, #90 and #91 merged into auto-clip-system main; PC tests passed.
- 2026-10-20 — DaVinci Resolve smoke test passed on the PC (4 audio tracks; fcpxml timeline opens with 2 clips and 4 tracks).
- 2026-10-20 — Re-cut Oct 9 only. Skip the Twitch download. No uploads, titles, or thumbnails until the editor is built. The top editor feature is the break/AFK report.
- 2026-10-20 — The main BRB sign is an empty facecam for a decent stretch. Loading, map, menu, and black screens are left alone. Shorter pauses go in a separate approve/deny list, and approve = cut. Nothing is removed without the user's approval.
- 2026-10-20 — Editor plan v1 approved by Claude. A new `<episode> (final).mkv` next to the original (both kept for now). Frame-exact high-quality re-encode. Plain hard cuts with 2 s padding. One mixed mic+game track is the default audio for the upload file. The final stays on ArmorATD only (transfer to the PC only on request). Dry run first and a per-episode user OK. Redo = the user deletes the final by hand and re-runs. A DaVinci Resolve package (a timeline file pointing at the original with separate tracks) is a later PR after an import test. Resolve Studio 20 is on the PC. Audio layout: track 1 mic, track 2 game, tracks 3 and 4 silent. The default flag is on the mic track.
- 2026-10-16 — Each episode is one plain file cut at the start and end of the Elden Ring segment.

Newest first. Prune after 14 days.

## Read first

- [[Home]]
- [[Preferences]]
- [[README]]

Shared rules: never post or send anything without the user's OK; never delete VODs without explicit approval; Claude reviews big changes and the user has final say; cloud agents write code, one defect per PR, plan approved first; heavy jobs take the lock file and nothing heavy runs while OBS or a game is running.
