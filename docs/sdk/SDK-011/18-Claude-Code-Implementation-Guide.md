# SDK-011 Claude Code Implementation Guide

## 1. Execution Context

This file is designed to be copied with the SDK-011 pack into the root or documentation area of the actual RetailBrainAI implementation repository. Claude Code must treat the destination repository—not this architecture repository—as the source of truth for language, build system, package layout, naming, dependency injection, persistence, messaging, testing, and deployment conventions.

Do not execute all prompts blindly in one pass. Run them in order. After each prompt, review the diff, run the repository's normal checks, and commit only a coherent stage.

## 2. Global Guardrails

Claude must:

1. inspect `README*`, `CLAUDE.md`, contribution guides, build files, package manifests, architecture records, and existing SDK modules before editing;
2. identify the current technology stack and reuse existing conventions;
3. preserve backward compatibility unless the prompt explicitly authorizes a breaking change;
4. use SDK-002 through SDK-010 instead of creating duplicate configuration, logging, errors, events, AI, workflow, security, data, or messaging utilities;
5. implement a single-enterprise deployment with no tenant IDs or tenant-isolation behavior;
6. keep a neutral optional partition extension point internal where it adds little complexity, but never expose tenant-specific APIs;
7. avoid provider-specific types in domain and application layers;
8. add automated tests for every implemented requirement;
9. run formatter, linter, type checks, unit tests, integration tests, and architecture checks available in the repository;
10. document assumptions and unresolved decisions in `docs/implementation-notes/SDK-011.md` rather than guessing silently;
11. stop and report a blocker when required platform dependencies are absent, rather than implementing competing substitutes;
12. never commit secrets, credentials, real customer data, or raw sensitive document content.

## 3. Prompt 00 — Repository Discovery

```text
You are implementing SDK-011 Knowledge & Context Framework in this repository.

First perform discovery only. Do not write production code yet.

Read the repository instructions and inspect:
- README and CLAUDE files;
- build and package manifests;
- source and test layout;
- SDK-002 through SDK-010 implementations;
- persistence, messaging, API, security, observability, and dependency-injection conventions;
- existing document, search, AI, or knowledge code;
- CI workflows and required quality gates.

Create docs/implementation-notes/SDK-011.md containing:
1. detected stack and repository conventions;
2. reusable platform components and exact paths;
3. proposed SDK-011 module/package paths;
4. proposed dependency direction;
5. test strategy using existing tooling;
6. detected conflicts or missing prerequisites;
7. a requirement-to-work-package plan.

Constraints:
- single enterprise deployment only;
- no tenant identifiers or tenant-isolation implementation;
- no new infrastructure choice unless the repository lacks an abstraction and the decision is documented;
- do not modify existing behavior.

Run only safe discovery/validation commands and show the resulting plan.
```

## 4. Prompt 01 — Domain Model and State Machines

```text
Using the approved SDK-011 discovery plan and the architecture documents under docs/sdk/SDK-011, implement the provider-neutral domain model and state machines.

Implement at minimum:
- KnowledgeSource;
- SourceItem identity;
- immutable SourceVersion;
- IngestionJob and valid transitions;
- ProcessingJob and valid transitions;
- ProcessingPolicy reference and version;
- content reference/value objects;
- metadata and provenance value objects;
- classification and principal/group access attributes;
- stable domain errors using SDK-004;
- deterministic identity and idempotency helpers.

Rules:
- match existing language and package conventions;
- domain code must not import web, database, broker, vector-store, or cloud-provider libraries;
- no tenant fields;
- illegal state transitions must fail deterministically;
- time and identifier generation must be injectable/testable;
- include exhaustive unit tests and requirement IDs in test names or metadata.

Run repository formatting, static analysis, and unit tests. Update the implementation notes with files changed and any deviations.
```

## 5. Prompt 02 — Ports and Persistence

