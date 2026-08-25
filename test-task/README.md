# Test Task: BrownEvents

> Читать по-русски: [README.ru.md](README.ru.md)

In front of you is a brownfield: a working conference-management application that nobody has maintained for two years. Your job is to understand it, stabilize it, and build two features on top of it — working in tandem with a console AI agent. What's assessed is not only the result but *how* you work with the agent — which is why the task has traceability rules and a final report.

**Deadline: roughly 14–20 days** from the moment you get repository access. That's a guideline, not a cutoff — taking longer is fine, just tell the reviewer.

## What You're Working With

BrownEvents is a conference management application built two years ago by a team that has since moved on. The app works — conferences can be created, sessions are listed, attendees can register. The codebase, however, has not been maintained. Your job is to explore it, understand it, and improve it.

The stack is **ASP.NET Core 6 + EF Core 6 + React + Vite + PostgreSQL**. Run `docker-compose up` to get a working environment before starting any task.

| Entity | Key Fields |
|--------|-----------|
| **Conference** | Id, Title, Description, Location, StartDate, EndDate, Status |
| **Session** | Id, Title, Description, StartTime, EndTime, Capacity, ConferenceId, SpeakerId, RoomId |
| **Speaker** | Id, FirstName, LastName, Bio, Email |
| **Room** | Id, Name, Capacity, Location |
| **Attendee** | Id, FirstName, LastName, Email |
| **Registration** | Id, ConferenceId, AttendeeId, RegisteredAt, Status |

## The Route

You work **individually**, tasks strictly in order — each one builds on the previous, so don't skip ahead. There are **two tracks**; choose by the backend stack you actually know — you must be able to *verify* the agent's output, not just apply it. State which track you chose in your very first PR.

**Track A — .NET.** Stabilize the existing backend, then build features on it.

| # | Task | Theme | Process |
|---|------|-------|---------|
| 1 | [EXT-100](tasks/EXT-100-import-issues-mcp.md) | Import the route as GitHub Issues (MCP) | free-form |
| 2 | [BEVN-001](tasks/BEVN-001-codebase-mapping.md) | Codebase mapping | free-form |
| 3 | [BEVN-002](tasks/BEVN-002-api-documentation.md) | API documentation | free-form |
| 4 | [BEVN-003](tasks/BEVN-003-tech-debt-audit.md) | Technical debt audit | free-form |
| 5 | [EXT-110](tasks/EXT-110-revive-ci.md) | Revive CI on GitHub Actions | free-form |
| 6 | [BEVN-104](tasks/BEVN-104-standardize-api-responses.md) | Standardize API responses and errors | free-form |
| 7 | [BEVN-107](tasks/BEVN-107-input-validation.md) | Add input validation | free-form |
| 8 | [BEVN-109](tasks/BEVN-109-transaction-boundaries.md) | Fix transaction boundaries | free-form |
| — | [BEVN-101](tasks/BEVN-101-sessions-page-slow.md) | *Optional:* Sessions page is slow (N+1) | free-form |
| 9 | [BEVN-115](tasks/BEVN-115-registration-modal-state.md) | Registration modal stale state | free-form |
| 10 | [BEVN-202](tasks/BEVN-202-session-waitlist.md) | Session Waitlist | **spec-driven (superpowers)** |
| 11 | [BEVN-203](tasks/BEVN-203-registration-dashboard.md) | Attendee Registration Dashboard | **spec-driven (superpowers)** |
| 12 | [BEVN-205](tasks/BEVN-205-e2e-suite.md) | End-to-end test suite (Playwright) | **spec-driven (superpowers)** |

**Track B — TypeScript.** Same discovery and CI work, then migrate the backend to TypeScript instead of stabilizing the .NET one — fixing its known defects in the process — and build the same features on the migrated backend.

| # | Task | Theme | Process |
|---|------|-------|---------|
| 1 | [EXT-100](tasks/EXT-100-import-issues-mcp.md) | Import the route as GitHub Issues (MCP) | free-form |
| 2 | [BEVN-001](tasks/BEVN-001-codebase-mapping.md) | Codebase mapping | free-form |
| 3 | [BEVN-002](tasks/BEVN-002-api-documentation.md) | API documentation | free-form |
| 4 | [BEVN-003](tasks/BEVN-003-tech-debt-audit.md) | Technical debt audit | free-form |
| 5 | [EXT-110](tasks/EXT-110-revive-ci.md) | Revive CI on GitHub Actions | free-form |
| — | [BEVN-101](tasks/BEVN-101-sessions-page-slow.md) | *Optional:* Sessions page is slow (N+1) — do it **before** the migration | free-form |
| 6 | [EXT-150](tasks/EXT-150-migrate-backend-ts.md) | Migrate backend to TypeScript (NestJS) | **spec-driven (superpowers)** |
| 7 | [BEVN-115](tasks/BEVN-115-registration-modal-state.md) | Registration modal stale state | free-form |
| 8 | [BEVN-202](tasks/BEVN-202-session-waitlist.md) | Session Waitlist | **spec-driven (superpowers)** |
| 9 | [BEVN-203](tasks/BEVN-203-registration-dashboard.md) | Attendee Registration Dashboard | **spec-driven (superpowers)** |
| 10 | [BEVN-205](tasks/BEVN-205-e2e-suite.md) | End-to-end test suite (Playwright) | **spec-driven (superpowers)** |

Both routes are one vertical slice: set up your tracker (EXT-100), understand the codebase (Phase 0), revive CI (EXT-110), get the registration flow into shape (fix it in place, or migrate it cleanly), build two features on top of it, and finish by covering the flows with e2e tests (BEVN-205). The optional BEVN-101 (query performance) is not required but strongly recommended.

**Numbering.** `BEVN-xxx` tasks are taken **verbatim** from the original BrownEvents task library — don't be surprised by gaps in the numbers. `EXT-xxx` tasks were added for this pilot. Where a pilot-specific requirement extends an original task, it appears as a marked **"Pilot addition"** block — the original text above it is untouched.

Each task's text lives in its own file under [`tasks/`](tasks/) in this repository. In your first task (EXT-100) you import the whole route as GitHub Issues into your working repository — from then on, when starting a session, hand the agent the current task's issue rather than this whole document: extra context hurts the agent just as it hurts you.

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

Every task in the route tables above has its mode marked:

- **Free-form** (EXT-100, discovery, EXT-110, the stabilization fixes, BEVN-101, the frontend fix) — work with your agent however you like.
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

The devlog is not paperwork for its own sake. The pilot ends with a **defense**: a call with a trainer where you talk through your work. A good devlog is a ready-made outline for that story; without one, weeks later you won't remember half of it.

## Final Report

Once every task of your track is merged, build the report on your work with the agent. From the repository folder:

```bash
npx -y -p @codemieai/code codemie analytics --report \
  --last 30d --include-external \
  --project brown-events-pilot \
  --report-format both --report-output ./report/report.html
```

`--project brown-events-pilot` filters by folder name: if you cloned the repository into a differently named folder, substitute yours. The `--last 30d` window covers 14–20 days of work with a margin; if you worked longer — give exact dates (`--from ... --to ...`).

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
