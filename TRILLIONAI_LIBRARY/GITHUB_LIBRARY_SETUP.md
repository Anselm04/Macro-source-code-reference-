# GitHub Reference Library — setup, import and handoff

## What already exists

- **Central reference catalogue and import workflow:** [Anselm04/Macro-source-code-reference-](https://github.com/Anselm04/Macro-source-code-reference-), branch `main`.
- **Three-product launch catalogue:** [THREE_PRODUCT_LAUNCH_REFERENCES.md](THREE_PRODUCT_LAUNCH_REFERENCES.md), now with 8 verified source snapshots.
- **Existing verified source:** Macro and bolt.diy as separate snapshot branches in this repository; Dyad in [its own reference repository](https://github.com/Anselm04/Dyad-Source-Code-Reference).

No further GitHub accounts, paid external services or personal access tokens are required for imports into this repository.

## Recommended organization

```text
Anselm04/
  Macro-source-code-reference-       # currently serves as central catalogue and source snapshot host
    main/
      docs/THREE_PRODUCT_LAUNCH_REFERENCES.md
      docs/GITHUB_LIBRARY_SETUP.md
      .github/workflows/import-selected-reference.yml
    macro-upstream-snapshot/upstream/
    reference-bolt-diy-snapshot/upstream/
    reference-trigger-dev-snapshot/upstream/   # VERIFIED
    reference-activepieces-snapshot/upstream/  # VERIFIED
    reference-chatwoot-snapshot/upstream/       # VERIFIED
    reference-openhands-snapshot/upstream/      # VERIFIED
    reference-appwrite-snapshot/upstream/       # VERIFIED

  Dyad-Source-Code-Reference/
    main/README.md
    dyad-upstream-snapshot/upstream/

  AppForge./                          # commercial code; never merge reference source
  ...                                 # other TrillionAI products remain independent
```

**Optional later:** Make a dedicated public `TrillionAI-Engineering-Reference-Library` repository for the catalogue, engineering findings, and import orchestration. The existing central repo is already functional; new repository creation is not a prerequisite to continue.

## For each new source snapshot

1. Check the source belongs to the claimed developer, is public, has current licence texts and paid/live product evidence (where claimed).
2. Add it to the fixed allowlist of the [import workflow](https://github.com/Anselm04/Macro-source-code-reference-/actions/workflows/import-selected-reference.yml), if not already present.
3. **Connected assistant workflow:** update the one-line [import request file](../.github/reference-import-request.txt) on `main` to the desired allowlisted project slug, e.g. `twenty`, `langgraphjs`, `medusa`, etc. That commit triggers the importer. Alternatively use manual **Run workflow** and select a project. **No scheduled imports**. The assistant can update the request file through its existing GitHub connection without you creating any more repositories or providing tokens.
4. GitHub checks out one immutable upstream commit, records its SHA/file count, stages its exact tracked tree at `upstream/`, and pushes a new branch.
5. Verify **upstream Git tree SHA == imported `upstream/` subtree SHA == remotely fetched subtree SHA**. If any mismatch or workflow failure, mark as failed, not imported.
6. Preserve original `LICENSE`, attribution and all source files, including enterprise/pro areas for study when redistribution is permitted. Those areas are not automatically available for commercial reuse.
7. Update the catalogue with upstream commit, imported branch, file count, exact licences, logs and any caveats.
8. Research the source but don't run imported repository workflows or execute external dependencies without a separate security review. An attempt to request an already imported slug fails safely and leaves existing branches unchanged.

## Github access configuration

- Repo visibility: public only for code already published publicly upstream; do not commit private TrillionAI source or credentials to the reference repo.
- Actions: `contents: write` only in the import job, using the built-in `GITHUB_TOKEN`.
- No SSH keys, PATs, Stripe keys, Supabase tokens, Fly.io tokens or cloud credentials in reference workflows.
- Keep customer data, auth sessions and proprietary implementation separate.
- Branches for source snapshots should be treated as immutable and **never merged into `main` or product repositories**.
- For an even stronger setup, configure GitHub branch protections on snapshot branches and `main` after transfer, requiring review for changes and preventing force pushes/deletion.
- Standard GitHub-hosted runners are generally free for public repositories, subject to GitHub's current policy; third-party services, Git LFS and storage/egress can have separate limitations or charges.
- Do not represent Git snapshots as full commercial product backends or licence-free material.

## Compare against launch checklist

Each investigation creates a factual matrix: customer-visible requirement → TrillionAI file/route → reproducible defect → verified reference implementation → independently designed repair → test and CI evidence → runtime acceptance. Focus on AppForge customer journey, Marketing publishing/onboarding and Manager consented execution.

## Source snapshot caveats

A passing Git tree check verifies the current **Git-tracked tree** of a specific commit. It does not import full history, private production infrastructure, secrets, untracked files or independent external dependencies; check Git LFS payloads and submodules separately where relevant.
