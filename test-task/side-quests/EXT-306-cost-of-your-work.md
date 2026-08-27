# EXT-306: What your work cost

> Available after the final report | Both tracks | Optional side quest
>
> Rules: [test task](../README.md) | Quest map: [README.md](README.md)

## Why

Agent usage has a measurable token and inference cost. Reviewing that cost helps identify expensive parts of the workflow and where the same work might be done with less model usage.

## What it trains

Reading usage data, attributing cost to tasks and stages, and comparing different development workflows.

## Task

Use `report/report.json` and the `/cost` data from your sessions to analyze the cost of your route.

Calculate:

- the cost of each task
- the cost of specification, planning, and implementation for one spec-driven task
- the difference between an average free-form task and a spec-driven task

Then identify where the most expensive work occurred and why.

## Definition of done

- [ ] Create `docs/tokenomics.md` with a table of task, sessions, tokens, and estimated cost
- [ ] Break down one spec-driven task by stage
- [ ] Write three conclusions based on the data
- [ ] Propose one concrete way to reduce cost
