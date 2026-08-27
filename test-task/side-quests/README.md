# Side quests

The side quests are optional exercises that extend the main [test task](../README.md). They cover project knowledge, automated guardrails, independent review, reusable skills, autonomous execution, and agent usage cost.

They do not affect assessment of the main route.

Use the same traceability rules as the main task:

```text
branch
→ agent session
→ commits
→ Pull Request
→ devlog
```

Use an `EXT-3xx-slug` branch, start each agent session with the quest ID, create a Pull Request, and add a devlog entry.

Each quest explains why the exercise exists. Read that section before starting. If the exercise is not useful for your workflow, skip it.

## Quest map

Quests are ordered by when they become available.

| Quest                                        | Name                            | Available after           | Focus                                   |
| -------------------------------------------- | ------------------------------- | ------------------------- | --------------------------------------- |
| [EXT-301](EXT-301-project-knowledge-file.md) | Project knowledge for the agent | BEVN-003                  | Project context for agents              |
| [EXT-302](EXT-302-hook-not-reminder.md)      | A hook instead of a reminder    | EXT-110                   | Automated guardrails                    |
| [EXT-303](EXT-303-critic-before-merge.md)    | A critic before merge           | BEVN-202 or BEVN-203      | Review against a specification          |
| [EXT-304](EXT-304-first-skill.md)            | Your first skill                | Any two spec-driven tasks | Reusable agent workflows                |
| [EXT-305](EXT-305-autonomous-contract.md)    | An autonomous run on a contract | BEVN-203                  | Task contracts and unattended execution |
| [EXT-306](EXT-306-cost-of-your-work.md)      | What your work cost             | Final report              | Token and cost analysis                 |
