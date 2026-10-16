# P12 Baseline Refresh — 26.1013 Locked Checkpoint

Date: 2026-10-16
Status: CLOSED / PASS

## Current locked package

```text
OpenAI.Codex 26.1013.3656.0 x64
app/resources/app.asar SHA256 = 163A18C84DB57AD5C50222B313DC4D11D45FEBC03EC065B516BA9F0380F2EB3F
ASAR header JSON SHA256 = 2950AEC8BA63FB2B905A208C7DE22F9692D7EF2D66E658162DAFFEBCCD6A509E
ASAR product version = 26.1013.31256
main = .vite/build/early-bootstrap.js
```

Package-critical identities:

```text
AppxManifest.xml = A4696F89A28E40F200893B6EC73E6BFCE955143FB5F265CAFA0D189409E2F4B1
AppxBlockMap.xml = 74C54A88CE5DC8383B7247255FE1BFA5EDF3857850204B8F8F4112AD3125266C
app/ChatGPT.exe = 28D75915964E3BF43F2A4AE568F7C78C51E5955FE36970BDECB6332E64E4C3DE
app/resources/codex-command-runner.exe = 0DE2B882D1F763ECDF4FCC3873FEC18DDCF20646B6291DAC54D33A9F9116D4C4
app/resources/codex.exe = 9ECB9DF2ECAFCC00542EF0966C6F1737A81397DC9531B0A4B178238E2BF4A46D
```

Current source/config fingerprint:

```text
rule = PATH_UTF8_NUL_RAW_BYTES_NUL_SORTED_V3
file count = 237
total bytes = 28526278
SHA256 = 3F60F1459DF150B6F4871762E7D9829E8E4C6DAA64ACC57595CC968C45D74D70
```

## Refresh chain

```text
identity delta V1 = PASS
R1 delta-scoped seam discovery = PASS
R2 semantic seam evidence capture = PASS
R3E interrupt/local-cleanup discriminant = PASS
R3ABC final semantic discriminants = PASS
final source/config identity V3 = PASS
```

## Semantic closure

The update changed exact bundle identities, but the P12 responsibility model and first-vertical design remain valid.

Revalidated:

```text
IPC topology = EVIDENCED
main app-server bridge = EVIDENCED
transport coverage = 4/4
required semantic signal coverage = 11/11
effect-bearing classifier = exact 8-method set preserved
NOT_SENT != OUTCOME_UNKNOWN
UNKNOWN != safe replay
mcp-request-abandon != cancel completion / quiescence
approval projection path remains present
turn/interrupt remains request + local orchestration; local state/cleanup is not authoritative cancellation truth
```

Decision:

```text
P12-0 current baseline = CLOSED/PASS / LOCKED
P12-1 new-build semantic revalidation = CLOSED_PASS
P12-1 responsibility map = REMAINS VALID
P12-2 first vertical design = REMAINS VALID
P12-2 reopen = NOT_REQUIRED
```

## Dependency/implementation state preserved

```text
D1 overall release input = BLOCKED
D1 narrow owner-observation -> authorized read-path binding = ACCEPTED FOR NARROW LOCAL OWNER SCOPE
D1 exact queue-attempt/resource-lease correlation + general I01 acceptance = OPEN
D2 exact-call product bridge = BLOCKED
P12 implementation hold = ACTIVE
P12 implementation authorization = NOT_GRANTED
P12 implementation source mutation = NOT_STARTED
```

## Historical baseline

Prior `OpenAI.Codex 26.1007.9446.0` is historical locked evidence only. It must not be resumed as current product truth.

## Resume rule

```text
DO NOT REOPEN P12-1 OR P12-2 BECAUSE OF THE 26.1013 UPDATE; THE UPDATE WAS REVALIDATED.
REEVALUATE ONLY WHEN D1 OR D2 ACCEPTANCE EVIDENCE CHANGES, OR NEW EXACT PRODUCT EVIDENCE INVALIDATES A PINNED INVARIANT.
WHEN BOTH D1 AND D2 CLEAR, RUN ONE FINAL IMPLEMENTATION-RELEASE REVIEW.
NO IMPLEMENTATION SOURCE MUTATION BEFORE EXPLICIT RELEASE AUTHORIZATION.
```
