# RetailBrainAI Architecture Governance

## Core documents

1. [Architecture Principles](01-Architecture-Principles.md)
2. [Architecture Decisions](02-Architecture-Decisions.md)
3. [Architecture Overview and Diagrams](03-Architecture-Overview-and-Diagrams.md)
4. [Agentic AI and Forecasting Architecture](04-Agentic-AI-and-Forecasting-Architecture.md)
5. [Final Production Architecture and Business Capabilities](05-Final-Production-Architecture-and-Business-Capabilities.md)

## Role of these documents

The architecture principles are mandatory design constraints for all SDK packs and application architectures. The architecture decision register records the accepted, deferred, rejected, and superseded choices that define the current platform baseline.

The architecture overview translates those principles and decisions into logical, runtime, data, security, and deployment views. Its diagrams describe ownership and interaction boundaries; an SDK box does not automatically imply a separately deployed microservice.

The agentic AI and forecasting architecture defines the supervisor and specialist agent portfolio, agent execution controls, tool and memory boundaries, forecasting lifecycle, forecast products, forecast-to-decision loop, human approvals, and closed-loop evaluation.

The final production architecture consolidates the approved platform architecture, all 32 SDK capabilities, application scenarios, functional coverage, data and integration design, security, deployment, operational quality gates, and customer-place acceptance criteria into one implementation reference.

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
- governed supervisor and specialist agent model;
- forecasting as an authoritative analytical platform capability;
- deterministic controls around probabilistic AI;
- versioned APIs, events, policies, prompts, agents, tools, forecasts, and AI resources;
- executable Claude Code prompts in each implementation pack;
- customer-deployable production quality rather than MVP or POC quality;
- final integrated architecture delivered in Markdown and HTML.

## Diagram and functional coverage

The architecture documents include:

- enterprise platform context;
- logical layer model and dependency rules;
- SDK capability map and ownership;
- knowledge ingestion and indexing sequence;
- grounded AI request sequence;
- governed supervisor and specialist agent architecture;
- agent delegation, evidence, forecast, tool, approval, and execution sequence;
- forecast pipeline and forecast-product architecture;
- forecast-to-decision and realized-outcome feedback loop;
- memory, tools, risk controls, and human-in-the-loop boundaries;
- data ownership, consistency and integration models;
- security and AI-specific control flows;
- initial runtime and deployment topology;
- Admin Portal, Copilot, Customer Service AI, Inventory Intelligence, Pricing, Promotion, Supply Chain AI and Executive Dashboard scenarios;
- observability, resilience, upgrade, rollback and customer acceptance requirements;
- three-person dependency and parallelization guidance;
- Claude implementation guidance in each SDK pack.

## Change process

Any material deviation requires an architecture decision that documents context, alternatives, rationale, consequences, migration impact, owner, and status.
