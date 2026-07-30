# Claude Code Guide — SDK-014

```text
Implement SDK-014 as a durable distributed scheduler suitable for customer production.

Define schedule, trigger, job, run, lease, misfire and administration contracts. Implement one-time/recurring/cron scheduling, timezone/DST semantics, durable persistence, leases/heartbeats, idempotency, bounded retry, cancellation, concurrency limits, pause/resume, messaging delivery, history and recovery.

Integrate long-running workflows through SDK-007 rather than recreating orchestration. Add failover, clock-skew, duplicate delivery, DST, load/soak and upgrade tests; HA deployment; metrics/alerts; backup/restore; customer operations and incident runbooks.
```
