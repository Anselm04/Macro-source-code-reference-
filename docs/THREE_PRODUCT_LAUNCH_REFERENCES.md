# TrillionAI Tech — Three-Product Launch Reference Library

Last research verification: 2026-11-14 (NZ time).

**Launch objective:** AppForge + TrillionAI Marketing + TrillionAI Manager, each commercially usable with a working end-to-end customer journey, connected where necessary through shared authorized services. This repository is a source study area, never a production build dependency.

## Evidence standard

- **LIVE PAID OFFERING** means the company has a public product website and an official price/paid-plan or hosted-plan page; it **does not prove actual sales, MRR, profitability, customer count or availability of every advertised capability**.
- **OPEN SOURCE / SOURCE AVAILABLE** indicates the GitHub repository exists; it **does not establish that the entire commercial cloud backend is public**.
- **IMPORTED VERIFIED** means an immutable snapshot branch has passed exact Git-tree comparison against a particular upstream commit. Not the full Git history, private deployment configuration, all LFS payloads or nested submodules.
- Licence classification is *preliminary*: inspect the exact files and third-party dependencies before reusing any implementation. Source-code studies use independent design; proprietary TrillionAI code is never contaminated by copying restricted sections.

## Current verified library size

**16 verified source snapshots · 293,294 retained Git-tracked files** across sixteen dedicated repositories, including the licence-filtered Twenty and PostHog snapshots. Git tree checks passed individually. Source-file counts are not measurements of line count, security quality, or commercial completeness.

## Launch-critical reference projects

