# Generation timing · desktop-greenfield · 2026-10-08

**Status: observed historical measurement.** This report records one `current-main` timing run on frozen source `f285dc0`; it is not a paired performance trial and is not timing evidence for source `08ef304`. It did not meet the previously used 15-minute efficiency target: measured request-to-quality-ready time was 19:08.377. The PREPARED and observer records do not establish an enforced hard cap for this run. `qualityReady=true` records five design-quality checks only; it does not mean the efficiency target or overall objective was achieved. The accepted criteria cover required information, budget focus, readability without truncation or overlap, table alignment, and native editability. They do not establish that the design is best possible or that the user has signed off; `userAcceptance` is null, and visual polish items remain.

**Separate source status:** Source checkpoint `08ef30426465d041a7c760fcfa84fd6ed7e54755` later received `SCOPED_NATIVE_PASS`; its Host state remains `REVIEW_REQUIRED`, and it has no timing result. Two local test runs exited 0 and reported 3,201 tests, 3,197 passed, 4 skipped, 0 failed, and 454 suites: a passive-preload test-only diagnostic (384.773 s), then the official plain `npm run verify` (387.477 s). Only the official plain run completed the guard, TypeScript build, and plugin build; it used no preload or `NODE_OPTIONS` and is the only full local release gate. The passive test-only diagnostic is not equivalent to a full gate. Three skips are the approved R06 local T12 fixture boundary; the fourth is `FDR_REAL_MODEL` unset. Earlier plain `npm run verify` attempts were stopped after stalling at listener27 and did not pass; the cause is unknown. These successful checks do not establish why the earlier attempts stalled.

## Run comparison

| Sample | Source · entry | Quality outcome | Request-to-quality-ready |
| --- | --- | --- | ---: |
| Observed run · 2026-10-08 | `f285dc0` · CLI → typed-bridge Host | Host COMPLETE; Root ACCEPTED; five design-quality checks passed | 1,148,376.876 ms · **19:08.377** |
| Historical · 2026-10-06 | `4fea12d` · NATIVE_MCP | Host COMPLETE; Root ACCEPTED; `qualityReady=true` | 760,815.878 ms · **12:40.816** |

The raw difference is 6:27.561 by direct subtraction. The source and entry differ (`f285dc0` with CLI/typed-bridge Host flow versus `4fea12d` with `NATIVE_MCP`), so these are not a controlled performance pair; the difference supports no acceleration or regression claim or percentage. This measurement belongs entirely to frozen source `f285dc0`; do not attribute it to later fixes. Source `08ef304` passed the official plain verification and scoped native acceptance, but was not timed. This observation remains historical and does not create a future Greenfield timing or optimization task.

## Evidence identifiers

- Current session: `e2e-luna-max-current-main-2026-10-08-01`; experiment: `optimization-oct8-timing-current-main`; pair: `current-main-single-2026-10-08-01`; full runtime commit: `f285dc0c603c56ac021cb9261903f272fb9be26c`; receipt file SHA-256: `7fd8e78da551ec299d300085c8d3018914249a795a1091936e8c1eb949362aba`.
- Historical accepted session: `e2e-lunamax-4fea-native-2026-10-06-01`; full source commit: `4fea12d2511dc3f70a828b9322c84ee6993e8076`; receipt file SHA-256: `5e2fe92709d5522d56d7c8096ba94afe475d42a96f4575ee0c4c8f202b9b9453`.
- Separate later gate: source `08ef30426465d041a7c760fcfa84fd6ed7e54755`; plain verification log `worktrees/visual-data-oct8/node_modules/.test-temp/plain-verify-08ef304-2026-10-08/verify.log`, SHA-256 `d84f037f436ae6a5590bd23581d384189bfc5f2a1f849cec882a464d80870463`. This is gate evidence, not a timing receipt.

## Observed-run evidence

