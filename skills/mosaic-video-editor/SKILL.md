---
name: mosaic-video-editor
description: AI-powered video editing via the Mosaic API. Create agents, run video workflows, manage social accounts, publish content, upload assets, and handle credits. Use when the user wants to edit videos, run agents, post to social media, or manage their Mosaic account programmatically.
metadata: {"openclaw":{"requires":{"env":["MOSAIC_API_KEY"]},"primaryEnv":"MOSAIC_API_KEY"}}
---

# Mosaic API Skill

With Mosaic you are an AI video editor. You create and run video editing workflows ("Agents"), upload media, connect social accounts, and publish edited videos automatically.

## Source of truth

Use this skill as an orientation and workflow guide, not as the canonical API schema.

- Before constructing request bodies, query parameters, or response parsing logic, check the live docs at [docs.mosaic.so](https://docs.mosaic.so/api/introduction).
- For endpoint details, follow the links in [references/docs-endpoints.md](references/docs-endpoints.md) and prefer the docs page over examples in this skill.
- For node parameters, call `GET /node_type/{node_type_id}` or read the linked tile docs before writing `update_params`.
- If this skill conflicts with `docs.mosaic.so` or the API response, trust the docs/API response.
- Do not infer private account, profile, billing, or social connection details from examples in this skill. Ask the API or the user.

## API key setup

Before any API call, you need a Mosaic API key (prefixed `mk_`).

1. **Check the environment first.** If `MOSAIC_API_KEY` is already set (e.g. via the one-click setup at [edit.mosaic.so](https://edit.mosaic.so)), use it directly.
2. If the key is not in the environment, ask the user for it. Direct them to [edit.mosaic.so/automations?tab=api](https://edit.mosaic.so/automations?tab=api) to generate one using the one-click setup for OpenClaw or Claude Code.
3. Store the key as `MOSAIC_API_KEY` in your environment for future sessions.
4. Validate with `GET https://api.mosaic.so/whoami` using header `Authorization: Bearer $MOSAIC_API_KEY`.

## HTTP conventions

- **Base URL:** `https://api.mosaic.so`
- **Auth:** `Authorization: Bearer $MOSAIC_API_KEY`
- **Content:** `Content-Type: application/json`

## Workflows

Each workflow has its own guide. Read the relevant file for the task at hand.

| Task | Guide |
|------|-------|
| Create and manage agents | [workflows/managing-agents.md](workflows/managing-agents.md) |
| Run an agent on video | [workflows/running-agents.md](workflows/running-agents.md) |
| Upload video/audio/image assets | [workflows/uploading-assets.md](workflows/uploading-assets.md) |
| Publish to social platforms | [workflows/social-publishing.md](workflows/social-publishing.md) |
| Credits, billing, and auto top-ups | [workflows/credits-and-billing.md](workflows/credits-and-billing.md) |

## Nodes (tiles)

Agents are graphs of **nodes** (also called "tiles"). Each node performs one editing action. To discover available nodes and their parameters, call:

```
GET /node_types          — list all node types
GET /node_type/{node_type_id} — get details for a specific node
```

Per-node reference files with IDs and docs links are in the [nodes/](nodes/) directory. Read the relevant node file when you need parameter details for `update_params`.

## Editing best practices

- For tighter edits, place **Rough Cut** or **Clips** before style nodes.
- Place **Reframe** before layout-sensitive nodes (Captions, Cinematic Captions, Motion Graphics, Watermark).
- Chain edits by passing prior `node_render_ids` to subsequent runs.

## Guardrails

- `update_params` keys must match `agent_node_id` values from `GET /agent/{agent_id}`.
- Invalid overrides return `400`.
- Do not rely on remembered parameter names. Fetch node details with `GET /node_type/{node_type_id}` before sending `update_params`.
- If a run is credit-blocked (`needs_credits: true` or `needsCredits: true`), follow the required plan-check and upgrade flow in [workflows/credits-and-billing.md](workflows/credits-and-billing.md) before attempting resume.
- For credits, billing, plans, and social publishing, verify the current endpoint docs before acting because those public APIs change more frequently.

## Endpoint map

Full endpoint reference: [references/docs-endpoints.md](references/docs-endpoints.md)
