---
id: ADR-2026-08-31-pin-methodology-5-0-0
title: "Pin methodology_version to 5.0.0 for the acme-corp model"
status: proposed
date: "2026-08-31"
author: agent
source: ad-hoc
relates_to:
  - ADR-2026-08-27-pin-methodology-4-2-0
  - ADR-0007
supersedes: ADR-2026-08-27-pin-methodology-4-2-0
superseded_by: null
---

## Context

The methodology released [5.0.0](https://github.com/transitrix/methodology/releases/tag/v5.0.0)
— a **MAJOR** increment over 4.2.0. Two breaking changes force the bump:
the ReqIF package's `transition`/`revise`/`history`/`suspect` commands and
`REQIF-008`/`REQIF-009` validation rules are removed (lifecycle now lives in
core's agreement axis, `CONTRACT.md` §6.3); and the `FGCA-008..014` rule
codes are retired (superseded by `DGCA-REPO-008..011`, or removed without
replacement). Every additive change accumulated since 4.2.0 — zone
enumeration validation, the `ORGANIZATION` element type, the DGCA chain-view
action-scoped selector and goal-scoped projection caption contract, the
Products Catalogue projection form, and others — rides along in the same
release.

Migration recipe: `migrations/4.2-to-5.0/` in the source methodology repository.
Neither breaking change alters file shape (no field is renamed or moved);
the recipe's own codemod scans for adopter automation still invoking one of
the four removed `transitrix-reqif` commands. This repository does not
declare `packages: [reqif]` in `transitrix.yaml` and has no `reqif/` folder;
running `node migrations/4.2-to-5.0/codemod.mjs --dry-run` against this
repository's checkout confirms **zero occurrences** across 254 files scanned.
The recipe's own step 1 ("check whether this recipe applies to you... skip
straight to the version bump if not") applies: nothing to migrate.

## Decision

Pin `methodology_version: "5.0.0"` in `transitrix.yaml` (and the three view
files carrying a concrete pin: `views/actions-tree/portfolio-all.actions-tree.transitrix.yaml`,
`views/glossary/full.glossary.transitrix.yaml`,
`views/rules-in-force/all.rules-in-force.transitrix.yaml`).

**Proposed — not yet ratified.** Per `method/08-governance.md` §2, an
`author: agent` record stays `proposed` until a human flips it to `accepted`;
an agent may never self-ratify.

## Consequences

- On ratification, the model is validated against 5.0.0 semantics. No
  codemod applies — confirmed above.
- Until ratified, `main` runs on a pin whose decision record is unratified —
  the same interim condition every prior pin recorded.
- If a future modelling decision adopts the `reqif` package, its own
  `transition`/`revise`/`history`/`suspect` commands are unavailable from
  this pin forward; use core's agreement axis for lifecycle tracking instead.
