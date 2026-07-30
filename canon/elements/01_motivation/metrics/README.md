# `canon/elements/01_motivation/metrics/`

Metric element primitives — each file is one **managed indicator** on the ArchiMate 3.2 **motivation** layer. `METRIC` has no ArchiMate counterpart (ArchiMate 3.x has no dedicated indicator/KPI element). Distinct from `COVERAGE_METRIC` (a report-config document under `notations/views/22-coverage-metric.md`, rendered from `ASSERTION` / `REQUIREMENT` / codex data, with no canonical content of its own): a `METRIC` is a first-class catalogue element naming what the organisation measures, its unit, its target, and its direction of good.

TYPE registry: [`notations/IDS_AND_REFERENCES.md`](../../../../../../notations/IDS_AND_REFERENCES.md) §3.1 (`METRIC`).

## File convention

`<id>.yaml`, where `<id>` follows the canonical grammar `METRIC-[<middle>-]<INTEGER>` from [`IDS_AND_REFERENCES.md`](../../../../../../notations/IDS_AND_REFERENCES.md) §1. Example: `METRIC-REVENUE-GROWTH-1.yaml`.

## Schema

Defined in [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §7.26 (per-TYPE fields) over the common envelope §3:

- Identity + metric fields: `notation: metric`, `id`, `name`, `measures` (**required**, non-empty list of `GOAL-…` / `CAPABILITY-…` / `PROCESS-…`), `unit` (**required**), `target` (**required**, number), `direction_of_good` (**required**, `higher_is_better` \| `lower_is_better` \| `on_target`), `owner_role` (**required**, `ROLE-…`), `description`.
- Admission record per [`CONTRACT.md`](../../../../../../notations/CONTRACT.md) §6: `zone: canon`, `admitted_at`, `admitted_by`, `gate_checks`.
- Primitive lifecycle per [`CONTRACT.md`](../../../../../../notations/CONTRACT.md) §7: `valid_from`, `valid_to`.

## Examples in this folder

| File | Notes |
|---|---|
| `METRIC-REVENUE-GROWTH-1.yaml` | Measures `GOAL-REVENUE-1`; owned by `ROLE-EXEC-1`; target 45% YoY, higher is better |

## See also

- Element-primitive schema: [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §7.26.
- The report-config view this is distinct from: [`notations/views/22-coverage-metric.md`](../../../../../../notations/views/22-coverage-metric.md).
- The goal this measures: [`../goals/`](../goals/).
