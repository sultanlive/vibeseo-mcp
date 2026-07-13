**en** • [es](README.es.md) • [de](README.de.md) • [ja](README.ja.md) • [fr](README.fr.md) • [pt](README.pt.md) • [ru](README.ru.md) • [it](README.it.md) • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**Model Context Protocol server for SEO research, audits, and content workflow — secured by OAuth.**

VibeSEO MCP brings live SEO work into your AI assistant. Connect Claude, ChatGPT, Cursor, VS Code, or a CLI client to VibeSEO. Then ask for keyword research, audits, backlinks, Search Console trends, and content workflow actions in natural language.

- **Server URL:** `https://mcp.vibeseo.dev/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.1 with PKCE, scope `mcp:tools`
- **Landing & setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Install

VibeSEO MCP is a **remote, OAuth-secured** server. Add this to your client's MCP config:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

**One-click install:**

<a href="https://cursor.com/en/install-mcp?name=vibeseo&config=eyJuYW1lIjoidmliZXNlbyIsInR5cGUiOiJodHRwIiwidXJsIjoiaHR0cHM6Ly9tY3AudmliZXNlby5kZXYvbWNwIn0="><img src="https://vibeseo.dev/icons/cursor.svg" width="36" alt="Cursor"></a>&nbsp;&nbsp;<a href="https://insiders.vscode.dev/redirect/mcp/install?name=vibeseo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.vibeseo.dev%2Fmcp%22%7D"><img src="https://vibeseo.dev/icons/vscode.svg" width="36" alt="VS Code"></a>&nbsp;&nbsp;<a href="https://claude.ai/settings/connectors"><img src="https://vibeseo.dev/icons/claude-desktop.svg" width="36" alt="Claude"></a>&nbsp;&nbsp;<a href="https://chatgpt.com/settings/connectors"><img src="https://vibeseo.dev/icons/chatgpt-icon.svg" width="36" alt="ChatGPT"></a>

CLI clients (Claude Code, Gemini CLI, Codex CLI) and manual snippets: see [Supported clients](#supported-clients).

## Quick start

1. Create a VibeSEO account at [vibeseo.dev](https://vibeseo.dev) and start a trial — $0 today, card required (see [Plans & access](#plans--access)).
2. Open the [VibeSEO MCP page](https://vibeseo.dev/mcp) and follow the setup link for your client.
3. Use the one-click install, copied CLI command, or manual JSON/TOML snippet.
4. Authorize with OAuth when your client opens the consent screen.
5. Ask your assistant for SEO work in natural language.

## What you can do from chat

- **🔍 Keyword research** — volumes, CPC, difficulty, intent, autocomplete ideas, question keywords, comparisons, and related terms.
- **🌐 Domain analysis** — domain overview, top keywords, top pages, traffic history, and competitor suggestions.
- **🛠️ Site audits** — start audits, read crawl results, list issues, and prioritize fixes.
- **📈 GSC performance** — connected Google Search Console summaries, top queries, top pages, trends, and query-level diagnostics.
- **🔗 Backlinks** *(Pro)* — profile, referring domains, anchor text, and history of any domain.
- **🚀 Content workflow** *(Pro)* — list posts, refresh ideas, generate drafts, approve ready articles, schedule, and review.

## Tool surface

The MCP server maps to the same SEO workflow inside VibeSEO. Categories:

| Category | What it covers |
|---|---|
| 📁 **Projects** | List projects, read project and site information, list and replace tracked competitors. |
| 🔍 **Keywords** | Metrics, autocomplete, related, question, preposition and comparison keywords, lookup history. |
| 🌐 **Domains** | Overview, top keywords, top pages, traffic history, competitor ideas, lookup history. |
| 🧯 **Audits** | Start site audits, read summaries, list issues, inspect crawled pages. |
| 📊 **GSC** | Connection status, summaries, top queries, top pages, trends, query details. |
| ⚔️ **Competitive** | Competitive overview and keyword gap analysis across domains. |
| 📍 **Locations** | Countries, languages, locations, city lookups, location codes for market-specific research. |
| 🔗 **Backlinks** *(Pro)* | Profile, referring domains, anchors, backlink history. |
| ✍️ **Content** *(Pro)* | Ideas, drafts, approvals, scheduling, content calendar, publications, keyword scoring. |

The live tool set evolves. For the exact, up-to-date list, run `tools/list` against `https://mcp.vibeseo.dev/mcp`.

