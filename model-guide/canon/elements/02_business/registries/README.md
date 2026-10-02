# `canon/elements/02_business/registries/`

Registry elements — curated, **org-authored operating configuration**. Each registry is one file under this folder. Registries sit on the ArchiMate 3.2 **business** layer.

A registry is the list the organisation maintains to drive an operating activity. The worked example is the **regulatory source registry** (`REGISTRY-REG-SOURCES-1.yaml`): which regulatory sources to watch, where each lives, whether and how each is monitored for change, and how often. A registry is model content the organisation *authors* — distinct from **codex** (`canon/../codex/`), which is *given to* the organisation from outside (`LAW` / `REGULATION` / `POLICY` / `INTERNAL_STANDARD`); from the **Field** zone, which is contradiction-tolerant evidence rather than curated truth; from a **rule** (`../rules/`), which is decision logic rather than a maintained list; and from the team `operations/` folder, which holds the team's working artefacts rather than model content.

TYPE registry: see [`notations/IDS_AND_REFERENCES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/IDS_AND_REFERENCES.md) §3.1 (`REGISTRY`).

## File convention

`<id>.yaml`, where `<id>` follows the canonical grammar `REGISTRY-[<middle>-]<INTEGER>` from `IDS_AND_REFERENCES.md`.

Examples: `REGISTRY-REG-SOURCES-1.yaml`, `REGISTRY-1.yaml`.

## Config vs operating state — two files

A registry that drives an automated activity accrues runtime **operating state** (last scan, next due, change-detected, review pending, latest snapshot). That state is machine-written and **must not** live inline on the registry — it would churn the source-of-truth file on every scan. It lives in a co-located **operating-state sidecar**, which is **not** canon (no admission record, regenerable):

```
REGISTRY-<…>.yaml            # the registry — authored configuration only
REGISTRY-<…>.runstate.yaml   # per-row operating state — machine-written, NOT canon
```

See [`notations/CONTRACT.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/CONTRACT.md) §9.6 (config/state boundary) and the full schema in [`notations/ELEMENT_PRIMITIVES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/ELEMENT_PRIMITIVES.md) §7.19.

## Element schema

The common envelope is in [`notations/ELEMENT_PRIMITIVES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/ELEMENT_PRIMITIVES.md) §3; the `REGISTRY` field set and the per-row schema are in §7.19.

### Required (element)

| Field | Description |
|---|---|
| `notation` | literal `registry` |
| `id` | `REGISTRY-[<middle>-]<INTEGER>` |
| `name` | one-line label |
| `type` | registry kind — v1: `regulatory_source` |
| `rows` | the registry entries (per-row schema depends on `type`) |
| admission record | `zone: canon`, `admitted_at`, `admitted_by`, `gate_checks` — [`CONTRACT.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/CONTRACT.md) §6 |
| lifecycle | `valid_from`, `valid_to` — [`CONTRACT.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/CONTRACT.md) §7 |

### Optional (element)

| Field | Description |
|---|---|
| `description` | what the registry is for and how it is maintained |
| `default_scan_frequency` | ISO 8601 duration; default cadence for rows that omit `scan_frequency`. Falls back to the manifest's `operating_parameters.default_scan_frequency` ([`MANIFEST.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/MANIFEST.md) §2). |

### Row schema — `type: regulatory_source`

| Field | Required | Description |
|---|---|---|
| `id` | yes | canonical-grammar source ID, e.g. `SOURCE-GDPR-1`; inline + promotable |
| `name` | yes | human label of the source |
| `type` | yes | `law` / `regulation` / `policy` / `standard` / `guidance` |
| `jurisdiction` | yes | regime / jurisdiction, e.g. `EU`, `DE`, `UK` |
| `citation` | recommended | human citation (title, article, issuing body) |
| `source_url` | recommended | canonical publication URL |
| `monitoring_needed` | yes | whether actively watched for change |
| `monitor_instead` | no | `SOURCE-…` IDs watched in its place (when `monitoring_needed: false`) |
| `scan_frequency` | no | ISO 8601 duration; omit to inherit the registry / manifest default |
| `change_signal_method` | when monitored | `etag` / `api-updated-field` / `version-date` / `content-hash` |

Rows are **canonical-by-containment**: a row's `id` is addressable and is promoted to its own registered standalone TYPE only when a second document references it (the same mechanic as a `PROCESS` flow step). See §7.19.

## Examples in this folder

| File | Description |
|---|---|
| `REGISTRY-REG-SOURCES-1.yaml` | Regulatory source registry — sources the org watches for obligations |
| `REGISTRY-REG-SOURCES-1.runstate.yaml` | Operating-state sidecar for the above (machine-written, not canon) |

## See also

- TYPE registry: [`notations/IDS_AND_REFERENCES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/IDS_AND_REFERENCES.md) §3.1 (`REGISTRY`), §4 (uniqueness scope).
- Config/state boundary: [`notations/CONTRACT.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/CONTRACT.md) §9.6.
- Sibling rules catalogue: [`../rules/`](../../../../../canon/elements/02_business/rules/).
