# Your First ShipReady PWA, Step by Step

This guide takes a first-time CodeFlowMu user through a real, verifiable delivery loop. Starting from one product brief, PM, DEV, QA and OPS collaborate to deliver an installable, offline-capable and statically hostable PWA.

> [!IMPORTANT]
> This tutorial is a product-use example, not a claim that Candidate 1 has passed the formal Provider compatibility gate. Confirm that your Provider can create and run agents in your environment before starting. Repository publication, static deployment and every other external write require separate explicit human approval.

## What you will deliver

App name: **ShipReady**

Users can:

- add today's delivery items;
- complete or reopen them;
- delete items and clear completed work;
- see total, completed and percentage counts;
- retain data after refresh;
- install the app on a phone home screen;
- keep using it offline after the first successful load.

Expected files:

```text
shipready/
├─ index.html
├─ styles.css
├─ app.js
├─ manifest.webmanifest
├─ sw.js
├─ icons/
│  ├─ icon-192.png
│  └─ icon-512.png
└─ README.md
```

Every asset must use relative paths so that the app works under a repository subpath such as GitHub Pages. Service Workers run on `localhost` or HTTPS; opening a `file://` page is not a valid PWA test.

## Preflight

| Check | Success signal |
| --- | --- |
| CodeFlowMu is running | Header reports a connected state |
| Provider is configured | Model/agent connection validation succeeds |
| Example project is registered | Header project and project root agree |
| Project is not the install root | Business files will be written to an independent project |
| Environment preflight is complete | No task-execution blocker remains |
| Project is recoverable | Empty project or an initial Git commit exists |

If project, Runtime, MCP, Watcher or agent working-directory state disagrees, stop writes and repair the binding first.

## Step 1: create and select the example project

1. Open **Settings → Projects**.
2. Create a blank project or register a new empty directory.
3. Set it as the active project.
4. Confirm the project name and root shown in the header.
5. Open **Environment Preflight** and resolve real blockers.

Never register the CodeFlowMu Program Files installation directory as the example project.

## Step 2: give the complete brief to PM

Copy the following task:

```text
Build and deliver a static PWA named ShipReady.

Product goal:
Help users record the delivery items that must be completed today and see progress.

Functional requirements:
1. Users can add a delivery item.
2. Users can mark an item complete or incomplete.
3. Users can delete an item.
4. Users can clear all completed items.
5. Show total items, completed items and completion percentage.
6. Persist data in localStorage across refreshes.
7. Support desktop and a 390px phone viewport without horizontal scrolling.
8. Include a valid manifest.webmanifest, Service Worker and 192/512 PNG icons.
9. After a successful first load, the app must open and work offline.
10. Use no backend, database, CDN, remote font or external API.
11. Use relative asset paths so the app can run under a hosted subdirectory.

Engineering deliverables:
- index.html
- styles.css
- app.js
- manifest.webmanifest
- sw.js
- icons/icon-192.png
- icons/icon-512.png
- README.md

Acceptance requirements:
- QA maps PASS/FAIL evidence to add, complete, reopen, delete, clear and statistics.
- QA verifies refresh persistence, 390px layout, Manifest, Service Worker, offline use
  and browser console errors.
- OPS provides the local static-server command, entry URL and runtime verification.
- Any GitHub, Cloudflare or other public deployment requires my explicit approval first.
- After approved deployment, OPS returns a credential-free URL, revision and access evidence.
- PM summarizes delivered files, acceptance results, limitations and an accept/rework recommendation.
```

In **Tasks → Submission Review**, confirm:

- the project root is correct;
- scope is limited to a static PWA;
- external dependencies are forbidden;
- every requirement is testable;
- public deployment explicitly requires human approval.

Only then publish the formal TASK.

## Step 3: watch PM plan and dispatch

Open the task tree. A reasonable plan covers at least:

| Work | Suggested owner | Required evidence |
| --- | --- | --- |
| Freeze scope and acceptance criteria | PM | Formal task and acceptance checklist |
| Page, interaction and local storage | DEV | Changed files and behavior summary |
| Manifest, Service Worker and icons | DEV | PWA files and registration result |
| Local static service | OPS | Command, URL and health result |
| Functional and persistence verification | QA | Criterion-level PASS/FAIL |
| Phone layout and offline verification | QA | Viewport, offline and console evidence |
| Public static deployment | OPS | Execute only after explicit approval |
| Final review | PM | Consolidated REPORT and acceptance recommendation |

