---
id: ADR-2026-08-27-pin-methodology-4-2-0
title: "Pin methodology_version to 4.2.0 for the acme-corp model"
status: proposed
date: "2026-08-27"
author: agent
source: ad-hoc
relates_to:
  - ADR-2026-08-25-pin-methodology-4-0-0
  - ADR-2026-08-23-pin-methodology-3-7-0
  - ADR-0007
supersedes: ADR-2026-08-25-pin-methodology-4-0-0
superseded_by: null
---

## Context

The methodology released [4.2.0](https://github.com/transitrix/methodology/releases/tag/v4.2.0)
— a **MINOR** increment over 4.1.0. This repository never pinned 4.1.0; the
current pin is 4.0.0. Two MINOR tags sit between 4.0.0 and 4.2.0
(`assembled_on` relation tests in 4.1.0; the `STANDARD` codex TYPE in 4.2.0).
Neither bump is breaking. There is no migration recipe for 4.0.0 → 4.2.0.

`STANDARD` is an externally issued technical standard (SDO), distinct from
`REGULATION` and from `INTERNAL_STANDARD`. Pinning does not require this
repository to admit a `STANDARD` artefact.

**Recorded, not resolved, by this ADR:** the same `AGENTS.md` / actual-practice
tension prior pin records named. Not this record's to settle.

## Decision

Pin `methodology_version: "4.2.0"` in `transitrix.yaml`.

**Proposed — not yet ratified.** Per `method/08-governance.md` §2, an
`author: agent` record stays `proposed` until a human flips it to `accepted`;
an agent may never self-ratify.

## Consequences

- On ratification, the model is validated against 4.2.0 semantics. No
  codemod applies.
- Until ratified, `main` runs on a pin whose decision record is unratified —
  the same interim condition the 4.0.0 pin recorded.
- Admitting a `STANDARD` artefact remains a separate modelling choice.
