# `canon/elements/01_motivation/risk-controls/`

`RISK_CONTROL` element primitives — the measures that address the hazards in `../hazards/`, on the ArchiMate 3.2 **motivation** layer.

Schema and the ISO 14971 three-tier control hierarchy: [`notations/elements/28-hazard-risk-control.md`](../../../../../../notations/elements/28-hazard-risk-control.md) §3, §4.

## The join into the requirement spine

`satisfies:` is what keeps the risk chain and the requirement chain as **one** model rather than two parallel ones: a control is realised as an existing `REQUIREMENT`, and that requirement's `VERIFICATION` is therefore also the control's verification. `RISKCTL-VERIF-COVERAGE-001` reads that join from the control's side — it fires when a control's requirement has no verification that reached `pass` or `fail`.

Acme carries one control today: [`RISK_CONTROL-ARCHIVE-PURGE-1`](RISK_CONTROL-ARCHIVE-PURGE-1.yaml), satisfying [`REQUIREMENT-GDPR-DATA-ERASURE-1`](../requirements/REQUIREMENT-GDPR-DATA-ERASURE-1.yaml).

## File convention

`<id>.yaml`, one control per file, named by its canonical ID.