PM may choose a different number of child tasks, but it must not omit acceptance, execution and evidence ownership.

## Step 4: inspect real engineering artifacts

In **Files** or the business project directory, confirm that the expected files exist.

Pay particular attention to:

- relative `start_url` and `scope` values suitable for subpath hosting;
- `index.html` registering `sw.js`;
- the Service Worker caching the application shell, not private data or credentials;
- no remote CDN, font, analytics script or API request;
- `localStorage` containing only the user's local delivery items;
- README instructions for local serving, PWA verification and static deployment.

## Step 5: run and verify

Use the local static-server command and URL reported by OPS. Do not use `file://` to verify a Service Worker.

QA should return at least:

| Criterion | Verification | Expected result |
| --- | --- | --- |
| Add | Add three items | Three rows, statistics 0/3 |
| Complete | Complete two | Statistics 2/3, about 67% |
| Reopen | Reopen one | Statistics return to 1/3 |
| Delete | Delete one | Total and completed counts update |
| Clear completed | Complete then clear | Only completed items are removed |
| Persistence | Refresh | Items and completion state remain |
| Phone layout | Use a 390px viewport | No horizontal scroll; controls remain usable |
| Manifest | Inspect browser Manifest | Name, icons, start_url and scope are valid |
| Service Worker | Inspect registration | Active and controlling the page |
| Offline | After first load, switch Offline and refresh | App opens and core behavior works |
| Console | Inspect Console | No unhandled error |

Browser Use may replace some manual browser actions only when the current product ships it, the project enables it and the operation is authorized. A tool call never replaces QA's evidence-to-criterion mapping.

## Step 6: decide whether to publish statically

After local acceptance, PM or OPS may request public deployment but must not publish on its own.

Before approval, confirm:

- the artifact contains only this public example app;
- there is no `.env`, API key, bind link, log, TASK, REPORT or customer data;
- no CodeFlowMu product source is present;
- icons, fonts and other assets are publishable;
- target repository, site and branch are correct;
- static paths work under the chosen site subpath;
- you understand that deployment is an external write.

Possible outcomes:

- GitHub Pages;
- Cloudflare Pages;
- another HTTPS static host;
- no publication—retain local acceptance only.

After approval, OPS should return the deployment target, revision, public URL, HTTP result, phone result and cache-update behavior.

## Step 7: continue from CodeFlowMu Mobile PWA

ShipReady is the example app the team delivers. CodeFlowMu Mobile PWA is the control surface used to manage the team. They are two different PWAs.

1. Keep CodeFlowMu running on the PC.
2. Open **Mobile** on the PC and refresh binding information.
3. Bind the phone over LAN or the public Gateway.
4. On the phone, inspect the ShipReady task tree, REPORTs and live activity.
5. Send PM this follow-up:

```text
Add dark mode to ShipReady. Follow the system theme by default and provide a manual
toggle whose choice survives refresh. Do not change the existing data structure.
QA must regress all original behavior, the 390px layout and offline mode. OPS must
verify the cache upgrade at the existing static URL.
```

6. Review the second DEV, QA and OPS evidence cycle.
7. Accept or continue rework as a human decision.

Never share a bind QR or URL. Revoke a lost or retired phone from the PC.

## Troubleshooting

| Symptom | Check first |
| --- | --- |
| PM does not start | Provider connection, model state and Runtime logs |
| TASK lands in the wrong project | Header root, Runtime, MCP, Watcher and agent cwd agreement |
| Page opens but PWA features fail | localhost/HTTPS and relative Manifest/Service Worker paths |
| GitHub Pages returns 404 | Repository subpath, entry-file location and Pages publish directory |
| Offline refresh fails | Service Worker scope, cache list and completed first online load |
| Old page remains after update | Service Worker version, cache name and activation strategy |
| Phone cannot see team state | PC running state, Gateway health and bind expiry |
| OPS is about to publish directly | Stop execution and obtain explicit deployment approval |

## Definition of done

The first task is complete only when:

- ShipReady passes functional, responsive and offline acceptance on a local static service;
- DEV, QA and OPS each return role-appropriate REPORTs and evidence;
- PM gives an explicit conclusion for every criterion;
- a human completes final acceptance;
- if public deployment occurred, it happened after explicit approval and the content was sanitized;
- CodeFlowMu Mobile PWA can inspect the task and a second change forms a new traceable delivery cycle.
