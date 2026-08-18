---
id: ADR-0006
title: "Pin methodology_version to 3.6.0 for the acme-corp model"
status: proposed
date: "2026-08-17"
author: agent
source: ad-hoc
relates_to:
  - ADR-0005
superseded_by: null
---

## Context

The methodology released [3.6.0](https://github.com/transitrix/methodology/releases/tag/v3.6.0)
— a **MINOR** increment over the previously pinned 3.5.0. No migration recipe
exists or is required for it: `migrations/` in the source repository carries
recipes only across MAJOR boundaries (`2.1-to-3.0`, `3.1-to-4.0`), and the
compatibility promise in `notations/CONTRACT.md` §10 is that a MINOR release
never breaks a previously-valid repository.

**The pin is already in force, ahead of this record.** `transitrix.yaml` was
bumped `3.5.0` → `3.6.0` on `main` by
[acme-corp#70](https://github.com/transitrix/acme-corp/pull/70), merged
2026-08-17 without an accompanying decision record. This ADR is therefore a
**backfill**: it documents a change that has already landed, rather than
proposing one that has not. That ordering is itself contrary to
[`method/08-governance.md`](https://github.com/transitrix/methodology/blob/main/method/08-governance.md)
§2, under which an agent may prepare a bounded upgrade PR but only a human may
ratify the accompanying ADR — "the worst an unattended agent can do … is leave a
proposal for a human to review, never a change already in force". The wider gap
this record surfaces (seven pin bumps since [ADR-0005](ADR-0005-pin-methodology-2-0-0.md)
with no decision record, and no CI guard requiring one) is reported separately
and is not decided here.

## Decision

Pin `methodology_version: "3.6.0"` in `transitrix.yaml`.

**Proposed — not yet ratified.** Ratification is the human gate: per
`method/08-governance.md` §2, an `author: agent` record stays `proposed` until a
human flips it to `accepted`, and an agent may never self-ratify. Note that what
ratification settles here is whether the already-applied pin *stands*, not
whether it is applied — reverting is the alternative, not withholding.

## Consequences

- On ratification, the model is validated against 3.6.0 semantics. As a MINOR
  increment with no recipe, no codemod is required and no model file changes.
- Until ratified, `main` runs on a pin whose decision record is unratified — the
  condition this repository's own [ADR-0001](ADR-0001-adopt-team-operations-convention.md)
  ("version pins … land as ADRs in `operations/decisions/`") exists to prevent.
- `operations/README.md` §"Local flow" currently states that an ADR's status
  flips to `accepted` **on merge**. For an `author: agent` record that conflicts
  with `method/08-governance.md` §2 and with `scripts/check-adl.mjs`, which
  rejects an `author: agent` record introduced already `accepted`. Merging this
  PR must therefore leave the status at `proposed`; the local wording is part of
  the separately-reported finding.
