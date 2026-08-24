# CodeFlowMu

<p align="center">
  <img src="assets/brand/codeflowmu-logo.png" alt="CodeFlowMu" width="132">
</p>

<p align="center"><strong>Turn a software request into a visible, interruptible, verifiable delivery with a local PM · DEV · QA · OPS digital development team.</strong></p>

<p align="center"><strong>Software delivery is not a chat response. It is a collaboration flow made of roles, tasks, tools, evidence and human decisions.</strong></p>

<p align="center">Free public preview · Proprietary software · Windows x64 · Local-first control plane</p>

<p align="center">
  <a href="README.zh-CN.md">简体中文</a> ·
  <a href="#five-minutes-to-start-thirty-minutes-to-a-first-delivery">Quickstart</a> ·
  <a href="FIRST-PWA-TASK.md">First PWA task</a> ·
  <a href="CUSTOMER-INSTALL.md">Install guide</a> ·
  <a href="ARCHITECTURE.md">Architecture</a> ·
  <a href="https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases">Downloads</a>
</p>

> [!IMPORTANT]
> This is the distribution repository for a **free public preview of proprietary software**. It is not the CodeFlowMu source repository and it grants no open-source license. The current `v1.9.7-candidate.1` download is an unsigned pre-release candidate, not a stable or formally supported release. The repository remains Private pending product acceptance and explicit publication approval.

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

[![Watch the CodeFlowMu 60-second overview](assets/video-poster.png)](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v1.9.7-candidate.1/CodeFlowMu-60s-overview-v1.9.7.mp4)

The video uses real product surfaces: the PC control center, task tree, human gate, verification evidence and CodeFlowMu Mobile PWA. [Download the MP4](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/download/v1.9.7-candidate.1/CodeFlowMu-60s-overview-v1.9.7.mp4).

## Five minutes to start, thirty minutes to a first delivery

### Five minutes: install and open the control center

1. Use a Windows 10/11 x64 machine.
2. Download the installer and `SHA256SUMS.txt` from [V1.9.7 Candidate 1](https://github.com/joinwell52-AI/CodeflowMu-Distribution/releases/tag/v1.9.7-candidate.1).
3. Verify installer SHA-256: `15c96e86d0583540793d0178727a1082ef38395831c460c988d9efc4ad2aca86`.
4. Install and launch **CodeFlowMu**.
5. Confirm that the header reports a connected state, then register an empty example project in Settings.

> [!WARNING]
> Candidate 1 is unsigned and Windows SmartScreen may warn. The formal real-Cursor-account compatibility gate has not passed. The installation root is not a business project and agents must not develop inside it. Provider accounts, credentials and any usage charges are separate from the free CodeFlowMu preview.

### Thirty minutes: have the team deliver a real static PWA

The standard first task is not “Hello World.” It is an installable, offline-capable and statically hostable **ShipReady PWA**:

- add, complete, reopen and delete today's delivery items;
- persist data in `localStorage`;
- work on phone and desktop widths;
- include a Web App Manifest and Service Worker;
- open offline after the first successful load;
- use no backend, database, CDN or external API;
- deploy to GitHub Pages, Cloudflare Pages or any HTTPS static host.

Copy this task to PM:

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

For the screen-by-screen actions, success signals, role handoffs, acceptance table, static deployment and Mobile PWA continuation, follow [Your first ShipReady PWA, step by step](FIRST-PWA-TASK.md).

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

## From theory to engineering

CodeFlowMu is not an isolated app. It is a continuous path from governance ideas to software delivery:

```text
TMPA: why digital employees must be governable, traceable and reviewable
  ↓
FCoP: how tasks, reports, issues, reviews and evidence persist
  ↓
PM / DEV / QA / OPS: who owns each part of delivery
  ↓
Skills / Playbooks: which method and evidence standard each role follows
  ↓
MCP / controlled tools: which engineering capabilities roles may connect to and call
  ↓
PC control center + Mobile PWA: where humans observe, instruct, interrupt and approve
  ↓
REPORT / Evidence / Human Gate: how completion is proved and a human decides the result
```

| Layer | Public project or product responsibility |
| --- | --- |
| Theory and specification | [TMPA / Digital Employee Works](https://github.com/joinwell52-AI/joinwell52): governance architecture, normative Core, conformance and evidence ideas |
| Collaboration protocol | [FCoP](https://github.com/joinwell52-AI/FCoP): MIT-licensed file-based behavior-governance protocol |
| Early product proof | [CodeFlowMu-open](https://github.com/joinwell52-AI/CodeFlowMu-open): earlier open-source four-role team, now maintenance-frozen |
| Current product | **CodeFlowMu Distribution**: proprietary installed product, isolated Runtime, PC/PWA, Provider lifecycle and release evidence |
| Long-term direction | **Digital employee development machine**: produce, test, assemble and upgrade employee packages; not a current capability |

The ideas and protocol continue; product engineering and distribution boundaries evolve. CodeFlowMu-open is not the source of the current proprietary product, and its install method, ports, capabilities and support status must not be assumed to apply to Distribution.

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

Candidate 1 ships a Skill schema, a controlled FCoP MCP execution boundary and Browser Use runtime components. A capability is usable only when the product actually ships it, the project enables it and the operation is authorized. This README does not promise automatic installation of arbitrary community MCP servers or formal support for unverified tools.

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

### Roadmap only

The “digital employee development machine” is intended to produce, test, assemble and upgrade reusable digital employee packages. It remains outside the current product promise until those capabilities ship with their own evidence, compatibility and lifecycle contracts.

## What can be public

| Public-safe | Must remain private |
| --- | --- |
| Product ideas, architecture, four-role responsibilities and sanitized real screenshots | Current proprietary product source and private implementation history |
| Public TMPA and FCoP specifications and project relationships | Internal mother Skills, unreleased governance experiments and private evaluation policy |
| Skill formats, layers, public templates and sanitized Playbook examples | Customer Skills, business knowledge, tasks, reports, logs and data |
| MCP's architectural position, controlled tool classes and safety principles | Gateway credentials, Provider keys, customer MCP configuration and private backend topology |
| Install, first-task, PWA binding and static deployment tutorials | Signing material, release credentials, internal test accounts and private pipelines |
| Installer, hashes, manifests, third-party notices and reviewed public security evidence | Any build or runtime material that has not passed sanitization and publication review |

Public repository visibility does not make the product open source. Technical checks also do not complete product acceptance; only the repository owner's explicit acceptance and publication approval can authorize a future visibility change.

## Documentation and support

- [Your first ShipReady PWA, step by step](FIRST-PWA-TASK.md)
- [Install, Provider, Mobile PWA and upgrade guide](CUSTOMER-INSTALL.md)
- [Architecture and trust boundaries](ARCHITECTURE.md)
- [中文 README](README.zh-CN.md)
- [Release policy](RELEASE-POLICY.md)
- [Public repository readiness review](PUBLICATION-CHECKLIST.md)
- [Support policy](SUPPORT.md)
- [Security policy](SECURITY.md)
- [Proprietary software notice](LICENSE.md)

After publication, use GitHub Issues for sanitized reproducible problems. Never post API keys, bind links, customer data, private source or internal tasks. Report vulnerabilities privately as described in [SECURITY.md](SECURITY.md).

---

**Commands flow. Evidence returns. Humans decide.**
