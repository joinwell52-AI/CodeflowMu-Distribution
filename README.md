# CodeFlowMu

<p align="center">
  <img src="assets/hero-banner.png" alt="CodeFlowMu: Commands Flow, Intelligence Follows" width="100%">
</p>

<p align="center"><strong>Your AI development team, commanded from your phone: PM · DEV · QA · OPS ready for the next task.</strong></p>

<p align="center">Send a software goal, follow progress remotely, take over critical actions and accept the delivery; engineering runs on your authorized Windows development machine.</p>

<p align="center">Not another chat. A real flow from planning and implementation to verification, delivery and human decision.</p>

<p align="center"><strong>Start the control center in 5 minutes · Run a first installable, offline-capable and statically hostable PWA task in 30 minutes</strong></p>

<p align="center">
  <img alt="Free public preview" src="https://img.shields.io/badge/status-free_preview-0891b2">
  <img alt="Windows x64" src="https://img.shields.io/badge/platform-Windows_x64-0078D4?logo=windows11">
  <img alt="Proprietary software" src="https://img.shields.io/badge/license-proprietary-111827">
</p>

<p align="center">Free public preview · Proprietary software · Windows x64 · Local-first control plane</p>

<p align="center">
  <a href="README.zh-CN.md">简体中文</a> ·
  <a href="https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v2.2.1-preview.18"><strong>Download for Windows · Preview 18</strong></a> ·
  <a href="#see-it-in-60-seconds">Watch 60 seconds</a> ·
  <a href="#five-minutes-to-start-thirty-minutes-to-a-first-delivery">Quickstart</a> ·
  <a href="FIRST-PWA-TASK.md">First PWA task</a> ·
  <a href="CUSTOMER-INSTALL.md">Install guide</a> ·
  <a href="ARCHITECTURE.md">Architecture &amp; boundaries</a>
</p>

> [!IMPORTANT]
> This distributes a **free public preview of proprietary software**, not the CodeFlowMu source repository or an open-source license. Installers are unsigned and there is no formally supported stable version. The repository remains Private; publication requires separate checks and explicit approval.

> [!NOTE]
> Preview 17 still fails real user initialization because of root discovery and lacks an explicit exit entry. It is no longer recommended for fresh installs. The previous resource-level initialization test did not exercise the real HTTP entry point; that success did not prove customer initialization worked.

## Download and test status

**[V2.2.1 Preview 18](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v2.2.1-preview.18) is available as a GitHub Pre-release download**, not an active update target or stable release. User reinstall acceptance is pending. Isolated installation, 8,884-file inventory verification, real HTTP initialization with native confirmation, restart persistence, native exit and port release passed. Tests used bundled Node/Python without paid model calls.

- [Download CodeFlowMu-Setup-2.2.1-preview.18-win-x64.exe](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v2.2.1-preview.18/CodeFlowMu-Setup-2.2.1-preview.18-win-x64.exe).
- [Download SHA256SUMS.txt](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v2.2.1-preview.18/SHA256SUMS.txt).
- SHA-256: `2958ffb025ed1572d082b7eb3e23bca8fec01f4929d91f1b6780f334b27af298`.
- Historical Preview 17 on [GitHub Releases](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases) **does not contain this repair**.
- Customer assets consist only of the installer and `SHA256SUMS.txt`; GitHub's automatic Source code archives are not installers. The repository remains Private and requires a GitHub account with access.

## Your installation directory is the default project root

In Preview 18, choosing `E:\CodeFlowMu` means:

| Content | Default location |
| --- | --- |
| Application and default project root | `E:\CodeFlowMu` |
| Tasks, reports and collaboration files | `E:\CodeFlowMu\fcop` (created by initialization) |
| State, project registry, logs, Provider and update cache | `E:\CodeFlowMu\data` |

Fresh installs no longer default to `C:\ProgramData\CodeFlowMu` or a nested `projects\default`. Choose a directory writable by your Windows user. Separately registered business projects retain their own paths. A fresh installation needs no data migration; historical directories are not silently removed.

**To close CodeFlowMu:** closing the browser only closes its interface. Right-click the CodeFlowMu notification-area icon, choose **Exit CodeFlowMu**, and confirm. Alternatively use **Exit CodeFlowMu** in the Start menu or run `CodeFlowMu.exe --exit` from the installation directory. This stops running tasks and disconnects the phone control surface.

## Why this is not another chat window

