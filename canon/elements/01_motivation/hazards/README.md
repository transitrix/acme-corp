# `canon/elements/01_motivation/hazards/`

`HAZARD` element primitives — a source of harm and the hazardous situation that gives rise to it, on the ArchiMate 3.2 **motivation** layer. Peer catalogue to `../requirements/`, `../constraints/` and `../risk-controls/` — not nested under any of them.

Schema and vocabularies (severity / probability / risk evaluation): [`notations/elements/28-hazard-risk-control.md`](../../../../../../notations/elements/28-hazard-risk-control.md) §2, §4.

## What Acme carries here

Acme is not a medical-device maker; the ISO 14971 risk vocabulary is applied here to **privacy hazards**, where the harm lands on the data subject rather than a patient. The shape of the chain is identical — hazard → control → requirement → verification — which is the point: the risk spine is domain-neutral.

| Hazard | Control | Status |
|---|---|---|
| [`HAZARD-ARCHIVE-RETENTION-1`](HAZARD-ARCHIVE-RETENTION-1.yaml) — data survives erasure in the cold-storage archive | [`RISK_CONTROL-ARCHIVE-PURGE-1`](../risk-controls/RISK_CONTROL-ARCHIVE-PURGE-1.yaml) | mitigated, residual risk ALARP; verification currently **fails** |
| [`HAZARD-CARRIER-PII-EXPOSURE-1`](HAZARD-CARRIER-PII-EXPOSURE-1.yaml) — excess personal data on the carrier label | — | **deliberate gap**: no control yet, so `HAZ-RISKCTL-COVERAGE-001` fires |

## File convention

`<id>.yaml`, one hazard per file, named by its canonical ID.
