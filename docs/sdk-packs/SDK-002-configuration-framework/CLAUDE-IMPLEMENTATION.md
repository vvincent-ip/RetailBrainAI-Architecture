# Claude Code Guide — SDK-002

```text
Validate and harden the completed SDK-002 for customer production deployment.

Inspect existing configuration contracts, bootstrap code, adapters, tests, and all typed settings consumers. Create a gap report before changes.

Implement missing deterministic precedence, typed validation, schema/version handling, secret references and redaction, atomic reload semantics, in-memory test source, production adapters, health diagnostics, and compatibility tests. Add a customer configuration guide, validation procedure, secure example overlays, upgrade/rollback notes, and operational troubleshooting.

Test malformed, missing, duplicate, secret, reload, concurrency, provider outage, and rollback scenarios. Do not expose values in telemetry or make breaking changes without migration approval.
```
