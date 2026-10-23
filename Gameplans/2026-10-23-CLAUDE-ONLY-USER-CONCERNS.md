# Claude-only switch: the user's concerns, habits and must-haves

Written by Proxy, Oct 23, 2026, 12:20 AM ET, from the Oct 22-23 night session. Claude should read this before designing any Claude-only setup. The user's bar: the switch only happens if Proxy and Claude are both confident it will be **fully seamless and as easy for the user as it is now with Proxy**.

## Who the user is and how they work
- Solo streamer. They say staying organized and managing many moving pieces at once is hard for them. Routing work between tools or sessions is a real weakness, not a preference.
- Today they talk to ONE chat (Proxy). It reaches the Mac, the PC, GitHub, the vault and every specialist bot, and it collects every approval in one place, mostly from their phone.
- They ask lots of plain-language questions ("what is cron?", "is a session a new conversation?"). Answers need to be plain, warm and short, with no jargon.
- They do their own hands-on work (rating clips, freeing disk) on the PC, not the Mac.
- They want ETA updates and a clear "it's ready" signal when they're waiting on something, like the CP2 drafts.
- They give decisions in quick bursts, often by replying in chat instead of tapping a card, and expect the assistant to work out which question they answered.
- Standing rule (Oct 22, 11:49 PM): no fixed dates. Work goes task to task, back to back, foot on the gas. Only real outside gates count (billing, a new stream existing, approvals).
- They want Claude's view on big plans, and they want Claude's answers brought to them unfiltered.

## What Proxy does tonight that a Claude-only setup must replace
On one night (Oct 22, about 8 PM to 12:20 AM ET), Proxy:
- Relayed the CP2 scoring, then turned the user's ruling into the official result.
- Got Claude's post-CP2 plan and turned it into 5 plain decisions (A-E) for the user.
- Turned two engineer plans (chat logging, triggers/rage) into 4 and 7 plain questions with recommendations. It took back the user's chat replies, including a mid-stream change to the trigger classes, and passed exact answers back.
- Caught a time-sensitive question (VOD chat expiring) and re-asked it when the user skipped the card. The answer turned out to be "only the recorded streams".
- Kept a live queue Page, and edited it as items moved.
- Decided small technical calls with Claude under the user's approval rule, without bothering the user.
- Ran a scheduled check that found a missed nightly note, then sent the fix to the engineer for the morning summary.
- Remembered dozens of standing rules (never post without OK, never delete VODs, G-DRIVE read-only, paid API key only for the clip pipeline, no .env reading, machine.lock, nothing heavy during OBS/games/Resolve, one defect per PR, plan first, 2-round review cap).

## Failures seen with the current setup (the new setup must prevent these)
- A render sat idle about 1 hour because an agent forgot a step in a chain.
- The nightly docs routine merged PRs without its required quick review check.
- The umbrella vault's nightly daily note was never written, and nobody noticed until a separate check ran.
- A box restart wiped /tmp and lost a plan file, which had to be recovered from logs.
- The PC test harness lived only in %TEMP% until it was committed.
- A silent Oct 17-21 switch in which models did the work.
- A tidy-up chore stalled behind the main engineer's work.
- Docs outran code: plan bloat, and 24 of 26 merges were docs.

## The user's specific concerns about Claude-only
1. **Becoming the router.** They'd have to pick which Claude session or project to talk to. They worry they can't keep track of many pieces.
2. **Memory across sessions.** Will Claude remember the project automatically? (Answer given: `CLAUDE.md` loads at the start of each new conversation. A resumed weeks-old conversation won't see vault changes unless a startup hook rereads them.)
3. **Work between sessions.** Who keeps things moving overnight and starts the next task when one merges? Something has to wake Claude up: cron/launchd, GitHub Actions or scheduled tasks.
4. **Quiet failures.** "I would have a real hard time finding out which scheduled job breaks if it does break quietly." They need alerts that come to them and say exactly what broke, plus a daily all-green message so silence never hides a failure.
5. **Approvals scattered** across GitHub, notifications and terminals, instead of one place.
6. **Setup effort.** They want Claude to build and maintain the automations, not do it themselves. At most they'd paste one key into a settings page, with guidance.

## Fixes discussed so far (starting points, not decisions)
- One main Claude orchestrator with a `CLAUDE.md` that reads the vault's Roadmap, Decisions and Status first and updates them after.
- A startup hook so resumed conversations reread the vault.
- Every fixed sequence becomes a script (detect, rank, transfer, render, notify), so nothing depends on an agent remembering a step.
- Scheduled jobs (launchd on the Mac, GitHub Actions) wake Claude with something like "read Status, do the next item, report back".
- Missed-job alerts: each job checks in with a free monitor (for example healthchecks.io) and the phone gets an alert if a check-in is missed, plus a morning all-green summary.
- The vault is the long-term memory and to-do list.
- Tailscale plus SSH for Mac/PC access, with lock files in the scripts.
- Moving off the Grok box: our audit estimate is about 3-4 days (BOX-DEPENDENCIES-2026-10-22.md); Claude's earlier guess was 1-2.

## Open question for Claude's plan
Can there be ONE place the user talks to, ideally on the phone, that knows everything, routes it and collects approvals the way Proxy does? If not, what's the closest thing, and is the gap honestly small enough to call the switch seamless?
