# SDK-020 — Compliance Framework

**Phase:** 4 — Governance & Compliance  
**Priority:** Medium  
**Dependencies:** SDK-008, SDK-019  
**Purpose:** GDPR, HIPAA, SOC2, PCI-DSS, retention, consent, and legal hold.

## Required capabilities

- Versioned compliance policies, control mappings, data classifications, processing purposes, consent records, retention schedules, deletion/erasure workflows, legal holds, evidence and exceptions.
- Policy evaluation APIs and integration hooks; owning SDKs still execute domain-specific deletion and retention.
- Data-subject/request workflow, approvals, deadlines, evidence packages, and reconciliation.
- Configurable regulatory profiles; no claim of legal certification by code alone.
- Authorization, segregation of duties, immutable audit, and policy change lifecycle.

## Production requirements

Customer-configurable policies, legal review points, control/evidence matrix, retention and erasure tests, legal-hold conflict handling, dashboards/alerts, migration, customer compliance operations and incident runbooks.

## Parallelization

Blocked by SDK-019. Once accepted, safe alongside SDK-021 and SDK-022.

## Acceptance

Policies are versioned and explainable, consent/retention/holds are enforced through owning SDK integrations, requests are traceable to evidence, and exceptions require authorized approval.
