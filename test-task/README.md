# Test task: BrownEvents

> Читать по-русски: [README.ru.md](README.ru.md)

BrownEvents is a conference management application that has not been maintained for two years. It already supports conference creation, session listing, and attendee registration.

Your task is to understand the existing system, stabilize it, and implement two features with the help of a console AI agent. The review covers both the finished work and your development process, so the task includes traceability rules, a development log, and a final analytics report.

## Expected duration

Plan for roughly 14 to 20 days from the day you receive repository access.

This is a guideline, not a hard deadline. If you need more time, tell the reviewer.

## Project

The stack is:

- ASP.NET Core 6
- EF Core 6
- React
- Vite
- PostgreSQL

Start the application with:

```bash
docker-compose up
```

Make sure the environment works before starting the tasks.

### Domain model

| Entity       | Key fields                                                                            |
| ------------ | ------------------------------------------------------------------------------------- |
| Conference   | Id, Title, Description, Location, StartDate, EndDate, Status                          |
| Session      | Id, Title, Description, StartTime, EndTime, Capacity, ConferenceId, SpeakerId, RoomId |
| Speaker      | Id, FirstName, LastName, Bio, Email                                                   |
| Room         | Id, Name, Capacity, Location                                                          |
| Attendee     | Id, FirstName, LastName, Email                                                        |
| Registration | Id, ConferenceId, AttendeeId, RegisteredAt, Status                                    |

## Task route

Work individually and complete tasks in order.

Choose the track for the backend stack you can review and verify yourself. Do not choose a track only because the agent can implement it.

Record your choice in the EXT-100 Pull Request and explain why you chose it.

### Common tasks

Both tracks begin with the same five tasks.

|   # | Task                                            | Purpose                                     | Mode      |
| --: | ----------------------------------------------- | ------------------------------------------- | --------- |
|   1 | [EXT-100](tasks/EXT-100-import-issues-mcp.md)   | Import the route as GitHub Issues using MCP | Free-form |
|   2 | [BEVN-001](tasks/BEVN-001-codebase-mapping.md)  | Codebase mapping                            | Free-form |
|   3 | [BEVN-002](tasks/BEVN-002-api-documentation.md) | API documentation                           | Free-form |
|   4 | [BEVN-003](tasks/BEVN-003-tech-debt-audit.md)   | Technical debt audit                        | Free-form |
|   5 | [EXT-110](tasks/EXT-110-revive-ci.md)           | Restore CI with GitHub Actions              | Free-form |

### Track A: .NET

Keep the existing .NET backend, fix its known problems, then build the new features on top of it.

|   # | Task                                                    | Purpose                                   | Mode        |
| --: | ------------------------------------------------------- | ----------------------------------------- | ----------- |
|   6 | [BEVN-104](tasks/BEVN-104-standardize-api-responses.md) | Standardize API responses and errors      | Free-form   |
|   7 | [BEVN-107](tasks/BEVN-107-input-validation.md)          | Add input validation                      | Free-form   |
|   8 | [BEVN-109](tasks/BEVN-109-transaction-boundaries.md)    | Fix transaction boundaries                | Free-form   |
|  \* | [BEVN-101](tasks/BEVN-101-sessions-page-slow.md)        | Fix the sessions page N+1 query           | Free-form   |
|   9 | [BEVN-115](tasks/BEVN-115-registration-modal-state.md)  | Fix stale state in the registration modal | Free-form   |
|  10 | [BEVN-202](tasks/BEVN-202-session-waitlist.md)          | Session waitlist                          | Spec-driven |
|  11 | [BEVN-203](tasks/BEVN-203-registration-dashboard.md)    | Attendee registration dashboard           | Spec-driven |
|  12 | [BEVN-205](tasks/BEVN-205-e2e-suite.md)                 | End-to-end test suite                     | Spec-driven |

### Track B: TypeScript

Replace the .NET backend with NestJS. Fix the known backend problems during the migration, then build the same features on the migrated backend.

|   # | Task                                                   | Purpose                                          | Mode        |
| --: | ------------------------------------------------------ | ------------------------------------------------ | ----------- |
|  \* | [BEVN-101](tasks/BEVN-101-sessions-page-slow.md)       | Fix the sessions page N+1 query before migration | Free-form   |
|   6 | [EXT-150](tasks/EXT-150-migrate-backend-ts.md)         | Migrate the backend to NestJS                    | Spec-driven |
|   7 | [BEVN-115](tasks/BEVN-115-registration-modal-state.md) | Fix stale state in the registration modal        | Free-form   |
|   8 | [BEVN-202](tasks/BEVN-202-session-waitlist.md)         | Session waitlist                                 | Spec-driven |
|   9 | [BEVN-203](tasks/BEVN-203-registration-dashboard.md)   | Attendee registration dashboard                  | Spec-driven |
|  10 | [BEVN-205](tasks/BEVN-205-e2e-suite.md)                | End-to-end test suite                            | Spec-driven |

\* BEVN-101 is optional but recommended.

### Task numbering

`BEVN-xxx` tasks come from the original BrownEvents task library, so gaps in their numbers are expected.

`EXT-xxx` tasks were added for this pilot.

When the pilot adds requirements to an original task, they appear in a marked **Pilot addition** section.

Each task has its own file under [`tasks/`](tasks/).

EXT-100 imports the tasks for your selected route into your working repository as GitHub Issues. After that, use the current issue as the agent's task context instead of passing this README into every session.

