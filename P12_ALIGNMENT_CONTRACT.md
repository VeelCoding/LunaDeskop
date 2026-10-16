# Luna Desktop P12 Alignment Contract

Date: 2026-10-16
Status: ACTIVE / P12 STARTED / CURRENT BASELINE LOCKED / P12-1 CLOSED/PASS / P12-2 FIRST VERTICAL DESIGN CLOSED / IMPLEMENTATION HOLD ACTIVE

This document is the canonical Git-side starting contract for the Luna Desktop P12 line. It prevents obsolete Desktop assumptions from becoming current truth.

## 1. Canonical Desktop identity

```text
GitHub repository = VeelCoding/LunaDeskop
Canonical local packaged-product evidence tree = C:\Users\istem\Projects\LunaDesktop
Previous Desktop repository = VeelCoding/Luna-Deskop-v0.1 (SUPERSEDED / DO NOT AUTO-RESUME)
```

The local Desktop workspace is a packaged AppX/MSIX-style product tree, not a Git checkout.

Current locked package tuple:

```text
OpenAI.Codex 26.1013.3656.0 x64
AppxManifest SHA256 = A4696F89A28E40F200893B6EC73E6BFCE955143FB5F265CAFA0D189409E2F4B1
AppxBlockMap SHA256 = 74C54A88CE5DC8383B7247255FE1BFA5EDF3857850204B8F8F4112AD3125266C
app/ChatGPT.exe SHA256 = 28D75915964E3BF43F2A4AE568F7C78C51E5955FE36970BDECB6332E64E4C3DE
app/resources/app.asar SHA256 = 163A18C84DB57AD5C50222B313DC4D11D45FEBC03EC065B516BA9F0380F2EB3F
app/resources/codex-command-runner.exe SHA256 = 0DE2B882D1F763ECDF4FCC3873FEC18DDCF20646B6291DAC54D33A9F9116D4C4
app/resources/codex.exe SHA256 = 9ECB9DF2ECAFCC00542EF0966C6F1737A81397DC9531B0A4B178238E2BF4A46D
ASAR header JSON SHA256 = 2950AEC8BA63FB2B905A208C7DE22F9692D7EF2D66E658162DAFFEBCCD6A509E
source/config V3 SHA256 = 3F60F1459DF150B6F4871762E7D9829E8E4C6DAA64ACC57595CC968C45D74D70
```

Current ASAR product identity:

```text
name = openai-codex-electron
version = 26.1013.31256
main = .vite/build/early-bootstrap.js
```

The previous OpenAI.Codex 26.1007.9446.0 package is retained as historical locked evidence only and is superseded as current source truth.

Exact lock evidence is in `P12_BASELINE_LOCK.md`.

`app/resources/default_app/` remains visible Electron default/fallback material, not the product authority/bootstrap owner.

Historical 2026-09-30 Desktop source and D01-D50 archaeology remain reference evidence only.

## 2. Truth order

```text
locked current packaged Desktop source/runtime
> exact current Luna source/runtime and authority contracts
> current P12 contract/team decisions
> current Sol-B12 continuity
> historical D-series / prior Desktop archaeology
> product/system memory
```

## 3. D21 MCP relationship

D21 MCP is fully closed:

```text
P0-P10 = CLOSED/PASS
P11A = CLOSED/PASS
P11B1 = CLOSED/PASS
P11B2 = CLOSED/PASS
P11C = CLOSED/PASS
P11D = CLOSED/PASS
D21_MCP_FINAL_UMBRELLA_V2 = PASS
D21_MCP_FULL_MCP = CLOSED_PASS
D21_MCP_HANDOFF_TO_LUNA_TEAM = READY
```

There is no remaining MCP gate blocking P12. MCP closure does not establish unrelated authority or admission provenance.

## 4. I01 remains separate and open

```text
I01 = OPEN
admission default = OFF
current bindings may remain UNBOUND
MCP closure != I01 provenance
MCP closure != operations authority
```

## 5. Responsibility boundary

Desktop owns presentation and user interaction, including conversation surfaces, editors/inputs, panels, approval screens, progress/status projection, UI flow, and local rendering orchestration. Desktop must not silently become a second execution authority.

Luna owns task/session identity, model/tool execution, authorization, execution budgets, cancellation decision semantics, continue/resume decisions, recovery decisions, and authoritative execution/result state.

The Desktop/Luna adapter translates:

