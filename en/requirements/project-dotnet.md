# Insurance Platform (.NET / Vue, US): Candidate Requirements

The team maintains and evolves the core insurance product and several additional services. Separate POC projects come up periodically — quick prototypes to validate new ideas.

**Core stack:**

* .NET Core;
* MS SQL;
* Vue, with some Angular and React;
* Azure;
* Playwright + TypeScript for test automation.

The core product is a monolith that is gradually being split into microservices.

**Processes and tools:** Azure DevOps / Jira, Scrum, PRs, CI/CD, test plans, acceptance criteria.

**Important:** overlap with US Eastern is required — the workday starts later than usual and lasts until roughly 19:00 CET.

---

## 2. What the Work Looks Like

On this project, the key skill is not so much writing code from scratch as quickly understanding an existing system and changing it safely.

Typical tasks:

* navigating an unfamiliar codebase;
* extending the existing frontend and backend;
* reading and validating C#/.NET code;
* working with MS SQL and troubleshooting performance issues;
* reading API contracts and Swagger;
* using coding agents to implement tasks;
* reading and reviewing agent-generated specs and implementation plans;
* verifying generated code via diffs, tests, and running the application;
* writing and maintaining unit / integration / e2e tests;
* troubleshooting CI/CD and environment issues;
* occasionally building small POCs.

---

# 3. What Is Required from the Candidate

## 3.1. Engineering Fundamentals

A solid foundation in the areas below is expected.

### 1. Runtime and Asynchronous Programming

For C#/.NET:

* `async/await`;
* how `await` differs from `.Result` / `.Wait()`;
* why synchronously waiting on async code blocks a thread;
* where deadlocks and thread-pool starvation come from.

For JS/TS (nice to have):

* event loop;
* promises;
* `async/await`;
* why CPU-bound code or synchronous I/O blocks the event loop;
* basic understanding of the Node.js runtime.

### 2. HTTP and APIs

You need to understand:

* HTTP methods;
* status codes 401 / 403 / 404 / 422 / 500;
* REST conventions;
* Swagger / OpenAPI;
* CORS;
* the structure of an API contract.

### 3. SQL

The project uses **MS SQL**, so SQL is especially important.

You need solid command of:

* `SELECT`;
* `JOIN`;
* aggregation;
* indexes;
* transactions;
* locks;
* N+1;
* the basic causes of slow queries.

**How we check:** write a JOIN and an aggregation without hints, then walk through a "why is this query slow and what can be done" case.

---

### 4. Git

Working proficiency with Git is expected:

* merge conflicts;
* merge vs rebase;
* reading diffs;
* understanding change history.

### 5. Testing

You need to understand:

* unit / integration / e2e;
* the test pyramid;
* TDD;
* regression testing;
* acceptance criteria.

For a bugfix, the expected pattern is:

**reproduce → failing test → fix → passing test.**

**How we check:** describe how testing was organized on your own training project, rather than reciting a definition from an article.

---

### 6. CI/CD

You need to be able to read someone else's pipeline and understand:

* which checks run;
* what actually blocks a merge;
* which tests are executed;
* where the deploy happens;
* why a green pipeline does not guarantee good code.

### 7. Environment and Debugging

You need to understand:

* environment variables;
* ports;
* logs;
* configuration;
* Docker / docker-compose at a basic level.


### 8. Reading Unfamiliar Code

This is one of the project's key competencies.

The candidate must be able to quickly identify:

* entry points;
* main modules;
* data flow;
* APIs;
* the persistence layer;
* dependencies.

## 3.2. One Frontend Framework in Depth

The project mostly uses **Vue**, with some Angular and React.

Deep prior knowledge of Vue specifically is not required. What matters far more is a solid understanding of one modern frontend framework and the ability to transfer concepts between them.

Expected understanding of:

* components;
* state;
* routing;
* forms;
* API interaction;
* lifecycle;
* architecture;
* testing.

**How we check:** explain the architecture of your own training project at the level of actual code.

---

## 3.3. Reading C#/.NET Code

Deep production experience with C# is **not required** at the start.

But the candidate must be able to independently read generated or legacy C# code and understand:

* typing;
* classes / interfaces;
* dependency injection;
* layers;
* async code;
* ORM;
* data access;
* API controllers / endpoints.

A significant part of the implementation can be done with a coding agent, but the result cannot be accepted as a black box.

You need to be able to:

1. understand what the agent changed;
2. spot a questionable architectural decision;
3. verify the code by running it;
4. check the tests;
5. fix the code or redirect the agent when needed.

---

# 4. Working with Coding Agents

The project expects real experience with **Claude Code, Codex, or a comparable agentic coding tool**.

Simply "using ChatGPT" is not enough.

What matters is full-cycle experience:

**task → context → research → plan → implementation → tests → diff review → validation.**

## What the Candidate Must Understand

### Context Management

An agent works with a limited context.

You need to be able to:

* provide only the necessary context;
* recognize when a session has become too noisy;
* start a new session with a short handoff;
* avoid loading unnecessary files and history into the context.

---

### Repository Instructions

You need to be able to find and read project instructions, such as:

* `AGENTS.md`;
* `CLAUDE.md`;
* repository-specific skills;
* coding conventions.

Agent instructions are part of the project, not magic inside the model.

---

### Specs and Plans

