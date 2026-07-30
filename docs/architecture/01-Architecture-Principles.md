# RetailBrainAI Architecture Principles

## Status

- **State:** Accepted baseline
- **Applies to:** SDK-001 through SDK-032 and all RetailBrainAI applications
- **Review trigger:** material platform, deployment, security, regulatory, or operating-model change

## Purpose

These principles define the non-negotiable design rules for RetailBrainAI. They translate the finalized platform direction into implementation constraints that must be applied consistently by architects, engineers, reviewers, and AI coding agents.

## AP-01 — Business capability first

Architecture shall be organized around stable business and platform capabilities rather than vendor products, infrastructure topology, or individual applications.

**Implications**

- SDK boundaries represent reusable capabilities.
- Applications consume SDK contracts rather than reimplementing shared concerns.
- Vendor-specific details remain behind adapters.

## AP-02 — Explicit ownership and bounded responsibility

Every SDK shall have a clearly documented purpose, owned domain concepts, public contracts, dependencies, and non-goals.

**Implications**

- No SDK may silently absorb another SDK's responsibility.
- Cross-SDK dependencies must use declared interfaces or events.
- Circular dependencies are prohibited.

## AP-03 — Contract-first interoperability

Public APIs, events, commands, schemas, extension points, and error contracts shall be defined before provider-specific implementation.

**Implications**

- Contracts are versioned independently from implementations.
- Consumers must not depend on internal persistence models.
- Compatibility and deprecation rules are part of the contract.

## AP-04 — Provider neutrality with replaceable adapters

Core domain and application logic shall not depend directly on cloud, model, database, vector-store, broker, search, cache, scheduler, or document-provider SDKs.

**Implications**

- External products are integrated through ports and adapters.
- Each adapter must pass a shared conformance suite.
- Provider replacement must not require rewriting domain behavior.

## AP-05 — Modular implementation before distributed decomposition

Logical modularity is mandatory; physical service separation is an operational choice.

**Implications**

- SDKs may initially run in the same deployable process when appropriate.
- Module boundaries, contracts, data ownership, and event semantics must still be preserved.
- Services are split only for scaling, resilience, security, ownership, or release-independence reasons.

## AP-06 — Asynchronous by default for long-running work

Operations involving ingestion, AI inference, workflow execution, indexing, reporting, document processing, notification fan-out, or background computation shall use durable asynchronous execution unless a bounded synchronous path is explicitly justified.

**Implications**

- Acceptance is distinct from completion.
- Job state is durable and queryable.
- Retry, replay, cancellation, deduplication, and dead-letter behavior are designed explicitly.

## AP-07 — Event-driven integration with stateful safeguards

Events shall communicate meaningful state changes, while durable state remains the source of operational truth.

**Implications**

- Consumers assume at-least-once delivery.
- Events include stable identifiers, schema versions, correlation, causation, and ordering metadata where available.
- Outbox or equivalent atomic publication patterns are required when state and events must remain consistent.

## AP-08 — Security and authorization are embedded controls

Authentication, authorization, data classification, secrets handling, input validation, content safety, and least privilege shall be incorporated into every framework boundary.

**Implications**

- Possession of an identifier never implies authorization.
- Secrets and raw sensitive content are excluded from logs, traces, metrics, and ordinary events.
- Security decisions are enforced server-side and are testable.

## AP-09 — Single-enterprise deployment for the current release

The current architecture targets one enterprise deployment without tenant-based data isolation.

**Implications**

- Current contracts do not require tenant identifiers or tenant partition keys.
- Authorization is based on enterprise principals, groups, roles, source ownership, classification, and policy.
- Data models should avoid choices that make later partitioning impossible, but no dormant multi-tenant complexity shall be implemented now.

## AP-10 — Data provenance and lifecycle are first-class

All governed data and AI-derived artifacts shall preserve origin, version, lineage, processing history, lifecycle status, and deletion semantics.

**Implications**

