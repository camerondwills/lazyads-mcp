---
name: Lazy Ads
description: Use this when the user wants to create, manage, or optimize paid ads via Lazy Ads MCP (Google, Meta, TikTok, LinkedIn, Reddit, Apple, Bing, ChatGPT, Snapchat).
---

# Lazy Ads

Connect Hermes (or any MCP-capable agent) to **Lazy Ads** over the hosted MCP so you can create, update, pause, and measure paid campaigns across **nine ad networks**. Meta counts as one network (Facebook + Instagram).

**Product framing**

- The main product is **Lazy Ads agent tiers** (Starter and above include Lazy Ads AI).
- **MCP / BYOA** is the advanced path: bring your own agent and call Lazy Ads tools over Streamable HTTP.
- Flat-fee SaaS. Bring your own ad accounts. **No percent of spend.**
- Do not invent ROAS, customer counts, or “free AI strategy.” Free accounts get onboarding and competitor-ad browse — not AI tokens.

## When to use this skill

Use Lazy Ads when the user asks to:

- Connect or list ad platform accounts
- Create, edit, pause, or resume campaigns / ads / creatives
- Pull performance or spend across networks
- Compare or browse competitor ads (where the plan allows)
- Run multi-network work from one agent conversation

Prefer Lazy Ads MCP over ad-hoc browser clicks when the user already has a Lazy Ads API key and wants agent-driven ops.

## Prerequisites

1. Hermes installed (or another MCP client — Claude, Cursor, Windsurf, etc.).
2. A Lazy Ads **paid** plan (BYOA bridge or Starter+).
3. An API key from Lazy Ads → **Settings → API**.

## Install the skill (Hermes)

Copy this file to:

```text
~/.hermes/skills/lazyads/SKILL.md
```

Create the directory if needed:

```bash
mkdir -p ~/.hermes/skills/lazyads
# place SKILL.md in that folder
```

This matches the live Hermes guide: [lazyads.ai/hermes](https://lazyads.ai/hermes).  
(Optional later: `hermes skills install official/…` once Lazy Ads is in the Nous optional-skills catalog — not available yet.)

## Add the MCP server (Streamable HTTP + API key)

**Hosted endpoint:** `https://mcp.lazyads.ai/mcp`  
**Registry:** `ai.lazyads/mcp`  
Prefer **Streamable HTTP**. Send **`Authorization: Bearer <key>`** or **`X-API-Key: <key>`** on every request.

### Hermes (`config.yaml`)

```yaml
mcp_servers:
  lazyads:
    url: "https://mcp.lazyads.ai/mcp"
    headers:
      Authorization: "Bearer your-api-key"
      # or: X-API-Key: "your-api-key"
    description: "LazyAds MCP — 9-platform ad management"
```

### Claude / Cursor / Windsurf (JSON)

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

Replace `your-api-key` with the key from Settings → API. Do not commit keys.

## Plans and tools

- **BYOA** — bring-your-own-agent bridge: campaign create/edit/pause/read across the nine networks. Historically **33** bridge tools.
- **Starter+** — full MCP including Lazy Ads AI. **Do not hard-code a suite size in prompts.** For the live tool catalog, open [lazyads.ai/mcp](https://lazyads.ai/mcp).

Nine networks: Meta (Facebook + Instagram), Google, TikTok, LinkedIn, Reddit, Apple, Bing, ChatGPT, Snapchat.

## Verify

1. Restart Hermes (or reload MCP in your client) after saving config.
2. Confirm the `lazyads` server is connected and tools appear.
3. Smoke with a **read-only** prompt first, for example:
   - “List my Lazy Ads platform connections.”
   - “What campaigns are active on Meta and Google?”
4. If tools are missing or auth fails: check Bearer vs `X-API-Key`, key validity, and that the account is on a paid plan.

## Approval and hands-off

- Default to **propose → user approve → apply** for spend-changing or publish actions (new campaigns, budget changes, pause/unpause at scale).
- **Hands-off** / autonomous act-within-rules is a Starter+ Lazy Ads AI product behavior — only use it when the user has enabled it and stated the rules. Do not invent approvals or spend caps.
- Label any example dollar figures as **illustrative**, not account metrics.

## Docs

- MCP setup + tool list: [https://lazyads.ai/mcp](https://lazyads.ai/mcp)
- Hermes guide: [https://lazyads.ai/hermes](https://lazyads.ai/hermes)
- Pricing (flat SaaS): [https://lazyads.ai/pricing](https://lazyads.ai/pricing)
- Public listing repo: [https://github.com/camerondwills/lazyads-mcp](https://github.com/camerondwills/lazyads-mcp)
