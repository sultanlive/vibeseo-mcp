# Setup — per-client install paths

The hosted page at [vibeseo.dev/mcp](https://vibeseo.dev/mcp) is the canonical setup entry point — overview, one-click links, copied commands, and live OAuth status all live there. This document mirrors those instructions for reference.

**Server URL** (used by every client): `https://mcp.vibeseo.dev/mcp`

Connecting a client only authorizes it. The tools themselves need a live VibeSEO subscription — a card-required trial ($0 today) or a paid plan. See [Plans & access](../README.md#plans--access); if you call a tool without one, the result comes back with a one-click checkout link.

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

**One-click:** the [VibeSEO MCP page](https://vibeseo.dev/mcp) generates the install deeplink dynamically — open it and click "Install in Cursor".

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

**One-click:** the [VibeSEO MCP page](https://vibeseo.dev/mcp) generates the install deeplink dynamically — open it and click "Install in VS Code".

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
