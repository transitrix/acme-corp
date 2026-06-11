<!-- DRAFT — structure only. Final narrative voice & positioning are owned by the
     comms / strategy layer (STYLE_GUIDE §3 voice tests, §3.5 no retired terms).
     This file is the demo SPINE: each beat maps to the notation/view that tells it.
     Fictional, data-free. -->

# acme_corp — a Transitrix walkthrough

> **What this is.** `acme_corp` is a fictional mid-size EU direct-to-consumer online
> retailer, modelled end-to-end in Transitrix. This walkthrough reads the repository as
> one story — from "who they are" to "audit-ready" — so the notations connect into a
> coherent picture rather than standing as isolated diagrams.
>
> _Fictional and data-free. GDPR / NIS2 / e-commerce appear here only as demonstration
> material._

## The story in eight beats

Each beat links to where it lives in this repo.

1. **Who they are — the as-is enterprise.**
   Products, the system estate, and capabilities at their current maturity.
   → [`canon/views/products/`](canon/views/products/) ·
     [`canon/views/applications/`](canon/views/applications/) ·
     [`canon/views/capabilities/`](canon/views/capabilities/)

2. **The pressure — why they had to change.**
   External drivers (a GDPR enforcement wave, incoming NIS2) and the real obligations
   behind them; the coverage read shows where the model was still "dark".
   → [`canon/views/fgca/`](canon/views/fgca/) (factors) ·
     [`codex/`](codex/) (the obligations) ·
     [`canon/views/coverage-metric/`](canon/views/coverage-metric/)

3. **What they decided to become — the intent.**
   The goal tree: compliance, resilience, growth.
   → [`canon/views/goals/`](canon/views/goals/) · [`canon/views/fgca/`](canon/views/fgca/)

4. **The transformation — how.**
   The changes, target capability maturity, alternative paths considered.
   → [`canon/views/fgca/`](canon/views/fgca/) ·
     [`canon/views/capabilities/`](canon/views/capabilities/) ·
     [`canon/views/scenarios/`](canon/views/scenarios/)

5. **The delivery — the work.**
   The readiness programme as a scheduled project: dependencies, critical path, milestones.
   → [`canon/views/activities/`](canon/views/activities/)

6. **How it runs day-to-day.**
   From the process landscape down to one detailed process, and a value-chain blueprint
   with the obligations lane.
   → [`canon/views/processmap/`](canon/views/processmap/) ·
     [`canon/views/bpmn/`](canon/views/bpmn/) ·
     [`canon/views/process-blueprint/`](canon/views/process-blueprint/)

7. **The proof — compliance, made legible.**
   Which obligations hit which products and processes, with each cell's status; the gaps
   that got closed.
   → [`canon/views/compliance-impact/`](canon/views/compliance-impact/)

8. **The outcome — audit-ready and machine-runnable.**
   Coverage before → after, and the decisions log that records how the architecture was
   governed along the way.
   → [`canon/views/coverage-metric/`](canon/views/coverage-metric/) ·
     [`operations/decisions/`](operations/decisions/)

## How to read it yourself

Open any view file in **Transitrix Studio** (VS Code) for a live diagram, or render with
`npx @transitrix/cli validate <file>`. The whole-repo model integrity is gated in CI
(`.github/workflows/architecture-validate.yaml`). New here? Start with
[`GETTING_STARTED.md`](GETTING_STARTED.md).

---

<!-- TODO (comms/strategy): replace beat blurbs with the final success-story prose;
     wire each beat to the specific view file(s) once the demo scenario content is
     filled in (see methodology task ADPT-3 for the modelling gaps that complete the
     compliance matrix in beats 6–7). Keep fictional + data-free; no client names. -->
