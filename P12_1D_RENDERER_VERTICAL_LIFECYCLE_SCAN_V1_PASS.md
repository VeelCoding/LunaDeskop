# P12-1D Renderer Vertical Lifecycle Scan V1 — PASS

Date: 2026-10-15
Status: PASS / READ-ONLY

## Locked baseline

- app.asar SHA256: `356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325`
- ASAR header JSON SHA256: `FA8C9B0734EA4E4DFEFE176A3375A9ED8E16C0C848D01A8A864D995D0348592D`

## Scan scope

- webview files: 20,119
- eligible renderer files scanned: 14,785
- hit records: 189
- hit files: 112
- extraction: NOT PERFORMED
- source/repository/Git mutation: NOT PERFORMED

## Exact high-value renderer owners

The cross-signal scan identified three core bundles:

- `webview/assets/app-shared-30671c57ec82.js`: bridge + thread/start + turn/start + turn/interrupt + approval + completion
- `webview/assets/app-initial-102e45562729.js`: bridge + thread/start + turn/start + approval + completion
- `webview/assets/app-primary-cd52df2361eb.js`: bridge + thread/start + turn/start

`app-shared` is the strongest current vertical lifecycle owner candidate.

## Delivery-state semantics

Renderer code preserves a material distinction between delivery states.

`startTurnWithOutcome(...)` maps:

- accepted request -> `accepted`
- explicit not-sent delivery -> `rejected`
- other uncertain failures -> `unconfirmed`

Composer/error handling separately tests `delivery.stage === "not-sent"` and `delivery.stage === "outcome-unknown"`.

Queued-message state also records `outcome-unknown` separately from queued/not-sent state.

This reinforces the P12/D21 law:

`NOT_SENT != OUTCOME_UNKNOWN`

and:

`OUTCOME_UNKNOWN != safe replay`

## Renderer request bridge

`app-shared` contains a renderer request scheduler/client that dispatches:

`mcp-request` with `hostId`, request id/method/params, priority/source, timeout/expiresAt, saved environment config, thread access, optional environment draft replacement, and `retainResponse` for effect-bearing methods when an outcome-unknown callback exists.

Effect-bearing set observed in renderer includes at least:

- `thread/start`
- `thread/startAeon`
- `thread/fork`
- `thread/inject_items`
- `thread/queue/add`
- `turn/addUserMessage`
- `turn/start`
- `turn/steer`

## Interrupt path

`app-shared` contains `interruptConversation` / descendant cleanup logic and sends exact app-server method:

`turn/interrupt { threadId, turnId }`

It also contains local/background cleanup orchestration around that request. Local cleanup must not be promoted to authoritative remote cancellation truth.

## Approval / elicitation projection

Renderer state recognizes server requests including:

- `item/commandExecution/requestApproval`
- `item/fileChange/requestApproval`
- `item/permissions/requestApproval`
- `mcpServer/elicitation/request`

Approval UI and notification handling exist in renderer. `app-approval-resolved` observed in renderer is presentation/telemetry evidence, not proof that renderer owns authorization authority.

## Responsibility interpretation

Provisional exact classification after P12-1D:

### A — presentation/state projection

- approval cards/panels
- thread/turn/item rendering
- delivery-state presentation
- notification projection

### B — adapter/plumbing

- renderer `mcp-request` dispatch
- response/delivery routing
- preload/Electron IPC bridge
- main request forwarding

### C — must delegate to Luna authority

- execution admission
- effect-bearing delivery truth
- `outcome-unknown` recovery/replay decisions
- approval authorization decision
- cancel/interrupt completion truth
- retry/reconnect/recovery decisions

No implementation mutation is authorized by this checkpoint.

## Next

P12-1E: resolve the exact renderer request-client state machine and approval reply path, especially delivery transitions (`not-sent`, `outcome-unknown`, accepted/result), retainResponse/onOutcomeUnknown behavior, and interrupt/approval result propagation. Then close P12-1 responsibility map if evidence is sufficient.