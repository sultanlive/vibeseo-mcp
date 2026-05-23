# OAuth — how access works

VibeSEO MCP uses OAuth 2.1 with PKCE, following the MCP authorization spec. Tokens are tied to your VibeSEO account and scoped to `mcp:tools`. Compatible clients discover the flow automatically — you only see the consent screen.

## Discovery flow

1. Your MCP client sends its first JSON-RPC request (e.g. `POST /mcp` with `tools/list`).
2. The server responds with:
   ```
   HTTP/2 401
   WWW-Authenticate: Bearer resource_metadata="https://mcp.vibeseo.dev/.well-known/oauth-protected-resource/mcp"
   ```
3. The client fetches the protected-resource metadata:
   ```
   GET https://mcp.vibeseo.dev/.well-known/oauth-protected-resource/mcp
   ```
   Response:
   ```json
   {
     "resource": "https://mcp.vibeseo.dev/mcp",
     "authorization_servers": ["https://api.vibeseo.dev"],
     "bearer_methods_supported": ["header"],
     "scopes_supported": ["openid", "offline_access", "mcp:tools"],
     "resource_documentation": "https://vibeseo.dev/docs/mcp"
   }
   ```
4. The client fetches the authorization-server metadata:
   ```
   GET https://api.vibeseo.dev/.well-known/oauth-authorization-server
   ```
   This returns the `authorization_endpoint`, `token_endpoint`, `jwks_uri`, supported grant types (`authorization_code`, `refresh_token`), and PKCE challenge methods (`plain`, `S256`).
5. The client opens the authorization endpoint in a browser — you sign in to VibeSEO and approve the requested scopes.
6. The client exchanges the auth code for a token at the token endpoint.
7. Subsequent requests carry `Authorization: Bearer <token>` and reach the tool surface.

## Scope

The only scope you grant is **`mcp:tools`** (plus `openid` and `offline_access` for identity + refresh). It lets the assistant call the published MCP tools. It does **not** bypass internal approval gates — drafts and scheduled posts still go through review.

## Managing access

The [VibeSEO MCP page](https://vibeseo.dev/mcp) lists every client that has completed OAuth under "Connected clients". You can disconnect any client to revoke its access immediately. To reconnect, the user has to authorize again.

## Token lifetime

Access tokens are short-lived; the refresh token (via `offline_access`) lets your client renew without re-prompting until you explicitly revoke from the VibeSEO MCP page.