The session is `e2e-luna-max-current-main-2026-10-08-01`, experiment `optimization-oct8-timing-current-main`, task `desktop-greenfield`, arm `current-main`, trial 1. The target was `AI2figma Performance AB`, on frozen runtime commit `f285dc0c603c56ac021cb9261903f272fb9be26c`, with a clean worktree and release tag `bench-oct7-integrity-f285dc0`. The session records GPT-6 Luna at max effort in Host mode, observer 1.1.0, and `providerCalls=0`. Its transport is `direct_orchestrator_host_via_typed_bridge`. The receipt reports `VALID_MONOTONIC` timing integrity and `MONOTONIC_TOOL_CALL_EXCLUDED` for Host reasoning. The receipt file hash appears in Evidence identifiers and is distinct from the receipt object's internal fingerprint.

Root accepted five checks: required information, budget focus, readability without truncation or overlap, table alignment, and native editable elements. The final canvas was 1440 × 900. Its complete native tree contains 129 design nodes (130 including the PAGE): 67 TEXT, 18 RECTANGLE, 44 FRAME, 0 IMAGE, and 0 image fills. The final tree proof SHA-256 is `ec61d06fa12a292c19e0f25021d225718b47b5db411ad0d82282cdae1c82b51e`; the accepted review image SHA-256 is `bcb6cf8ac0bbdbd4f89c96c4755c59de8ac8d45da11e5f15eacfbad82647c08f`.

The first tree read was depth-limited to 108 nodes, so it was not a complete-tree proof. Six supplemental helper reads recovered 21 additional nodes. The final count and hash above refer to the complete tree. This readback gap is relevant to the workflow analysis and should not be described as a design-node omission.

The visual review also retained polish opportunities: chart axis labels break million-scale scientific notation across lines; the interface copy is English although the request is Chinese; `Slow` and `Failed` are styled like `Completed`; and the anomaly baseline value wraps onto a short line by itself. These did not invalidate the five Root acceptance checks. Record acceptance as scoped quality approval, not as a claim that no visual issues remain.

## Timing interpretation

| Clock | Recorded value | Interpretation |
| --- | ---: | --- |
| Request → quality ready | **1,148,376.876 ms (19:08.377)** | Continuous observer-monotonic interval from watcher start immediately before the fixed request through machine COMPLETE and accepted Root review; includes runtime, model, and intervening idle time. |
| Host reasoning | 282,846.245 ms | Union of measured manual Host spans after subtracting overlapping tool-call intervals on the continuous monotonic clock. Manual Host time may include reasoning, service wait, coordination, and other work; it is not pure inference. |
| Raw Host-span sum | 293,815.712 ms | Additive pre-correction sum for 2 measured Host spans; audit value, not exclusive Host time. |
| Tool-call span union | 150,332.065 ms across 12 spans | Manually bracketed tool-call intervals. |
| Root independent review | 648,921.942 ms across 1 span | Manual wall interval includes waiting for Host COMPLETE, typed-tree proof readback and supplemental reads, tool handoffs, and Root coordination; it is not pure visual inspection or CPU inference. |
| Runtime active | 6,577.206 ms | Host task-ledger runtime active time. |
| Host waiting | 597,023 ms | Host ledger cross-process waiting; may include model reasoning or idle time. |
| Latest Host workflow wall clock | 603,600 ms | Starts at the first Figma Host call, not at the user request. |
| Cumulative Figma ActionLog duration | 1,383 ms | Sum of operation durations; it is not end-to-end wall time. |
| Explicit user wait | 0 ms | No operator wait span was recorded. |

These clocks have different scopes and may overlap; do not sum them to reconstruct the request window. The receipt records 2 Host spans, 12 tool-call spans, 1 Root review span, and 0 incomplete or unmeasured spans. “No incomplete spans” does not mean manual spans cover the entire request window. The observer event-bounded `observer_start → quality_ready` window is a separate denominator from the receipt's request-to-quality-ready interval.

**Coverage report:** `.fdr/tmp/optimization-oct8/timing-current-main/coverage-report.json`, SHA-256 `c18029fc710b8dd7404290a9806a914efdc725c3b0d6bbf072e1464d32fe9011`. Its `COMPLETE_MONOTONIC_WINDOW` status means the observer start and quality-ready events share a valid monotonic window; manual spans cover 79.308% of that window. The event-bounded denominator is 1,148,363.998 ms; the covered union is 910,741.968 ms, and 237,622.030 ms (20.692%) is unclassified. The sum of clipped span durations is 1,117,452.159 ms, with 206,710.191 ms of overlap. The five uncovered intervals, measured from observer start, are 0–29,279.971 ms; 64,789.384–96,029.853 ms; 258,942.428–323,563.225 ms; 342,198.053–451,304.970 ms; and 1,144,990.122–1,148,363.998 ms. Each is labeled `UNCLASSIFIED_NOT_COVERED_BY_A_MEASURED_MANUAL_SPAN`; the report has 0 unknown intervals and 0 anomalies. The event-bounded duration is 12.878 ms shorter than the receipt's request-to-quality-ready value because the boundaries differ. Do not attribute uncovered time to model reasoning or combine this denominator with receipt timing.

