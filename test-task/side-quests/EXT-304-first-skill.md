# EXT-304: Your first skill

> Available after any two spec-driven tasks | Both tracks | Optional side quest
>
> Rules: [test task](../README.md) | Quest map: [README.md](README.md)

## Why

Repeated work is a good candidate for reusable tooling. A skill captures one repeatable action so it can be applied consistently in later tasks.

## What it trains

Extracting a small repeatable workflow and defining how to verify it.

## Task

Find an action in your devlog that you have performed at least twice.

Examples include:

- check a task's Definition of Done against the diff
- update Swagger descriptions for an endpoint
- write a Pull Request walkthrough

Package the action as a skill under `.claude/skills/`.

Its `SKILL.md` should define:

- when to use the skill
- the steps
- the completion criterion

Apply the skill on the next task.

## Definition of done

- [ ] Commit the skill
- [ ] Apply it at least once and record that use in the devlog
- [ ] Make the skill independently verifiable from other workflow steps
- [ ] Record what changed compared with asking the agent without the skill
