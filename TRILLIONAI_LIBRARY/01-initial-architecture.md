# Macro engineering study 01 — verified architectural entry points

Date: 2026-11-14 (NZ)
Original project: https://github.com/macro-inc/macro
Verification basis: directly fetched upstream repository files from GitHub. This is an initial structural inspection, **not** a comprehensive security audit, full clone, or runtime test.

## Evidence table

| Source | Verified observations | What must be traced next |
|---|---|---|
| [AGENTS.md](https://github.com/macro-inc/macro/blob/main/AGENTS.md) | Repository describes Rust backend, web frontend, `apps/web`, `services`, `crates`, `infra`, database migrations and engineering guides. Coding agents are instructed to follow `CODING.md` and subtree rules. | Read full coding guide and actual CI rules; confirm tests execute and enforce requirements. |
| [agent_harness Cargo.toml](https://github.com/macro-inc/macro/blob/main/crates/agent_harness/Cargo.toml) | Agent harness depends on agent sessions, runtime protocol, triggers, billing/usage, authorization, event broker, Redis, Postgres, tracing and other connectors. | Entry points, scheduling, tool-call isolation, cancellation, retries, durable state, error propagation, approval gates. |
| [agent_trigger Cargo.toml](https://github.com/macro-inc/macro/blob/main/crates/agent_trigger/Cargo.toml) | Feature-gated event-trigger implementation separates domain vocabulary from optional outbound adapters and billing admission. | Event schema, deduplication, idempotency, delivery guarantees, dead-letter processing and race behavior. |
| [memory Cargo.toml](https://github.com/macro-inc/macro/blob/main/crates/memory/Cargo.toml) | Dedicated memory crate integrates scheduled actions, prompts, AI tooling, authorization, SQLx and HTTP service support. | Storage lifecycle, retrieval quality, consent, user isolation, expiry, deletion, injection resistance. |
| [macro_authorization Cargo.toml](https://github.com/macro-inc/macro/blob/main/crates/macro_authorization/Cargo.toml) | Authorization functionality is a standalone crate with bot/harness token dependencies and optional PostgreSQL features. | Resource checks at service boundaries, owner permissions, token scopes, tenant isolation and bypass tests. |
| [macro_event_broker Cargo.toml](https://github.com/macro-inc/macro/blob/main/crates/macro_event_broker/Cargo.toml) | Broker uses optional outbound Kafka libraries and correlation-related dependencies. | Publishing/outbox consistency, retries, consumer groups, message visibility and replay behavior. |
| [agent_harness_service Cargo.toml](https://github.com/macro-inc/macro/blob/main/services/agent_harness_service/Cargo.toml) | Deployable Rust service aggregates agent components, AWS SDK packages, API support and other domain integrations. | Network exposure, runtime service boundaries, request validation, telemetry and resource budgets. |

## Engineering conclusions — preliminary

1. **Clear subsystem boundaries:** independent modules are a useful architectural model, not evidence of correctness on their own.
2. **Domain vocabulary separate from adapters:** event definitions should not pull expensive infrastructure dependencies into every consumer.
3. **Agent permissions belong in backend enforcement:** neither UI hiding nor natural-language prompts constitute authorization.
4. **Operational costs need admission control:** verify usage ceilings, tenant quotas, per-task budgets and payment entitlement checks.
5. **Observability must identify actions:** correlate task, agent, session, customer, cost, tool invocation and verification status.
6. **Coding rules should be machine-checked:** architecture standards matter only when tests, CI and actual execution enforce them.

## Original TrillionAI application design

Recommended independent design for Flutter + Node.js/TypeScript:

- `apps/dashboard`: Flutter-based operator and customer dashboards.
- `services/manager-api`: authenticated Node.js HTTP API with tenant/role checks.
- `services/agent-worker`: durable task executor with idempotency and bounded tool access.
- `packages/domain-events`: typed event schemas and version compatibility.
- `packages/policy`: authorization, approval and cost admission decisions.
- `packages/memory`: scoped memory records with explicit retention and deletion.
- `packages/telemetry`: structured traces, progress/evidence records and alerts.
- `packages/contracts`: versioned API and message contracts consumed by Flutter clients.

These are **recommendations**, not claims that corresponding modules currently exist in TrillionAI repositories. Audit existing implementation before introducing or duplicating components.

## Next deeper investigations

1. Read agent harness runtime entry points, agent session and tool wrappers to trace a complete user request.
2. Read trigger and broker handlers to trace message-to-task workflow, retries and failure outcomes.
3. Read memory storage and authorization paths to inspect consent, isolation and prompt-injection handling.
4. Compare each verified finding with actual TrillionAI code and existing tests before proposing implementation changes.
5. Record exact upstream commit SHA on subsequent inspections to ensure findings remain reproducible.

## Licensing and provenance

All linked Macro source remains the copyright of its authors and is subject to its applicable licence (upstream AGPL-3.0). This document contains independent findings and design recommendations; it does **not** reproduce Macro implementation code. Do not combine Macro's licensed implementation with proprietary TrillionAI code without examining legal obligations.
