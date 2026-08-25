# EXT-150 — Migrate the Backend to TypeScript (NestJS)

> Phase 1B — Migration · Track B only · SPEC-DRIVEN · replaces Phase 1A
> Rules & route: [README.md](../README.md)

The team is consolidating on a TypeScript stack. Reimplement the backend in **TypeScript with NestJS and Prisma** (PostgreSQL stays), preserving the existing API surface so the React frontend keeps working unchanged. This is a *clean* migration: the defects you documented in BEVN-003 must be **fixed in the new backend, not ported**. NestJS maps almost one-to-one onto the ASP.NET Core structure — controllers, services, DI — so use the existing code as the source of truth for behavior, not as a style guide.

**Definition of Done:**
- [ ] Backend reimplemented in TypeScript: NestJS + Prisma, PostgreSQL unchanged
- [ ] Same API surface: every existing endpoint keeps its path, method and response data — the frontend works against the new backend without changes
- [ ] Demo data seeding preserved (equivalent of `DataSeeder`)
- [ ] All endpoints return responses in the same structure; errors are structured JSON with appropriate status codes — never a raw stack trace
- [ ] `POST` endpoints return `201 Created` with the created resource
- [ ] Input validated with `class-validator` + `ValidationPipe`; invalid input returns `400 Bad Request` listing which fields failed and why
- [ ] Multi-step writes are atomic (`$transaction`), with a brief comment explaining what state would be corrupted otherwise
- [ ] Defects from your BEVN-003 audit are fixed, not ported — the PR description lists each one and how the new code avoids it
- [ ] Existing backend unit tests ported to the new stack (Jest or Vitest) and passing
- [ ] API documentation from BEVN-002 survives the migration (e.g. `@nestjs/swagger`) — `/swagger` works on the new backend
- [ ] No N+1 queries: list endpoints execute a bounded number of queries regardless of record count
- [ ] The CI workflow from EXT-110 is updated to build and test the new backend
- [ ] `docker-compose up --build` brings up the app with the new backend; README updated with new run instructions
