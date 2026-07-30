# SDK-004 — Error Framework

**Phase:** 1 — Platform Foundation  
**Status:** Complete  
**Dependencies:** SDK-002, SDK-003  
**Purpose:** Platform error model, classifications, and retry semantics.

## Required capabilities

- Stable error code, category, severity, retryability, safe message, correlation ID, causal chain, and optional structured details.
- Distinguish validation, authentication, authorization, not-found, conflict, concurrency, quota, dependency, timeout, transient, permanent, and internal failures.
- Map provider exceptions to platform errors at adapter boundaries.
- Separate customer-safe responses from internal diagnostic details.
- Retry guidance must be explicit and bounded; errors do not execute retries themselves.
- HTTP, messaging, workflow, and background-job mappings with compatibility tests.

## Production requirements

Maintain an error catalog, support documentation, localization-ready safe messages, telemetry mapping, security review against information disclosure, and release compatibility guarantees.

## Parallelization

Nonbreaking catalog additions are safe. Changes to categories, retry semantics, or transport mappings are cross-platform and must not occur concurrently with dependent SDK integration.

## Acceptance

All provider errors are normalized, customer responses leak no sensitive internals, retry classifications are tested, and support can resolve incidents using stable codes and correlation data.
