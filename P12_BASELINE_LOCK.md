# Luna Desktop P12-0 Baseline Lock

Date: 2026-10-16
Status: CLOSED / PASS / CURRENT BASELINE REFRESHED

## Result

```text
P12_0_BASELINE_LOCK=PASS
P12_BASELINE_REFRESH_IDENTITY_DELTA_V1=PASS
P12_REFRESH_R1_DELTA_SCOPED_SEAM_DISCOVERY_V1=PASS
P12_REFRESH_R2_SEMANTIC_SEAM_EVIDENCE_CAPTURE_V1=PASS
P12_R3E_SELF_CONTAINED_INTERRUPT_DISCRIMINANT_V2=PASS
P12_R3ABC_SELF_CONTAINED_FINAL_DISCRIMINANTS_V2=PASS
P12_REFRESH_FINAL_SOURCE_CONFIG_IDENTITY_V3=PASS
P12_NEW_BUILD_SEMANTIC_REVALIDATION=CLOSED_PASS
P12_2_REOPEN=NOT_REQUIRED
P12 implementation mutation=NOT_STARTED
```

## Canonical Desktop evidence tree

```text
Local packaged product tree = C:\Users\istem\Projects\LunaDesktop
Git-side contract/history repo = VeelCoding/LunaDeskop
Local tree type = packaged AppX/MSIX-style product tree, not a Git checkout
Current package generation = OpenAI.Codex 26.1013.3656.0 x64
```

The absence of local Git metadata is expected for this packaged baseline and is not a failure.

## Current locked package identity

```text
Name = OpenAI.Codex
Publisher = CN=50BDFD77-8903-4850-9FFE-6E8522F64D5B
Version = 26.1013.3656.0
Architecture = x64
```

Declared application entrypoints remain packaged FullTrust executables anchored by `app/ChatGPT.exe` and `app/resources/codex-command-runner.exe`.

## Exact current baseline identities

```text
AppxManifest.xml
bytes  = 8671
SHA256 = A4696F89A28E40F200893B6EC73E6BFCE955143FB5F265CAFA0D189409E2F4B1

AppxBlockMap.xml
bytes  = 3359342
SHA256 = 74C54A88CE5DC8383B7247255FE1BFA5EDF3857850204B8F8F4112AD3125266C

app/ChatGPT.exe
bytes  = 4795184
SHA256 = 28D75915964E3BF43F2A4AE568F7C78C51E5955FE36970BDECB6332E64E4C3DE

app/resources/app.asar
bytes  = 582042823
SHA256 = 163A18C84DB57AD5C50222B313DC4D11D45FEBC03EC065B516BA9F0380F2EB3F

app/resources/codex-command-runner.exe
bytes  = 8217392
SHA256 = 0DE2B882D1F763ECDF4FCC3873FEC18DDCF20646B6291DAC54D33A9F9116D4C4

app/resources/codex.exe
bytes  = 341312816
SHA256 = 9ECB9DF2ECAFCC00542EF0966C6F1737A81397DC9531B0A4B178238E2BF4A46D
```

## ASAR structural identity

```text
ASAR header size = 5852140
ASAR JSON length = 5852130
ASAR header JSON SHA256 = 2950AEC8BA63FB2B905A208C7DE22F9692D7EF2D66E658162DAFFEBCCD6A509E
ASAR data offset = 5852148
ASAR files = 21070
ASAR directories = 323
ASAR unpacked files = 8
```

Root product identity remains:

```text
name = openai-codex-electron
version = 26.1013.31256
main = .vite/build/early-bootstrap.js
```

The stable `main` path does not imply unchanged bundle identities. All prior hashed high-value owner filenames changed in this generation and were rediscovered/revalidated read-only.

## Current high-value owner identities

