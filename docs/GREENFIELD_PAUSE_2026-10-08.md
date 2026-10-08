# Greenfield pause and stage archive · 2026-10-08

**Status: no-reference Greenfield is paused.** On 2026-10-08, the user changed the product direction: the no-reference workflow that creates a design from zero is closed for development after this stage's bounded wrap-up and evidence archive. This is a work-priority decision, not a request to delete code, disable the workflow, or change API routing. Resume no-reference Greenfield work only if the user explicitly asks to reopen it or requests a specific exception.

The boundary is based on the actual presence of a real reference input, not on a `greenfield` string in a route or feature name. The pause applies to no-reference `workflow="greenfield"`. It does not apply to `reference_greenfield` when the user supplies an actual image, Figma node, or other supported reference, or to Existing edits based on a supplied Figma file, page, or selection.

## Archived stage and verified state

The archived code checkpoint is `08ef30426465d041a7c760fcfa84fd6ed7e54755`; its tracked source worktree was clean at verification time. An annotated archive tag, `archive/greenfield-stage-2026-10-08`, points to this checkpoint. It is a stage marker, not a formal release or version change. This checkpoint reference does not claim that the repository HEAD remains unchanged after documentation closeout. Two local test runs exited 0 and reported 3,201 tests, 3,197 passed, 4 skipped, 0 failed, and 454 suites: a passive-preload test-only diagnostic (384.773 s), then the official plain `npm run verify` (387.477 s). Only the official plain run completed the guard, TypeScript build, and plugin build; it used no preload or `NODE_OPTIONS` and is the only full local release gate. The passive test-only diagnostic is not equivalent to it. Four skips are the approved boundary: three R06 local T12 fixture cases and one case skipped because `FDR_REAL_MODEL` was unset.

The pause is not a test-skip policy. Existing Greenfield tests remain part of the required full release gate and must not be deleted, skipped, or weakened; no dedicated no-reference Greenfield test, benchmark, or acceptance run is scheduled. A future reference-led code change still follows the ordinary required verification gate.

The scoped native fixture reached Root `SCOPED_NATIVE_PASS` after review of its PNG and complete tree. The associated Host run remains `REVIEW_REQUIRED`, `hostComplete=false`, and `visualReviewSubmitted=false`; no Host `qualityReady` result was produced. The native result therefore closes only the recorded fixture scope. Its strict-empty cleanup removed the owned root and verified page `282:1083` had no children, selection, locks, or active transaction. Protected root `253:1518` on page `212:2` was untouched.

The tree artifact contains 129 native nodes: 67 TEXT, 18 RECTANGLE, and 44 FRAME, with unique IDs, no child-count mismatches, 0 IMAGE nodes, and 0 image fills. Artifact, root digest, and PNG checks matched. Six runtime supplemental reads recovered 21 nodes; the artifact delivers that complete readback and avoids repeating those helper reads at Host/Root. It does not eliminate the runtime's own reads. Existing compiler behavior omits three proposal headings from this fixture's native output; all 67 actual baseline text nodes were preserved. The sample does not establish that every raw proposal string rendered or that the Host workflow completed.

The fixture replay changed only alignment serialization from a map to the ordered array `LEFT, LEFT, RIGHT, RIGHT, LEFT`; the provenance records that all other content matched the source proposal. This was a scoped normalization/replay check, not a fresh design task or benchmark. No old timing receipt was used. The separate 19:08.377 timing belongs to the earlier frozen `f285dc0` CLI/typed-bridge run, not `08ef304`; it missed the previously used 15-minute efficiency target, and the different entry means it supports no speedup claim. Do not turn it into a future Greenfield optimization task.

Earlier plain `npm run verify` attempts were stopped after stalling at listener27 and did not pass; the cause is unknown. The separate passive-preload diagnostic and later official plain run both exited 0; the plain run left no owned listeners. These successful runs do not explain the earlier stall. The scoped native evidence also did not include a full Host visual review, so aesthetic polish may remain. No work is scheduled to address it under the pause.

## Future product work

Default future work to real reference-led flows:

- Faithful recreation from an actual supplied image, Figma node, or supported local reference file, with the target, fidelity needs, and editable-output constraints stated.
- Bounded Existing edits against an actual Figma file, page, or selected root, with preservation requirements and a review boundary.
- Cross-layout fidelity and resource handling—vectors, text, typography, and other media—when the user supplies the relevant reference and acceptance criteria.
- Packaging and releasing these reference-led capabilities after their own validation and review.

