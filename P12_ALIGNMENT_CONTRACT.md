# Luna Desktop P12 Alignment Contract

Date: 2026-10-15
Status: ACTIVE / P12 STARTED / P12-0 BASELINE IDENTITY ACTIVE

This document is the canonical Git-side starting contract for the Luna Desktop P12 line. It exists to prevent future chats, contributors, or recovered contexts from silently resuming obsolete Desktop assumptions.

## 1. Canonical Desktop identity

```text
GitHub repository = VeelCoding/LunaDeskop
Canonical local workspace = C:\Users\istem\Projects\LunaDesktop
Previous Desktop repository = VeelCoding/Luna-Deskop-v0.1 (SUPERSEDED / DO NOT AUTO-RESUME)
```

The local Desktop workspace has been refreshed from the 2026-10-14 ChatGPT/Codex Desktop generation. P12 has now started with a read-only baseline identity phase. Before any P12 implementation claim, establish exact current source/tree/runtime identity from that refreshed workspace.

Historical 2026-09-30 Desktop source and archaeology are evidence only, not current source truth.

## 2. D-series / archaeology rule

D01-D50 and the archaeology that preceded the D-series remain valuable historical evidence.

They are not P12 implementation gates and must not be replayed mechanically onto the refreshed Desktop source.

Use them only as comparison/reference material:

```text
current 2026-10-14 Desktop source/runtime
> exact current Luna/Luna Desktop contracts
> current P12 alignment contract
> historical D-series findings
```

If old archaeology conflicts with current source/runtime, current source/runtime wins.

## 3. P12 relationship to D21 MCP

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

There is no remaining MCP gate blocking P12.

However, MCP closure does not establish unrelated authority or admission provenance.

## 4. I01 remains separate and open

```text
I01 = OPEN
admission default = OFF
current bindings may remain UNBOUND
MCP closure != I01 provenance
MCP closure != operations authority
```

P12 must not infer I01 closure from MCP completion.

## 5. Responsibility boundary

### Desktop owns presentation and user interaction

Desktop may own or retain:

- conversation view
- editor/input surfaces
- panels
- approval screens
- status/progress presentation
- user interaction flow
- local UI state and rendering orchestration

Desktop must not silently become a second execution authority.

### Luna owns execution truth and authority

Luna owns:

- task identity
- session identity
- model/tool execution
- authorization decisions
- execution budgets
- cancellation decision semantics
- continue/resume decisions
- recovery decisions
- authoritative execution/result state

### Adapter is thin and authority-free

The Desktop/Luna adapter translates:

```text
Desktop action -> Luna request
Luna event/state -> Desktop projection
```

The adapter must not mint independent:

- task authority
- execution authority
- approval authority
- replay/resend authority
- cancellation truth
- recovery truth

## 6. Preserve before removing

Do not remove a current ChatGPT/Codex Desktop component merely because it lives under a harness, runtime, or orchestration layer.

Before changing or removing a component, classify its actual responsibility:

```text
A. presentation / screen-state orchestration
B. protocol / transport / adapter plumbing
C. execution / retry / recovery / authority decision
```

A and B may remain or be minimally adapted when they do not duplicate Luna authority.

C must be delegated to, consumed from, or reconciled against Luna authority.

The goal is minimal necessary change, not broad mechanical replacement.

## 7. First integration slice

The first P12 integration should prove one narrow vertical lifecycle before broad surface migration:

```text
create task
-> request/resolve approval
-> execute in Luna
-> project authoritative progress
-> request cancellation
-> show authoritative final/recovery result
```

The slice should prove the Desktop/Luna seam rather than merely individual components.

After this vertical path is sound, additional Desktop surfaces can move through the same adapter/event model.

## 8. MCP recovery laws remain pinned

P12 must preserve the completed D21 MCP authority laws:

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

In particular:

- UNKNOWN must never be converted into automatic rerun/replay permission.
- Local Desktop close/cancel/timeout must not be displayed as proof that the remote operation stopped unless Luna owns evidence for that claim.

## 9. Plugin independence

Plugin support may be integrated later.

Core Desktop/Luna connectivity must not require plugin presence as a mandatory dependency unless a later exact contract explicitly changes this decision.

Keep plugin capability additive rather than foundational so plugin work can be added without reopening the core Desktop authority seam.

## 10. P12 current phase

P12 is now STARTED.

Current phase:

```text
P12-0 = fresh Desktop baseline identity lock
mode = read-only / no implementation mutation
```

P12-0 must:

1. establish exact current Git/worktree identity for `C:\Users\istem\Projects\LunaDesktop`;
2. fingerprint the refreshed source tree without mutating it;
3. identify package/runtime entrypoints and current source topology from exact source;
4. record which current files are product source versus generated/vendor/build material;
5. preserve the responsibility boundary in this contract;
6. avoid historical D-series assumptions until current source evidence is collected.

After P12-0 is locked:

1. map current source responsibilities before removal or rewiring;
2. identify the exact Desktop/Luna adapter seam;
3. define the first narrow vertical implementation gate;
4. only then begin implementation mutation.

No historical Desktop baseline may be treated as current truth without revalidation.

## 11. Truth hierarchy

```text
exact current refreshed Desktop source/runtime
> exact current Luna source/runtime and authority contracts
> exact current P12 contract / team decisions
> current Sol-B12 continuity
> historical D-series / prior Desktop archaeology
> product/system memory
```

## 12. Coordination

- Luna team owns Luna aggregate source history/commit/push for the completed D21 MCP line.
- `VeelCoding/LunaDeskop` is the canonical Desktop Git repository.
- `C:\Users\istem\Projects\LunaDesktop` is the canonical local Desktop workspace.
- Sol-B12 stores continuity and resume pointers; it does not outrank exact current source.
- P12 is started, but implementation mutation is not authorized until P12-0 baseline identity and responsibility mapping are complete.

## Resume marker

```text
D21 MCP = FULL CLOSED/PASS
Luna Desktop remote = VeelCoding/LunaDeskop
Luna Desktop local = C:\Users\istem\Projects\LunaDesktop
Desktop baseline = refreshed from 2026-10-14 ChatGPT/Codex Desktop
historical 2026-09-30 archaeology = reference only
I01 = OPEN / admission default OFF
P12 = STARTED
P12-0 = BASELINE IDENTITY ACTIVE
implementation mutation = NOT STARTED
NEXT = exact refreshed source identity -> responsibility map -> adapter seam -> first vertical implementation gate
```
