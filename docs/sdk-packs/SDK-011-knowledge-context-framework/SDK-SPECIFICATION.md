# SDK-011 — Knowledge & Context Framework

**Phase:** 2 — Enterprise Intelligence  
**Priority:** Highest  
**Dependencies:** SDK-002, 003, 004, 005, 006, 008, 009  
**Purpose:** Document ingestion, chunking, embeddings, vector search, RAG, and context assembly.

## Required capabilities

- Source registration, ingestion commands, durable jobs, versioned documents, content normalization, classification, provenance, lifecycle, and deletion.
- Pluggable parsing, chunking, metadata enrichment, embedding generation/versioning, vector projection, keyword projection integration, and rebuild/reindex.
- Authorized semantic/hybrid retrieval, filters, reranking hooks, deduplication, context budgeting, citation packages, and grounded evidence contracts.
- Durable database/object records are authoritative; vector/search indexes are rebuildable projections.
- Idempotent at-least-once processing, outbox events, partial-failure recovery, quarantine, reconciliation, and operational control APIs.
- Single-enterprise deployment; authorization, roles/groups, classification and provenance remain mandatory; tenant isolation is deferred.

## Production requirements

Production object, embedding, vector, and parser adapters; malware/content safety controls; scale benchmarks; retention/deletion propagation; backup/restore; reindex runbooks; source connector security; retrieval quality evaluation; customer deployment and acceptance tests.

## Parallelization

Safe alongside SDK-013, SDK-014, SDK-015, SDK-016, SDK-019, SDK-021, SDK-022, SDK-026, SDK-027, and SDK-029. SDK-012, SDK-018, SDK-023, SDK-024, SDK-031, and SDK-032 are gated by stable SDK-011 contracts.

## Acceptance

Documents are traceable from source to citation, authorization is enforced before retrieval, indexes can be rebuilt, deletion propagates, failures resume idempotently, and grounded results expose stable provenance.
