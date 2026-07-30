# SDK-001 — Platform Standards & Common Types

**Phase:** 1 — Platform Foundation  
**Status:** Optional/internal; Complete  
**Dependencies:** None  
**Purpose:** Shared types, coding standards, and common utilities.

## Production scope

SDK-001 owns only stable platform-wide primitives already proven to be shared: identifiers, result/value abstractions, clock and ID generation ports, pagination, correlation metadata, compatibility annotations, serialization conventions, and coding standards. It must not become a miscellaneous utility library or absorb domain models owned by other SDKs.

## Required capabilities

- Immutable, serialization-safe common contracts with deterministic equality.
- Injectable time, randomness, and identifier generation.
- Published naming, nullability, versioning, and package-boundary rules.
- Static analysis and architecture tests that prevent circular dependencies and infrastructure coupling.
- Compatibility tests for every externally consumed primitive.

## Production requirements

Comply with [Production and Customer Deployment Standard](../PRODUCTION-DEPLOYMENT-STANDARD.md). SDK-001 has no runtime service, but its package must be signed/versioned, dependency-minimal, deterministic, and safe for customer builds. Breaking changes require an approved migration and coordinated downstream release.

## Parallelization

Validation may run alongside any SDK. Public contract changes must not run in parallel with downstream integration. Adapter or documentation-only work is safe because SDK-001 has no provider adapters.

## Acceptance

Inventory existing types, remove only verified duplication, retain domain ownership, pass serialization and compatibility tests, and document every public primitive and migration impact.
