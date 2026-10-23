> Copy of `PLAN-TRACK1-v3-opus48-draft.md` (box handoffs), added 2026-10-22. Draft, not approved. Approved version: [[Gameplans/2026-10-21-PLAN-TRACK1-v3]]. Text below is unchanged.

<!-- STATUS (updated 11:08 AM ET Oct 21): v3 WRITER REVISION DONE (10:22-10:24 AM, model per session log: claude-opus-4-8 — NOT Opus 5.5); FINAL EDIT + REVIEW NOT YET RUN.
Paused 11:07 AM ET on the user's rule: no new `--model opus` run until the verified full Opus 5.5 model ID arrives (the alias runs claude-opus-4-8).
Two final-edit attempts (10:32-10:58, killed with no output after ~26 min; 11:00-11:05, interrupted) left intermediate plan-mode drafts only: /workspace/v3work/salvage/ (715 and 961 words, not final).
STILL PENDING in the final edit (prompt ready: /workspace/v3work/condense-prompt.md, decisions: /workspace/v3work/inputs/ + clone's .plan-inputs/DECISIONS-2026-10-21.md):
 1. <=600 words (this text is 922).  2. Comparative ranker (one call, ordered list + one-line reasons, no 0-10/subscores), scout only finds, detector main+overflow + scout finds = one Event candidate list (detector/detection_heuristics.py:288).
 3. CP2 smoke test (render one clip, check frames).  4. (d) state Oct 24-30 test uses Oct 9/14/15 transcripts vs Oct 27-29 footage, reconciled with the Oct 27 detect+transcribe-only lift.
 5. (e) review minutes in T1-5 if cheap.  6. 10:49 AM user answers (6-7 clips/week; thin path new-plans-only blind-on-3; Oct 27 detect+transcribe no render; Mac VOD delete approved as separate ops task; done definition, ranker model, dreaming/2-round pause still open).  7. HEAD 473af8d.
Text below: Claude's output verbatim from the Stamp line (the Stamp says "opus"; actual model claude-opus-4-8). -->

Stamp: Claude Code / user's Claude Pro account / opus / writer

# PLAN-TRACK1-v3

## 1. Short version
- Next 10 days build ONLY: (a) content ranker proven blind side-by-side vs today's detector (CP1, Oct 24–26); (b) thin edit path — model sets start/end then ~6 hard checks, 41-step chain skipped for new plans (CP2, by Oct 30); (c) ratings-log writer. Editor CostGuard first (hard prereq for any render).
- Holds stay: no new VOD scans (replay of existing transcripts OK), add-only drafts into `Needs_Your_Review`, protected folders, Oct 9 clip 14 locked (old path).
- Scout replay DONE ($0.037, 36 Haiku calls): top picks mostly new (Oct 9 3/5, 14 4/5, 15 5/5); nearly all 0.5 confidence → ranker needs its OWN content scoring. Oct 15 hit 40-row cap; quote-check dropped 16/21/53 (Oct 9/14/15). Scout output = candidates only.
- HEAD `7c9fe2c`. Haiku price verified — no verify step.

## 2. PRs (one defect each; `cc/<topic>` branch, draft, fresh-session review — Opus big / Sonnet small; PC tests via runner)
- **T1-0 docs** — Status/freeze, mark scout replay done, retire OI-036 waits. No test. Dep none.
- **T1-2 ranker** — *detector has no content ranker.* New `detector/rank_windows.py` + test + `rank_rubric.md`. Own score (game/on-screen). The user's "clip that" voice trigger / Twitch marker is the **STRONGEST** input — reuse `shared/spoken_triggers.find_spoken_triggers`/`CLIP_THAT`; it **replaces** the trigger weight with a hard override so a marked moment always lands top 3–5 (not additive). Energy score stays out (test tags on/off). Candidates = scout replay + detector main/overflow; surface 40-row cap + quote-check drops. Test: fake client → deduped top-10, marked moment forced into top-5, `detect.json` unchanged, offline. Gate: PC PASS, ≤$0.05/100-win. Dep none.
- **T1-R1 CP1 + judge** — reuse `editor/plan_replay.py`; ranker replay Oct 9/14/15 (no scan); blind shuffled-card tool, ranker top-5 vs detector top-5. The judge is calibrated on the user's ratings against a **frozen, protected test set** (Oct 9/14/15 + protected clips; never used as prompt examples), agreement measured on unseen clips — this IS the ranker test, not a second judge. Show the user borderline picks + a small random sample (not "disagreements"). `machine.lock`, no OBS/game/Resolve. Gate = CP1. Dep T1-2.
- **T1-3 CostGuard** *(prereq, hard gate for render)* — *editor paid calls bypass the cap.* Wire `windows_editor_skeleton.py`/`content_generator.py` through `shared/llm_cost.py` `CostGuard`; add `editor` budget **seeded with October's earlier editor spend**, price-by-model (refuse unknown), image w×h/750, 16k/20k plan ceiling; $1/run+$10/mo+preflight. Dep #83.
- **#61 merge** — merge once its Mac run is pasted, with Fix B + loudness gate out of the chain.
- **T1-7 thin path** — new-plan branch: model start/end on word times, ~6 hard checks (inside source, word-snap, ≤60 s, facecam, slur mask, spellings); `finish_checked_variations` skipped for new plans; 45 s target/60 s payoff. **Cut step LOCKED: `max_cuts = 0` for EVERY game, Elden Ring bosses included, Oct 24–30.** Post-test only (not built now): at most 1 cut, used only with a model-stated reason, blind-tested vs no-cut before keeping. Clips 01/14 stay old path. Test: new plan keeps model start/end, chain skipped, `max_cuts=0` enforced. Dep T1-3.
- **T1-5 ratings writer** — *CP2 tallies by hand.* Reads `vault/Jobs/review-batch.md` → appends `vault/scorecards.csv`; each row carries a **version stamp (commit, prompt version, model, ranker score)**. Test: fixture `review-batch.md` → exact `scorecards.csv` rows; idempotent re-run (no dupes); malformed line rejected. Dep none.
- **T1-R3 render CP2** — new `detector/export_picks.py` (reuse `export_clips`, ±15 s), add-only `T1 R<rank>`→`Needs_Your_Review\<date>\`; each draft carries the version stamp; **render runs after the tuning steps**; Dropbox transfer folds here; preflight ≤$1; `machine.lock`. Dep T1-3 + thin path.

*Superseded:* v2 T1-4→T1-R3; T1-6 length + T1-8 no-cuts fold into thin path (cut step now locked to 0).

## 3. Checkpoints
- **CP1 (Oct 24–26):** blind one-line cards, ranker top-5 vs detector top-5/stream; user ticks keepers. **PASS:** ranker wins ≥2 of 3 streams AND ≤1 known "no" in its top-5. **Stop:** loses ≥2 of 3 → halt, phone-card fallback.
- **CP2 (by Oct 30):** render top 3–5 via thin path + 3 clips also old path, unlabeled; rate ≤10/session. **PASS:** thin ≥ old on the blind 3, ≥40% moments 4–5, ≤15 min/stream.
- **Done:** a stream passes with ≥1 postable clip, OR system says "nothing strong tonight" and user agrees after a card check; a morning message always fires. **Stop rule:** not met by Dec 4 → 2-minute phone pick is the product.

## 4. Reconciled pause list (paused, never closed)
- **Trigger CP4/hands-off:** four-outcomes PRs 1–7+A/B1/B2 (move files by hand meanwhile); scout S1b/S2/S3; Fix B transcribe-then-detect; #77+OI-029.
- **Until CP2:** OI-014+PX-001 Sunday run, OI-015 Proxy, Long-form lane.
- **No date:** folder guards, stall alerts, any-game detection, archive script, single-clip polish, Publishing bot, judge #16; #88; CR-004 (clip 14 → re-approval).
- **Superseded by ranker:** OI-034/024, OI-031 Oct 9/15, OI-036 waits.

## 5. Open user questions (new only; each with Rec)
1. If the test truly needs an Elden Ring boss cut exception, add it? **Rec:** no — hold `max_cuts=0`; flag to the Proxy only if a boss clip proves it. *(Cut-default question removed — decided.)*
2. Ranker candidates = detector main+overflow+scout finds? **Rec:** yes.
3. Replay detector yelling/laugh/goal tags on/off, keep winner (score stays out)? **Rec:** yes.

**Scan hold:** lifted for Oct 27–29 and Nov 3–5 **only after** the OI-036 overview + user OK (detect+transcribe, no render).

**7 undecided direction-review calls (not planned around):** (1) "nothing-strong" passes; (2) weekly posting target; (3) strong model for ranking + raise $10 cap after CP2; (4) **Mac VOD delete — no**; (5) thin-path new-plans-only, blind-on-3; (6) scan-hold shape; (7) pause Sunday dreaming + no new Decisions lines.
