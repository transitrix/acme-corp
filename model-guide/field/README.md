# `field/` — Field zone

Field retains evidence gathered about the organisation, including interview notes, survey responses, and observations. The zone model is defined in the methodology canon, `notations/CONTRACT.md` §5.

Field preserves what people said or observed, including contradictions. Canon records can cite Field evidence via `derived_from:` after a separate review (`CONTRACT.md` §6).

Each artefact carries the admission record (`zone: field`, `admitted_at`, `admitted_by`, `gate_checks: { provenance: … }`) and is one `<ID>.yaml` per file, named by its canonical ID.

| Folder | Holds | ID TYPE |
|---|---|---|
| `interviews/` | recorded interviews and their notes | `INTERVIEW` |
| `surveys/` | survey instruments and responses | `SURVEY` |
| `observations/` | direct observations of work, systems, or events | `OBSERVATION` |
| `drafts/` | working drafts not yet admitted to canon | `DRAFT` |

TYPE registry: the methodology's `notations/IDS_AND_REFERENCES.md` §3.4.

## Add an interview

Submit new Field records through [Ingest](https://github.com/transitrix/methodology/tree/main/transitrix/skills/ingest#add-a-field-record).
Acme declares the `ingest` profile in [`_intake/profile.json`](../../_intake/profile.json).
Open your own clone and start Ingest (for example, with `/transitrix:ingest`).
Try either route below using the same fictional interview.

### From a file

Save the following as `finance-interview.md` and attach it in the Ingest session
or place it in `_intake/inbox/` in your clone.

```text
I interviewed Acme's finance operations lead on 2026-04-16 on a video call
about month-end close. I took these notes during the call.
The lead said the team manually compares CRM and order-system totals
before signing off the close. Mismatches are tracked in a spreadsheet.
```

Send this request in the Ingest session.

> Add my notes in `finance-interview.md` to Field as an interview.

### From chat

Paste the request and notes together in the Ingest session.

> Add my interview notes to Field. I interviewed Acme's finance operations
> lead on 2026-04-16 on a video call about month-end close. I took these
> notes during the call. The lead said the team manually compares CRM and
> order-system totals before signing off the close. Mismatches are tracked
> in a spreadsheet.

Ingest prepares the working file for chat notes and applies the same checks to
both inputs. Before publication, it checks who recorded the evidence, when and
in what context, scans for sensitive data, and verifies that the team can
retrieve the evidence independently of the contributor's workspace. When the
shared Field record carries the evidence in full, that record provides access.
If the team needs a separate original, record a link to its specific revision in
organisation-managed storage and check that teammates can open it. Local
`_intake/` working files are excluded from Git and cannot provide team access.

An authorised contributor's explicit request to add their own notes is enough
to publish once those checks pass and Ingest has preserved the substance. See
the existing [CFO onboarding interview](../../field/interviews/INTERVIEW-cfo-onboarding-2026-04-15-1.yaml)
for the shape of a self-contained Field record.
