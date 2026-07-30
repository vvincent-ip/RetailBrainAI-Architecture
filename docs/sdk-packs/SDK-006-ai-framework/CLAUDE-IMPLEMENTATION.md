# Claude Code Guide — SDK-006

```text
Validate and production-harden SDK-006. Do not redesign downstream prompt, evaluation, memory, knowledge, or agent ownership into this SDK.

Inspect public AI contracts, routing, adapters, streaming, structured output, tool calls, telemetry, security, and tests. Produce a gap report.

Implement missing capability-based routing, policy filters, budgets, timeout/cancellation, bounded retry, circuit breaker, rate/concurrency limits, normalized usage and safety metadata, secure redaction, provider fallback, production adapter conformance, load/soak tests, outage tests, cost dashboards, customer configuration, and operations runbooks.

No provider SDK type may cross the adapter boundary. No model may directly execute a tool. Completion requires customer-place installation and failure-recovery evidence.
```
