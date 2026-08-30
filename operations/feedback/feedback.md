# Feedback register

Upstream feedback for the Transitrix methodology — a generic-limitation-only
register of methodology-directed findings raised while working this repo. See
[`method/06-team-operations.md`](https://github.com/transitrix/methodology/blob/main/method/06-team-operations.md)
§3.2 for the record shape. Submission to `hello@transitrix.com` is opt-in
and manual — nothing here is sent automatically.

## Register

- [ ] FB-0001 — no relation kind connects GOAL to CAPABILITY — open
- [ ] FB-0002 — onboarding scaffolds two validators instead of one — sent-upstream

---

### FB-0001
type: notation-gap
methodology_version: "2.0.0"
raised_by: modeler
date: "2026-06-20"
status: open
upstream: not-sent
observation: No relation kind in the REL registry connects a GOAL directly to
  the CAPABILITY it requires — today the link can only be inferred indirectly
  (co-occurrence in a capability-map view, or a `stakeholding` relation naming
  both), not expressed as a first-class, queryable REL between the two.
proposed: A `requires_capability` (or symmetric `supports_goal`) relation
  kind, GOAL → CAPABILITY, alongside the existing motivation-to-business
  relation kinds.

---

### FB-0002
type: tooling-friction
methodology_version: "2.0.0"
raised_by: validator
date: "2026-07-10"
status: sent-upstream
upstream: sent 2026-07-10
observation: Onboarding scaffolds two separate validators — a Python
  whole-repo linter and a TypeScript per-file CLI — instead of one unified
  runtime, so a freshly scaffolded repo needs both Python and Node on PATH
  just to validate a single change locally.
proposed: Converge repo-scope and file-scope validation onto the single
  `@transitrix/cli --scope=repo` runtime, retiring the separate Python
  linter once parity is reached.
