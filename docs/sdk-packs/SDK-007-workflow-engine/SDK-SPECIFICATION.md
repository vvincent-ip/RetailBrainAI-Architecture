# SDK-007 — Workflow Engine

**Phase:** 1 — Platform Foundation  
**Status:** Complete  
**Dependencies:** SDK-002–006  
**Purpose:** Durable workflows, orchestration, compensation, and retries.

## Required capabilities

- Versioned workflow definitions and durable instance state.
- Deterministic orchestration, activity boundaries, timers, signals, cancellation, retries, compensation, and human approval steps.
- Idempotent activity execution, lease/ownership control, duplicate delivery handling, and recovery after process/node failure.
- Explicit state machine and terminal outcomes; queryable history and correlation.
- Workflow migration/versioning rules for in-flight instances.
- AI calls occur as governed activities through SDK-006 and are never treated as deterministic orchestration code.

## Production requirements

Provide production persistence and worker adapters, HA deployment guidance, capacity and queue controls, backup/restore, disaster recovery, stuck-workflow diagnostics, replay/version tests, load/soak tests, and customer runbooks.

## Parallelization

New workflow definitions are safe once engine contracts are stable. Engine contract or persistence changes affect SDK-008, SDK-012–014, and applications; avoid concurrent breaking edits.

## Acceptance

Workflows recover from crashes without duplicate business effects, support cancellation/compensation, expose complete operational history, and can be upgraded with documented in-flight migration behavior.
