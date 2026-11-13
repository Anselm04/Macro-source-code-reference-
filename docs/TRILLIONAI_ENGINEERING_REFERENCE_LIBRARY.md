# TrillionAI Engineering Reference Library — priority register

Updated: 2026-11-14 (Pacific/Auckland). This is a **candidate catalogue**, not proof the sources have been cloned or tested.

## Objective

Study verified real-world implementations, compare them to actual TrillionAI repository code, and produce original fixes. **AppForge end-to-end customer delivery remains the first commercial milestone.** No paid runtime tests, subscriptions, cloud provisioning, or production deployment without explicit approval.

## Prioritized reference candidates

| Priority | Candidate | Upstream | Source licence / important exclusions | TrillionAI application | Inspection target | Status |
|---|---|---|---|---|---|---|
| P0 | Macro | https://github.com/macro-inc/macro | AGPL-3.0; check bundled dependencies | Manager, AppForge, Identity | Agent harness, memory, events, authorization | **IMPORTED**: `macro-upstream-snapshot:upstream/`, 41,545 tracked files; commit `532fba5e60c14b91ae641619c32a58120b6b4546` |
| P0 | bolt.diy | https://github.com/stackblitz-labs/bolt.diy | MIT source; **WebContainers API commercial licence** applies for relevant production uses | AppForge | Prompt→files→preview→edit→deploy, project snapshots and provider integration | CANDIDATE |
| P0 | Dyad | https://github.com/dyad-sh/dyad | Apache-2.0 outside `src/pro/`; pro uses Functional Source License | AppForge | Local builder state, real file revisions, recovery and testing | CANDIDATE |
| P0 | LangGraph.js | https://github.com/langchain-ai/langgraphjs | MIT | AppForge, Manager | Agent state graph, persistence, resumability, tool invocation boundaries | CANDIDATE |
| P0 | Temporal | https://github.com/temporalio/temporal | MIT | AppForge, Manager | Durable workflows, retries, signals, idempotence and failure recovery | CANDIDATE |
| P1 | Trigger.dev | https://github.com/triggerdotdev/trigger.dev | Apache-2.0 top-level; check subdirectories and dependencies | Manager, Marketing | TypeScript background task runtime, retry behavior, queues | CANDIDATE |
| P1 | Appwrite | https://github.com/appwrite/appwrite | BSD-3-Clause | Identity, AppForge | Signup/session state, service boundaries, workers, storage | CANDIDATE |
| P1 | Activepieces | https://github.com/activepieces/activepieces | MIT Community Edition; **commercial enterprise sections excluded** | Marketing, Manager | External connectors, workflow triggers, auth integration | CANDIDATE |
| P1 | OpenTelemetry JS | https://github.com/open-telemetry/opentelemetry-js | Apache-2.0 | Observability | Distributed tracing, correlation, instrumentation | CANDIDATE |
| P1 | Keycloak | https://github.com/keycloak/keycloak | Apache-2.0 (verify bundled modules) | Identity | OIDC, MFA, session revocation, authorization | CANDIDATE |
| P2 | Coolify | https://github.com/coollabsio/coolify | Apache-2.0 (check per-component licence) | AppForge | Customer-controlled deployments, credential boundaries, lifecycle | CANDIDATE |
| P2 | Medusa | https://github.com/medusajs/medusa | MIT core; **enterprise materials licensed separately** | Manager and future commerce applications | Product/order/transaction modelling and integrations | CANDIDATE |
| P2 | Twenty | https://github.com/twentyhq/twenty | Primarily AGPLv3; separate commercial and MIT-labelled parts | Marketing, Manager | CRM domain modelling and multi-tenant access patterns | RESEARCH-ONLY |
 
### Priority engineering questions

**AppForge first:** Compare how an authenticated user creates an application, pays, obtains entitlement, runs a real generation job, previews, edits files, saves/reopens, exports and deploys. Trace concrete code paths in both projects. Do not assume a README assertion proves a functioning customer journey.

**Manager second:** Durable queue, task ledger, bounded AI tool permissions, approval before spending, error recovery, idempotency, and evidence records.

**Identity and Observability third:** MFA/session enforcement, access boundaries, structured traces, alert lifecycle and incident response.

**Marketing, Secure, TrillionEngine and future products:** Add reference candidates only for identifiable milestones, so reference collection does not displace engineering delivery.

## Import policy

- One **immutable upstream snapshot per source project**, with upstream SHA, full tracked tree and audit log.
- Preserve licence and attribution. Keep imports in independent reference repositories when possible; never insert upstream source directly into commercial product repositories.
- Treat Git LFS payloads, submodules, generated files and private production infrastructure as separate verification items.
- Do not execute source code automatically: imported repositories are **untrusted**. Review workflows, scripts, dependencies and supply-chain security before any build.
- Never infer commercial reuse rights from a repository being public or from modifying code superficially.
- For mixed/open-core licences, isolate applicable subdirectories and review restrictions before any incorporation.
- Comparing architecture and writing independently implemented Flutter/Node.js code is the default.

## Comparison evidence template

For each candidate feature:
1. Customer-visible behaviour proven (source, running demo or end-to-end test).
2. Upstream source paths + immutable commit SHA.
3. Corresponding TrillionAI repo, commit and implementation paths.
4. Observed fault / missing element / design trade-off.
5. Test reproducing fault or establishing baseline.
6. Original TrillionAI design and repair PR.
7. CI results and production/runtime evidence (do not confuse mocks with live checks).
8. Security, licence, reliability and unit-cost review.

## Ownership and outcomes

- Every source study must have **one concrete engineering question** and a defined exit condition.
- A candidate is not considered imported until source commit and tree/hash verification pass.
- Never claim TrillionAI is production-ready without real customer-journey verification.
