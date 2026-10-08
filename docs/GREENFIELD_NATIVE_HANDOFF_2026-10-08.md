# Greenfield native handoff · 2026-10-08

**Status: scoped native pass and source verification complete; Host completion remains open.** Root reviewed this fixture's PNG and complete native tree and returned `SCOPED_NATIVE_PASS`. The same run's Host state is `REVIEW_REQUIRED`; `hostComplete=false` and `visualReviewSubmitted=false`. The archived code checkpoint `08ef30426465d041a7c760fcfa84fd6ed7e54755` had two successful local test runs with the same result: 3,201 tests, 3,197 passed, 4 skipped, 0 failed, 454 suites. The passive-preload diagnostic (384.773 s) ran tests only; the official plain `npm run verify` (387.477 s) is the only run here that completed the guard, TypeScript build, and plugin build. It used no preload or `NODE_OPTIONS` and is the only full local release gate; the passive test-only diagnostic is not equivalent to it. Three skips are the approved R06 local T12 fixture boundary; the fourth is `FDR_REAL_MODEL` unset. Earlier plain `npm run verify` attempts were stopped after stalling at listener27 and did not pass; the cause is unknown. These successful checks do not establish why those attempts stalled. This is not a benchmark: `benchmarkRun=false`, `speedupClaim=null`, and `oldTimingReceiptUsed=false`.

## Source, entry, and scope

The native acceptance was run from the tracked-clean code checkpoint `worktrees/visual-data-oct8`, branch `fix/visual-data-oct8`, at source `08ef30426465d041a7c760fcfa84fd6ed7e54755`. Provenance records `canonicalHead=f285dc0c603c56ac021cb9261903f272fb9be26c` at capture; this is a provenance boundary, not a statement about the repository HEAD after the documentation closeout. The Oct 8 `19:08.377` timing belongs to `f285dc0`, not `08ef304`.

The run was `host_0muzajjeo127e7n1`, targeting `AI2figma Performance AB`, page `282:1083` (`E2E Oct7`), owned root `289:261`. The path was Host-only pure Greenfield through `node packages/cli/src/bin.ts host start/continue and typed CLI rpc`; this feature adds no provider-mode or reference-mode footprint. A language hint exists in the new work, but it has not been separately timed or shown to improve quality.

The fixture intentionally derives from the earlier source proposal and changes only the alignment representation: the alignment map is serialized as the ordered array `LEFT, LEFT, RIGHT, RIGHT, LEFT`. The provenance reports `allOtherContentMatchesSource=true`. This is a scoped normalization/replay test, not fresh independent design generation. It reuses proposal content as fixture input, but not a prior timing receipt or screenshot/result. The protected prior root `253:1518` on page `212:2` was not touched.

The existing compiler behavior omits three proposal headings in the native output. The 67 actual baseline text nodes were preserved and matched (`visibleTextCount=67`, `rootConfirmedBaselineTextMatch=true`). Do not claim that every raw proposal heading or string was rendered; the preservation result is specifically about those 67 baseline texts.

For deployment context, the Bridge was not restarted and the Figma plugin was not reimported. The loaded manifest ID is `fdr-integrity-oct7-6576101`. The provenance identifies the plugin bundle under `worktrees/perf-integrity`; therefore this result must not be described as a fresh deployment of a plugin built from `08ef304`.

## Visual checks and native result

The provenance records three checked visual-fix areas:

1. The chart's zero tick is centered on its one-pixel zero line within 1 px (`zeroTickCenterDeltaPx=1.0`, `zeroTickWithin1px=true`).
2. The scale ticks `5.6e+6` and `2.8e+6` each fit on one 40 × 15 px line, and the daily-token caption fits on one 64 × 15 px line.
3. Both right-aligned table headers and all 10 numeric cells align to the right; the long bilingual service name remains present and readable. The root also confirmed the baseline text match.

The emitted `greenfield-native-tree-v1` artifact is complete for root `289:261`: 129 nodes with unique IDs, no child-count mismatches, 44 FRAME, 18 RECTANGLE, 67 TEXT, 0 IMAGE, and 0 image fills. Its record reports `artifactShaMatches=true`, `rootDigestMatches=true`, and `pngShaMatches=true`. The run fingerprint matches the artifact fingerprint and is embedded in the artifact filename. The separate tree verification proof also records the full-tree result.

