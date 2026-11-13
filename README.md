# TrillionAI Engineering Reference Library — source research

This is a public research workspace for studying the architecture of [Macro](https://github.com/macro-inc/macro) to inform original TrillionAI engineering. A verified snapshot of the **complete Git-tracked upstream source tree** is available on the [`macro-upstream-snapshot` branch](https://github.com/Anselm04/Macro-source-code-reference-/tree/macro-upstream-snapshot/upstream) under `upstream/`. This is a source snapshot, not an import of all historical commits, submodule payloads, or Git LFS binary objects.


## Three-product launch research

This public repository also hosts our **AppForge + TrillionAI Marketing + TrillionAI Manager** source reference programme.

- [Verified commercial-reference catalogue and import status](docs/THREE_PRODUCT_LAUNCH_REFERENCES.md) — 7 snapshots, 103,692 Git-tracked files verified.
- [GitHub setup and source-import process](docs/GITHUB_LIBRARY_SETUP.md).
- [Source import workflow](.github/workflows/import-selected-reference.yml) — manual-only; no paid service activation and no upstream application execution.
- Individual snapshot branches: `macro-upstream-snapshot`, `reference-bolt-diy-snapshot`, `reference-trigger-dev-snapshot`, `reference-activepieces-snapshot`, `reference-chatwoot-snapshot`, `reference-openhands-snapshot`. Dyad is in its own dedicated reference repository.

This is for licensed source inspection and independent engineering designs. **None of the copies is proof that a TrillionAI application is production-ready.**

## Verified Macro source import
- Upstream commit: `532fba5e60c14b91ae641619c32a58120b6b4546`
- Git tree hash (matches source subtree): `6a1e16ef0f36bb7d93658cb524696c27f37f2c07`
- Git-tracked files: **41,545**
- [Successful GitHub Actions import and verification](https://github.com/Anselm04/Macro-source-code-reference-/actions/runs/43500903850)
- Source location: `macro-upstream-snapshot:upstream/`

## Provenance
- Upstream: https://github.com/macro-inc/macro
- Copyright and credit remain with their respective authors.
- Macro is AGPL-3.0 licensed; preserve upstream licensing, copyright and notices if copying or redistributing source.
- Record the exact upstream commit SHA for every detailed code review.

## Architecture subjects
1. Agent harness, session lifecycle and tool execution
2. Domain triggers, scheduled jobs and event broker
3. Long-term memory and context isolation
4. Authorization, authentication and tenancy
5. AI usage, billing admission and budget limits
6. Telemetry, observability, debugging and reliability
7. Web interfaces, API contracts and verification
8. Database models, migrations and transaction safety

## First study
[Initial verified architecture notes](docs/01-initial-architecture.md)

## Check out the source independently
For a manageable study checkout on a computer with GitHub access:

```bash
git clone --depth=1 --filter=blob:none --no-checkout https://github.com/macro-inc/macro.git macro-upstream
cd macro-upstream
git sparse-checkout init --cone
git sparse-checkout set crates/agent_harness crates/agent_trigger crates/memory crates/macro_authorization crates/macro_event_broker services/agent_harness_service docs
git checkout main
git rev-parse HEAD
```

Macro is a large repository. A shallow sparse clone downloads selected working files rather than the complete history; it still needs disk space and network access. Keep this checkout separate from proprietary TrillionAI repositories.

## Research ground rules
- Analyze design, security boundaries, failure recovery and test strategy.
- Document evidence, caveats and exact source locations.
- Independently implement ideas in TrillionAI's Flutter and Node.js stack.
- Do not copy upstream AGPL code into proprietary products without an appropriate licence review.
- Do not enable paid integrations, deployments or production workloads for this study.
