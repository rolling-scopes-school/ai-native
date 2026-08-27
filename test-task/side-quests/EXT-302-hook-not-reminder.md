# EXT-302: A hook instead of a reminder

> Available after EXT-110 | Both tracks | Optional side quest
>
> Rules: [test task](../README.md) | Quest map: [README.md](README.md)

## Why

A reminder in a prompt can be missed. A hook can enforce the same rule automatically.

## What it trains

Turning a repeated instruction into an executable project guardrail.

## Task

Add one hook for a problem you have already encountered in this project.

Examples include:

- block a commit containing `console.log`
- run tests after a service file changes
- warn when a diff exceeds a chosen size

Choose a rule that is useful for this project rather than adding a hook only to complete the quest.

## Definition of done

- [ ] Commit the hook configuration
- [ ] Record one case in the devlog where the hook fired
- [ ] Record which prompt reminder or manual check the hook replaced
