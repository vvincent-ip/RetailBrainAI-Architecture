# Claude Code Guide — SDK-027

```text
Implement SDK-027 as production distributed caching, never as a source of truth.

Define typed cache, key, serialization, expiration and atomic-operation contracts. Implement cache-aside helpers, stampede protection, jitter, namespacing, size limits, timeouts, circuit breaker, bypass/degraded behavior, encryption/auth and safe diagnostics.

Add a production distributed adapter and local test adapter, conformance tests, outage/eviction/stampede/serialization migration/load tests, capacity dashboards, customer deployment, invalidation, recovery and incident runbooks.
```
