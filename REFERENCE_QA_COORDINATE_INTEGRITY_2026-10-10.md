# Reference baseline QA and coordinate integrity — 2026-10-10

> The combined source corrections are integrated at code checkpoint `8a3f6b653163e5f9fa21f95b7e6612b34fafe874`. Its local `npm run verify` passed 3,274 tests (3,270 passed, 4 skipped, 0 failed; 459 suites); Node test-runner duration was 392,952.6874 ms, not application or end-to-end time. The post-fast-forward build passed. The fresh Native run received technical visual review but remains `CORRECTION_REQUIRED`; strict fidelity is 0/8. Only partial stage and observed interval timings are available, with no accepted total-generation timing or final acceptance. The formal product version remains v0.4.10; no new product tag was created.
>
> 组合源码修复已集成于检查点 `8a3f6b653163e5f9fa21f95b7e6612b34fafe874`。本地 `npm run verify` 通过 3,274 项测试（3,270 通过、4 跳过、0 失败；459 个套件）；Node test-runner 用时 392,952.6874 ms，不是应用或端到端耗时。fast-forward 后的 build 通过。修复后的 Native 运行已完成技术画面复核，但状态仍为 `CORRECTION_REQUIRED`，strict fidelity 为 0/8。当前仅有部分阶段耗时和观测区间，没有已接受的总生成耗时或最终验收。正式产品仍为 v0.4.10，未创建新产品 tag。

## English

### Baseline text QA

For two comparable text elements, baseline QA compares their declared `bounds.y` origins when both are non-empty, single-line HUG text and explicitly share `fontFamily`, `fontSize`, `fontWeight`, `lineHeight`, `letterSpacing`, and `textAlign`. Different or incomplete typography, empty or multiline text, and fixed/FILL sizing continue to use the existing box-center check. The change is limited to the baseline drift comparison; it does not change other QA rules.

### Coordinate identity and prior Reference diagnostic

The protocol validates AUTO coordinates by exact forward identity, `origin + local === expected`. Non-AUTO coordinates keep the strict reverse identity check. No floating-point tolerance was added, and the existing 0.5 px physical write gate is unchanged.

The preceding Reference diagnostic classified all 12 flows as AUTO, and icon write-side page bounds passed the 0.5 px physical gate. Its receipt's maximum arithmetic reconstruction delta is `2.48689957516035065e-14 px`; this is not a measured Figma position error. Separate Figma position evidence reports a maximum deviation of approximately `0.00017518 px`. Strict protocol round-trip artifact validation rejected the coordinate identity because of floating-point representation, producing `RECONCILIATION_REQUIRED`. That run is historical and is not formal Native acceptance.

### Fresh post-fix Native run

The fresh run reached technical visual review (`REVIEWED`), but its final status is `CORRECTION_REQUIRED`. Vector verification was `14/14 VECTOR_VERIFIED` with no failures. A depth-6 tree readback plus a separate GROUP readback returned 101 unique nodes: 46 FRAME, 30 VECTOR, 24 TEXT, and 1 GROUP. The readback showed 24 editable single-line HUG text nodes, 14 native SVG assets, zero IMAGE nodes or image paint, and two native gradients. These structure and asset checks do not establish strict visual fidelity.

The external-raster check passed 8/8. Live text-construction parity passed 23/24 rows; the one failing cardholder-text row had ambiguous ink ownership and color families. This is separate from the offline v2.4 source-measurement result. Strict `fidelityV2` passed 0/8 and failed 8/8; 18 root TEXT glyphs were `NOT_COMPARABLE`, with 38 ancestor occurrences across those 18 unique texts. All eight V2 failures stem from incomparable text-ink evidence, not a pixel-threshold miss; `strictComplete` is false. One proposed one-operation correction conflicts with the supplied source style and role token, so it was not approved; seven regions remain unhandled. The current canvas remains a technical review candidate, not a formally accepted result.

Construction took 3.427 s and the asset-call stage took 5.668 s. The Host SDK active-call sum was 92.365 s, excluding auxiliary checks. The observed checkpoint interval was 36 min 10.345 s and includes planning, reviews, waits, and the `CORRECTION_REQUIRED` pause. These are partial stage and checkpoint measurements, not an accepted total-generation duration or a successful end-to-end sample. No before/after comparison or speedup is claimed.

### Text sizing and flow planning lesson

An observed source/ink rectangle describes painted source evidence; it is not the target text layout size. In the Oct 10 review, 19 single-line TEXT elements inside flow parents were semantically HUG, but `MEASURED_OBSERVATION` owned both dimensions. Their effective sizing became FIXED and the text wrapped. Assigning `AUTO_LAYOUT` as the owner compiled the intended `WIDTH_AND_HEIGHT` sizing as HUG.

Before calibration or a write, review effective sizing against its owner and check the parent flow's available capacity. This is a planning check, not a rule that all TEXT must use HUG: fixed-width and multiline text remain valid when intentional and supported by the flow. This finding concerns plan assembly; it does not change the separate v2.4 source-measurement evidence, which keeps source ink windows distinct from semantic layout bounds.

### Release boundary

