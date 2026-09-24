# Changelog

All notable changes to the VibeSEO MCP listing are recorded here. Versions match the records published to `registry.modelcontextprotocol.io`.

## 0.1.4 — 2026-09-24

- Add GitHub MCP Registry metadata under `_meta` (display name, tags, categories).
- Shorten `description` to the registry's 100-character limit; the listing now names keyword discovery and Search Console explicitly.
- Companion listing: the GEO server is published separately as `dev.vibeseo/geo` from [sultanlive/vibeseo-geo-mcp](https://github.com/sultanlive/vibeseo-geo-mcp).

## 0.1.3 — 2026-05-24

- No functional change. Smoke test of the new CI workflow (`.github/workflows/publish-mcp.yml`) — first publish driven entirely by `git push --tags v0.1.3`.

## 0.1.2 — 2026-05-24

- Add `icons` field — client UIs (Claude Desktop, VS Code `@mcp`, aggregators) now render the VibeSEO brand mark from `vibeseo.dev/brand/vibeseo-icon.svg` instead of a placeholder.

## 0.1.1 — 2026-05-24

- `websiteUrl` → `https://vibeseo.dev/mcp` so users coming from the registry land directly on the MCP page instead of the root domain.

## 0.1.0 — 2026-05-24

- Initial registry listing under the `dev.vibeseo/vibeseo` namespace.
- Streamable-HTTP remote at `https://mcp.vibeseo.dev/mcp`.
- OAuth 2.1 with PKCE, scope `mcp:tools`.
- Tool surface across nine categories: Projects, Keywords, Domains, Backlinks, Audits, GSC, Content, Competitive, Locations.
