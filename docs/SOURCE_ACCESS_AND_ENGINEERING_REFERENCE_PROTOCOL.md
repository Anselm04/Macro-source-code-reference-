# Source Access and Complete Engineering Reference Protocol

## Purpose

Build full-context research references without confusing legal permissions, publicly accessible source, or synthetic replacements. Each pinned source reference retains the exact project, version, licence files, and original source locations. Never silently remove a file from a reference without documenting it and the reason.

## A. File-by-file reconciliation (all repositories)

For every missing path in the repository's `docs/verified-source-audit/*-main-delta.json`:

1. Confirm the original Git object SHA, mode, path, upstream repository and pinned commit.
2. Determine whether the exact file can be lawfully republished under its governing licence, including directory-specific and per-file terms.
3. Independently classify secrets, keys, real tokens, private data and unsafe workflows; never commit authentic credentials.
4. If redistribution is permitted and no secret exposure exists, restore the original source file unchanged and record a matching SHA/mode.
5. If not permitted, retain the **exact Git path, original hash/mode, pinned upstream file URL, governing licence notice**, and a non-copying architectural/interface analysis. Keep this link accessible in the existing missing-file index.
6. For a credential-containing test fixture, produce a synthetic/redacted fixture preserving the relevant syntax, parsing behavior and negative-test cases. Label it synthetic; never pass it off as an exact upstream file.
7. For an external submodule, preserve its upstream Gitlink and separately track whether its exact nested commit and contents have been acquired with appropriate permissions.
8. Maintain a machine-readable manifest that distinguishes verified originals, synthetic replacements, links to original source, submodule pointers and unresolved unavailable files.

## B. Independent proprietary engineering

From available source research, create evidence-backed specifications of inputs, outputs, state transitions, interfaces, data models, trust boundaries, failure modes and tests. Independently implement and test original Flutter frontend / Node.js backend solutions. The ability to view upstream source or produce a character-for-character copy does not change legal rights. For patents, avoiding copying code does not by itself avoid patent claims.

## C. Current six-repository backlog

| Repo | Currently absent | First assessment |
|---|---:|---|
| Twenty | 825 | `@license Enterprise` marked files; inspect file-level commercial terms |
| PostHog | 839 | `ee/` files with separate commercial licence |
| Medusa | 265 | Listed enterprise materials; evaluate exact paths |
| Coolify | 48 | **Mixed**: includes ordinary PHP implementation files as well as SSH/private-key fixtures; reconsider the original broad secret exclusions individually |
| Cal.diy | 1 | Token-bearing YAML configuration, use synthetic/redacted structural fixture |
| Trivy | 67 | Secret-scanner test vectors plus test file; audit safe subsets separately |

Every exact missing path has already been recorded in `docs/UPSTREAM_SOURCE_GAP_INDEX.md`. The source indexes contain links into the pinned original public upstream, not the restricted source contents.

## D. Acceptance criteria per repository

- All pinned original files accounted for by Git path and SHA.
- Every allowable non-sensitive source file restored and hash checked.
- Every not-mirrored file has exact upstream location plus labelled licence/security rationale.
- Original licence texts and attribution preserved.
- No unreviewed upstream workflows executed; CI source archived inertly.
- No false claims that index links, pseudocode, synthetic fixtures or submodule Gitlinks constitute complete local upstream source.
- For each research topic, technical requirements and independent implementation tests replace the need to copy protected code into TrillionAI proprietary products.

This procedure prioritizes **complete engineering visibility** without republishing code for which the authors have not granted sufficient rights or exposing live credentials.
