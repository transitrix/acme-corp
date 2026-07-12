---
id: WI-0002
title: "Apply methodology 1.0→2.0 view-purity migration (Goals + Action Schedule)"
status: done
opened: "2026-07-06"
closed: "2026-07-12"
owner: "vkgeorgia"
relates_to:
  - GOAL-EU-COMPLIANCE-1
---

## Outcome

Migrate acme-corp from methodology **1.0.0** to **2.0.0** using the official
`migrations/1.0-to-2.0/` recipe once it lands on `transitrix/methodology` `main`.
Goals Tree and Action Schedule views become pure projections (`view_config` only);
inline `goals[]` / `actions[]` move to standalone canon element files.

## Blocked on

- [methodology#327](https://github.com/transitrix/methodology/pull/327) merged and
  `notations/CURRENT_VERSION.yaml` bumped to **2.0.0** on methodology `main`. Done —
  [v2.0.0](https://github.com/transitrix/methodology/releases/tag/v2.0.0) released
  2026-07-12.
- Maintainer ratification of [ADR-0004](../decisions/ADR-0004-defer-methodology-2-0-migration.md)
  superseded by a new ADR accepting the 2.0.0 pin. Done —
  [ADR-0005](../decisions/ADR-0005-pin-methodology-2-0-0.md).

## Resolution

- Merged: [acme-corp#29](https://github.com/transitrix/acme-corp/pull/29).
- `ACTION-EU-COMPLIANCE-1`/`ACTION-GDPR-REMEDIATION-1` had been authored
  independently on `main` in the interim (richer — real descriptions, a
  `delivers_changes` link); kept those over #29's bare migration drafts.
  `eu-strategy.goals.transitrix.yaml` regenerated against `main`'s current inline
  data (which had grown to 5 goals and renamed "Enabling Goal" → "Project Goal"
  since #29 branched), not the stale 07-06 draft.

## Checklist

- [x] methodology 2.0.0 released; migration recipe available on `main`.
- [x] Rebase or recreate branch from `main`; resolve conflicts with #28 element files.
- [x] Run `node migrations/1.0-to-2.0/validate.mjs <acme-corp-root>` — exit 0.
- [ ] Run `transitrix validate --scope=repo` — clean. **Not run** — `@transitrix/cli`
      isn't installed in this environment; `validate.mjs`'s narrower check substituted.
- [x] File ADR ratifying `methodology_version: "2.0.0"` in `transitrix.yaml`.
- [x] Close or replace draft #29 with the validated migration PR.
