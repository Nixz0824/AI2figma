# Source text measurement 2.4.0 — 2026-10-10

> Verified component checkpoint; Native verification is pending. The published product remains v0.4.10 and no new product tag was created. This report covers offline source-pixel evidence only; it does not record live calibration, Native acceptance, or end-to-end timing.

## English

The source candidate `53f514a` passed the recorded local release gate `npm run verify`: 3,271 tests, 3,267 passed, 4 skipped, 0 failed across 459 suites. Node test-runner duration was 385,066.363 ms; this measures the test runner, not application or end-to-end time. The gate ran with approved elevated execution and `TEMP`, `TMP`, and `TMPDIR` set to a temporary directory inside the workspace. It covered unit/contract tests and a local fake Bridge loopback; it used no live Host, Figma, or external publish. The receipt records this gate at 2026-10-09T17:13:58.680Z; at that recorded point, the published product remained v0.4.10 and no new product tag had been created.

Source measurement 2.4.0 treats the bound `textEvidence.sourceRect` as a source-pixel allocation window and keeps semantic bounds as the layout and `sourceLineBox` geometry. Each raw window is bound to the primary source and its text, checked within the painted ancestor, then converted to an effective raster window by rounding shared edges once with `Math.round`. Both raw and resolved windows bind the measurement fingerprint. Overlapping pixel domains fail closed. A 24-window offline check measured all 24 windows with zero failures and zero Figma probe calls. During the source-only measurement phase there were also zero artifact writes and zero probe-image reads; the JSON diagnostic report was saved separately. This did not create a renderer calibration or Native acceptance record.

The fractional-pixel regression checks the actual History fragments: 9/12 px vertical overlap and a 1 px horizontal gap yield the complete 140×16 source ink, starting at pixel x=17 for raw x=17.08. A merchant window at raw x=67.1813 resolves to pixel 67. Merchant/date windows meeting at raw y=756.0813 both resolve that edge to pixel 756 and remain disjoint; windows that claim the same raster pixel are rejected. The 3-window Show Details/Add/Withdraw fixture confirms that the Show window excludes the nearby eye and that flow-owned target bounds remain semantic.

Overlapping root TEXT pixels are attributed only when one measured ink window, the actual text paint, and a supported painted ancestor agree. Blank frame/root margins remain surface pixels, not extra glyph ink. The watcher update uses a consistent elapsed-time origin for continuous spans and leaves interrupted boundaries unknown; it corrects measurement integrity but supplies no new end-to-end duration.

Native verification for v2.4 is pending. No final derived root, accepted Native result, or v2.4 live/end-to-end timing is recorded. The earlier v2.2 `PARTIAL` child, the v2.3 calibration timing observation (about 80 seconds), and the October 8 snapshot / October 7 correction history remain separate historical records. The v2.4 offline result does not retroactively change those outcomes.

## 中文

源码候选 `53f514a` 通过记录在案的本地 release gate `npm run verify`：3,271 项测试，3,267 通过、4 跳过、0 失败，共 459 个套件。Node test-runner 用时为 385,066.363 ms；这是测试运行器耗时，不是应用或端到端耗时。该 gate 使用经批准的 elevated execution，并将 `TEMP`、`TMP`、`TMPDIR` 指向 workspace 内的临时目录。检查范围为 unit/contract 测试与本地 fake Bridge loopback；没有使用 live Host、Figma 或外部发布。回执记录该 gate 的时间为 2026-10-09T17:13:58.680Z；在该记录时点，已发布产品仍为 v0.4.10，且尚未创建新产品 tag。

源码测量版本 2.4.0 将绑定的 `textEvidence.sourceRect` 作为来源像素分配窗口，并继续使用语义 bounds 作为布局及 `sourceLineBox` 几何。每个 raw 窗口先绑定 primary source 和可见文字、核验位于 painted ancestor 内，再按 `Math.round` 对共享边界只量化一次，生成有效栅格窗口。Raw 与解析后的窗口都绑定 measurement fingerprint。争用同一栅格像素的窗口 fail closed。24 个窗口的离线检查全部测得，失败为 0，Figma probe 调用为 0；source-only 测量阶段的 artifact 写入和 probe image 读取也为 0，JSON 诊断报告另行保存。本次没有生成 renderer calibration 或 Native 验收记录。

小数像素回归使用实际 History 字形片段：9/12 px 纵向重叠与 1 px 水平间隙合并成完整的 140×16 来源 ink，raw x=17.08 从像素 x=17 开始。Merchant 窗口 raw x=67.1813 解析到像素 67。Merchant/date 窗口在 raw y=756.0813 相接，两侧统一解析到像素边界 756 并保持不重叠；争用同一栅格像素的窗口会被拒绝。Show Details/Add/Withdraw 三窗口 fixture 证明 Show 窗口排除了附近 eye 图标，并且 flow-owned target bounds 仍是语义几何。

重叠 root TEXT 像素只有在唯一测量 ink 窗口、实际文字填充和受支持的 painted ancestor 一致时才会归属到文字。空白 frame/root 余量仍是表面像素，不会额外算作字形。Watcher 更新让连续 span 使用一致的 elapsed-time 起点，中断的边界保持 unknown；它修复测量完整性，但没有提供新的端到端耗时。

v2.4 Native verification 仍待进行。尚未记录最终 derived root、已接受的 Native 结果或 v2.4 live/端到端计时。此前 v2.2 `PARTIAL` child、v2.3 约 80 秒的校准历史观测，以及 10 月 8 日 snapshot / 10 月 7 日 correction 历史均继续作为独立旧记录。v2.4 离线结果不会追溯更改这些历史结果。
