# TrillionAI Reference Library — Source Completeness Audit

> **SUPERSEDED BY FULL GIT-TREE VERIFICATION.** [Read the 31-repository verified source audit](REFERENCE_LIBRARY_VERIFIED_GIT_TREE_AUDIT_2026-11-15.md). This earlier inventory was preliminary. A later exact upstream Git-object comparison identified **2,045**, not 2,044, remaining non-CI omissions (Trivy has 67, not 66), repaired 11 other missing original Git entries, and safely archived 821 original upstream CI files without executing them. Use the newer report for current totals.\n\n**Audit date:** 2026-11-15 (Pacific/Auckland)  
**Scope:** 31 public `Anselm04/*Source-Code-Reference*` repositories; current `main` and their original pinned-source documentation.  
**Method:** GitHub repository discovery; retrieved provenance/licence documents; inspected import and restoration commit records; inspected representative source files. Existing historical importer tree-verification results were reviewed as recorded claims, not independently re-executed.

## Conclusions

- All **31 named source reference repositories** were discoverable and exhibited upstream-source import commits on `main`; none was found README-only.
- Upstream project identity / pinned commit is recorded in `TRILLIONAI_REFERENCE.md` for the older archives, and in `.trillionai/SOURCE_PROVENANCE.txt` for OSCAL, Cosign, and Compliance Trestle.
- Original root licence notices were readable using the project's own filenames (`LICENSE`, `LICENSE.md`, or `LICENSE.txt`). Licences are not uniform; do not assume all files have the root licence.
- **2,044 previously documented intentionally excluded upstream tracked files** across six repositories, listed below. This total DOES NOT include omitted upstream CI workflows, submodule contents, Git LFS payloads, downloaded binaries, private services, or unpublished source.
- Activepieces, Chatwoot and Dyad separately licensed paths were restored on `main` after an erroneous licence-path filtering pass. Restorations restored **1,166 files**; counts for the affected source directories match their pre-filter inventories. No full hash-by-hash verification was rerun here.
- **Do not equate a source snapshot with complete upstream history, passing builds, legal redistribution permission, or proprietary product ownership.**

## All 31 repository audit inventory

| # | Repository | Main branch source evidenced | Provenance recorded | Root licence found | Known caveat |
|---:|---|---|---|---|---|
| 1 | Macro-source-code-reference- | Yes | Yes | LICENSE.txt | AGPL; history, LFS/submodules not archived |
| 2 | Dyad-Source-Code-Reference | Yes | Yes | LICENSE; src/pro/LICENSE | 198 FSL files restored; check original snapshot |
| 3 | Bolt-DIY-Source-Code-Reference | Yes | Yes | LICENSE | WebContainers service licence separate |
| 4 | OpenHands-Source-Code-Reference | Yes | Yes | LICENSE | External/private services not part of open source |
| 5 | Appwrite-Source-Code-Reference | Yes | Yes | LICENSE | Original BSD-style licence |
| 6 | Activepieces-Source-Code-Reference | Yes | Yes | LICENSE; packages/ee/LICENSE | 229 enterprise-path files restored; mixed terms |
| 7 | Chatwoot-Source-Code-Reference | Yes | Yes | LICENSE; enterprise/LICENSE | 739 enterprise-path files restored; mixed terms |
| 8 | TriggerDev-Source-Code-Reference | Yes | Yes | LICENSE | CI, LFS and submodules separate |
| 9 | LangGraph-Source-Code-Reference | Yes | Yes | LICENSE | Snapshot of LangGraph.js, not all hosted services |
| 10 | Temporal-Source-Code-Reference | Yes | Yes | LICENSE | Git source snapshot only |
| 11 | Twenty-Source-Code-Reference | Yes | Yes | LICENSE | **825** enterprise-marked files excluded |
| 12 | PostHog-Source-Code-Reference | Yes | Yes | LICENSE | **839** `ee/` files excluded |
| 13 | Medusa-Source-Code-Reference | Yes | Yes | LICENSE; ENTERPRISE-LICENSE.md | **265** enterprise files excluded |
| 14 | Keycloak-Source-Code-Reference | Yes | Yes | LICENSE.txt | Upstream provenance points to Java source |
| 15 | Coolify-Source-Code-Reference | Yes | Yes | LICENSE | **48** credential/private-key-related files excluded |
| 16 | CalCom-Source-Code-Reference | Yes | Yes | LICENSE | Cal.diy; **1** token-bearing file excluded |
| 17 | Plane-Source-Code-Reference | Yes | Yes | LICENSE.txt | AGPL; separate copyright notice |
| 18 | OpenTelemetry-Source-Code-Reference | Yes | Yes | LICENSE | JS upstream only |
| 19 | MCP-TypeScript-SDK-Source-Code-Reference | Yes | Yes | LICENSE | MIT/Apache transition; other document licences |
| 20 | NodeRED-Source-Code-Reference | Yes | Yes | LICENSE | External node dependencies separate |
| 21 | OpenID-Client-Source-Code-Reference | Yes | Yes | LICENSE.md | MIT |
| 22 | Trivy-Source-Code-Reference | Yes | Yes | LICENSE | **66** credential-shaped test fixtures excluded |
| 23 | OSV-Scanner-Source-Code-Reference | Yes | Yes | LICENSE | No source blob exclusions declared |
| 24 | Semgrep-Source-Code-Reference | Yes | Yes | LICENSE | LGPL and component licences; CI excluded; submodule not fetched |
| 25 | Playwright-Source-Code-Reference | Yes | Yes | LICENSE; NOTICE | CI excluded; browser binaries not downloaded |
| 26 | Syft-Source-Code-Reference | Yes | Yes | LICENSE | CI excluded |
| 27 | Grype-Source-Code-Reference | Yes | Yes | LICENSE | CI excluded |
| 28 | OPA-Source-Code-Reference | Yes | Yes | LICENSE | CI excluded |
| 29 | OSCAL-Source-Code-Reference | Yes | Yes | LICENSE.md | NIST public domain notices; CI excluded |
| 30 | Cosign-Source-Code-Reference | Yes | Yes | LICENSE; COPYRIGHT.txt | CI excluded |
| 31 | Compliance-Trestle-Source-Code-Reference | Yes | Yes | LICENSE | CI excluded; `nist-content` submodule not initialized |

