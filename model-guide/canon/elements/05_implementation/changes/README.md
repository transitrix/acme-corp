# `canon/elements/05_implementation/changes/`

Change element primitives — each file is one BDN **business change** (an ArchiMate 3.2 *Gap*) on the **Implementation & Migration** layer. A change is a required delta to reach the target state, at any granularity; higher-level changes decompose into lower-level ones via a `parent` relation. Changes are arranged by the DGCA view ([`../../../views/dgca/`](../../../../../views/dgca)) and delivered by actions ([`../actions/`](../../../../../canon/elements/05_implementation/actions/)).

TYPE registry: [`notations/IDS_AND_REFERENCES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/IDS_AND_REFERENCES.md) §3.1 (`CHANGE`). Layer rationale: [`notations/ELEMENT_PRIMITIVES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/ELEMENT_PRIMITIVES.md) §6.1.

## File convention

`<id>.yaml`, where `<id>` follows `CHANGE-[<middle>-]<INTEGER>` from [`IDS_AND_REFERENCES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/IDS_AND_REFERENCES.md) §1. Examples: `CHANGE-EU-CRM-1.yaml`.

## Schema

Defined in [`notations/ELEMENT_PRIMITIVES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/ELEMENT_PRIMITIVES.md) §7.3 over the common envelope §3:

- Identity + change fields: `notation: change`, `id`, `name`, `goals: [GOAL-…]`, optional `parent: CHANGE-…` (multi-scale decomposition), `description`.
- Admission record ([`CONTRACT.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/CONTRACT.md) §6) and primitive lifecycle ([`CONTRACT.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/CONTRACT.md) §7).

## Examples in this folder

| File | Notes |
|---|---|
| `CHANGE-EU-CRM-1.yaml` | Stand up EU-localised CRM; delivers `GOAL-EU-1` |
| `CHANGE-ONBOARD-1.yaml` | Onboarding rework; delivers `GOAL-CUST-1` |

## See also

- Element-primitive schema: [`notations/ELEMENT_PRIMITIVES.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/ELEMENT_PRIMITIVES.md) §7.3, layer §6.1.
- DGCA notation: [`notations/views/02-dgca.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/views/diagrams/02-dgca.md).
- Sibling actions catalogue: [`../actions/`](../../../../../canon/elements/05_implementation/actions/).
