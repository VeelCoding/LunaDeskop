# P12-1E Request Delivery / Approval State Machine V2 — PASS

Date: 2026-10-15

## Result

```text
P12_1E_REQUEST_DELIVERY_APPROVAL_STATE_MACHINE_V2=PASS
P12_1E_ASAR_EXTRACTION=NOT_PERFORMED
P12_1E_SOURCE_MUTATION=NOT_PERFORMED
P12_1E_REPOSITORY_MUTATION=NOT_PERFORMED
P12_1E_GIT_ADD=NOT_PERFORMED
P12_1E_GIT_COMMIT=NOT_PERFORMED
P12_1E_GIT_PUSH=NOT_PERFORMED
```

Locked identities remained unchanged:

```text
app/resources/app.asar SHA256 = 356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325
ASAR header JSON SHA256 = FA8C9B0734EA4E4DFEFE176A3375A9ED8E16C0C848D01A8A864D995D0348592D
```

Exact renderer source identities inspected:

```text
webview/assets/app-shared-30671c57ec82.js
SHA256 = 392B023063A3569A2EFC47A019ACCB2D1E72295B1BFEC2CBB81FC37E1515580A

webview/assets/app-initial-102e45562729.js
SHA256 = C59B2A0BE6C13496B30EBDA167925CDCCAB26799CAE350C62D2B37AFE3589B57

webview/assets/app-primary-cd52df2361eb.js
SHA256 = 9602EEA8C6DD07DDFBBC2772EAC271E8EC7F765E1F275FE47EF681B996AC056A
```

## Effect-bearing method fence discovered

Current Desktop request client has an explicit effect-bearing classification including:

```text
thread/start
thread/startAeon
thread/fork
thread/inject_items
thread/queue/add
turn/addUserMessage
turn/start
turn/steer
```

For such methods, request construction may carry `onOutcomeUnknown`, and the renderer bridge sets `retainResponse` when the method is effect-bearing and an outcome-unknown listener exists.

## Delivery-state semantics

The request client explicitly separates delivery/result states.

- `outcome-unknown` is not converted into ordinary failure truth.
- `onDelivery(...)` marks a request outcome unknown, clears the local timeout, releases local request capacity, and invokes the outcome-unknown listener.
- normal `onResult(...)` completes the request and emits a completed lifecycle event.
- normal `onError(...)` rejects the request and emits a failed lifecycle event.
- dispatch exceptions for effect-bearing requests with outcome-unknown handling are converted to delivery stage `outcome-unknown` rather than silently treated as definitely-not-sent.
- renderer turn state preserves unconfirmed submissions when delivery is `outcome-unknown`.

Historical/current renderer logic also distinguishes known not-sent/rejected cases from unconfirmed outcome-unknown cases. Preserve this distinction in P12.

## Approval path

Current renderer/Desktop notification flow projects an approval request to UI actions:

```text
approve -> accept
approve-for-session -> acceptForSession
decline -> decline
```

The UI decision is then translated to the matching app-server reply helper, including:

```text
replyWithCommandExecutionApprovalDecision(...)
replyWithFileChangeApprovalDecision(...)
```

The UI notification is cleared from the authoritative `serverRequest/resolved` notification path. This supports the P12 boundary: Desktop presents and translates the user's choice; authorization/result truth must remain authoritative outside Desktop UI state.

## Interrupt / cancel mapping

Current Desktop helper sends:

```text
turn/interrupt { threadId, turnId }
```

but also performs local state mutation after success / no-active-turn handling, including setting a current turn status to `interrupted`, plus local Node REPL/background terminal/subagent cleanup.

This is important C-class behavior for P12. Local cleanup and local state mutation cannot establish Luna's authoritative cancellation or remote quiescence truth.

## Responsibility conclusion

```text
A = renderer presentation, approval UI, local display/state projection
B = request dispatch, preload/IPC routing, response/event translation, transport plumbing
C = execution admission, effect truth, approval authorization truth, cancel/interrupt completion truth, outcome-unknown/replay/recovery decisions
```

P12 must preserve useful A/B orchestration while delegating or reconciling C against Luna authority.
