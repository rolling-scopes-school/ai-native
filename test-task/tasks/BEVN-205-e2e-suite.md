# BEVN-205: End-to-end test suite

> End-to-end testing | Both tracks | Spec-driven
>
> Rules and route: [README.md](../README.md)

Cover the three critical user flows with Playwright end-to-end tests. Run the tests against the live `docker-compose` stack. Do not mock API responses for happy-path scenarios.

The original task targets GitLab CI and a conference search flow. The pilot overrides those two requirements below.

## Definition of done

- [ ] Configure Playwright in `frontend/` or a dedicated `e2e/` folder
- [ ] Flow 1: Browse conferences → open detail → view sessions
- [ ] Flow 2: Open session detail → register attendee → verify the registration appears
- [ ] Flow 3: Open conference search → apply keyword filter → verify results update
- [ ] Each flow includes at least one failure case, such as an empty registration email or a search with no results
- [ ] Tests pass against the `docker-compose up` stack
- [ ] `.gitlab-ci.yml` has an `e2e` job in the `test` stage that starts the stack and runs Playwright
- [ ] Failed test screenshots are saved as GitLab CI artifacts

## Pilot addition

For this pilot, replace these parts of the original definition of done:

1. Replace Flow 3 with the BEVN-202 waitlist flow:

   ```text
   register attendees until the session is full
   → reject the next registration
   → join the waitlist
   → cancel a confirmed registration
   → verify that the first waitlisted attendee is promoted
   ```

2. Use GitHub Actions instead of GitLab CI. Add the `e2e` job to `.github/workflows/ci.yml` from EXT-110 and upload failed-test screenshots as workflow artifacts. A failing e2e job must keep CI red, so the Pull Request cannot be merged under the CI gate.
