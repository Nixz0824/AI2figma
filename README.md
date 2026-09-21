# AI2figma — AI Designer Agent

> Point an AI agent at Figma and let it **read, modify and rebuild native design files** —
> with typed operations, transactions, locks, rollback and recorded evidence.

**Status:** Skeleton `v0.4.2-band-fills` · **Source:** private — this repository is the public showcase and distribution channel

---

## What it is

AI2figma is a local runtime that connects an AI agent host (Codex, DSH, Claude, Cursor, …)
to **Figma Desktop**. The host owns the reasoning; the runtime owns the deterministic half:
schema-validated Figma operations, transactions, locks, rollback, idempotent replay,
screenshot capture, region fidelity and evidence artifacts.

Three workflows are implemented end to end:

| Workflow | What it does |
|---|---|
| **Existing** | Inspect a page → scoped plan → one transaction → before/after capture → automatic rollback on regression |
| **Greenfield** | Brief → deterministic tokens/blueprint → native page (desktop / mobile / tablet / landing shells) |
| **Reference** | Local PNG/JPEG/WebP → deterministic pixel measurement → host-authored decomposition manifest → verified native construction → asset settlement → region fidelity ledger → scoped correction |

Everything produced is **native and editable** — frames, auto layout, text, components, instances —
not a screenshot placed on a canvas.

## By the numbers

| Metric | Value |
|---|---|
| TypeScript source | **~202,000 lines** across 478 source files |
| Automated tests | **2,772 test cases**, 0 failures (`v0.4.2-band-fills`) |
| Workspace packages | **13** |
| Typed Figma protocol methods | **51** (zod-validated at every boundary) |
| MCP tools exposed to agent hosts | **31** |
| Commits | **310** |
| Real-Figma commissioning records | **8** (run IDs, transaction IDs, hashes, rollback probes) |
| Decision shadow points | **4** (routing / finding triage / risk gate / correction materiality) |

Full breakdown: [METRICS.md](METRICS.md) · Architecture: [ARCHITECTURE.md](ARCHITECTURE.md)

## Architecture

```
Agent Host (owns reasoning: Codex / DSH / Claude / Cursor)
        │  MCP (stdio)
        ▼
MCP server ── typed zod protocol (51 methods) ──► local bridge (127.0.0.1)
        │                                             │  WebSocket
        │                                             ▼
        │                                    Figma plugin (real Plugin API)
        │                                             │
        ▼                                             ▼
   evidence artifacts ◄─────────────────────────  Figma document
```

## Engineering highlights

- **Write safety first** — every write is schema-validated before dispatch; writes are never retried
  automatically; transactions keep a shadow snapshot; locks live in node `pluginData`; terminal states
  are backed by write-once artifacts with hashes.
- **Evidence over optimism** — independent integrity checks recompute coverage, warnings and operation
  ownership from the raw ledger; a failing gate stops the run and asks a human instead of claiming success.
- **Reference reconstruction** — a 115-element support matrix, deterministic measurement, host-authored
  manifests, asset settlement (Community transfer / media / vectors) and a region fidelity ledger with
  pixel metrics.
- **Honest limits, documented** — no URL references; assets are supplied manually; chart data series are
  not drawn; reconstruction is structural (native, editable), not pixel-identical across renderers.
- **Three-page demo closure (`v0.3.0-demo`)** — Analytics, Settings and Pokecut as native Figma pages;
  fake icons are refused; missing media/vectors stay on a typed work order; a measured same-PNG
  decomposition can be rebound onto a new run.
- **Measured skeleton (`v0.4.1-host-crops`)** — a new PNG does not need a page generator: measurement
  grows a shell, empty vertical gutters split columns, the host fills only leaf bands, and Auto Layout
  owns in-flow geometry (ink calibration is evidence, not a write). `figma_design_start` returns
  `leafFillBands` with a 1:1 crop of each leaf — no OCR. `figma_design_continue` accepts
  `reference_band_fills` against that skeleton (same path as the CLI `fill` command).
- **A typed decision layer, shadow-calibrated** — `@fdr/decision` sends typed choice / yes-no / score
  questions to a System One model (TypeSafe Jev) alongside the deterministic pipeline. Four shadow points
  record agreement, confidence, latency and cost as evidence, and **nothing in the runtime acts on any
  answer**: thresholds will be calibrated from collected data before any point is allowed to act.

## Tech stack

TypeScript · Node ≥ 20 · zod · ws · esbuild · Figma Plugin API · MCP (Model Context Protocol) ·
TypeSafe Jev (System One decisions, shadow-only) · in-house PNG codec and pixel-diff tooling

## Availability

- **Personal, non-commercial evaluation: free.** Builds / evaluation access are provided on request.
- **Commercial use requires written permission.**
- **Source code is private** and not distributed; redistribution and redevelopment are not permitted.

See [LICENSE](LICENSE). For evaluation or commercial licensing, open an issue or send a direct message.

---

## 中文概要

AI2figma 是一个把 AI Agent 连到 Figma 桌面版的本地运行时：宿主负责推理，运行时负责安全的原生施工
（事务 / 锁 / 回滚 / 幂等 / 证据）。三种闭环：改现有页面、从需求建页、从参考图复刻为可编辑原生节点。
**源码私有**；个人非商业评估免费（按需提供构建），商用需书面授权。
规模：约 20 万行 TypeScript、2,563 项测试、12 个包、51 个协议方法、31 个 MCP 工具、8 份真机验收记录。
