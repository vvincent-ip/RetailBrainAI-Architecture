# RetailBrainAI Architecture Decisions

## Status

This register captures the accepted architecture baseline used by the SDK implementation packs. Each decision applies unless superseded by a later accepted decision record.

Decision states:

- **Accepted:** active architecture direction.
- **Deferred:** intentionally postponed; not rejected.
- **Superseded:** replaced by a later decision.
- **Rejected:** evaluated and not selected.

---

## ADR-001 — Organize the platform as reusable SDK capabilities

- **Status:** Accepted
- **Decision:** RetailBrainAI shall be organized into the frozen SDK roadmap, with SDK-001 through SDK-032 representing explicit reusable platform capabilities.
- **Rationale:** Shared concerns need consistent contracts and implementation patterns across applications. Capability SDKs reduce duplication, clarify ownership, and allow phased delivery.
- **Consequences:** Each SDK requires business context, requirements, architecture, contracts, tests, acceptance criteria, and Claude implementation prompts. Applications must not recreate an SDK capability privately without an approved exception.

## ADR-002 — Preserve the finalized SDK roadmap and numbering

- **Status:** Accepted
- **Decision:** The established SDK names, identifiers, phases, and ordering are the source of truth for this release. New frameworks shall not be inserted into the roadmap during implementation-pack production.
- **Rationale:** Stable scope is required to complete the architecture and avoid repeated redesign.
- **Consequences:** Missing concerns are addressed inside the owning SDK, through an ADR, or as explicitly deferred future scope. The final architecture document must use the frozen roadmap.

## ADR-003 — Use contract-first, ports-and-adapters architecture

- **Status:** Accepted
- **Decision:** SDK domain and application logic shall expose provider-neutral ports and published contracts. Infrastructure and vendor integrations shall be implemented as adapters.
- **Rationale:** The platform must support provider replacement, local testing, controlled adoption, and separation of business behavior from infrastructure products.
- **Consequences:** Vendor SDK types shall not cross public framework boundaries. Adapters must pass conformance tests. Provider-specific configuration remains outside domain models.

## ADR-004 — Start modular; distribute only when justified

- **Status:** Accepted
- **Decision:** SDK boundaries are logical and enforceable, but do not require one deployable service per SDK. Initial implementations may use a modular monolith or a small number of deployables.
- **Rationale:** Premature service decomposition increases operational and delivery complexity without guaranteed value.
- **Consequences:** Modules must preserve independent contracts and ownership. Later extraction must be possible without redesigning public behavior. Distribution decisions require scaling, resilience, security, ownership, or release-cadence evidence.

## ADR-005 — Use asynchronous durable jobs for long-running operations

- **Status:** Accepted
- **Decision:** Ingestion, processing, indexing, AI inference, workflows, reports, document generation, notifications, and background computation shall use durable job orchestration when they cannot reliably complete within bounded request latency.
- **Rationale:** These operations are failure-prone, variable in duration, and often depend on external systems.
- **Consequences:** APIs distinguish accepted from completed. Jobs expose state, progress, attempts, cancellation, retry, and terminal results. State transitions are validated and persisted.

## ADR-006 — Use event-driven integration with at-least-once semantics

- **Status:** Accepted
- **Decision:** Cross-module and cross-service state changes shall use versioned events where asynchronous integration is appropriate. Consumers shall assume at-least-once delivery.
- **Rationale:** Event-driven integration reduces temporal coupling and supports replay, scaling, and independent consumers.
- **Consequences:** Events need identifiers, schema versions, correlation and causation identifiers, aggregate identity, and safe payloads. Consumers implement deduplication. State plus publication uses an outbox or equivalent consistency pattern.

## ADR-007 — Keep durable state authoritative

- **Status:** Accepted
- **Decision:** Events, caches, indexes, embeddings, and generated artifacts are projections or derived representations; governed durable records remain authoritative.
- **Rationale:** Derived systems can be rebuilt, become stale, or fail independently.
- **Consequences:** Reconciliation and regeneration paths are required. Deletion and lifecycle changes propagate to all projections. Operational decisions must not depend solely on an event stream or cache unless that component is explicitly the authoritative store.

## ADR-008 — Target a single-enterprise deployment now

