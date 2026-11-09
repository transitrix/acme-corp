# Canon placement repair for methodology 7.0.0

Release records now live under `canon/elements/05_implementation/releases/`.
The Node.js release needed an ID change because the underscore in its middle
segment violated the canonical grammar.

| Previous ID | Current ID |
| --- | --- |
| `RELEASE-TECHNOLOGY_SERVICE-NODEJS-1` | [`RELEASE-APPLICATION-NODEJS-1`](../../canon/elements/05_implementation/releases/RELEASE-APPLICATION-NODEJS-1.yaml) |

[The assembly relation](../../canon/relations/REL-ECOMM-1-NODEJS-1.yaml) now
uses the current ID. The Node.js application subject, release version and ship
date, and the relation's own ID and validity window carry forward.
