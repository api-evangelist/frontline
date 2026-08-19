---
name: max-settings
description: View and change how your Max assistant behaves — timezone, scheduling links, language, personality, global instructions, per-mailbox email drafting/follow-ups/labels, agent status, and the knowledge-base toggle. Use whenever the user asks to see or tune a Max preference (e.g. "change my timezone", "make drafts more formal", "pause Max"). All commands are `max settings <section> get|update` on the `max` binary. Related but different surfaces: `max integrations` reads account connections; `frontline agents agent-setting` configures Studio agents, not Max.
allowed-tools: Bash(max:*)
---

# Max Settings (your agent's preferences)

Your personal Max preferences (maxProfile-scoped), split into five sections. Every section follows
the same `get` → edit → `update` loop: read the current shape, then send back only the fields you
want to change as a JSON object.

These commands exist **only on the `max` binary** — the `frontline` binary has no Max settings
surface (`frontline agents agent-setting` configures Studio agents, a different scope).

```bash
max settings scheduling     get | update --data '<json>'
max settings advanced       get | update --data '<json>'
max settings email          get <id> | update <id> --data '<json>'   # <id> = connectedAccountId
max settings overview       get | update --data '<json>'
max settings knowledge-base get | update --data '<json>'
```

> **Workflow:** always `get` first, then `update` with a partial object. Updates are merges — only the
> keys you include change. Each `update` returns the full, refreshed section so you can confirm.
> **Two exceptions** are full-replacement arrays: `schedulingLinks` and email `labels` (see below).

## Common intents (first-turn routing)

| User says                                  | Section          | Example                                                                     |
| ------------------------------------------ | ---------------- | --------------------------------------------------------------------------- |
| timezone, city/region for scheduling       | `scheduling`     | `max settings scheduling update --data '{"timezone":"America/Sao_Paulo"}'`  |
| personality, language, global instructions | `advanced`       | `max settings advanced update --data '{"personality":"PROFESSIONAL"}'`      |
| email drafts, follow-ups, labels           | `email <id>`     | `max settings email get <id>` first; id from `max integrations list`        |
| pause/resume Max agent                     | `overview`       | `max settings overview update --data '{"status":"ACTIVE"}'`                 |
| use knowledge bases                        | `knowledge-base` | `max settings knowledge-base update --data '{"knowledgeBaseEnabled":true}'` |

Use **IANA** timezone ids (`America/Sao_Paulo`, not `"sao paulo"`). `overview get` also shows
`timezone` read-only — to **change** it, use `scheduling update`.

## Sections

### `scheduling`

| Field                    | Type           | Notes                                        |
| ------------------------ | -------------- | -------------------------------------------- |
| `schedulingEnabled`      | boolean        | Master toggle for scheduling                 |
| `schedulingInstructions` | string \| null | Free-text guidance (max 2000 chars)          |
| `timezone`               | string         | IANA tz, e.g. `America/New_York`             |
| `schedulingLinks`        | array (max 5)  | `{ link, description?, isActive? }` per item |

`schedulingLinks` is a **full replacement** of the list: include the `id` of links you keep, omit a
link to delete it, leave `id` off to create a new one. Changing `timezone` also re-times all of your
Max periodic tasks.

```bash
max settings scheduling update --data '{"timezone":"America/New_York","schedulingLinks":[{"link":"https://cal.com/me","description":"30-min intro"}]}'
```

### `advanced`

| Field               | Type           | Notes                                          |
| ------------------- | -------------- | ---------------------------------------------- |
| `preferredLanguage` | enum           | e.g. `ENGLISH` (run `get` to see current)      |
| `instructions`      | string \| null | Global persona/behavior guidance (max 2000)    |
| `personality`       | enum           | e.g. `PROFESSIONAL` (run `get` to see options) |

```bash
max settings advanced update --data '{"instructions":"Be concise and proactive.","personality":"PROFESSIONAL"}'
```

### `email <connectedAccountId>`

Per-mailbox settings for a **Gmail/Outlook** integration. Get the `connectedAccountId` from
`max integrations list` (the `id` of a `gmail`/`outlook` integration).

Key fields (run `get` for the full shape):

- **Categorization:** `categorizationEnabled`, `categorizationInstructions`, `toRespondSensitivity`, `marketingSensitivity`, `labels[]`
- **Drafting:** `draftEnabled`, `draftInstructions`, `customSignature` (`writingStyle` is read-only)
- **Follow-up:** `followupEnabled`, `followUpInstructions`, `followUpAfter` (1–30 days)
- **Processing / people-sync:** `emailProcessingEnabled`, `contactSyncEnabled`, `autoCreateContactsModeOverride`, `linkMaxContactToPeopleOverride`, `peopleSyncDefaultOverride`

```bash
max settings email get 42 --pretty
max settings email update 42 --data '{"draftEnabled":true,"draftInstructions":"Match my tone","followUpAfter":3}'
```

> **Dependency:** `draftEnabled` and `followupEnabled` require `categorizationEnabled: true` — drafts
> and follow-ups are driven by the labels categorization applies. Enabling either while categorization
> is off is rejected with a 400.
>
> **`labels` is a FULL REPLACEMENT — do NOT send it unless you mean to rewrite the whole list.** Any
> existing label whose `id` you omit gets deleted (and omitting a SYSTEM label is a 400). To edit
> labels: `get` first, send back **every** label (with its `id`) plus your changes; each item needs
> the full shape (`name`, `description`, `color`, `isActive`, `moveToFolder`, `generateAutoDraft`,
> `ingestEmail`). Omit the `labels` key entirely when updating other email fields.
>
> People-sync overrides (`autoCreateContactsModeOverride`, `linkMaxContactToPeopleOverride`,
> `peopleSyncDefaultOverride`) require an **OWNER/ADMIN** role.

### `overview`

Read-mostly. `get` returns agent `status`, `phoneNumber`, `enabled`, free-trial info, `maxSeat` /
billing plan, a `connectedAccounts` summary (gmail, googleCalendar, outlook, slack), `availableTools`,
and `timezone`. **`update` only changes `status`.**

```bash
max settings overview get --pretty
max settings overview update --data '{"status":"ACTIVE"}'
```

### `knowledge-base`

Single toggle, `knowledgeBaseEnabled`, controlling whether Max consults knowledge bases at all.

```bash
max settings knowledge-base update --data '{"knowledgeBaseEnabled":true}'
```

> This only flips the toggle. Every user's Max has a **private KB that can't be deleted**, and users
> can **assign shared KBs** — but KB content and assignment live in the app, NOT on this command.

## Out of scope (do these elsewhere)

- **Connecting / disconnecting** integrations → app (read status via `max integrations`).
- **Creating / editing knowledge-base content** → app.
- **Studio agent configuration** → `frontline agents agent-setting` (account-scoped agents, not your Max).

## See also

- `max-integrations` skill — find the `connectedAccountId` for `max settings email`.
- `max-tasks` / `max-playbooks` skills — automations that run under these settings.
