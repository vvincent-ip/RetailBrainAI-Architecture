# Claude Code Guide — SDK-018

```text
Implement SDK-018 as production enterprise search after SDK-011 contracts are frozen.

Define provider-neutral schema, indexing, query, filter, facet, ranking, result and administration contracts. Implement full-text and hybrid search, authorization filtering, safe pagination, index versioning/aliases, durable indexing jobs, reindex/rebuild/reconciliation, deletion propagation and telemetry.

Add a production search adapter, conformance suite, relevance benchmark corpus, load/soak tests, authorization leakage tests, outage/reindex/rollback tests, HA/DR and snapshot guidance, customer deployment/index operations and incident runbooks.

Do not take ownership of SDK-011 knowledge lifecycle or expose provider query types publicly.
```
