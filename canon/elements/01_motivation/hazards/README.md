# `canon/elements/01_motivation/hazards/`

`HAZARD` element primitives, on the ArchiMate 3.2 **motivation** layer. Peer catalogue to [`../requirements/`](../requirements/), [`../constraints/`](../constraints/) and [`../risk-controls/`](../risk-controls/).

Schema and the severity / probability / risk-evaluation vocabularies: [`notations/elements/28-hazard-risk-control.md`](../../../../../../notations/elements/28-hazard-risk-control.md).

## What Acme carries here

Acme is not a medical-device maker; the risk vocabulary is applied here to privacy hazards, where the harm lands on the data subject.

| Hazard | Control | Status |
|---|---|---|
| [`HAZARD-ARCHIVE-RETENTION-1`](HAZARD-ARCHIVE-RETENTION-1.yaml) — data survives erasure in the cold-storage archive | [`RISK_CONTROL-ARCHIVE-PURGE-1`](../risk-controls/RISK_CONTROL-ARCHIVE-PURGE-1.yaml) | mitigated, residual ALARP; verification currently **fails** |
| [`HAZARD-CARRIER-PII-EXPOSURE-1`](HAZARD-CARRIER-PII-EXPOSURE-1.yaml) — excess personal data on the carrier label | — | no control yet, so `HAZ-RISKCTL-COVERAGE-001` fires |

## File convention

`<id>.yaml`, one hazard per file, named by its canonical ID.
