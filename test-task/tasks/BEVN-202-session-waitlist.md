# BEVN-202: Session waitlist

> Phase 2: New features | Both tracks | Spec-driven
>
> Rules and route: [README.md](../README.md)

Add a waitlist for full sessions. An attendee can join the waitlist after a session reaches capacity. When a confirmed attendee cancels, promote the first waitlisted attendee automatically and log the promotion.

The session detail page should show the current registration count, capacity, and waitlist count.

## Definition of done

- [ ] `POST /api/sessions/{id}/waitlist` adds an attendee to the waitlist
- [ ] Registering for a full session returns `409` and does not add the attendee to the waitlist
- [ ] Cancelling a confirmed registration promotes the next waitlisted attendee
- [ ] Log each promotion at `INFO` level with the attendee ID and session ID
- [ ] `GET /api/sessions/{id}` includes `registeredCount`, `capacity`, and `waitlistCount`
- [ ] The session detail page shows capacity and waitlist count
- [ ] Unit tests cover joining the waitlist, promotion after cancellation, and waitlist ordering
