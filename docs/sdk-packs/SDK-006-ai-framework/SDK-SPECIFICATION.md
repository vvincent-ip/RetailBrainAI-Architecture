# SDK-006 — AI Framework

**Phase:** 1 — Platform Foundation  
**Status:** Complete  
**Dependencies:** SDK-002–005  
**Purpose:** LLM abstraction, prompt execution, tool calling, and provider independence.

## Required capabilities

- Provider-neutral chat/completion, embedding where retained by current implementation, structured output, streaming, and tool-call contracts.
- Model registry and routing by capability, policy, availability, cost, latency, region, and data-classification constraints.
- Request budgets, timeouts, cancellation, bounded retries, circuit breaking, rate limiting, concurrency controls, and usage/cost telemetry.
- Normalized responses with provider/model/version, finish reason, token/usage metadata, safety signals, and correlation identifiers.
- Tool calls are proposals until validated and executed through governed tool contracts; the model never receives unrestricted infrastructure access.
- Prompt management lifecycle belongs to SDK-022; evaluation belongs to SDK-023; knowledge grounding belongs to SDK-011; agents belong to SDK-012.

## Production requirements

Provide at least one production-capable provider adapter, secure customer configuration, regional/data handling notes, fallback policy, chaos and load tests, cost controls, provider outage runbook, compatibility matrix, and model-change governance.

## Parallelization

New provider adapters preserving contracts are safe alongside other SDKs. Public AI request/response and tool-call contract changes directly affect SDK-011, SDK-012, and SDK-022–025 and require coordination.

## Acceptance

Customer deployment can switch approved providers through configuration, enforces budgets and policy, survives provider faults predictably, emits safe telemetry, and produces reproducible normalized contracts.
