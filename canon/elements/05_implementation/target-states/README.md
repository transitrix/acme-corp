# `canon/elements/05_implementation/target-states/`

Target-state element primitives — each file is one ArchiMate 3.2 **Plateau** on the **Implementation & Migration** layer. A target state is the structural snapshot of the `CAPABILITY` / `PROCESS` / `APPLICATION` selection that exists when one or more `GOAL`s are met — the object an architect *varies* when offering the customer solution options. The path that reaches a target state is a `SCENARIO`; the goals a target state satisfies are carried as a first-class time-aware `REL`, never inline on the target state.

TYPE registry: [`notations/IDS_AND_REFERENCES.md`](../../../../../../notations/IDS_AND_REFERENCES.md) §3.1 (`TARGET_STATE`). Layer rationale: [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §6.1.

## File convention

`<id>.yaml`, where `<id>` follows `TARGET_STATE-[<middle>-]<INTEGER>` from [`IDS_AND_REFERENCES.md`](../../../../../../notations/IDS_AND_REFERENCES.md) §1. Examples: `TARGET_STATE-EU-LIVE-1.yaml`.

## Schema

Defined in [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §7.17 over the common envelope §3:

- Identity + composition: `notation: target-state`, `id`, `name`, optional `capabilities: [CAPABILITY-…]`, `processes: [PROCESS-…]`, `applications: [APPLICATION-…]`, `description`.
- Goal satisfaction is **not** an inline field — it is a first-class `REL` kind (`target_state_satisfies_goal`, `notations/elements/17-relations.md` §3).
- Scenarios point at target states (a `SCENARIO.target_state` reference on the scenario side); there is no `scenarios:` back-reference here.
- Admission record ([`CONTRACT.md`](../../../../../../notations/CONTRACT.md) §6) and primitive lifecycle ([`CONTRACT.md`](../../../../../../notations/CONTRACT.md) §7).

## Examples in this folder

| File | Notes |
|---|---|
| `TARGET_STATE-EU-LIVE-1.yaml` | EU operations live in three markets — composition spans existing capabilities, onboarding and fulfilment processes, and the CRM and OMS applications. Reaches `GOAL-EU-1` via a separate `REL`. |
| `TARGET_STATE-BASE-1.yaml` | `type: base` — the baseline plateau (today, not a destination): all currently-live capabilities, processes, and applications. Partially satisfies `GOAL-REVENUE-1` via `REL-TS-BASE-GOAL-REVENUE-1.yaml`. Lets impact/retirement analysis trace an `APPLICATION` up through this composition to the standing goals it serves right now — see `ELEMENT_PRIMITIVES.md` §7.17. |

## See also

- Element-primitive schema: [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §7.17, layer §6.1.
- Sibling actions catalogue: [`../actions/`](../actions/).
- Sibling changes catalogue: [`../changes/`](../changes/).
