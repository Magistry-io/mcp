# Magistry MCP server

Magistry is an AI operations platform for online stores. Its remote MCP server lets Claude, ChatGPT, Cursor, Gemini CLI or any MCP client read and run a store that Magistry is connected to: Google Ads and other ad networks, the Merchant Center feed, the catalog, orders, customer service, disputes, costs and the Marketing Brain.

This repository holds no server code. It holds the public manifests and install snippets for the hosted server.

- **Endpoint:** `https://app.magistry.io/api/mcp` (streamable HTTP)
- **Auth:** OAuth 2.1. You sign in to Magistry and choose which store and which scopes the client gets. There is no anonymous access to store data.
- **Official MCP Registry:** `io.magistry/magistry` ([server.json](server.json))
- **Docs:** https://www.magistry.io/platform/developers/mcp
- **REST API:** https://app.magistry.io/api/v1/openapi.json
- **Pricing:** free plan (50 AI credits a month, no credit card); paid plans from $99 a month.

## Works with

Everything the merchant connected in Magistry:

- **Store platforms:** Shopify, WooCommerce, Shopware, Magento, Lightspeed eCom and PrestaShop, or any other platform through Magistry's custom API.
- **Marketplaces:** bol.
- **Advertising:** Google Ads, Meta (Facebook and Instagram), Microsoft Advertising, Pinterest, Reddit, LinkedIn, bol Ads, Criteo, Taboola and Outbrain.
- **Feeds and analytics:** Google Merchant Center, Google Analytics 4 and Search Console.
- **Customer service:** the email inbox and threads Magistry handles.
- **Approvals anywhere:** approval cards from a client land in the Magistry dashboard and in the Magistry app for [iOS](https://apps.apple.com/app/id6809195526) and [Android](https://play.google.com/store/apps/details?id=io.magistry.app).

## What a client can do

Reads cover orders, catalog and variants, ad performance, customer service threads, disputes, costs and expenses, decisions and alerts, and the Marketing Brain. Writes reach Google Ads, Shopify admin, Google Analytics 4 and Merchant Center, plus Magistry's own discounts, drafts and settings.

Every write states its outcome. Depending on the grants the merchant gave the connection, a write is either applied at once or waits as an approval card in Magistry. Each action is logged, price and copy changes can be undone, and a kill switch stops everything. The tool list a client sees is filtered to the scopes it was granted.

## Install

**Claude Code**

```bash
claude mcp add --transport http magistry https://app.magistry.io/api/mcp
```

**Claude (claude.ai or desktop):** Settings → Connectors → Add custom connector → `https://app.magistry.io/api/mcp`.

**ChatGPT:** Settings → Connectors → developer mode → create a connector with `https://app.magistry.io/api/mcp` and OAuth.

**Cursor, Windsurf, Cline and other clients:** use [.mcp.json](.mcp.json):

```json
{
  "mcpServers": {
    "magistry": {
      "type": "streamable-http",
      "url": "https://app.magistry.io/api/mcp"
    }
  }
}
```

**Gemini CLI**

```bash
gemini extensions install https://github.com/Magistry-io/mcp
```

([gemini-extension.json](gemini-extension.json))

## Support

support@magistry.io · https://www.magistry.io

The manifests in this repository are MIT licensed. The Magistry service is governed by its own terms at https://www.magistry.io/legal/terms.
