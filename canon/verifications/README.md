# `canon/verifications/`

`VERIFICATION` element primitives — the record that a requirement was checked: by what method, under what protocol, with what result and outcome. The folder sits at the canon-zone root alongside [`../assertions/`](../assertions/), not under `canon/elements/`.

Schema and the method / outcome vocabularies: [`notations/elements/27-verification.md`](../../../../notations/elements/27-verification.md) §2, §3.

## Verification is not assertion

The two catalogues answer different questions about the same requirement and are deliberately independent:

| | Question | Element |
|---|---|---|
| **Compliance** | does the organisation claim a subject satisfies this obligation? | `ASSERTION` — [`../assertions/`](../assertions/) |
| **Engineering V&V** | was it actually checked, how, and what happened? | `VERIFICATION` — here |

A requirement can carry a compliance claim with no verification evidence, or the reverse. Where both exist they should agree — and on `REQUIREMENT-GDPR-DATA-ERASURE-1` they do: the assertion records the archive gap as `non_compliant`, the verification records the same gap as an outcome of `fail`.

## What Acme carries here

| Verification | Requirement | Outcome |
|---|---|---|
| [`VERIFICATION-ARCHIVE-PURGE-TEST-1`](VERIFICATION-ARCHIVE-PURGE-TEST-1.yaml) | `REQUIREMENT-GDPR-DATA-ERASURE-1` | **fail** — archive sweep not in production |
| [`VERIFICATION-PORTABILITY-EXPORT-TEST-1`](VERIFICATION-PORTABILITY-EXPORT-TEST-1.yaml) | `REQUIREMENT-GDPR-PORTABILITY-1` | pass |

Every other requirement has no verification yet, so `REQ-VERIF-COVERAGE-001` fires on it — the V&V half of the coverage read.

## File convention

`<id>.yaml`, one verification per file, named by its canonical ID.