The artifact records six runtime supplemental reads and 21 supplemental nodes. It delivers the completed readback for independent inspection and avoids repeating those helper reads manually at Host/Root; it does not remove the runtime's own readback work. The read consists of multiple reads rather than one transactionally frozen Figma snapshot. This scoped result confirms a complete, internally consistent capture (`complete=true`, unique IDs, zero child-count mismatches); it does not establish atomic isolation from concurrent document edits or measure latency.

Artifact identity is the fingerprint of the whole serialized package, including timestamps and read/capture anchors; the native tree digest alone does not determine it. A fresh capture's artifact key uses that full-body fingerprint, so an unchanged root digest does not guarantee the same artifact path. Stable path across restart/replay comes from restoring or reusing the same persistent artifact pointer, not from taking a new capture. A correction invalidates the stored pointer before the mutation plan is applied; this does not require claiming that every correction changes the tree digest. This provenance confirms the matching artifact, root digest, and PNG for one captured run. The persistence and invalidation behavior is a lifecycle contract, not an additional measurement from this single native review.

## Cleanup and protection evidence

Cleanup transaction A stashed deletion of the owned root `289:261` and committed one operation. Cleanup transaction B then committed as a no-op with zero operations. Strict-empty readback on the same page `282:1083` confirmed zero page children, zero direct children, no truncation, zero selection, zero locks, no active transaction, and no current transaction in the list. The prior transaction history did not contain A or B before this run; the post-run history records the cleanup. The protected root `253:1518` and page `212:2` remained untouched. This proves cleanup for this owned fixture root; it is not a migration or deletion of prior records.

## Limits and closure state

`08ef304` has a scoped native acceptance and passed local source verification, while Host remains `REVIEW_REQUIRED` and the Host visual-review stage was not submitted. No `qualityReady` result, timing, speedup, regression, feature-release readiness, or full Host workflow completion can be inferred. The `f285dc0` timing and historical `4fea12d` native-MCP timing remain separate observations with different source and entry. Earlier plain `npm run verify` attempts were stopped after stalling at listener27 without passing; the cause is unknown. They are historical diagnostics, not evidence of a current hang or a diagnosed fix. This handoff records local verification only.

This record closes the scoped Greenfield fixture and cleanup evidence. It does not reopen the no-reference Greenfield workflow or continue Host review. Preserve prior receipts and historical reports unchanged.

## Local evidence pointers (not publication links)

- Native provenance: `D:\python项目\AI2figma\worktrees\visual-data-oct8\.fdr\tmp\visual-native-oct8\scoped-native-acceptance.provenance.json` — SHA-256 `0b8c54a52137069cf44271c6c542105806d7e36ed20fcdbb6d63e8bee2211bc2`.
- Native-tree artifact: `D:\python项目\AI2figma\worktrees\visual-data-oct8\.fdr\artifacts\runs\host_0muzajjeo127e7n1\greenfield-native-tree-v1-635bb771605ac14804c88efe4e58c853b68986002df481ffd6bb4944da37c460.json` — file SHA-256 `814af23c4c1b53bbd6cb5f792dcad475d0d91922f215eae5c9ee9f5088b8ee9b`; tree digest `e805e804757e0e9c1a0b71bf26abb0514615f5327ad201305f28897fd2bf89a0`; artifact fingerprint `635bb771605ac14804c88efe4e58c853b68986002df481ffd6bb4944da37c460`.
- Captured PNG: `D:\python项目\AI2figma\worktrees\visual-data-oct8\.fdr\artifacts\runs\host_0muzajjeo127e7n1\images\greenfield.png` — SHA-256 `ea5374dd91cc489d964f5dab04e7f09df0c8349b0968e8d5d04b0461dbda0fa5`.
- Full-tree verification proof: `.fdr\tmp\visual-native-oct8\native-tree-verify.json` — SHA-256 `977a667332df13c7332bcf6993cd69e6d6b14deea7194504c4310d89aa4a7e8f`.
- Replay fixture SHA-256 `7eb7715574028db0e3b169537e6e26e9ed72327787a8cd1677500315c5acb7b4`; source proposal SHA-256 `53f8842c13050529bd1ac8b1bdd6e34f44bec49062dce9b278a33c8cea320815`.
- Plain verification log: `worktrees/visual-data-oct8/node_modules/.test-temp/plain-verify-08ef304-2026-10-08/verify.log` — SHA-256 `d84f037f436ae6a5590bd23581d384189bfc5f2a1f849cec882a464d80870463`.

---

# Greenfield 原生交接 · 2026-10-08