The full `npm run verify` on the combined code checkpoint passed 3,274 tests: 3,270 passed, 4 skipped, 0 failed, across 459 suites. Its 392,952.6874 ms Node test-runner duration measures test execution only, not application or end-to-end time. The subsequent fast-forward to canonical was followed by a successful build. This is local source verification, not GitHub CI. The fresh Native run remains `CORRECTION_REQUIRED`; its stage and checkpoint measurements are not accepted total-generation timing. This report does not claim final Native acceptance or end-to-end speedup. The formal product version remains v0.4.10; no new product tag was created.

## 中文

### 基线文字 QA

对于可比较的两个文字元素，只有在两者均为非空、单行、HUG，且显式共享 `fontFamily`、`fontSize`、`fontWeight`、`lineHeight`、`letterSpacing` 和 `textAlign` 时，基线 QA 才比较声明的 `bounds.y` 原点。排版属性缺失或不同、文字为空或多行、以及固定/FILL 尺寸仍走原有的框中心检查。本次只改变 baseline drift 比较，不改变其他 QA 规则。

### 坐标身份与此前 Reference 诊断

组合源码检查点为 `8a3f6b653163e5f9fa21f95b7e6612b34fafe874`，包含基线文字原点 QA 修复和 AUTO 坐标精确身份修复。AUTO 坐标现通过严格正向恒等式 `origin + local === expected` 校验；非 AUTO 坐标保留严格的反向恒等式检查。不新增浮点容差，现有 0.5 px 实际写入门禁不变。

此前的 Reference 诊断中 12 个 flow 均判定为 AUTO，图标写入侧的 page bounds 通过 0.5 px 实物门禁。该回执的最大算术重构差为 `2.48689957516035065e-14 px`，它不是 Figma 位置误差；另一份 Figma 位置证据报告的最大偏差约为 `0.00017518 px`。protocol strict round-trip artifact 校验曾因浮点表示误拒坐标身份，导致状态为 `RECONCILIATION_REQUIRED`。该运行是历史诊断，不是正式 Native 验收。

### 修复后的 Native 运行

新运行已完成技术画面复核（`REVIEWED`），最终状态为 `CORRECTION_REQUIRED`。Vector verification 为 `14/14 VECTOR_VERIFIED`，失败为 0。depth-6 树读回加一次独立 GROUP 补读，共得到 101 个唯一节点：46 FRAME、30 VECTOR、24 TEXT 和 1 GROUP。读回包含 24 个可编辑单行 HUG 文字节点、14 个原生 SVG 素材、0 个 IMAGE 节点或 image paint，以及 2 个原生渐变。这些结构和素材检查不证明严格视觉保真。

External-raster 检查 8/8 通过。Live text-construction parity 为 23/24 通过；唯一失败的 cardholder-text 行因 ink ownership 和 color family 不明确。该检查与离线 v2.4 源码测量结果分开记录。严格 `fidelityV2` 为 0/8 通过、8/8 失败；18 个 root TEXT glyph 为 `NOT_COMPARABLE`，涉及这 18 个唯一文本的 38 次 ancestor occurrence。8 项 V2 失败都来自不可比较的 text-ink 证据，并不表示像素阈值未达标；`strictComplete=false`。一项拟议的单操作修正与用户提供的 source style 和 role token 冲突，未获批准；仍有 7 个区域未处理。当前画布只是技术复核候选，不是正式验收结果。

Construction 阶段用时 3.427 秒，asset-call 阶段用时 5.668 秒。Host SDK active-call 累计为 92.365 秒，不含辅助检查。观测区间为 36 分 10.345 秒，其中包含规划、复核、等待以及 `CORRECTION_REQUIRED` 暂停。这些是部分阶段和观测区间耗时，不是已接受的总生成耗时或完整成功的端到端样例；没有前后对比或提速结论。

### 文字尺寸与 flow 规划经验

观测到的 source/ink 矩形描述来源中实际绘制的文字证据，不是目标文字布局尺寸。10 月 10 日复核发现，19 个位于 flow 父容器内的单行 TEXT 在语义上为 HUG，但宽、高两个方向都由 `MEASURED_OBSERVATION` 持有，因此 effective sizing 变成 FIXED 并发生换行。将 owner 改为 `AUTO_LAYOUT` 后，预期的 `WIDTH_AND_HEIGHT` 才按 HUG 编译。

校准或写入前，应核对 effective sizing 与其 owner 是否一致，并检查父级 flow 的可用容量。这是通用计划检查项，不是要求所有 TEXT 都使用 HUG：设计意图明确且 flow 容量足够时，固定宽度和多行文字仍然合理。本次发现属于计划组装；它不改变独立的 v2.4 源码测量证据。v2.4 报告仍将 source ink 窗口与语义布局 bounds 分开处理。

### 发布边界

组合源码检查点 `8a3f6b653163e5f9fa21f95b7e6612b34fafe874` 的完整 `npm run verify` 通过 3,274 项测试：3,270 通过、4 跳过、0 失败，共 459 个套件。Node test-runner 用时 392,952.6874 ms，仅代表测试运行器耗时，不是应用或端到端耗时；随后 fast-forward 到 canonical 后的 build 也通过。这是本地源码验证，不是 GitHub CI。修复后的 Native 运行仍为 `CORRECTION_REQUIRED`；其阶段及观测区间耗时不是已接受的总生成计时。本报告不宣称 Native 验收完成或端到端提速。正式产品仍为 v0.4.10，未创建新产品 tag。