```text
Desktop action -> Luna request
Luna event/state -> Desktop projection
```

The adapter must not mint independent task, execution, approval, replay/resend, cancellation, recovery, or final-result authority.

## 6. P12-1 closed responsibility map

Exact current route remains:

```text
renderer
-> electronBridge / preload
-> codex_desktop:message-from-view
-> main ipcMain
-> per-window/context handleMessage
-> mcp-request message
-> app-server connection/request client
-> Codex app-server
```

Reverse:

```text
Codex app-server response/event
-> Desktop main routing
-> codex_desktop:message-for-view
-> preload
-> renderer projection
```

Final responsibility classes:

```text
A = presentation / screen-state / approval UI / progress projection
B = request dispatch / preload / IPC / request-response translation / transport plumbing
C = execution admission / effect truth / authorization / approval authority / cancel truth / replay-retry-reconnect-recovery / outcome-unknown resolution / authoritative final state
```

A and B may remain or be minimally adapted when they do not duplicate Luna authority. C must delegate to, consume from, or reconcile against Luna authority.

Responsibilities are not files. Current packaged bundles co-locate B and C behavior.

Original P12-1 closure evidence remains valid, and the 26.1013 refresh revalidated the same responsibility model against the new exact package generation.

```text
P12_1A_ASAR_MAP_V3 = PASS
P12_1B_MAIN_PRELOAD_SEAM_V2 = PASS
P12_1C_EXACT_ROUTER_REQUEST_OWNER_V1 = PASS
P12_1D_RENDERER_VERTICAL_LIFECYCLE_SCAN_V1 = PASS
P12_1E_REQUEST_DELIVERY_APPROVAL_STATE_MACHINE_V2 = PASS
P12_1_RESPONSIBILITY_MAP = CLOSED_PASS
P12_NEW_BUILD_SEMANTIC_REVALIDATION = CLOSED_PASS
```

## 7. Current package refresh / semantic revalidation

The package update from 26.1007.9446.0 to 26.1013.3656.0 changed all previously tracked hashed owner bundle identities. New current owners were rediscovered read-only and semantic discriminants were revalidated.

Current high-value owners include:

```text
.vite/build/application-network-startup-DB1VeU3v.js
.vite/build/bootstrap-cdWF4rWM.js
.vite/build/main-C4DYk222.js
.vite/build/preload.js
.vite/build/src-DsLVGakC.js
.vite/build/src-Dtwb7yKT.js
webview/assets/app-initial-df84a35d942d.js
webview/assets/app-primary-2525363b0384.js
webview/assets/app-shared-2f18b1632f37.js
```

Revalidated invariants:

```text
IPC topology = EVIDENCED
main bridge topology = EVIDENCED
transport coverage = 4/4
required semantic signals = 11/11
effect-bearing set = 8/8
NOT_SENT != OUTCOME_UNKNOWN
UNKNOWN != safe replay
mcp-request-abandon != cancellation completion
mcp-request-abandon != remote quiescence
local interrupt cleanup/state mutation != authoritative cancellation/final truth
```

Therefore:

```text
P12-1 new-build revalidation = CLOSED_PASS
P12-2 first-vertical design = REMAINS VALID
P12-2 reopen due to package update = NOT_REQUIRED
```

## 8. First integration slice / P12-2

P12-2 first-vertical design is CLOSED. Its contract construction chain completed without implementation source mutation.

Target lifecycle:

```text
create task
-> request/resolve approval
-> execute in Luna
-> project authoritative progress
-> request cancellation
-> show authoritative final/recovery result
```

P12-2 gate chain:

```text
P12-2A = PASS
P12-2B = PASS
P12-2C = PASS
P12-2D = PASS
P12-2E = HOLD_PASS
P12-2F = HOLD_PASS
```

The design contract is closed, but implementation release is not granted.

### D1 — I01 authority dependency

Current narrow dependency state:

```text
I01 general acceptance = OPEN
owner observation -> authorized outcome/operations read-path binding = ESTABLISHED / ACCEPTED FOR NARROW LOCAL OWNER SCOPE
exact queue-attempt / resource-lease binding = OPEN
admission default = OFF / explicit opt-in / fail-closed
P12 D1 release input = BLOCKED
```

The accepted narrow binding does not establish completion, quiescence, replay permission, resource-release authority, or general I01 closure.

Required remaining release evidence includes:

