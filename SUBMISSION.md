# Directory submission kit

Reusable answers for MCP directories and AI app stores. Keep in sync with `README.md` and
spywinads.com/developers. Submit only after SpyWinAds opens the API to all accounts (flag `mo_mcp`).

## Identity

- **Name:** SpyWinAds
- **Server URL:** `https://spywinads.com/mcp` (universal URL, Streamable HTTP, JSON responses)
- **Registry name:** `com.spywinads/mcp` (DNS-verified namespace)
- **Website / docs:** https://spywinads.com/developers
- **Privacy policy:** https://spywinads.com/privacy · **Terms:** https://spywinads.com/terms
- **Support:** support@spywinads.com
- **Publisher:** ATT ECOMMERCE COMPANY LIMITED, Hanoi, Vietnam
- **Icon:** `assets/logo.png` (800×800)
- **Category:** Marketing / E-commerce / Advertising research

## Descriptions

- **Short (≤100):** Facebook video ad intel: a video ad's real age and every store running the same video.
- **Long:** SpyWinAds helps online sellers investigate Facebook video ads. Give it a Meta Ad Library link, a store
  domain or a Facebook Page and it returns when the video file was first uploaded to Facebook (within 1–2 days),
  when its first ad started, how many stores run the same video now and ever, and the earliest stores in the
  SpyWinAds library. It can also export a public Shopify product to a CSV. Data covers Meta ads shown in the US.
  Counts are minimums of ads observed, not sales; no ad spend or revenue data. Read-only.

## Authentication

- OAuth 2.1, authorization code + PKCE S256. Public clients (`token_endpoint_auth_method: none`).
- Client registration: Client ID Metadata Documents (`client_id_metadata_document_supported: true`) and Dynamic
  Client Registration (`/oauth/register`).
- Discovery: `401` + `WWW-Authenticate: Bearer resource_metadata="https://spywinads.com/.well-known/oauth-protected-resource/mcp", scope="ads:read product:export"`.
  Authorization server metadata at `/.well-known/oauth-authorization-server`. `iss` returned on every authorization response.
- Lazy authentication: `initialize`, `tools/list` and `spywin_get_video_reuse_research` work without sign-in; the
  other 4 tools require sign-in. Claude connector setting: **Sign in when needed**.
- Redirect URIs accepted: `https://claude.ai/api/mcp/auth_callback`, `https://chatgpt.com/connector_platform_oauth_redirect`,
  loopback `http://localhost/*` and `http://127.0.0.1/*` on any port (Claude Code), any URI registered by DCR / declared in CIMD.
- Tokens: access 1 hour, refresh 30 days with rotation; reuse of a rotated refresh token or authorization code revokes
  the whole grant. Stored as SHA-256 hashes, bound to resource `https://spywinads.com/mcp`.
- Scopes: `ads:read`, `product:export`, `offline_access`. No write scopes.

## Data source (directory policy question)

SpyWinAds' own API over its own database. The database is built from Meta's public Ad Library (ads shown in the US),
collected by the SpyWinAds desktop app on its users' computers while they research keywords. SpyWinAds does not log in
to Facebook, does not use users' Facebook accounts, and does not call any third-party API through the MCP server —
every tool reads SpyWinAds' database, except `spywin_export_shopify_product`, which fetches the public Shopify product
page the user gives (blocked from private and internal addresses).

## Tools (all read-only)

| Tool | readOnly | destructive | openWorld | Scope |
|---|---|---|---|---|
| spywin_lookup_video_ad | true | false | false | ads:read |
| spywin_spy_store_ads | true | false | false | ads:read |
| spywin_get_page_ads | true | false | false | ads:read |
| spywin_export_shopify_product | true | false | true | product:export |
| spywin_get_video_reuse_research | true | false | false | none (public) |

## Example prompts (≥3)

1. "Is this video ad new or an old video brought back? https://www.facebook.com/ads/library/?id=1014622548199238"
2. "What Facebook video ads is zenblux.com running, and how many other stores use the same videos?"
3. "Which stores share the videos of the Facebook Page https://www.facebook.com/61553397207581/ ?"
4. "Copy this Shopify product into a CSV I can import: https://www.allbirds.com/products/mens-tree-runners"
5. "What does the SpyWinAds Video Reuse Index say about how often old videos are reused in Facebook ads?"

## Test account for reviewers

- **Email:** `app-review@spywinads.com` (internal plan, no daily limit, API and MCP on). Password: 1Password vault `SpyWin VPS`, item "SpyWinAds app reviewer (Claude/ChatGPT)". Never commit it.
- **Steps for the reviewer:** add `https://spywinads.com/mcp` → when a tool asks, sign in with the email + password above → click **Allow**.
- No 2FA, no email code at sign-in.

## Commerce (ChatGPT)

No purchases, plans or upgrade prompts inside ChatGPT or Claude. Limit messages only say the daily limit and when it resets.

## Evaluation

`evaluation.xml` — 10 read-only questions with stable answers (mcp-builder format).
