# Luna Desktop P12 Alignment Contract

Date: 2026-10-16
Status: ACTIVE / P12 STARTED / P12-0 BASELINE LOCKED / P12-1 CLOSED/PASS / P12-2 FIRST VERTICAL DESIGN CLOSED / IMPLEMENTATION HOLD ACTIVE

This document is the canonical Git-side starting contract for the Luna Desktop P12 line. It prevents obsolete Desktop assumptions from becoming current truth.

## 1. Canonical Desktop identity

```text
GitHub repository = VeelCoding/LunaDeskop
Canonical local packaged-product evidence tree = C:\Users\istem\Projects\LunaDesktop
Previous Desktop repository = VeelCoding/Luna-Deskop-v0.1 (SUPERSEDED / DO NOT AUTO-RESUME)
```

The local Desktop workspace was refreshed from the 2026-10-14 ChatGPT/Codex Desktop generation. It is a packaged AppX/MSIX-style product tree, not a Git checkout.

P12-0 baseline identity is CLOSED/PASS. Exact lock evidence is in `P12_BASELINE_LOCK.md`.

Primary locked package tuple:

```text
OpenAI.Codex 26.1007.9446.0 x64
AppxManifest SHA256 = 631AA3A829CF29990652808050EE824A5ADE2A20C98C1DE99924670E29AFE838
AppxBlockMap SHA256 = 755F6A8A0B55CFAA33604C7CB0EA1F957C2882790550D7EB333B8687747E37B4
app/ChatGPT.exe SHA256 = EE785AEC9FF3058AFB01069A8B455FB17E46F3C33611A867EFD3DB37DE1F05F3
app/resources/app.asar SHA256 = 356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325
app/resources/codex-command-runner.exe SHA256 = BDF5160289BC4D64BC2FA38C43F9679558B3A4386226ADC66A0AF741E41424B7
source/config tree SHA256 = 51B7E2ACE9D2FBA7B73DFF1BD0A9B99CF8EB42B47C451F38B2215D31233CC3C9
```

`app/resources/default_app/` remains classified as visible Electron default/fallback material, not the product authority/bootstrap owner.

Historical 2026-09-30 Desktop source and D01-D50 archaeology are evidence only, not current source truth.

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

The adapter must not mint independent task, execution, approval, replay/resend, cancellation, or recovery authority.

## 6. P12-1 closed responsibility map

Exact current route:

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

P12-1 closure evidence:

```text
P12_1A_ASAR_MAP_V3 = PASS
P12_1B_MAIN_PRELOAD_SEAM_V2 = PASS
P12_1C_EXACT_ROUTER_REQUEST_OWNER_V1 = PASS
P12_1D_RENDERER_VERTICAL_LIFECYCLE_SCAN_V1 = PASS
P12_1E_REQUEST_DELIVERY_APPROVAL_STATE_MACHINE_V2 = PASS
P12_1_RESPONSIBILITY_MAP = CLOSED_PASS
```

## 7. Critical current semantic findings

Current Desktop explicitly separates known not-sent states from outcome-unknown/unconfirmed states for effect-bearing operations.

```text
NOT_SENT != OUTCOME_UNKNOWN
UNKNOWN != safe replay
```

Current approval UI translates user choice to app-server reply methods; authoritative request resolution is separately observed through server/app-server notifications.

Current interrupt logic sends `turn/interrupt` but also performs local cleanup and local state mutation. Under P12, neither local cleanup nor local state mutation may mint Luna cancellation/final truth.

## 8. First integration slice / P12-2

P12-2 first-vertical design is now CLOSED. Its read-only contract construction chain completed without source mutation.

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

```text
I01 general acceptance = OPEN
owner observation -> authoritative outcome/operations read-path acceptance = NOT_ESTABLISHED
admission default = OFF / explicit opt-in / fail-closed
P12 D1 release input = BLOCKED
```

Required release evidence:

```text
I01 general acceptance = CLOSED_PASS
owner observations explicitly bound to authorized outcome/operations read path
exact origin/scope preserved
BODY_EXITED != completion
BODY_EXITED != global quiescence
BODY_EXITED != replay/resend permission
admission remains explicit opt-in / fail-closed
```

Mere co-existence of BODY_ENTERED/BODY_EXITED records, `observe_outcome`, and Desktop `status` is not sufficient evidence of this binding.

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
P12-0 = CLOSED/PASS — locked packaged baseline identity
P12-1 = CLOSED/PASS — current product responsibility map + exact adapter seam
P12-2 first vertical design = CLOSED
P12-2F release-input contract = PINNED / HOLD_PASS
D1 I01 release input = BLOCKED
D2 exact-call product bridge release input = BLOCKED
implementation hold = ACTIVE
implementation authorization = NOT_GRANTED
implementation source mutation = NOT STARTED
```

Do not generate a new P12 archaeology/gate merely to make progress. Reevaluate only when D1 or D2 acceptance evidence changes. When both dependencies are accepted, perform one explicit final implementation-release review before any source mutation.

## 12. Coordination

- Luna team owns aggregate Luna source history/commit/push for completed D21 MCP and its own I01 line.
- `VeelCoding/LunaDeskop` is the canonical Desktop Git-side contract/history repository.
- `C:\Users\istem\Projects\LunaDesktop` is the locked current packaged-product evidence tree.
- Sol-B12 stores continuity and resume pointers and never outranks exact current source/runtime evidence.
- I01 team reports are supporting dependency evidence for P12; they do not redirect P12 into the I01 roadmap.

## Resume marker

```text
D21 MCP = FULL CLOSED/PASS
Luna Desktop remote = VeelCoding/LunaDeskop
Luna Desktop packaged baseline = C:\Users\istem\Projects\LunaDesktop
package = OpenAI.Codex 26.1007.9446.0 x64
P12-0 = CLOSED/PASS
P12-1 = CLOSED/PASS
P12-2 first vertical design = CLOSED
P12-2F release-input contract = PINNED / HOLD_PASS
D1 I01 release input = BLOCKED
D2 exact-call product bridge release input = BLOCKED
I01 = OPEN / admission default OFF
implementation hold = ACTIVE
implementation authorization = NOT_GRANTED
implementation source mutation = NOT STARTED
NEXT = reevaluate only when D1 or D2 acceptance evidence changes; when both clear, run one final implementation-release review
```
