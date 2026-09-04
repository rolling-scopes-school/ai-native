# EXT-307 — The Odyssey: your session under glass (after BEVN-202)

> Optional side quest · both tracks · not part of the main route
> Rules: [test task](../README.md) · Quest map: [side-quests/README.md](README.md)

**Why:** context is the main lever of quality ([doc 02](../../en/02-fundamentals.md)) — and it is invisible. You manage what the agent sees without ever seeing it yourself. This quest ends that: you build a visualization of one of your own sessions and look at what actually happened — which files were pulled in, when hooks fired, what the model was really sent. You can't manage what you can't see.

**What it trains:** observability of the agentic loop; reading your harness's own data; the difference between what the harness records and what goes over the wire.

**The task:** take one rich session from a spec-driven task you've done (BEVN-202 is ideal — you have a devlog to compare against) and travel through it. Four chapters, each with its own thing to notice. The final deliverable is **one static HTML page** — opens in a browser from a file, no build step, no server. This is a visualization, not an app: resist the urge to build a framework.

## Chapter I — The ship's log

Claude Code keeps a transcript of every session as JSONL: `~/.claude/projects/<project>/<session-id>.jsonl` — every message, every tool call and its result. (The format is undocumented and may change — parsing it *is* the exercise. Another agent? Find your harness's equivalent log, or skip the quest.)

Parse it and render a timeline: messages, tool calls with the file names they touched, hook firings.

*Notice:* which files entered the context, and when. Is your `CLAUDE.md` there? When did the biggest file arrive, and did it need to?

## Chapter II — Beneath the sails

The log is the harness's diary. The wire is the truth. Point your harness at a local logging proxy (for Claude Code: `ANTHROPIC_BASE_URL` to a small relay that logs requests and forwards them to the real API; or mitmproxy) and capture **one full request**.

*Notice:* how much of the request you never wrote — the system prompt, the tool definitions, the assembled history. Measure them.

> **Warning:** raw captures contain your auth token and your entire codebase. Never commit them. The page shows sizes, structure, and redacted excerpts — not the dumps.

## Chapter III — The sirens

Find the three heaviest items in your context by size. Usually they are not your prompts — they are fat tool results: a whole file read when ten lines were needed, a verbose test run, a dump nobody asked for.

*Notice:* what each one cost. Context growth is money ([EXT-306](EXT-306-cost-of-your-work.md)) — and attention: the model reads all of it every call.

## Chapter IV — Ithaca

Assemble the page. Alongside the timeline, two honest lists:

1. **What stayed invisible** — things you know are in play but neither the log nor the wire shows. Knowing the limits of your observability is half the point.
2. **What you missed** — one event the visualization shows that your devlog entry for that step didn't record.

**Definition of Done:**
- [ ] A single static HTML page in the repo, opens from a file, no build step
- [ ] The timeline distinguishes messages, tool calls (with file names), and hook firings
- [ ] One full API request dissected: system prompt / tools / history, with sizes
- [ ] The three heaviest context items named, with sizes and what they cost
- [ ] The two Ithaca lists: what stayed invisible, and one event your devlog missed
- [ ] No raw captures or transcripts committed — sizes, structure, redacted excerpts only
