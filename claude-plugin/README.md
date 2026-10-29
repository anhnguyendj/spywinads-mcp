# SpyWinAds plugin for Claude

Check Facebook video ads before you spend money testing a product. This plugin connects Claude to the SpyWinAds MCP server and adds skills that turn its data into a clear, honest report.

## What it adds

- **MCP server** `https://spywinads.com/mcp` (remote, Streamable HTTP). 5 read-only tools: look up a video ad's real age and the stores running the same video, see a store's or a Facebook Page's video ads, copy a public Shopify product to an import CSV, and read the SpyWinAds Video Reuse Index.
- **Skill `check-ad-before-testing`**: from a Meta Ad Library link, reports how old the video really is, how far it has spread, which stores ran it first in the library, and what the data can't tell.
- **Skill `spy-competitor-store`**: from a store domain or Facebook Page, reports live and new ads and which top videos are new or widely copied.
- **Skill `get-started`**: picks the right tool for what you give it and keeps answers within what the data shows.

## Sign-in and limits

The research tool works without an account. The other tools ask you to sign in to SpyWinAds (OAuth, then click **Allow**). Free plan: 30 calls a day, resetting at 00:00 UTC+7. Revoke access any time in SpyWinAds Settings → API & MCP.

## What the plugin sends and stores

The plugin itself runs no code and makes no network calls of its own. Claude calls the SpyWinAds server above when a skill or your question needs data. The server reads SpyWinAds' own database; the only outside fetch is the public Shopify product page you ask it to copy. SpyWinAds logs the tool name, success or error and the calling app, not your prompts. Privacy policy: https://spywinads.com/privacy

## Data limits

Meta ads shown in the US, from the SpyWinAds library. Counts are minimums of ads observed, not sales. No ad spend, reach, orders or revenue data. "Earliest store" means earliest in the library, not the verified owner of the video.

## Example prompts

- "Is this video ad new or an old video brought back? https://www.facebook.com/ads/library/?id=1014622548199238"
- "What Facebook video ads is zenblux.com running, and which videos are copied by other stores?"
- "Copy this Shopify product into a CSV I can import: https://www.allbirds.com/products/mens-tree-runners"

Docs: https://spywinads.com/developers · Support: support@spywinads.com · Publisher: ATT ECOMMERCE COMPANY LIMITED, Hanoi, Vietnam
