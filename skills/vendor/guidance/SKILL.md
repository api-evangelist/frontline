---
name: guidance
description: Fetch authoritative builder reference data from the live backend using the `frontline guidance` CLI — valid icon keys/icon colors/select-option colors (`frontline guidance icons`), the field-type & metadata reference (`frontline guidance fields`), the workflow/flow node-type catalog (`frontline guidance nodes`), and per-node configuration guidance (`frontline guidance node <type>`). Use this whenever you need a current allowlist or reference instead of a hard-coded one: before setting an `emoji`/`icon_color`, choosing option colors, picking a field type/metadata, or building/configuring a flow/workflow graph. Values come straight from backend constants and editable prompts, so they never drift from what the API will accept.
allowed-tools: Bash(frontline:*)
---

# Builder guidance (live reference data)

`frontline guidance` returns reference data sourced directly from the backend, so the values are
always exactly what create/update calls will accept. Prefer these over any list pasted into a
skill or your own memory — those drift; this does not.

Four commands:

| Command                       | Returns                                                                                    |
| ----------------------------- | ------------------------------------------------------------------------------------------ |
| `frontline guidance icons`    | `iconKeys`, `iconColors`, `optionColors`, `tagModes`, `relationModes`                      |
| `frontline guidance fields`   | Markdown reference for every field/column type, its metadata shape, and best practices     |
| `frontline guidance nodes`    | Every node `type` with `validInFlow`, `validInAutomation`, `allowsMultipleOutgoingHandles` |
| `frontline guidance node <t>` | Markdown guidance for configuring one node type (e.g. `TOOLS_AI`, `API`)                   |

JSON is the default output. Add `--table` for a human-readable view — for `fields` and
`node <type>` this prints the raw markdown instead of a JSON-wrapped string. Any valid API key works.

## Icons & colors — `frontline guidance icons`

```bash
$ frontline guidance icons
```

Returns, for example:

```json
{
    "iconKeys": ["home", "users", "briefcase", "ticket", "rocket", "..."],
    "iconColors": [
        { "name": "blue", "value": "#60a5fa" },
        { "name": "emerald", "value": "#34d399" }
    ],
    "optionColors": [
        { "name": "Sky", "value": "#339AFF" },
        { "name": "Emerald", "value": "#00DC71" }
    ],
    "tagModes": ["singleSelect", "multiSelect"],
    "relationModes": ["single", "multi"]
}
```

How to use the fields:

- **`iconKeys`** → the `emoji` field on **objects** and **record types** (e.g. `"emoji": "briefcase"`).
  Tables (`frontline table create`) take a **literal Unicode emoji** instead (e.g. `"📁"`), not a key.
- **`iconColors`** → the `icon_color` field on objects/record-types/fields. Pass the `name`
  (case-insensitive, e.g. `"blue"`) or the hex `value`.
- **`optionColors`** → the `color` on a tag/select option. This is a **different palette** from
  `iconColors` — don't mix them up.
- **`tagModes` / `relationModes`** → the `metadata.mode` for tag (single/multi select) and relation fields.

## Field types — `frontline guidance fields`

```bash
$ frontline guidance fields --table   # prints the markdown reference directly
```

Returns a markdown reference covering every creatable field type (`string`, `number`, `boolean`,
`date`, `dateOnly`, `select` (alias for `tags`), `relation`), the exact `metadata` shape each
accepts (formats, currency, decimals, modes, related-table ids), end-user-wording → type mappings,
and best practices. Read this **before** a `field create`/`field update` so you pick a valid
`type` + `metadata` and avoid a 400.

Worth calling out (the full reference has more):

- **Short text vs long text** — both are `type: "string"`. Use plain string (single-line) for names,
  titles, and short labels; add `metadata.extendedField: true` (multi-line text area) for
  descriptions, notes, summaries, issues — anything longer than a name/address/phone/email.
- **Currency** — `metadata.currency` is an ISO 4217 code (default `USD`). It isn't enforced
  server-side, but `frontline guidance fields` lists the common codes to pick from (`USD`, `EUR`,
  `GBP`, `MXN`, `BRL`, …) — use one of those rather than inventing a code.
- **Date display** — `metadata.format` on date/dateOnly is a date-fns pattern (`MM/dd/yyyy`,
  `yyyy-MM-dd`, …, or `timeDelta` for relative display); `metadata.timeFormat` is `"12"` or `"24"`;
  `timezone` is required whenever `metadata` is passed on a `date` field.
- **Constraints** — `required`/`unique` are top-level booleans; some types can't take them
  (e.g. boolean can't be required; file/tags/boolean can't be unique) — the reference lists the rules.
- Select/tag options are created in a **separate step**, never inline in the field body.

## Node types — `frontline guidance nodes`

```bash
$ frontline guidance nodes --table
```

Use this before adding nodes to a flow or workflow: it tells you which node types are valid in a
**flow** (agent) vs an **automation** workflow, and which may have more than one outgoing edge.

- `validInFlow: false` → adding that node to a flow returns a 400 (e.g. `DYNAMIC_TABLES` is
  automation-only).
- `allowsMultipleOutgoingHandles: true` → the node may branch to multiple edges
  (e.g. `CONDITIONAL_ROUTING`, `TOOLS_AI`, `API`); all others allow only one.

## Per-node guidance — `frontline guidance node <type>`

```bash
$ frontline guidance node TOOLS_AI --table   # prints the markdown guidance directly
```

Returns prose guidance for configuring a single node type. Use it after `frontline guidance nodes`
tells you a type is valid, to learn how to fill that node's fields. Guidance is published per node
type and editable without a deploy; it returns empty when none is published for that type.

## When to reach for this

- About to set an icon or color and unsure of the exact key/name → `frontline guidance icons`.
- Choosing a select-option color → `optionColors` (not `iconColors`).
- Picking a field `type`/`metadata` for a `field create` → `frontline guidance fields`.
- Building a graph and unsure whether a node type belongs in a flow or an automation → `frontline guidance nodes`.
- Configuring a specific node and unsure what its fields mean → `frontline guidance node <type>`.

See also: `resource-creation`, `schema-design`, `crud-operations` (these reference this command for
value lists), and `workflow-builder` / `flow-builder` (graph construction).
