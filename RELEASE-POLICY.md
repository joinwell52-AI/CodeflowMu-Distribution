# CodeFlowMu Distribution Release Policy

This private repository is a customer-distribution boundary, not a source mirror.

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
3. Self-contained Windows runtimes are present and pinned.
4. `CodeFlowMu.exe` and the Windows installer build successfully.
5. The installer can be silently installed into a clean location.
6. Installed files match the product manifest and SHA-256 inventory.
7. The installed product reaches its health endpoint using bundled runtimes only.
8. Mutable runtime state remains outside the installed program tree.
9. Effective product security audit contains zero unresolved critical, high, or moderate findings.
10. Every remaining low-severity finding has an explicit, version-bound risk acceptance record with rationale and review triggers.
11. Third-party license and redistribution requirements are satisfied for every bundled provider/runtime component.

Any failed or unresolved gate is release-blocking.

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
```

The security audit and risk-acceptance evidence are part of the release identity. A release must not publish an installer while omitting the evidence used to authorize it.

## Immutability

Release tags are immutable. If a release tag already exists, the publication pipeline must preserve it rather than overwrite its files.

A corrected product requires a new version/tag.

## Customer release contents

Formal Windows releases contain the installer and verification evidence only. They do not contain the CodeFlowMu source repository.

## Current visibility

This distribution repository is currently Private while productization and formal release preparation are still in progress. A future change in repository visibility does not weaken any release gate above.
