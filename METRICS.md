# METRICS — AI2figma v0.4.10 — generic native content and layout correctness
English | [简体中文](METRICS.zh-CN.md)

## v0.4.10 release (Oct 6 2026)

Canonical v0.4.10 tag points to bfb8b8f2a7da987621d2103a0d69d247b7a9f3dc (414 commits). Compared with v0.4.9, v0.4.10 includes generic demo-provenance disclosure, shared native wrapping, responsive global header actions and the high-severity completion gate. The final tag commit adds only this accepted-sample report to canonical source 4fea12d2511dc3f70a828b9322c84ee6993e8076; the tag runtime-production directories match that already-verified source. The current inventory is 538 tracked TypeScript/TSX files and 251,916 LF-delimited physical lines across packages/, figma-plugin/, scripts/ and tests/. The v0.4.9 release tag remains unchanged.

The generic generation path derives one DEMO DATA page-title suffix from parsed demo-content provenance, preserves source content, wraps long text in allocated tracks, adapts global header actions, and blocks completion while high-severity findings remain. The default mode uses the AI host for reasoning and needs no provider API key; optional provider modes are configured separately.

- **Canonical production-source verification at 4fea12d:** 3,105 tests / 3,104 passed / 1 skipped / 0 failed / 453 suites. Node test duration: 385,593.2573 ms; command duration: 388,356.2393 ms. Receipt SHA-256: 08ec103218bc0e65ca5efe268b14e6fcd3d5845f6ee5f8aec3a51e840cab7417. The release-tag production directories are identical to this verified source.
- **v0.4.10 scrubbed mirror main CI:** mapped HEAD 5e932eee62adc07d821c94b1c1042c2c7c95a1b6; [run 37460767274](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460767274) passed 3,099 tests / 3,083 passed / 16 skipped / 0 failed / 453 suites. Node test duration: 378,394.047746 ms. Log SHA-256: BC7BA27A6FA9BA31C6018578332B42E2757665B188C5FBE64F11E71DCD9103CF.
- **v0.4.10 scrubbed mirror tag CI:** the same mapped HEAD; [run 37460770403](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460770403) passed 3,099 tests / 3,083 passed / 16 skipped / 0 failed / 453 suites. Node test duration: 383,879.596894 ms. Log SHA-256: D8E9050E5ED6B7743752CC1E892D3C5149F5D9A2B1A9BF28A13A6772B6895EF2.
- The canonical v0.4.10 tag maps to scrubbed mirror tag ref 90205406b29f87dcf8c6b725e83c270d7d90667b, peeled to mirror HEAD 5e932eee62adc07d821c94b1c1042c2c7c95a1b6. The pre-release source-maintenance main CI remains historical: [run 37449461427](https://github.com/Nixz0824/AI2figma-source/actions/runs/37449461427).

## Native timing and review results

| Observation | Elapsed | Endpoint | Outcome | Integrity | Receipt SHA-256 |
| --- | ---: | --- | --- | --- | --- |
| A · v0.4.8 | 17m30.088s | Recorded terminal state | Review required after the 15-minute cap; not quality-ready | VALID_MONOTONIC | 1151683F6F08A9DE7476BBC013AB96CA8F706AE6D07C59111F773BA4AF553111 |
| 0248B · candidate 0248 | 12m44.386s | Recorded terminal state | Machine complete, then independent rework required; Host timing span missing | DEGRADED | F5DF30A741C4270584D8E014D141F9BDD74E46021D0FB8F523BD5FC7159BF058 |
| d8B2 · canonical d8 | 16m21.281s | Recorded terminal state | Review required after the 15-minute cap; later visual closure did not rewrite the receipt | VALID_MONOTONIC | 657E3445A050BD4203F712AF51C7D4D8C879D3EF8FD4228558D39A86D2338C11 |
| 4fea · v0.4.10 source | 12m40.816s | Quality-ready after independent review | Host complete; review accepted; one accepted quality-ready timing point | VALID_MONOTONIC | 5E2FE92709D5522D56D7C8096BA94AFE475D42A96F4575EE0C4C8F202B9B9453 |

The first three elapsed times end at their recorded terminal states. A and d8B2 actually ran longer than the 15-minute cap; the table preserves those observations rather than substituting the cap value. The 4fea clock ends only after Host COMPLETE and independent review acceptance. The first three are failed or degraded observations, so there is no accepted old/new pair, speedup percentage, or median.

The accepted session was e2e-lunamax-4fea-native-2026-10-06-01 on clean runtime commit 4fea12d2511dc3f70a828b9322c84ee6993e8076. It started at 2026-10-06T11:27:00.652Z and reached qualityReady at 2026-10-06T11:39:41.470Z: 760,815.878 ms total. Host state was COMPLETE, overall 84.52, with no must-fix item. visual_balance remained a non-blocking should-fix item; an overdesign diagnostic also marked equal visual weight between two sibling sections as MAJOR. An information-density enum choice was rejected before Figma writes, corrected to compact, and counted in the elapsed time. The receipt userAcceptance field is null.

Independent review accepted five checks: required information, budget focus, readability, table alignment, and native editable elements. The contemporaneous v0.4.10 report recorded 91 native nodes and 0 IMAGE nodes, but its readback was depth-limited; see the correction below. The accepted review PNG SHA-256 is 220919c0fed104aafdc2d66e51be7598e39b23a02a33cd756b669610516ac425; the original tree-proof SHA-256 remains a09242a4dd8aa929268595a847ae1c0795b81a5eb34687dd6e8666f91e09ee0b.

<a id="native-readback-correction-oct-7"></a>
## Native readback correction (Oct 7, 2026)

The 91-node figure is the count returned by a depth-limited snapshot, not the complete count in the existing 1440×900 frame 253:1518. A complete Oct 7 readback found 112 unique nodes, 0 image nodes, and no truncation. Three cutoff parents omitted 21 existing descendants: ChartScale (3), ChartCanvas (11), and ChartCategories (7). The probe was read-only; these nodes were not newly written. The accepted visual result, 12:40.816 timing, original review PNG, and historical tree-proof hash above remain unchanged. The full-tree SHA-256 is 188905c49142c730e0c6ea17a891b1437d02c4f32853d8afc03bd618111438d1; the refreshed scale-one capture SHA-256 is bc5fb66ae13cbcf7126f9d51de793ec24775afe574c6ece151399450b388c6c8.

The continuous clock is request-to-qualityReady. The four manually bracketed Host spans total 194,887.494 ms; Root review spans total 226,607.797 ms; runtime active is 4,837.979 ms; Host waiting is 555,796 ms; user wait is 0 ms. Manual Host/Root span union covers 53.9% of the full clock; 46.1% remains unclassified. These clocks have different scopes and are not additive. Host waiting includes reasoning or idle time and is not pure inference. No single cause is assigned to the unclassified remainder.

The Host runtime commit was clean 4fea12d. The loaded plugin manifest came from the original candidate-0248 perf-oct6 deployment; its bundle bytes were verified equivalent to the d8 and 4fea builds. The session plugin.sourceCommit value of 4fea12d is a canonical-equivalence annotation, not evidence that the plugin was rebuilt or reloaded at 4fea12d. Bundle SHA-256: a0afccd2cb438bf280d26d79ad3d06275456f6de1e5f955fd093fdf585feb25e.

## Separate untimed disclosure check

A separate untimed run, host_0muwk42jg1gn1bek, used the original B proposal bytes (SHA-256 581177dd3571030bc7c8a10aa936ec19927f151c784ca9e2647722ead8e596c3) and rendered the title “AI API 用量与费用控制台 · DEMO DATA”. The independent reviewer accepted five checks; the tree had 104 nodes, 0 IMAGE nodes, and no child-count gaps. Host strictComplete was true, while deliverableReady remained false. This is quality evidence for one page and is not a timing sample.

The user fully restarted Codex; Figma and the plugin/Bridge stayed running. Earlier MCP processes had exited, and the only new MCP process, PID 23140, started at 18:45:06 +08:00 from the clean frozen 4fea build. Its generated title matched a fresh local 4fea compile. This process evidence applies to that bounded untimed run.

The acceptance-evidence-with-tree.json SHA-256 is e39ba721462014fbf523b4e90b665009a2eac1a810d97380b6a943c1fc18409b; full-native-tree.json is 9eb4f09ae7eb4a1e3d205d0e9b9f9ec2056abf61f44909305f3f86248c5898dd; greenfield.png is a0472a867fbf94b6c86da7aafe1d6a495764482032c0f022ea87f5fa1c136bae. No screenshot is embedded in the public documentation.

## v0.4.9 release metrics (historical)

Canonical release tree: `v0.4.9` (402 canonical commits). This inventory counts 537 tracked TypeScript files
and 250,786 LF-delimited physical lines across the 13 workspaces under `packages/`, the `figma-plugin` workspace,
`scripts/`, and `tests/`. It is not a production-only LOC count or a software-quality metric.

Canonical v0.4.9 `npm run verify`: **3,085 tests / 3,084 pass / 1 skip / 0 fail / 453 suites**; exit 0.
Guard, TypeScript build and plugin build passed. Scrubbed-history CI for v0.4.9 passed on both `main` and the release tag.

## v0.4.9 file inventory (historical)

| Area | Files | Lines |
|---|---:|---:|
| `packages/core` | 17 | 5,497 |
| `packages/protocol` | 51 | 34,863 |
| `packages/design` | 18 | 12,944 |
| `packages/decision` | 7 | 770 |
| `packages/orchestrator` | 63 | 58,210 |
| `packages/tools` | 6 | 1,504 |
| `packages/bridge` | 9 | 3,482 |
| `packages/model` | 14 | 3,601 |
| `packages/memory` | 4 | 1,083 |
| `packages/browser` | 7 | 1,388 |
| `packages/cli` | 5 | 1,792 |
| `packages/mcp-server` | 5 | 986 |
| `packages/bench` | 18 | 5,466 |
| `figma-plugin` | 22 | 4,777 |
| `scripts` | 71 | 23,815 |
| `tests` | 220 | 90,608 |
| **Total** | **537** | **250,786** |

## Verification

- **v0.4.9 canonical full verify:** 3,085 test cases / 3,084 passed / 1 skipped / 0 failed / 453 suites; exit 0. Oct 5 Node test-runner duration 392,074.7201 ms. Log SHA-256: `345f45d08d21e8e4a52ef11d6a2fa5f27a2b7db21ab31546c0e1359d1547c59c`.
- **v0.4.9 scrubbed mirror CI:** main and release tag each ran 3,079 tests / 3,063 passed / 16 skipped / 0 failed / 453 suites. Main run `37313859741`: Node duration 382,873.79346 ms. Tag run `37313862915`: Node duration 379,846.3941 ms. Both passed on scrubbed HEAD `7e7857df949a526fc93a3c648084b6020920fd36`.
- **v0.4.8 historical canonical full verify:** 3,079 test cases / 3,078 passed / 1 skipped / 0 failed / 452 suites; exit 0. Oct 5 Node test-runner duration 390,027.6074 ms.
- **v0.4.8 historical scrubbed mirror CI:** main and release tag each ran 3,073 tests / 3,057 passed / 16 skipped / 0 failed / 452 suites. Main run `37295332019`: Node duration 373,877.570165 ms, Actions job about 411 s. Tag run `37295336675`: Node duration 374,256.20633 ms, Actions job about 412 s. Both passed.
- Historical v0.4.7 canonical full verify: 3,055 test cases / 3,054 passed / 1 skipped / 0 failed / 452 suites; exit 0.
- Historical v0.4.7 scrubbed mirror CI: 3,049 test cases / 3,033 passed / 16 skipped / 0 failed / 452 suites. Tag run `36902346689` and main run `36902337954` both completed successfully.
- **v0.4.6 historical scrubbed mirror CI:** 3,007 test cases / 2,991 passed / 16 skipped / 0 failed / 452 suites; run `36832313819` completed successfully.
- Scrubbed mirror skips include provider-gated checks and checks whose local source inputs are omitted by history scrub. R6 test 2b preflights its four non-`EXTERNAL` image paths, skips only when an exact path is absent, and retains the byte, pixel, `EXACT_RENDERED` and `checked=4` assertions whenever those images are present.
- **33 dedicated decision-shadow tests**; 4 shadow points; no runtime behavior depends on any answer
- **52** typed Figma protocol methods, **32** MCP tools
- **14** workspaces: 13 under `packages/`, plus `figma-plugin`
- One live mobile ADAPTATION run reached `ADAPTATION_COMPLETE` under its independent acceptance policy with
  `strictComplete=false`; the retained strict fidelity ledger is `NOT_COMPARABLE_TARGET`. This is not a strict
  fidelity PASS.
- CI runs the full suite on every change

## Functional scope

- **115-element** reference construction support matrix (native draw / reuse / transfer / defer)
- **5 platform shells**: desktop sidebar, top navigation, single column, mobile stack, tablet stack
- Region fidelity ledger with deterministic pixel metrics (MAE, changed-pixel ratio, luminance, edge)
- Asset settlement: local component reuse, Community transfer, media placement, outline vector import
- Host workflows: existing design, greenfield, reference reconstruction, reference adaptation
- Typed decision shadow (routing / finding triage / risk gate / correction materiality) with
  per-artifact agreement, confidence, latency and cost evidence; classification report for calibration

## General generation

- Optional typed `visualTokens` carry supported color and typography choices through deterministic token resolution into native construction. The runtime checks exact font faces and applies font size, line height, and letter spacing.
- Native text construction reuses loaded font promises and resolved parents. Eligible Host Reference Stage-A candidates use batched child reads and PNG exports, reducing transport round trips along that probe path.
- Evidence: three compiled-proposal scenes validated native parameters, viewport, relations, and containment. Measured transport improvement is scoped to eligible candidate reads and exports.
- Greenfield pages derive one page-level `DEMO DATA` title suffix from existing parsed demo-content markers on items or chart data. The source product type and content values stay unchanged; the native title uses its existing wrapping track.
- v0.4.9 Host planning: the CLI exposes complete start DTOs, state-guarded continuation, and offline proposal/review/plan validation. MCP initialize plus `tools/list` changed from 41,238 B to 24,585 B (40.4% less default discovery payload). The full reference guide remains available on demand: 20,352 B of text, 20,600 B as a JSON-RPC response. This measures context payload only; it is not a runtime latency or quality result.
- v0.4.8: explicit chart data, bounded table/activity/mobile layouts, and content/style/geometry-aware component reuse with fail-closed evidence checks. Grouped sections preserve native order and header bounds. Delete guards protect rollback stashes and refuse overlapping parent/descendant targets before writes. Two fixed Native fixtures passed scoped tree/text/viewport audits and exact rollback; they do not establish whole-page design quality or successful component reuse.
- Host visual closure: the Oct 2 task reached COMPLETE after post-clock final review and fresh capture on Oct 5. Root accepted the bounded result; no elapsed time was measured on that pass. The original timed receipt remains REVIEW_REQUIRED with degraded timing integrity, so no speedup or normal-latency claim is made.

## Host visual closure and timing

Host task host_0muqsigre0rrehmt reached COMPLETE after a post-clock final review and read-only capture on Oct 5. Root accepted the bounded output. This continued the Oct 2 task after its timed interval; it was not a new generation run. Closure proof: .fdr/tmp/e2e-luna-max-2026-10-05-live/quality-closure-oct5.json, SHA-256 4e54ce6e3af69358aa5e5ae28ecf5148b1ba0812693ab140cf8d0514888bd69a.

The root frame was 1440×900; its exact-byte 1008×630 export SHA-256 is f3516354cdbefaa252ec5a4310fc5c21c37cec3ca9202b0382b845b3b4719d85. Root review confirmed the DEMO DATA label, budget values, seven trend dates and bars, five aligned recent-call rows, viewport fit, and native editable elements. A low-severity chart-axis/grid alignment item remains. Read-only postflight found no active transaction, locks, or mutations. No elapsed time or speedup was measured for this Oct 5 closure.

The Oct 2 timed observer receipt ended REVIEW_REQUIRED at TIME_CAP_15_MIN with timingIntegrity=DEGRADED. Its Host planning spans include dependency-tool misuse and waiting. The original failed receipt remains unchanged and does not measure the Oct 5 post-clock completion.



## Known limits

- No URL references; local PNG/JPEG/WebP and Figma nodes only
- Assets (Community components, photos, icons) must be supplied by a human
- Greenfield charts use explicit labels, units, and finite numeric values. Absent chartData renders the no-data state; malformed and non-finite input fails schema validation. Zero-valued points in a signed domain do not create bars, while valid all-zero series retain zero-baseline markers.
- The external blind holdout currently fails; raw results are preserved in the private tree
- Vision scoring is a model judgment with observed ±7.5 noise on identical images
- Activity and table content wraps within bounded section widths; narrow mobile activity rows stack. Current Native fixtures cover fixed dashboard and signed-boundary cases only. Chart-axis and grid alignment remains a P2 polish item.

## Related documentation

- [English homepage](README.md)
- [中文主页](README.zh-CN.md)
- [Architecture overview (English)](ARCHITECTURE.md)
- [Evaluation license](LICENSE)
