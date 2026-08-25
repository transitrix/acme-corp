---
id: ADR-2026-08-23-pin-methodology-3-7-0
title: "Pin methodology_version to 3.7.0 for the acme-corp model"
status: proposed
date: "2026-08-23"
author: agent
source: ad-hoc
relates_to:
  - ADR-0006
  - ADR-0007
superseded_by: ADR-2026-08-25-pin-methodology-4-0-0
---

## Context

The methodology released [3.7.0](https://github.com/transitrix/methodology/releases/tag/v3.7.0)
— a **MINOR** increment over the previously pinned 3.6.0, adding the
`PRINCIPLE` codex TYPE (a self-held rule with no stated issuing authority or
conformance test, distinct from `POLICY` and `INTERNAL_STANDARD`) and
widening `REQUIREMENT.derived_from` to accept it. Per the release notes, the
change is purely additive: no existing field became required, no existing
TYPE's shape changed, and no previously-valid repository needs updating. No
migration recipe exists or is required — `migrations/` in the source
repository carries recipes only across MAJOR boundaries, and the
compatibility promise in `notations/CONTRACT.md` §10 is that a MINOR release
never breaks a previously-valid repository.

This pin lands together with a worked example that uses the new TYPE — a
`PRINCIPLE` artefact under `codex/internal/`, a `REQUIREMENT` deriving from
it, an `ASSERTION` closing the compliance chain, and a compliance-impact view
resolving it — in the same change set, so unlike
[ADR-0006](ADR-0006-pin-methodology-3-6-0.md) this record is contemporaneous
with the pin, not a backfill.

**Recorded, not resolved, by this ADR:** `AGENTS.md` §12 states the agent
"never edits `transitrix.yaml` to change the `methodology_version` pin" —
that step is described there as belonging to the administrator. The pin was
nonetheless applied by an agent here, consistent with every prior pin bump in
this repository's history ([ADR-0002](ADR-0002-pin-methodology-0-5-0.md)
through [ADR-0006](ADR-0006-pin-methodology-3-6-0.md), plus the six
unrecorded ones [ADR-0007](ADR-0007-record-unrecorded-methodology-pins.md)
backfills) and with the task that motivated this change. The tension between
stated doctrine and actual practice is not this record's to settle; it is
named here so a reader does not have to re-derive it, the same posture
ADR-0006 and ADR-0007 already took toward it.

## Decision

Pin `methodology_version: "3.7.0"` in `transitrix.yaml`.

**Proposed — not yet ratified.** Per `method/08-governance.md` §2, an
`author: agent` record stays `proposed` until a human flips it to `accepted`;
an agent may never self-ratify.

## Consequences

- On ratification, the model is validated against 3.7.0 semantics. As a
  MINOR increment with no recipe, no codemod is required beyond the worked
  example added alongside this pin.
- Until ratified, `main` runs on a pin whose decision record is unratified —
  the same interim condition ADR-0006 recorded and that was later resolved by
  a human reviewer.
- The `AGENTS.md` §12 / actual-practice gap noted above is not closed by this
  record; it remains an open question for whoever next revises that file.
