---
id: ADR-0003
title: "Pin methodology_version to 1.0.0 for the acme-corp model"
status: proposed
date: "2026-07-06"
author: agent
source: ad-hoc
relates_to: []
superseded_by: null
---

## Context

The methodology released 1.0.0. The Discovery job, comparing the pinned
`methodology_version` against the latest released tag on the source repository,
found this repository behind and prepared this record. Per the architecture
decision log, a consequential change made by an agent leaves a `proposed`
decision for human ratification, not an unannounced edit.

## Decision

Pin `methodology_version: "1.0.0"` in `transitrix.yaml`.
(Proposed — not in force until a maintainer ratifies this record.)

## Consequences

- Once ratified, the model is validated against 1.0.0 semantics; any
  applicable migration notes for the bump apply (`migrations/` in the
  source methodology repository).
- For a MINOR or PATCH increment with no migration recipe, no codemod is required.
- For a MAJOR increment, run the migration recipe before accepting this ADR.