**状态：范围内原生验收与源码验证已通过；Host 完成状态仍开放。** Root 已检查本 fixture 的 PNG 和完整原生树，给出 `SCOPED_NATIVE_PASS`。同一次运行的 Host 状态仍为 `REVIEW_REQUIRED`；`hostComplete=false`、`visualReviewSubmitted=false`。归档的 code checkpoint `08ef30426465d041a7c760fcfa84fd6ed7e54755` 有两次成功的本地测试运行，结果相同：3,201 项测试、3,197 通过、4 跳过、0 失败，共 454 个套件。passive-preload 诊断（384.773 s）只运行了测试；官方 plain `npm run verify`（387.477 s）是这里唯一完整执行 guard、TypeScript build 与 plugin build 的运行。它未使用 preload 或 `NODE_OPTIONS`，是唯一完整的本地 release gate；passive test-only 诊断不等同于全量 gate。3 个 skip 是已批准的 R06 local T12 fixture 边界，另 1 个是未设置 `FDR_REAL_MODEL`。更早的 plain `npm run verify` 尝试卡在 listener27 后被停止，未通过；原因未知。这些成功检查不能解释此前停滞的原因。本样本不是 benchmark：`benchmarkRun=false`、`speedupClaim=null`、`oldTimingReceiptUsed=false`。

## 源码、入口与范围

原生验收从 tracked-clean code checkpoint `worktrees/visual-data-oct8` 运行，branch 为 `fix/visual-data-oct8`，源码 commit 为 `08ef30426465d041a7c760fcfa84fd6ed7e54755`。provenance 记录捕获时的 `canonicalHead=f285dc0c603c56ac021cb9261903f272fb9be26c`；这是来源边界，不代表本次文档收尾之后仓库 HEAD 仍然如此。10 月 8 日 `19:08.377` 计时属于 `f285dc0`，不属于 `08ef304`。

本次 run 为 `host_0muzajjeo127e7n1`，目标文件 `AI2figma Performance AB`，页面 `282:1083`（`E2E Oct7`），owned root `289:261`。入口是 Host-only pure Greenfield，通过 `node packages/cli/src/bin.ts host start/continue and typed CLI rpc`；这项功能没有增加 provider mode 或 reference mode 的 footprint。新工作中有 language hint，但没有单独计时，也没有证明它能提升质量。

Fixture 是从先前的 source proposal 派生，只改变 alignment 表示：将 alignment map 编码为有序数组 `LEFT, LEFT, RIGHT, RIGHT, LEFT`。provenance 记录 `allOtherContentMatchesSource=true`。这是范围内的规范化/重放验证，不是全新独立设计生成。它有意复用 proposal 内容作为 fixture 输入，但没有复用旧计时 receipt 或旧 screenshot/result。既有保护 root `253:1518`（位于页面 `212:2`）未被触碰。

现有 compiler 行为会在原生输出中省略三个 proposal headings。67 个实际 baseline text 节点均保留并匹配（`visibleTextCount=67`、`rootConfirmedBaselineTextMatch=true`）。不要宣称所有 raw proposal headings 或 strings 都被渲染；保留结果特指这 67 个 baseline texts。

部署背景：Bridge 未重启，Figma 插件未重新导入。已加载 manifest ID 为 `fdr-integrity-oct7-6576101`。provenance 标明插件 bundle 来自 `worktrees/perf-integrity`；因此不能把本结果表述为已将 `08ef304` 构建的插件重新部署。

## 视觉检查与原生结果

provenance 记录了三个视觉修复检查面：

1. 图表零刻度与 1 px 零线居中差值为 1 px，符合 1 px 范围（`zeroTickCenterDeltaPx=1.0`、`zeroTickWithin1px=true`）。
2. `5.6e+6` 和 `2.8e+6` 刻度都以单行放入 40 × 15 px 区域；daily-token caption 也以单行放入 64 × 15 px 区域。
3. 两个右对齐表头及 10 个数值单元格均右对齐；长中英文服务名仍完整可见。Root 同时确认 baseline 文本匹配。

为 root `289:261` 输出的 `greenfield-native-tree-v1` artifact 完整，含 129 个节点且 ID 唯一，没有 child-count mismatch；节点类型为 44 FRAME、18 RECTANGLE、67 TEXT、0 IMAGE、0 image fills。记录显示 `artifactShaMatches=true`、`rootDigestMatches=true`、`pngShaMatches=true`。run fingerprint 与 artifact fingerprint 相同，并包含在 artifact 文件名中。另有独立的完整树验证 proof。

