# P12-1C Exact Router / Request Owner V1 — PASS

Date: 2026-10-15
Status: PASS

## Locked packaged baseline

- app.asar SHA256: `356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325`
- ASAR header JSON SHA256: `FA8C9B0734EA4E4DFEFE176A3375A9ED8E16C0C848D01A8A864D995D0348592D`

## Exact source set

- `.vite/build/bootstrap-iULMfRBf.js` — `385E3885EDA6A2852D8E0B75D1D0B579AC06E27EB9B9300FA7E92D9B5216C869`
- `.vite/build/main-Bgi5Xaw-.js` — `E8923725AD6357380AC7BB25818F78EB4D97E522EBBDE2DDF6FF5A2A93032E54`
- `.vite/build/application-network-startup-YSC7OAs0.js` — `52F0BE375FB08281E88AD41BE64220FB73F85210523E53E7D7ACF094FDA6344E`
- `.vite/build/src-CP7XXlpZ.js` — `79623D50989F9EFBCB8E5752C56B3CC608A0F5993C05112E03E11B718AC7A586`

## Exact IPC alias resolution

Bootstrap defines:

- `St = codex_desktop:message-from-view`
- `Ct = codex_desktop:message-for-view`

Bootstrap export table maps:

- `exports.wt = St` -> main import `g.wt` is `codex_desktop:message-from-view`
- `exports.bt = Ct` -> main import `g.bt` is `codex_desktop:message-for-view`

Main registers `ipcMain.handle(g.wt, ...)` for renderer-to-main Desktop messages. After Desktop-global message handling, routing falls through to the window-context `handleMessage(sender, message)` owner.

## Exact app-server bridge

The per-window/main message handler contains a `case "mcp-request"` branch. It:

1. receives renderer request metadata and request object,
2. obtains the selected host connection,
3. calls `getAppServerConnection(hostId).handleClientRequest(...)`,
4. routes app-server responses back to the view through `sendAppServerResponseToView(...)`,
5. explicitly emits a `mcp-request-delivery` failure with delivery stage `not-sent` when the bridge fails before send and retained-response semantics are requested.

This establishes the concrete Desktop adapter seam. The historical message type is named `mcp-request`, but P12 must not treat that name as an MCP authority boundary; it is the generic Desktop<->Codex app-server request bridge in this packaged generation.

## Request/lifecycle client

The main bundle request client has:

- `requestLifecycleListeners`
- `sendRequest(...)`
- `handleHostRequest(...)`
- explicit `outcome-unknown`
- timeout behavior calling `request.abandon()` rather than asserting remote non-execution.

Effect-bearing methods receiving the outcome-unknown path include at least:

- `thread/start`
- `thread/startAeon`
- `thread/fork`
- `turn/start`
- `turn/steer`
- `plugin/uninstall`

This strongly matches the P12/D21 law that local timeout/abandon is not proof of remote non-effect.

## Provisional responsibility classification

### A — presentation/state projection
- renderer/webview UI and conversation projection
- conversation-turn state reducers/mutations

### B — adapter/plumbing
- `preload.js` Electron bridge
- `codex_desktop:message-from-view` / `message-for-view`
- main IPC routing
- response projection to renderer
- app-server transport implementation as transport plumbing only

### C — execution/lifecycle/authority logic that must belong to or delegate to Luna in the target architecture
- effect-bearing request admission
- task/thread/turn execution request authority
- `outcome-unknown` interpretation
- timeout/abandon policy
- retry/reconnect/recovery decisions
- approval authority
- interrupt/cancel completion truth

Important: source co-location in `main-*.js` does not imply all of it remains Desktop-owned. P12 classifies by responsibility, not by file.

## Probe result

- `P12_1C_ASAR_EXTRACTION=NOT_PERFORMED`
- `P12_1C_SOURCE_MUTATION=NOT_PERFORMED`
- `P12_1C_REPOSITORY_MUTATION=NOT_PERFORMED`
- `P12_1C_GIT_ADD=NOT_PERFORMED`
- `P12_1C_GIT_COMMIT=NOT_PERFORMED`
- `P12_1C_GIT_PUSH=NOT_PERFORMED`
- `P12_1C_EXACT_ROUTER_REQUEST_OWNER_V1=PASS`

## Next

P12-1D should trace the exact first vertical lifecycle through the renderer/main bridge for `thread/start`, `turn/start`, approval, `turn/interrupt`/stop, authoritative progress/completion, and delivery/outcome-unknown semantics. No implementation mutation yet.
