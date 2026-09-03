# BEVN-104: Standardize API responses and error handling

> Phase 1A: Stabilize | Track A only | Free-form
>
> Rules and route: [README.md](../README.md)

API responses currently vary between endpoints, and failures may return an ASP.NET error page or raw stack trace. Make the response and error formats consistent for API callers.

## Definition of done

- [ ] All endpoints return responses in the same structure
- [ ] `POST` endpoints return `201 Created` with the created resource instead of `200 OK`
- [ ] Error responses are structured JSON with a message, never HTML or a raw stack trace
- [ ] Common failures such as not found, bad input, and unexpected errors return appropriate HTTP status codes
- [ ] Update at least one existing unit test for the new response shape
