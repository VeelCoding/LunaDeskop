# Luna Desktop P12-1B Main/Preload Seam V2

Date: 2026-10-15
Status: PASS / READ-ONLY ARCHAEOLOGY

## Locked inputs

```text
app.asar SHA256 = 356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325
ASAR header JSON SHA256 = FA8C9B0734EA4E4DFEFE176A3375A9ED8E16C0C848D01A8A864D995D0348592D
loaded direct .vite/build JS files = 34
```

No ASAR extraction or source/repository mutation was performed.

## Exact renderer/preload IPC seam

Current preload exposes `electronBridge` through Electron `contextBridge`.

Primary renderer -> main channel:

```text
codex_desktop:message-from-view
renderer -> electronBridge.sendMessageFromView(...) -> ipcRenderer.invoke(...)
```

Primary main -> renderer channel:

```text
codex_desktop:message-for-view
main/preload -> ipcRenderer event -> window MessageEvent projection
```

This is a strong P12 category-B adapter/plumbing seam candidate. It is not itself evidence of execution authority.

## Main-side routing evidence

`main-Bgi5Xaw-.js` contains the main Electron IPC handlers and routes trusted view messages into per-window/context handlers. It also contains the Codex app-server request client and lifecycle plumbing.

Observed request methods include:

```text
thread/start
thread/startAeon
thread/fork
thread/resume
turn/start
turn/steer
turn/interrupt
```

The request client has explicit request-lifecycle tracking including:

```text
requestLifecycleListeners
onOutcomeUnknown
outcome-unknown
handleHostRequest(...)
timeout -> l.abandon()
failed lifecycle event
```

Important interpretation: a local timeout/abandon path is represented separately from proof of remote non-execution. This is compatible with the pinned D21 law that UNKNOWN is not safe replay authority.

## Codex process / transport evidence

`application-network-startup-YSC7OAs0.js` is a high-value current transport/runtime owner candidate. It contains:

```text
codex.exe runtime discovery
codex-command-runner.exe inventory
stdio transport launch
websocket transport
app-server parsing / version negotiation
process spawn / execFile plumbing
supportsReconnect() differentiation
```

Observed local stdio transport logs `stdio_transport_spawned` and resolves the packaged Codex runtime on Windows.

This module therefore contains substantial category-B transport/bootstrap behavior. Any retry/reconnect/recovery decision inside it must be classified separately before reuse.

## Approval evidence

`main-Bgi5Xaw-.js` contains approval-related processing, including `app-approval-resolved` and Computer Use approval bridge behavior. Presence alone does not establish which layer should own approval authority under P12; exact request/response flow must be mapped before rewiring.

## Conversation state evidence

`conversation-turn-mutations-szl89rld.js` contains projection/state mutation logic including handling interrupted command execution item IDs and conversation pagination reconnect state. This is primarily an A-class presentation/state-projection candidate unless deeper evidence shows authority decisions.

## Preliminary A/B/C classification

```text
A candidate:
  webview/*
  conversation-turn-mutations-szl89rld.js

B candidate:
  preload.js renderer/main bridge
  main-side IPC router
  application-network-startup transport/runtime bootstrap

C candidate requiring exact follow-up:
  app-server request client around sendRequest / handleHostRequest
  outcome-unknown / abandon / retry / reconnect policy
  approval resolution / authorization decisions
  thread/turn interrupt/cancel/resume decisions
```

Do not mechanically delete C-class current Desktop code. P12 requires determining which parts are merely compatibility/transport logic versus independent execution/recovery authority that must delegate to Luna.

## Result

```text
P12_1B_MAIN_PRELOAD_SEAM_V2=PASS
P12_1_RESPONSIBILITY_MAP=IN_PROGRESS
P12 implementation mutation=NOT_STARTED
```

## Next

P12-1C should resolve the exact path:

```text
renderer action
-> preload electronBridge
-> exact main ipcMain handler
-> window/context handleMessage owner
-> app-server client sendRequest/handleHostRequest
-> thread/turn/approval/interrupt lifecycle methods
```

and classify each step A/B/C without filename inference.
