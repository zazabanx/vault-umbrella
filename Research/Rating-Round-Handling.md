# Research: rating-round handling notes (alongside SPEC-RATING-ROUND-v1, which stays unchanged)

- Approval rule (user, 2026-10-20 7:43 PM via Proxy): every outside-creator clip in a rating round is an unapproved candidate. It goes into Reference-Library.md or any reference list only after the user personally approves that clip with a thumbs up. "love it" is a rating, not approval, unless the user says it is.
- Round files keep their format; no column is added or changed for approval. Approvals are recorded only in Reference-Library.md's "Approved reference clips" table, with the date and the user's words.
- Spec answers from the Engineer (2026-10-20): exact view counts; bucket edges go to the higher bucket, and 60 goes in 45-60; dates are the platform's own (YouTube Pacific, TikTok UTC noted in the intro); captions=yes means any burned-in text, with "spoken subs" added to why_it_works when verified; creator is the handle as shown; never guess hook_text.
- When ratings arrive: fill the rating and user_note fields, then send the Engineer the CSV path and the love/meh/not-me counts.

## Engineer answers on OI-038 (2026-10-20)
- game: leave blank when not verified; never "mixed".
- payoff_type: title-based labels are OK, but add "(from title)" in why_it_works. Allowed values now include `unknown`, used when even the title gives no clue.
- TikTok views: rounded counts are OK; say "rounded by TikTok" in the intro so code doesn't treat them as exact.
- Dates: YouTube is Pacific and TikTok is UTC; say both in the intro.
- captions: burned-in text only. A CC or auto-caption track doesn't count; if one is seen, note it in why_it_works.

## Log
- 2026-10-20 8:15 PM: OI-028 ratings recorded (10 love it, 1 meh, 1 not me). CSV sent to the Engineer, summary to the Proxy.
