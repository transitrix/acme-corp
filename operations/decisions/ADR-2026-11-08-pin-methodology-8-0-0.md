---
id: ADR-2026-11-08-pin-methodology-8-0-0
title: "Propose methodology 8.0.0 for the reference model"
status: proposed
date: "2026-11-08"
author: agent
source: ad-hoc
relates_to: []
superseded_by: null
---

## Context

Methodology [PR #662](https://github.com/transitrix/methodology/pull/662)
prepares a MAJOR release for closed relation enum expansion and stricter
optional-field and intake-profile tooling. Version 8.0.0 is not released.
The source recipe changes only the manifest pin; manual compatibility review
and release-qualified tooling remain necessary before adoption.

The current accepted 7.0.0 model decision and its original validation limitations
remain historical evidence. This proposal does not alter them or claim that
previously unvalidated files are validated by the new pin.

## Decision

Propose `methodology_version: "8.0.0"` as the required reference-adopter companion
to the source release preparation. Keep this change draft and unmerged until
the release, migration review, exact-tool checks and human ratification are
complete. The branch pin is a proposal, not an upgrade in force.

## Consequences

- Review capability stage/tags, technical capability payloads/windows/references,
  capability-map configuration and explicit profile ownership/layout using the
  7.0-to-8.0 recipe. Preserve originals and unknown content; no implicit defaults,
  inferred reporting or automatic store split is permitted.
- Vocabulary/specs, vendored linter, ingest presets and skill bundle must be
  reconciled with the reviewed release before acceptance. No install or intake
  is performed by this PR.
- Studio PR #754 prepares 3.10.0 / CLI 2.13.0 / diagrams 1.17.0. Methodology's
  skill pins the exact candidate source and blocks until matching artifact
  integrity and qualification exist; this ADR supplies no runtime evidence.
- Only the proposed manifest pin and this ADR change. Existing records,
  historical decisions and model bytes remain preserved. Acceptance requires a
  separate human-reviewed decision; do not self-accept this record.
