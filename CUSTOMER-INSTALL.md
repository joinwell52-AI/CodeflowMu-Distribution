# CodeFlowMu Customer Install and Upgrade

This repository distributes the **CodeFlowMu Windows x64 customer product**. It does not provide the CodeFlowMu source repository.

## System requirements

- Windows 10/11 x64 or another supported Windows x64 environment
- Git is not required
- Node.js / npm are not required
- Python is not required
- Access to the CodeFlowMu source repository is not required

The installer carries the product runtimes pinned and verified by the CodeFlowMu product pipeline.

## Download

After a formal release is published, download at least these files from the matching GitHub Release:

```text
CodeFlowMu-Setup-<version>-win-x64.exe
SHA256SUMS.txt
installer-manifest.json
product-manifest.json
THIRD-PARTY-NOTICES.json
runtime-security-audit.json
```

Development candidates are not formal customer releases until every Release Gate passes.

## Install

1. Verify the SHA-256 of `CodeFlowMu-Setup-<version>-win-x64.exe` against `SHA256SUMS.txt`.
2. Run the installer.
3. Complete the installation wizard.
4. Start **CodeFlowMu** from the Start menu or desktop shortcut.

Program files are installed under Windows Program Files. Mutable runtime/customer data is kept outside the installed program tree.

The installed product must not depend on the source checkout, Git, npm, a system Node.js installation, or a system Python installation.

## Data and upgrades

Upgrades must not treat customer work data as application files. Back up important workspaces, Evidence, Audit, Reports, and configuration before major upgrades.

Every formal upgrade remains subject to:

```text
installed-file integrity
→ product manifest
→ SHA-256
→ installed runtime health check
→ security audit
→ third-party license/redistribution gate
```

## Uninstall

Use Windows Installed Apps / Apps & Features to uninstall CodeFlowMu.

Application removal and customer-data retention are separate boundaries. A formal product must not silently delete customer tasks, Evidence, Audit, or other persistent data as a side effect of uninstalling the program.

## Verify product origin

A formal customer version is recognized only when it is published as a GitHub Release in this repository and is traceable to a verified `main` source commit in `joinwell52-AI/codeflowmu`.

Do not treat PR artifacts, feature-branch builds, source archives, or a Setup.exe that has not passed the Release Gate as a formal customer release.
