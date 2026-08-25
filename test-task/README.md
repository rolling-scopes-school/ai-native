# Test Task: BrownEvents

In front of you is a brownfield: a working conference-management application that nobody has maintained for two years. Your job is to understand it, stabilize it, and build two features on top of it — working in tandem with a console AI agent. What's assessed is not only the result but *how* you work with the agent — which is why the task has traceability rules and a final report.

**Deadline: 14 days** from the moment you get access to the repository.

## What to Do

The task routes are described in [PRODUCT.md](PRODUCT.md) — read it first. There are **two tracks**; choose by the backend stack you actually know — you must be able to *verify* the agent's work, not just apply it:

- **Track A (.NET)** — 12 tasks: set up issues via MCP → understand the code → revive CI → fix the registration flow in .NET → build two features → cover them with e2e tests.
- **Track B (TypeScript)** — 10 tasks: set up issues via MCP → understand the code → revive CI → migrate the backend to NestJS + Prisma, fixing the known defects along the way → build the same two features on the new backend → cover them with e2e tests.

Both tracks have one optional task (BEVN-101, query performance) — not required, but strongly recommended.

About the numbering: `BEVN-xxx` tasks are taken verbatim from the original BrownEvents task library (hence the gaps in the numbers), `EXT-xxx` tasks were added for this pilot. Additions to original tasks are marked with "Pilot addition" blocks.

Tasks go strictly in order: each one builds on the previous — don't skip ahead, you'd only make your own life harder. State which track you chose in your very first PR.

Each task's text lives in its own file under [`tasks/`](tasks/) in this repository. In your first task (EXT-100) you import the whole route as GitHub Issues into your working repository — from then on, when starting a session, hand the agent the current task's issue rather than the whole PRODUCT.md: extra context hurts the agent just as it hurts you.

Beyond the main route there are **[side quests](side-quests/README.md)** — six optional assignments for the highly motivated, about the internals of the process itself: project knowledge for agents, hooks, a critic before merge, your own skill, an autonomous run, the cost of your work. They don't affect the main route's assessment; each explains why it exists.

## The Code

The code lives in a separate **private** template repository, `brown-events-pilot` — access is granted after you apply (write in the [chat](https://t.me/+u5HQoDbqaO4yMTI6)). Once you have access:

1. Click **Use this template** → create **your own private copy**.
2. Add the reviewer as a collaborator on your copy.
3. All your work happens in your copy: issues, branches, PRs, the report.

## Tools

- **A console AI agent** — required: Claude Code, Codex CLI, Gemini CLI, Copilot CLI, or Pi. Cursor, web chats, and IDE plugins won't do — their sessions don't make it into the report (see [codemie-analytics.md](codemie-analytics.md)).
- **Node.js 20+** — to build the report at the end.
- **Docker** — `docker-compose up --build` brings up the whole application (run instructions are in the code repository's README).

## Working Rules

These rules are what threads the task number through the whole chain: ticket → branch → agent sessions → commits → PR. Without them the report is unreadable, so they are mandatory.

1. **One task — one branch.** Before starting a task: `git checkout -b BEVN-001-codebase-map` (task number + a short slug). Run your agent only from this branch.
2. **Start the first message of every agent session with the task number:** "*BEVN-104: bring the API responses to a single format...*". This becomes the session's name in the report.
3. **Commits carry the task number:** `docs: add architecture map (BEVN-001)`.
4. **One task — one Pull Request** in your repository: from the task branch into `main`, the number in the PR title, a link to the task's issue in the description (`Closes #N`). Once you've checked the Definition of Done is met — merge it yourself and move to the next task.

The number of sessions, attempts, and clarifications is **not penalized** — work as you normally would. What will be looked at is the approach: how you frame the task, how you iterate, whether you drive it to a result.

## Process: Free-Form and Spec-Driven

Every task in the route has its mode marked (see the tables in PRODUCT.md):

- **Free-form** (EXT-100, discovery, EXT-110, the Phase 1A fixes, BEVN-101, the frontend fix) — work with your agent however you like.
- **Spec-driven** (the EXT-150 migration on Track B; BEVN-202, BEVN-203, and BEVN-205 on both tracks) — before the first line of code there must be a spec (what exactly is being built, contentious cases resolved) and a plan (how, step by step). Both documents are committed into the task branch together with the code — the reviewer will read them before the diff. For the migration this is not a formality: a migration without a plan burns days.

  - In Claude Code, install the [superpowers](https://github.com/obra/superpowers) plugin for this: its brainstorming → spec → plan → implementation flow does exactly that, saving the spec and plan under `docs/superpowers/`.
  - If you work in another agent — reproduce the same flow: `spec.md` and `plan.md` files in the PR are mandatory.

**CI as a gate.** Starting from the task after EXT-110, a PR merges only with green CI. A red pipeline is part of the task, not background noise.

## Development Log and Defense

Keep `docs/devlog.md` — a work journal, a few lines after each task. Both the agent (ask it at the end of a session) and you can write it; what matters is that it holds *your* take, not a retelling of the diff:

- what you did and what came of it;
- which decisions the agent made *on its own*, and why you accepted or redid them;
- where you had to step in by hand;
- what you would do differently.

The devlog is not paperwork for its own sake. The pilot ends with a **defense**: a call with a trainer where you talk through your work. A good devlog is a ready-made outline for that story; without one, two weeks later you won't remember half of it.

## Final Report

Once every task of your track is merged, build the report on your work with the agent. From the repository folder:

```bash
npx -y -p @codemieai/code codemie analytics --report \
  --last 21d --include-external \
  --project brown-events-pilot \
  --report-format both --report-output ./report/report.html
```

`--project brown-events-pilot` filters by folder name: if you cloned the repository into a differently named folder, substitute yours. The `--last 21d` window covers two weeks of work with a margin; if you worked longer — give exact dates (`--from ... --to ...`).

Then:

1. **Open `report/report.html` in a browser** and check it with your own eyes: only this project's sessions inside, nothing extra. What gets into the report and what doesn't — see [codemie-analytics.md](codemie-analytics.md); in short: session metrics, branches, and the text of each session's first message, but no full dialogues and no file contents.
2. **Commit both files** (`report/report.html`, `report/report.json`) as the final PR into your repository.
3. **Tell the reviewer** the task is done.

## What Will Be Assessed

- The solution itself: is each task's Definition of Done met; the quality of the code and documents.
- The spec and plan in spec-driven tasks: completeness, resolved forks, whether the implementation follows the plan.
- Traceability: can the "task → sessions → commits → PR" chain be read from the repository and the report; is CI green on merges after EXT-110.
- Your work with the agent, per the report and the devlog: how you frame tasks, how you iterate, whether you notice decisions the agent made silently — not the number of attempts.
- The defense: a coherent account of your work on the final call.

## Questions

If something won't start, won't build, or is worded unclearly — write to the reviewer right away instead of losing days fighting the environment. Fighting legacy code is part of the task; fighting the instructions is not.
