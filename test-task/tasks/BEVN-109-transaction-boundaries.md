# BEVN-109 — Fix Transaction Boundaries in Multi-Step Writes

> Phase 1A — Stabilize · Track A only · free-form
> Rules: [ASSIGNMENT.md](../README.md) · Route: [PRODUCT.md](../PRODUCT.md)

The registration flow saves an attendee and then saves a registration in two separate `SaveChangesAsync` calls with no transaction. If anything fails between the two saves, the database is left in an inconsistent state — an attendee row with no matching registration. Find all multi-step write operations and make them atomic.

**Definition of Done:**
- [ ] Multi-step write operations are wrapped in a transaction
- [ ] A brief comment in each transactional method explains what state would be corrupted without the transaction
- [ ] Existing unit tests still pass
