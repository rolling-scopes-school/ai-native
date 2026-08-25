# BEVN-107 — Add Input Validation

> Phase 1A — Stabilize · Track A only · free-form
> Rules & route: [README.md](../README.md)

The API accepts any payload without validation. Submitting a registration with an empty email, creating a conference with no title, or sending a completely empty JSON body all either silently succeed or produce an unhelpful 500. Add proper input validation so the API rejects invalid input with a clear error message before it reaches the service layer.

**Definition of Done:**
- [ ] Relevant model properties annotated with `[Required]`, `[MaxLength]`, `[EmailAddress]` where appropriate
- [ ] Controllers annotated with `[ApiController]` so `ModelState` is checked automatically
- [ ] Invalid input returns `400 Bad Request` with a structured message listing which fields failed and why
- [ ] At least two unit or integration tests covering validation failure scenarios
