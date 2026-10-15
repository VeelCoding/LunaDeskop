# P12-1B Main/Preload Seam Probe V1 — Partial Evidence

Date: 2026-10-15
Status: PARTIAL / PROBE STOPPED AFTER HIGH-VALUE SOURCE READ

## Locked identity

```text
app.asar SHA256 = 356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325
ASAR header JSON SHA256 = FA8C9B0734EA4E4DFEFE176A3375A9ED8E16C0C848D01A8A864D995D0348592D
P12-1B ASAR identity = PASS
P12-1B header identity = PASS
```

## Exact .vite/build surface

The probe resolved 34 direct `.vite/build` entries. High-value owners include:

```text
early-bootstrap.js
bootstrap-iULMfRBf.js
main-Bgi5Xaw-.js
preload.js
browser-page-preload.js
sandbox-preload.js
conversation-turn-mutations-szl89rld.js
worker.js
```

Exact target identities:

```text
early-bootstrap.js
  bytes = 3304
  SHA256 = 61D485EB56C803D6A0EE4EC55F8E4E2A9547FFE118E2FC6F835668BE6872F8AE

bootstrap-iULMfRBf.js
  bytes = 461537
  SHA256 = 385E3885EDA6A2852D8E0B75D1D0B579AC06E27EB9B9300FA7E92D9B5216C869

main-Bgi5Xaw-.js
  bytes = 3827962
  SHA256 = E8923725AD6357380AC7BB25818F78EB4D97E522EBBDE2DDF6FF5A2A93032E54

preload.js
  bytes = 6909
  SHA256 = A3E622F8D80A83E58FB3CFCC640FA7E14E6461CCCDAE9EF7D7B0C821DDE256B7

browser-page-preload.js
  bytes = 527604
  SHA256 = 6844EC68A38171555A8DBDD97C1BFB524E358EDFF60E0146FD77073694DBB515

sandbox-preload.js
  bytes = 2102
  SHA256 = E24E4D655E339484EB0EF842393BEBFA13FB86A7863350EF49CD6A63EB1BDDFA

conversation-turn-mutations-szl89rld.js
  bytes = 52799
  SHA256 = 116870FB4AA77E0D56A9C1AEF70B7C6B21A7EA30EF5B601A6D2A7CB7B719C3EC
```

## Exact startup chain

`early-bootstrap.js` is the package-declared main entry and performs early Chromium/network/bootstrap setup. After startup requirements succeed, it dynamically loads `bootstrap-iULMfRBf.js`.

Observed chain:

```text
package.json main
-> .vite/build/early-bootstrap.js
-> startup requirements / network permissions
-> .vite/build/bootstrap-iULMfRBf.js
-> .vite/build/main-Bgi5Xaw-.js and supporting modules
```

This is current product evidence, not a historical D-series inference.

## Preload bridge — strong seam candidate

`.vite/build/preload.js` exposes `electronBridge` into the renderer through Electron `contextBridge`.

High-value bridge behavior includes:

```text
renderer -> main:
  ipcRenderer.invoke("codex_desktop:message-from-view", message)

main -> renderer:
  ipcRenderer.on("codex_desktop:message-for-view", ...)
  -> window.dispatchEvent(new MessageEvent("message", { data: message }))

worker bridge:
  codex_desktop:worker:<id>:from-view
  codex_desktop:worker:<id>:for-view

additional narrow IPC:
  show-context-menu
  get-fast-mode-rollout-metrics
  get-initial-sidebar-bootstrap
  system-theme-variant-updated
  start-file-drag
  start-link-drag
```

Preliminary classification:

```text
preload.js = strong B candidate (protocol / IPC / adapter plumbing)
```

This is not yet promoted to a final Desktop/Luna adapter owner. The corresponding main-side handler and task/session/approval/cancel authority paths still need exact inspection.

## MCP sandbox preload

`.vite/build/sandbox-preload.js` bridges the MCP Apps sandbox guest via Electron IPC and message ports. It includes operations such as MCP app host context, tool input/result/cancel notifications, environment preparation, user-code execution, screenshot, stop, and widget operations.

Preliminary classification:

```text
sandbox-preload.js = B / MCP-app-specific plumbing
```

It remains additive/plugin-adjacent and must not be made a prerequisite for core Desktop/Luna connectivity without new exact evidence.

## Probe STOP

The probe stopped after static dependency output because PowerShell collapsed a one-element dependency result into a scalar string and strict-mode `.Count` access failed:

```text
P12_1B_MAIN_PRELOAD_SEAM_V1=STOP
STOP reason = 'Count' property absent on scalar result
```

This is a probe-shape bug, not a negative product finding.

No extraction or mutation occurred:

```text
ASAR extraction = NOT PERFORMED
source mutation = NOT PERFORMED
repository mutation = NOT PERFORMED
git add/commit/push = NOT PERFORMED
```

## Next

Rerun a corrected P12-1B probe with all pipeline results forced to arrays. Continue exact main-side handler / process-launch / approval / cancel / retry / recovery signal extraction before final A/B/C mapping.