## Known source omissions in pre-existing imports

| Reference | Original tracked files | Imported/retained | Excluded | Reason |
|---|---:|---:|---:|---|
| Twenty | 44,522 | 43,697 | **825** | Commercial `@license Enterprise` markers |
| PostHog | 71,984 | 71,145 | **839** | Commercial `ee/` source |
| Medusa | 25,297 | 25,032 | **265** | Enterprise licence path inventory |
| Coolify | 5,500 | 5,452 | **48** | SSH key fixtures / GitHub secret protection |
| Cal.diy | 7,712 | 7,711 | **1** | Token-bearing `apps/web/calendso.yaml` |
| Trivy | n/a in recorded summary | n/a | **66** | `pkg/fanal/secret/testdata/` and `pkg/fanal/artifact/local/fs_test.go` |
| **Total** | | | **2,044** | Excludes uncounted CI workflow omissions |

**Additional differences shared by numerous repositories:** upstream `.github/workflows/` entries were intentionally omitted so imported workflows would not execute. A reproducible, path-by-path delta manifest for all 31 source trees has **not** been generated in this audit. The upstream **Git-tracked snapshot** is not the full repository history, external dependency source, private code, Git LFS binary objects, or the contents of submodules unless explicitly fetched.

## Restoration verification (2026-11-15 NZ)

| Repository | Removed and restored implementation files | Original special-directory count incl. licence | Restoration commit |
|---|---:|---:|---|
| Activepieces | 229 | 230 | `9da64307b568446b44b3bdfe0a5c8634d16bfe03` |
| Chatwoot | 739 | 740 | `9b1c986d54c625003eb9e7a17736264240a8738b` |
| Dyad | 198 | 199 | `a4801df46497a86bf8b44652f40a0368665a10a7` |
| **Total** | **1,166** | | |

These commits restored source on `main` from pre-cleanup revisions. This verifies directory inventories; a separate Git object-by-object comparison against pre-cleanup snapshots is recommended for stronger assurance.

## Remaining engineering verification

1. **Produce a machine-readable file-level delta manifest** for each repository at its exact pinned upstream SHA, comparing every path / Git object SHA / mode against its destination source snapshot. Tag exclusions: source import metadata, workflows, licence-restricted files, credential fixtures, LFS pointers, submodules. Include genuine absent/mismatched files separately from deliberate exclusions.
2. **Check original snapshot branches and current `main` independently.** Licence-filtered imports are intentionally not complete upstream mirrors; do not claim otherwise.
3. **Perform source-specific licence and security review before copying or republishing** code, including directory-level enterprise notices; the presence of source in a public GitHub repository does not confer general redistribution permission.
4. **For sensitive test fixtures, retain file path/hash, structure and safely redacted examples** rather than publishing usable credentials/private keys.
5. Implement TrillionAI's proprietary Flutter + Node.js technology independently based on requirements, behaviour and architectural research. Use a documented requirements/design/test trail for inventions; assess patents independently if relevant.

## Notes on verification scope

This report is a **repository inventory and documented exclusion audit**, not an exhaustive byte-for-byte current-versus-upstream certification and not legal clearance. Individual earlier importer jobs recorded source tree verification. The documented exclusions are real gaps relative to pinned public upstream tracked files, not evidence that unavailable proprietary/private upstream components can or should be acquired. No paid deployments, upstream builds, or batch GitHub Actions auditing jobs were started for this report.
