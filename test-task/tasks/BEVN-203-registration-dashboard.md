# BEVN-203 — Attendee Registration Dashboard

> Phase 2 — New Features · both tracks · SPEC-DRIVEN
> Rules: [ASSIGNMENT.md](../README.md) · Route: [PRODUCT.md](../PRODUCT.md)

An attendee can view all their conference registrations in one place. The dashboard shows each registration with conference name, dates, status, and a cancel button. Cancellation triggers the same waitlist promotion logic as BEVN-202.

**Definition of Done:**
- [ ] `GET /api/attendees/{email}/registrations` returns all registrations with conference context
- [ ] Dashboard page accessible at `/dashboard` with an email input to look up registrations
- [ ] Each registration shows conference name, dates, status
- [ ] Confirmed registrations have a cancel button; cancelled ones are read-only
- [ ] Cancellation refreshes the list
- [ ] Empty state shown when no registrations found for the email
