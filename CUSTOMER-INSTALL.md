# CodeFlowMu Customer Install and Upgrade

This repository distributes the **free public preview of the proprietary CodeFlowMu Windows x64 product**. It does not provide the CodeFlowMu source repository or grant an open-source license.

## System requirements

- Windows 10/11 x64 or another supported Windows x64 environment
- A user-writable installation directory on an NTFS volume (first-start configuration requires hard-link support)
- Git is not required
- Node.js / npm are not required
- Python is not required
- Access to the CodeFlowMu source repository is not required

The installer carries the base product runtimes pinned and verified by the CodeFlowMu product pipeline.

## Download

> [!IMPORTANT]
> [V2.2.1 Preview 19](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v2.2.1-preview.19) is available as a GitHub Pre-release download, not an active update target. User reinstall acceptance is pending. Preview 17 has a root-discovery defect; Preview 18 lacks first-start team configuration and embedded EXE icons. Use Preview 19 for this repair. There is no formally supported stable release. This Private repository requires a GitHub account with access.

Download this candidate and its checksum file from GitHub:

- [Download CodeFlowMu-Setup-2.2.1-preview.19-win-x64.exe](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v2.2.1-preview.19/CodeFlowMu-Setup-2.2.1-preview.19-win-x64.exe).
- [Download SHA256SUMS.txt](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v2.2.1-preview.19/SHA256SUMS.txt).
- SHA-256: `cd774146001b8ffbb924b9b059cbcbd76c300e1d09e3ae2b4dfbabb91dd4395c`.

Checks cover isolated installation, 8,886-file inventory verification, startup, initialization, the real team API, team configuration persistence across restart and native exit. Both EXEs contain seven verified icon sizes. First startup generates a clean default team; existing customer configuration is preserved. User reinstall acceptance is pending. These checks do not cover Provider accounts, mobile business tasks or full upgrade regression and do not establish formal support.

The candidate installer is not code-signed and may trigger Windows SmartScreen. Verify its SHA-256 before running it. CodeFlowMu itself is free during the public preview; external Provider accounts, services and usage charges are separate.

Download installers only from this repository's [GitHub Releases](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases). Customers need only these two files:

```text
CodeFlowMu-Setup-<version>-<candidate>-win-x64.exe
SHA256SUMS.txt
```

The filename includes the complete candidate identity. Historical Preview 17 on GitHub does not contain this repair and cannot be used to test Preview 19.

Product inventory, module configuration, security audit and installation-acceptance details remain in the Workbench's internal version record instead of being distributed as customer attachments. Cursor is managed as a separate `sdk.v1` Provider Runtime; the installer does not bundle the real Cursor SDK or customer credentials.

Development candidates are not formal customer releases until every Release Gate passes.

## Install CodeFlowMu

1. Verify the SHA-256 of the downloaded CodeFlowMu installer against `SHA256SUMS.txt`.
2. Run the installer.
3. Complete the installation wizard.
4. Start **CodeFlowMu** from the Start menu or desktop shortcut.

The installer presents a branded welcome page, complete candidate identity, editable destination chooser and final destination confirmation before writing files.

Preview 19 uses a per-user installation. Choose a directory writable by your Windows user, such as `E:\CodeFlowMu`. This is also the default project root: initialization creates collaboration files under `fcop`; state, logs, Provider and update cache live under `data`. It no longer defaults to `C:\ProgramData\CodeFlowMu` or creates a nested `projects\default`.

Fresh installs require no migration. Back up existing projects yourself before making changes; the installer does not silently remove historical C-drive directories. Do not use a drive root or a directory containing important unrelated files as a disposable test directory.

## Exit CodeFlowMu

Closing the browser does not stop the backend. Right-click the CodeFlowMu notification-area icon, choose **Exit CodeFlowMu**, and confirm. The icon may be inside the notification-area overflow list.

Alternatively use **Exit CodeFlowMu** in the Start menu or run this from the installation directory:

```text
CodeFlowMu.exe --exit
```

The supervisor requests graceful shutdown, with a timeout fallback limited to its own process tree. Exiting stops current tasks and disconnects the phone; there is no need to end unrelated Node or Python processes manually.

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
E:\CodeFlowMu\data\providers\cursor\
├─ versions\<version>\
├─ current\
└─ current.json
```

Cursor Provider versions have a lifecycle separate from the CodeFlowMu application. Only the bridge version proven by this CodeFlowMu Release's `cursor.json` should be treated as formally supported. Do not promote an untested bridge update directly into production use.

## Data and upgrades

Upgrades must not treat customer work data as application files. Back up important workspaces, Evidence, Audit, Reports, and configuration before major upgrades.

The PC product compares both product version and candidate number in a signed update feed. It prompts before downloading, verifies the full installer, applies it to the existing directory and restarts. Equal or older versions are not upgrade targets. Preview 19 is a manual GitHub download and absent from the feed; this handoff does not claim full upgrade regression coverage.

The Workbench activates an update only after the installer passes isolated-install, first-project-initialization and normal-startup acceptance and a maintainer explicitly publishes the candidate as a prerelease. While the repository is Private, unauthenticated external customers cannot use the GitHub update feed; this does not bypass publication acceptance.

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