- **Status:** Accepted
- **Decision:** The current release shall not implement tenant-based data isolation, tenant identifiers in every contract, tenant partitioning, or cross-tenant administration.
- **Rationale:** Multi-tenancy is not currently required and would add pervasive complexity to contracts, persistence, authorization, testing, operations, and AI retrieval.
- **Consequences:** Authorization uses enterprise principals, groups, roles, source ownership, classification, and policy. Data models should avoid irreversible assumptions, but speculative tenant abstractions are prohibited.

## ADR-009 — Defer multi-tenancy as a future architecture stage

- **Status:** Deferred
- **Decision:** Multi-tenancy shall be reconsidered only when a concrete deployment or business requirement exists.
- **Revisit triggers:** hosted multi-customer offering, legal separation requirement, independent customer encryption domains, per-customer residency, customer-controlled retention, or contractual isolation SLAs.
- **Consequences:** A future ADR must define tenant identity, partitioning, encryption, authorization, indexing, caching, observability, migration, and operational isolation. It must not be introduced piecemeal by individual SDKs.

## ADR-010 — Centralize cross-cutting platform concerns

- **Status:** Accepted
- **Decision:** Configuration, logging, errors, events, AI access, workflow, security, data access, and messaging shall be provided through SDK-002 through SDK-010 rather than reimplemented by later SDKs.
- **Rationale:** Consistent cross-cutting behavior is essential for reliability, governance, and operability.
- **Consequences:** Later SDKs depend on stable abstractions from Phase 1. Provider-specific shortcuts that bypass those frameworks are architecture violations.

## ADR-011 — Separate knowledge grounding from search infrastructure

- **Status:** Accepted
- **Decision:** SDK-011 owns knowledge ingestion, processing, representations, provenance, retrieval orchestration, and context assembly. SDK-018 owns general search capabilities and search-provider abstraction.
- **Rationale:** Knowledge grounding includes lifecycle, chunking, embeddings, citations, and AI context concerns beyond generic search, while search remains a reusable platform capability.
- **Consequences:** SDK-011 may consume SDK-018 through stable interfaces when available. It must not permanently bind its domain to one search or vector product.

## ADR-012 — Separate AI invocation, agents, prompts, evaluation, memory, and tools

- **Status:** Accepted
- **Decision:** AI concerns shall be split across SDK-006, SDK-012, and SDK-022 through SDK-025 according to their frozen responsibilities.
- **Rationale:** Model invocation, orchestration, prompt lifecycle, evaluation, memory, and tool governance change independently and require different controls.
- **Consequences:** Agent code does not embed provider-specific model calls or unmanaged prompts. Memory does not become an ungoverned substitute for enterprise knowledge. Tools require explicit registration and authorization.

## ADR-013 — Use deterministic controls around AI behavior

- **Status:** Accepted
- **Decision:** Probabilistic model output shall be constrained by deterministic schemas, policies, rules, workflow controls, authorization, budgets, and validation.
- **Rationale:** Enterprise actions require predictable safety and accountability even when inference is probabilistic.
- **Consequences:** Structured outputs are validated. SDK-013 owns deterministic decision logic. High-impact operations may require human approval. Model output alone cannot grant authorization or bypass policy.

## ADR-014 — Make provenance and citations mandatory for grounded AI

- **Status:** Accepted
- **Decision:** Context assembled from enterprise knowledge shall preserve source, version, chunk, retrieval, and transformation provenance sufficient to produce citations and audit evidence.
- **Rationale:** Grounded answers must be explainable and traceable to governed sources.
- **Consequences:** Retrieval results and context packages include provenance. Derived content cannot silently lose source relationships. Citation failures are observable quality defects.

## ADR-015 — Version all externally meaningful contracts and resources

- **Status:** Accepted
- **Decision:** APIs, event schemas, processing policies, prompts, model configurations, rules, reports, feature configurations, and other externally meaningful resources shall use explicit versioning.
- **Rationale:** Long-running jobs, replay, audit, and controlled rollout require reproducibility.
- **Consequences:** Breaking changes require a migration path. Historical execution records retain the versions used. In-place mutation must not destroy reproducibility.

