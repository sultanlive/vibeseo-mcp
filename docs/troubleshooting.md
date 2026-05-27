# Troubleshooting

Common errors when connecting to or calling VibeSEO MCP, and what to do about them.

---

## Connection / OAuth

### `WWW-Authenticate: Bearer resource_metadata=...` on first call

Expected. The first request to `mcp.vibeseo.dev/mcp` returns HTTP 401 with the `WWW-Authenticate` header so a compatible MCP client can run OAuth discovery automatically. Authorize in the browser when prompted and the client will retry with a valid token.

### "Invalid redirect_uri" during OAuth consent

The redirect URI sent by your client during Dynamic Client Registration must be a well-formed absolute URL (`https://...`). Self-hosted clients with custom-scheme callbacks (e.g. `cursor://`) work as long as the scheme is valid. If you build your own client, log the exact `redirect_uri` value you POST to `/connect/register` and confirm it matches the `redirect_uri` parameter you later send to `/authorize`.

### OAuth consent screen never appears / popup blocked

Allow popups for `api.vibeseo.dev` in your browser. Some clients open a new tab instead of a popup — check tab focus. After consent, the tab closes automatically and the client resumes.

### Tokens expire / repeated re-auth

VibeSEO issues short-lived access tokens with refresh tokens (`offline_access` scope). If your client does not store the refresh token, it will re-prompt on every session. Confirm the client persists the refresh token between runs.

### Revoking access

In VibeSEO web app: `vibeseo.dev/agent` lists all active OAuth connections with a Revoke button. Revoking immediately invalidates the refresh token; the next tool call will fail with 401 and the user can re-authorize.

---

## Tool calls

### `400 Bad Request — Too many keywords`

`get_keyword_metrics`, `autocomplete_keywords`, `related_keywords`, `question_keywords`, `preposition_keywords`, and `comparison_keywords` accept at most **5 keywords per call**. Split larger lists across multiple calls.

### Keyword Difficulty (`KD`) is `null`

KD requires **both** `locationCode` and `languageCode`. Worldwide calls (both omitted) return null KD. Either pass both parameters, or first call one of the suggestion tools (`autocomplete_keywords`, `related_keywords`) — each returned suggestion includes the `locationCode` / `languageCode` it was scored against, which you can feed back into `get_keyword_metrics`.

### `gsc_summary` returns zeros / empty

The project either has no Google Search Console connection, or the connection was made recently and GSC has not yet backfilled. Call `gsc_status` first — `connected: false` or a recent `lastSyncAt` (under 7 days) explains the empty data. GSC backfill typically completes within 7–14 days of connecting.

### `refresh_ideas` returns a job acceptance, not posts

`refresh_ideas` and `refill_queue` are **async**: they queue a strategist job and return `{ jobId, projectId, mode, wasInFlight }` immediately. The new Idea-status posts appear within ~30–60 seconds. Follow up with `list_posts(projectId, status: "Idea")` to see them.

### `score_keyword` says "keyword not in top-100"

`score_keyword` only scores keywords the project already ranks for. If the keyword is not yet in the project's tracked ranking set, the tool returns an error. Use `autocomplete_keywords` or `domain_top_keywords` to discover ranking keywords first.

### Site audit stays in `running` for a long time

`start_site_audit` triggers a crawl that can take 5–30 minutes depending on page count. Poll `get_audit` with the returned audit ID until `status: "completed"`. If status stays `running` longer than an hour, contact support — there may be a crawler-side block (robots.txt, IP blocking, etc.).

---

## Rate limits

VibeSEO applies per-user rate limits to protect downstream APIs (DataForSEO, Google Search Console, the strategist LLM). When hit, tools return HTTP 429 with a `retry-after` hint. Reduce call frequency or batch related calls.

---

## Still stuck?

- Email: [support@vibeseo.dev](mailto:support@vibeseo.dev)
- Telegram: [@vibeseo_support_bot](https://t.me/vibeseo_support_bot)
- Issue tracker: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)
