# RetailBrainAI Architecture Governance

## Core documents

1. [Architecture Principles](01-Architecture-Principles.md)
2. [Architecture Decisions](02-Architecture-Decisions.md)
3. [Architecture Overview and Diagrams](03-Architecture-Overview-and-Diagrams.md)

## Role of these documents

The architecture principles are mandatory design constraints for all SDK packs and application architectures. The architecture decision register records the accepted, deferred, rejected, and superseded choices that define the current platform baseline.

The architecture overview translates those principles and decisions into logical, runtime, data, security, and deployment views. Its diagrams describe ownership and interaction boundaries; an SDK box does not automatically imply a separately deployed microservice.

Every SDK implementation pack shall reference these documents and must not introduce contradictory assumptions without a new architecture decision record.

## Current baseline highlights

- frozen SDK-001 through SDK-032 roadmap;
- capability-oriented modular platform;
- contract-first ports-and-adapters design;
- provider-neutral domain and application logic;
- modular deployment before service decomposition;
- durable asynchronous execution for long-running work;
- event-driven integration with at-least-once semantics;
- authoritative durable state with rebuildable projections;
- single-enterprise deployment for the current release;
- multi-tenancy deferred to a future architecture stage;
- deterministic controls around probabilistic AI;
- versioned APIs, events, policies, prompts, and AI resources;
- executable Claude Code prompts in each implementation pack;
- final integrated architecture delivered in Markdown and HTML.

## Diagram coverage

The architecture overview includes:

- enterprise platform context;
- logical layer model and dependency rules;
- SDK capability map;
- knowledge ingestion and indexing sequence;
- grounded AI request sequence;
- initial runtime and deployment topology;
- data ownership and consistency model;
- security control flow;
- observability, resilience, evolution, and Claude implementation guidance.

## Change process

Any material deviation requires an architecture decision that documents context, alternatives, rationale, consequences, migration impact, owner, and status.
