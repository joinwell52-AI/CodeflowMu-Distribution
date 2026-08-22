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
9. Runtime security audit contains no release-blocking high/critical finding.
10. Third-party license and redistribution requirements are satisfied.

Any failed or unresolved gate is release-blocking.

## Immutability

Release tags are immutable. If a release tag already exists, the publication pipeline must preserve it rather than overwrite its files.

A corrected product requires a new version/tag.

## Customer release contents

Formal Windows releases contain the installer and verification evidence only. They do not contain the CodeFlowMu source repository.
