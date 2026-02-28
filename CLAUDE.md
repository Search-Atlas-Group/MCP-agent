# Agentic Omnichannel Marketing MCP — Project Context

## What This Is

The **Agentic Omnichannel Marketing MCP** by [SearchAtlas](https://searchatlas.com) — the first programmable omnichannel marketing platform built on the Model Context Protocol. This repo contains playbooks, tool references, and execution guides for running end-to-end digital marketing campaigns across SEO, GEO (Generative Engine Optimization), Google Ads, local SEO, GMB optimization, AI search visibility, content generation, digital PR, and website creation — all through 112 MCP tools across 17 product namespaces.

## MCP Server

- **Endpoint:** `https://mcp.searchatlas.com/api/v1/mcp`
- **Protocol:** JSON-RPC 2.0, method `tools/call`
- **Auth Header:** `X-API-KEY`

## Key Files

| File | Purpose |
|------|---------|
| `AGENT_PLAYBOOK.md` | **Start here.** Golden rules, full 112-tool registry with schemas, verified workflows. |
| `summit-challenge-playbooks.json` | 15 ready-to-run agentic marketing playbook definitions from the AI Search & Agentic Marketing Summit challenge. |
| `README.md` | Project overview, omnichannel marketing tool categories, setup instructions. |
| `discover_tools.sh` | Batch tool discovery script — use to verify current tool names and schemas. |
| `EXECUTION_REPORT.md` | Historical log from 4 execution runs showing progression from 40% to 78% success rate. |

## How to Call a Tool

```bash
curl -s -X POST "https://mcp.searchatlas.com/api/v1/mcp" \
  -H "Content-Type: application/json" \
  -H "X-API-KEY: $MCP_API_KEY" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"<TOOL_NAME>","arguments":{"op":"<OPERATION>","params":{...}}}}'
```

## Golden Rules (Summary)

1. **Schema Discovery First** — Always send an empty call to discover the real schema. Documentation may have wrong parameter names.
2. **Read Error Messages** — Distinguish between param validation, auth blocks, and backend errors.
3. **Don't Fabricate Timelines** — Use actual API timestamps.
4. **Poll Async Tasks** — Many operations return a `task_id`. Poll until `SUCCESS`.
5. **Watch for Tool Name Collisions** — Multiple tools share short names. The MCP server routes to the first match.
6. **Never Invent Tool Names** — If `tools/list` doesn't show it, it doesn't exist.

See `AGENT_PLAYBOOK.md` for the complete golden rules with examples and the full tool registry.

## Tool Categories (112 Omnichannel Marketing Tools)

| Category | Tools | Key Operations |
|----------|-------|----------------|
| OTTO SEO | 15 | On-page optimization, audits, schema markup, knowledge graphs, instant indexing, wildfire internal linking |
| PPC / Google Ads | 13 | Business setup, campaign creation, ad groups, keyword clustering, bid management, performance tracking |
| Site Explorer | 8 | Organic keywords, backlinks, competitor analysis, keyword research, SERP features |
| Content Genius | 7 | AI article generation, topical authority maps, DKN, publication to 11+ CMS platforms |
| GBP (GMB Optimization) | 16 | Location management, automated posting, AI review responses, categories, services, attributes, media |
| Local SEO | 7 | Heatmap rank tracking, citation building, analytics, AI keyword recommendations |
| Press Release | 4 | AI content creation, Tier 1 publisher distribution, knowledge graphs |
| Cloud Stack | 4 | Authority backlinks across 14+ cloud providers |
| Digital PR | 4 | Publisher outreach campaigns, email templates, opportunity management |
| LinkLab | 4 | Guest post marketplace, editorial link building, publication discovery |
| LLM Visibility (GEO) | 8 | Brand visibility across AI models, sentiment tracking, citation monitoring, prompt simulation |
| Brand Vault | 1 | Brand identity, voice profiles, company intelligence |
| Website Studio | 1 | AI website generation and one-click publishing |