**Cleanup:** the cleanup receipt at `.fdr/tmp/optimization-oct8/timing-current-main/observer-evidence/cleanup-receipt.json` confirms one owned root was deleted, zero roots remain, and the experiment was retired. Cleanup occurred after quality-ready and is explicitly excluded from request-to-quality-ready timing. Its separate `.fdr/tmp/optimization-oct8/timing-current-main/cleanup-stopwatch.json` has SHA-256 `b72f5ce0b0adfb49dd9d5b95ff7c03a7d07206c6e479239111aeb658f2de6001`; `clockIntegrity=DEGRADED_SPLIT_MONOTONIC_AFTER_LOCAL_PROOF_VALIDATION_FAILURE`, `elapsedMs=null`, wall-clock display 360,571.934 ms, monotonic time across segments 6,375.085 ms, and a UTC gap of 354,413.726 ms. Treat those as cleanup diagnostics, not as one valid elapsed duration and not as part of the official request clock.

## Archive boundary

This timing record is retained as a historical observation of source `f285dc0`. It does not open further no-reference Greenfield design, timing, observer-optimization, or release work. The later `08ef304` verification and scoped native result are separate evidence and are recorded separately.

---

# 生成计时 · desktop-greenfield · 2026-10-08（中文）

**状态：已观测的历史计时。** 本报告只记录冻结源码 `f285dc0` 上的一次 `current-main` 运行，不是成对性能实验，也不是源码 `08ef304` 的计时证据。本轮未达到此前采用的 15 分钟效率目标：实测 request-to-quality-ready 为 19:08.377。PREPARED 和 observer 记录没有定义本轮必须执行的硬性 cap。`qualityReady=true` 只表示五项设计质量检查通过，不表示效率目标或整体任务目标已完成。验收覆盖必要信息、预算重点、无截断或重叠、表格对齐和原生可编辑元素；这不等于设计已经达到最佳状态，也不代表用户已签收（`userAcceptance=null`），目前仍有视觉润色项。

**独立的源码状态：** 源码检查点 `08ef30426465d041a7c760fcfa84fd6ed7e54755` 后续通过了 `SCOPED_NATIVE_PASS`，但 Host 仍是 `REVIEW_REQUIRED`，且没有计时结果。两次本地测试运行均 exit 0，报告相同结果：3,201 项测试、3,197 通过、4 跳过、0 失败，共 454 个套件。先是仅运行 test suite 的 passive-preload 诊断（384.773 s），之后是官方 plain `npm run verify`（387.477 s）。只有官方 plain run 完整执行了 guard、TypeScript build 和 plugin build；其未使用 preload 或 `NODE_OPTIONS`，是唯一完整的本地 release gate。passive test-only 诊断不等同于全量 gate。3 个 skip 是已批准的 R06 local T12 fixture 边界，另 1 个是未设置 `FDR_REAL_MODEL`。更早的 plain `npm run verify` 尝试卡在 listener27 后被停止，未通过；原因未知。这些成功检查不能解释此前停滞的原因。

## 本轮与历史样本

| 样本 | 源码 · 入口 | 质量结果 | 请求到质量就绪 |
| --- | --- | --- | ---: |
| 观测样例 · 2026-10-08 | `f285dc0` · CLI → typed-bridge Host | Host COMPLETE；Root ACCEPTED；五项设计质量检查通过 | 1,148,376.876 ms · **19:08.377** |
| 历史 · 2026-10-06 | `4fea12d` · NATIVE_MCP | Host COMPLETE；Root ACCEPTED；`qualityReady=true` | 760,815.878 ms · **12:40.816** |

