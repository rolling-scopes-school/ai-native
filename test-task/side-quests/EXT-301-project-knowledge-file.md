# EXT-301 — Project Knowledge for the Agent (after BEVN-003; Track B: update after EXT-150)

> Optional side quest · both tracks · not part of the main route
> Rules: [test task](../README.md) · Quest map: [side-quests/README.md](README.md)

**Why:** context is the main quality lever for an agent: the same agent produces garbage or a result depending on what it has read before working. The project rules file is the first thing an agent reads — and this repository doesn't have one.

**What it trains:** context engineering; turning knowledge "for humans" into an asset that a machine executes.

**Real-world case:** in modernization projects the first phase is Knowledge Extraction: guides to the legacy system are baked into agent instructions *before* any work starts; without this, the agent confidently writes code that ignores the project's conventions.

**The task:** from your codebase map (BEVN-001) and audit (BEVN-003), assemble a `CLAUDE.md` (or `AGENTS.md`): how to run and test the project, conventions, the architecture in five lines, known traps. Then verify the effect: give the agent the same small task in a session without the file and with it.

**Definition of Done:**
- [ ] The file is in the repository root, written for the agent (imperative, no filler)
- [ ] The devlog has a before/after comparison on a concrete example
- [ ] On Track B the file is updated after the migration
