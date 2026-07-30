# SDK-017 — Reporting Framework

**Phase:** 3 — Enterprise Operations  
**Priority:** Medium  
**Dependencies:** SDK-009, SDK-015  
**Purpose:** Reports, dashboards, exports, and scheduled reporting.

## Required capabilities

- Versioned report definitions, parameters, datasets, filters, sorting, pagination, layouts, formats, schedules, recipients, and delivery status.
- Provider-neutral query and rendering ports; authorization enforced at dataset and output level.
- Synchronous small reports and durable asynchronous generation for large reports.
- Export to approved formats, safe templating, localization, accessibility metadata, caching with invalidation, and reproducible snapshots.
- Delivery through SDK-015; durable report metadata and lineage through SDK-009.

## Production requirements

Production rendering adapter, load and large-export tests, resource quotas, cancellation, secure temporary storage, retention, scheduling integration, dashboards, customer authoring/deployment guidance, and failure/recovery runbooks.

## Parallelization

Blocked by stable SDK-015 contracts. Once accepted, safe alongside SDK-018 and SDK-019.

## Acceptance

Reports enforce authorization, large jobs do not exhaust runtime resources, outputs are reproducible and traceable, scheduled delivery is idempotent, and operators can cancel/retry/diagnose generation.
