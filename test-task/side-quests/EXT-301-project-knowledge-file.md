# EXT-301: Project knowledge for the agent

> Available after BEVN-003 | Both tracks | Optional side quest
>
> Track B: update after EXT-150
>
> Rules: [test task](../README.md) | Quest map: [README.md](README.md)

## Why

Agents work better when they have accurate project context before they start. This repository does not yet have a project rules file that gives an agent that context automatically.

## What it trains

Turning project knowledge into instructions an agent can use.

## Task

Use your codebase map from BEVN-001 and technical debt audit from BEVN-003 to create `CLAUDE.md` or `AGENTS.md` in the repository root.

Include:

- how to run and test the project
- project conventions
- an architecture summary in five lines
- known traps and constraints

Then test whether the file helps. Give the agent the same small task once without the project knowledge file and once with it, and compare the results.

## Definition of done

- [ ] Add `CLAUDE.md` or `AGENTS.md` to the repository root
- [ ] Write it for the agent using direct instructions and no filler
- [ ] Record a before and after comparison in the devlog using one concrete task
- [ ] On Track B, update the file after EXT-150
