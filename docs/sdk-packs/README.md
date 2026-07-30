# RetailBrainAI SDK Implementation Packs

This directory is the implementation documentation index for the frozen SDK-001 through SDK-032 roadmap.

Each SDK folder contains:

- `SDK-SPECIFICATION.md` — purpose, boundaries, production functional requirements, architecture, contracts, security, observability, testing, customer-deployment expectations, acceptance criteria, and dependency/parallelization gates.
- `CLAUDE-IMPLEMENTATION.md` — staged Claude Code instructions for implementing or validating that SDK in the real project repository.

Portfolio execution guidance for the three-person team is defined in [TEAM-EXECUTION-AND-PARALLELIZATION.md](TEAM-EXECUTION-AND-PARALLELIZATION.md). Mandatory release quality is defined in [PRODUCTION-DEPLOYMENT-STANDARD.md](PRODUCTION-DEPLOYMENT-STANDARD.md).

## Governing constraints

1. The supplied SDK identifiers, names, purposes, dependencies, priorities, phases and completion states are the source of truth.
2. No additional SDK is introduced by these packs.
3. Phase 1 SDKs are complete. Their guides direct validation, conformance hardening and verified gap remediation, not unapproved replacement.
4. Every SDK must be production-grade and directly deployable in a customer-controlled environment. MVP, POC, mock-only and in-memory-only shortcuts do not satisfy completion.
5. Provider products remain behind adapters. Public domain/application contracts remain provider-neutral.
6. Current deployment is single-enterprise; tenant isolation is deferred.
7. Every implementation must comply with `docs/architecture` and the production deployment standard.
8. Downstream work may start against frozen contracts and test doubles, but production integration is incomplete until upstream conformance and end-to-end tests pass.
9. Customer deployment requires documented installation, secure configuration, migrations, monitoring, backup/restore, upgrade, rollback, runbooks and acceptance evidence.

## Recommended execution

Use one branch and one PR per SDK. Each of the three engineers works on only one SDK at a time. Shared dependency changes are delivered and accepted separately before dependent SDK branches consume them.
