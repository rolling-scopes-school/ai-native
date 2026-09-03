# EXT-100: Import the route as GitHub Issues with MCP

> Setup | Both tracks | Free-form
>
> Rules and route: [README.md](../README.md)

The task route is stored as Markdown in this repository. Your working repository needs one GitHub Issue for each task so branches and Pull Requests can reference the work they implement.

Configure the GitHub MCP server for your coding agent and use the agent to create the issues. MCP gives the agent tools for working with GitHub directly.

Do not create the issues manually in the GitHub web UI.

## Definition of done

- [ ] Configure the GitHub MCP server for your coding agent and record the setup briefly in `docs/devlog.md`
- [ ] State your chosen track, A or B, in the Pull Request description and give one sentence explaining why
- [ ] Create one issue for each task in your chosen track, in route order
- [ ] Label the optional BEVN-101 issue as optional
- [ ] Use the issue title format `<ID> — <task name>`
- [ ] Copy the full task text from this repository into each issue body
- [ ] Create the issues through the agent and GitHub MCP, not manually in the web UI
- [ ] Starting with the next task, reference the related issue in every Pull Request description with `Closes #N`
