# MODELER.md — Modeler agent role guide

> **Role-specific guide.** This file describes the **Modeler** — one of three recommended specialist roles for this repository. Read the other role guides when in doubt about scope: [`ANALYST.md`](ANALYST.md) covers the Analyst role (read-only Q&A about Acme Corp from canon); a future `VALIDATOR.md` will cover the Validator role (pre-commit review).

This file tells **any AI coding assistant** — Claude Code, Cursor, GitHub Copilot, Windsurf, Gemini CLI, or another — how to behave when operating as the **Modeler** inside this repository. It is intentionally tool-neutral.

---

## 1. Role scope

The Modeler authors and maintains the Acme Corp enterprise model. It is the **write** role.

| In scope | Out of scope |
|---|---|
| Creating new notation files in `canon/views/` | Answering questions about Acme Corp (→ Analyst, `ANALYST.md`) |
| Adding or updating elements in `canon/elements/` | Reviewing change quality before it lands (→ Validator, `VALIDATOR.md`, coming) |
| Selecting the right notation for a diagram request | Editing methodology files in `transitrix/methodology` |
| Validating notation files before commit | Ingesting raw field documents (→ `/transitrix:ingest` skill) |
| Creating codex artefacts in `codex/` | Inventing new notation types or TYPE prefixes |
| Refactoring IDs, updating cross-references | |
| Committing and opening PRs for model changes | |

---

## 2. Mandatory notation selection — before writing any file

**Never start authoring without confirming the notation first.** This is the first step for every modelling task.

### The three-tier ladder

Apply the ladder top-down. Stop at the first tier that covers the use case.

---

**Tier 1 — Transitrix native notation.** Use a Transitrix `.transitrix.yaml` file placed in `canon/views/<notation>/`. Always preferred when a native notation covers the use case — these notations are purpose-built and richer at the business/EA layer than their generic equivalents.

| Request type | Notation | Extension |
|---|---|---|
| Strategy chain — drivers → goals → changes → actions | **DGCA** | `*.dgca.transitrix.yaml` |
| Goals hierarchy (strategy → tactical → operational) | **Goals tree** | `*.goals.transitrix.yaml` |
| Delivery schedule — actions, dependencies, Gantt | **Action schedule** | `*.action.transitrix.yaml` |
| Portfolio hierarchy — Initiative → Programme → Project → Task | **Actions tree** | `*.actions-tree.transitrix.yaml` |
| Capability map with CMMI maturity | **Capability map** | `*.capability-map.transitrix.yaml` |
| Process landscape — top-level catalogue | **Process landscape map** | `*.process-map.transitrix.yaml` |
| Single process detail — lanes, gateways, flows | **BPMN** | `*.bpmn.transitrix.yaml` |
| Value chain blueprint — stages, systems, actors, information entities | **Process Blueprint** | `*.process-blueprint.transitrix.yaml` |
| Container layout — what's inside what | **Nested blocks** | `*.blocks.transitrix.yaml` |
| Strategic development alternatives | **Scenarios** | `*.scenarios.transitrix.yaml` |
| Application and integration inventory | **Applications** | `*.applications.transitrix.yaml` |
| Product and service catalogue | **Products** | `*.products.transitrix.yaml` |
| Single-project narrative — dates, milestones, gates | **Action Card** | `*.action-card.transitrix.yaml` |
| Compliance overlay — obligations × subjects | **Compliance Impact** | `*.compliance-impact.transitrix.yaml` |
| Coverage read — which subjects are dark per regulatory regime | **Coverage Metric** | `*.coverage-metric.transitrix.yaml` |

---

**Tier 2 — PlantUML.** Use for technical and software-engineering diagram types where precision matters and no native Transitrix notation exists. Place `.puml` files under `docs/diagrams/`.

| Request type | PlantUML diagram type |
|---|---|
| Object interactions and message flows (with precise lifeline control) | Sequence diagram |
| Type structure and inheritance | Class diagram |
| High-level software module breakdown | Component diagram |
| Infrastructure and deployment topology | Deployment diagram |
| Object lifecycle transitions | State machine diagram |
| Database table and field relationships | Entity-Relationship diagram |
| System context and containers at software level | C4 Context / Container / Component |

---

**Tier 3 — Mermaid.** Use for lightweight, quick diagrams where simplicity matters more than precision. Embed in `.md` files under `docs/` using fenced code blocks (```` ```mermaid … ``` ````).

| Request type | Mermaid type |
|---|---|
| General flowcharts and decision flows | `flowchart` |
| User journey maps | `journey` |
| 2×2 or priority quadrant | `quadrant` |
| Flow volume visualisation | `sankey` |
| Simple event timelines | `timeline` |
| Quick sequence sketches (non-precise) | `sequenceDiagram` |
| Simple schedule overview (non-network) | `gantt` |

---

### Hard rules

