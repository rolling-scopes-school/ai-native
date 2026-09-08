# BEVN-001 — Codebase Mapping

> Phase 0 — Discovery · both tracks · free-form
> Rules & route: [README.md](../README.md)

Explore the backend codebase and produce a written map of what exists. Document the project structure, the responsibility of each layer (Controllers, Services, Models, Data), and the relationships between entities. Draw an entity-relationship diagram. Identify the request flow from HTTP call to database and back. At the end, a new team member should be able to understand the architecture from your document without reading the code.

**Definition of Done:**
- [ ] Entity-relationship diagram created (any format: draw.io, Mermaid, plain ASCII)
- [ ] Layer responsibility table written: Controllers, Services, Models/Data mapped to their roles
- [ ] Request flow documented for at least 3 endpoints end-to-end
- [ ] Saved as `docs/architecture.md` in the project root

> **Pilot addition — the map is yours, not the agent's.** The original text above says "backend"; the file is `architecture.md`, so map **both** the backend and the frontend: how they talk to each other, what is stored in the database.
>
> The bar: imagine a call where you explain this project to a customer — frontend, backend, how they communicate, the database — at a high level, without opening the file. Then go one step deeper: take one feature (registration is a good one) and explain it end-to-end — what happens on each layer, and how it is covered by tests. On the project that has the most open positions there are no testers, so this second part is what you will be asked at the defense.
>
> Reviewers already see one pattern: the task is handed to the agent, the agent produces a document, and the result is not verified. Read the map against the code. Anything in it you cannot explain is not yet yours.
>
> **Added to the Definition of Done:**
> - [ ] The frontend is on the map: main modules, how it calls the backend
> - [ ] You can tell one feature end-to-end (layers + tests) without reading the file
