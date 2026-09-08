// Reviewed by Dzmitry Varabei on August 31, 2026.

## AI-Assisted Software Development (AI SDLC)

Understand how AI is built into the development lifecycle on an AI Native position: the agent writes most of the code, and the developer is responsible for context, control, and acceptance.

On these projects this way of working is called a "factory". Note that "factory" is EPAM's own term, not an industry-standard one. An AI factory is a defined, repeatable process for AI-assisted delivery: a protocol of phases, review gates between them, and a shared set of agent skills that the team maintains. Factory setups differ from project to project; the areas below are the common base that lets you join any of them.

AI SDLC builds on the regular [SDLC](./sdlc.md) base: you cannot review, accept, or stop work that you cannot judge.

A junior developer should understand these areas and be able to take part in them:

* **Working with a coding agent in a codebase** — do day-to-day tasks through a coding agent (Claude Code or similar): run sessions, give the agent the right context, read and verify its output. Know the typical failure modes: answers that are wrong but sound confident, ignored project conventions, losing direction on long tasks. Understand that the developer, not the agent, is responsible for the result.

* **Context engineering** — understand that the quality of the agent's output depends on what the agent has read before working. Create and maintain project knowledge files (CLAUDE.md / AGENTS.md): how to run and test the project, the conventions, the architecture in a few lines, known traps. Keep these files updated as the project changes.

* **Spec-driven development** — work in steps: task → spec → plan → implementation. On production projects almost every task follows this or a similar protocol; doing a task in one prompt is usually not an option, because quality is achieved by reviewing the intermediate steps (the spec, the plan) — not only the final code. Write acceptance criteria before implementation starts, and accept the result strictly against them.

* **Reviewing and controlling AI-generated code** — review every AI-produced diff as if it came from an unfamiliar author. Before merge, run a critic pass: a fresh agent session that gets only the spec and the diff, and is asked to find differences from the spec, not to praise the code. Give every finding an explicit verdict: accept and fix, or reject with a reason.

* **Guardrails and rule automation** — understand that neither humans nor models follow written reminders consistently. Turn repeated rules into automation: hooks that block a bad commit, auto-run tests after a change, warn about an oversized diff. The principle: make breaking the rule impossible instead of asking the agent "not to forget".

* **Agent tooling: MCP and skills** — connect the agent to external tools through MCP servers (issue trackers, documentation systems, and so on). Package actions you repeat often as reusable skills instead of explaining them again in every session.

* **Autonomous runs** — before letting an agent work without supervision, write a complete task contract: objective, inputs, tools, constraints, Definition of Done, validation, budget, failure policy. Do not correct the agent mid-run. Accept or reject the result against the written DoD, not against impressions.

* **Cost awareness (tokenomics)** — see the price of AI work: read token and cost reports, and attribute cost to stages (spec, plan, implementation). Know that on production projects the cost of a task is estimated already at the spec / plan / task level, before implementation starts. Compare approaches by cost. Notice when a task is costing too much, so it can be stopped and re-scoped early.

A junior developer is **not expected to design agent platforms, orchestration pipelines, or the AI factory itself from scratch**. They should be able to work inside the agentic workflow the team has already set up.

## Questions already asked in interviews

* How would you onboard an agent into a project? (context engineering; agent tooling)
* Why were hooks invented? (guardrails and rule automation)
* What context does the agent get when a session starts? (working with a coding agent; context engineering)
