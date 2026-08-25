# BrownEvents — Brownfield Task Route

> *"All our events are brown as s... stale coffee"*
>
> Read this document before starting any task. The code lives in a separate private
> template repository (access — see [README.md](README.md)); set it up with
> `docker-compose up` and explore it before picking up a task.
>
> Each task lives in its own file under [`tasks/`](tasks/). In your working repository the
> route becomes GitHub Issues (that's the first task, EXT-100) — in a session, hand the agent
> the current task's issue, not the whole library.
> The rules of the pilot (branches, PRs, process, report) are in [README.md](README.md).
>
> **Two task numberings.** `BEVN-xxx` tasks are taken **verbatim** from the original
> BrownEvents task library — don't be surprised by gaps in the numbers. `EXT-xxx` tasks
> were added for this pilot. Where a pilot-specific requirement extends an original task,
> it appears as a marked **"Pilot addition"** block — the original text above it is untouched.

---

## What You're Working With

BrownEvents is a conference management application built two years ago by a team that has since moved on. The app works — conferences can be created, sessions are listed, attendees can register. The codebase, however, has not been maintained. Your job is to explore it, understand it, and improve it.

The stack is **ASP.NET Core 6 + EF Core 6 + React + Vite + PostgreSQL**. Run `docker-compose up` to get a working environment before starting any task.

> **Important:** Phase 0 tasks are prerequisites. Complete them before Phase 1 so you have a map of the codebase and a list of its problems.

---

## Domain Entities

| Entity | Key Fields |
|--------|-----------|
| **Conference** | Id, Title, Description, Location, StartDate, EndDate, Status |
| **Session** | Id, Title, Description, StartTime, EndTime, Capacity, ConferenceId, SpeakerId, RoomId |
| **Speaker** | Id, FirstName, LastName, Bio, Email |
| **Room** | Id, Name, Capacity, Location |
| **Attendee** | Id, FirstName, LastName, Email |
| **Registration** | Id, ConferenceId, AttendeeId, RegisteredAt, Status |

---

## The Route

You work **individually**, tasks strictly in order. There are **two tracks** — pick one based on the backend stack you know well (you must be able to judge the agent's output, not just apply it):

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

Both routes are one vertical slice: set up your tracker (EXT-100), understand the codebase (Phase 0), revive CI (EXT-110), get the registration flow into shape (Phase 1: fix it in place, or migrate it cleanly), build two features on top of it (Phase 2), and finish by covering the flows with e2e tests (BEVN-205). Skipping ahead makes later tasks harder — the Phase 2 features rely on clean error handling, validation and atomic writes, whichever way you got them, and the e2e suite tests what you built.

"Free-form" means: work with your agent however you like. "Spec-driven" means: spec and plan are written and reviewed **before** the code — see [README.md](README.md).

---

## Side Quests

For the motivated: six optional quests about what the delivery process is *made of* — project knowledge for agents, guardrails, an adversarial critic, reusable skills, autonomous runs, and the cost of your work. They don't affect the main route's assessment. Start at the quest map: [side-quests/README.md](side-quests/README.md).
