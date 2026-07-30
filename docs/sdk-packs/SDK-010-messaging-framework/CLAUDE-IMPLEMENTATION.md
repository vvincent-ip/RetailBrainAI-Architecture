# Claude Code Guide — SDK-010

```text
Production-harden SDK-010 after inspecting current contracts, adapters, middleware, retry/DLQ logic, security, and consumers.

Implement missing idempotency and inbox/outbox integration, ordering documentation, bounded retry, poison-message handling, back-pressure, trace/security context propagation, production broker conformance, TLS/auth configuration, HA/DR guidance, replay tools, load/soak and outage tests, metrics/alerts, customer deployment manifests, and runbooks.

Assume at-least-once delivery; never claim exactly-once business processing. Keep broker-specific types in adapters.
```
