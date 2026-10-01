# METRICS — AI2figma v0.4.5-reference-reliability

Canonical release tree: `v0.4.5-reference-reliability` (393 source commits). The inventory below counts tracked
TypeScript files and LF-delimited physical lines across the 13 workspaces under `packages/`, the `figma-plugin`
workspace, `scripts/`, and `tests/`. It is not a production-only LOC count or a software-quality metric.

Final verification: **3,013 tests / 3,012 pass / 1 skip / 0 fail / 452 suites**. `npm run verify` exited 0;
guard, TypeScript build and plugin build passed.

## Code

| Area | Files | Lines |
|---|---:|---:|
| `packages/core` | 17 | 5,497 |
| `packages/protocol` | 51 | 34,863 |
| `packages/design` | 18 | 12,344 |
| `packages/decision` | 7 | 770 |
| `packages/orchestrator` | 63 | 57,365 |
| `packages/tools` | 6 | 1,502 |
| `packages/bridge` | 9 | 3,474 |
| `packages/model` | 14 | 3,601 |
| `packages/memory` | 4 | 1,083 |
| `packages/browser` | 7 | 1,388 |
| `packages/cli` | 4 | 1,453 |
| `packages/mcp-server` | 4 | 928 |
| `packages/bench` | 18 | 5,466 |
| `figma-plugin` | 22 | 4,570 |
| `scripts` | 71 | 23,815 |
| `tests` | 216 | 86,569 |
| **Total** | **531** | **244,688** |

## Verification

- **3,013 test cases / 452 suites / 0 failures** — final `npm run verify`; one provider-gated test skipped
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

## Known limits (verbatim, not marketing)

- No URL references; local PNG/JPEG/WebP and Figma nodes only
- Assets (Community components, photos, icons) must be supplied by a human
- Chart data series are not drawn — containers and measured gridlines only
- The external blind holdout currently fails; raw results are preserved in the private tree
- Vision scoring is a model judgment with observed ±7.5 noise on identical images
