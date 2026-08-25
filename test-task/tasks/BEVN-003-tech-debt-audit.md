# BEVN-003 — Technical Debt Audit

> Phase 0 — Discovery · both tracks · free-form
> Rules & route: [README.md](../README.md)

Read the codebase thoroughly — both backend and frontend — and produce a structured audit document listing every quality issue you find. Each issue should be actionable: a reader should know exactly where to look and what to change. Group issues by category and assign severity. The output of this task feeds directly into the Phase 1 stabilization work.

**Definition of Done:**
- [ ] Both backend and frontend covered in the audit
- [ ] Each issue has: location (file + line where relevant), description, severity (High / Medium / Low), suggested fix
- [ ] Issues grouped by category (e.g. performance, correctness, security, maintainability, configuration)
- [ ] At least 10 distinct issues documented (there are more than 10 intentional ones — find them)
- [ ] Saved as `docs/tech-debt-audit.md` in the project root

> **Pilot addition:** the audit must explicitly cover at least these three areas — blocking
> calls on async code, query efficiency (how the ORM actually loads related data), and CORS
> configuration. If you find nothing wrong in one of them, say so and explain why.
