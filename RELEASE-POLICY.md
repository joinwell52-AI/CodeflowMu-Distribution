# CodeFlowMu Distribution Release Policy

This public repository is a product-distribution boundary, not a source mirror and not an open-source repository.

Public repository visibility does not weaken the separation between publicly downloadable product artifacts and the private CodeFlowMu source repository.

## Authority

A formal CodeFlowMu customer release must originate from a verified commit on:

```text
joinwell52-AI/codeflowmu
branch: main
```

Feature branches and pull requests may produce development artifacts, but those artifacts are not formal customer releases.

## Required release gates

Before a release may be created here, the source pipeline must verify all of the following:

1. Closed-distribution boundary is enforced.
2. Product staging contains built/runtime artifacts only.
3. Self-contained Windows base runtimes are present and pinned.
4. `CodeFlowMu.exe` and the Windows installer build successfully.
5. The installer can be silently installed into a clean location.
6. Installed files match the product manifest and SHA-256 inventory.
7. The installed product reaches its health endpoint using bundled base runtimes only.
8. Mutable runtime state remains outside the installed program tree.
9. Effective product security audit contains zero unresolved critical, high, or moderate findings.
10. Every remaining low-severity finding has an explicit, version-bound risk acceptance record with rationale and review triggers.
11. Any bundled third-party runtime satisfies its license and redistribution requirements.
12. Cursor is proven to use the external `sdk.v1` Provider boundary: the formal CodeFlowMu installer must not contain the real `@cursor/sdk` package or Cursor bridge binary.
13. The exact Cursor bridge version promoted as supported has passed a real installed-product compatibility smoke covering model listing, model-free agent creation, resume, send/stream, and terminal wait.
14. Cursor compatibility evidence is bound to the current product manifest, CodeFlowMu bridge shim, Provider Manager, source commit, and official bridge archive SHA-256.

Any failed, missing, stale, skipped, or unresolved gate is release-blocking.

## Required release evidence

A formal Windows release includes at least:

```text
CodeFlowMu-Setup-<version>-win-x64.exe
SHA256SUMS.txt
installer-manifest.json
product-manifest.json
THIRD-PARTY-NOTICES.json
runtime-security-audit.json
security-risk-acceptance.json
cursor.json
```

The security audit, risk-acceptance evidence, and Provider compatibility evidence are part of the release identity. A release must not publish an installer while omitting the evidence used to authorize it.

`cursor.json` must identify the supported `sdk.v1` bridge version and its official archive SHA-256. A candidate bridge version is not a formally supported Provider version until the real compatibility smoke passes and the source runtime lock promotes that same version from candidate to tested.

## Provider lifecycle

Cursor Provider runtime is independently managed under the CodeFlowMu product-data boundary rather than Program Files. A supported Provider version may therefore be upgraded or rolled back independently of a CodeFlowMu application update, provided the compatibility contract for the installed CodeFlowMu version remains satisfied.

CodeFlowMu must not silently promote an untested new Cursor bridge version merely because the upstream Provider published it.

## Immutability

Release tags are immutable. If a release tag already exists, the publication pipeline must preserve it rather than overwrite its files.

A corrected product requires a new version/tag.

## Preview candidates

A pre-release candidate may be published for public evaluation before every formal customer gate passes only when all of the following are true:

1. GitHub marks it as a Pre-release.
2. The Release title and notes say that it is not stable or formally supported.
3. Every known formal-release blocker is stated prominently.
4. Installer signing status, target platform and verification hash are disclosed.
5. The candidate is never relabeled in place as a formal release; promotion requires a new immutable tag and complete evidence set.

## Customer release contents

Formal Windows releases contain the CodeFlowMu installer and verification evidence only. They do not contain the CodeFlowMu source repository, the real Cursor SDK package, or the Cursor bridge binary.

## Repository publication gate

Before the distribution repository becomes or remains Public, its tracked files and full Git history must be checked for source, committed binaries, credentials, customer data and internal-only paths. Public links, screenshots and release metadata must be reviewed, and the README must preserve the free-preview, proprietary-software and candidate-release boundaries.
