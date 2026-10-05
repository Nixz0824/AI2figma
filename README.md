# AI2figma — AI Designer Agent

> Point an AI agent at Figma and let it **read, modify and rebuild native design files** —
> with typed operations, transactions, locks, rollback and recorded evidence.

**Status:** `v0.4.9` — Host planning context and offline validation · **Source:** private — this repository is the public showcase and distribution channel

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
| Tracked TypeScript inventory | **537 files / 250,786 LF-delimited physical lines**, including `scripts/` and `tests/` |
| Canonical full verification | **3,085 cases: 3,084 passed, 1 skipped, 0 failed** (`npm run verify`; 453 suites; Oct 5) |
| Scrubbed mirror CI | **3,079 cases: 3,063 passed, 16 skipped, 0 failed** (453 suites; main and v0.4.9 tag runs) |
| Workspaces | **14** (13 packages under `packages/` plus `figma-plugin`) |
| Typed Figma protocol methods | **52** (zod-validated at every boundary) |
| MCP tools exposed to agent hosts | **32** |
| Canonical source commits | **402** at `v0.4.9` |
| Decision shadow points | **4** (routing / finding triage / risk gate / correction materiality) |

Full breakdown: [METRICS.md](METRICS.md) · Architecture: [ARCHITECTURE.md](ARCHITECTURE.md)

The v0.4.9 scrubbed mirror's 16 skipped tests include provider-gated checks and checks whose local source inputs are omitted by the
history scrub; the R6 reference check skips only when one of its exact source-bound image paths is absent.

## Architecture

```
Agent Host (owns reasoning: Codex / DSH / Claude / Cursor)
        │  MCP (stdio)
        ▼
MCP server ── typed zod protocol (52 methods) ──► local bridge (127.0.0.1)
        │                                             │  WebSocket
        │                                             ▼
        │                                    Figma plugin (real Plugin API)
        │                                             │
        ▼                                             ▼
   evidence artifacts ◄─────────────────────────  Figma document
```

## Engineering highlights

- **Reference reliability (`v0.4.5-reference-reliability`)** — opt-in `RELATIONAL_V2` planning, plan review
  before calibration/construction, capture- and tree-bound visual review, and narrow read-only recovery for a
  verified packet-pending ADAPTATION checkpoint. `LEGACY_V1` remains the default.
- **Mirror CI fixture handling (`v0.4.6-mirror-ci`)** — the R6 benchmark test checks its four
  non-`EXTERNAL` reference paths before reading them, skips with the exact missing path in a scrubbed mirror, and
  keeps the existing byte, pixel and `EXACT_RENDERED` checks when the images are available. The canonical and
  scrubbed mirror verification gates both passed.
- **General generation and typed layout (`v0.4.7`)** — optional `visualTokens` preserve
  supported model-selected color and typography roles through deterministic token resolution and native construction.
  The runtime checks exact font family/style availability and applies the selected size, line height, and letter
  spacing; it reuses loaded fonts and parent nodes. Eligible Host Reference Stage-A candidate reads and PNG exports
  are batched to reduce round trips in that probe path. Evidence: three compiled-proposal scenes validated native
  parameters, viewport, relations and containment; measured transport improvement is scoped to eligible candidate
  reads and exports.
- **Host planning and offline validation (`v0.4.9`)** — Host CLI start returns the complete start DTO, continue
  uses the saved run-state guard, and `host validate` checks proposals, reviews, and plans offline. Proposal
  validation returns its normalized result and deterministic repairs for review. MCP initialize plus `tools/list`
  shrank from 41,238 to 24,585 bytes (40.4% less default discovery payload); the full reference guide remains on
  demand at 20,352 text bytes (20,600 bytes in its JSON-RPC response). This is a context-size result, not a runtime
  speed or design-quality claim.
- **General generation and typed native layout (`v0.4.8`)** — Greenfield charts use explicit labels,
  units, and finite numeric points. Missing chartData shows a no-data state; malformed or non-finite input fails
  schema validation. Zero-valued points in signed data create no bars, while valid all-zero series retain zero-baseline
  markers. Tables, activity rows, mobile titles, and actions fit bounded section widths through wrapping or stacking.
  Reuse keeps row content, styles, descendant positions, and component identity, and fails closed when geometry is
  missing. Grouped sections preserve native order and header bounds. Delete guards protect rollback stash frames named
  fdr:stash that are both hidden and locked, and refuse overlapping ancestor/descendant targets. Two fixed Native
  fixtures passed scoped tree, text, viewport, and rollback checks; they do not establish premium design quality or
  successful component reuse. Chart-axis and grid alignment remains a P2 polish item. The Oct 5 Host closure completed
  final review of the Oct 2 task after its timing window; it provides no new generation time.
