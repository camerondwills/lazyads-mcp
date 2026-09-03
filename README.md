# Lazy Ads MCP

Public listing for the [Lazy Ads](https://lazyads.ai) MCP server.

Connect Claude, Cursor, Hermes, and any MCP-compatible client to your ad accounts across **nine networks**: Meta (Facebook + Instagram), Google, TikTok, LinkedIn, Reddit, Apple, Bing, ChatGPT, and Snapchat.

This repository is documentation only. It does not contain product source code.

## Hosted endpoint

- **URL:** `https://mcp.lazyads.ai/mcp`
- **Protocol:** MCP 2026-07-28 Streamable HTTP
- **Auth:** API key from Lazy Ads → Settings → API (any paid plan)

Docs: [lazyads.ai/mcp](https://lazyads.ai/mcp)

## Connect your client ([lazyads.ai/mcp#setup](https://lazyads.ai/mcp#setup))

Cursor (`.cursor/mcp.json`) and Claude Code (`.mcp.json`):

```json
{
  "mcpServers": {
    "lazyads": {
      "url": "https://mcp.lazyads.ai/mcp",
      "headers": { "Authorization": "Bearer la_your_api_key" }
    }
  }
}
```

Claude Code one-liner: `claude mcp add --transport http lazyads https://mcp.lazyads.ai/mcp --header "Authorization: Bearer la_your_api_key"`

Windsurf uses `serverUrl` instead of `url`. Gemini CLI uses `httpUrl`. VS Code uses `servers` with `"type": "http"`. Codex CLI reads `[mcp_servers.lazyads]` with `url` and `bearer_token_env_var = "LAZY_ADS_API_KEY"` from `~/.codex/config.toml`. Claude Desktop only launches local processes, so bridge it with `mcp-remote` and put the header in `env`. Copy-ready blocks for every client: https://lazyads.ai/mcp#setup

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

Free accounts can onboard and browse competitor ads. Lazy Ads AI tools require Starter or above. REST and outbound webhooks require Growth or above.

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
