# Architecture on a Page

An A3-landscape, manually assembled reading of the fictional Acme Corp model.
It uses Svyatoslav Kotusev's CSVLOD taxonomy as a reading frame, not as an
implemented Transitrix notation or a complete catalogue of EA artefacts.

`architecture-on-a-page.svg` is the rendered artefact. Its root declares
**420 × 297 mm**, with a `1191 842` viewBox. The physical dimensions, not the
rounded viewBox coordinates, determine the print size.

## Snapshot and interpretation

Model sources: [Acme Corp revision 0530089](https://github.com/transitrix/acme-corp/tree/053008958d5a4ccc9cad7d2b9d671ad337c03094),
checked **2026-10-21**, pinned to Methodology **7.0.0** in `transitrix.yaml`.
Counts describe that repository snapshot. Versioned maturity attributes are
resolved at 2026-10-21 by the latest `valid_from` not later than that date.
An arrow is current → target, not proof of progress. Scenario statements and
milestones describe targets/plans, not verified achievements or legal compliance.

The reading frame follows [Enterprise Architecture on a Page v1.2](https://eaonapage.com/Enterprise%20Architecture%20on%20a%20Page%20(v1.2).pdf)
and [Enterprise Architecture on a Single Page (Kotusev, 2017)](https://kotusev.com/Enterprise%20Architecture%20on%20a%20Single%20Page.pdf).
Rows are **Business-Focused / IT-Focused**; columns are **Rules / Structures /
Changes**. The six cells and their selected source correspondence are:

| Cell | Snapshot sources and limits |
|---|---|
| **Considerations** (business rules) | `codex/internal/`: 0 `POLICY`, 1 `PRINCIPLE`; selected driver → goal links from `canon/elements/01_motivation/{factors,goals}/`. These illustrate business direction, not a claim that every goal is a CSVLOD artefact. |
| **Visions** (business structures) | `views/capabilities/compliance-domain.capability-map.transitrix.yaml` plus maturity sidecars in `canon/elements/02_business/capabilities/`; 2 `canon/elements/05_implementation/target-states/` records; `views/process-blueprint/order-fulfilment.process-blueprint.transitrix.yaml` (5 stages). No dedicated activity-network view; the 2 planned milestones are on the action card. |
| **Outlines** (business changes) | `views/scenarios/eu-go-live.scenarios.transitrix.yaml` (1 target scenario); `canon/elements/05_implementation/changes/` (3 changes); `views/action-card/eu-gdpr-remediation.action-card.transitrix.yaml` (1 action card, 2 planned milestones). |
| **Standards** (IT rules) | `codex/internal/INTERNAL_STANDARD-coding-conventions-1.yaml` (1 organisation-issued standard). No claim of a technology patterns catalogue. |
| **Landscapes** (IT structures) | `views/applications/eu-portfolio.applications.transitrix.yaml` (2 selected applications, 1 inline integration), with vendor/maturity sidecars; `canon/elements/02_business/business-objects/` (1 primitive, not a complete logical data model); `views/blocks/personal-data-landscape.blocks.transitrix.yaml` (rendered systems/stores panel). No dedicated integration-map view. |
| **Designs** (IT changes) | No SRS or SDD document-view instances in this snapshot. This zero is a repository observation, not an absence of the specifications. |

## Principles and counted gaps

CSVLOD places Principles within **Considerations**. The snapshot has
`codex/internal/PRINCIPLE-customer-data-purpose-limitation-1.yaml`,
“Customer Data Purpose Limitation”; it is included in that cell. It is counted
separately from `POLICY` and `INTERNAL_STANDARD`, rather than silently changing
the rules-in-force report's selection scope.

There are 0 modelled `NODE` and 0 `TECHNOLOGY_SERVICE` primitives, and no dedicated
integration-map, activity-network, SRS or SDD view instances. These are counts of
specified model/view populations, not claims that the fictional organisation has
no infrastructure, integrations or designs. Patterns and logical data models are
not represented by this page; it makes no claim that Methodology lacks those
concepts. The personal-data blocks panel describes technical structure and is
therefore presented in Landscapes, not as a technical standard.

## Assembly and refresh

The existing systems/stores panel is retained from the original
`renderBlocksSvg()` output for `BLOCKS-PERSONAL-DATA-1`. The other cells are
manually transcribed from the sources above. The renderer output has not been
recomputed, and no current engine capability beyond that existing panel is
asserted. There is no committed composition CLI or automatic refresh.

To refresh: choose a source revision and an effective date, re-read the named
populations and sidecars, verify the selected relationships and view contents,
update the text and any changed panel, and inspect the full rendered A3 page.
The SVG is a derived report outside `views/`; it introduces no canonical model
records. A source change does not automatically update a downloaded copy.
