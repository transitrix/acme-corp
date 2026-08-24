# `canon/elements/02_business/processes/`

Process element primitives — each file is one business process on the ArchiMate 3.2 **business** layer. The process-map view (`../../../views/processmap/`) catalogues them by Operating / Supporting / Management; detailed flows live in `../../../views/bpmn/`.

TYPE registry: [`notations/IDS_AND_REFERENCES.md`](../../../../../../notations/IDS_AND_REFERENCES.md) §3.1 (`PROCESS`).

## File convention

`<id>.yaml`, where `<id>` follows `PROCESS-[<middle>-]<INTEGER>` from [`IDS_AND_REFERENCES.md`](../../../../../../notations/IDS_AND_REFERENCES.md) §1. Examples: `PROCESS-ORD-FULFILL-1.yaml`.

## Schema

Defined in [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §7.5 over the common envelope §3:

- Identity + process fields: `notation: process`, `id`, `name`, `owner_role: ROLE-…`, `capability: CAPABILITY-…`, `maturity` (CMM 1–5), `bpmn_file`, `description`.
- Admission record ([`CONTRACT.md`](../../../../../../notations/CONTRACT.md) §6) and primitive lifecycle ([`CONTRACT.md`](../../../../../../notations/CONTRACT.md) §7).

## Examples in this folder

| File | Notes |
|---|---|
| `PROCESS-ORD-FULFILL-1.yaml` | Operating — realises `CAPABILITY-V1`, owned by `ROLE-OPS-1` |
| `PROCESS-CUST-ONBOARD-1.yaml` | Operating — realises `CAPABILITY-V2` |
| `PROCESS-CS-RESOLVE-1.yaml` | Supporting |
| `PROCESS-STRAT-PLAN-1.yaml` | Management |
| `PROCESS-RETURNS-1.yaml` | Operating — realises `CAPABILITY-V1`, owned by `ROLE-OPS-1` |

## Deliberately unmodelled, now scaffolded — Returns & Refunds

Until this addition, `PROCESS-ORD-FULFILL-1` covered the forward order-to-cash path only (intake through shipment / backorder notice) with no reverse-logistics counterpart — a customer-initiated return or refund had no process to attach to anywhere in `canon/`, despite `PRODUCT-ECOMM-1` being a live storefront that necessarily generates returns. This was a genuine coverage gap, not staged: nothing in the model asserted a returns process existed.

**Notation recommendation.** A single process's participants and flow are the definition home of a `PROCESS` element (`ELEMENT_PRIMITIVES.md` §7.5) — the same notation as every process already in this folder — not a `.bpmn.transitrix.yaml` view, which is a *derived projection* of that element's `flow` and not itself the source ([`views/01-bpmn.md`](../../../../../../notations/views/01-bpmn.md)). Three of the four pre-existing processes in this folder (`ORD-FULFILL`, `CUST-ONBOARD`, `CS-RESOLVE`) have no BPMN projection at all, so `PROCESS-RETURNS-1.yaml` follows that same majority pattern: a minimal but structurally complete `PROCESS` element (participants + a short flow), with a BPMN rendering left for if/when a presentation-scale diagram was actually needed.

A presentation-scale rendering was since needed, so `../../../views/bpmn/returns-processing.bpmn.transitrix.yaml` now provides it — a projection of the `flow:` above, kept small enough to read at 1080p with no zoom. The `flow:` on this element stays the source of truth; regenerate the view if it changes.

## See also

- Element-primitive schema: [`notations/ELEMENT_PRIMITIVES.md`](../../../../../../notations/ELEMENT_PRIMITIVES.md) §7.5.
- Process-map notation: [`notations/views/06-process-map.md`](../../../../../../notations/views/06-process-map.md).
- Views over these elements: [`../../../views/processmap/`](../../../views/processmap/), [`../../../views/bpmn/`](../../../views/bpmn/).
