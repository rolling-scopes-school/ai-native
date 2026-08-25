# EXT-304 — Your First Skill (after any two spec-driven tasks)

> Optional side quest · both tracks · not part of the main route
> Rules: [test task](../README.md) · Quest map: [side-quests/README.md](README.md)

**Why:** what separates a factory from "a team with an agent" is that a factory leaves tooling behind: reusable, versioned packages of "how tasks of this class are done". Until you've left at least one behind, your knowledge dies with the chat.

**What it trains:** extracting an atomic, repeatable action; a skill as a unit of use and of testing.

**Real-world case:** in production factories skills number in the dozens against a handful of agents (33 skills to 7 agents in one of the strongest cases) — because a skill is reused by many agents, while a fat prompt is reused by none.

**The task:** find an action in your devlog that you have done at least twice (for example: "check a task's DoD against the diff", "update an endpoint's swagger descriptions", "write a PR walkthrough"). Package it as a skill (`SKILL.md`: when to apply, the steps, the done criterion) under `.claude/skills/` and apply it on the next task.

**Definition of Done:**
- [ ] The skill is committed and applied at least once (visible in the devlog)
- [ ] It passes the atomicity check: it can be verified in isolation from other steps
- [ ] The devlog notes what changed compared to "just asking the agent"
