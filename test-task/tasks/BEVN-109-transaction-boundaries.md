# BEVN-109: Fix transaction boundaries in multi-step writes

> Phase 1A: Stabilize | Track A only | Free-form
>
> Rules and route: [README.md](../README.md)

The registration flow saves an attendee and a registration in separate `SaveChangesAsync` calls without a transaction. A failure between those writes can leave an attendee without a matching registration.

Find all multi-step write operations and make them atomic.

## Definition of done

- [ ] Wrap every multi-step write operation in a transaction
- [ ] Add a short comment to each transactional method stating which inconsistent state the transaction prevents
- [ ] Keep all existing unit tests passing