| Priority | Product | Official upstream GitHub | Live commercial evidence | Licence boundary | TrillionAI target | What to inspect | Source status |
|---|---|---|---|---|---|---|---|
| L0 | Macro | https://github.com/macro-inc/macro | https://macro.com/pricing/ (paid per-seat offering) | AGPL-3.0; third-party code may vary | **Manager** | Agent sessions, context/memory, permissions, event broker, task lifecycle | **VERIFIED** [41,545 files](https://github.com/Anselm04/Macro-source-code-reference-/tree/macro-upstream-snapshot/upstream) |
| L0 | Dyad | https://github.com/dyad-sh/dyad | https://www.dyad.sh/plans (Pro/Max subscriptions offered) | Apache-2.0 outside `src/pro/`; `src/pro/` FSL 1.1 | **AppForge** | Generate, persist, edit, recover, preview | **VERIFIED** [4,052 files](https://github.com/Anselm04/Dyad-Source-Code-Reference/tree/dyad-upstream-snapshot/upstream) |
| L0 | bolt.diy | https://github.com/stackblitz-labs/bolt.diy | https://bolt.new/ (related paid Bolt product; **not evidence of bolt.diy revenue**) | MIT code; WebContainers commercial licence separate | **AppForge** | Agent-to-file pipeline, editor, runtime preview | **VERIFIED** [720 files](https://github.com/Anselm04/Bolt-DIY-Source-Code-Reference/tree/bolt-diy-upstream-snapshot/upstream) in dedicated research repository |
| L0 | Trigger.dev | https://github.com/triggerdotdev/trigger.dev | https://trigger.dev/pricing/ (paid hosted workflow tiers) | Apache-2.0, audit subtrees | **Manager + Marketing + AppForge** | Durable workflows, retries, schedules, concurrency, status reporting | **VERIFIED** [7,940 files](https://github.com/Anselm04/TriggerDev-Source-Code-Reference/tree/trigger-dev-upstream-snapshot/upstream) in dedicated repository; upstream `2fbd5c7cf4e9c8e19b88e2b72a7133795611e33d`; tree `c87759655a420817332da8d187a48265f2e41b03` |
| L0 | Activepieces | https://github.com/activepieces/activepieces | https://www.activepieces.com/pricing (paid cloud/enterprise/embedded products) | MIT community core; commercial `packages/ee` and enterprise server paths | **Marketing + Manager** | Connector patterns, consented automation, flow versioning | **VERIFIED** [36,504 files](https://github.com/Anselm04/Activepieces-Source-Code-Reference/tree/activepieces-upstream-snapshot/upstream) in dedicated repository; upstream `b9f66339ed218e564a645d5c8d23e632e9b2d90c`; tree `d5602f7f09abf4ad8f7c03a95a659485de940d74` |
| L0 | Twenty | https://github.com/twentyhq/twenty | https://twenty.com/pricing (paid cloud CRM) | AGPLv3/selected MIT packages; commercial-marked files excluded from public mirror | **Marketing + Manager** | CRM leads, workspaces, tenancy, workflows, onboarding | **VERIFIED FILTERED** [43,697 retained files](https://github.com/Anselm04/Twenty-Source-Code-Reference/tree/twenty-upstream-snapshot/upstream), 825 commercial-marked application files excluded; original LICENSE retained; upstream `1dd1c249ad213de6883be5296deb3bbba8420a22`; retained tree `dc9e1541d5d24bc4ec18a12d95bfd71a59e51490` |
| L1 | OpenHands | https://github.com/OpenHands/OpenHands | https://www.openhands.dev/pricing/ (hosted/enterprise offerings) | MIT core; **separate OpenHands-Cloud has non-OSS Polyform restrictions** | **AppForge** | Tool execution, coding agent lifecycle, sandbox and validation | **VERIFIED** [2,916 files](https://github.com/Anselm04/OpenHands-Source-Code-Reference/tree/openhands-upstream-snapshot/upstream) in dedicated research repository; upstream `46f20abafecbd03c422213bff4bc4499607b9b4f`; tree `3c7ae35db4ee1c485551cdf9ad79366852354426` |
| HISTORICAL ONLY | Flowise | https://github.com/FlowiseAI/Flowise | https://flowiseai.com/sunset (project announced shutdown, code freeze July 29 2026 and EOL Aug 31 2026; older pricing pages are stale) | Apache-2.0 source | **Manager, historical comparison only** | Agent graphs, tooling and archived implementation patterns | **NOT an active paid commercial reference; do not import in launch-priority list** |
| L1 | PostHog | https://github.com/PostHog/posthog | https://posthog.com/pricing (paid usage tiers) | MIT community source; separately licensed root `ee/` omitted | **Marketing + Manager + AppForge** | Funnels, campaigns analytics, cohorts, usage telemetry, feature flags | **VERIFIED FILTERED** [71,145 files](https://github.com/Anselm04/PostHog-Source-Code-Reference/tree/posthog-upstream-snapshot/upstream), 839 enterprise files excluded; upstream `a081bda2be64e0520cec834fab22e1d66a670864`; filtered tree `012523f26af8f806b43d98a24387b430154721ef` |
| L1 | Chatwoot | https://github.com/chatwoot/chatwoot | https://www.chatwoot.com/pricing (paid agent plans) | Mixed/open-core; verify repository licence and enterprise dirs | **Marketing + Manager** | Inbound support, customer messaging, escalation, ticket handling | **VERIFIED** [10,015 files](https://github.com/Anselm04/Chatwoot-Source-Code-Reference/tree/chatwoot-upstream-snapshot/upstream) in dedicated repository; upstream `1ef1d2b45ae0a17a35c5f1bd055e4ddf04dadabf`; tree `0d8bda9062fcc80ee5330d669ea550fb4053d402` |
| L1 | Appwrite | https://github.com/appwrite/appwrite | https://appwrite.io/pricing (cloud tiers) | BSD-3-Clause upstream; dependencies separately licensed | **AppForge/shared customer backend** | Registration, sessions, storage, queues, functions, persistent data | **VERIFIED** [16,673 files](https://github.com/Anselm04/Appwrite-Source-Code-Reference/tree/appwrite-upstream-snapshot/upstream) in dedicated repository; upstream `8d5559c74e9d8ef336713cabfb9b512fdb86c5b1`; tree `9b3935082e0eda53bc811eb0d786ca9a96fe38c7` |
| L1 | Temporal | https://github.com/temporalio/temporal | https://temporal.io/pricing (commercial Temporal Cloud; source is separate) | MIT | **Manager + AppForge** | Durable workflows, retry/idempotency, fault recovery and history | **VERIFIED** [4,198 files](https://github.com/Anselm04/Temporal-Source-Code-Reference/tree/temporal-upstream-snapshot/upstream); upstream `98925be15707693868c3a900a5d41df126da7fdf`; tree `6d462212d9c308ef9e56f9d7e5cf72d3731861b7` |
| L1 | Coolify | https://github.com/coollabsio/coolify | https://coolify.io/ (hosted commercial offerings; revenue not independently verified) | Apache-2.0, with sensitive key-bearing fixtures excluded | **AppForge + Manager** | Application deployment, container runtime, environment handling and recovery | **VERIFIED FILTERED** [5,452 files](https://github.com/Anselm04/Coolify-Source-Code-Reference/tree/coolify-upstream-snapshot/upstream); 48 SSH private-key-bearing or related files excluded; upstream `93c7e53e9f07bfdb1c776899cb2e559e5a49aa34`; filtered tree `0c4275fa9feaf5eb8e74ad782e51762d82003022` |
| L1 | Keycloak | https://github.com/keycloak/keycloak | https://www.keycloak.org/ (open-source IAM platform; **not a verified paid product of Keycloak itself**) | Apache-2.0; review component-specific licensing | **Identity + all launch products** | OAuth2/OIDC, sessions, identity federation, MFA, authorization | **VERIFIED** [13,621 files](https://github.com/Anselm04/Keycloak-Source-Code-Reference/tree/keycloak-upstream-snapshot/upstream); upstream `a29205c778402c02bad1d90b00c390f923d059ac`; tree `a620948522cd495a1f44b782a8b131a37c39994e` |
| L1 | LangGraph.js | https://github.com/langchain-ai/langgraphjs | https://www.langchain.com/pricing (LangSmith commercial service, **distinct from OSS library**) | MIT | **Manager + AppForge** | Stateful agent graphs and checkpoints | **VERIFIED** [2,073 files](https://github.com/Anselm04/LangGraph-Source-Code-Reference/tree/langgraph-upstream-snapshot/upstream); upstream `62e40b998f769ccf9d872d394d2fd3d6796a0ddf`; tree `c534cd4169babeba9499f1c38363a88782f12961` |
| L2 | Medusa | https://github.com/medusajs/medusa | https://medusajs.com/pricing (paid Medusa Cloud) | MIT community code; 265 enterprise-licensed paths excluded according to ENTERPRISE-LICENSE.md | **Shared commercial services** | Events, orders, webhooks, transactions, subscriptions integration patterns | **VERIFIED FILTERED** [25,032 files](https://github.com/Anselm04/Medusa-Source-Code-Reference/tree/medusa-upstream-snapshot/upstream), 265 restricted files excluded; upstream `01de0be27a7c228795d5cfc31662ca144781fbfc`; filtered tree `9dfde825357225687b752656368e03a89919c711` |
| L2 | Cal.com / Cal.diy | https://github.com/calcom/cal.diy | https://cal.com/pricing (Cal.com commercial product, **production source private since April 2026**; community Cal.diy has no verified sales) | MIT community Cal.diy; one OAuth-token YAML fixture excluded | **Manager + Marketing** | Scheduling, booking, calendar integration and notification patterns | **VERIFIED FILTERED** [7,711 files](https://github.com/Anselm04/CalCom-Source-Code-Reference/tree/cal-diy-upstream-snapshot/upstream); upstream `ae027bb70e694e2d2c44569f398d6cbcee0389b1`; filtered tree `917c9be2f9a11a6a0b3d7888ff38fcc76e5a8471` |
| L2 | Plane | https://github.com/makeplane/plane | https://plane.so/pricing (paid team plans) | Mixed licensing, check before reuse | **Manager** | Work queues, operations dashboards, task dependencies | RESEARCH CANDIDATE |
| RESEARCH ONLY | n8n | https://github.com/n8n-io/n8n | https://n8n.io/pricing (paid hosted automation) | Sustainable Use License + enterprise licence; **not standard open-source**, customer-facing workflow SaaS may require commercial licensing | **Manager + Marketing** | Compare patterns ONLY; do not embed or copy its implementation | NO IMPORT PLANNED without separate review |

