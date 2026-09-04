---
id: ADR-2026-09-04-pin-methodology-5-1-0
title: "Pin methodology_version to 5.1.0 for the acme-corp model"
status: accepted
date: "2026-09-04"
author: agent
source: ad-hoc
relates_to:
  - ADR-2026-08-31-pin-methodology-5-0-0
  - ADR-0007
supersedes: ADR-2026-08-31-pin-methodology-5-0-0
superseded_by: null
---

## Context

The methodology is cutting [5.1.0](https://github.com/transitrix/methodology/releases/tag/v5.1.0)
— a **MINOR** increment over 5.0.0. Additive work since that pin: the
`documents` package (optional, experimental), knowledge-object
`supersedes` / `superseded_by` fields and `FRESHNESS-001` on knowledge
objects, the issue-tracker binding guide, and document-renderer
paged-media / landscape / caption work. No field is renamed or removed.
There is no migration recipe for 5.0.0 → 5.1.0.

This repository does not declare `packages: [documents]` and has no
knowledge-store objects, so none of the new optional surfaces apply.

## Decision

Pin `methodology_version: "5.1.0"` in `transitrix.yaml` (and the three view
files carrying a concrete pin: `views/actions-tree/portfolio-all.actions-tree.transitrix.yaml`,
`views/glossary/full.glossary.transitrix.yaml`,
`views/rules-in-force/all.rules-in-force.transitrix.yaml`).

**Accepted by automation 2026-09-04.** `acme-corp` is a demo/reference
repository, not a production adopter — the maintainer confirmed 2026-08-31
that the methodology agent may flip an `author: agent` ADR's status directly
here, rather than holding it at `proposed` pending a human reviewer as
`method/08-governance.md` §2 requires for a real adopter's model.

## Consequences

- The model is validated against 5.1.0 semantics. No codemod applies.
- Admitting a `documents` package artefact, or a knowledge object that
  uses supersession / freshness, remains a separate modelling choice.