An answer is not a delivery. Real software work needs scope, ownership, execution, verification, rework, evidence and a final decision. CodeFlowMu brings that lifecycle into one local control plane:

```text
Request
→ PM clarifies, plans and dispatches
→ DEV implements + OPS runs and delivers + QA verifies and regresses
→ REPORT and runtime evidence
→ PM review
→ human approval, rejection or continuation
```

Tasks, reports, approvals, files, live activity and delivery evidence remain connected. The human operator can see what the team is doing, why it is doing it, what actually changed and when intervention is required.

## See it in 60 seconds

[![Play the CodeFlowMu 60-second product overview](assets/video-poster.png)](https://joinwell52-ai.github.io/joinwell52/assets/video/codeflowmu-product-intro-zh.mp4?v=21-role-matrix)

Click the poster to play in the browser. The video uses real product surfaces: the PC control center, task tree, human gate, verification evidence and CodeFlowMu Mobile PWA. [Fallback: open the 1080p MP4 directly](https://joinwell52-ai.github.io/joinwell52/assets/video/codeflowmu-product-intro-zh.mp4?v=21-role-matrix).

## Install once, then upgrade by version

The Windows distribution uses a branded installer and version-controlled full-installer upgrades. An accepted target in the signed feed is required; Preview 18 is a manual GitHub download and is not automatically promoted into the update feed:

```text
First or manual installation
→ see the CodeFlowMu welcome page, product name, version and logo
→ choose the destination in the installer
→ confirm the final destination before files are written

A higher complete release version is detected
→ ask the user before downloading anything
→ the user confirms “Download and install”
→ download the full Windows installer
→ verify manifest signature, origin, size and SHA-256
→ silently apply it to the existing installation directory
→ verify the installed product version and candidate number
→ restart CodeFlowMu
```

Version control compares both the product version and release candidate:

- `V2.2.1-preview.15 < V2.2.1-preview.17`;
- `V2.2.1 < V2.2.2`;
- the same complete version is not downloaded again;
- an older version is never treated as an upgrade.

Only an accepted and explicitly published prerelease can become the signed update target. Drafts, local builds and unpublished candidates cannot trigger a customer upgrade. The updater preserves the existing installation directory; projects, tasks, reports and other mutable customer data must not be treated as replaceable program files.

> [!CAUTION]
> While this repository remains Private, ordinary external customers cannot anonymously read its update feed or Release assets. External customer upgrades can be enabled only after publication acceptance and an explicit switch to Public, or through a future supported authenticated download service. This change never alters repository visibility automatically.

## Before running the installer: verify, do not merely trust

A proprietary product cannot honestly claim a reproducible build from source in this repository. CodeFlowMu Distribution uses a **proprietary runtime plus reviewable release evidence**:

| What to verify | Evidence to inspect | Current conclusion |
| --- | --- | --- |
| Download origin | This repository's GitHub Release and explicit version tag | Accept only the official Release, never a mirror or forwarded file |
| File integrity | `SHA256SUMS.txt` | The installer hash can be recomputed independently; do not run a mismatch |
| Install, initialize and start | Checks bound to the installer hash | Preview 18 isolated install, real initialization, restart and exit passed; user acceptance is pending |
| Signing and provider | Unsigned installer; Cursor uses an external `sdk.v1` Provider | Preview only, not a stable formal release; provider accounts and compatibility are managed separately |

The Release download page intentionally contains only the installer and `SHA256SUMS.txt`. Product inventory, module configuration, security audit and installation-acceptance details remain in the Workbench's internal version record; customers are not asked to identify or download a collection of pipeline JSON files. See the [public repository readiness review](PUBLICATION-CHECKLIST.md) and [release policy](RELEASE-POLICY.md) for the boundary.

## Five minutes to start, thirty minutes to a first delivery

### Five minutes: install and open the control center

1. Use a Windows 10/11 x64 machine.
2. Download the installer and `SHA256SUMS.txt` from [V2.2.1 Preview 18](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v2.2.1-preview.18), not historical Preview 17.
3. Compare the installer SHA-256 against this candidate's record.
4. Install and launch **CodeFlowMu**.
5. Confirm that the header project root matches the chosen installation directory, then confirm initialization in Environment Preflight. Preserve errors instead of repeatedly clearing the environment. Additional business projects can be registered separately.

Verify the download in PowerShell:

```powershell
(Get-FileHash .\CodeFlowMu-Setup-2.2.1-preview.18-win-x64.exe -Algorithm SHA256).Hash
```

Compare the output with this page's candidate SHA-256, ignoring case. Do not run a mismatch.

> [!WARNING]
> The test installer is unsigned and Windows SmartScreen may warn. The default project shares the installation directory, but application binaries, bundled runtimes and `data` must not be deleted or overwritten as task outputs. Provider accounts, credentials and usage charges are separate from the free preview. Installation/startup checks do not prove a real model business workflow.

### Thirty minutes: have the team deliver a real static PWA

The standard first task is not “Hello World.” It is an installable, offline-capable and statically hostable **ShipReady PWA**:

- add, complete, reopen and delete today's delivery items;
- persist data in `localStorage`;
- work on phone and desktop widths;
- include a Web App Manifest and Service Worker;
- open offline after the first successful load;
- use no backend, database, CDN or external API;
- deploy to GitHub Pages, Cloudflare Pages or any HTTPS static host.

<details>
<summary><strong>Expand and copy the complete first task to PM</strong></summary>

<br>

```text
Build and deliver a static PWA named ShipReady.

Users can add, complete, reopen and delete “today's delivery items.” Show the total,
completed count and completion percentage. Persist data in localStorage. Support a
390px phone viewport. Include manifest.webmanifest, a Service Worker, 192/512 icons
and a README. Use no backend, database, CDN or external API. After the first load,
the app must still open and work offline.

QA must verify every behavior, refresh persistence, responsive layout, Manifest,
Service Worker, offline mode and console errors. OPS must provide a local run path.
Any public deployment requires my explicit approval before it happens; after approval,
return the deployment URL and verification evidence. PM must summarize the delivery
and every known limitation.
```

</details>

**Next:** follow [Your first ShipReady PWA, step by step](FIRST-PWA-TASK.md) for screen-by-screen actions, success signals, role handoffs, the acceptance table, static deployment and Mobile PWA continuation.

## What happens during the first task

| Stage | Team action | Success signal |
| --- | --- | --- |
| Request enters | You give the brief to PM and review it before publication | A formal TASK appears in the task list |
| Plan and dispatch | PM fixes scope, acceptance criteria and child work | DEV, QA and OPS work appears in the task tree |
| Engineering | DEV creates the static site and PWA capabilities | Page, Manifest, Service Worker and icon files appear in the project |
| Run and deliver | OPS starts a local static server and records the entry point | The local URL works; any public deployment waits for approval |
| Verify and regress | QA tests behavior, phone layout, persistence and offline use | A REPORT maps PASS/FAIL and evidence to every criterion |
| Review and accept | PM summarizes results, limitations and rework | The human accepts, rejects or continues the delivery |

The example demonstrates the central principle: **commands flow, evidence returns, humans decide.**

## The product today: a four-role digital development team

| Role | Current responsibility | Work in the first PWA example |
| --- | --- | --- |
| **PM** | Clarify, plan, dispatch and review | Freeze scope, acceptance criteria and the delivery conclusion |
| **DEV** | Implement and refactor inside an authorized project | Build UI, interaction, storage, Manifest and Service Worker |
| **QA** | Verify criteria, test behavior and report regressions | Test behavior, 390px layout, offline use, installability and errors |
| **OPS** | Run environments, deliver artifacts and record evidence | Start the static service; after approval, deploy and verify the public URL |

The human remains ADMIN: defining project scope, holding credentials, approving external writes and risky operations, and accepting the final result from reports and evidence.

## Public architecture: TMPA → FCoP → CodeFlowMu

CodeFlowMu is the engineering implementation in a public three-part architecture: TMPA defines governance theory and normative semantics, FCoP turns collaboration and evidence into a tool-executable protocol, and CodeFlowMu provides the Agent programming Runtime that performs real engineering work.

<p align="center">
  <picture>
    <source srcset="assets/architecture/tmpa-fcop-codeflowmu-public-architecture.svg" type="image/svg+xml">
    <img src="assets/architecture/tmpa-fcop-codeflowmu-public-architecture.png" alt="TMPA–FCoP–CodeFlowMu public architecture" width="100%">
  </picture>
</p>

| System | Public position | What it contributes | What it is not |
| --- | --- | --- | --- |
| **TMPA** | Theory and normative governance layer | Governance objects, role/action relationships, Reader semantics and conformance criteria | An application Runtime or tool host |
| **FCoP** | File-based collaboration and evidence protocol | TASK / REPORT / REVIEW / ISSUE records, lifecycle semantics, references and tool entry points such as PyPI and MCP | The CodeFlowMu Runtime or a substitute for real execution |
| **CodeFlowMu** | Agent programming engineering Runtime | A **Runtime Foundation**, pluggable **Execution Slots**, and a controlled **Capability Bus** for models, Skills, MCP tools and local engineering tools | A new name for TMPA or FCoP |

The operational loop is explicit: **CodeFlowMu work actions → FCoP collaboration evidence → TMPA governance reconstruction → CodeFlowMu governance use**. This diagram is a public semantic view; it does not disclose private deployment topology, provider configuration, internal class names or credentials, and it does not make a new conformance claim.

Public references: [TMPA A1.0](https://joinwell52-ai.github.io/joinwell52/zh/publications/tmpa-architecture-paper-a1.0) · [TMPA S1.0](https://joinwell52-ai.github.io/joinwell52/zh/publications/tmpa-core-specification-s1.0) · [TMPA–FCoP–CodeFlowMu I1.0](https://joinwell52-ai.github.io/joinwell52/zh/publications/implementation-case-i1.0) · [FCoP](https://joinwell52-ai.github.io/FCoP/) · [Public architecture and trust boundaries](ARCHITECTURE.md)

| Path | Entry point | Use it for | Boundary to understand |
| --- | --- | --- | --- |
| Theory and specification | [TMPA / Digital Employee Works](https://github.com/joinwell52-AI/joinwell52) | Study governance architecture, normative Core, conformance and evidence ideas | Follow that repository's own license and status |
| Collaboration protocol | [FCoP](https://github.com/joinwell52-AI/FCoP) | Study or implement the MIT-licensed file-based behavior-governance protocol | The protocol is not the proprietary CodeFlowMu runtime source |
| Early implementation | [CodeFlowMu-open](https://github.com/joinwell52-AI/CodeFlowMu-open) | Inspect the earlier four-role product proof and historical workflows | Maintenance-frozen; not the current product's Community Edition or Open Core |
| Current product | **CodeFlowMu Distribution** | Download the proprietary PC/PWA product, report issues and inspect release evidence | A free preview is not open source; the current Release contract controls |
| Ecosystem integration | Candidate future public SDKs, adapters and examples | Build integrations, adapters and templates against stable interfaces | No compatibility-backed public SDK exists today; this is roadmap only |
| Long-term product direction | **Digital employee development machine** | Produce, test, assemble and upgrade employee packages | Not a current capability |

This is a **Spec First + Proprietary Distribution** path, not a relabeling of the early open-source version as the current product's Open Core. The ideas and protocol continue while product engineering and distribution boundaries evolve; old install methods, ports, capabilities and support status do not transfer to Distribution.

## Skills, MCP, permission and evidence

| Concept | What it answers | What it cannot decide by itself |
| --- | --- | --- |
| **Role** | Who owns planning, implementation, verification or operations? | A role name does not grant unlimited authority |
| **Skill / Playbook** | Which procedure, constraint and evidence standard should a role follow? | A Skill is not a tool and does not create execution authority |
| **MCP / Tool** | Which external capability can an agent connect to and call? | A callable tool does not make a task legitimate or an outcome trustworthy |
| **Permission** | Is this operation authorized for this project and occurrence? | Skill or MCP cannot expand it on their own |
| **FCoP** | How do TASK, REPORT, ISSUE and REVIEW persist and hand off? | A protocol record does not replace a real runtime result |
| **Evidence** | How is a real file, command, test or page demonstrated? | Evidence cannot accept business risk for a human |
| **Human Gate** | Who approves external writes, sensitive actions and final delivery? | Technical checks cannot replace product acceptance |

V2.2.1 Preview 18 ships a Skill schema, 48 manifest-referenced Skill packages, a controlled FCoP MCP execution boundary and Browser Use runtime components. A capability is usable only when the product actually ships it, the project enables it and the operation is authorized. This README does not promise automatic installation of arbitrary community MCP servers or formal support for unverified tools.

## Real product surfaces

| PC control center | Task tree |
| --- | --- |
| ![CodeFlowMu PC control center](assets/screens/desktop-control-center.png) | ![CodeFlowMu task tree](assets/screens/task-graph.png) |

| Runtime and protocol evidence | CodeFlowMu Mobile PWA |
| --- | --- |
| ![CodeFlowMu runtime evidence](assets/screens/runtime-evidence.png) | <img src="assets/screens/mobile-pwa.png" alt="CodeFlowMu Mobile PWA" width="260"> |

## CodeFlowMu Mobile PWA: manage delivery away from the PC

CodeFlowMu Mobile PWA is a remote control surface for a running PC instance, not a second product that executes independently.

```text
Start CodeFlowMu on the PC
→ refresh Gateway and binding information on Mobile
→ bind the phone over LAN or the public Gateway
→ inspect the ShipReady task tree, role states, REPORTs and live activity
→ ask PM from the phone to “add dark mode”
→ review the second QA/OPS evidence cycle
→ handle decisions that require human approval or acceptance
```

Never share a QR code or bind link. Revoke lost or retired devices from the PC. The PWA, Gateway, PC product and Provider have independent version lifecycles. See the [install and Mobile PWA guide](CUSTOMER-INSTALL.md).

## Current capability and roadmap boundary

### Available today

- Windows x64 installer with bundled base Node.js/Python runtimes;
- PC control center for projects, tasks, reports, approvals, files, logs, skills and runtime state;
- fixed PM / DEV / QA / OPS team and visible task tree;
- FCoP-backed task, report, issue, review and evidence collaboration;
- human gates and project authority boundaries;
- Mobile PWA bound to a running PC;
- external Provider lifecycle plus release manifests, security and third-party license evidence.

### Installation and upgrade capabilities (check the version status)

- CodeFlowMu-branded welcome page, product logo, complete candidate identity and non-colliding installer filename;
- interactive destination selection before installation;
- update detection using both product version and release-candidate number;
- user-confirmed download, verification and installation of the full Windows installer;
- post-upgrade version verification, preservation of the current install directory and automatic restart;
- update-feed activation only after the Workbench publishes an accepted prerelease.
- Preview 18 repairs root discovery, uses the installation as the default project root and adds native tray exit; its GitHub Pre-release is available while user acceptance and formal release approval remain pending.

### Roadmap only

The “digital employee development machine” is intended to produce, test, assemble and upgrade reusable digital employee packages. It remains outside the current product promise until those capabilities ship with their own evidence, compatibility and lifecycle contracts.

### Near-term release gates, not date commitments

- repository visibility may change only after repository-owner product acceptance;
- add code signing for a formal installer;
- add real-account Cursor Provider compatibility evidence;
- continue to record versions, changes, hashes and compatibility boundaries through GitHub Releases;
- decide whether to publish SDKs, adapters and examples only after public interfaces, authority models and compatibility tests are stable.

## Openness boundary: current, candidate and proprietary

| Public now | Evaluate after stabilization | Must remain private |
| --- | --- | --- |
| Product ideas, architecture, four-role responsibilities and sanitized real screenshots | Versioned public APIs and a minimal SDK | Current proprietary product source and private implementation history |
| Public TMPA and FCoP specifications and project relationships | Sanitized adapter, example and template repositories | Unreleased governance experiments and private evaluation policy |
| Skill formats, layers, public templates and sanitized Playbook examples | Extension kits with explicit authority and compatibility contracts | Customer Skills, business knowledge, tasks, reports, logs and data |
| MCP's architectural position, controlled tool classes and safety principles | Security-reviewed client protocols and adapter examples | Gateway credentials, Provider keys, customer MCP configuration and private backend topology |
| Install, first-task, PWA binding and static deployment tutorials | Standalone static examples and verification tools | Signing material, release credentials, internal test accounts and private pipelines |
| Installer, hashes, manifests, third-party notices and reviewed public security evidence | Versioned compatibility matrices and migration examples | Any build or runtime material that has not passed sanitization and publication review |

Public repository visibility does not make the product open source. Technical checks also do not complete product acceptance; only the repository owner's explicit acceptance and publication approval can authorize a future visibility change.

## Documentation and support

- [Your first ShipReady PWA, step by step](FIRST-PWA-TASK.md)
- [Install, Provider, Mobile PWA and upgrade guide](CUSTOMER-INSTALL.md)
- [Public architecture and trust boundaries](ARCHITECTURE.md)
- [中文 README](README.zh-CN.md)
- [Release policy](RELEASE-POLICY.md)
- [Public repository readiness review](PUBLICATION-CHECKLIST.md)
- [Support policy](SUPPORT.md)
- [Security policy](SECURITY.md)
- [Proprietary software notice](LICENSE.md)

After publication, use GitHub Issues for sanitized reproducible problems. Never post API keys, bind links, customer data, private source or internal tasks. Report vulnerabilities privately as described in [SECURITY.md](SECURITY.md).

---

**Commands flow. Evidence returns. Humans decide.**
