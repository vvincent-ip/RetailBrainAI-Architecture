# Production and Customer Deployment Standard

This standard applies to every RetailBrainAI SDK implementation pack. An SDK is not complete merely because its core behavior works in a developer environment. It must be safe, supportable, observable, upgradeable, and deployable in a customer-controlled production environment.

## Mandatory engineering qualities

1. **Security:** least privilege, secure defaults, secret redaction, encryption in transit and at rest where applicable, dependency and container scanning, threat modeling, abuse-case tests, and no hard-coded credentials.
2. **Reliability:** bounded retries, timeouts, cancellation, idempotency, circuit breaking where remote calls are made, failure isolation, durable recovery where state is involved, and tested degraded behavior.
3. **Compatibility:** semantic versioning, backward-compatible public contracts by default, schema and event evolution rules, migration tooling, deprecation periods, and rollback-safe releases.
4. **Observability:** structured logs, metrics, traces, correlation IDs, health/readiness indicators, audit events where required, operational dashboards, and actionable alerts. Sensitive data must not appear in normal telemetry.
5. **Performance:** declared service-level objectives, capacity assumptions, benchmark methodology, load and soak tests, resource limits, back-pressure behavior, and evidence that critical paths meet targets.
6. **Operations:** environment-specific configuration, customer-owned secrets, deployment manifests or modules, backup and restore procedures, disaster-recovery expectations, runbooks, troubleshooting guidance, support diagnostics, and upgrade/rollback instructions.
7. **Quality:** unit, contract, integration, security, resilience, concurrency, performance, and end-to-end tests as applicable. Tests must be deterministic and runnable in CI.
8. **Provider independence:** domain and application layers depend on ports; provider SDKs remain inside adapters. At least one production-capable reference adapter is required when the SDK's purpose needs infrastructure.
9. **Data governance:** explicit data ownership, classification, retention, deletion, provenance, validation, schema versioning, and reconciliation behavior.
10. **Customer acceptance:** reproducible installation, configuration validation, smoke tests, operational handover, known-limit documentation, and signed acceptance evidence.

## Required release artifacts

Each SDK release must include API and contract documentation, configuration reference, deployment guide, security considerations, operations runbook, migration and rollback guide, examples, test evidence, compatibility matrix, dependency bill of materials, and release notes.

## Prohibited completion shortcuts

The following do not qualify as completion: in-memory-only production paths where durable behavior is required; placeholder adapters; skipped failure handling; unbounded retries; manual database edits as a normal operation; undocumented defaults; tests that require developer machines; mock-only integration claims; or MVP/POC language used to waive production requirements.

## Customer-place definition of done

The SDK can be installed into a clean customer environment using documented steps, configured without source changes, integrated through stable contracts, monitored by the customer's operations team, upgraded and rolled back safely, recovered from tested failures, and supported using documented diagnostics without exposing sensitive information.
