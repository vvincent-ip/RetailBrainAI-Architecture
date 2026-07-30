# SDK-011 — Knowledge & Context Framework

## Status

- **Lifecycle:** Draft
- **Roadmap phase:** Phase 2
- **Framework identifier:** SDK-011
- **Primary consumers:** AI services, agent runtimes, workflow services, search services, reporting services, and application APIs

## Purpose

The Knowledge & Context Framework provides shared capabilities to ingest, normalize, enrich, govern, retrieve, and assemble enterprise knowledge for AI and non-AI workloads. It establishes consistent contracts for retrieval-augmented generation, semantic and hybrid retrieval, metadata filtering, contextual grounding, provenance, access control, and lifecycle management.

## Current Deployment Scope

This release targets a single enterprise deployment. Tenant partitioning and tenant-specific policy isolation are explicitly deferred. The implementation must not hard-code assumptions that prevent later partitioning, but no tenant identifiers, tenant-aware APIs, tenant-specific indexes, or tenant-isolation acceptance tests are required now.

Authorization, source ownership, data classification, provenance, and principal/group access controls remain in scope.

## Document Set

1. [Business Context](01-Business-Context.md)
2. Functional Requirements
   - [Knowledge Ingestion](02-Functional-Requirements/02.01-Knowledge-Ingestion.md)
   - [Knowledge Processing](02-Functional-Requirements/02.02-Knowledge-Processing.md)
   - Chunking
   - Embedding Generation
   - Embedding Versioning
   - Vector Index Management
   - Metadata Management
   - Retrieval
   - Hybrid Search
   - Context Assembly
   - Governance
   - Security
   - Lifecycle Management
   - Error Handling
   - Performance Requirements
   - Non-functional Requirements
   - Acceptance Criteria
3. Technical Architecture
4. Domain Model
5. RAG Pipeline
6. Embedding Architecture
7. Chunking Strategy
8. Vector Store Abstraction
9. Context Assembly
10. Persistence
11. API Contracts
12. Event Contracts
13. Security
14. Observability
15. Deployment
16. Testing Strategy
17. Architecture Decision Records
18. [Claude Code Implementation Guide](18-Claude-Code-Implementation-Guide.md)
19. Acceptance Criteria
20. Implementation Roadmap

## Architectural Boundaries

SDK-011 owns knowledge ingestion contracts, canonical knowledge records, document-processing orchestration, retrieval abstractions, context assembly, provenance, and knowledge lifecycle controls.

SDK-011 does not own large-language-model invocation, agent planning, workflow execution, enterprise identity, raw object-storage infrastructure, message-broker infrastructure, or general-purpose search infrastructure. Those responsibilities remain with their corresponding platform frameworks and are consumed through stable interfaces.

## Key Dependencies

- SDK-002 Configuration Framework
- SDK-003 Structured Logging Framework
- SDK-004 Error Framework
- SDK-005 Event Framework
- SDK-006 AI Framework
- SDK-008 Security Framework
- SDK-009 Enterprise Data Framework
- SDK-010 Messaging Framework
- SDK-018 Search Framework, when available
- SDK-019 Audit Framework, when available

## Implementation Principle

All implementation work must preserve authorization-aware retrieval, source provenance, deterministic traceability, provider independence, replaceable storage adapters, and a future-compatible partition key extension point. Multi-tenant behavior is not part of the current release.
