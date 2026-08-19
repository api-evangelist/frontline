---
name: max-integrations
description: Read your own Max connected integrations from the `max` CLI — the maxProfile-scoped accounts (Gmail, Outlook, Slack, HubSpot, Stripe, Google Workspace, etc.) that power Max chat, tasks, and playbooks. Read-only: list connection status / connected email / tool counts and get one integration's OAuth scopes + enabled tool slugs. Use to check what's connected and to discover the valid toolkit slugs for `--integrations` on `max tasks` / `max playbooks`. Connecting/disconnecting accounts and editing tool selection are done in the app, NOT here. NOT `frontline integrations` (those are account/Studio-scoped agent integrations).
allowed-tools: Bash(max:*)
---

# Max Integrations (your connected accounts)

Your Max agent acts through **your own** connected accounts (maxProfile-scoped) — distinct from the
account/Studio integrations that power customer-facing agents (`frontline integrations`). This command
is the read-only window into them.

Two commands:

```bash
max integrations list            # all your connected integrations + status
max integrations get <id>        # one integration (adds OAuth scopes + enabled tool slugs)
```

`<id>` is the numeric integration ID (the `id` from `list`).

## What you get

`list` returns, per integration:

| Field                                       | Meaning                                                            |
| ------------------------------------------- | ------------------------------------------------------------------ |
| `id`                                        | Numeric integration ID (use with `get`)                            |
| `toolkit`                                   | Toolkit slug — `gmail`, `outlook`, `slack`, `hubspot`, `stripe`, … |
| `isConnected`                               | Whether the account is currently connected                         |
| `isExpired`                                 | Whether the connection needs re-auth (reconnect in the app)        |
| `connectedEmail`                            | The connected email/account identifier (for Gmail/Outlook)         |
| `availableToolsCount` / `enabledToolsCount` | How many tools the toolkit exposes vs how many are enabled         |

`allowedToolSlugs` (enabled tool slugs) is included on both `list` and `get`. `get <id>` additionally
resolves `allowedScopes` (granted OAuth scopes) via a live lookup.

> `list` returns **every** account on your profile, including disconnected and expired ones. Only use
> a `toolkit` whose `isConnected` is `true` (and `isExpired` is `false`) — passing a disconnected
> toolkit as `--integrations` will silently fail at runtime.

## Primary use — discover valid `--integrations` values

`max tasks` and `max playbooks` scope which integrations they may use via a toolkit-slug array
(e.g. `--integrations '["gmail","hubspot"]'`). Those slugs are exactly the `toolkit` values of your
**connected** integrations. So before wiring a task/playbook:

```bash
# 1. See what's connected (and not expired)
max integrations list --pretty

# 2. Use the toolkit slugs in a task
max tasks create --name "Daily HubSpot digest" \
  --instructions "Summarize new HubSpot deals" \
  --cron "0 8 * * 1-5" \
  --integrations '["hubspot"]'
```

> `max tasks triggers` also lists `connectedToolkits`, but only surfaces toolkits that have **event
> triggers**. For the full set of connected accounts (including action-only toolkits like Stripe or
> HubSpot without a subscribed trigger), use `max integrations list`.

## Out of scope (do these in the app)

- **Connecting / disconnecting** an integration (OAuth — needs a browser).
- **Editing which tools are enabled** on an integration. Max discovers tools at runtime via its
  Integrations capability (SEARCH_TOOLS); per-tool selection is not exposed on the CLI by design.

## See also

- `max-tasks` skill — uses these toolkit slugs as `--integrations`.
- `max-playbooks` skill — same `--integrations` scoping for playbooks.
- `frontline integrations` (frontline CLI) — the **account/Studio** integrations for customer-facing
  agents. Different scope; not your personal Max accounts.
