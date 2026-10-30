# Frontline

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Frontline is an AI-native CRM platform that builds and maintains itself. It unifies customer context from WhatsApp, email, and meetings, ships AI agents (Max) that draft replies, proposals, follow-ups and meeting notes, and a Studio for building an AI workforce for sales and support. The Frontline Public API exposes agents, agent-builder flows, automation workflows, CRM objects and rows, tables, tools, intents, AI models, incoming webhooks, account, and billing over REST at https://prod-api.getfrontline.ai/public/v1, authenticated with GENERAL (account) and USER Bearer API keys. Backed by 500 Global.

**Areas:** Company · CRM · AI Agents · Sales Automation · Customer Service · Workflows · Conversational AI

## Frontline on APIs.io

Everything profiled for Frontline is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/frontline/](https://apis.io/providers/frontline/)** — or go straight to one of the APIs or properties below.

### APIs (43)

- [Frontline Account API](https://apis.io/apis/frontline/frontline-account-api/) — Inspect the identity attached to the current API key
- [Frontline Agent Builder API](https://apis.io/apis/frontline/frontline-agent-builder-api/) — View and manage your AI agents across your account
- [Frontline Agents API](https://apis.io/apis/frontline/frontline-agents-api/) — Agent runtime data: conversations and transcripts
- [Frontline AI Models API](https://apis.io/apis/frontline/frontline-ai-models-api/) — Discover available AI models for agent configuration
- [Frontline Billing API](https://apis.io/apis/frontline/frontline-billing-api/) — View billing plan details, credits, and renewal information
- [Frontline Flow Variables API](https://apis.io/apis/frontline/frontline-flow-variables-api/) — Manage variables scoped to an agent's flow
- [Frontline Flows API](https://apis.io/apis/frontline/frontline-flows-api/) — View and manage flows associated with your agents
- [Frontline Incoming Webhooks API](https://apis.io/apis/frontline/frontline-incoming-webhooks-api/) — Inbound HTTPS endpoints that external systems can post events to
- [Frontline Intents API](https://apis.io/apis/frontline/frontline-intents-api/) — Manage agent intents and training phrases
- [Frontline Object activities API](https://apis.io/apis/frontline/frontline-object-activities-api/) — Manual activities (notes, calls, meetings, emails) attached to object rows
- [Frontline Object aggregations API](https://apis.io/apis/frontline/frontline-object-aggregations-api/) — Per-view aggregations on objects
- [Frontline Object export API](https://apis.io/apis/frontline/frontline-object-export-api/) — Export object data as XLSX or CSV
- [Frontline Object fields API](https://apis.io/apis/frontline/frontline-object-fields-api/) — Manage columns on an object
- [Frontline Object files API](https://apis.io/apis/frontline/frontline-object-files-api/) — Files attached to object rows
- [Frontline Object options API](https://apis.io/apis/frontline/frontline-object-options-api/) — Manage tag/select options on object fields
- [Frontline Object record types API](https://apis.io/apis/frontline/frontline-object-record-types-api/) — Categorize records inside an object
- [Frontline Object relations API](https://apis.io/apis/frontline/frontline-object-relations-api/) — Link and unlink records across objects
- [Frontline Object rows API](https://apis.io/apis/frontline/frontline-object-rows-api/) — Read and write object records
- [Frontline Object tasks API](https://apis.io/apis/frontline/frontline-object-tasks-api/) — Tasks attached to object rows
- [Frontline Object views API](https://apis.io/apis/frontline/frontline-object-views-api/) — Saved view configurations on an object
- [Frontline Objects API](https://apis.io/apis/frontline/frontline-objects-api/) — Manage CRM objects (standard and custom)
- [Frontline Table activities API](https://apis.io/apis/frontline/frontline-table-activities-api/) — Manual activities (notes, calls, meetings, emails) attached to table rows
- [Frontline Table aggregations API](https://apis.io/apis/frontline/frontline-table-aggregations-api/) — Per-view aggregations on tables
- [Frontline Table export API](https://apis.io/apis/frontline/frontline-table-export-api/) — Export table data as XLSX or CSV
- [Frontline Table fields API](https://apis.io/apis/frontline/frontline-table-fields-api/) — Manage columns on a table
- [Frontline Table files API](https://apis.io/apis/frontline/frontline-table-files-api/) — Files attached to table rows
- [Frontline Table options API](https://apis.io/apis/frontline/frontline-table-options-api/) — Manage tag/select options on table fields
- [Frontline Table rows API](https://apis.io/apis/frontline/frontline-table-rows-api/) — Read and write table rows
- [Frontline Table tasks API](https://apis.io/apis/frontline/frontline-table-tasks-api/) — Tasks attached to table rows
- [Frontline Tables API](https://apis.io/apis/frontline/frontline-tables-api/) — Manage spreadsheet-style tables
- [Frontline Workflow Variables API](https://apis.io/apis/frontline/frontline-workflow-variables-api/) — Manage variables scoped to an automation workflow
- [Frontline Workflows API](https://apis.io/apis/frontline/frontline-workflows-api/) — View and manage your workflows across your account
- [Frontline Account Integrations API](https://apis.io/apis/frontline/frontline-account-integrations-api/) — View account-scoped (Studio) connected integrations, discover connectable toolkits, and configure which tools each integration exposes to agents, flows, and…
- [Frontline Agent Channels API](https://apis.io/apis/frontline/frontline-agent-channels-api/) — View connected channel integrations (WhatsApp, Instagram, Messenger) and bind numbers/accounts/pages to agents
- [Frontline Agent Playbooks API](https://apis.io/apis/frontline/frontline-agent-playbooks-api/) — Manage reusable instruction sets assigned to agents
- [Frontline Channels API](https://apis.io/apis/frontline/frontline-channels-api/) — Communication channels connected to this account (WhatsApp, Instagram, Messenger)
- [Frontline Custom Tools API](https://apis.io/apis/frontline/frontline-custom-tools-api/) — Manage custom tools — reusable HTTP/API-call integrations the account creates and assigns to agents, flows, and workflows. Distinct from built-in system…
- [Frontline Guidance API](https://apis.io/apis/frontline/frontline-guidance-api/) — Builder reference data sourced live from backend constants: valid icons, colors, and formats for objects/tables/fields, plus the workflow/flow node-type…
- [Frontline Integration Resources API](https://apis.io/apis/frontline/frontline-integration-resources-api/) — Resolve resource IDs (spreadsheets, docs, drive folders, Asana projects, Salesforce SObjects, Gmail labels, Outlook folders/calendars) needed to configure…
- [Frontline Integrations API](https://apis.io/apis/frontline/frontline-integrations-api/) — OAuth/API connected accounts for toolkits like Google Sheets, Gmail, and Slack
- [Frontline Knowledge Bases API](https://apis.io/apis/frontline/frontline-knowledge-bases-api/) — Manage knowledge bases, their sources (URLs, website crawls), search, and agent assignment
- [Frontline User Tasks API](https://apis.io/apis/frontline/frontline-user-tasks-api/) — User tasks — the account 'To-dos' inbox: create, list, update, complete, and delete tasks, optionally linked to an object record. Distinct from object-row…
- [Frontline Users API](https://apis.io/apis/frontline/frontline-users-api/) — List account users to resolve IDs for relations and assignment

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [frontline](https://apis.io/servers/frontline/frontline/)

#### Agent skills (41)

Agent skills built on the API.

- [agent-builder](https://apis.io/agent-skills/frontline/agent-builder/)
- [agent-channels](https://apis.io/agent-skills/frontline/agent-channels/)
- [agent-playbooks](https://apis.io/agent-skills/frontline/agent-playbooks/)
- [agents-chat](https://apis.io/agent-skills/frontline/agents-chat/)
- [aggregations](https://apis.io/agent-skills/frontline/aggregations/)
- [ai-models](https://apis.io/agent-skills/frontline/ai-models/)
- [auth-and-profiles](https://apis.io/agent-skills/frontline/auth-and-profiles/)
- [crm-objects](https://apis.io/agent-skills/frontline/crm-objects/)
- [crm-setup](https://apis.io/agent-skills/frontline/crm-setup/)
- [crud-operations](https://apis.io/agent-skills/frontline/crud-operations/)
- [custom-tools](https://apis.io/agent-skills/frontline/custom-tools/)
- [export-and-delete](https://apis.io/agent-skills/frontline/export-and-delete/)
- [files](https://apis.io/agent-skills/frontline/files/)
- [filter-and-query](https://apis.io/agent-skills/frontline/filter-and-query/)
- [flow-builder](https://apis.io/agent-skills/frontline/flow-builder/)
- [formulas](https://apis.io/agent-skills/frontline/formulas/)
- [frontline-agents](https://apis.io/agent-skills/frontline/frontline-agents/)
- [frontline-api](https://apis.io/agent-skills/frontline/frontline-api/)
- [frontline-billing](https://apis.io/agent-skills/frontline/frontline-billing/)
- [frontline-docs](https://apis.io/agent-skills/frontline/frontline-docs/)
- [frontline-internals](https://apis.io/agent-skills/frontline/frontline-internals/)
- [frontline-workflows](https://apis.io/agent-skills/frontline/frontline-workflows/)
- [incoming-webhooks](https://apis.io/agent-skills/frontline/incoming-webhooks/)
- [integrations](https://apis.io/agent-skills/frontline/integrations/)
- [knowledge-bases](https://apis.io/agent-skills/frontline/knowledge-bases/)
- …and 16 more published on APIs.io

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Frontline Agentic Access](https://apis.io/agentic-access/frontline/frontline-agentic-access/)

#### Collections (33)

Postman and Open Collection request collections.

- [Public Account API](https://apis.io/collections/frontline/open-frontline-account-api/)
- [Public Account Agent Builder API](https://apis.io/collections/frontline/open-frontline-agent-builder-api/)
- [Public Account Agents API](https://apis.io/collections/frontline/open-frontline-agents-api/)
- [Public Account AI Models API](https://apis.io/collections/frontline/open-frontline-ai-models-api/)
- [Public Account Billing API](https://apis.io/collections/frontline/open-frontline-billing-api/)
- [Public Account Flow Variables API](https://apis.io/collections/frontline/open-frontline-flow-variables-api/)
- [Public Account Flows API](https://apis.io/collections/frontline/open-frontline-flows-api/)
- [Public Account Incoming Webhooks API](https://apis.io/collections/frontline/open-frontline-incoming-webhooks-api/)
- [Public Account Intents API](https://apis.io/collections/frontline/open-frontline-intents-api/)
- [Public Account Object activities API](https://apis.io/collections/frontline/open-frontline-object-activities-api/)
- [Public Account Object aggregations API](https://apis.io/collections/frontline/open-frontline-object-aggregations-api/)
- [Public Account Object export API](https://apis.io/collections/frontline/open-frontline-object-export-api/)
- [Public Account Object fields API](https://apis.io/collections/frontline/open-frontline-object-fields-api/)
- [Public Account Object files API](https://apis.io/collections/frontline/open-frontline-object-files-api/)
- [Public Account Object options API](https://apis.io/collections/frontline/open-frontline-object-options-api/)
- [Public Account Object record types API](https://apis.io/collections/frontline/open-frontline-object-record-types-api/)
- [Public Account Object relations API](https://apis.io/collections/frontline/open-frontline-object-relations-api/)
- [Public Account Object rows API](https://apis.io/collections/frontline/open-frontline-object-rows-api/)
- [Public Account Object tasks API](https://apis.io/collections/frontline/open-frontline-object-tasks-api/)
- [Public Account Object views API](https://apis.io/collections/frontline/open-frontline-object-views-api/)
- [Public Account Objects API](https://apis.io/collections/frontline/open-frontline-objects-api/)
- [Public Account Table activities API](https://apis.io/collections/frontline/open-frontline-table-activities-api/)
- [Public Account Table aggregations API](https://apis.io/collections/frontline/open-frontline-table-aggregations-api/)
- [Public Account Table export API](https://apis.io/collections/frontline/open-frontline-table-export-api/)
- [Public Account Table fields API](https://apis.io/collections/frontline/open-frontline-table-fields-api/)
- …and 8 more published on APIs.io

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Frontline Overlay](https://apis.io/overlays/frontline/frontline-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Frontline Authentication](https://apis.io/security/frontline/frontline-authentication/)
- [Frontline Domain Security](https://apis.io/security/frontline/frontline-domain-security/)
- [Frontline Trust Center](https://apis.io/security/frontline/frontline-trust-center/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Frontline Plans Pricing](https://apis.io/plans/frontline/frontline-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Frontline Rate Limits](https://apis.io/rate-limits/frontline/frontline-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://getfrontline.ai)
- [Documentation](https://docs.getfrontline.ai/)
- [Getting started](https://docs.getfrontline.ai/docs/getting-started)
- [API reference](https://frontline-public-api.redocly.app/)
- [Pricing](https://www.getfrontline.ai/pricing)
- [Sign up](https://app.getfrontline.ai)
- [Support](https://help.getfrontline.ai/)
- [Blog](https://www.getfrontline.ai/blog)
- [Compliance](https://trust.getfrontline.ai/)
- [Terms of service](https://www.getfrontline.ai/terms-of-service)
- [Privacy policy](https://www.getfrontline.ai/privacy-policy)

## API Evangelist rating

**Kin Score 48.2** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 51.3 |
| Contract governance | 4.5 |
| Operational transparency | 21.1 |
| Developer ergonomics | 71.4 |
| Access clarity | 47.4 |

**Agent readiness 32.0** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 29.4** — AI & Biometrics

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/frontline/](https://apis.io/providers/frontline/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Frontline: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/frontline/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
