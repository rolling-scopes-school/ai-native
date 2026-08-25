# EXT-303 — A Critic Before Merge (on BEVN-202 or BEVN-203)

> Optional side quest · both tracks · not part of the main route
> Rules: [test task](../README.md) · Quest map: [side-quests/README.md](README.md)

**Why:** in production pipelines a critic stands between the plan and the merge — an agent whose only job is to find divergences from the spec. It's a second pair of eyes *before* the human; without it, the author's self-check is the only line of defense, and an author is always kind to their own code.

**What it trains:** adversarial review, reading a diff against a spec, the discipline of "don't praise — hunt".

**Real-world case:** a mature factory keeps critics between every pair of steps (plan → critic → implementation → critic) — they are what takes the load off the human gate.

**The task:** before merging the chosen task, start a *fresh* agent session, give it only the spec and the diff, with a prompt like: "find divergences from the spec, missed edge cases, and defects; do not praise; answer as a list". Then work through every finding: accept it (and fix) or reject it (and say why).

**Definition of Done:**
- [ ] The critic's report is a file in the PR (`docs/critic-<task>.md`)
- [ ] At least two findings are worked through with a verdict and a reason
- [ ] The commit history shows the critic ran before the merge