## Plans & access

The tools call paid data providers and AI models on your behalf, so they need a live VibeSEO subscription — a trial or a paid plan. There is no anonymous or free-forever tier.

| | Trial | SEO Researcher | Pro |
|---|---|---|---|
| **Price** | $0 today, card required | $9/mo | $39/mo |
| Keywords, domains, audits, GSC, competitive, locations | ✅ | ✅ | ✅ |
| Backlink data | — | — | ✅ |
| AI content workflow (ideas, drafts, publishing) | — | — | ✅ |
| Monthly credits | 40 | 400 | 1500 |

The trial is card-required, starts at $0, and can be cancelled at any time; it runs at research-level limits and converts to the plan you picked when it ends. Credits meter the calls that cost money (keyword lookups, audits, AI generation) — see [vibeseo.dev/pricing](https://vibeseo.dev/pricing) for the current plans.

**You never have to leave the chat to pay.** If you call a tool without an active subscription, out of credits, or on a plan that doesn't include it, the tool result comes back with a one-click checkout or top-up link for your account.

## Supported clients

Setup paths for each:

- **Claude** (web & desktop) — Connectors page or `claude_desktop_config.json`
- **ChatGPT** — custom MCP connector with OAuth
- **Cursor** — one-click install via deeplink, or `~/.cursor/mcp.json`
- **VS Code** — one-click install via deeplink, or `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Generic HTTP MCP client** — point at the URL, let it complete OAuth discovery

Full per-client install instructions: [docs/setup.md](docs/setup.md).

## Cursor plugin

This repository is also a Cursor plugin. It contributes one MCP server (`vibeseo`) and no rules, skills, agents, or hooks.

```
.cursor-plugin/plugin.json   ← plugin manifest
mcp.json                     ← the MCP server it contributes
assets/logo.svg              ← plugin logo
```

`mcp.json` points Cursor at the hosted server:

```json
{
  "mcpServers": {
    "vibeseo": {
      "type": "http",
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

There is nothing to configure. No API key or environment variable is required: the server advertises OAuth 2.1 metadata, and Cursor registers itself dynamically and opens the consent screen on first use. Authorizing needs a VibeSEO account on a trial or paid plan — see [Plans & access](#plans--access).

## Example prompts

**Keyword plan**
> "Find comparison keywords for my invoicing app that are realistic to rank for."

→ VibeSEO returns a prioritized topic list (commercial intent, lower difficulty, comparison angle).

**Technical audit**
> "Audit my project and tell me what to fix before publishing more articles."

→ VibeSEO turns crawl data into next actions (missing canonicals, oversized images, internal-link gaps).

**Publish queue**
> "Show ready posts, generate the next draft, and schedule the strongest one."

→ VibeSEO manages the content workflow (counts of Ready/Drafting, schedules the next approved article).

More: [docs/examples.md](docs/examples.md).

## Authorization & approval gate

Auth is OAuth 2.1 with PKCE. Your assistant gets a token scoped to `mcp:tools`, tied to your VibeSEO account. Tokens are revocable at any time from the [VibeSEO MCP page](https://vibeseo.dev/mcp) under "Connected clients" — disconnecting a client revokes its access immediately.

**MCP can help manage the workflow, but VibeSEO keeps the approval gate before content goes live.** Drafts and scheduled posts still go through the standard review step inside VibeSEO.

OAuth flow details: [docs/oauth.md](docs/oauth.md).

## Troubleshooting

Common connection, OAuth, and tool-call errors: [docs/troubleshooting.md](docs/troubleshooting.md).

## Project links

- Product: [vibeseo.dev](https://vibeseo.dev)
- VibeSEO MCP page: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- MCP server: `https://mcp.vibeseo.dev/mcp`
- OAuth issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## License

MIT — see [LICENSE](LICENSE).

---

Built by [@sultanlive](https://github.com/sultanlive). VibeSEO is a hosted SEO platform; this repo is documentation for its public MCP server. Server source is not open.
