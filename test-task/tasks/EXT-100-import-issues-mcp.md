# EXT-100 — Import the Route as GitHub Issues (MCP)

> Setup · both tracks · free-form
> Rules & route: [README.md](../README.md)

The route you are about to walk lives as markdown files in this program repository. Your **working repository** (your copy of the [code template](https://github.com/dzmitry-varabei/brown-events-pilot)) needs its own tracker: one GitHub Issue per task, so that every branch and PR can reference the issue it implements — the same "ticket → branch → PR" chain used on real projects.

Don't click the issues together by hand. This is your first agent task: set up the **GitHub MCP server** for your coding agent, and have the agent create the issues for you. MCP (Model Context Protocol) is how agents get tools beyond the local filesystem — knowing how to connect and use an MCP server is part of the job.

**Definition of Done:**
- [ ] GitHub MCP server configured for your coding agent (how you did it — a couple of lines in `docs/devlog.md`)
- [ ] The PR description states which track you chose (A or B) and one sentence on why — this is where your track choice is recorded
- [ ] Your repository copy has one issue per task of your chosen track, in route order; the optional BEVN-101 is labeled as optional
- [ ] Each issue: title `<ID> — <task name>`, body contains the full task text copied from this repository
- [ ] The issues were created by the agent through MCP — not by hand in the web UI
- [ ] From this point on, every PR description references its issue (`Closes #N`)

> **Pilot addition — the token.** The GitHub MCP server needs a personal access token. Keep it out of the agent's session. Console agents write the full session log to disk (that is what `codemie analytics` reads), so a token pasted into the chat, or read from a file by the agent, ends up in a log that any other agent or tool on your machine can read. A real question from the Q&A call: the MCP config did not pick up `.env`, so the token was hardcoded into a gitignored `mcp.json` — and the agent still read the file and printed the token into the chat.
>
> What to do: keep the MCP config outside the repository, or reference an environment variable instead of the literal token (most agents support this — check your agent's docs); the agent has no reason to read that file. If a token does get printed — revoke it and issue a new one, it is compromised. The reliable fix is a hook that blocks the agent from reading secret files at all (`.env`, the MCP config) — that is exactly [EXT-302](../side-quests/EXT-302-hook-not-reminder.md), and one participant solved it this way.
