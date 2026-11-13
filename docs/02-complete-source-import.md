# Importing Macro's complete current source tree

## Status

The workflow is **installed, not executed**. No claim is made that the Macro source already exists in this research repository.

## Run the one-time source import

1. Review GitHub's Actions spending limits before running. **This repository is private**, so GitHub-hosted runner minutes can be charged when included usage is exhausted.
2. Open [Import Macro complete source snapshot](https://github.com/Anselm04/Macro-source-code-reference-/actions/workflows/import-macro-source.yml).
3. Select **Run workflow**, choose **main**, then run it.
4. Confirm the job finishes successfully, including the last **Verify uploaded snapshot against upstream** step.
5. Open [the complete source branch](https://github.com/Anselm04/Macro-source-code-reference-/tree/macro-upstream-snapshot).

## What the workflow imports

- All files tracked by `macro-inc/macro` on the current `main` commit, including all source directories.
- The exact tracked-file tree is compared against the upstream commit before push, and the uploaded Git tree verified afterward.
- Upstream commit ID and file count are printed in the run log.
- The snapshot lives on a new **macro-upstream-snapshot** branch so the study documents on this repository's **main** branch remain untouched.
- **No complete commit history, Git submodule contents, Git LFS binary payloads, or untracked/generated files are promised.** The term *complete source* here means the current Git-tracked tree of the upstream repository.
- The workflow does not run automatically or on schedule, and refuses to overwrite an existing snapshot branch.

## Failure modes

- Large pushes can hit GitHub's size limits (GitHub enforces a 2 GB push limit) or runner disk limits.
- An upstream Git object larger than GitHub's file limit may prevent import.
- An upstream change during an attempt is prevented from corrupting provenance by taking and comparing one source commit's tree.
- GitHub Actions minutes on a private repo are not guaranteed free: check billing/spending caps first.
- If the workflow fails because of limits, the source should be imported in smaller verified directory batches or from a sufficiently provisioned local Linux checkout; do not declare it complete after a partial failure.

## Licensing

Original source and copyright remain with Macro's contributors. Macro publishes its repository under AGPL-3.0. Preserve the original licence and attribution in the source branch. This source is for research; incorporation into proprietary commercial code requires a licensing review.

## Local no-hosted-runner alternative

From a Linux machine with adequate disk space and GitHub authentication already configured:

```bash
git clone --depth=1 --single-branch --branch main --filter=blob:none \
  https://github.com/macro-inc/macro.git macro-upstream
cd macro-upstream
UPSTREAM_TREE=$(git rev-parse HEAD^{tree})
UPSTREAM_SHA=$(git rev-parse HEAD)
git config user.name "Macro Reference Import"
git config user.email "macro-reference@users.noreply.github.com"
git checkout --orphan macro-upstream-snapshot
git add -A
test "$(git write-tree)" = "$UPSTREAM_TREE" || { echo "Tree mismatch"; exit 1; }
git commit -m "Source snapshot of macro-inc/macro at $UPSTREAM_SHA"
git remote add research https://github.com/Anselm04/Macro-source-code-reference-.git
git push research HEAD:refs/heads/macro-upstream-snapshot
```

This local alternative uses no hosted GitHub Actions minutes, but uses your bandwidth/disk and needs write authentication on push. Stop on any errors; do not use `--force`.
