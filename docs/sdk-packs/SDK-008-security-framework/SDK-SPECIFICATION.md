# SDK-008 — Security Framework

**Phase:** 1 — Platform Foundation  
**Status:** Complete  
**Dependencies:** SDK-002–007  
**Purpose:** Authentication, authorization, identity propagation, and secrets.

## Required capabilities

- Authentication adapter contracts for enterprise identity providers and service identities.
- Principal model, roles/groups/claims, authorization policy evaluation, resource/action context, deny-by-default behavior, and decision reasons.
- Identity and authorization context propagation across HTTP, messages, events, workflows, jobs, AI calls, retrieval, and tools.
- Secret reference, retrieval, rotation, caching, and redaction contracts.
- Service-to-service authentication, key/certificate rotation, clock-skew handling, replay protection where relevant, and secure token validation.
- Current release is single-enterprise deployment; do not introduce tenant isolation.

## Production requirements

Threat model, secure defaults, at least one production identity and secret-store adapter, key rotation tests, authorization conformance suite, penetration/security testing, incident runbooks, audit integration, and customer identity onboarding documentation.

## Parallelization

Provider adapters are safe in parallel. Changes to principal or policy contracts affect nearly all SDKs and must be centrally reviewed and frozen during dependent work.

## Acceptance

Unauthorized access is denied across every transport, identity propagates end-to-end without raw credential propagation, secrets are never logged, rotation is tested, and customer administrators can configure identity and policies without code changes.
