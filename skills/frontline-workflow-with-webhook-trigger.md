---
name: Build a Frontline workflow triggered by an incoming webhook
description: Create an inbound webhook, then build an automation workflow that reacts to it.
api: openapi/frontline-openapi-original.yml
operations: [createIncomingWebhook, createWorkflow, getWorkflowGraph, createWorkflowNode, createWorkflowEdge, getWorkflowAnalytics]
generated: '2026-07-19'
method: generated
---

# Build a Frontline workflow triggered by an incoming webhook

Base URL `https://prod-api.getfrontline.ai/public/v1`. Use a **USER** key for
these writes.

## Steps

1. **Create the inbound webhook** — `createIncomingWebhook`
   (`POST /public/v1/incoming-webhooks`) with a name. With
   `useAuthentication: true` (recommended) Frontline returns a 64-character
   `accessToken` **only on this create response** — store it now; external
   callers POST to the generated `url` with `Authorization: Bearer <accessToken>`.
2. **Create the workflow** — `createWorkflow` (`POST /public/v1/workflows`).
   Capture the workflow `id`.
3. **Add a WEBHOOK trigger node** — `createWorkflowNode` referencing the incoming
   webhook, then further action nodes.
4. **Wire the graph** — `createWorkflowEdge` to connect trigger → action nodes;
   read it back with `getWorkflowGraph`.
5. **Observe** — `getWorkflowAnalytics` for run counts and outcomes.

## Rules

- Incoming webhooks are **inbound only** — Frontline does not push outbound events;
  do not design around outbound delivery.
- Node creation validates every reference up front: a bad `aiModelId`,
  `customToolIds[]`, `tableId`, etc. returns `400 bad_request` with each offending
  reference in `error.details.issues[]` (`code: not_found` / `wrong_kind` /
  `wrong_owner`) and persists nothing.
- Losing the webhook `accessToken` means rotating the webhook — it is never shown
  again.
