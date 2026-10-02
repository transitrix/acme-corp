---
id: ADR-2028
title: "Adopt methodology 7.0.0 for the acme-corp model"
status: accepted
date: "2026-09-26"
author: agent
source: ad-hoc
relates_to: []
superseded_by: null
---

## Context

Methodology 7.0.0 is released with an ACTION numeric compatibility boundary and
additive numeric risk authoring. The initial companion change pinned the release
after its numeric migration postcheck, but deliberately left this agent-authored
decision proposed until a maintainer could review the whole model.

That review found adopter defects beyond the manifest: time-varying capability
and application attributes were duplicated inline instead of living in history
sidecars, and explanatory Markdown files occupied admitted model zones. PR #95
reconciled those defects while preserving existing IDs and dated values.

## Decision

Retain `methodology_version: "7.0.0"` and accept the reconciled model at merge
commit `43eba159bf937a306285b05b319d58ce02d3ca33`.

The migration consists of the manifest pin plus the contract-determined model
repairs in PR #95. It is not a manifest-only migration. Valerii ratified this
decision on 2026-10-02 after reviewing the exact source head and its validation
and preservation evidence.

## Consequences

- Existing model IDs, issued decisions, assertions and reference history remain
  preserved. The previously referenced `ROLE-OPS-2` is now admitted explicitly.
- The released 6-to-7 migration check reads 141 YAML files and checks 15 ACTION
  records with no numeric errors.
- Whole-model CLI 2.10.0 reads all 147 discovered files, validates 86 and reports
  61 as unvalidated, with no read failures or exclusions. CLI 2.11.0 validates
  110 and reports 37 as unvalidated.
- Both CLI releases retain five capability-map errors because the validator
  requires inline `current_maturity` while the 7.0 contract requires that value
  exclusively in a history sidecar. This is an accepted validator limitation,
  not an unresolved model decision; its minimal reproduction is tracked in
  `transitrix/methodology#635`.
