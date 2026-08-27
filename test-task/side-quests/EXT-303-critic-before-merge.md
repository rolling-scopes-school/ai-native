# EXT-303: A critic before merge

> Available on BEVN-202 or BEVN-203 | Both tracks | Optional side quest
>
> Rules: [test task](../README.md) | Quest map: [README.md](README.md)

## Why

A fresh review can find differences between the specification and implementation that the author missed.

## What it trains

Reviewing a diff against a specification and resolving findings before merge.

## Task

Before merging BEVN-202 or BEVN-203, start a fresh agent session. Give the agent only the specification and the diff.

Ask it to find:

- differences from the specification
- missed edge cases
- defects

Tell it not to praise the implementation and to return only findings.

Review every finding. Either fix it or reject it with a reason.

## Definition of done

- [ ] Save the critic report as `docs/critic-<task>.md` in the Pull Request
- [ ] Resolve at least two findings with a verdict and reason
- [ ] The commit history shows that the critic review happened before merge