- Derived artifacts remain traceable to source versions and processing versions.
- Deactivation, deletion, restoration, retention, and legal hold behavior are explicit.
- AI output must not erase source provenance.

## AP-11 — AI is governed, observable, and replaceable

Models, prompts, tools, memories, evaluations, and agents are governed platform resources rather than opaque application code.

**Implications**

- Model providers are accessed through SDK-006 abstractions.
- Prompts are versioned through SDK-022.
- Quality and safety are measured through SDK-023.
- Agent execution uses SDK-012 and approved tools from SDK-025.
- Knowledge grounding uses SDK-011 with citations and provenance.

## AP-12 — Deterministic control surrounds probabilistic intelligence

Probabilistic AI behavior shall operate within deterministic policies, schemas, limits, workflow controls, and validation.

**Implications**

- Structured outputs are schema validated.
- Rules and policy decisions remain in SDK-013 when deterministic behavior is required.
- High-impact actions require explicit authorization and, where appropriate, human approval.

## AP-13 — Observability is part of the contract

Every framework shall define logs, metrics, traces, audit signals, health indicators, and safe diagnostic context as implementation requirements.

**Implications**

- Correlation identifiers cross process and message boundaries.
- Metric labels must remain bounded.
- Operational state and failure classification are externally visible through governed APIs.

## AP-14 — Reliability is designed, not delegated

Timeouts, retries, idempotency, concurrency control, backpressure, circuit breaking, graceful degradation, and recovery shall be specified at framework boundaries.

**Implications**

- Retries occur only for classified retryable failures.
- Duplicate delivery cannot create duplicate logical outcomes.
- State transitions are validated and persisted.

## AP-15 — Configuration and policy are externalized and versioned

Environment-specific configuration, feature switches, rules, prompt versions, model policies, retention settings, and operational limits shall not be hard-coded into domain logic.

**Implications**

- SDK-002 is the configuration authority.
- SDK-021 controls feature rollout.
- Policy changes are auditable and reproducible.

## AP-16 — APIs and events evolve compatibly

Published contracts shall use explicit versioning and backward-compatible evolution wherever practical.

**Implications**

- Breaking changes require a new major contract version and migration plan.
- Consumers are given deprecation periods.
- Stored events and long-running workflows remain interpretable after upgrades.

## AP-17 — Testability and conformance are mandatory

Each SDK shall provide contract tests, conformance tests, test fixtures, reference adapters, and acceptance evidence appropriate to its responsibilities.

**Implications**

- Provider adapters are interchangeable only after passing conformance tests.
- Requirement identifiers map to tests.
- Failure, recovery, security, and upgrade paths are tested, not only happy paths.

## AP-18 — Progressive delivery and reversible change

Architecture shall support incremental rollout, rollback, coexistence, and migration rather than big-bang replacement.

**Implications**

- Feature flags control risky rollout.
- Schema and contract changes support transition periods.
- Reindexing, replay, and regeneration are designed as normal operations.

## AP-19 — Documentation is executable guidance

Architecture documents and implementation packs shall be written so they can be moved into the target project and used directly by Claude Code or another engineering agent.

**Implications**

- Prompts instruct the agent to inspect the destination repository first.
- Prompts preserve the destination stack and conventions.
- Ambiguities are recorded as decisions or implementation assumptions rather than silently invented.
- Each implementation stage includes validation and completion criteria.

## AP-20 — Build only the complexity required now

The platform shall preserve strategic extension points without implementing speculative capabilities before they are required.

**Implications**

- Multi-tenancy is deferred.
- Physical microservice decomposition is not mandatory.
- Additional providers are added after core contracts and reference adapters are proven.
- Deferred scope is documented separately from rejected scope.

## Governance

A design that conflicts with a principle must document:

1. the principle being varied;
2. the business or technical reason;
3. the scope and duration of the exception;
4. the risks and compensating controls;
5. the owner and review date.

Undocumented exceptions are architecture defects.