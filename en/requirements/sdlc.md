// Reviewed by Dzmitry Varabei on August 31, 2026. 

## Software Development Life Cycle (SDLC)

Understand the basic software development lifecycle: how a code change moves from a requirement to production.

A junior developer should understand these areas and be able to take part in them:

* **Working with requirements and task tracking** — work with GitHub Issues, Jira, Trello, or similar tools. Read user stories and acceptance criteria. Ask questions when requirements are unclear. Find the parts of the system a task affects. Break a small feature or bug into implementation steps.

* **Git-based development and Pull Request workflow** — create branches, make meaningful commits, push changes, create Pull Requests, resolve merge conflicts, and keep a branch up to date. Understand the typical path from an assigned task to a merged change.

* **Code review** — review your own changes before opening a Pull Request. Understand review comments and respond to them. Make the requested changes. Take part in reviewing simple changes made by other developers. Understand what code review is for: correctness, readability, maintainability, and knowledge sharing.

* **Unit, integration, and E2E testing** — understand the purpose of each test type and the differences between them. Run existing tests, investigate failures, and write or update tests for a small feature or bug. Understand common concepts: mocks, test data, assertions, test isolation. Know that teams also run smoke / synthetic tests — automated checks of the main user flows that run on a live environment after each deployment or on a schedule (also called synthetic monitoring).

* **CI pipelines** — understand what happens after code is pushed or a Pull Request is created. Know the common CI steps: installing dependencies, build, linting, automated tests, security checks, artifact creation. Be able to investigate and fix common pipeline failures.

* **CD and deployment basics** — understand how an application moves from source code to a running environment. Know the difference between development, staging, and production environments. Understand basic Continuous Delivery / Continuous Deployment concepts. Be able to follow an existing deployment process.

* **Debugging CI and deployment failures** — read pipeline and deployment logs and find which step failed. Understand common causes: failed tests, build errors, missing configuration, environment-specific issues. Make or propose a fix.

* **Application logging, monitoring, and production troubleshooting** — understand why applications write logs and metrics. Find the relevant logs, read errors and stack traces, and use the available monitoring tools to investigate simple production issues.

* **Secure development basics** — understand common security practices: input validation, the difference between authentication and authorization, safe handling of secrets and credentials, vulnerable dependencies, and common web vulnerabilities such as XSS and SQL injection. Know that security checks can be part of the development and CI process.

* **Maintenance, bug fixing, and refactoring** — investigate bugs in an existing codebase: reproduce the issue, find the likely cause, implement and test a fix. Perform small refactorings without changing the expected behavior.

A junior developer is **not expected to design CI/CD infrastructure, production architecture, monitoring systems, or deployment platforms from scratch**. They should be able to work with the processes and tools the team has already set up.
