# BEVN-202 — Session Waitlist

> Phase 2 — New Features · both tracks · SPEC-DRIVEN
> Rules & route: [README.md](../README.md)

When a session has reached its capacity, an attendee can join a waitlist. If a registered attendee cancels, the first person on the waitlist is automatically promoted to a confirmed registration. This promotion should be logged. The session detail page shows current registration count, capacity, and waitlist count.

**Definition of Done:**
- [ ] `POST /api/sessions/{id}/waitlist` adds an attendee to the waitlist
- [ ] Registering for a session at capacity returns 409 — does not auto-waitlist
- [ ] Cancelling a confirmed registration triggers automatic promotion of the next waitlisted attendee
- [ ] Promotion is logged at INFO level with attendee ID and session ID
- [ ] `GET /api/sessions/{id}` response includes `registeredCount`, `capacity`, `waitlistCount`
- [ ] Session detail page shows capacity and waitlist count
- [ ] Unit tests cover: join waitlist, cancel triggers promotion, waitlist ordering

---

> **Pilot addition — the operator on every step.** The DoD above defines *what* to build. This addition defines *how you watch yourself work* and adds deliverables to the same PR.

On a spec-driven task it is easy to experience the pipeline as ceremony — you write a spec because the rules demand one, you commit a plan because the reviewer will look for it. But the pipeline exists for a different reason: the agent writes the code, and **you are present at every step as the operator** — the person who catches what the agent got wrong *before* it becomes expensive. You validate with what you know, and you cannot check a layer you don't understand. On this task you make that work visible.

The task flows through the conveyor:

```
ticket → spec → plan → critic → implementation → checks → evidence → PR
```

The operator is present on every step, and every step has its own job:

| Conveyor step | What the operator does |
|---|---|
| **ticket** | understands the requirement, finds the parts of the system it touches, asks questions where it is unclear |
| **spec** | writes acceptance criteria; resolves the contentious cases in writing, before any code |
| **plan** | reads the agent's plan end to end and checks it against the spec |
| **critic** | runs an adversarial pass on the plan — a fresh session that gets only the spec and the plan and looks for gaps and silent decisions; gives every finding an explicit verdict |
| **implementation** | watches context and cost, stops early, intervenes by hand when needed |
| **checks** | knows what the tests actually run and what really blocks the merge |
| **evidence** | discipline: ticket number in the branch, proofs in the repository |
| **PR** | reads the diff, validates the result independently of the agent's words |

**Tooling:** unchanged — the usual spec-driven setup (in Claude Code, the superpowers plugin, whose brainstorming → spec → plan → implementation flow drives part of this conveyor; in another agent, the equivalent flow with `spec.md` and `plan.md` committed). Notice, though, that the tooling orchestrates only part of the map: nobody runs the critic, keeps the evidence, or validates the PR for you. Seeing where the automation ends and the operator begins is part of the exercise.

**The operator journal:** keep `docs/operator-journal.md` in the task branch. One entry per conveyor step, written *at* that step, not reconstructed afterwards. Each entry answers three questions:

1. What did I do here that the agent could not or should not do for me?
2. What did I catch, question, or decide? (Or honestly: nothing — and what did I check to conclude that?)
3. What has the task cost so far?

(If you later take [EXT-306](../side-quests/EXT-306-cost-of-your-work.md), this journal's cost line is ready input.)

**Additional Definition of Done:**
- [ ] The journal has an entry for every step of the conveyor, and the commit history shows the entries were written along the way, not backfilled at the end
- [ ] The *ticket* entry records at least one question you asked about the requirements (or names the ambiguity you looked for and didn't find)
- [ ] The *plan* or *critic* entry records at least one silent decision the agent made that the ticket didn't ask for (there is always at least one) — with your explicit verdict on it
- [ ] The *PR* entry records how you validated the result yourself, without relying on the agent's summary
- [ ] A closing debrief: which step turned out to be the most work for you as operator — and is that where you expected it?
