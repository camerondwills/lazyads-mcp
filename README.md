# Lazy Ads MCP

Public listing for the [Lazy Ads](https://lazyads.ai) MCP server.

Connect Claude, Cursor, Hermes, and any MCP-compatible client to your ad accounts across **nine networks**: Meta (Facebook + Instagram), Google, TikTok, LinkedIn, Reddit, Apple, Bing, ChatGPT, and Snapchat.

This repository is documentation only. It does not contain product source code.

## Hosted endpoint

- **URL:** `https://mcp.lazyads.ai/mcp`
- **Protocol:** MCP 2026-07-28 Streamable HTTP
- **Auth:** API key from Lazy Ads → Settings → API (any paid plan)

Docs: [lazyads.ai/mcp](https://lazyads.ai/mcp)

## Connect (Claude / Cursor / Windsurf)

```json
{
  "mcpServers": {
    "lazyads": {
      "url": "https://mcp.lazyads.ai/mcp",
      "headers": {
        "Authorization": "Bearer your-api-key"
      }
    }
  }
}
```

`X-API-Key` is also accepted.

## Connect (Hermes)

```yaml
mcp_servers:
  lazyads:
    url: "https://mcp.lazyads.ai/mcp"
    headers:
      Authorization: "Bearer your-api-key"
    description: "LazyAds MCP — 9-platform ad management"
```

Hermes skill: [`SKILL.md`](./SKILL.md) in this repo, or the live guide at [lazyads.ai/hermes](https://lazyads.ai/hermes)

## What you get

- **BYOA:** 33 bridge tools to create, update, pause, and measure campaigns on all nine networks
- **Starter and above:** full suite (45 tools), including Lazy Ads AI

Free accounts can onboard and browse competitor ads. AI tools require a paid plan with tokens.

## Pricing

See [lazyads.ai/pricing](https://lazyads.ai/pricing). Plans: BYOA, Starter, Growth, Scale. Flat SaaS, bring your own ad accounts, no percent of spend.

## Links

- Site: https://lazyads.ai
- MCP docs: https://lazyads.ai/mcp
- Pricing: https://lazyads.ai/pricing
- Hermes: https://lazyads.ai/hermes
- Blog: https://lazyads.ai/blog

## License

Documentation in this repo is MIT. Lazy Ads the product remains a separate, private codebase.
