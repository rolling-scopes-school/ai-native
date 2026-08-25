# EXT-305 — An Autonomous Run on a Contract (after BEVN-203)

> Optional side quest · both tracks · not part of the main route
> Rules: [test task](../README.md) · Quest map: [side-quests/README.md](README.md)

**Why:** the longer an agent works unsupervised, the less ambiguity you can afford. While you sit next to it, you do invisible work for free: you notice the agent drifting off course and correct it on the fly. This quest is about feeling what happens when nobody does that work.

**What it trains:** writing a complete task contract (not just the "what", but the budget, the validation, the failure policy); honest acceptance against criteria written down in advance.

**Real-world case:** overnight autonomous runs formalize a task as an eight-field contract (Objective · Inputs · Tools · Constraints · DoD · Validation · Budget · Failure Policy); the classic anti-example is "Improve our API" versus "analyze error handling in 15 endpoints, no production changes, budget $2, escalate after 2 attempts".

**The task:** take a mini-feature outside the main route: *"the Register Now button must not be shown on completed and cancelled conferences"*. Before launching, write a complete contract with all eight fields. Launch the agent and **do not intervene**: corrections only via a stop and a new contract. Accept or reject the result strictly against the written DoD.

**Definition of Done:**
- [ ] `docs/contract-ext-305.md` is written before the first command to the agent (visible from the commits)
- [ ] The run had no interventions (each intervention, if any, is recorded in the devlog as a contract defect)
- [ ] A verdict against the DoD + a debrief: which contract fields turned out underspecified
