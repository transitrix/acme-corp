---
id: ADR-2026-08-25-pin-methodology-4-0-0
title: "Pin methodology_version to 4.0.0 for the acme-corp model"
status: proposed
date: "2026-08-25"
author: agent
source: ad-hoc
relates_to:
  - ADR-2026-08-23-pin-methodology-3-7-0
  - ADR-0006
  - ADR-0007
supersedes: ADR-2026-08-23-pin-methodology-3-7-0
superseded_by: null
---

## Context

The methodology is cutting 4.0.0
([methodology#528](https://github.com/transitrix/methodology/pull/528))
— a **MAJOR** increment over the previously pinned 3.7.0. The breaking set is
the FGA notation key's removal, the `.ttrs` header rename
(`template_id`/`template_version` → `recipe_id`/`recipe_version`), and
underscore forbidden in an ID middle segment. Additive work in the same
window (`process_parent`, optional `DRIVER.falsifier` /
`ASSESSMENT.geographic_scope`, the `rules-in-force` view, `ACT-021`) does
not require this repository to grow new artefacts in order to pin.

This model has no `*.fga.transitrix.yaml` file and no `.ttrs` recipe file.
The `views/fga/` folder is already a stub pointing at DGCA. No
middle-segment underscore IDs are in use. The migration recipe at
`migrations/3.1-to-4.0/` therefore has nothing here to rewrite; the pin is
the whole change.

**Recorded, not resolved, by this ADR:** the same `AGENTS.md` / actual-practice
tension the 3.7.0 pin record named — an agent applied the pin, consistent
with every prior pin bump in this repository's history. Not this record's to
settle.

## Decision

Pin `methodology_version: "4.0.0"` in `transitrix.yaml`.

**Proposed — not yet ratified.** Per `method/08-governance.md` §2, an
`author: agent` record stays `proposed` until a human flips it to `accepted`;
an agent may never self-ratify.

## Consequences

- On ratification, the model is validated against 4.0.0 semantics. The
  migration recipe is a no-op on this repository today.
- Until ratified, `main` runs on a pin whose decision record is unratified —
  the same interim condition the 3.7.0 pin recorded.
- The `views/fga/` stub remains a pointer, not a live FGA document.