直接相减的原始差值为 6:27.561。两次运行源码和入口不同（本轮 `f285dc0` + CLI / typed-bridge Host 流程，历史为 `4fea12d` + `NATIVE_MCP`），不是受控性能对照，因此不能据此声称加速或回退，也不能计算百分比。本次计时完全对应冻结源码 `f285dc0`，不能归因于后续修复。`08ef304` 已通过官方 plain verification 和范围内原生验收，但没有计时；本报告只是历史观测，不再生成无参考 Greenfield 计时或优化任务。

## 证据标识

- 当前 session：`e2e-luna-max-current-main-2026-10-08-01`；experiment：`optimization-oct8-timing-current-main`；pair：`current-main-single-2026-10-08-01`；完整 runtime commit：`f285dc0c603c56ac021cb9261903f272fb9be26c`；receipt 文件 SHA-256：`7fd8e78da551ec299d300085c8d3018914249a795a1091936e8c1eb949362aba`。
- 历史已验收 session：`e2e-lunamax-4fea-native-2026-10-06-01`；完整源码 commit：`4fea12d2511dc3f70a828b9322c84ee6993e8076`；receipt 文件 SHA-256：`5e2fe92709d5522d56d7c8096ba94afe475d42a96f4575ee0c4c8f202b9b9453`。
- 后续独立 gate：源码 `08ef30426465d041a7c760fcfa84fd6ed7e54755`；plain verify 日志 `worktrees/visual-data-oct8/node_modules/.test-temp/plain-verify-08ef304-2026-10-08/verify.log`，SHA-256 `d84f037f436ae6a5590bd23581d384189bfc5f2a1f849cec882a464d80870463`。这是验证证据，不是计时 receipt。

## 本次观测证据

本轮 session 为 `e2e-luna-max-current-main-2026-10-08-01`，experiment 为 `optimization-oct8-timing-current-main`，task 为 `desktop-greenfield`，arm 为 `current-main`，trial 1。目标文件为 `AI2figma Performance AB`；固定 runtime commit 为 `f285dc0c603c56ac021cb9261903f272fb9be26c`，worktree clean，release tag 为 `bench-oct7-integrity-f285dc0`。session 记录 GPT-6 Luna、max effort、Host mode、observer 1.1.0 和 `providerCalls=0`；记录的 transport 为 `direct_orchestrator_host_via_typed_bridge`。receipt 报告 `VALID_MONOTONIC` 计时完整性和 `MONOTONIC_TOOL_CALL_EXCLUDED` Host 计时状态。receipt 文件 hash 在“证据标识”中列出，与 receipt 对象内部 fingerprint 不同。

Root 接受五项检查：必要信息、预算重点、无截断或重叠、表格对齐、原生可编辑元素。最终画布为 1440 × 900。完整原生树含 129 个设计节点（加 PAGE 共 130 个）：67 TEXT、18 RECTANGLE、44 FRAME、0 IMAGE、0 image fills。最终 tree proof SHA-256 为 `ec61d06fa12a292c19e0f25021d225718b47b5db411ad0d82282cdae1c82b51e`；Root 接受的 review image SHA-256 为 `bcb6cf8ac0bbdbd4f89c96c4755c59de8ac8d45da11e5f15eacfbad82647c08f`。

首次 tree 读取受 depth 限制，只有 108 个节点，因此不能当作完整树证明。随后通过 6 次补充 helper 读取补回了 21 个节点。上面的最终节点数和 hash 对应完整树。这个 readback 缺口属于工作流证据，不应表述成设计节点缺失。

视觉评审还记录了润色项：图表纵轴把百万级科学计数刻度拆成多行；任务提示为中文而界面文案为英文；`Slow` 与 `Failed` 和 `Completed` 使用相同样式；异常基线数值独占一行。这些问题没有推翻 Root 的五项验收。报告应说明这是限定范围内的质量接受，不应称为完全没有视觉问题。

## 计时解释