## Strict transfer order

1. **Already verified:** Macro, Dyad, bolt.diy.
2. **Imported and verified:** Trigger.dev and Activepieces — durable execution and marketing workflows.
3. **Imported and verified:** Chatwoot and OpenHands — customer support and coding agents.
4. **Verified, licence-filtered:** Twenty — CRM source reference; commercial-marked files not redistributed.
5. **Imported and verified:** Appwrite — backend/auth/storage reference. **Next if warranted:** PostHog for analytics.
6. **Imported and verified:** LangGraph.js and Temporal — agent state and durable execution.
7. **Optional:** PostHog, Medusa, Cal.com and Plane as defects warrant. Flowise is historical-only due to its shutdown.

Only copy an upstream snapshot when it answers a concrete product milestone. Don't claim paid functionality from its public source is complete without actually tracing/testing it.

## GitHub setup and storage layout

**Current separation:**
- Every one of the sixteen verified reference projects now has its **own dedicated public repository**, linked in the table above; each uses a source snapshot branch under `upstream/`.
- `Anselm04/Macro-source-code-reference-` currently also hosts the central catalogue and the older legacy snapshot branches created before separation; those older duplicates should not be used for future research.
- Do **not** merge source snapshot branches into main or commercial TrillionAI repos.

**Recommended future central rename/reorganization (optional):** create a public repository named `TrillionAI-Engineering-Reference-Library`, use it for the index, audit templates and importer only; keep snapshots in dedicated reference repositories or isolated branches. Moving the already verified sources isn't necessary to begin engineering.

