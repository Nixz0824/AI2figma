# METRICS — AI2figma v0.4.7 — general generation

Canonical release tree: `v0.4.7` (396 source commits). This inventory counts 532 tracked TypeScript files
and 247,916 LF-delimited physical lines across the 13 workspaces under `packages/`, the `figma-plugin` workspace,
`scripts/`, and `tests/`. It is not a production-only LOC count or a software-quality metric.

Canonical v0.4.7 `npm run verify`: **3,055 tests / 3,054 pass / 1 skip / 0 fail / 452 suites**; exit 0.
Guard, TypeScript build and plugin build passed. Scrubbed-history CI for v0.4.7 passed on both `main` and the tag.

## Code

| Area | Files | Lines |
|---|---:|---:|
| `packages/core` | 17 | 5,497 |
| `packages/protocol` | 51 | 34,863 |
| `packages/design` | 18 | 12,439 |
| `packages/decision` | 7 | 770 |
| `packages/orchestrator` | 63 | 58,068 |
| `packages/tools` | 6 | 1,504 |
| `packages/bridge` | 9 | 3,482 |
| `packages/model` | 14 | 3,601 |
| `packages/memory` | 4 | 1,083 |
| `packages/browser` | 7 | 1,388 |
| `packages/cli` | 4 | 1,453 |
| `packages/mcp-server` | 4 | 928 |
| `packages/bench` | 18 | 5,466 |
| `figma-plugin` | 22 | 4,690 |
| `scripts` | 71 | 23,815 |
| `tests` | 217 | 88,869 |
| **Total** | **532** | **247,916** |

## Verification

- **v0.4.7 canonical full verify:** 3,055 test cases / 3,054 passed / 1 skipped / 0 failed / 452 suites; exit 0.
- **v0.4.7 scrubbed mirror CI:** 3,049 test cases / 3,033 passed / 16 skipped / 0 failed / 452 suites. Tag run `36902346689` and main run `36902337954` both completed successfully.
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

## Known limits (verbatim, not marketing)

- No URL references; local PNG/JPEG/WebP and Figma nodes only
- Assets (Community components, photos, icons) must be supplied by a human
- Chart data series are not drawn — containers and measured gridlines only
- The external blind holdout currently fails; raw results are preserved in the private tree
- Vision scoring is a model judgment with observed ±7.5 noise on identical images
- Activity/Table rows remain fixed at 40px, so wrapped long text can overflow or overlap; the smoke used short fixture text. A long mobile title sat near the right edge, and longer-title wrapping or truncation remains unverified.
