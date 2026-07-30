# Claude Code Guide — SDK-003

```text
Validate SDK-003 as a production telemetry library.

Inspect logging contracts, context propagation, OpenTelemetry adapters, redaction, configuration, and downstream usage. Preserve compatibility.

Add missing structured schemas, correlation propagation for HTTP/messages/jobs/workflows, provider-neutral exporters, redaction tests, sampling/back-pressure controls, exporter outage isolation, benchmarks, dashboards, alert examples, customer configuration, and operations runbook.

Prove that sensitive values never enter normal logs and that telemetry failure cannot cause a business transaction failure. Coordinate any schema change across all consumers.
```
