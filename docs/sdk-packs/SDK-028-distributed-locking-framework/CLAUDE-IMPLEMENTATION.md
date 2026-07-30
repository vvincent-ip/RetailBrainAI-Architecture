# Claude Code Guide — SDK-028

```text
Implement production distributed locking only after SDK-027 contracts are accepted.

Define lock handle, owner, lease, fencing token, acquisition, renewal and release contracts. Implement bounded acquisition, cancellation, lease renewal/loss, safe release, fencing and provider adapters.

Add correctness tests for contention, duplicate owner, process pause, network partition, provider failover, stale release and clock effects; benchmarks; metrics/alerts; customer provider configuration and recovery runbook. Never present a lease lock as a substitute for a database transaction and never omit fencing where stale writers can cause harm.
```
