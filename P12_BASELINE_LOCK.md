# Luna Desktop P12-0 Baseline Lock

Date: 2026-10-15
Status: CLOSED / PASS

## Result

```text
P12_0_PREFLIGHT_V2=PASS
P12_0B_PACKAGED_IDENTITY_V2=PASS
P12_0_BASELINE_LOCK=PASS
P12 implementation mutation = NOT STARTED
```

## Canonical Desktop evidence tree

```text
Local packaged product tree = C:\Users\istem\Projects\LunaDesktop
Git-side contract/history repo = VeelCoding/LunaDeskop
Local tree type = packaged AppX/MSIX-style product tree, not a Git checkout
Generation basis = refreshed from 2026-10-14 ChatGPT/Codex Desktop
```

The absence of local Git metadata is expected for this packaged baseline and is not a failure.

## Package identity

```text
Name = OpenAI.Codex
Publisher = CN=50BDFD77-8903-4850-9FFE-6E8522F64D5B
Version = 26.1007.9446.0
Architecture = x64
ResourceId = ABSENT
```

Declared applications:

```text
App
  executable = app/ChatGPT.exe
  entrypoint = Windows.FullTrustApplication

CodexCoreCommandRunner
  executable = app/resources/codex-command-runner.exe
  entrypoint = Windows.FullTrustApplication
```

## Exact baseline identities

```text
AppxManifest.xml
bytes  = 8634
SHA256 = 631AA3A829CF29990652808050EE824A5ADE2A20C98C1DE99924670E29AFE838

AppxBlockMap.xml
bytes  = 3332162
SHA256 = 755F6A8A0B55CFAA33604C7CB0EA1F957C2882790550D7EB333B8687747E37B4

app/ChatGPT.exe
bytes  = 4781872
SHA256 = EE785AEC9FF3058AFB01069A8B455FB17E46F3C33611A867EFD3DB37DE1F05F3

app/resources/app.asar
bytes  = 567412548
SHA256 = 356C13DC715816436FA1CF31E9F77863F62EA7B7CACC465B397313246EB29325

app/resources/codex-command-runner.exe
bytes  = 8204592
SHA256 = BDF5160289BC4D64BC2FA38C43F9679558B3A4386226ADC66A0AF741E41424B7

app/resources/codex.exe
bytes  = 334121776
SHA256 = E98C516F1C8935789AABE9122EE7E05EC4C3EFD1BA6ACF179242E031C495B99E
```

Additional source/config fingerprint from P12-0 preflight:

```text
rule = SOURCE_CONFIG_TEXT_EXCLUDING_GENERATED_VENDOR_BUILD_DIRS_V2
file count = 233
total bytes = 28134062
SHA256 = 51B7E2ACE9D2FBA7B73DFF1BD0A9B99CF8EB42B47C451F38B2215D31233CC3C9
```

## default_app classification

`app/resources/default_app/` is present and contains Electron default/fallback bootstrap material:

```text
package name = electron
productName = Electron
type = module
main = main.js
```

It is not promoted to the product authority/bootstrap owner merely because its files are directly visible. The packaged product payload is anchored by `app/resources/app.asar` plus the manifest-declared executables. Responsibility mapping must inspect that current payload before assigning owners.

## No mutation

Both P12-0 probes were read-only:

```text
source mutation = NOT PERFORMED
repository mutation = NOT PERFORMED
git add = NOT PERFORMED
git commit = NOT PERFORMED
git push = NOT PERFORMED
```

## Next phase

P12-0 is closed. P12-1 is now the active phase:

```text
P12-1 = current packaged-product responsibility map + exact Desktop/Luna adapter-seam discovery
mode = read-only archaeology first
implementation mutation = NOT STARTED
```

P12-1 must classify current product components by responsibility before removal or rewiring:

```text
A = presentation / screen-state orchestration
B = protocol / transport / adapter plumbing
C = execution / retry / recovery / authority decision
```

Historical D01-D50 findings remain reference-only until revalidated against this locked baseline.
