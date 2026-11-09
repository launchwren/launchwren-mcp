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
| `my_launches` | Signed-in endpoint only: your own launches with status, votes, rank, reviews, views, clicks and badge status. |

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

### Signed-in endpoint (OAuth)

`https://launchwren.com/mcp/auth` has the same tools plus `my_launches`. It uses OAuth 2.1: authorization code with PKCE (S256), dynamic client registration and refresh tokens. The scope is `launches:read` (read-only). Clients find the sign-in automatically from the `401` response:

- Protected resource metadata: `https://launchwren.com/.well-known/oauth-protected-resource/mcp/auth`
- Authorization server metadata: `https://launchwren.com/.well-known/oauth-authorization-server`

You sign in with Google on launchwren.com and approve read-only access.

## Example prompts

- "Which launch directories have a free plan and a dofollow link, with no badge needed?"
- "What is launching on LaunchWren this week?"
- "Compare Uneed, Fazier and Peerlist as launch sites."

## Launch your product

Launches on LaunchWren are free: [submit your product](https://launchwren.com/submit) and it goes live in the next open week.

## License

MIT