- **ADAPTATION boundary** — one live adaptation reached policy completion with `strictComplete=false`; the
  strict fidelity ledger remained `NOT_COMPARABLE_TARGET`. This is not a strict fidelity PASS or pixel-equivalence claim.
- **Write safety first** — every write is schema-validated before dispatch; writes are never retried
  automatically; transactions keep a shadow snapshot; locks live in node `pluginData`; terminal states
  are backed by write-once artifacts with hashes.
- **Evidence over optimism** — independent integrity checks recompute coverage, warnings and operation
  ownership from the raw ledger; a failing gate stops the run and asks a human instead of claiming success.
- **Reference reconstruction** — a 115-element support matrix, deterministic measurement, host-authored
  manifests, asset settlement (Community transfer / media / vectors) and a region fidelity ledger with
  pixel metrics.
- **Honest limits, documented** — no URL references; assets are supplied manually; chart values require explicit
  numeric input; reconstruction is structural (native, editable), not pixel-identical across renderers. Axis and grid
  alignment remains a P2 polish item.
- **Three-page demo closure (`v0.3.0-demo`)** — Analytics, Settings and Pokecut as native Figma pages;
  fake icons are refused; missing media/vectors stay on a typed work order; a measured same-PNG
  decomposition can be rebound onto a new run.
- **Measured skeleton (`v0.4.1-host-crops`)** — a new PNG does not need a page generator: measurement
  grows a shell, empty vertical gutters split columns, the host fills only leaf bands, and Auto Layout
  owns in-flow geometry (ink calibration is evidence, not a write). `figma_design_start` returns
  `leafFillBands` with a 1:1 crop of each leaf — no OCR. `figma_design_continue` accepts
  `reference_band_fills` against that skeleton (same path as the CLI `fill` command).
- **The measured host loop (`v0.4.4-host-loop`)** — one live run through the whole path: skeleton → 3x reading
  crops → host fills (48 strings read from the crops) → real Figma text calibration → visual review → two
  scoped correction rounds. A real library icon (koboyo) imported through the existing `TRACE_VECTOR`
  bindings (29/29 verified), and real photos settled the `PLACE_MEDIA` avatars. Measured families converge
  on one type token (7 → 1 drift on replay); fills never place columns closer than the minimum gap and never
  overwrite a completed skeleton.
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
源码规模：537 个 TypeScript 文件、250,786 行（统计包含 `scripts/` 与 `tests/`）；14 个 workspace
（`packages/` 下 13 个加 `figma-plugin`）；52 个类型化 Figma 协议方法、32 个 MCP 工具。
v0.4.9 canonical 完整验证：3,085 项测试，3,084 通过、1 项跳过、0 项失败，共 453 个测试套件。
v0.4.9 清理镜像 CI：3,079 项测试，3,063 通过、16 项跳过、0 项失败，共 453 个测试套件（main 与 release tag 均通过）。
镜像跳过项包含 provider-gated 检查与历史清理中缺失的本地 source inputs；R6 scene-reference 检查只在准确输入路径缺失时跳过。
v0.4.9 Host planning：CLI 可返回完整 start handoff，按运行状态继续，并离线校验 proposal/review/plan。MCP 默认 initialize + `tools/list` 从 41,238 字节降至 24,585 字节（减少 40.4% 的默认 discovery payload）；完整 reference guide 按需返回，文本为 20,352 字节。这是上下文体积变化，不代表端到端提速或视觉质量提升。
通用生成能力（v0.4.7）：可选 typed `visualTokens` 将受支持的视觉选择从 proposal 传到确定性 token 解析和原生施工；运行时校验精确字体 face，并实际应用字号、行高和字距。符合条件的 Host Reference Stage-A 候选读回与 PNG 导出按批处理，减少该探针路径的往返。三场景 compiled-proposal smoke 验证了原生参数、viewport、关系和 containment；实测收益限定在候选读回与导出路径。
v0.4.8 Greenfield 图表消费明确提供的标签、单位和有限数值；未提供 chartData 时显示空数据状态，格式错误或非有限数值由 schema 拒绝。正负数值域中的零点不会生成柱，合法的全零 series 保留零基线标记。表格、活动行、移动端标题和动作遵守 section 可用宽度，需要时换行或纵向堆叠。组件复用保留内容、样式、后代位置和组件身份；缺少几何证据时拒绝复用。分组 section 保持原生顺序，fdr:stash 回滚框架需同时隐藏且锁定才受保护，重叠删除请求在写入前拒绝。Oct 5 Host task 跨过 Oct 2 计时窗口后完成最终复审，没有新的生成计时；限定的 Native 与 Host 证据不代表 premium design 或严格参考图等价。
有一个真实移动端 ADAPTATION 样例按独立策略完成；`strictComplete=false`，保留的 fidelity ledger 为
`NOT_COMPARABLE_TARGET`。这不代表 strict fidelity PASS 或像素等价。