Do not infer that reference features as a whole are complete or optimized. Start a future task from its real reference input and target constraints; do not invent a Greenfield brief, reference, benchmark, or promotional example. A general design request without a reference does not restart no-reference Greenfield work.

## Evidence and retention

The timing record and its limits are in [GENERATION_TIMING_2026-10-08.md](GENERATION_TIMING_2026-10-08.md); the scoped native proof and cleanup details are in [GREENFIELD_NATIVE_HANDOFF_2026-10-08.md](GREENFIELD_NATIVE_HANDOFF_2026-10-08.md). Keep the older accepted reports, receipts, screenshots, source history, and tags unchanged. No new feature release was made by this stage closeout.

Local evidence pointers below are for repository audit; they are not public links:

- Native provenance SHA-256: `0b8c54a52137069cf44271c6c542105806d7e36ed20fcdbb6d63e8bee2211bc2`.
- Native-tree artifact SHA-256: `814af23c4c1b53bbd6cb5f792dcad475d0d91922f215eae5c9ee9f5088b8ee9b`; tree digest: `e805e804757e0e9c1a0b71bf26abb0514615f5327ad201305f28897fd2bf89a0`; artifact fingerprint: `635bb771605ac14804c88efe4e58c853b68986002df481ffd6bb4944da37c460`.
- Native PNG SHA-256: `ea5374dd91cc489d964f5dab04e7f09df0c8349b0968e8d5d04b0461dbda0fa5`; full-tree verification proof SHA-256: `977a667332df13c7332bcf6993cd69e6d6b14deea7194504c4310d89aa4a7e8f`.
- Plain verification log SHA-256: `d84f037f436ae6a5590bd23581d384189bfc5f2a1f849cec882a464d80870463`.

---

# Greenfield 暂停与阶段归档 · 2026-10-08

**状态：无参考 Greenfield 已暂停。** 2026-10-08，用户调整产品方向：从零创建设计的无参考工作流在本阶段完成有限收尾与证据归档后暂停开发。这是工作优先级决定，不是删除代码、停用工作流或修改 API 路由的要求。只有用户明确要求重启无参考 Greenfield 或提出具体例外时，才恢复相关工作。

边界根据是否有真实参考输入判断，而不是根据 route 或功能名里是否含有 `greenfield` 字符串。本次暂停只影响无参考 `workflow="greenfield"`。用户提供真实图片、Figma node 或其他受支持参考的 `reference_greenfield` 不受影响；基于用户提供的 Figma 文件、页面或选中节点的 Existing 编辑也不受影响。

## 已归档阶段与验证状态

归档的 code checkpoint 为 `08ef30426465d041a7c760fcfa84fd6ed7e54755`；验证时其 tracked source worktree clean。annotated archive tag `archive/greenfield-stage-2026-10-08` 指向该检查点，是阶段归档标记，不是正式版本或版本变更。此检查点引用不表示文档收尾后仓库 HEAD 保持不变。两次本地测试运行均 exit 0，结果相同：3,201 项测试、3,197 通过、4 跳过、0 失败、共 454 个套件。先是只运行测试的 passive-preload 诊断（384.773 s），之后是官方 plain `npm run verify`（387.477 s）。只有官方 plain run 完整执行 guard、TypeScript build 和 plugin build；其未使用 preload 或 `NODE_OPTIONS`，是唯一完整的本地 release gate。passive test-only 诊断不等同于全量 gate。4 个 skip 属于已批准边界：3 个 R06 local T12 fixture，以及 1 个因未设置 `FDR_REAL_MODEL` 而跳过的用例。

暂停不等于跳过测试。既有 Greenfield 测试仍属于必需的全量 release gate，不得删除、跳过或弱化；暂停期间不安排专门的无参考 Greenfield 测试、benchmark 或验收运行。未来有参考源码变更仍按常规要求执行全量验证门禁。

