> Copy of `REVIEW-POST-CP2-v1-r1.md` (box handoffs), added 2026-10-22. See [[Roadmap]]. Text below is unchanged.

<!-- Opus r1 review of PLAN-POST-CP2-v1.md | fresh session | models ['claude-opus-5-5'] | --effort xhigh | Claude Max (no API key) | read-only | total_cost_usd 0.8142228 notional | Oct 22 2026 -->

VERDICT: APPROVE WITH CHANGES

The diagnosis and main-track direction are right. The queue, the decisions and the renewal call need edits. One caution: "7 of 9 misses were picking misses" is unproven. Those 7 rows have no notes; M1 decides.

**1. Queue moves**
- Move start-fix PR 1 from item 11 to item 9, right after 3a. Move PR 2 from 14 to 10.
- Make M2 item 11, then run M3 on the Mac alongside the PC fixes. Pull up the OI-059 wrapper (20) as well. These are CP3's critical path; the reliability PRs aren't.
- Post-pack docs (10) goes behind the gate. Nothing is postable yet.
- CP3 (29) must also wait for 18, the thin-path banned-line gap. Thin is now the only path.
- Start chat logging (26) before Oct 27, so CP3 streams have chat. Run it on the Mac, not the box.
- Cut 30–32. The rulebook, overlap check, Float trial and Clip Renders bot upgrades are upkeep for a Grok team you're dropping. Keep "never invent a quote, speaker or timestamp" as one prompt line.
- Add two items: turn off Grok auto-renew, and list what depends on the box (read-only). Re-scope 34 as local launchd / Task Scheduler scripts. That is the migration.

**2. Guard next to 3a? Yes.** Late starts are the main problem on 5 of the 7 needs-work drafts, the ones closest to postable. But the test bar doesn't match the guard. Using preroll's numbers, the guard as written:
- puts BALL at −14 s (bar: 17.2), BRO at −12 (bar: 18.3) and TREE at about −6 (bar: 12.3);
- likely leaves RUN unchanged, because only a video burst comes before it;
- can't move DAD earlier than the pick start.

Make PR 1's bar "BALL at −14 s or earlier, locked clips stay green." Apply the 7-draft bar only after PR 2 plus a ~15 s export front-pad (for DAD).

**3. Wrong defaults**
- **4 should be No.** "What are you doing" and "where are you" likely fire constantly in team games. They already go to the $0 rage collection.
- **3:** approve together with a preset rule: a phrase that fires more than twice a stream drops to a ranker cue. That avoids a second ask. "Oh my god" will probably trip it.
- **1:** take item 34 out of the fix OK. It's the CP4 build.
- **2:** lift the freeze, but dreaming stays log-only. Docs already outnumber code 24 of 26 merges.
- **15 is a fake decision.** "Keep Grok unless CP4 has passed" by Nov 10 can't come out any other way, because CP4 runs Nov 12–21.
- **Missing:** the CP3 pass mark (§10). The "done criteria" need hands-off, which won't exist by CP3.

**4. Reduced list: 5 user decisions, down from 15**
- **A.** Lift the freeze; dreaming stays log-only. *Default: yes.*
- **B.** Approve the trigger list with the auto-demote rule; scream triggers go to the rage collection only. *Default: yes.*
- **C.** CP3 runs on fresh streams from Oct 27, before the OI-036 overview. Postable means ready or perfect. Pass: at least 1.5 postable per stream on average, over at least 3 streams. CP4 cost mark: $2 per stream. *Default: yes.*
- **D.** Caps from now: PC $20, Mac $10. *Default: yes.* October has $1.10 left.
- **E.** Renewals, as in §5.

**Ask only if triggered:** the quality-bar goal (8) when CP3 is scored, the pick-first switch, any deletion (14: default is delete nothing), and Gemini.

**Proxy plus Claude decide:** 1, 6, 7, 10, 13 and cached trends. After Nov 12 that means Claude alone, keeping a decision log.

**5. One renewal plan**
- **Today:** turn off Grok auto-renew. It can be undone.
- **Oct 23–Nov 2:** no migration work. Build any new automation on the Mac/PC, not the box.
- **Nov 3–9:** migrate, capped at 2 days (Tailscale/SSH, flock, run_pipeline, CLAUDE.md files, memory export). Run at least one CP3 stream locally, with Grok as the fallback.
- **Nov 10, go/no-go:** if that local run worked, let Grok lapse Nov 12. If not, renew one month; $60 beats a broken CP4.
- **Nov 18:** renew Max 5x for one month. Moving to Pro limits during CP4, right after losing Grok, is the wrong week to save money. The $60 Grok saving mostly covers it.
- **Dec 4 stop check:** if the project continues, move to Pro on Dec 21. Go back to Max if you hit the limit more than twice a week (tooling.md's rule).