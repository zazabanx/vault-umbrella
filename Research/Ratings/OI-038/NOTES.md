# NOTES: ROUND-OI-038 (Research bot), 2026-10-20 ~7:45 PM ET

Read-only. Nothing posted, sent, committed, pushed or downloaded (no video files). No logins. No machine.lock.

## Link check (all 40 rows from RESEARCH-OI-038)
- Method: YouTube oEmbed (`/oembed?url=...`) plus a logged-out fetch of each `/shorts/ID` page (playabilityStatus, viewCount, lengthSeconds, publishDate, owner, description).
- Result: **40 kept, 0 dropped, 0 replaced, 0 unverified-access.** Every short gave oEmbed 200, page 200, playability OK.
- Two single-request timeouts (n4zSGAz4HHE page on pass 1; mLTbcHM9LT8 oEmbed on pass 2) passed on the other pass. Not dead.
- Views were re-read on the final pass, so they are slightly higher than in RESEARCH-OI-038. They are the exact `viewCount` integer.
- The 11 new rows went through the same check (YouTube: oEmbed + page; TikTok: video page 200, `statusCode` 0).

## What was added (11 rows, 41-51)
- **Other games.** The repo (`shared/games/`, the Oct 9 games fixture) and both vaults name only Rocket League, Elden Ring and generic. Twitchmetrics' public page for zazabanx (last 15 streams, Sep 23 to Oct 15) also shows **How to Fish** (2 h on Sep 28) and **Where Winds Meet** (10 min on Oct 13), plus Just Chatting. Twitchtracker, Streamscharts and SullyGnome returned Cloudflare 403s, so this is one source.
  - How to Fish: 5 rows (3 YouTube Shorts, 2 TikTok).
  - Where Winds Meet: 4 YouTube Shorts. It had only 10 minutes on stream, so treat it as a weak shelf.
  - Just Chatting is a category, not a game. The streamer rows already cover it.
- **Elden Ring:** +1 TikTok (verified @kai_cenat, 22.2M, 59 s). Elden Ring now has 7 rows.
- **CaseOh:** +1 TikTok (@caseohgames, 44.8M, 61 s). CaseOh is at the 3-per-creator cap.
- **Nick Fuentes:** still 0. Rumble returned 403 to curl. Page fetches showed only the channel and a 4:30:50 episode. The one Rumble short found (`rumble.com/shorts/v27jmuu`) is posted by `afclips07`, a fan clip account (Rumble oEmbed, 48 s), and shows no view count. YouTube `@nickjfuentes` and `@nickfuentes4152` are not him (OI-028). Nothing to add.
- **Instagram Reels:** 0. `/reels/` pages 302-redirect to the login page.
- **TikTok method:** a logged-out `tiktok.com/@handle/video/ID` page embeds `webapp.video-detail`. That object has `stats.playCount`, `video.duration`, `createTime` and `author`. I got candidate IDs from public listing pages (anontiktokviewer, tokgauge, toklytics) and read every number from TikTok's own page. TikTok rounds playCount at the source (for example 22200000), so it is the exact field but not an exact count. TikTok profile pages still return an empty itemList.
- Candidates I checked and left out:
  - @tenacitytv TikTok 13.9M / 9 s and @alphakep TikTok 2.1M / 13 s: dropped to hold the total near 50.
  - Mr. Swaggerton "this fishing game is literally CS2" (825,782 views, 11 s): How to Fish row 6.
  - Emiru, Where Winds Meet (110,751 views, 14 s).
  - Character-creator memes: Legendskidz 21.8M, celtralis 5.6M and 3.9M. Not gameplay moments.
  - Cosplay/skit #eldenring TikToks (yannisammarr 88M, mataneven 23.6M). Not gameplay.

## Cell rules used
- views: the exact integer on the page (YouTube `viewCount`; TikTok `playCount`).
- creator: the channel handle from the page's canonical URL (for example @tenacitytv_, @caseoh_). TikTok: `@uniqueId`.
- game: filled only when the title or description names it (or a TikTok hashtag like #eldenring). Otherwise blank: **21 rows**. I did not use channel-default keyword lists, because they are often boilerplate. For example, Lacy's 0qvSz-4eGk4 keywords say Fortnite and the title does not.
- length_bucket: <15 = 0-14, 15-30 = 15-29, 30-45 = 30-44, 45-60 = 45-60, >60 = 61+.
- published: YouTube `publishDate` (Pacific). TikTok `createTime` as a UTC date.
- hook_text: blank on all 51. Nothing was watched.
- captions: `unknown` on all 51, because no burned-in text was seen. Page metadata does show a caption *track* (CC or auto-subs, not burned-in) on these rows:
  - YouTube: E4pMd62mYsQ, 7orNpUOO_RQ, DepN0zaCNf4, tfiLeyu02oo, 6j_BQCxHn74, woyE48VUswo, 98kEg2afJ5o, gTl8sLuU588, AWtrZaoBtPE, uZVpD3SQKRw, 407rXPS-xo4, fK6y7EXV21M, bKwpKRN8Se0, rrQbqobhkYk, n4zSGAz4HHE, YhomwPtcWko, 5qyUkI8iCCE, oH7JHuEPqV4, ZOZlGcsaut0, FVqpRDWMmT8, 4EzNyoEIiq4, aPhfP8sFoqM, KOGNYDAO1d8, mfJs7wp6COg, 0qvSz-4eGk4, RQPbAjINT-E, bG2MzP3BT50.
  - TikTok `subtitleInfos`: @caseohgames and @ayegoom rows.
  - I added no "spoken subs" notes, because none were seen on screen.
- payoff_type: a **title/caption-based label**, not a watched verdict. The spec has no blank or unknown value for this field. `other` is used where the title does not show the payoff.
- why_it_works: every sentence starts with its basis. "Title/length only:" (most rows), "From title, length and description:" (rows 02, 05, 06, 27, 35, 41, 46, 48, 49), or "From TikTok caption and length:". Rows 01-40 keep the RESEARCH-OI-038 sentence text. None of them claim on-screen text, pacing or cuts.

## Counts
51 rows (about 50; trim 2 if the cap is strict): 47 YouTube Shorts, 4 TikTok, 0 Reels.
- Games: Elden Ring 7, How to Fish 5, Where Winds Meet 4.
- Streamers: 17 × 2 YouTube, plus 2 TikTok (Kai Cenat Elden Ring, CaseOh).
- No creator has more than 3 rows.

## Remaining gaps
- No hooks, burned-in captions or pacing. Watching needs playback, which asked for a sign-in in OI-028.
- Game blank on 21 streamer rows.
- No Reels (login wall). No Nick Fuentes.
- Other-games evidence is one third-party page that covers only the last 15 streams.
- The Burnt Peanut and bluscr3n (Posting.md creator list) are not in this round. They were also missing from OI-028.

## Spec questions for the Engineer
1. Is a blank `game` OK, or should unverified streamer rows be `mixed`?
2. `payoff_type` has no unknown value. Is a title-based label OK, or should a value like `unknown` be added?
3. TikTok `playCount` is rounded by TikTok. Is that OK as "exact as shown"?
4. TikTok dates are UTC, not Pacific. Should the intro wording cover both?
5. Should a caption *track* (CC/auto-subs) count toward `captions`, or only burned-in text?
- Dropped original row 49 (@BlueSquadronClips, lowest-viewed new row) to keep the round at 50; rows 50-51 renumbered 49-50.
