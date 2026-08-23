# CodeFlowMu Customer Install and Upgrade

This repository distributes the **CodeFlowMu Windows x64 customer product**. It does not provide the CodeFlowMu source repository.

## System requirements

- Windows 10/11 x64 or another supported Windows x64 environment
- Git is not required
- Node.js / npm are not required
- Python is not required
- Access to the CodeFlowMu source repository is not required

The installer carries the base product runtimes pinned and verified by the CodeFlowMu product pipeline.

## Download

After a formal release is published, download at least these files from the matching GitHub Release:

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

`runtime-security-audit.json` records the effective dependency security result for the shipped product. If a low-severity finding is explicitly accepted, `security-risk-acceptance.json` records the rationale and review triggers. `cursor.json` records the real Cursor Provider compatibility result for the release, including the verified `sdk.v1` bridge version, official archive SHA-256, and create/send/stream checks.

Development candidates are not formal customer releases until every Release Gate passes.

## Install CodeFlowMu

1. Verify the SHA-256 of `CodeFlowMu-Setup-<version>-win-x64.exe` against `SHA256SUMS.txt`.
2. Run the installer.
3. Complete the installation wizard.
4. Start **CodeFlowMu** from the Start menu or desktop shortcut.

Program files are installed under Windows Program Files. Mutable runtime/customer data is kept outside the installed program tree.

The installed product must not depend on the source checkout, Git, npm, a system Node.js installation, or a system Python installation.

## Enable the Cursor Provider

The CodeFlowMu installer does not redistribute the real `@cursor/sdk` package or the Cursor bridge binary. Cursor is an independently managed `sdk.v1` Provider Runtime.

For a formal release, configure the customer's own `CURSOR_API_KEY`, then use the product Provider Manager:

```text
CodeFlowMu --install-cursor-provider
```

The Provider Manager downloads the declared Cursor standalone bridge from the official Cursor release, verifies the official `SHA256SUMS.txt`, validates the `sdk.v1` manifest, and installs the provider under the CodeFlowMu product-data directory.

Typical layout:

```text
C:\ProgramData\CodeFlowMu\providers\cursor\
├─ versions\<version>\
├─ current\
└─ current.json
```

Cursor Provider versions have a lifecycle separate from the CodeFlowMu application. Only the bridge version proven by this CodeFlowMu Release's `cursor.json` should be treated as formally supported. Do not promote an untested bridge update directly into production use.

## Data and upgrades

Upgrades must not treat customer work data as application files. Back up important workspaces, Evidence, Audit, Reports, and configuration before major upgrades.

Every formal upgrade remains subject to:

```text
installed-file integrity
→ product manifest
→ SHA-256
→ installed runtime health check
→ effective product security audit
→ explicit low-risk acceptance (if any)
→ real Provider compatibility smoke
→ Provider compatibility evidence
```

A compatible Cursor Provider can be upgraded or rolled back independently without reinstalling the entire CodeFlowMu application.

## Uninstall

Use Windows Installed Apps / Apps & Features to uninstall CodeFlowMu.

Application removal and customer-data retention are separate boundaries. A formal product must not silently delete customer tasks, Evidence, Audit, Provider state, or other persistent data as a side effect of uninstalling the program.

## Verify product origin

A formal customer version is recognized only when it is published as a GitHub Release in this repository and is traceable to a verified `main` source commit in `joinwell52-AI/codeflowmu`.

Do not treat PR artifacts, feature-branch builds, source archives, an untested Provider, or a Setup.exe that has not passed the Release Gate as a formal customer release.