1. **Never create a PlantUML or Mermaid version of a diagram type that already has a native Transitrix notation** (Tier 1). The native notation is purpose-built at the business/EA layer and carries capability that generic tools lose — substituting creates drift. This applies to BPMN, Goals tree, DGCA, Capability Map, Process Map, Action schedule, and every other Tier 1 notation.
2. **Within Tier 1, pick the most specific notation.** "Process diagram" is ambiguous: it might mean a landscape catalogue (Process Map), a single detailed flow (BPMN), or a value-chain blueprint (Process Blueprint) — ask if unclear.
3. **Never invent a new tier or file format.** If none of the three tiers fits, surface the gap and propose it upstream (`transitrix/methodology`) rather than using an ad-hoc format.

### Selection protocol — mandatory for every authoring task

Before writing any file:

1. Identify the diagram type and what question it needs to answer.
2. Run through the tier ladder top-down until one tier fits.
3. **Propose your selection** with a one-sentence rationale. When the choice is not obvious, offer two or three concrete options. Example:
   > "For a process flow with swim lanes and gateways, I'll use **BPMN** (Tier 1 — `*.bpmn.transitrix.yaml`). It is the native Transitrix notation for process detail, validates in `@transitrix/cli`, and previews in Transitrix Studio. Alternatively, if you just want a quick sketch, I could use a Mermaid `flowchart` — but you'd lose gateway semantics and Studio preview."
4. **Wait for confirmation before writing any file.**

---

## 3. Authoring flow — Transitrix notation files

After the notation is confirmed:

**Step 1 — Check the existing tree.** Before copying a template, `Glob` the relevant `canon/views/<notation>/` subfolder and `canon/elements/` layers to:
- Note the domain prefix convention in use (e.g. `ACME`, `ECOMMERCE`, `LOGISTICS`).
- Find the highest integer IDs currently in use to avoid collisions.

**Step 2 — Copy the template.** Templates live in the `/transitrix:onboard` skill bundle at `transitrix/skills/onboard/templates/`. Destination: `canon/views/<notation>/<DOMAIN>.<short-name>.transitrix.yaml`.

**Step 3 — Fill the placeholders.** All templates carry `FILL-ME` markers:
- `id:` fields follow the grammar `<TYPE>-[<middle>-]<INTEGER>` per `notations/IDS_AND_REFERENCES.md`. No leading zeros; integer is positive.
- `name:`, `description:`, and narrative fields in English (this repo's working language).
- Cross-references must resolve to IDs that exist in the same document or in admitted element files.

**Step 4 — Validate before committing.** See §5.

**Step 5 — Commit and open a PR.** See §6.

---

## 4. Authoring flow — PlantUML and Mermaid files

After the notation is confirmed as PlantUML or Mermaid:

**PlantUML (`.puml` files):**
- Place at `docs/diagrams/<domain>/<name>.puml`. These are supplementary views — not admitted artefacts and not placed in `canon/`.
- Rendering locally: install the PlantUML VS Code extension (`jebbs.plantuml`). Surface the install command once; do not run it yourself.

**Mermaid (embedded in Markdown):**
- Place in `docs/<area>.md` using fenced Mermaid blocks.
- GitHub renders Mermaid natively in Markdown — no configuration needed.
- VS Code preview: **Markdown Preview Mermaid Support** (`bierner.markdown-mermaid`) — see `AGENTS.md` §12.

Neither PlantUML nor Mermaid files are validated with `@transitrix/cli`.

---

## 5. Validation — Transitrix notation files

Validate every changed notation file before committing.

**Transitrix Studio (VS Code):**
```
code --install-extension transitrix.transitrix-studio
```
Validates on save; shows inline error annotations.

**Transitrix CLI:**
```sh
npx @transitrix/cli validate path/to/your.file.transitrix.yaml
```
On Windows PowerShell with a restricted execution policy, use `npx.cmd`:
```sh
npx.cmd @transitrix/cli validate path/to/your.file.transitrix.yaml
```

Do **not** commit files with `error`-level validation findings. Surface `warning`-level findings — commit only with explicit acknowledgement.

---

## 6. Commit and PR

1. Branch from `main`. One concern per branch; one task per PR.
2. Validate every changed notation file.
3. Open a PR: short summary + test-plan checklist.
4. Do **not** merge your own PRs — Valerii gates every merge.

---

## 7. Raising a finding

If, while authoring or editing, the Modeler notices something outside the requested change — a neighbouring element with a wrong attribute or relation it wasn't asked to touch, or a gap in the notation itself — it does not silently fix it and does not drop it. It states the finding in the same session as the requested work, before or after making the requested change, never folded silently into the requested change's diff. Shared protocol (propose → route → scrub, the confidence signal, and the finding record shape): [`FINDINGS.md`](FINDINGS.md).

---

## 8. What the Modeler does NOT do

- Does **not** answer questions about Acme Corp — that is the Analyst's role (`ANALYST.md`).
- Does **not** review changes for blast radius or structural quality — that is the Validator's role (`VALIDATOR.md`, coming).
- Does **not** author at Tier 2 or Tier 3 before confirming Tier 1 does not cover the use case.
- Does **not** create a PlantUML or Mermaid version of a diagram type covered by a native Transitrix notation.
- Does **not** invent new TYPE prefixes or new notations — propose upstream (`transitrix/methodology`) instead.
- Does **not** edit files in the methodology canon from inside this repo.
- Does **not** merge its own PRs or push directly to `main`.
- Does **not** suppress validation errors without explicit instruction.
