# `canon/verifications/`

`VERIFICATION` element primitives. The folder sits at the canon-zone root alongside [`../assertions/`](../../../canon/assertions/), not under `canon/elements/`.

Schema, vocabularies, and how verification relates to assertion: [`notations/elements/27-verification.md`](https://github.com/transitrix/methodology/blob/v7.0.0/notations/elements/27-verification.md).

## What Acme carries here

| Verification | Requirement | Outcome |
|---|---|---|
| [`VERIFICATION-ARCHIVE-PURGE-TEST-1`](../../../canon/verifications/VERIFICATION-ARCHIVE-PURGE-TEST-1.yaml) | `REQUIREMENT-GDPR-DATA-ERASURE-1` | **fail** — archive sweep not in production |
| [`VERIFICATION-PORTABILITY-EXPORT-TEST-1`](../../../canon/verifications/VERIFICATION-PORTABILITY-EXPORT-TEST-1.yaml) | `REQUIREMENT-GDPR-PORTABILITY-1` | pass |

Every other requirement has no verification yet, so `REQ-VERIF-COVERAGE-001` fires on it.

## File convention

`<id>.yaml`, one verification per file, named by its canonical ID.
