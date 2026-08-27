# EXT-150: Migrate the backend to TypeScript with NestJS

> Phase 1B: Migration | Track B only | Spec-driven | Replaces Phase 1A
>
> Rules and route: [README.md](../README.md)

Reimplement the backend in TypeScript with NestJS and Prisma while keeping PostgreSQL. Preserve the existing API contract so the React frontend continues to work without changes.

Use the existing backend as the source of truth for behavior. Do not copy its defects into the new implementation. Fix the issues identified in BEVN-003 as part of the migration.

## Definition of done

- [ ] Reimplement the backend with TypeScript, NestJS, and Prisma while keeping PostgreSQL
- [ ] Preserve every existing endpoint path, HTTP method, and response data so the frontend works without changes
- [ ] Preserve demo data seeding equivalent to `DataSeeder`
- [ ] Use one consistent response structure across endpoints
- [ ] Return structured JSON errors with appropriate HTTP status codes and never expose raw stack traces
- [ ] `POST` endpoints return `201 Created` with the created resource
- [ ] Validate input with `class-validator` and `ValidationPipe`
- [ ] Invalid input returns `400 Bad Request` and identifies each failed field and the reason
- [ ] Make multi-step writes atomic with `$transaction`
- [ ] Add a short comment to each transactional operation stating which inconsistent state the transaction prevents
- [ ] Fix the defects identified in BEVN-003, and list each defect in the Pull Request description with how the new backend avoids it
- [ ] Port the existing backend unit tests to Jest or Vitest and keep them passing
- [ ] Preserve the BEVN-002 API documentation with a NestJS equivalent such as `@nestjs/swagger`
- [ ] Keep `/swagger` working
- [ ] Avoid N+1 queries so list endpoints use a bounded number of queries as record count grows
- [ ] Update the EXT-110 CI workflow to build and test the new backend
- [ ] `docker-compose up --build` starts the application with the new backend
- [ ] Update the README with the new run instructions
