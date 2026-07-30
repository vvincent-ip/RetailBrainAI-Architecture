# Three-Person SDK Execution and Parallelization Plan

## 1. Objective

This plan schedules the frozen SDK-001 through SDK-032 roadmap for a team of three engineers. Each engineer implements only one SDK at a time. Parallel work is permitted only when dependency contracts are already accepted or when the work is isolated to provider adapters, documentation, tests, fixtures, or downstream code built against approved mocks.

## 2. Non-negotiable dependency rule

An SDK may enter full implementation only after every listed primary dependency has an accepted public contract and passing baseline conformance tests. A downstream SDK may start earlier in **contract-first mode** when it uses only published interfaces and test doubles; it may not claim integration completion until upstream dependencies are available and the integration test suite passes.

## 3. Work classifications

- **Safe parallel:** no unresolved dependency edge between the SDKs and no shared contract is being edited.
- **Contract-first parallel:** a downstream SDK can implement domain and application layers against frozen upstream ports and mocks, but adapter integration is gated.
- **Do not parallelize:** one SDK directly depends on another whose contracts are still changing, or both efforts modify the same shared public contracts.

## 4. Recommended delivery waves

### Wave 0 — Baseline verification

The three engineers validate completed Phase 1 SDKs without rebuilding them:

- Engineer A: SDK-002, then SDK-003, then SDK-004.
- Engineer B: SDK-005, then SDK-010.
- Engineer C: SDK-006, then SDK-007, then SDK-008, then SDK-009.

SDK-001 is optional/internal and should be reviewed only where the existing codebase already uses it. Any breaking deficiency discovered in a Phase 1 contract is resolved before Phase 2 implementation.

### Wave 1 — Highest-priority knowledge foundation

- Engineer A: SDK-011 Knowledge & Context.
- Engineer B: SDK-014 Scheduler & Background Jobs after SDK-007 and SDK-010 validation.
- Engineer C: SDK-013 Rules & Decision Engine after SDK-007, SDK-008, and SDK-009 validation.

SDK-011, SDK-013, and SDK-014 have no dependency on one another and are safe to implement concurrently after Phase 1 validation.

### Wave 2 — Agents and independent enterprise operations

- Engineer A: SDK-012 Agent Framework after SDK-011 contracts are frozen.
- Engineer B: SDK-015 Notification Framework.
- Engineer C: SDK-016 File & Document Framework.

SDK-012, SDK-015, and SDK-016 are safe in parallel. SDK-012 is gated by SDK-006, SDK-007, and SDK-011. SDK-015 is gated by SDK-005 and SDK-010. SDK-016 is gated by SDK-008 and SDK-009.

### Wave 3 — Reporting, search, and audit

- Engineer A: SDK-018 Search Framework after SDK-011 retrieval representations are accepted.
- Engineer B: SDK-017 Reporting Framework after SDK-015 contracts are accepted.
- Engineer C: SDK-019 Audit Framework.

These are safe in parallel when their listed dependencies are stable. SDK-018 must not redefine SDK-011 knowledge lifecycle ownership.

### Wave 4 — Compliance, flags, and prompt management

- Engineer A: SDK-020 Compliance Framework after SDK-019.
- Engineer B: SDK-021 Feature Flag Framework.
- Engineer C: SDK-022 Prompt Management Framework.

These are safe in parallel. SDK-021 depends only on configuration. SDK-022 depends on the completed AI framework.

### Wave 5 — Evaluation, memory, and tool marketplace

- Engineer A: SDK-023 AI Evaluation after SDK-022 and SDK-011.
- Engineer B: SDK-024 AI Memory after SDK-011.
- Engineer C: SDK-025 AI Tool Marketplace after SDK-012.

These are safe in parallel once the stated dependencies are accepted. Coordinate only on shared AI metadata identifiers; do not edit SDK-006 contracts independently.

### Wave 6 — Distributed platform services

- Engineer A: SDK-026 Service Discovery.
- Engineer B: SDK-027 Distributed Cache.
- Engineer C: SDK-029 API Gateway.

These are safe in parallel. SDK-029 uses SDK-008 and SDK-010 but does not depend on SDK-026 or SDK-027 in the roadmap.

After SDK-027 is accepted:

- The first available engineer implements SDK-028 Distributed Locking.

Do not implement SDK-028 concurrently with active breaking changes to SDK-027 contracts.

### Wave 7 — Analytics, recommendations, and forecasting

- Engineer A: SDK-030 Analytics Framework.
- Engineer B: SDK-031 Recommendation Engine after SDK-023.
- Engineer C: prepares SDK-032 domain contracts, fixtures, and test harness while SDK-030 is being completed.

SDK-031 and SDK-030 are safe in parallel. SDK-032 depends on SDK-030, so only contract-first preparation is safe until SDK-030 public metrics and analytical data contracts are accepted. Full SDK-032 implementation starts after SDK-030 acceptance.

## 5. Pairwise impact notes

- SDK-011 can run alongside SDK-013, SDK-014, SDK-015, SDK-016, SDK-019, SDK-021, SDK-022, SDK-026, SDK-027, or SDK-029, provided Phase 1 contracts are stable.
- SDK-012 must wait for stable SDK-011 contracts but can run alongside SDK-015 through SDK-017, SDK-019 through SDK-022, SDK-026, SDK-027, and SDK-029.
- SDK-013 is independent of SDK-011 and SDK-012; application-level pricing or promotion integration is future scope.
- SDK-014 is independent of SDK-011 through SDK-013 but may later host their recurring jobs through adapters.
- SDK-015 and SDK-016 are independent of each other.
- SDK-017 is blocked by SDK-015 but independent of SDK-018 and SDK-019.
- SDK-018 is blocked by SDK-011 but independent of SDK-017 and SDK-019.
- SDK-019 is independent of SDK-011 through SDK-018 at implementation time; other SDKs emit audit contracts through adapters.
- SDK-020 is blocked by SDK-019.
- SDK-021 is broadly independent and can fill a scheduling gap after SDK-002 validation.
- SDK-022 is independent of SDK-011 implementation, but SDK-023 later requires both.
- SDK-023 is blocked by SDK-011 and SDK-022.
- SDK-024 is blocked by SDK-011.
- SDK-025 is blocked by SDK-012.
- SDK-026 and SDK-027 are independent.
- SDK-028 is blocked by SDK-027.
- SDK-029 is independent of SDK-026 through SDK-028 according to the supplied roadmap.
- SDK-030 can run alongside SDK-031 once SDK-031 dependencies are ready.
- SDK-031 is blocked by SDK-011 and SDK-023.
- SDK-032 is blocked by SDK-009, SDK-011, and SDK-030.

## 6. Branch and ownership controls

Each engineer uses one branch per SDK and owns that SDK's public contracts during implementation. Shared dependency changes require a separate dependency PR and approval before downstream SDK branches consume them. Avoid combining multiple SDK implementations in one PR.

## 7. Definition of ready

An SDK is ready when its dependencies have accepted contracts, the specification has no unresolved architecture questions, security classifications are defined, test fixtures exist, and the implementation prompt identifies the exact repository modules to inspect.

## 8. Definition of done

An SDK is done only when public contracts, implementation, provider-neutral ports, at least one reference adapter where required, unit tests, contract tests, integration tests, security tests, observability, examples, migration notes, and acceptance criteria are complete. Downstream compilation against mocks alone is not integration completion.
