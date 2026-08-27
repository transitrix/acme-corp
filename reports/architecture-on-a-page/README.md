# Architecture on a Page

A one-page A3-landscape read of this repository's whole model, organised by
Svyatoslav Kotusev's CSVLOD taxonomy ("Enterprise Architecture Artifacts on a Page",
[eaonapage.com](https://www.eaonapage.com/)): six cells on two axes — rows are
business-focused / IT-focused, columns are rules / structures / solutions.

`architecture-on-a-page.svg` is the rendered artefact. Page box: **420×297mm /
1191×842pt**, declared on the root `<svg width="1191pt" height="842pt" viewBox="0 0
1191 842">` and verified on that produced attribute, not on any stylesheet.

## Why this isn't a `views/` file

Every file under `views/` is a notation-conformant, schema-validated model
input. This page is the opposite direction: a rendered *output* assembled from
several of those views plus codex and canon elements. It carries no model content of
its own and is not re-admitted through the ingest gate, so it sits in its own
top-level folder rather than inside `views/`.

## Cell → source mapping

| Cell | Filled from |
|---|---|
| **Considerations** (business rules) | `POLICY` under `codex/internal/` (0 admitted) + DGCA driver→goal pairs: `views/dgca/*`, `canon/elements/01_motivation/{factors,goals}/*` |
| **Visions** (business structures) | `views/capabilities/compliance-domain.capability-map.transitrix.yaml`; `canon/elements/05_implementation/target-states/*`; milestones (no dedicated activity-network view exists — carried on the Outlines-cell action card instead); `views/process-blueprint/order-fulfilment.process-blueprint.transitrix.yaml` |
| **Outlines** (business solutions) | `views/scenarios/eu-go-live.scenarios.transitrix.yaml`; `canon/elements/05_implementation/changes/*`; `views/action-card/eu-gdpr-remediation.action-card.transitrix.yaml` |
| **Standards** (IT rules) | `INTERNAL_STANDARD` under `codex/internal/` (1 admitted) + `NODE`/`TECHNOLOGY_SERVICE` elements (0 instances — see note below) arranged in `blocks`: `views/blocks/personal-data-landscape.blocks.transitrix.yaml` |
| **Landscapes** (IT structures) | `views/applications/eu-portfolio.applications.transitrix.yaml`; no dedicated integration-map view exists (0); `canon/elements/02_business/business-objects/*` |
| **Designs** (IT solutions) | SRS/SDD document-views — 0 instances in this repo |

The Considerations/Standards "rules in force" figures (`POLICY`: 0, `INTERNAL_STANDARD`:
1) are computed against current canon using the same selection criteria as
methodology's rules-in-force report-config (`POLICY` + `INTERNAL_STANDARD` under
`codex/internal/`) — independently re-derived here rather than depending on the
still-open rules-in-force demonstration branch for this repo.

## Known absent / known zero (counted states, not omissions)

- **Principles, Patterns, Logical Data Models** — no primitive for these three in the
  methodology; out of scope for this page by design. `acme-corp` does carry one
  `PRINCIPLE` element (`PRINCIPLE-customer-data-purpose-limitation-1`), but Kotusev's
  CSVLOD grid has no cell for it, so it does not appear here.
- **`POLICY`, `NODE`, `TECHNOLOGY_SERVICE`, integration-map, SRS, SDD** — all defined
  in methodology; zero instances currently modelled in this repo. Shown on the page as
  an explicit "0", not left blank.

## Assembly method

`@transitrix/document-view-engine`'s current renderer (`packages/document-view-engine/src/render.mjs`
in `transitrix/methodology`) renders only the `blocks` notation inline; every other
notation resolves as a missing illustration. Fixing that limit is out of scope here —
this page is hand-assembled instead:

- The **Standards** cell's technology-blocks panel is the real, unmodified output of
  `renderBlocksSvg()` (`packages/document-view-engine/src/blocks-view.mjs`) run
  against this repo's `BLOCKS-PERSONAL-DATA-1` — a genuine renderer call, not a
  drawing of one.
- Every other cell is hand-transcribed text, each line traced back to the source file
  cited in the table above and re-read at time of writing (not reconstructed from
  memory or from filenames).
- Layout, wrapping and page-box declaration were produced by a one-off local script,
  not committed — it is rendering apparatus, not the deliverable; the deliverable is
  this SVG plus this README.

## Re-running

There is no committed CLI for this composition (same posture as the rules-in-force
report: `REPORT_VIEW_CONFIG.md` §5 — "the CLI implementation itself is tooling,
delivered separately"). To refresh the page: re-read each cited source file, re-run
`renderBlocksSvg()` against the current `BLOCKS-PERSONAL-DATA-1`, and re-lay-out a
1191×842pt SVG in the six-cell grid described above.