| 时钟 | 记录值 | 解释 |
| --- | ---: | --- |
| 请求到 quality ready | **1,148,376.876 ms（19:08.377）** | 从固定请求前 watcher 启动，到机器 COMPLETE 且 Root 接受的连续 observer monotonic 区间；包括 runtime、模型和中间空闲时间。 |
| Host reasoning | 282,846.245 ms | 连续 monotonic 时钟上，扣除与 tool-call 重叠区间后的手动 Host span 并集。手动 Host 时间可能包括推理、服务等待、协调及其他工作，不是纯模型推理。 |
| Host 原始 spans 总和 | 293,815.712 ms | 2 个实测 Host span 的修正前加和；仅供审计，不代表互斥的 Host 用时。 |
| Tool-call span 并集 | 150,332.065 ms，共 12 段 | 手动记录的 tool-call 区间。 |
| Root independent review | 648,921.942 ms，共 1 段 | 手动墙钟区间包含等待 Host COMPLETE、typed-tree proof 回读与补充读取、工具交接及 Root 协调；它不是纯视觉检查或 CPU 推理时间。 |
| Runtime active | 6,577.206 ms | Host task ledger 中的 runtime active 时间。 |
| Host waiting | 597,023 ms | Host ledger 跨进程等待，可能包括模型推理或空闲时间。 |
| Latest Host workflow wall clock | 603,600 ms | 从首次 Figma Host call 开始，不是从用户请求开始。 |
| Figma ActionLog duration 累计 | 1,383 ms | 多个操作时长的加和，不是端到端墙钟时间。 |
| 明确的 user wait | 0 ms | 没有记录 operator 等待 span。 |

这些时钟范围不同、可能重叠，不能相加来重建请求总时长。receipt 记录 2 个 Host span、12 个 tool-call span、1 个 Root review span、0 个未完成或未测量 span。“没有未完成 span”并不表示手动 spans 覆盖了整个请求窗口。Observer 的 `observer_start → quality_ready` 事件区间是另一个分母，与 receipt 的 request-to-quality-ready 不同。

**Coverage report：** `.fdr/tmp/optimization-oct8/timing-current-main/coverage-report.json`，SHA-256 为 `c18029fc710b8dd7404290a9806a914efdc725c3b0d6bbf072e1464d32fe9011`。`COMPLETE_MONOTONIC_WINDOW` 表示 observer start 与 quality-ready 事件处于有效的 monotonic 窗口；手动 spans 覆盖该窗口的 79.308%。事件窗口分母为 1,148,363.998 ms，覆盖并集为 910,741.968 ms，另有 237,622.030 ms（20.692%）未分类。裁剪后的 spans 加和为 1,117,452.159 ms，其中重叠 206,710.191 ms。相对 observer start 的五段未覆盖区间为：0–29,279.971 ms；64,789.384–96,029.853 ms；258,942.428–323,563.225 ms；342,198.053–451,304.970 ms；1,144,990.122–1,148,363.998 ms。每段都标记为 `UNCLASSIFIED_NOT_COVERED_BY_A_MEASURED_MANUAL_SPAN`；报告含 0 个 unknown intervals、0 个 anomalies。事件窗口时长比 receipt 的 request-to-quality-ready 值短 12.878 ms，是因为两者边界不同。不要将未覆盖时间归因于模型推理，也不要把 coverage 分母与 receipt 计时混用。

**Cleanup：** `.fdr/tmp/optimization-oct8/timing-current-main/observer-evidence/cleanup-receipt.json` 确认删除了一个本次运行创建的 root、剩余 root 为 0，且 experiment 已 retired。Cleanup 发生在 quality-ready 之后，并明确排除在 request-to-quality-ready 计时之外。独立的 `.fdr/tmp/optimization-oct8/timing-current-main/cleanup-stopwatch.json` SHA-256 为 `b72f5ce0b0adfb49dd9d5b95ff7c03a7d07206c6e479239111aeb658f2de6001`；其 `clockIntegrity=DEGRADED_SPLIT_MONOTONIC_AFTER_LOCAL_PROOF_VALIDATION_FAILURE`、`elapsedMs=null`、wall-clock 显示 360,571.934 ms、分段 monotonic 累计 6,375.085 ms、UTC gap 354,413.726 ms。这些是 cleanup 诊断数据，不构成一个有效的总耗时，也不属于正式 request clock。

## 归档边界

本计时记录作为源码 `f285dc0` 的历史观测保留，不再作为继续无参考 Greenfield 设计、计时、observer 优化或发布工作的依据。后续 `08ef304` 验证和范围内原生结果是独立证据，另行记录。