**Permissions / costs:** GitHub Actions `contents: write` in the public research repository; workflow uses a built-in token, no personal access token required. Research jobs download source and compare Git trees only; they do not install or run project dependencies, run AI agents, or deploy anything. Before any future bulk imports check repository storage, Git LFS quotas, submodules, public-repository eligibility and usage. No paid APIs or Fly.io.

## First commercial acceptance contract

**AppForge:** sign up → verify email → purchase → entitlement/credits → genuine generation → preview → edit → save/reopen → export → deploy (do not require customer SMS; owner-only MFA is separate).

**Marketing:** sign up → subscription → complete onboarding → generated content → authorize publishing → publish through supported connectors → see accurate campaign outcomes. Paid advertising spends nothing until explicitly approved within customer budget.

**Manager:** sign up → subscription/entitlement → connect accounts with scoped permission → queue real tasks → execute via approved tools → produce verifiable evidence → retry/report failures → customer can pause/revoke consent. Spending always bounded.

**Integrated:** cross-product customer identity, billing and entitlements; event-driven handoff; support, audit trail and transparent metering. No fictional success signals, no uncontrolled recurring spending.

## Source study to repair ticket format

Record *upstream product and commit*, *specific source paths and flow*, *real commercial capability demonstrated*, *existing TrillionAI paths and commit*, *root cause / reproduction*, *original implementation plan*, *security/licence review*, *tests before/after*, and *end-to-end result*. A copied reference never itself constitutes a completed engineering ticket.

## Licensing and verification

Keep exact original source, notices and licence files in each verified snapshot. Do not sanitize or rename proprietary sections to claim open-source rights; use the snapshot for lawful study while separately evaluating licence obligations. Public repository does not mean permission to use code commercially without restrictions. Revenue is independently unverified unless audited financial evidence is provided; live paid pricing is evidence of an offered commercial product, not sales.
