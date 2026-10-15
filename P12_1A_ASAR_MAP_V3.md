# Luna Desktop P12-1A ASAR Map V3

Date: 2026-10-15
Status: PASS / READ-ONLY ARCHAEOLOGY

## Locked baseline anchor

```text
app/resources/app.asar
SHA256 = 356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325
P12_0_BASELINE_LOCK=PASS
```

## ASAR header identity

```text
header size = 5829680
header payload size = 5829676
header JSON bytes = 5829669
header JSON SHA256 = FA8C9B0734EA4E4DFEFE176A3375A9ED8E16C0C848D01A8A864D995D0348592D
data base offset = 5829688
```

## Archive map

```text
entry count = 21311
file count = 20988
directory count = 323
link count = 0
unpacked file count = 8
```

Root:

```text
.vite/
native-menu-locales/
node_modules/
package.json
webview/
```

Top-level distribution:

```text
webview = 20278 entries
node_modules = 931 entries
native-menu-locales = 65 entries
.vite = 36 entries
package.json = 1 entry
```

## Product package identity

Root `package.json` inside the locked ASAR is present:

```text
SHA256 = 03285612942752337EBF828039E408DD1F1DC79697C043A4088ACA6D59A54E26
name = openai-codex-electron
productName = Codex
version = 26.1007.71326
main = .vite/build/early-bootstrap.js
```

Declared main resolution is exact:

```text
path = .vite/build/early-bootstrap.js
size = 3304
unpacked = false
```

This supersedes any temptation to treat `app/resources/default_app/main.js` as the product bootstrap owner. The current packaged product owner begins from the ASAR root package and `.vite/build/early-bootstrap.js`.

## High-value current product surfaces

Exact current ASAR entries observed under `.vite/build` include:

```text
.vite/build/early-bootstrap.js                    3304 bytes
.vite/build/bootstrap-iULMfRBf.js               461537 bytes
.vite/build/main-Bgi5Xaw-.js                   3827962 bytes
.vite/build/preload.js                            6909 bytes
.vite/build/browser-page-preload.js             527604 bytes
.vite/build/sandbox-preload.js                     2102 bytes
.vite/build/conversation-turn-mutations-szl89rld.js 52799 bytes
```

The archive also contains a very large `webview/` presentation/product surface. The first responsibility-map pass must keep `.vite/build` Desktop main/preload/runtime behavior separate from `webview` presentation/state code.

## Classification implications

Current evidence supports the following provisional map, subject to source inspection in P12-1B:

```text
.vite/build/early-bootstrap.js = bootstrap owner candidate
.vite/build/bootstrap-*.js = main bootstrap/runtime orchestration candidate
.vite/build/main-*.js = major Electron main-process/runtime candidate
.vite/build/preload.js = primary renderer bridge candidate
.vite/build/browser-page-preload.js = browser/webview bridge candidate
.vite/build/sandbox-preload.js = sandbox bridge candidate
webview/ = dominant presentation/UI/state surface
```

These are responsibility candidates, not authority assignments. No component is classified A/B/C merely from its filename.

## Noise rule learned from V3

The broad filename regex returned 1390 candidates and became dominated by `node_modules` package/test files. P12-1B must exclude `node_modules` and focus on exact `.vite/build` owners plus narrowly selected `webview` seams.

## Mutation status

```text
ASAR extraction = NOT PERFORMED
source mutation = NOT PERFORMED
repository mutation = NOT PERFORMED
git add = NOT PERFORMED
git commit = NOT PERFORMED
git push = NOT PERFORMED
```

## Result

```text
P12_1A_ASAR_MAP_PREFLIGHT_V3=PASS
P12_1_RESPONSIBILITY_MAP=IN_PROGRESS
implementation mutation = NOT STARTED
```

## Next

P12-1B must inspect exact current `.vite/build` source content read-only and answer:

1. what `early-bootstrap.js` imports/starts;
2. which main-process module creates windows/webviews and launches/communicates with Codex runtime;
3. which preload surfaces are pure bridge/projection versus authority-bearing control;
4. where approval/cancel/task/session/execution decisions occur;
5. where the narrow Desktop -> Luna request and Luna event/state -> Desktop projection adapter seam can be inserted with minimal change.