```text
I01 general acceptance = CLOSED_PASS
narrow owner evidence remains bound to authorized outcome/operations read path
exact origin/scope preserved
specific queue attempt/resource lease correlation accepted where required
BODY_EXITED != completion
BODY_EXITED != global quiescence
BODY_EXITED != replay/resend permission
admission remains explicit opt-in / fail-closed
```

### D2 — exact-call approval product bridge

```text
runtime exact-call approval consumer = PRESENT
runtime exact-call approval tests = PRESENT
product ExactCallApproval.bind producer = 0
product ExactCallApproval constructor producer = 0
product exact_call_approvals injection = 0
product bridge acceptance = ABSENT
P12 D2 release input = BLOCKED
```

Required release evidence:

```text
runtime supplies exact current approval basis
owner-facing exact-call approval request exists
owner response binds one exact task/tool/call/basis
approval enters Luna policy without broadening authority
runtime rechecks fresh basis before effect
stale basis requires reapproval
NOT_SENT and OUTCOME_UNKNOWN remain distinct
exact tests pass
```

Task/session authority approval and runtime exact-call approval remain separate layers.

P12 must not implement duplicate task authority, duplicate running-cancel truth, a replacement I01 DesktopRuntimeSurface, a local final-result authority, or an UNKNOWN replay engine while either dependency remains blocked.

## 9. MCP recovery laws remain pinned

```text
authentication != execution authority
connection != execution authority
retry eligibility != replay authority
reconnect != resend authority
UNKNOWN != safe replay
local timeout/close != remote cancellation/stop truth
process termination != remote quiescence truth
no response != never sent
rediscovery != recovery proof
```

## 10. Plugin independence

Plugin support remains additive/deferred. Core Desktop/Luna connectivity must not require plugin presence unless a later exact contract explicitly changes this.

## 11. Current P12 phase

```text
P12-0 current baseline = CLOSED/PASS — OpenAI.Codex 26.1013.3656.0 locked
P12-1 = CLOSED/PASS — responsibility map + exact adapter seam revalidated against current package
P12-2 first vertical design = CLOSED / REMAINS VALID
P12-2F release-input contract = PINNED / HOLD_PASS
D1 I01 release input = BLOCKED (narrow read-path binding advanced; general release not cleared)
D2 exact-call product bridge release input = BLOCKED
implementation hold = ACTIVE
implementation authorization = NOT_GRANTED
implementation source mutation = NOT STARTED
```

Do not generate a new P12 archaeology/gate merely to make progress. Reevaluate only when D1 or D2 acceptance evidence changes. When both dependencies are accepted, perform one explicit final implementation-release review before any source mutation.

## 12. Coordination

- Luna team owns aggregate Luna source history/commit/push for its I01 line.
- `VeelCoding/LunaDeskop` is the canonical Desktop Git-side contract/history repository.
- `C:\Users\istem\Projects\LunaDesktop` is the locked current packaged-product evidence tree.
- Sol-B12 stores continuity and resume pointers and never outranks exact current source/runtime evidence.
- I01 team reports are supporting dependency evidence for P12; they do not redirect P12 into the I01 roadmap.

## Resume marker

```text
D21 MCP = FULL CLOSED/PASS
Luna Desktop remote = VeelCoding/LunaDeskop
Luna Desktop packaged baseline = C:\Users\istem\Projects\LunaDesktop
package = OpenAI.Codex 26.1013.3656.0 x64
app.asar = 163A18C84DB57AD5C50222B313DC4D11D45FEBC03EC065B516BA9F0380F2EB3F
ASAR header JSON = 2950AEC8BA63FB2B905A208C7DE22F9692D7EF2D66E658162DAFFEBCCD6A509E
P12-0 = CLOSED/PASS / CURRENT BASELINE LOCKED
P12-1 = CLOSED/PASS / CURRENT BUILD REVALIDATED
P12-2 first vertical design = CLOSED / REMAINS VALID
P12-2F release-input contract = PINNED / HOLD_PASS
D1 I01 release input = BLOCKED; narrow authorized read-path binding accepted, remaining release evidence open
D2 exact-call product bridge release input = BLOCKED
I01 = OPEN / admission default OFF
implementation hold = ACTIVE
implementation authorization = NOT_GRANTED
implementation source mutation = NOT STARTED
NEXT = reevaluate only when D1 or D2 acceptance evidence changes; when both clear, run one final implementation-release review
```
