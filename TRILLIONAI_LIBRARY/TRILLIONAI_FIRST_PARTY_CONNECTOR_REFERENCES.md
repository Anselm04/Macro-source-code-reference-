# TrillionAI First-Party Plugins and Connector Independence Reference Plan

Verified research date: 2026-11-14 (New Zealand).

## Business objective

Develop a **TrillionAI Connect** plugin runtime and first-party connector SDK shared by AppForge, Marketing and Manager. Reduce avoidable payments to workflow/connector middleware vendors. Preserve customer ownership, scoped authorizations, revocation and auditing.

**Important boundary:** A self-built connector does **not** eliminate third-party API fees, model inference costs, social-platform restrictions, payment processing fees, network/compute costs, SMS delivery charges, or external accounts required by providers. The objective is lower *total cost of ownership*, not zero infrastructure cost.

## Reuse verified reference material before importing anything

| Reference already archived | Location | What to study | Risk |
|---|---|---|---|
| Activepieces | https://github.com/Anselm04/Activepieces-Source-Code-Reference/tree/activepieces-upstream-snapshot/upstream | MIT-licensed pieces/connector interfaces, triggers/actions, package versioning, polling, webhooks | Exclude separate `packages/ee/` and `packages/server/api/src/app/ee` commercial components from proprietary reuse |
| Trigger.dev | https://github.com/Anselm04/TriggerDev-Source-Code-Reference/tree/trigger-dev-upstream-snapshot/upstream | Durable tasks, retry backoff, concurrency, scheduled connector sync | Running background workers still incurs compute |
| LangGraph.js | https://github.com/Anselm04/LangGraph-Source-Code-Reference/tree/langgraph-upstream-snapshot/upstream | Permissioned agent tools and checkpointed tasks | Agents must never receive arbitrary unbounded customer credentials |
| Keycloak | https://github.com/Anselm04/Keycloak-Source-Code-Reference/tree/keycloak-upstream-snapshot/upstream | OAuth2/OIDC, token lifecycle and authorization | Do not write bespoke security cryptography |
| OpenTelemetry JS | https://github.com/Anselm04/OpenTelemetry-Source-Code-Reference/tree/opentelemetry-js-upstream-snapshot/upstream | Traces/metrics for each connector call | Redact credentials and customer data in telemetry |

## New dedicated reference repositories — priority

Only references explicitly marked **VERIFIED** have been imported and checked; the others have not. Create one repository per source to preserve clean separation, public only for redistributable upstream material.