artifact 记录 runtime 使用 6 次 supplemental reads，补回 21 个节点。它把完整读回结果交付给独立检查，避免 Host/Root 再手动重复这些 helper reads；但不会取消 runtime 自身的读回。这些结果来自多次读取，不是对 Figma 文档做一次事务冻结的 snapshot。本范围证明本次 capture 完整且内部一致（`complete=true`、ID 唯一、child-count mismatch 为 0），不证明并发编辑隔离，也不提供耗时测量。

Artifact identity 是整个序列化 package body 的 fingerprint，包含 timestamps 与 read/capture anchors；它不只由 native-tree digest 决定。Fresh capture 的 artifact key 使用完整 body fingerprint，因此 root digest 相同也不保证 artifact path 相同。跨 restart/replay 的路径稳定性来自恢复或重用同一持久化 artifact pointer，而不是重新 capture。执行 correction 时，应在应用 mutation plan 前 invalidate 已存 pointer；这不要求声称每次 correction 都改变 tree digest。本 provenance 确认的是单次捕获的 artifact、root digest 与 PNG 匹配；持久化与失效行为属于生命周期契约，不是本次原生复核额外测得的结果。

## 清理与保护证据

Cleanup A 将 owned root `289:261` 的删除操作 stashed 并提交了一个 operation。随后 Cleanup B 以 no-op 提交，operation 数为 0。在同一页面 `282:1083` 做 strict-empty readback，确认页面 child 数为 0、direct children 为 0、没有截断、selection 为 0、locks 为 0、无 active transaction，transaction list 中也没有当前事务。本轮前的事务历史不含 A 或 B；本轮后的历史记录了这两次 cleanup。保护 root `253:1518` 和页面 `212:2` 未被触碰。这证明本次 owned fixture root 清理成功，不是迁移或删除历史记录。

## 限制与封存状态

`08ef304` 有范围内原生验收和通过的本地源码验证；Host 仍是 `REVIEW_REQUIRED`，且 Host visual-review 阶段未提交。不能据此推断 `qualityReady`、计时、加速、回退、feature-release readiness 或完整 Host 工作流完成。`f285dc0` 计时和历史 `4fea12d` native-MCP 计时仍是源码、入口不同的独立观测。早先 plain-verification 序列是已中断的历史诊断，原因未知；它不代表当前仍挂起，也不代表已查明修复原因。本交接只记录本地验证。

本记录封存范围内 Greenfield fixture 与 cleanup 证据；不会据此重启无参考 Greenfield 工作流或继续 Host review。保留既有 receipt 和历史报告。

## 本地证据指针（不是发布链接）

- Native provenance：`D:\python项目\AI2figma\worktrees\visual-data-oct8\.fdr\tmp\visual-native-oct8\scoped-native-acceptance.provenance.json` — SHA-256 `0b8c54a52137069cf44271c6c542105806d7e36ed20fcdbb6d63e8bee2211bc2`。
- Native-tree artifact：`D:\python项目\AI2figma\worktrees\visual-data-oct8\.fdr\artifacts\runs\host_0muzajjeo127e7n1\greenfield-native-tree-v1-635bb771605ac14804c88efe4e58c853b68986002df481ffd6bb4944da37c460.json` — 文件 SHA-256 `814af23c4c1b53bbd6cb5f792dcad475d0d91922f215eae5c9ee9f5088b8ee9b`；tree digest `e805e804757e0e9c1a0b71bf26abb0514615f5327ad201305f28897fd2bf89a0`；artifact fingerprint `635bb771605ac14804c88efe4e58c853b68986002df481ffd6bb4944da37c460`。
- Captured PNG：`D:\python项目\AI2figma\worktrees\visual-data-oct8\.fdr\artifacts\runs\host_0muzajjeo127e7n1\images\greenfield.png` — SHA-256 `ea5374dd91cc489d964f5dab04e7f09df0c8349b0968e8d5d04b0461dbda0fa5`。
- Full-tree verification proof：`.fdr\tmp\visual-native-oct8\native-tree-verify.json` — SHA-256 `977a667332df13c7332bcf6993cd69e6d6b14deea7194504c4310d89aa4a7e8f`。
- Replay fixture SHA-256 `7eb7715574028db0e3b169537e6e26e9ed72327787a8cd1677500315c5acb7b4`；source proposal SHA-256 `53f8842c13050529bd1ac8b1bdd6e34f44bec49062dce9b278a33c8cea320815`。
- Plain verification log：`worktrees/visual-data-oct8/node_modules/.test-temp/plain-verify-08ef304-2026-10-08/verify.log` — SHA-256 `d84f037f436ae6a5590bd23581d384189bfc5f2a1f849cec882a464d80870463`。
