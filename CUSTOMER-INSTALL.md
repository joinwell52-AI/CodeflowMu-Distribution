# CodeFlowMu Customer Install and Upgrade

This repository distributes the **free public preview of the proprietary CodeFlowMu Windows x64 product**. It does not provide the CodeFlowMu source repository or grant an open-source license.

## System requirements

- Windows 10/11 x64 or another supported Windows x64 environment
- Git is not required
- Node.js / npm are not required
- Python is not required
- Access to the CodeFlowMu source repository is not required

The installer carries the base product runtimes pinned and verified by the CodeFlowMu product pipeline.

## Download

> [!IMPORTANT]
> This repository provides V2.2.1 Preview 15, but no formally supported stable release. Prerelease software is for free preview and installation testing only.

For installation testing on another Windows x64 computer, use the explicitly non-formal [V2.2.1 Preview 15](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v2.2.1-preview.15):

- [Download the installer directly](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v2.2.1-preview.15/CodeFlowMu-Setup-2.2.1-preview.15-win-x64.exe)
- SHA-256: `6923af6c5b00f15c799413a03123db01ad4a0456bd67ec921847da684016e9be`

The installer passed automatic isolated silent installation and installed-program startup checks. This basic acceptance does not configure an external Provider account or cover mobile business tasks and upgrade scenarios, and it must not be treated as a formal or stable supported release.

The candidate installer is not code-signed and may trigger Windows SmartScreen. Verify its SHA-256 before running it. CodeFlowMu itself is free during the public preview; external Provider accounts, services and usage charges are separate.

Download installers only from this repository's [GitHub Releases](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases). Customers need only these two files:

```text
CodeFlowMu-Setup-<version>-<candidate>-win-x64.exe
SHA256SUMS.txt
```

The Preview 15 filename contains the complete candidate number so multiple Preview builds of one product version cannot be confused.

Product inventory, module configuration, security audit and installation-acceptance details remain in the Workbench's internal version record instead of being distributed as customer attachments. Cursor is managed as a separate `sdk.v1` Provider Runtime; the installer does not bundle the real Cursor SDK or customer credentials.

Development candidates are not formal customer releases until every Release Gate passes.

## Install CodeFlowMu

1. Verify the SHA-256 of the downloaded CodeFlowMu installer against `SHA256SUMS.txt`.
2. Run the installer.
3. Complete the installation wizard.
4. Start **CodeFlowMu** from the Start menu or desktop shortcut.

The currently downloadable Preview 15 first presents a CodeFlowMu-branded welcome page with the product name, complete candidate number and logo. It then shows an editable destination chooser and repeats the final destination on the confirmation page before writing files. A remembered previous directory is only an editable default and no longer suppresses the chooser.

Windows Program Files remains the recommended default. Mutable runtime/customer data is kept outside the installed program tree.

The installed product must not depend on the source checkout, Git, npm, a system Node.js installation, or a system Python installation.

After installation, follow [Your first ShipReady PWA, step by step](FIRST-PWA-TASK.md) to complete one PM, DEV, QA and OPS delivery loop before connecting a real business project.

## Use the Mobile PWA

The Mobile PWA is the phone entry point for CodeFlowMu. Its current public URL is:

<https://ai.chedian.cc/cfm/>

The PWA cannot execute work independently from CodeFlowMu on the PC. Keep CodeFlowMu running on the PC and bind the phone to that PC Runtime instance.

### Public Gateway binding

1. Start CodeFlowMu on the PC.
2. Open **Mobile** in the left navigation and select **Refresh**.
3. Confirm that Gateway is online and that a **Public Gateway bind QR** is shown.
4. Scan the QR code with the phone browser, or open the displayed bind link on the phone.
5. Confirm that the phone appears under **Bound devices** on the PC.
6. Use the phone browser menu to choose **Add to Home Screen** or **Install app**.

Public Gateway mode does not require the phone and PC to share a LAN, but the PC must be able to connect to the CodeFlowMu Gateway and the phone must be able to open the HTTPS URL above.

### LAN binding

1. Connect the phone and PC to the same Wi-Fi network.
2. Select **Refresh** on the PC's **Mobile** page.
3. Scan the **LAN bind QR**, or open the LAN bind link on the phone.
4. If the phone cannot open the link, allow inbound TCP port `18766` for CodeFlowMu in Windows Firewall, then refresh the binding information.

Do not share a QR code or bind link with unrelated people. Bind each phone separately and revoke lost or retired devices under **Mobile → Bound devices** on the PC. If the bind code expires, Gateway goes offline, or the PC is shut down, restart CodeFlowMu and select **Refresh** to generate current binding information.

The PWA, Mobile API, Gateway, and PC product have independent versions. A PWA update does not mean that a PC installer has been released, and a PC installer update must not be described as a completed PWA update.

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

Beginning with Preview 15, the PC product checks a signed feed using both the product version and the release-candidate number. It prompts before downloading a higher complete version. After confirmation, it downloads the full installer, verifies signature, origin, size and SHA-256, applies the upgrade silently to the current installation directory, and restarts CodeFlowMu. The same version is not downloaded twice and an older version is never selected as an upgrade.

The Workbench activates an update only after the installer passes isolated-install and normal-startup acceptance and a maintainer explicitly publishes the candidate as a prerelease. While the repository is Private, unauthenticated external customers cannot use the GitHub update feed; this does not bypass publication acceptance.

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