| Priority | Suggested repository name | Original upstream GitHub | Licence / legal check | Product use |
|---|---|---|---|---|
| P0 | **[MCP-TypeScript-SDK-Source-Code-Reference](https://github.com/Anselm04/MCP-TypeScript-SDK-Source-Code-Reference/tree/mcp-typescript-sdk-upstream-snapshot/upstream)** — **VERIFIED, 1,253 files** | https://github.com/modelcontextprotocol/typescript-sdk | Mixed MIT/Apache-2.0, with CC-BY-4.0 documentation terms; upstream `919bb8ea88b6e10e72c2f8b6218fad4cfdc40b2c`, tree `32137c3eb5b46afa7f783231b0eed90b21ae9ed5` | Native TrillionAI plugin contract, secure Node.js MCP tools and agent integration |
| P0 | **[NodeRED-Source-Code-Reference](https://github.com/Anselm04/NodeRED-Source-Code-Reference/tree/node-red-upstream-snapshot/upstream)** — **VERIFIED, 1,551 files** | https://github.com/node-red/node-red | Apache-2.0; upstream `e4f7fc516cd8da1b4b4d571169cf6937b500bb30`, tree `836c91b89faddaee02dac01506f3cdb90ea7bbd3`; third-party nodes have own licences | Event-driven triggers, plugin discovery, flow-node lifecycle |
| P0 | **[OpenID-Client-Source-Code-Reference](https://github.com/Anselm04/OpenID-Client-Source-Code-Reference/tree/openid-client-upstream-snapshot/upstream)** — **VERIFIED, 292 files** | https://github.com/panva/openid-client | MIT; upstream `7eb59483b44241d843a96903e5c7a09a747f6b06`, tree `a95f14972a41c0f69d95d92a686692c3fe5a19a6`; review dependencies/provider requirements | Secure OAuth/OIDC consent, refresh/revoke, delegated app connections |
| P1, study first | `Nango-Source-Code-Reference` | https://github.com/NangoHQ/nango | Elastic License: **not MIT/Apache**, review restrictions on SaaS/managed connector competition before mirroring/using code | OAuth and multi-tenant integration comparison |
| P1, study first | `Airbyte-Connectors-Source-Code-Reference` | https://github.com/airbytehq/airbyte | Mixed connector licences including ELv2; identify per-connector licence and any restrictions before transfer | ETL, data sync, incremental cursors and schema evolution |
| RESEARCH ONLY | Pipedream | https://github.com/PipedreamHQ/pipedream | Pipedream Source Available License; not general OSS and may restrict competing services. Do not import by default. | Compare connector authoring patterns by reading upstream only |

Official reference licensing documents:
- https://www.activepieces.com/docs/about/license
- https://github.com/modelcontextprotocol/typescript-sdk
- https://nodered.org/about/license/
- https://github.com/panva/openid-client
- https://github.com/NangoHQ/nango
- https://github.com/airbytehq/airbyte/blob/master/docs/community/licenses/README.md
- https://github.com/PipedreamHQ/pipedream/blob/master/LICENSE

## Authoritative new production component (private, **not** a mirror)

**Recommended private repository:** `Anselm04/TrillionAI-Connect`.
It will be our own product component, not a third-party source mirror. It should have:
- Node.js + TypeScript API: connector manifests, capability names, input/output schema, versioned actions/triggers; signed packages + allowlist and supply-chain/SBOM checks.
- Authorization broker: customer-scoped OAuth2 PKCE, encryption at rest, refresh, rotation, revocation, least privilege; no secrets in GitHub, logs or prompts.
- Connector runtime: queue-based dispatch, rate-limit buckets, exponential backoff, idempotency keys, webhook signatures, DLQ, circuit breakers and per-customer quotas.
- Consent/approval boundaries: read/write permissions; explicit user confirmation on sending messages, ads, publishing and payments; limit monetary risk by default.
- Tenant isolation and usage: isolated credentials; provider calls tagged with customer, connector and billing entitlement; budget ceilings and accurate cost attribution.
- Flutter frontend: integrations marketplace, add/connect/disconnect, scope preview, status, permissions, usage and error recovery.
- MCP adapter: expose authorized capabilities as typed tools, but delegate credential handling to backend; no arbitrary execution.
- Native connector contracts first: GitHub, Stripe, Supabase, Cloudflare, Google OAuth-supported services, social publishing APIs only where granted, analytics and webhooks; prioritize existing customer use cases over quantity.

## Engineering milestones and proof

1. Audit actual existing integration code in all three TrillionAI repositories and list subscription/connector vendors with actual invoiced or documented costs.
2. Define shared provider-independent connector manifest + typed contract, security boundary and tests.
3. First real connector: GitHub read and permissioned write, with scoped credential and test account; prove connect, use, revoke, error and audit.
4. Next: Stripe events and subscriptions, Google-supported integrations, Meta publishing (subject to app review and platform rules), analytics.
5. Implement safe marketing automation: customer authorizes connections and scheduled content; no unsolicited outreach; spend always explicit and bounded.
6. Instrument metrics: costs per 1,000 connector executions, monthly retained vendor fees, self-hosted compute, failures, engineering maintenance effort and API usage.
7. Only replace a paid intermediary when a verified native connector provides equivalent end-to-end reliability at lower projected *total cost*.

Every imported reference must have original SHA, licence audit, file counts, and remote Git-tree verification. Exclude files that GitHub secret scanning flags; never disable/bypass push protection or remove licence notices.
