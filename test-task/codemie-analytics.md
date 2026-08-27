# CodeMie Analytics for students

> Written in tandem by Dzmitry Varabei and Claude Fable. Critiqued by GPT Sol.
> August 24, 2026.

Use CodeMie Analytics to generate a report of your work with console AI agents. Before submitting it, check that the report contains only sessions from the test task.

## What the tool does

[CodeMie CLI](https://github.com/codemie-ai/codemie-code), published as `@codemieai/code`, is an open-source Apache 2.0 tool from the EPAM AI/Run team.

CodeMie CLI supports several workflows, but this task only uses:

```text
codemie analytics
```

The command reads session logs that supported console agents already store locally. This includes Claude Code, Codex CLI, Gemini CLI, Copilot CLI, and Pi.

It generates an HTML report and a JSON file with information such as:

- sessions;
- turns and tool calls;
- changed files;
- token usage;
- branches;
- the first message of each session.

CodeMie does not need to sit between you and your agent. Keep using your console agent normally.

### Privacy

The report files are created locally in the current directory. Running `codemie analytics` does not send the report to the reviewer.

Before submitting a report, open the HTML file and inspect its contents.

The report includes session metadata, project paths, and the first message of each session. It does not include full conversations with the agent or file contents.

## Requirements

You need:

- Node.js 20 or newer;
- Claude Code, Codex CLI, Gemini CLI, Copilot CLI, or Pi.

Cursor, web chats such as ChatGPT or claude.ai, and IDE plugins are not included in the report. Complete the test task with a supported console agent.

You do not need to install CodeMie globally. The commands below use `npx`.

## Inspect analytics for all projects

This step is optional. You can generate a report covering all supported agent sessions from the last seven days:

```bash
npx -y -p @codemieai/code codemie analytics --report \
  --last 7d --include-external \
  --report-format both --report-output ./my-report.html
```

The command creates:

```text
my-report.html
my-report.json
```

Open the HTML file in a browser to inspect the report. The JSON file contains the same report data in a machine-readable format.

`--include-external` includes native agent sessions found on the machine.

`--last 7d` limits the report to the previous seven days. Other supported ranges include:

```text
--last 24h
--from 2026-08-20 --to 2026-08-24
```

Do not submit this report. It may contain sessions from unrelated projects.

## Build the test-task report

1. Work in a dedicated repository folder.

2. Launch your console agent from that folder and complete the tasks normally.

3. After finishing the test task, generate a report for the repository:

   ```bash
   npx -y -p @codemieai/code codemie analytics --report \
     --last 30d --include-external \
     --project brown-events-pilot \
     --report-format both --report-output ./report/report.html
   ```

   `--project brown-events-pilot` filters sessions by project folder name. If your repository folder has a different name, replace `brown-events-pilot` with that name.

   The 30-day window covers the expected 14 to 20 days of work. If your work spans more than 30 days, use exact dates:

   ```text
   --from ... --to ...
   ```

4. Open `report/report.html` and verify that it contains only sessions from the test task.

5. Submit both generated files according to the test-task rules:

   ```text
   report/report.html
   report/report.json
   ```

## Keep sessions traceable to tasks

The reviewer should be able to follow this chain:

```text
ticket
→ branch
→ agent sessions
→ commits
→ Pull Request
```

Use the task ID in each part of that chain.

### Branch

Create a branch that starts with the task ID:

```bash
git checkout -b BEVN-104-standardize-responses
```

Agent sessions started on that branch will record it in the report.

### First message

Start the first message of every agent session with the task ID:

```text
BEVN-104: standardize the API error responses...
```

The report records the first message of each session. Together with the branch, it gives the reviewer a second way to identify the task.

### Commits and Pull Requests

Include the task ID in related commit messages:

```text
feat: add waitlist (BEVN-202)
```

Include it in the Pull Request title as required by the test-task rules.

### Filter by branch

You can also generate a report for one task by filtering on its branch:

```text
codemie analytics --report --branch BEVN-202 ...
```

## What the reviewer sees

| In the report                             | Not in the report                                             |
| ----------------------------------------- | ------------------------------------------------------------- |
| Number of sessions, turns, and tool calls | Full conversations with the agent                             |
| First message of each session             | File contents                                                 |
| Changed files and lines added or removed  | API keys, access tokens, and passwords                        |
| Languages used                            | Sessions from other folders when `--project` filters them out |
| Models, token usage, and estimated cost   |                                                               |

The reviewer uses this information together with your implementation and devlog to understand how you worked with the agent. The number of sessions or attempts is not graded by itself.
