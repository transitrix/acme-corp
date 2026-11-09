# Knowledge Store example

This standalone bundle shows the `knowledge-store` profile with fictional Acme
material. The Acme team repository uses the ordinary `ingest` profile. Each
profile has its own repository root.

| Open | What it shows |
| --- | --- |
| [Reconciliation run card](example/sources/reconciliation-run.md) and [uploaded original](example/sources/reconciliation-run.original.md) | An upload and its card share a stem in `sources/`. The card records the original's path and SHA-256. |
| [CFO interview card](example/sources/cfo-onboarding-interview.md) | A document already available elsewhere gets a card with a link to its exact revision. The interview stays in Acme's `field/`. |
| [Knowledge index](example/knowledge/index.md) | A reviewed finding in `knowledge/` cites both pieces of evidence. |

## Run the example

Copy the **contents** of [`example/`](example/) into a new directory outside
the Acme checkout. Include the hidden files and directories shown in GitHub.
From that directory, initialise Git and run the two checks below. Use the
[Ingest CLI from a current methodology checkout](https://github.com/transitrix/methodology/tree/main/packages/ingest-cli#install)
for the profile check. The Knowledge Store linter requires Python and PyYAML.
Replace `/path/to/methodology` with your methodology checkout path.

```sh
git init
transitrix-intake-profile check . --profile knowledge-store
python /path/to/methodology/tools/knowledge_store_lint.py .
```

The profile check should report `knowledge-store`. The linter checks the
source cards, finding, and uploaded file's hash. For storage and migration
rules, see the [Knowledge Store pattern](https://github.com/transitrix/methodology/blob/main/patterns/knowledge-store.md#preserve-uploaded-originals).