```text
Implement SDK-011 application ports and persistence adapters using existing repository patterns.

Required ports:
- source repository;
- ingestion-job repository;
- item/version repository;
- processing-job repository;
- content store abstraction or integration with the existing SDK-009 abstraction;
- transaction/unit-of-work boundary;
- outbox integration through SDK-005/SDK-010;
- clock, ID generator, hash service, and authorization decision ports where not already provided.

Required behavior:
- optimistic concurrency;
- immutable version history;
- idempotency-key conflict detection;
- atomic accepted-state plus outbox persistence;
- cursor-based queries;
- resurrection-safe tombstones;
- migrations using existing migration tooling;
- local/in-memory adapter only when consistent with repository testing conventions.

Do not introduce a new database or ORM when the project already standardizes one. Add repository contract tests and transactional integration tests. Run all relevant checks.
```

## 6. Prompt 03 — Ingestion Application Services

```text
Implement the SDK-011 ingestion use cases defined by 02.01-Knowledge-Ingestion.md.

Implement commands and handlers for:
- register, update, validate, activate, pause, disable, and decommission source;
- create/update item ingestion;
- batch submission;
- reprocess, cancel, retry, replay, quarantine, release, reject, deactivate, delete, and restore;
- synchronization start and checkpoint update;
- job, item history, batch, and synchronization queries.

Requirements:
- one canonical ingestion envelope for every adapter;
- strict schema and content-reference validation;
- durable idempotency;
- outbox-based dispatch;
- SDK-008 authorization for source and principal/group permissions;
- SDK-003 structured logging with no raw content;
- SDK-004 stable errors;
- SDK-005/010 versioned messages;
- metrics and traces following existing repository conventions;
- no tenant-specific behavior.

Add unit, integration, concurrency, restart-recovery, and security tests. Include requirement IDs in test coverage evidence.
```

## 7. Prompt 04 — Knowledge Processing Pipeline

```text
Implement the knowledge-processing pipeline defined by 02.02-Knowledge-Processing.md.

Build a composable ordered pipeline with ports for:
- content acquisition;
- format detection;
- malware/safety gate integration;
- parsing;
- text normalization;
- structural extraction;
- metadata enrichment;
- language detection;
- sensitive-data classification/redaction policy hooks;
- quality validation;
- artifact persistence;
- downstream chunking dispatch.

Pipeline stages must be independently testable, idempotent where applicable, cancellable, observable, and replayable from durable stage boundaries. Provider-specific parsers must be adapters selected through a registry.

Implement at least one safe reference parser for plain text and one test double. Do not add heavyweight external parsers unless already approved by the project. Add conformance tests for parser adapters and failure/retry behavior.
```

## 8. Prompt 05 — API and Event Adapters

```text
Expose SDK-011 through the repository's established API and messaging conventions.

Implement versioned request/response schemas and handlers for source administration, item ingestion, batch ingestion, job status, history, retry, replay, cancellation, quarantine, deletion, restoration, and synchronization.

Implement versioned events for accepted, queued, processing, succeeded, warning, failed, quarantined, cancelled, deactivated, deleted, and restored outcomes.

Rules:
- asynchronous acceptance must return 202 or the project-equivalent contract;
- provider exception text must never cross the boundary;
- raw content must not appear in events or logs;
- at-least-once consumers must deduplicate;
- API specifications and generated clients must use existing repository tooling;
- no tenant fields.

Add contract tests, schema compatibility tests, authorization tests, and redaction tests.
```

## 9. Prompt 06 — Acceptance and Hardening

```text
Complete SDK-011 acceptance hardening.

1. Build a traceability matrix mapping every implemented FR-ING and FR-PROC requirement to code and tests.
2. Add restart, duplicate-delivery, concurrent-update, stale-version, deletion-precedence, legal-hold, quarantine, and corrupted-content scenarios.
3. Verify raw content and secrets never appear in logs, traces, metrics, or normal events.
4. Verify provider-neutral domain/application layers through architecture tests.
5. Run the repository's complete validation suite.
6. Produce docs/implementation-notes/SDK-011-acceptance.md with commands run, results, known limitations, and deferred items.
7. Do not claim completion for requirements without evidence.
```

## 10. Prompt 07 — Final Review

```text
Review the complete SDK-011 implementation as a senior platform architect.

Check correctness, dependency direction, failure semantics, transactions, idempotency, concurrency, security, data lifecycle, observability, migration safety, API compatibility, test quality, and operational readiness.

Fix concrete defects you can prove. Do not perform unrelated refactoring. Update documentation and the traceability matrix. Present a final summary of implemented capabilities, validation results, remaining risks, and explicitly deferred multi-tenant support.
```
