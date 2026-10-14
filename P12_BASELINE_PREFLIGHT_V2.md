# P12-0 Fresh Desktop Baseline Preflight V2

Date: 2026-10-15
Status: PASS / BASELINE LOCK PENDING

Canonical local workspace:

```text
C:\Users\istem\Projects\LunaDesktop
```

Declared generation:

```text
2026-10-14_CHATGPT_CODEX_DESKTOP
```

## Observed workspace form

The refreshed local workspace is **not a Git checkout**. It is a packaged AppX/MSIX-style Desktop tree.

```text
P12_0_GIT_REPOSITORY=NO
P12_0_GIT_TOPLEVEL=NONE
P12_0_BRANCH=NONE
P12_0_HEAD=NONE
P12_0_REMOTES=NONE
P12_0_STATUS=NOT_APPLICABLE
P12_0_INDEX=NOT_APPLICABLE
```

This does not fail P12-0. GitHub `VeelCoding/LunaDeskop` remains the canonical Git-side contract/history repository, while `C:\Users\istem\Projects\LunaDesktop` is the exact current packaged-product evidence tree.

## Top-level package evidence

Observed top-level entries include:

```text
app/
AppxBlockMap.xml
AppxManifest.xml
AppxMetadata/
AppxSignature.p7x
assets/
priconfig.xml
resources.language-is.pri
resources.pri
resources.scale-200.pri
```

No root `package.json` is present.

## Source/config fingerprint

Fingerprint rule:

```text
SOURCE_CONFIG_TEXT_EXCLUDING_GENERATED_VENDOR_BUILD_DIRS_V2
```

Observed:

```text
P12_0_SOURCE_FILE_COUNT=233
P12_0_SOURCE_TOTAL_BYTES=28134062
P12_0_SOURCE_TREE_SHA256=51B7E2ACE9D2FBA7B73DFF1BD0A9B99CF8EB42B47C451F38B2215D31233CC3C9
```

Extension counts:

```text
.md   80
.py   68
.json 38
.js   19
.mjs  12
.css   4
.html  4
.yaml  4
.txt   3
.ps1   1
```

## Current bootstrap candidates

```text
app/resources/default_app/index.html
app/resources/default_app/main.js
app/resources/default_app/package.json
app/resources/default_app/preload.js
```

This establishes `app/resources/default_app/` as the first exact packaged application bootstrap seam to inspect. It does **not** yet prove the full runtime owner graph or Desktop/Luna adapter seam.

## Mutation evidence

```text
P12_0_REPOSITORY_MUTATION=NOT_PERFORMED
P12_0_SOURCE_MUTATION=NOT_PERFORMED
P12_0_GIT_ADD=NOT_PERFORMED
P12_0_GIT_COMMIT=NOT_PERFORMED
P12_0_GIT_PUSH=NOT_PERFORMED
P12_0_PREFLIGHT_V2=PASS
```

## Lock status

```text
P12_0_BASELINE_LOCK=NOT_YET_DECLARED
```

Before lock, resolve exact package/runtime identity from the current packaged tree: Appx manifest package/application identity, packaged app version, executable/entrypoint identity, and exact SHA256 identities for the current bootstrap files. Then declare the baseline lock and begin responsibility mapping.
