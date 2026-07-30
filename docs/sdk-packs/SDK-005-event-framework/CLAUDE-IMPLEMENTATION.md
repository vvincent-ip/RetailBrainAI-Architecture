# Claude Code Guide — SDK-005

```text
Validate SDK-005 for production event-driven integration.

Inspect envelopes, serializers, publisher ports, outbox contracts, catalogs, and consumers. Preserve existing compatible schemas.

Add missing version metadata, correlation/causation, classification, idempotency guidance, schema compatibility checks, replay controls, dead-letter metadata, observability, performance tests, and customer replay/operations runbooks. Provide test doubles and conformance tests for producers and consumers.

Assume at-least-once delivery. Never imply exactly-once processing and never place broker-specific types in public contracts.
```
