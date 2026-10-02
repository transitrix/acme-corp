---
id: ADR-2028
title: "Prepare the model for methodology 7.0.0"
status: proposed
date: "2026-09-26"
author: agent
source: ad-hoc
relates_to: []
superseded_by: null
---

## Context

Methodology 7.0.0 has a prepared release with an ACTION numeric compatibility
boundary and additive numeric risk authoring. This proposal accompanies the
reference model pin; it does not claim that the release has been published.

## Decision

After 7.0.0 publication and maintainer ratification, adopt
`methodology_version: "7.0.0"`. The migration changes the manifest only. The
release-specific postcheck read 134 YAML files and checked 15 ACTION records
without numeric errors. That bounded check is not whole-model acceptance.

## Consequences

Original model content and historical decisions are preserved. Complete the
whole-model check with a compatible released validator before ratification.
Until then this decision remains proposed and the companion PR must not merge.
