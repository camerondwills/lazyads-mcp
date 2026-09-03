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

Store the key in `~/.hermes/.env` as `LAZY_ADS_API_KEY=la_...`, then:

```yaml
mcp_servers:
  lazyads:
    url: "https://mcp.lazyads.ai/mcp"
    headers:
      Authorization: "Bearer ${LAZY_ADS_API_KEY}"
    description: "LazyAds MCP. 9-platform ad management"
```

Install the skill:

```bash
mkdir -p ~/.hermes/skills/lazyads
curl -fsSL https://raw.githubusercontent.com/camerondwills/lazyads-mcp/main/SKILL.md \
  -o ~/.hermes/skills/lazyads/SKILL.md
```

Hermes skill: [`SKILL.md`](./SKILL.md) in this repo, or the live guide at [lazyads.ai/hermes](https://lazyads.ai/hermes)

## What you get

- **BYOA:** 33 bridge tools to create, update, pause, and measure campaigns on all nine networks
- **Starter and above:** full suite (47 tools), including 14 Lazy Ads AI tools

Free accounts can onboard and browse competitor ads. AI tools require a paid plan with tokens. REST and outbound webhooks require Growth or above.

## Pricing

See [lazyads.ai/pricing](https://lazyads.ai/pricing). Plans: BYOA, Starter, Growth, Scale, Enterprise. Flat SaaS, bring your own ad accounts, no percent of spend.

## Links

- Site: https://lazyads.ai
- MCP docs: https://lazyads.ai/mcp
- Pricing: https://lazyads.ai/pricing
- Hermes: https://lazyads.ai/hermes
- Blog: https://lazyads.ai/blog

## License

Documentation in this repo is MIT. Lazy Ads the product remains a separate, private codebase.
