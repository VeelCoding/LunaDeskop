# P12-1 Responsibility Map — CLOSED/PASS

Date: 2026-10-15

## Closure state

```text
P12-1A ASAR responsibility map = PASS
P12-1B main/preload seam = PASS
P12-1C exact router/request owner = PASS
P12-1D renderer vertical lifecycle scan = PASS
P12-1E request delivery/approval state machine = PASS
P12_1_RESPONSIBILITY_MAP=CLOSED_PASS
P12_IMPLEMENTATION_MUTATION=NOT_STARTED
```

## Current exact product route

```text
renderer
-> window.electronBridge / sendMessageFromView
-> preload
-> ipcRenderer.invoke("codex_desktop:message-from-view", ...)
-> main ipcMain handler
-> per-window/context handleMessage(...)
-> message type `mcp-request`
-> getAppServerConnection(hostId).handleClientRequest(...)
-> Codex app-server request stack
```

Reverse projection:

```text
Codex app-server response/event
-> Desktop main routing
-> codex_desktop:message-for-view
-> preload
-> renderer state/UI projection
```

The label `mcp-request` is current product message naming and must not be interpreted as a separate execution authority boundary.

## Responsibility map

### A — presentation / screen state

Keep or minimally adapt when useful:

- renderer/webview conversation presentation
- composer/input surfaces
- panels and local navigation
- approval/request UI
- status/progress display
- local display-state orchestration

### B — adapter / protocol / transport plumbing

Keep or minimally adapt when it remains translation-only:

- renderer-to-preload bridge
- Electron IPC transport
- main request routing
- app-server request/response translation
- response/event projection back to renderer
- process/stdio/websocket transport plumbing

### C — execution / authority decisions

Must delegate to, consume from, or reconcile against Luna authority:

- task/session identity authority
- execution admission
- effect/release truth
- authorization truth
- approval authority
- cancel/interrupt completion truth
- continue/resume decisions
- retry/resend/replay authority
- reconnect/recovery decisions
- outcome-unknown resolution
- authoritative final/result state

## Critical discovered current behavior

Current Desktop bundles co-locate B and C responsibilities. Therefore P12 must not classify or delete by file/bundle name alone.

Current product explicitly distinguishes known not-sent/rejected states from `outcome-unknown` / unconfirmed states for effect-bearing operations. Preserve this law:

```text
NOT_SENT != OUTCOME_UNKNOWN
UNKNOWN != safe replay
```

Current interrupt logic performs local cleanup and may mark local turn state `interrupted` after interrupt request handling. Under P12 this local projection must not mint remote/Luna cancellation truth.

Current approval UI translates user choice to app-server reply methods, while authoritative request resolution arrives through server/app-server state such as `serverRequest/resolved`. Preserve UI/authority separation.

## P12-1 closure criterion

P12-1 required a fresh packaged-product responsibility map and an exact Desktop adapter-seam discovery before implementation mutation.

Those conditions are now met on the locked 2026-10-15 baseline.

No implementation source mutation has been authorized or performed by P12-1.

## Next gate

```text
P12-2 = FIRST VERTICAL CONTRACT / IMPLEMENTATION GATE
```

P12-2 must define the narrow vertical contract before source mutation:

```text
create task
-> request/resolve approval
-> execute in Luna
-> project authoritative progress
-> request cancellation
-> show authoritative final/recovery result
```

The gate must name exactly which current A/B surfaces are preserved/adapted and which C decisions are delegated to Luna before implementation begins.
