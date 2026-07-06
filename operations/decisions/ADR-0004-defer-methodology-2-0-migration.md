---
id: ADR-0004
title: "Defer methodology 2.0.0 migration until an official release"
status: proposed
date: "2026-07-06"
author: agent
source: ad-hoc
relates_to: []
superseded_by: null
---

## Context

`transitrix.yaml` pins `methodology_version: "1.0.0"` per [ADR-0003](ADR-0003-pin-methodology-1-0-0.md).
The released methodology canon on `transitrix/methodology` `main` is also **1.0.0**
(`notations/CURRENT_VERSION.yaml`).

Draft PR [transitrix/acme-corp#29](https://github.com/transitrix/acme-corp/pull/29)
(`feat/view-purity-migration-2.0`) bumps the adopter to **2.0.0** and applies the
view-purity codemod (Goals Tree + Action Schedule). That work is a companion to
[methodology#327](https://github.com/transitrix/methodology/pull/327), which is still
**open** and not released. Merging #29 now would pin the demo corpus to a version
that does not exist on the methodology `main` branch and would conflict with the
1.0.0 fixes already merged via [#28](https://github.com/transitrix/acme-corp/pull/28).

## Decision

**Do not merge acme-corp #29** until methodology **2.0.0** is released on
`transitrix/methodology` `main` (expected via methodology#327 or its successor).
Keep #29 as a **draft** reference branch only. Track the follow-up work in
[WI-0002](../work-items/WI-0002-methodology-2-0-view-purity-migration.md).

## Consequences

- The demo adopter stays on 1.0.0 semantics; Studio validators and previews match
  the pinned version.
- #29 remains available as a starting point for the future migration but must be
  rebased and re-validated after methodology 2.0.0 ships.
- A new ADR will be required to ratify the `methodology_version` pin change when
  the migration actually runs (superseding the effective scope of ADR-0003 for
  version-pin purposes).
