---
name: Build and deploy a Frontline AI agent
description: Create an AI agent, configure its model/settings/theme, and deploy it live.
api: openapi/frontline-openapi-original.yml
operations: [listAiModels, createAgent, getAgent, updateAgentSetting, updateAgentTheme, updateAgentDeploymentStatus]
generated: '2026-07-19'
method: generated
---

# Build and deploy a Frontline AI agent

Base URL `https://prod-api.getfrontline.ai`, all paths under `/public/v1`.
Authenticate every request with `Authorization: Bearer <API_KEY>`. Creating and
deploying agents are write operations, so use a **USER** key (a GENERAL key is
read/analytics only). Verify the key first with `getMe` (`GET /public/v1/me`).

## Steps

1. **Pick a model** — call `listAiModels` (`GET /public/v1/ai-models`) to get the
   available `aiModelId`s. `getDefaultAiModel` returns the account default.
2. **Create the agent** — `createAgent` (`POST /public/v1/agents`) with the agent
   name and the chosen `aiModelId`. Capture the returned agent `id`.
3. **Configure settings** — `updateAgentSetting` (`PATCH`/`PUT` on the agent
   setting) to set behavior; `updateAgentTheme` to brand the live-chat surface.
4. **Confirm** — `getAgent` (`GET /public/v1/agents/{agentId}`) to read back the
   full configuration.
5. **Deploy** — `updateAgentDeploymentStatus` to take the agent live on its
   channels.

## Rules

- Branch on `error.code` (`unauthorized`, `not_found`, `conflict`, `bad_request`),
  not on `error.message`. Validation errors carry `error.details.issues[]`.
- A `409 conflict` on create usually means a duplicate agent name.
- Respect the 1,000 req / 60s per-account rate limit; back off on `429`.
- No idempotency key exists — do not blindly retry a `POST` that may have
  succeeded; re-list to check before recreating.