A spec-driven process is used regularly.

Before implementation, you must read the agent-generated:

* specification;
* implementation plan.

It is especially important to notice **implicit decisions** — places where the agent chose an architecture or behavior on its own, even though the requirements did not explicitly define it.

---

### Validation

The agent's "done" reply cannot be accepted as proof.

After implementation, you need to verify:

* the diff;
* the tests;
* the running application;
* the acceptance criteria;
* possible regression issues.

---

### Tool Choice

Not every task needs the full agentic cycle.

The candidate must be able to choose a tool proportional to the task: sometimes a small change is faster and more reliable to make by hand.

---

## How We Check Agent Skills

A good exercise:

1. In one session, the agent completes a small task.
2. In a second session, the candidate analyzes the result:

   * what exactly changed;
   * which decisions the agent made on its own;
   * where it could have gone wrong;
   * which tests are needed;
   * what the candidate verified themselves.

A big plus is if the candidate can also estimate the cost and the amount of context used.

---

# 5. Testing and TDD

TDD and the test pyramid are asked about directly in the interview.

The candidate must understand not just the definitions but the practical application.

For example, when fixing a bug:

1. reproduce the problem;
2. write a failing test;
3. fix the code;
4. make sure the test passes;
5. check the remaining tests.

The project uses **Playwright + TypeScript** for e2e.

---

# 6. Cloud

Deep Azure experience is not required, but you need to understand cloud concepts.

At a minimum:

* why companies use the cloud;
* IaaS vs PaaS;
* managed services;
* compute;
* storage;
* databases;
* scaling;
* the basic idea of Azure.

Separately, you should understand the difference:

**MS SQL** — a relational database.

**Cosmos DB** — a distributed NoSQL/document database.

You need to be able to explain why SQL fits one situation and Cosmos DB another.

---

# 7. Team Workflow

Regular team development experience is needed:

* Jira or Azure DevOps;
* tickets;
* branches;
* pull requests;
* code review;
* standups;
* sprints.

**How we check:** describe the usual path of a task:

**ticket → analysis → branch → implementation → tests → PR → review → merge.**

---

# 8. English

The target level is **B1+/B2**.

English is needed for:

* documentation;
* tickets;
* specs;
* standups;
* communicating with the US team.

**How we check:** a 5–10 minute conversation about your experience and one of your projects.

---

# 9. Practical Experience

A big plus is a pet project or internal project where the candidate made engineering decisions independently.

Projects that involved a coding agent are especially interesting.

You need to be able to explain:

1. what problem the project solved;
2. what architecture you chose;
3. what you did yourself;
4. what the agent did;
5. how you verified the agent's work;
6. which agent mistakes you managed to catch;
7. what you would do differently now.

---

# 10. Questions Already Asked in Interviews

The project's interviews have already included:

* What is TDD and how is the test pyramid structured?
* What is MCP and what problems does it solve?
* How does the ChatGPT interface differ from Claude Code / Codex?
* How does an agentic coding CLI work "under the hood"?
* How does an LLM differ from an agent?
* What is the cloud and what problems does Azure solve?
* How does Cosmos DB differ from MS SQL?
* When is a relational database the better choice, and when a document database?
* Tell us about your pet project.
* What did you do on the project, and what did the coding agent do?
* How did you verify the agent's work?

---

# 11. What to Brush Up Before the Interview

## P0 — Must Have

### 1. How a Coding Agent Works

Be able to explain without looking anything up:

* LLM vs agent;
* tools;
* agent loop;
* context window;
* repository context;
* why a ChatGPT UI and a coding agent are different working tools.

---

### 2. Reading C#

Take a small open-source C# project.

In 30–40 minutes, try to identify:

* the entry point;
* the architecture;
* DI;
* the API;
* the database layer;
* the main entities;
* a few potentially problematic spots.

The goal is not to learn all of C#, but to learn to find your way around someone else's .NET code.

---

### 3. Presenting Your Own Project

Prepare a 3–5 minute story:

**task → architecture → what the agent did → what you verified yourself → where the agent went wrong → result.**

---

## P1 — Nice to Have

### 4. Hands-On MCP

MCP (Model Context Protocol) is a standard for connecting AI applications and agents to external data and tools.

At least once, you should:

1. connect an MCP server;
2. give the agent access to its tools/resources;
3. complete a real small task with it.

Then you can answer interview questions from your own experience.

---

### 5. Azure Basics

A basic understanding is enough:

* cloud;
* IaaS / PaaS;
* App Service / managed compute;
* storage;
* managed databases;
* MS SQL vs Cosmos DB.

---

## P2 — Bonus

### 6. Git Worktree + Parallel Agents

A useful working pattern:

* one task → one worktree;
* a second task → a second worktree;
* a separate agent session for each task.

This lets you carry several changes in parallel without mixing branches, working trees, and agent context.

---

# Short Readiness Criterion

The candidate is most likely ready for the interview if they:

* confidently cover the engineering areas from section 3.1;
* know SQL well;
* know at least one frontend framework in depth;
* can read unfamiliar C#/.NET code;
* have actually worked with a coding agent;
* understand TDD and the test pyramid;
* can explain basic cloud concepts;
* can discuss their experience in English for 5–10 minutes;
* can walk through at least one of their own projects in detail and explain where the agent's involvement ended and their own engineering responsibility began.
