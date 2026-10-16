# Build or improve

> Draft, not in force, until this file lives in the private umbrella repo. Delete this line when copying. In that repo, save this note as `Templates/build-or-improve.md`. The live AutoClip playbook is [[build-or-improve]]. The stamped steps are in [AGENTS.md](../../../AGENTS.md).

Stamp on this proposal: `build-loop v1`. AutoClip's product copy is `build-loop v2` (the 2026-10-16 plan-before-code decision in [AGENTS.md](../../../AGENTS.md)). Do not copy this v1 block over that product file. When this proposal's stamp changes, update the product copy in a pull request. Do not schedule the compare.

Step 1 of any run is that product's master note. Then follow the steps below. Do not copy product names, clip ids, or lock numbers into this note.

1. Plan. Name one defect and the success tests: a test that fails first, and an observable "done when". Read that product's known-problems note and its locks. Link the lock file. Do not copy the numbers.
2. Build. One small draft pull request, test first, using that repo's PR template. Agents never mark a PR ready.
3. Review. Claude reviews against that repo's checklist.
4. Real test on the product's machine. Tests that would call a paid API stay offline.
5. The user reviews only what needs human eyes.
6. Merge, then update that product's status, known problems, and the day's note.

One defect per pull request. Never delete the user's source media, drafts, or backups. No secrets in the vault. The product copy of these steps is the one Cursor reads. This note is the source of the stamp.
