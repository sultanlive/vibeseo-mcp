# Setup — per-client install paths

The hosted setup page at [vibeseo.dev/agent](https://vibeseo.dev/agent) has one-click links, copied commands, and live OAuth status. This page mirrors those instructions for reference.

**Server URL** (used by every client): `https://mcp.vibeseo.dev/mcp`

---

## Claude (web & desktop)

**One-click:** [claude.ai/settings/connectors](https://claude.ai/settings/connectors) → Add custom connector.

**Manual** (Claude Desktop) — edit `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

Claude Desktop opens a browser window the first time it connects to complete OAuth.

---

## ChatGPT

Custom MCP connector with OAuth.

1. **Settings → Apps & Connectors → Advanced settings** — turn on Developer Mode.
2. **Settings → Connectors → Create**, or **Apps → Create**.
3. Name: `vibeseo`. MCP Server URL: `https://mcp.vibeseo.dev/mcp`. Authentication: OAuth.
4. Confirm, then **Create**.

---

## Cursor

**One-click:** [Install in Cursor](https://vibeseo.dev/agent) (from the hosted setup page — the deeplink is generated dynamically).

**Manual** — `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

---

## VS Code

**One-click:** [Install in VS Code](https://vibeseo.dev/agent) (from the hosted setup page).

**Manual** — `.vscode/mcp.json`:

```json
{
  "servers": {
    "vibeseo": {
      "type": "http",
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

---

## Claude Code (CLI)

```bash
claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp
```

Then run `/mcp` inside Claude Code and authorize in the browser.

---

## Gemini CLI

```bash
gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp
```

**Manual** — `~/.gemini/settings.json` (uses `httpUrl`, not `url`):

```json
{
  "mcpServers": {
    "vibeseo": {
      "httpUrl": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

---

## Codex CLI

```bash
codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp
```

**Manual** — `~/.codex/config.toml`:

```toml
[mcp_servers.vibeseo]
url = "https://mcp.vibeseo.dev/mcp"
```

---

## Generic HTTP MCP client

Point any compatible client at `https://mcp.vibeseo.dev/mcp`. The server returns HTTP 401 with `WWW-Authenticate: Bearer resource_metadata="..."` on the first call, which lets the client complete standard MCP OAuth discovery (OAuth 2.1 with PKCE).

See [docs/oauth.md](oauth.md) for the discovery flow.