```text
.vite/build/application-network-startup-DB1VeU3v.js
SHA256 = C338BBDDE151467554D63BEEA59206848CA38A68ABE16B0477D983A172C67578

.vite/build/bootstrap-cdWF4rWM.js
SHA256 = A8FDD0FEEA4448D66037DF9F264AADE773F1405299BBCCF2418544E4B619B41B

.vite/build/main-C4DYk222.js
SHA256 = C8A2AF504B21314FA6A64AD1B4EC83DBAD80033EDE902CAF9978FD9C74A2C175

.vite/build/preload.js
SHA256 = A3E622F8D80A83E58FB3CFCC640FA7E14E6461CCCDAE9EF7D7B0C821DDE256B7

.vite/build/src-DsLVGakC.js
SHA256 = 28A0918F01C50B0EB17676E894998AD7182F119D978ADF0467CCAAC3583F259C

.vite/build/src-Dtwb7yKT.js
SHA256 = A0E4B4B014F04A9391BCFA6A0D6F2B6703590DAACF3591831A62FEC809B2CB76

webview/assets/app-initial-df84a35d942d.js
SHA256 = D7659A96F7D0CFE2249E089EF19675D09D04D6DD9569B550DDAA64722D4F13F3

webview/assets/app-primary-2525363b0384.js
SHA256 = 0013774ADA36C93B41FA11402047E6EB2D6EABF55249237E411A37A8598A6CB1

webview/assets/app-shared-2f18b1632f37.js
SHA256 = C25C71CB02162EDC2F03E8EFCE83708B00C453323CAA5A4212BEE5CBE4CDCF90
```

## Source/config fingerprint

Current deterministic rule:

```text
rule = PATH_UTF8_NUL_RAW_BYTES_NUL_SORTED_V3
file count = 237
total bytes = 28526278
SHA256 = 3F60F1459DF150B6F4871762E7D9829E8E4C6DAA64ACC57595CC968C45D74D70
```

Extension counts:

```text
.css  = 4
.html = 4
.js   = 19
.json = 40
.md   = 81
.mjs  = 12
.ps1  = 1
.py   = 69
.txt  = 3
.yaml = 4
```

The historical 26.1007 source/config fingerprint used a different V2 rule. Preserve it as historical evidence; do not compare its SHA directly with the V3 SHA as though the hashing rules were identical.

## Semantic revalidation result

The package update changed exact bundle identities but did not invalidate the pinned P12 responsibility model or first-vertical design.

Revalidated current behavior includes:

```text
renderer/preload/main IPC topology = EVIDENCED
main app-server bridge topology = EVIDENCED
transport term coverage = 4/4
required semantic signal coverage = 11/11
effect-bearing request set coverage = 8/8
```

The exact effect-bearing classifier remains:

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

Pinned delivery/recovery semantics remain valid:

```text
NOT_SENT != OUTCOME_UNKNOWN
UNKNOWN != safe replay
outcome-unknown may release local request capacity without minting remote outcome truth
mcp-request-abandon abandons request correlation; it is not cancellation completion or quiescence truth
```

Approval projection and `serverRequest/resolved` remain present. `turn/interrupt` remains an app-server request surrounded by local state mutation, fallback, descendant cleanup, and terminal cleanup; those local actions are not Luna authoritative cancellation/final truth.

Therefore:

```text
P12-1 new-build revalidation = CLOSED_PASS
P12-1 responsibility map = REMAINS VALID
P12-2 first vertical design = REMAINS VALID
P12-2 reopen = NOT_REQUIRED
```

## Historical baseline retained

The prior locked package remains historical evidence only:

```text
OpenAI.Codex 26.1007.9446.0 x64
app.asar SHA256 = 356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325
ASAR header JSON SHA256 = FA8C9B0734EA4E4DFEFE176A3375A9ED8E16C0C848D01A8A864D995D0348592D
```

It is superseded as the current P12 packaged-product baseline by 26.1013.3656.0.

## No implementation mutation

All refresh/revalidation probes were read-only:

```text
source mutation = NOT PERFORMED
repository mutation by probes = NOT PERFORMED
implementation authorization = NOT_GRANTED
implementation source mutation = NOT_STARTED
```

Git-side documentation updates that record this checkpoint do not constitute Luna/Desktop implementation source mutation.
