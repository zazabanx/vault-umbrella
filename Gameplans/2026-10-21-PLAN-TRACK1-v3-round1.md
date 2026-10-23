> Copy of `PLAN-TRACK1-v3-round1.md` (box handoffs), added 2026-10-22. Round 1, not approved. Approved version: [[Gameplans/2026-10-21-PLAN-TRACK1-v3]]. Text below is unchanged.

<!-- STATUS (11:37 AM ET Oct 21): v3 FINAL WRITER (round 1 on Opus 5.5) — fresh review says VERDICT: REVISE, more blockers exist: no. Stopped per the 2-round cap; NOT approved. Writer: Claude Code 2.1.306, claude -p fresh session, modelUsage claude-opus-5-5, --effort xhigh, --permission-mode plan, read-only clone of main 1daac72 + vault-umbrella 53e21f2, 11:19:22-11:29:30 AM ET. Text below is Claude output verbatim from the Stamp line; the trailing writer note was requested by the operator prompt (wc -w: body 590, with note 806). 4.8 draft kept as PLAN-TRACK1-v3-opus48-draft.md. -->

Stamp: Claude Code / user's Claude Max account / claude-opus-5-5 / writer

# PLAN-TRACK1-v3

## Short version
- Build only: comparative ranker, thin edit path, ratings writer.
- Footage: Oct 24–30 test uses ONLY existing Oct 9/14/15 transcripts, no Oct 27–29 footage. New streams from Oct 27: detect+transcribe only, no render (call 5).
- Scout replay DONE ($0.037, 36 Haiku calls; 0.5 confidence everywhere; Oct 15 40-row cap; quote-check drops 16/21/53): candidates only.
- 7 calls settled; no Decisions line. Holds: no other scans; add-only `Needs_Your_Review`; protected folders; Oct 9 clip 14 locked. HEAD `1daac72`.

## PRs in order
One defect, `cc/<topic>` draft, fresh-session review (Opus big/Sonnet small), PC runner tests.
- **T1-0 docs:** stale Status/Open-Items (OI-045 done, OI-048 settled, OI-036 waits dropped). Gate Engineer; dep none.
- **T1-2 ranker:** no content ranker. `detector/rank_windows.py`, rubric, test; `llm_cost.py` Opus price, `ranker` budget. Main+overflow+scout finds→one `Event` list; one `claude-opus-5-5` `xhigh` call/stream orders ALL, one-line reason each, no scores, no fallback (other models need Proxy OK). `CLIP_THAT` pinned top 3–5 instead of `SPOKEN_RANK_BONUS`; Twitch marker: OI-054. Test: all ordered+reasoned; scores rejected; `CLIP_THAT` 9th→≤5; `detect.json` unchanged. Gate PC; dep none.
- **T1-R1 CP1+judge:** no blind proof. `plan_replay.py`, card tool, test. Judge=this test on frozen protected set (Oct 9/14/15, protected clips; never prompt examples), agreement on unseen clips; user sees borderline picks+small random sample. `machine.lock`. Test: cards unlabeled; frozen IDs not in prompts. Gate PC, CP1; dep T1-2.
- **T1-3 CostGuard:** editor calls bypass cap. `windows_editor_skeleton.py`, `content_generator.py`: `editor` budget seeded with October spend; $1/run, $10/mo; unknown model refused; preflight. Test: over-cap/unknown refused pre-call. Gate PC, blocks render; dep #83.
- **#61:** merge once Mac run pasted; Fix B, loudness gate out of chain.
- **T1-7 thin path:** chain moves model start/end. Same files. New plans: model start/end+6 hard checks, skip `finish_checked_variations`; 45s target, 60s payoff; `max_cuts` 0 all games incl. Elden Ring bosses; post-test ≤1 cut, stated reason, blind vs no-cut. Clips 01/14 old path. Test: boss plan with cuts→0 cuts, start/end kept, chain uncalled. Gate PC; dep T1-3.
- **T1-5 ratings writer:** manual tallies. `ratings_writer.py`→`vault/scorecards.csv`; stamp (commit, prompt version, model, ranker score=rank); session start/end→minutes/stream beside ledger cost. Test: fixture→exact rows incl. minutes; re-run adds none; malformed rejected. Gate PC; dep none.
- **T1-R3 CP2 render:** nothing to rate. `detector/export_picks.py`. Smoke test (render one clip, check frames), then stamped add-only `T1 R<rank>`→`Needs_Your_Review\<date>\` via Dropbox, after tuning; `machine.lock`. Gate smoke, CP2; dep T1-3, T1-7, #61.

## Checkpoints/done/stop
- **CP1 (Oct 24–26):** blind: ranker vs detector top-5. PASS: wins ≥2/3 streams, ≤1 known "no". Loses ≥2/3→halt.
- **CP2 (Oct 30):** thin top 3–5, 3 also old path, unlabeled; ≤10/session. PASS: thin≥old; ≥40% moments 4–5; ≤15 min/stream.
- **Done (PASS):** ≥1 postable clip, or honest "nothing strong tonight" only if user agrees after a 2-minute look at top cards; FAIL if they spot a missed moment. 6–7 postable/week tracked separately.
- **Stop:** not met by Dec 4→2-minute phone pick is the product.
- Until CP2 review: log-only dreaming (both routines), 2-round cap, Decisions: checkpoint results only; Nov 1 asks user.

## Pause list (never closed)
- **Hands-off:** four-outcomes PRs 1–7, A/B1/B2 (hand moves); scout S1b/S2/S3; Fix B; #77; OI-029.
- **Render Oct 27–29, Nov 3–5:** after OI-036 overview+user OK.
- **No date:** folder guards, any-game detection, archive script, single-clip polish, Publishing bot, #88, CR-004.
- **Superseded:** OI-034/#16, OI-024, OI-031 Oct 9/15.
- Out of scope: Mac VOD deletion (ops).

## Open user questions
1. (Proxy) Boss clip truly needs a cut? **Rec:** no exception; flag it.
2. $10/mo, seeded, may not fit CP1+CP2. **Rec:** over at preflight→stop, ask.
<!-- writer note: completeness: plan is 590 words by wc -w, this note excluded, and the later inputs won over stale context, namely the 10:43 brief (main d1a3cf9, 7 calls pending), vault/Current-Holds.md and umbrella OI-048 (calls undecided, VOD deletion no, no Oct 27 detect carve-out); Current-Holds still needs its owner to refresh it because T1-0 is kept to Status/Open-Items as asked; .plan-inputs/PLAN-TRACK1-v3-draft.md is unlisted and older than -long; CostGuard has only the Haiku price, so T1-2 adds Opus 5.5 at $4/$20 per MTok (claude-api skill reference, cached 2026-10-06), with thinking billed as output and effort set to xhigh explicitly because the default is medium, est. $0.3–0.8 per stream call; no Twitch marker code exists; the review checklist T1-5 parses is not in the repo, so the fixture must come from a real batch; the detector tags on/off question moves to T1-2's own short plan; (e) included — session start/end in the same scorecards.csv rows gives minutes per stream beside the ledger's per-stream cost, adds no rule, and CP2's 15 min/stream check needs it; footage: the Oct 24–30 test uses only the existing Oct 9/14/15 transcripts, and Oct 27+ streams get detect+transcribe with no render, but the watcher hard-codes the export flag, so run the detector without it or add a switch (Mac run, rule 8) -->