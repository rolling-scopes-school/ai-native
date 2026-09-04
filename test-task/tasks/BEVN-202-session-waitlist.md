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

On a spec-driven task it is easy to experience the pipeline as ceremony — a spec because the rules demand one, a plan because the reviewer will look for it. The pipeline exists for a different reason: the agent writes the code, and **you are present at every step as the operator** — the person who catches what the agent got wrong *before* it becomes expensive to change. You validate with what you know; you cannot check a layer you don't understand. Why a delivery process is built from these steps at all is the subject of [doc 03: The AI factory](../../en/03-ai-factory.md) — this task is where you feel it in your hands.

The task flows through a fixed sequence of steps — the [AI SDLC](../../en/requirements/ai-sdlc.md) in its smallest practical form:

| Step | The agent side: session and context | The operator's job |
|---|---|---|
| **ticket** | your working session starts; context: the ticket text (from the tracker via MCP, or pasted by you) + the codebase to explore | understand the requirement, find what it touches, ask questions |
| **spec** | same session: brainstorming → `spec.md` | own the acceptance criteria; settle contentious cases in writing |
| **plan** | same session; context: the spec + the codebase → `plan.md` | read it end to end, check it against the spec |
| **critic** | a **fresh session**: the spec, the plan, the code where the plan's claims need checking — but none of your conversation and its assumptions | commission it; resolve every finding with an explicit verdict — then **gate 1: approve the plan**; nothing is built before your verdict |
| **implementation** | a session that could start fresh: `plan.md` + project rules + the code are meant to be enough — if it only works with your old conversation loaded, the plan is incomplete; the context grows with every step | watch context and cost; stop early; intervene by hand |
| **checks** | no session at all — CI and hooks run with no memory and no opinions | know what the tests actually run and what really blocks the merge |
| **evidence** | none: artifacts in the repository | task ID in the branch name; spec, plan, devlog, checks record — committed |
| **PR** | the agent drafts the description *from its own context* — exactly why you don't rely on it | read the diff yourself — **gate 2: accept or reject** |

It is not a straight line — work gets sent back:

- critic findings reopen the **plan**;
- red checks and PR review comments reopen the **code**;
- implementation can even reopen the **spec**, if it proves the acceptance criteria wrong.

One naming note: the *critic* is a pattern, not a single step — a fresh session with a narrow brief and an explicit verdict on every finding. A mature pipeline runs it at several points, and the depth depends on the risk. Here it runs on the plan; [EXT-303](../side-quests/EXT-303-critic-before-merge.md) runs the same pattern on the completed diff before merge, and on a real factory a review gate like that blocks the path to the PR. And a critic is not a gate: a critic advises, a gate decides — both gates here are yours.

**Tooling:** the usual spec-driven setup (superpowers in Claude Code, or the equivalent flow with `spec.md` and `plan.md` committed). It orchestrates only part of the map: nobody runs the critic, keeps the evidence, or validates the PR for you. Seeing where the automation ends and the operator begins is part of the exercise.

**The operator journal — this task's devlog entry.** No separate file: for BEVN-202 the [devlog](../README.md#development-log-and-defense) entry is kept differently — eight short sub-entries under `## BEVN-202`, one per step (`### ticket`, `### spec`, …), each written *at* that step, not reconstructed afterwards. Each answers three questions:

1. What did I do here that the agent could not or should not do for me?
2. What did I catch, question, or decide? (Or honestly: nothing — and what did I check to conclude that?)
3. The cumulative cost at the end of the step (`/cost` in Claude Code, or your agent's equivalent) — consecutive values give you the cost of every step.

(If you later take [EXT-306](../side-quests/EXT-306-cost-of-your-work.md), these cost lines are ready input.)

**Additional Definition of Done:**
- [ ] The BEVN-202 devlog section has an entry for every step, and the commit history shows the entries were written along the way, not backfilled at the end
- [ ] The *ticket* entry records at least one question you asked about the requirements (or names the ambiguity you looked for and didn't find)
- [ ] The *plan* or *critic* entry records at least one material decision the agent made that the ticket didn't spell out — with your explicit verdict on it — or names the decisions you checked and why none needed a verdict
- [ ] The *PR* entry records how you validated the result yourself, without relying on the agent's summary
- [ ] A closing debrief in the devlog: which step turned out to be the most work for you as operator — and is that where you expected it?

**What stays in whose head.** When this task merges, the agent's head — its context window — is compacted and discarded. Everything it "learned" about waitlists, promotions, and your codebase: gone. Tomorrow's session arrives as a bright, confident stranger who has never heard of BEVN-202. (This is not a bug to fix but a fact to design around — it is why project knowledge files and skills exist; see [EXT-301](../side-quests/EXT-301-project-knowledge-file.md) and [EXT-304](../side-quests/EXT-304-first-skill.md).) The principle: session context is not durable project knowledge — anything that exists only in the conversation is disposable; anything that must survive has to become a repository artifact. What stays in *your* head is different: the domain, the map of the system, the scar from the silent decision you almost let through. Of the two of you, only one accumulates — and the journal is how you check that it's you. The journal itself is not yet the factory's **second output** (doc 03: the reusable artifacts that make the next task cheaper) — it is where you notice what deserves to become one.
