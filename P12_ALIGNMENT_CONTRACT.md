# Luna Desktop P12 Alignment Contract

Date: 2026-10-15
Status: ACTIVE / P12 STARTED / P12-0 BASELINE LOCKED / P12-1 CLOSED/PASS / P12-2 FIRST VERTICAL CONTRACT ACTIVE

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

P12-2 is the first vertical contract and implementation gate. It is read-only contract construction first.

Target lifecycle:

```text
create task
-> request/resolve approval
-> execute in Luna
-> project authoritative progress
-> request cancellation
-> show authoritative final/recovery result
```

Before implementation mutation, P12-2 must name for every step:

1. Desktop A surface preserved;
2. B adapter request/event mapping;
3. Luna C authority owner;
4. not-sent / unknown / failure semantics;
5. current Desktop C behavior to delegate/remove/reconcile;
6. validation evidence required before advancing.

Only after that contract is pinned may the first vertical implementation gate authorize source mutation.

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
P12-2 = ACTIVE — first vertical contract / implementation gate
implementation source mutation = NOT STARTED
```

## 12. Coordination

- Luna team owns aggregate Luna source history/commit/push for completed D21 MCP.
- `VeelCoding/LunaDeskop` is the canonical Desktop Git-side contract/history repository.
- `C:\Users\istem\Projects\LunaDesktop` is the locked current packaged-product evidence tree.
- Sol-B12 stores continuity and resume pointers and never outranks exact current source/runtime evidence.

## Resume marker

```text
D21 MCP = FULL CLOSED/PASS
Luna Desktop remote = VeelCoding/LunaDeskop
Luna Desktop packaged baseline = C:\Users\istem\Projects\LunaDesktop
package = OpenAI.Codex 26.1007.9446.0 x64
P12-0 = CLOSED/PASS
P12-1 = CLOSED/PASS
P12-2 = FIRST VERTICAL CONTRACT ACTIVE
historical D01-D50 = reference only
I01 = OPEN / admission default OFF
implementation source mutation = NOT STARTED
NEXT = pin first vertical Desktop/Luna contract -> define mutation gate -> only then implement
```
