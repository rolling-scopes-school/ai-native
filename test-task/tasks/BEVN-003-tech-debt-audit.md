# BEVN-003: Technical debt audit

> Phase 0: Discovery | Both tracks | Free-form
>
> Rules and route: [README.md](../README.md)

Review both the backend and frontend and write a structured technical debt audit. Each issue should identify where the problem is, why it matters, and what should change. Group related issues and assign a severity.

This audit feeds into the stabilization work that follows.

## Definition of done

- [ ] Cover both backend and frontend
- [ ] For each issue, record the file and line where relevant, description, severity, and suggested fix
- [ ] Use `High`, `Medium`, or `Low` severity
- [ ] Group issues by category, such as performance, correctness, security, maintainability, or configuration
- [ ] Document at least 10 distinct issues. The codebase contains more than 10 intentional issues
- [ ] Save the audit as `docs/tech-debt-audit.md` in the project root

> **Pilot addition**
>
> Explicitly review these areas:
>
> - blocking calls on async code
> - query efficiency, including how the ORM loads related data
> - CORS configuration
>
> If you find no problem in one of these areas, record that conclusion and explain why.
