# 100Hires MCP Server

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Official MCP Registry](https://img.shields.io/badge/MCP%20Registry-com.100hires%2F100hires-blue)](https://registry.modelcontextprotocol.io/v0/servers/com.100hires%2F100hires/versions/latest)
[![smithery badge](https://smithery.ai/badge/100hires/mcp-server)](https://smithery.ai/servers/100hires/mcp-server)
[![Glama](https://img.shields.io/badge/Glama-Listed-blueviolet)](https://glama.ai/mcp/connectors/com.100hires/100hires)

Official [Model Context Protocol](https://modelcontextprotocol.io/) server for [100Hires](https://100hires.com) — the applicant tracking system for recruiting teams.

Connect ChatGPT, Claude, Cursor, or any MCP-compatible AI assistant to your 100Hires account and manage candidates, jobs, applications, interviews, messages, and more — all without writing code.

> **Full documentation, screenshots, and demo:** https://100hires.com/mcp

## Quick connect

The server is hosted at **`https://mcp.100hires.com/mcp`** with OAuth 2.1 authentication (DCR + PKCE). No install required — just point your client at the URL and authenticate via the browser.

### Native HTTP transport (recommended)

#### claude.ai Cowork (web)

Settings → Custom Connectors → Add → URL: `https://mcp.100hires.com/mcp` → complete OAuth.

#### Claude Code CLI

```bash
claude mcp add --transport http 100hires https://mcp.100hires.com/mcp
```

Or in `.mcp.json`:

```json
{
  "mcpServers": {
    "100hires": {
      "type": "http",
      "url": "https://mcp.100hires.com/mcp"
    }
  }
}
```

#### Claude Desktop

Settings → Developer → Custom Connectors → Add Custom Connector → URL: `https://mcp.100hires.com/mcp`.

#### Cursor

`~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "100hires": {
      "type": "http",
      "url": "https://mcp.100hires.com/mcp"
    }
  }
}
```

#### Codex (OpenAI CLI)

`~/.codex/config.toml`:

```toml
[mcp_servers.100hires]
url = "https://mcp.100hires.com/mcp"
```

#### VS Code Copilot

`.vscode/mcp.json`:

```json
{
  "servers": {
    "100hires": {
      "type": "http",
      "url": "https://mcp.100hires.com/mcp"
    }
  }
}
```

### Fallback for stdio-only clients (`mcp-remote` shim)

For older clients that don't yet support HTTP transport natively, use the third-party [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) bridge:

```json
{
  "mcpServers": {
    "100hires": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.100hires.com/mcp"]
    }
  }
}
```

## What you can do

The server exposes the full 100Hires API as MCP tools, covering:

- **Candidates** — list, create, update, tag, attach files, view timeline, message
- **Applications** — list, move through pipeline stages, advance, hire, reject, transfer
- **Jobs** — list, create, publish to job boards, manage hiring team, set up webhooks
- **Interviews** — schedule, list, retrieve details
- **Messages & email templates** — schedule, batch-send, manage notification emails, build nurture campaigns
- **Notes & evaluations** — full CRUD for application-level feedback
- **Forms & questions** — application form management
- **Workflows** — pipeline stages, reusable questions
- **Companies, users, taxonomy** — sources, statuses, departments, categories, tags, etc.

See the full tool reference at https://100hires.com/mcp/tools.

## Authentication

The server uses **OAuth 2.1** with [Dynamic Client Registration (RFC 7591)](https://datatracker.ietf.org/doc/html/rfc7591) and [PKCE](https://datatracker.ietf.org/doc/html/rfc7636) per the [MCP authorization spec](https://modelcontextprotocol.io/specification/authorization).

Compatible clients discover the OAuth metadata automatically — no manual API key setup required. You can revoke a connected client at any time from **Settings → API → Connected AI clients** in your 100Hires account.

## Status & registry

- Listed in the [Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers/com.100hires%2F100hires/versions/latest) as `com.100hires/100hires`
- Listed on [Glama](https://glama.ai/mcp/connectors/com.100hires/100hires)
- Submitted to [PulseMCP](https://www.pulsemcp.com/), [mcp.directory](https://mcp.directory/), [LobeHub](https://lobehub.com/mcp), [MCP Server Finder](https://mcpserverfinder.com/), and [Smithery](https://smithery.ai/)

## Support

- **Docs:** https://100hires.com/mcp
- **API reference:** https://100hires.com/api
- **Issues / feedback:** support@100hires.com

## License

MIT — see [LICENSE](./LICENSE).
