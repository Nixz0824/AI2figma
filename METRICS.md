# METRICS — AI2figma v0.4.3-skill

Code-size table below is from `v0.2.0-mvp`. Verification counts at `v0.4.3-skill`:
**2,778 tests / 2,777 pass / 1 skip / 0 fail**. Demo canvas: Analytics, Settings, Pokecut.
Skeleton loop: start → leafFillBands + crops → continue `reference_band_fills` → construct.
Host skill is test-locked to that path.

## Code

| Area | Files | Lines |
|---|---:|---:|
| `packages/core` | 17 | 5,497 |
| `packages/protocol` | 42 | 28,457 |
| `packages/design` | 17 | 10,984 |
| `packages/decision` | 7 | 770 |
| `packages/orchestrator` | 56 | 43,005 |
| `packages/tools` | 6 | 1,484 |
| `packages/bridge` | 9 | 3,473 |
| `packages/model` | 14 | 3,599 |
| `packages/memory` | 4 | 1,083 |
| `packages/browser` | 7 | 1,388 |
| `packages/cli` | 4 | 1,453 |
| `packages/mcp-server` | 4 | 871 |
| `packages/bench` | 18 | 5,466 |
| `figma-plugin` | 23 | 4,815 |
| `scripts` | 69 | 21,249 |
| `tests` | 181 | 68,756 |
| **Total** | **478** | **202,350** |

## Verification

- **2,596 test cases / 383 suites / 0 failures** — clean-room verified from a fresh clone
- **33 dedicated decision-shadow tests**; 4 shadow points; no runtime behavior depends on any answer
- **51** typed Figma protocol methods, **31** MCP tools
- **8** real-Figma commissioning records: R3B, R4B, R4C, R4D, HOST_REFERENCE, D032, D083, D085 —
  each with run ID, transaction ID, byte hashes, rollback probes and PNG evidence
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
