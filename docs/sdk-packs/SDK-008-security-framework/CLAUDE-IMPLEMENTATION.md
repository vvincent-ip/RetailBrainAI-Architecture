# Claude Code Guide — SDK-008

```text
Validate SDK-008 for direct customer production deployment.

Review authentication, principal, authorization, identity propagation, secret handling, adapters, configuration, and all consumers. Build a threat model and gap report first.

Implement missing deny-by-default policies, role/group/claim evaluation, resource/action context, cross-transport identity propagation, service identity, token validation hardening, secret references/rotation/redaction, production adapters, authorization conformance tests, penetration-oriented tests, security telemetry, customer onboarding guide, and incident runbooks.

Do not add tenant isolation. Do not propagate raw credentials. Any public principal or policy change requires coordinated compatibility approval.
```
