# BEVN-104 — Standardize API Responses and Error Handling

> Phase 1A — Stabilize · Track A only · free-form
> Rules: [ASSIGNMENT.md](../README.md) · Route: [PRODUCT.md](../PRODUCT.md)

The frontend team keeps running into surprises when consuming the API — different endpoints return data in different shapes, and when something breaks, the full ASP.NET error page (or raw stack trace) comes back. Fix this so the API is predictable for any caller.

**Definition of Done:**
- [ ] All endpoints return responses in the same structure — no surprises per endpoint
- [ ] `POST` endpoints return `201 Created` with the created resource, not `200 OK`
- [ ] Error responses are structured JSON with a message, never an HTML page or raw stack trace
- [ ] Common failure scenarios (not found, bad input, unexpected errors) return appropriate HTTP status codes
- [ ] At least one existing unit test updated to reflect the new response shape
