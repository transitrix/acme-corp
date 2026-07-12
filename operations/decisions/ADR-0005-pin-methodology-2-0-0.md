---
id: ADR-0005
title: "Pin methodology_version to 2.0.0 for the acme-corp model"
status: accepted
date: "2026-07-12"
author: agent
source: ad-hoc
relates_to:
  - ADR-0004
superseded_by: null
---

## Context

The methodology released [2.0.0](https://github.com/transitrix/methodology/releases/tag/v2.0.0)
— a breaking release completing the view-purity migration for the Goals Tree and
Action Schedule notations (both now project over the canonical element catalogue;
inline `goals[]`/`actions[]` are no longer accepted). [ADR-0004](ADR-0004-defer-methodology-2-0-migration.md)
deferred merging the migration ([acme-corp#29](https://github.com/transitrix/acme-corp/pull/29))
until this release existed on methodology `main`; it now does.

The 1.0 → 2.0 migration recipe (`migrations/1.0-to-2.0/` in the source methodology
repository) was applied: `eu-strategy.dgca.transitrix.yaml` (wrong notation/extension
for a Goals Tree document, also carrying an inline `goals[]` array) replaced by
`eu-strategy.goals.transitrix.yaml` (pure `view_config` projection) plus the
previously-missing standalone `GOAL-EU-COMPLIANCE-1.yaml` element; the former inline
GDPR remediation action network (`gdpr-remediation.dgca.transitrix.yaml`) extracted
to nine standalone `ACTION-*` element files plus a pure-projection
`gdpr-remediation.action.transitrix.yaml`. `ACTION-EU-COMPLIANCE-1` and
`ACTION-GDPR-REMEDIATION-1` had also been authored independently on `main` in the
interim (richer content — real descriptions, a `delivers_changes` link); those
versions were kept over the migration branch's bare drafts. Post-migration
`migrations/1.0-to-2.0/validate.mjs` exits clean.

## Decision

Pin `methodology_version: "2.0.0"` in `transitrix.yaml`.
**Accepted** by maintainer 2026-07-12 after the migration recipe was applied and
acme-corp#29 merged.

## Consequences

- The model is validated against 2.0.0 semantics; Goals Tree and Action Schedule
  views are pure projections, no inline element arrays remain.
- Supersedes the effective scope of ADR-0003 (1.0.0 pin) and closes out ADR-0004's
  deferral for methodology-version purposes.
- Known pre-existing gap, not introduced by this migration: goal parent-hierarchy
  (e.g. `GOAL-EU-COMPLIANCE-1` → `GOAL-EU-1`) is recorded neither inline nor as a
  `REL-*-goal_parent` file for any of the five goals in `eu-strategy.goals.transitrix.yaml`.
  Worth a follow-up work item if the rendered tree needs to show hierarchy.
