# BEVN-205 — End-to-End Test Suite

> E2E Testing · both tracks · SPEC-DRIVEN
> Rules & route: [README.md](../README.md)

Cover the three critical user flows with end-to-end tests using Playwright. Tests run against the live `docker-compose` stack — no mocked API responses for happy-path scenarios. The suite is integrated into the GitLab CI pipeline and blocks merging on failure.

**Definition of Done:**
- [ ] Playwright configured in `frontend/` or a dedicated `e2e/` folder
- [ ] Flow 1: Browse conferences → open detail → view sessions
- [ ] Flow 2: Open session detail → register attendee → verify registration appears
- [ ] Flow 3: Open conference search → apply keyword filter → verify results update
- [ ] Each flow includes at least one failure case (e.g. register with empty email, search with no results)
- [ ] Tests pass against `docker-compose up` stack
- [ ] `.gitlab-ci.yml` has an `e2e` job in the `test` stage that starts the stack and runs Playwright
- [ ] Failed test screenshots saved as GitLab CI artifacts

> **Pilot addition:** two DoD items above are remapped to this pilot's setup.
> Conference search (Flow 3) is not part of this route — replace Flow 3 with the waitlist
> flow you built in BEVN-202: *register attendees until the session is full → next
> registration is rejected → join the waitlist → cancel a confirmed registration → verify
> the first waitlisted attendee is promoted*. And CI here is GitHub Actions, not GitLab:
> the `e2e` job goes into your `.github/workflows/ci.yml` from EXT-110, with failed-test
> screenshots uploaded as workflow artifacts.
