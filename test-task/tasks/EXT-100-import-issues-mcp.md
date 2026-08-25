# EXT-100 — Import the Route as GitHub Issues (MCP)

> Setup · both tracks · free-form
> Rules: [README.md](../README.md) · Route: [PRODUCT.md](../PRODUCT.md)

The route you are about to walk lives as markdown files in this program repository. Your **working repository** (your private copy of the code template) needs its own tracker: one GitHub Issue per task, so that every branch and PR can reference the issue it implements — the same "ticket → branch → PR" chain used on real projects.

Don't click the issues together by hand. This is your first agent task: set up the **GitHub MCP server** for your coding agent, and have the agent create the issues for you. MCP (Model Context Protocol) is how agents get tools beyond the local filesystem — knowing how to connect and use an MCP server is part of the job.

**Definition of Done:**
- [ ] GitHub MCP server configured for your coding agent (how you did it — a couple of lines in `docs/devlog.md`)
- [ ] Your repository copy has one issue per task of your chosen track, in route order; the optional BEVN-101 is labeled as optional
- [ ] Each issue: title `<ID> — <task name>`, body contains the full task text copied from this repository
- [ ] The issues were created by the agent through MCP — not by hand in the web UI
- [ ] From this point on, every PR description references its issue (`Closes #N`)
