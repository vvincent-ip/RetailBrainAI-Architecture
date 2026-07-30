# Claude Code Guide — SDK-001

```text
Implement or validate SDK-001 as production-grade customer-deployable code.

Read the architecture documents, SDK specification, Production and Customer Deployment Standard, existing source, tests, and all consumers before editing.

1. Inventory public primitives and downstream usages; produce a gap report.
2. Preserve compatible contracts. Do not move domain-specific types into SDK-001.
3. Eliminate hidden global state and nondeterminism; add injectable clock/ID/random abstractions where required.
4. Add architecture rules, serialization round trips, compatibility tests, static analysis, package metadata, API docs, and migration notes.
5. Run all affected CI checks and prove no downstream breakage.

Do not create placeholder utilities, new SDKs, tenant isolation, or unapproved breaking changes. Completion requires production release evidence and customer-consumable package documentation.
```
