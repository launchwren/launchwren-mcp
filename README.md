# LaunchWren MCP server

A read-only, remote [MCP](https://modelcontextprotocol.io) server for [LaunchWren](https://launchwren.com), the free weekly launch platform for indie makers.

Ask your AI assistant where to launch a product, which launch directories give a dofollow link on the free plan, or what launched this week.

- Endpoint (Streamable HTTP): `https://launchwren.com/mcp`
- No API key, no sign-in. Read-only.
- Website: [launchwren.com](https://launchwren.com)

## Tools

| Tool | What it does |
|---|---|
| `search_directories` | Search 170+ launch directories and Product Hunt alternatives: DR, free plan, wait time, dofollow rule, badge requirement. Filters: `query`, `free_only`, `dofollow_only`, `no_badge`, `min_dr`, `limit`. Same data as [launchwren.com/launch-directories](https://launchwren.com/launch-directories). |
| `list_launches` | List the products launching in one week (Monday to Sunday, UTC). Optional `week` as `YYYY-MM-DD` (a Monday). |
| `get_launch` | Get one launch by its slug, for example `testoptim` from [launchwren.com/p/testoptim](https://launchwren.com/p/testoptim). |

## Connect

Claude Code:

```sh
claude mcp add --transport http launchwren https://launchwren.com/mcp
```

Cursor, VS Code, LobeHub and other clients: add a remote (HTTP) MCP server with the URL `https://launchwren.com/mcp`.

```json
{
  "mcpServers": {
    "launchwren": { "url": "https://launchwren.com/mcp" }
  }
}
```

## Example prompts

- "Which launch directories have a free plan and a dofollow link, with no badge needed?"
- "What is launching on LaunchWren this week?"
- "Compare Uneed, Fazier and Peerlist as launch sites."

## Launch your product

Launches on LaunchWren are free: [submit your product](https://launchwren.com/submit) and it goes live in the next open week.

## License

MIT
