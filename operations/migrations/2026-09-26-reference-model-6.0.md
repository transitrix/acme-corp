# Reference-model migration for methodology 6.0.0

This record preserves the identifiers used before the model repair. The input
revision is `46d01f662d7c2eb5601b5aa60f06ce7a0b521a39`; the methodology remains
pinned to 6.0.0. It does not ratify the separately proposed ADR-2027.

| Previous identifier | Current identifier | Change |
|---|---|---|
| `APPLICATION-REACT` | `APPLICATION-REACT-1` | Complete the required terminal integer; retain the React software subject. |
| `TECHNOLOGY_SERVICE-NODEJS` | `APPLICATION-NODEJS-1` | Model the versioned Node.js runtime software as an application platform, rather than a provided technology service. |

Both software records use the application envelope and live under
`canon/elements/03_application/applications/`. This does not introduce a separate
host, running service instance or a new dependency. The descriptions retain the
original model text; historical classification and original bytes remain at the
input revision above.

`RELEASE-APPLICATION-REACT-1.of` now names `APPLICATION-REACT-1`.
`RELEASE-TECHNOLOGY_SERVICE-NODEJS-1.of` now names `APPLICATION-NODEJS-1`.
The latter release keeps its existing identifier: its middle segments are an
historical label, not the subject TYPE. The two release IDs, versions, release
dates, E-commerce predecessor chain and all `assembled_on` endpoints/windows
remain unchanged. No assertion, issued-document or decision history is rewritten.

Eight files previously combined Markdown frontmatter with prose while carrying
a `.yaml` extension. Each is now one YAML mapping; its prose is preserved in
`description`. No model object or relation is removed. Every known working
reference to the two old subject identifiers is updated in this same migration;
this mapping remains the durable lookup for historical references.

The local model linter checks YAML, identifiers, atomicity, references and its
implemented semantic rules. A successful run does not certify complete downstream
validator coverage, installed tooling, release publication or decision ratification.
