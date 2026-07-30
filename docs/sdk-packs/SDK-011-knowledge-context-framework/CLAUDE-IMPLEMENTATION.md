# Claude Code Guide — SDK-011

```text
Implement SDK-011 as a production customer-deployable knowledge plane.

Read all architecture documents, existing SDK-011 detailed specifications, this pack, production standard, and dependency contracts. Inventory existing code and produce a gap plan before editing.

Build provider-neutral domain/application modules for source registration, versioned ingestion, durable jobs, processing, chunking, embeddings, metadata, lifecycle, retrieval, context assembly, citations, authorization, provenance, deletion, reconciliation, and reindexing. Implement production adapters behind ports and test doubles for each boundary.

Require outbox/idempotency, authoritative durable state, rebuildable indexes, bounded retries/timeouts, quarantine, secure content handling, metrics/traces/audit, quality/load/failure tests, customer configuration, deployment, migration, backup/restore, reindex and incident runbooks.

Do not add tenant isolation. Do not leak vector/model/provider types. No mock-only or in-memory-only production path qualifies as complete.
```