## ADR-016 — Adopt outbox and idempotency patterns

- **Status:** Accepted
- **Decision:** Operations that persist state and publish work or events shall use an outbox, transactional messaging, or equivalent guarantee. Commands and event consumers shall be idempotent where duplicate delivery is possible.
- **Rationale:** Distributed failure can otherwise produce lost work or duplicate outcomes.
- **Consequences:** Idempotency keys, aggregate versions, deduplication records, and retry semantics are part of implementation requirements. Exactly-once transport claims are not relied upon.

## ADR-017 — Externalize configuration, policy, prompts, and feature rollout

- **Status:** Accepted
- **Decision:** Runtime configuration, rules, prompts, model selection policy, limits, retention, and feature rollout shall be externally managed and versioned through their owning SDKs.
- **Rationale:** These values vary by environment and evolve faster than domain code.
- **Consequences:** Domain logic does not contain hidden environment constants. Changes are auditable. Safe defaults and validation are required.

## ADR-018 — Observability and audit are separate but complementary

- **Status:** Accepted
- **Decision:** SDK-003 provides operational logging and telemetry; SDK-019 provides governed audit records. One must not be treated as a substitute for the other.
- **Rationale:** Operational diagnostics and immutable accountability have different retention, access, integrity, and content requirements.
- **Consequences:** Sensitive actions emit audit records even if logs exist. Logs must not contain unrestricted audit or business content. Correlation links the two where authorized.

## ADR-019 — Use feature flags for progressive delivery

- **Status:** Accepted
- **Decision:** Risky or incremental capability rollout shall use SDK-021 rather than deployment-time code forks or unmanaged environment toggles.
- **Rationale:** The platform needs reversible rollout, experimentation boundaries, and controlled migration.
- **Consequences:** Flags have owners, expiry expectations, evaluation context, and auditability. Permanent business rules must not remain hidden in feature flags.

## ADR-020 — Require shared conformance and acceptance suites

- **Status:** Accepted
- **Decision:** Each SDK shall define contract tests and acceptance evidence; every provider adapter shall pass a common conformance suite.
- **Rationale:** Interfaces alone do not guarantee compatible behavior.
- **Consequences:** Error mapping, retry behavior, lifecycle semantics, security controls, and edge cases are tested consistently. Requirement identifiers map to tests or approved manual evidence.

## ADR-021 — Treat architecture packs as executable implementation inputs

- **Status:** Accepted
- **Decision:** Each SDK pack shall include Claude Code prompts intended to be copied into the actual implementation repository and executed there.
- **Rationale:** The architecture must translate into implementation without requiring manual reinterpretation.
- **Consequences:** Prompts first inspect the destination repository, preserve its language and conventions, avoid inventing technologies, implement incrementally, run validations, and record deviations or unresolved choices.

## ADR-022 — Produce one final integrated architecture in Markdown and HTML

- **Status:** Accepted
- **Decision:** After all SDK implementation packs are complete, the repository shall contain a consolidated final architecture document and a navigable standalone HTML representation.
- **Rationale:** Individual packs need an integrated system view for governance, implementation sequencing, onboarding, and review.
- **Consequences:** The final document must reconcile dependencies, boundaries, principles, decisions, data flows, security, deployment, operations, and roadmap. HTML is generated from the completed architecture, not maintained as an independent conflicting source.

## Rejected or intentionally avoided approaches

The following are not part of the accepted baseline:

- one microservice per SDK by default;
- direct provider SDK usage inside domain logic;
- synchronous request blocking for unbounded AI or processing work;
- exactly-once delivery assumptions;
- unversioned events or prompts;
- AI output treated as authoritative policy or authorization;
- tenant complexity added without a concrete requirement;
- application-specific copies of shared SDK behavior;
- final HTML authored independently before the underlying architecture is complete.

## Decision governance

A new decision record is required when a proposed change:

1. changes an SDK boundary or roadmap responsibility;
2. introduces a mandatory platform technology;
3. changes deployment or data-authority strategy;
4. changes security, authorization, tenancy, or compliance assumptions;
5. changes public API or event compatibility policy;
6. supersedes an accepted decision in this register.

New records must state context, decision, alternatives, rationale, consequences, migration impact, and status.