# Claude Code Guide — SDK-007

```text
Production-harden the completed SDK-007.

Inspect orchestration determinism, durable state, workers, activities, retries, compensation, timers, signals, migrations, and operational tooling.

Add missing idempotency, leases, crash recovery, cancellation, compensation, human approval, workflow versioning, in-flight migration, queue back-pressure, metrics/traces, production persistence adapter, HA/DR guidance, load/soak and failure-injection tests, customer deployment manifests, and runbooks.

Keep nondeterministic I/O and AI calls inside activities. Do not claim durability with in-memory state. Prove recovery without duplicate business effects.
```