Root 检查 PNG 和完整树后，对范围内 native fixture 给出 `SCOPED_NATIVE_PASS`。对应 Host run 仍为 `REVIEW_REQUIRED`，`hostComplete=false`、`visualReviewSubmitted=false`；没有 Host `qualityReady` 结果。因此这里只关闭已记录的 fixture 范围。strict-empty 清理删除了本次 owned root，并确认页面 `282:1083` 无子节点、无 selection、无 locks、无 active transaction。页面 `212:2` 上受保护的 root `253:1518` 未触碰。

Tree artifact 有 129 个原生节点：67 TEXT、18 RECTANGLE、44 FRAME；ID 唯一、无 child-count mismatch、0 IMAGE、0 image fills。Artifact、root digest 和 PNG 校验匹配。Runtime 通过 6 次 supplemental reads 补回 21 个节点；artifact 把完整读回结果交付，避免 Host/Root 重复执行这些 helper reads，但不取消 runtime 自身读回。该 fixture 的原生输出因既有 compiler 行为遗漏三个 proposal headings；67 个实际 baseline text 节点均保留。该样本不证明每个 raw proposal string 都已渲染，也不代表 Host 工作流已完成。

Fixture replay 只将 alignment serialization 从 map 改成有序数组 `LEFT, LEFT, RIGHT, RIGHT, LEFT`；provenance 记录其他内容均与 source proposal 相同。这是范围内的规范化/重放检查，不是新设计任务或 benchmark，未使用旧 timing receipt。独立的 19:08.377 计时属于较早冻结源码 `f285dc0` 的 CLI/typed-bridge 运行，不属于 `08ef304`；它未达到此前使用的 15 分钟效率目标。入口不同，因此该结果不能支持 speedup claim，也不再作为 Greenfield 优化任务。

更早的 plain `npm run verify` 尝试卡在 listener27 后被停止，未通过；原因未知。独立的 passive-preload diagnostic 与之后官方 plain run 均 exit 0；plain run 没有遗留 owned listener。这些成功运行没有解释更早的停滞原因。本次范围内原生证据也没有完整 Host visual review，因此审美润色可能仍有不足。暂停期间不安排处理此项工作。

## 后续产品工作

未来默认面向有真实参考输入的工作流：

- 基于用户实际提供的图片、Figma node 或受支持的本地参考文件进行忠实复刻，并明确目标、保真要求和可编辑输出约束。
- 针对实际 Figma 文件、页面或选中 root 做范围受限的 Existing 编辑，并说明保留要求和复核边界。
- 在用户提供相关参考与验收标准后，处理跨版式 fidelity 及资源——向量、文字、字体排版和其他媒体。
- 这些参考路线各自完成验证与复核后，再封装和发布。

不要据此宣称 Reference 功能整体已完成或已优化。下一阶段应从真实参考输入和目标约束开始；不要自造 Greenfield brief、参考、benchmark 或宣传样例。若用户提出不带参考的一般设计需求，也不会自动恢复无参考 Greenfield 工作。

## 证据与保留

计时记录与边界见 [GENERATION_TIMING_2026-10-08.md](GENERATION_TIMING_2026-10-08.md)；范围内原生证明与清理事实见 [GREENFIELD_NATIVE_HANDOFF_2026-10-08.md](GREENFIELD_NATIVE_HANDOFF_2026-10-08.md)。旧验收报告、receipt、截图、源码历史与 tags 保持不变。本阶段收尾没有发布新功能版本。

以下本地证据指针用于仓库审计，不是公开链接：

- Native provenance SHA-256：`0b8c54a52137069cf44271c6c542105806d7e36ed20fcdbb6d63e8bee2211bc2`。
- Native-tree artifact SHA-256：`814af23c4c1b53bbd6cb5f792dcad475d0d91922f215eae5c9ee9f5088b8ee9b`；tree digest：`e805e804757e0e9c1a0b71bf26abb0514615f5327ad201305f28897fd2bf89a0`；artifact fingerprint：`635bb771605ac14804c88efe4e58c853b68986002df481ffd6bb4944da37c460`。
- Native PNG SHA-256：`ea5374dd91cc489d964f5dab04e7f09df0c8349b0968e8d5d04b0461dbda0fa5`；完整树验证 proof SHA-256：`977a667332df13c7332bcf6993cd69e6d6b14deea7194504c4310d89aa4a7e8f`。
- Plain verification log SHA-256：`d84f037f436ae6a5590bd23581d384189bfc5f2a1f849cec882a464d80870463`。