### Side quests

The repository also contains six optional [side quests](side-quests/README.md). They cover agent project knowledge, hooks, pre-merge criticism, custom skills, autonomous execution, and development cost.

Side quests do not affect assessment of the main route.

## Repository setup

The application code is in the [brown-events-pilot](https://github.com/dzmitry-varabei/brown-events-pilot) template repository.

1. Select **Use this template** and create your own repository.
2. A private repository is recommended because it will contain your devlog and final report.
3. If the repository is private, add the reviewer as a collaborator.
4. Do all task work in your copy, including issues, branches, commits, Pull Requests, the devlog, and the final report.

For pilot questions, use the [Telegram chat](https://t.me/+u5HQoDbqaO4yMTI6).

## Required tools

### Console AI agent

Use one of these console agents:

- Claude Code
- Codex CLI
- Gemini CLI
- Copilot CLI
- Pi

Cursor, web chats, and IDE plugins do not satisfy this requirement because their sessions are not included in the final analytics report. See [codemie-analytics.md](codemie-analytics.md) for details.

### Node.js

Node.js 20 or newer is required to generate the final report.

### Docker

Use Docker to run the application.

The code repository README contains the full startup instructions. The complete application can be started with:

```bash
docker-compose up --build
```

## Traceability rules

Every task must be traceable through:

```text
GitHub Issue
→ branch
→ agent session
→ commits
→ Pull Request
```

Follow these rules for every task.

1. Create one branch per task. Use the task ID and a short slug.

   ```bash
   git checkout -b BEVN-001-codebase-map
   ```

   Run the agent for that task only from this branch.

2. Start the first message of every agent session with the task ID.

   ```text
   BEVN-104: bring the API responses to a single format...
   ```

   The analytics report uses this first message to identify the session.

3. Include the task ID in related commit messages.

   ```text
   docs: add architecture map (BEVN-001)
   ```

4. Create one Pull Request per task from the task branch into `main`.

   The PR must:
   - include the task ID in its title;
   - link the corresponding GitHub Issue with `Closes #N`;
   - satisfy the task's Definition of Done;
   - include the required devlog update.

   Review the result, then merge the PR yourself before moving to the next task.

You may use as many agent sessions, attempts, and clarifications as needed. Session count is not graded. The reviewer is interested in how you define tasks, verify decisions, correct problems, and reach a working result.

## Development process

Tasks use one of two modes.

### Free-form

There is no prescribed agent workflow. Work with the agent in whatever way helps you complete and verify the task.

### Spec-driven

Before implementation begins, create:

1. a specification that defines what will be built and resolves unclear or disputed cases;
2. an implementation plan with the steps needed to build and verify it.

Commit both documents to the task branch together with the implementation.

If you use Claude Code, install the [superpowers](https://github.com/obra/superpowers) plugin and use its brainstorming, specification, planning, and implementation workflow. It stores the documents under `docs/superpowers/`.

If you use another console agent, follow an equivalent process. The Pull Request must contain `spec.md` and `plan.md`.

The following tasks are spec-driven:

- EXT-150 on Track B;
- BEVN-202;
- BEVN-203;
- BEVN-205.

### CI gate

EXT-110 restores CI.

Starting with the next task, merge a Pull Request only when CI is green. If the pipeline fails because of your changes, fixing it is part of the current task.

## Development log

Maintain `docs/devlog.md`.

Add a short entry after every task. The entry should record your judgment about the work rather than summarize the diff.

Cover what matters:

- what you changed and what result you got;
- decisions the agent made independently, including whether you accepted or changed them;
- places where you had to intervene manually;
- what you would do differently next time.

You or the agent may write the entry, but it must reflect your assessment of the work.

The Pull Request template includes a `devlog updated` checkbox. A task is not complete until its devlog entry exists.

You will use the devlog during the final defense, so write it while the decisions are still fresh.

## Final report

After all required tasks for your track are merged, generate the analytics report from the repository directory:

```bash
npx -y -p @codemieai/code codemie analytics --report \
  --last 30d --include-external \
  --project brown-events-pilot \
  --report-format both --report-output ./report/report.html
```

The `--project brown-events-pilot` argument filters sessions by the repository folder name. If your local folder has a different name, use that name instead.

The `--last 30d` window is enough for the expected 14 to 20 day schedule. If your work spans more than 30 days, use exact dates with `--from` and `--to`.

Before submitting:

1. Open `report/report.html` in a browser.
2. Check that it contains only sessions related to this project.
3. Review [codemie-analytics.md](codemie-analytics.md) if you need to confirm what the report contains. It includes session metrics, branches, and the first message of each session. It does not include full conversations or file contents.
4. Commit both generated files:
   - `report/report.html`
   - `report/report.json`

5. Create and merge the final Pull Request.
6. Tell the reviewer that the task is complete.

## Assessment

The reviewer will assess:

- whether each task meets its Definition of Done;
- the quality of the code and documentation;
- the specification and plan for spec-driven tasks;
- whether implementation follows those documents;
- traceability from task to agent sessions, commits, and Pull Request;
- green CI for merges after EXT-110;
- how you use the agent, verify its work, and handle its decisions;
- your explanation of the work during the final defense.

The number of agent attempts or sessions is not an assessment criterion.

## Questions

If the application does not start, the build fails for reasons unrelated to your work, or an instruction is unclear, contact the reviewer instead of spending days guessing what the task expects.
