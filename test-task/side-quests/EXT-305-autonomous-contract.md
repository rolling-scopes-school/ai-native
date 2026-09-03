# EXT-305: An autonomous run on a contract

> Available after BEVN-203 | Both tracks | Optional side quest
>
> Rules: [test task](../README.md) | Quest map: [README.md](README.md)

## Why

An agent working without supervision needs a more complete task description because you cannot correct unclear assumptions while it works.

## What it trains

Writing a complete task contract and evaluating the result against criteria defined before implementation.

## Task

Implement this mini-feature outside the main route:

> The Register Now button must not be shown on completed or cancelled conferences.

Before starting the agent, write a contract with these eight fields:

1. Objective
2. Inputs
3. Tools
4. Constraints
5. Definition of Done
6. Validation
7. Budget
8. Failure policy

Run the agent without intervening. If you need to correct it, stop the run and start again with a revised contract.

Accept or reject the result using only the Definition of Done written before the run.

## Definition of done

- [ ] Commit `docs/contract-ext-305.md` before the first agent command
- [ ] Do not intervene during the run
- [ ] If an intervention is necessary, record it in the devlog as a defect in the contract
- [ ] Record an acceptance or rejection verdict against the Definition of Done
- [ ] Record which contract fields were underspecified
