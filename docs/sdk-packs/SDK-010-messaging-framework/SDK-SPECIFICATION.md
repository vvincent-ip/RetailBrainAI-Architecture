# SDK-010 — Messaging Framework

**Phase:** 1 — Platform Foundation  
**Status:** Complete  
**Dependencies:** SDK-002–009  
**Purpose:** Provider-independent messaging, publish/subscribe, retry, and DLQ.

## Required capabilities

- Provider-neutral producer, consumer, subscription, acknowledgement, header, and administration contracts.
- At-least-once delivery, idempotency, ordering scope, partition/key strategy, bounded retry, poison-message detection, dead-letter handling, replay, and back-pressure.
- Correlation, causation, principal context reference, schema version, classification, and trace propagation.
- Transactional outbox/inbox integration and duplicate-safe consumer middleware.
- Production broker adapter, local test adapter, conformance suite, and operational metrics.

## Production requirements

HA topology, capacity planning, TLS/authentication, least privilege, retention, DLQ/replay runbooks, failure injection, load/soak tests, disaster recovery, and customer deployment/configuration artifacts.

## Parallelization

Additional broker adapters are safe. Public envelope, acknowledgement, or retry changes affect SDK-014, SDK-015, SDK-029 and applications and require coordination.

## Acceptance

Duplicate and out-of-order delivery are tested, poison messages are isolated, replay is controlled and auditable, and broker outage behavior is bounded and observable.
