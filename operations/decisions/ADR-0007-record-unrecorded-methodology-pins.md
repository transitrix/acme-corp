---
id: ADR-0007
title: "Record the six methodology_version pins applied between 2.1.0 and 3.5.0 without a decision record"
status: proposed
date: "2026-08-18"
author: agent
source: ad-hoc
relates_to:
  - ADR-0005
  - ADR-0006
superseded_by: null
---

## Context

This repository's own [ADR-0001](ADR-0001-adopt-team-operations-convention.md)
commits the team to landing `methodology_version` pins as decision records in
`operations/decisions/`. Between [ADR-0005](ADR-0005-pin-methodology-2-0-0.md)
(the 2.0.0 pin, 2026-07-12) and [ADR-0006](ADR-0006-pin-methodology-3-6-0.md)
(the 3.6.0 pin) that did not happen. Six pins were applied to `transitrix.yaml`
with **no contemporaneous decision record of any kind**:

| Pin | Applied | Change |
|---|---|---|
| `2.1.0` | 2026-07-28 | MINOR over 2.0.0 |
| `3.0.0` | 2026-07-29 | **MAJOR** over 2.1.0 |
| `3.1.0` | 2026-08-01 | MINOR |
| `3.2.0` | 2026-08-07 | MINOR |
| `3.3.0` | 2026-08-08 | MINOR |
| `3.5.0` | 2026-08-15 | MINOR |

**This record is a retrospective acknowledgment, not a reconstruction.** It does
not invent six rationales or six dates for choices already made and already
merged; the reasoning behind each of those six pins was never written down, and
writing it now — after the fact, in the voice of a decision that was not
recorded when it was taken — would produce a decision log that reads as
complete while being partly fabricated. That is a worse outcome than an honest
gap. So: one record, stating what happened, naming what is not knowable from
here.

**What the gap is, and what it is not.** The gap is in the *record*, not
necessarily in the *work*. Two points are verifiable from the repository today
and are stated here because a future reader would otherwise have to re-derive
them:

- **The MAJOR crossing carried out its migration.** 3.0.0 removed the ISO 14971
  risk-management chain (`HAZARD`, `RISK_CONTROL`, the design-controls trace
  matrix) from the methodology's public core, with an on-disk recipe at
  [`migrations/2.1-to-3.0/`](https://github.com/transitrix/methodology/tree/main/migrations/2.1-to-3.0).
  The substance of that migration was applied to this repository in
  [acme-corp#49](https://github.com/transitrix/acme-corp/pull/49), which
  scrubbed the chain and kept the `VERIFICATION` spine; the pin followed it the
  next day. The recipe's own post-migration validator
  (`migrations/2.1-to-3.0/validate.mjs`) exits clean against this repository as
  of 2026-08-18. What is missing for 3.0.0 is the decision record, not the
  migration.
- **3.3.0 → 3.5.0 did not skip a release.** Methodology 3.4.0 has a CHANGELOG
  entry but was never tagged; 3.5.0 folds it in explicitly. The absence of a
  `3.4.0` pin here is therefore correct, not an omission.

The remaining four pins (2.1.0, 3.1.0, 3.2.0, 3.5.0 as MINOR increments) needed
no migration recipe: `notations/CONTRACT.md` §10 promises that a MINOR release
never breaks a previously-valid repository, and `migrations/` carries recipes
only across MAJOR boundaries.

**Not established here: who decided, and on what basis.** The commits carry
differing author identities, and this record deliberately does not attribute
the six decisions to any person or process on that evidence — commit authorship
does not establish who made a decision. That question is not answerable from
this repository, and guessing at it would be the same fabrication this record
exists to avoid.

**Why it went unnoticed** is a separate, mechanical matter: nothing in CI
requires a `methodology_version` change to arrive with a decision record, so
every one of these six passed a clean build. That finding, and the wiring that
would close it, are reported upstream and are deliberately not addressed in this
record — see *Consequences*.

## Decision

Acknowledge, as a single retrospective record, that the six `methodology_version`
pins listed above were applied to this repository without contemporaneous
decision records, and that none of them was reverted.

Each pin held until its successor replaced it; the chain terminates in the
current `3.6.0` pin, which is recorded by [ADR-0006](ADR-0006-pin-methodology-3-6-0.md)
and was built on top of all six. The model in this repository has been validated
against 3.x semantics throughout and remains so. **No pin is changed, proposed,
or re-decided by this record** — `transitrix.yaml` is untouched by the change
that introduces it.

**Proposed — not yet ratified.** Per
[`method/08-governance.md`](https://github.com/transitrix/methodology/blob/main/method/08-governance.md)
§2, an `author: agent` record stays `proposed` until a human flips it to
`accepted`; an agent may never self-ratify. What ratification settles here is
narrower than for a normal ADR: not whether to adopt something, but whether this
account of the gap is accurate and whether the six pins stand as applied. There
is no alternative course of action being withheld — the only thing a ratifier
could do instead is dispute the account or order a revert.

## Consequences

- The decision log reads continuously again: [ADR-0005](ADR-0005-pin-methodology-2-0-0.md)
  (2.0.0, the last record before the gap) → this record (the gap itself,
  2.1.0 through 3.5.0) → [ADR-0006](ADR-0006-pin-methodology-3-6-0.md) (3.6.0,
  the first record after it). A reader following the chain no longer has to
  infer that six pins happened in between.
- The log is honest about being incomplete. Anyone reading this repository as a
  reference for the ADR convention should read this record as the worked example
  of what to do about a gap — one acknowledgment — rather than as evidence that
  the convention was followed throughout. It was not.
- The rationale for those six pins remains unrecoverable. If a future change
  needs to know why a particular version was adopted when it was, the answer is
  not in this repository and this record does not supply one.
- **Not addressed here, deliberately:** (a) no CI guard requires a pin change to
  carry a decision record — `scripts/check-adl.mjs` guards record immutability
  and the agent-authorship gate, not pin/record correspondence, and this
  repository does not yet wire that script at all; (b) `operations/README.md`'s
  Local flow states that an ADR's status flips to `accepted` **on merge**, which
  for an `author: agent` record contradicts the governance doctrine cited above.
  Both are reported upstream and are held pending a doctrine question about
  whether an unattended agent should be moving this pin at all. Patching either
  one inside this record would bundle a process change into a retrospective
  acknowledgment.
