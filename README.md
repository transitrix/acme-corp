# Acme Corp

Acme Corp is a growing e-commerce company — an online storefront and mobile shopping app, backed by order fulfilment, warehouse, and customer-support operations. The current plan is to triple revenue over three years, including launching in three EU markets, which brings a set of EU regulatory obligations (personal data handling, consumer protection) into scope alongside the growth.

This repository is Acme Corp's own enterprise architecture — the goals, capabilities, processes, applications, and obligations that make up how the company actually runs, kept as version-controlled text and updated as the company changes.


**Tooling:** [Transitrix Studio](https://transitrix.com/install/) for live notation preview; [Markdown Preview Mermaid Support](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid) for the Mermaid-based views.

---

This repository follows the [Transitrix methodology](https://github.com/transitrix/methodology).

## Model guide

Folder-level explanations and worked-example notes live under
[`model-guide/`](model-guide/), mirroring the `canon/` and `field/` paths they
describe. The model zones themselves contain only contract-admitted model
artefacts, as required by Methodology 7.0.

## Work with sources

Acme's team repository uses the ordinary `ingest` profile. To add a finance
interview, attach `finance-interview.md` and ask Ingest to add it to Field, or
paste the notes into chat with the same request. The
[Field walkthrough](model-guide/field/README.md#add-an-interview) gives both
prompts and shows what to include about the interview.

The [Knowledge Store example](model-guide/knowledge-store/) shows how a separate
workspace keeps source cards, uploaded originals, and curated findings.
