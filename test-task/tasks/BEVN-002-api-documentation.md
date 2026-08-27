# BEVN-002: API documentation

> Phase 0: Discovery | Both tracks | Free-form
>
> Rules and route: [README.md](../README.md)

The API has no documentation. Add Swagger/OpenAPI so callers can inspect and test the API without reading the source code. Document every endpoint, including its request and response schemas.

## Definition of done

- [ ] All existing endpoints are documented and available through Swagger UI at `/swagger`
- [ ] Each endpoint has a description, expected inputs, possible responses, and at least one example request body
- [ ] Each endpoint can be tested from Swagger UI
- [ ] A frontend developer can build against the API using only Swagger UI
