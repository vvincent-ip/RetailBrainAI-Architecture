# Claude Code Guide — SDK-004

```text
Harden the completed SDK-004 for production use.

Inventory error types, codes, mappings, provider exceptions, and downstream handling. Produce a compatibility gap report.

Implement missing classifications, safe/internal message separation, causal metadata, transport mappings, provider normalization, bounded retry guidance, catalog documentation, information-disclosure tests, and customer support diagnostics. Add contract tests for HTTP, messaging, workflow, and background-job surfaces.

Do not place retry loops inside error types or expose stack traces/provider details to customers. Preserve published codes unless an approved migration exists.
```
