# Operations — acme_corp

The **operational layer** for the team applying Transitrix to the `acme_corp` model. Distinct from the model itself (`canon/`, `field/`, `codex/`) — this folder is where the team records the decisions it has made about its own setup and the units of work it currently has in flight.

> Convention canon: [`method/team-operations.md`](../../../method/team-operations.md). This README is the **local** rules — it adapts the convention to how the `acme_corp` team works, and it should fit on one screen.

## Layout

```
operations/
├── README.md            # this file — local rules
├── feedback.md          # FB-NNNN entries — upstream feedback register (one file)
├── config/              # environment-level settings (scan-sources.yaml, …)
├── decisions/           # ADR-NNNN-<slug>.md — Architecture Decision Records
├── users/               # per-user state — one subfolder per GitHub username
│   └── <github-username>/
│       └── settings.md  # user preferences (YAML frontmatter)
└── work-items/          # WI-NNNN-<slug>.md — Work Items
```

## File shapes

- **ADR — Architecture Decision Record.** A short, append-only record of a decision about how the team runs the model. Once `status: accepted` the body is immutable; a later decision that changes course is a **new** ADR that names this one in its `superseded_by:` field. Schema: [`method/team-operations.md`](../../../method/team-operations.md) §3.1. Template: [`../.templates/operations/ADR-template.md`](../.templates/operations/ADR-template.md).

- **WI — Work Item.** A short record of a piece of work the team has in flight or queued. Mutable while active; `closed` when done — not deleted. Schema: [`method/team-operations.md`](../../../method/team-operations.md) §3.2. Template: [`../.templates/operations/WI-template.md`](../.templates/operations/WI-template.md).

- **FB — Feedback Record.** A short record of a methodology-directed finding — the landing place for `FINDINGS.md`'s `escalate-methodology` route. One file (`feedback.md`), not one-per-record: a checklist index at the top, one block per entry below. Anonymised at authoring time — generic limitation only, no element IDs, no organisation-identifying detail. Schema: [`method/02-team-operations.md`](https://github.com/transitrix/methodology/blob/main/method/02-team-operations.md) §3.3.

- **Per-user settings** (`users/<github-username>/settings.md`). User preferences: output language, report format, ingest focus layers, and any adopter-specific fields. Created on first interaction with a new user; updated in place. Template: [`../.templates/operations/settings-template.md`](../.templates/operations/settings-template.md).

- **Environment config** (`config/`). Environment-level files shared across all users — e.g. `scan-sources.yaml` (reg-intel scanner watch-list). Not a notation file; not zoned. Edited by the administrator, not by individual users.

## What goes where — local rules

| Situation | File shape |
|---|---|
| The team agreed on a way the repo or model is set up (a versioning pin, a naming override, a process choice) | **ADR** in `decisions/` |
| Someone is doing a piece of work that touches one or more model entities (filling in capability assessments, drafting a view, refactoring a relation set) | **WI** in `work-items/` |
| The notation or spec itself has a gap, friction, or suggestion — not a data problem | **FB** entry in `feedback.md` |
| An architectural problem about the modelled enterprise (e.g. a defect in a process, a risk in a system) | **NOT here** — model it as an `ASSESSMENT` in canon (ArchiMate Assessment); the former model-side `issues` notation was retired (2026-06-07) |
| A long discussion or proposal that has not landed on a decision | The pull-request that opens the candidate ADR — not a separate file here |

## Linking into the model — `relates_to:`

Both ADR and WI carry an optional `relates_to:` list of model entity IDs (Goals, Capabilities, Activities, …). That is the only link from operations into the model. The model **never** links back — nothing in `canon/` references an ADR or a WI.

`relates_to:` entries use the canonical ID grammar from [`notations/IDS_AND_REFERENCES.md`](../../../notations/IDS_AND_REFERENCES.md) §3. Unresolved IDs are treated as warnings, not errors — the doc-lint does not validate `operations/`.

Feedback Records do **not** carry `relates_to:` — the shape is anonymised by design, so an entry never names a model ID in the first place.

## Local flow

- **Opening an ADR.** Open a PR with `status: proposed`. Discussion lives on the PR. On merge the status flips to `accepted`. Owner: Valerii (sole maintainer of `acme_corp` today).
- **Superseding an ADR.** Open a new ADR; in the same PR set the old ADR's `status: superseded` and `superseded_by:`. The old body is otherwise untouched.
- **Opening a Work Item.** Anyone on the team may open a WI with `status: proposed` or `status: in_progress`. Update the status as the work moves. On completion set `status: done` (outcome recorded in body) or `status: closed` (won't do / withdrawn).
- **Writing a Feedback entry.** Append a checklist line to `feedback.md`'s `## Register` plus its block below, following the scrub discipline in `FINDINGS.md` §2 step 3 — no model content, no element IDs, no organisation-identifying detail. Update `status`/`upstream` in place as the entry moves; the checkbox flips to `[x]` at `closed` or `wont-fix`.

## Numbering

Sequence is per-folder, monotonically increasing, four-digit zero-padded (`ADR-0001`, `WI-0042`). When opening a new file pick the next free number. `FB-…` is the exception — its sequence is per-*file* (there is only one, `feedback.md`), not per-folder.
