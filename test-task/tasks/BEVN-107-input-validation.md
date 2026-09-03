# BEVN-107: Add input validation

> Phase 1A: Stabilize | Track A only | Free-form
>
> Rules and route: [README.md](../README.md)

The API currently accepts invalid payloads or fails with an unhelpful `500` response. Add input validation so invalid data is rejected before it reaches the service layer and the caller receives a clear error response.

## Definition of done

- [ ] Use `[Required]`, `[MaxLength]`, and `[EmailAddress]` on relevant model properties where appropriate
- [ ] Add `[ApiController]` to controllers so ASP.NET Core checks `ModelState` automatically
- [ ] Invalid input returns `400 Bad Request` with a structured message that identifies each failed field and the reason
- [ ] Add at least two unit or integration tests for validation failures
