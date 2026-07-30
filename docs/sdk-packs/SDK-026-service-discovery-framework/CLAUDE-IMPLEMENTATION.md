# Claude Code Guide — SDK-026

```text
Implement a production provider-neutral service discovery library.

Define registration, endpoint, lease, health, query, watch and selection contracts. Implement TTL renewal, deregistration, bounded-staleness cache, watch recovery, filtering, last-known-good behavior, secure metadata and cancellation/timeouts.

Add at least one production adapter, conformance suite, outage/partition/stale-entry/load tests, TLS/auth configuration, metrics/alerts, customer deployment and troubleshooting runbooks. Do not leak Kubernetes, Consul or Eureka types into public contracts.
```
