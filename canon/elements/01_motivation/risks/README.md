# `canon/elements/01_motivation/risks/`

Risk element primitives — each file is one **projected event** on the ArchiMate 3.2 **motivation** layer. `RISK` has no ArchiMate counterpart (ArchiMate 3.x has no risk element). Distinct from `ASSESSMENT` (`../assessments/`): an assessment is a dated finding about the *present* state of a `DRIVER`; a risk is a claim about *something that has not happened yet* — its likelihood, its impact, and the exposure judged to remain once treatment is in place.

`RISK` is additive alongside the ArchiMate Risk and Security Overlay mapping ([`notations/CONTRACT.md`](../../../../../../notations/CONTRACT.md) §8.1), which expresses risk entirely through existing motivation primitives (`ASSESSMENT` / `DRIVER` / `GOAL` / `REQUIREMENT` / `CONSTRAINT`). The two are not exclusive — this repository uses `RISK` directly for the worked example below.

TYPE registry: [`notations/IDS_AND_REFERENCES.md`](../../../../../../notations/IDS_AND_REFERENCES.md) §3.1 (`RISK`).

## File convention

`<id>.yaml`, where `<id>` follows the canonical grammar `RISK-[<middle>-]<INTEGER>` from [`IDS_AND_REFERENCES.md`](../../../../../../notations/IDS_AND_REFERENCES.md) §1. Example: `RISK-SUPPLY-CHAIN-BREACH-1.yaml`.

## Schema

Defined in [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §7.26 (per-TYPE fields) over the common envelope §3:

- Identity + risk fields: `notation: risk`, `id`, `name`, `likelihood` / `impact` / `residual` (**required**, `low` \| `medium` \| `high`), `owner_role` (**required**, `ROLE-…`), `threatens` (**required**, non-empty list of typed IDs), `treated_by` (optional list of `REQUIREMENT-…` / `CONSTRAINT-…`), `description`.
- Admission record per [`CONTRACT.md`](../../../../../../notations/CONTRACT.md) §6: `zone: canon`, `admitted_at`, `admitted_by`, `gate_checks`.
- Primitive lifecycle per [`CONTRACT.md`](../../../../../../notations/CONTRACT.md) §7: `valid_from`, `valid_to`.

## Examples in this folder

| File | Notes |
|---|---|
| `RISK-SUPPLY-CHAIN-BREACH-1.yaml` | Threatens `DRIVER-EU-REG-1`; treated by the existing `REQUIREMENT-NIS2-SUPPLY-CHAIN-1`; owned by `ROLE-TECH-1` |

## See also

- Element-primitive schema: [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §7.26.
- The alternative motivation-primitive risk mapping: [`notations/CONTRACT.md`](../../../../../../notations/CONTRACT.md) §8.1.
- The driver this threatens: [`../factors/`](../factors/).
- The requirement that treats it: [`../requirements/`](../requirements/).
