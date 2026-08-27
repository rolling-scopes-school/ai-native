# BEVN-203: Attendee registration dashboard

> Phase 2: New features | Both tracks | Spec-driven
>
> Rules and route: [README.md](../README.md)

Add a dashboard where an attendee can view all conference registrations associated with their email. Show the conference name, dates, registration status, and cancellation controls.

Cancelling a registration must use the same waitlist promotion behavior introduced in BEVN-202.

## Definition of done

- [ ] `GET /api/attendees/{email}/registrations` returns all registrations with conference context
- [ ] `/dashboard` provides an email input for looking up registrations
- [ ] Each registration shows the conference name, dates, and status
- [ ] Confirmed registrations have a cancel button
- [ ] Cancelled registrations are read-only
- [ ] Cancelling a registration refreshes the list
- [ ] Show an empty state when no registrations are found for the email
