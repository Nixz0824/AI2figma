# METRICS — AI2figma v0.4.8 — general generation data and layout

Canonical release tree: `v0.4.8` (401 canonical commits). This inventory counts 533 tracked TypeScript files
and 249,930 LF-delimited physical lines across the 13 workspaces under `packages/`, the `figma-plugin` workspace,
`scripts/`, and `tests/`. It is not a production-only LOC count or a software-quality metric.

Canonical v0.4.8 `npm run verify`: **3,079 tests / 3,078 pass / 1 skip / 0 fail / 452 suites**; exit 0.
Guard, TypeScript build and plugin build passed. Scrubbed-history CI for v0.4.8 passed on both `main` and the release tag.

## Code

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
| `packages/cli` | 4 | 1,453 |
| `packages/mcp-server` | 4 | 928 |
| `packages/bench` | 18 | 5,466 |
| `figma-plugin` | 22 | 4,777 |
| `scripts` | 71 | 23,815 |
| `tests` | 218 | 90,149 |
| **Total** | **533** | **249,930** |

## Verification

- **v0.4.8 canonical full verify:** 3,079 test cases / 3,078 passed / 1 skipped / 0 failed / 452 suites; exit 0. Oct 5 Node test-runner duration 390,027.6074 ms.
- **v0.4.8 scrubbed mirror CI:** main and release tag each ran 3,073 tests / 3,057 passed / 16 skipped / 0 failed / 452 suites. Main run `37295332019`: Node duration 373,877.570165 ms, Actions job about 411 s. Tag run `37295336675`: Node duration 374,256.20633 ms, Actions job about 412 s. Both passed.
- Historical v0.4.7 canonical full verify: 3,055 test cases / 3,054 passed / 1 skipped / 0 failed / 452 suites; exit 0.
- Historical v0.4.7 scrubbed mirror CI: 3,049 test cases / 3,033 passed / 16 skipped / 0 failed / 452 suites. Tag run `36902346689` and main run `36902337954` both completed successfully.
- **v0.4.6 historical scrubbed mirror CI:** 3,007 test cases / 2,991 passed / 16 skipped / 0 failed / 452 suites; run `36832313819` completed successfully.
- Scrubbed mirror skips include provider-gated checks and checks whose local source inputs are omitted by history scrub. R6 test 2b preflights its four non-`EXTERNAL` image paths, skips only when an exact path is absent, and retains the byte, pixel, `EXACT_RENDERED` and `checked=4` assertions whenever those images are present.
- **33 dedicated decision-shadow tests**; 4 shadow points; no runtime behavior depends on any answer
- **52** typed Figma protocol methods, **31** MCP tools
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
