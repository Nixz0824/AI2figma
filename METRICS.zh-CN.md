# AI2figma v0.4.10 指标与历史记录
中文 | [English](METRICS.md)

<a id="stage-closure-oct-8"></a>
## 10 月 8 日阶段收尾与有参考方向

无参考 `workflow="greenfield"` 开发在本阶段收尾后暂停；现有实现和证据保留。未来工作默认面向 Existing 编辑，以及基于用户真实参考的新页面。正式发布版本仍为 v0.4.10；本次文档快照不是新功能版本。

源码检查点 `08ef30426465d041a7c760fcfa84fd6ed7e54755` 上，官方 plain 本地 `npm run verify` 通过 3,201 项测试：3,197 通过、4 跳过、0 失败，共 454 个套件。Guard、TypeScript build 和 plugin build 均通过；该运行未使用 preload 或 `NODE_OPTIONS`。4 个 skip 为 3 个已批准的 R06 local T12 fixture，以及 1 个因未设置 `FDR_REAL_MODEL` 的 provider-gated 测试。另一次 passive-preload 诊断只运行了测试，不等同于完整本地 gate。

范围内原生 fixture 获得 `SCOPED_NATIVE_PASS`，但对应 Host 运行仍为 `REVIEW_REQUIRED`，且没有提交 Host visual review；这不是完整 Host 工作流，也没有 08ef304 的计时结果。另一项 19:08.377 测量属于冻结源码 `f285dc0`，未达到此前使用的 15 分钟效率目标；它不是受控对照，也不能作为 `08ef304` 的计时结论。

- [生成计时观测（10 月 8 日）](docs/GENERATION_TIMING_2026-10-08.md)
- [范围内原生交接（10 月 8 日）](docs/GREENFIELD_NATIVE_HANDOFF_2026-10-08.md)
- [Greenfield 暂停与阶段归档（10 月 8 日）](docs/GREENFIELD_PAUSE_2026-10-08.md)

<a id="first-reference-batch-oct-8"></a>
## 首批有参考优化（10 月 8 日）

这是 main 分支维护批次，聚焦真实参考输入，不改变正式 v0.4.10 版本。集成源码 HEAD `8eb298a5bc7e517d277f0da280225439c6e1b0a2` 于 2026-10-08 通过官方 plain 本地 `npm run verify`：3,222 项测试、3,218 通过、4 跳过、0 失败，共 456 个套件；耗时 404,787.1937 ms。这是本地验证结果，不是 GitHub CI。

| 范围 | 有界结果 | 边界 |
| --- | --- | --- |
| CLI 入口 | 参考输入使用 `fdr host start "<request>" --references-file <json>`。 | 公开文档统一使用这一入口；本地图片仍为本地输入。 |
| 密集文字定位 | 调用方选择启用 `rowPitchAware` 后，至少需要 3 条稳定测量 baseline 行及至少 2 个相似紧凑行距。本案例检查了 1×/2× 输入。 | 未匹配或多行文字保留原有边界、字体和内容；这不代表全面缩放独立性或覆盖所有参考图。 |
| Existing fixture RPC 数 | 在调用与查询相同的受控样例中，Bridge RPC 数从 9 次降到 6 次。 | 这是范围内的传输调用计数，不是端到端耗时结果或 benchmark 平均值。 |
| 截图 viewport | Host agent 检查用户提供的图片，并明确选择 viewport。画板完整且清楚时，用户无需另做干净导出。准备过程保留 `original.png`，并生成 `reference.png`、`references.json`、`lineage.json`；lineage 记录原图哈希和尺寸、`SOURCE_PIXEL` 矩形、派生图哈希及精确像素对应关系。 | 选择整图时按字节保留原图；完全相同的重跑新增写入为 0。候选不明确或被截断时保持未决，不猜测边界。裁图保留截图像素，不声称是原生 1× 导出。 |

原生工作流仍处于 `DECOMPOSITION_REQUIRED`；本批尚未向 Figma 绘制，没有 Native PASS 或已验收计时结果。最新一次 `continue` 请求（第三次，2026-10-08T15:33:17Z）在执行前被 automatic approval 的 usage/resource limit 阻断；这不是安全拒绝。无参考 Greenfield 暂停继续有效。本公开报告不包含用户截图、图标源文件或应用源码。

<a id="current-main-font-payload-oct-7"></a>
## 当前 main：限定字体查询载荷（10 月 7 日）

当前 main 的字体查询修复保持未限定查询的全局清单不变，并在请求某一字体家族时只返回匹配的标签。Figma 插件 READ 专项套件 26/26 通过，其中包含字体断言。对包含 18 个 Inter 字体样式及家族标签的响应进行离线序列化后，compact UTF-8 JSON 从 30,784 字节降至 749 字节（97.57%）；pretty JSON 从 41,532 字节降至 1,237 字节（97.02%）。18 个 Inter 字体样式全部保留。

<p align="center">
  <img src="assets/readme/font-payload-zh.svg" width="100%" alt="Inter 字体查询 compact JSON：限定家族标签后，载荷从 30,784 字节降至 749 字节，18 个字体样式均保留">
</p>

两条柱形条共用从零开始的线性 UTF-8 字节刻度；共同尺度上的长度便于准确比较（Cleveland 与 McGill，1984），零基线可避免柱长产生误导（Cairo，2019）。本地封存元数据输入的 SHA-256 为 `947ad6037d97d84447aad0f7941304db91b2bde6b4750bcc60b16aee32ca6c72`。

10 月 7 日另一次 E2E 计时尝试发生在此修复提交前，并在到达 Host 前被自动复核拒绝（`PRE_HOST_REQUEST_BLOCKED`）；没有生成设计或已验收计时。115,803 ms 仅是未完成的 pre-Host 观测，不计入生成耗时。v0.4.10 的 `12:40.816` 已验收样例保持不变。

<a id="current-main-existing-integrity-oct-7"></a>
## 当前 main：Existing 完整性与撤销 guard（10 月 7 日）

源码提交 `6576101` 增加了这项 guard，并包含此前 `c5f700e` 的字体查询修复。

| 源码范围 | 当前行为 | 边界或状态 |
| --- | --- | --- |
| Existing 修改 | 使用独立的 agent-lock 快照检查内容、样式与几何；保持 BEFORE/AFTER/rollback 捕获一致；在加锁前和撤销前检查；基线缺失或不完整时 fail closed。 | 不扩展 model context。这些快照不构成完全原子的并发用户修改排除机制。 |
| Existing 撤销 | 现有 `undo_last_agent_batch` 方法接受可选的 `expectedTransactionId`。Existing 传入自己记录的 ID；插件 handler 内部在 rollback 前核对，防止此流程撤销后来出现的其他事务。 | 方法数仍为 52。省略该 ID 的旧 `{}` 调用保持原有行为。 |
| 专项检查 | 专项 build 通过，专项套件 117/117 通过，覆盖 Existing 文本/样式/填充/边界/native-lock 漂移、深层叶节点、缺失或不可读基线下的 32-read 上限拒绝、BEFORE/AFTER 边界、纠正与 owned-KEEP rollback、无关锁和混合节点 ID、expected-undo 不匹配时不回滚、adapter 转发及选定的 reference 用例。 | 专项结果不替代完整发布门禁。 |
| 当前源码完整门禁 | production HEAD `657610181b1d1587fe7556c989c6b42d1a2a4a55` 上 `npm run verify` 通过 3,190 项测试、共 454 个套件：3,189 通过、1 跳过、0 失败。Guard、TypeScript build 和 plugin build 均通过。日志 SHA-256：`674118d66562997f94c4a89a93635e7c0d8a5b5485b9d4ee53c2c19f1f19b8ab`。 | `f4414ef` 上早先的 3,178 项结果属于有界移动端/Existing 复核，不是当前门禁总数。 |
| 部署状态 | 此前被拦截的 pre-Host 尝试之后，没有新的原生验收或已验收计时。字体响应和该 guard 都需要更新插件包。 | 当前连接的部署仍是 10 月 6 日插件包，尚未运行这一轮源码。 |

以上是源码行为描述；当前连接的插件尚未运行这一轮源码。

## v0.4.10 发布（2026-10-06）

canonical v0.4.10 标签指向提交 bfb8b8f2a7da987621d2103a0d69d247b7a9f3dc（414 个提交）。相较 v0.4.9，v0.4.10 包含通用演示内容披露、原生文本换行、响应式全局操作区和高严重度问题完成门禁。标签提交只增加本次验收记录；其生产目录与已验证的 4fea12d2511dc3f70a828b9322c84ee6993e8076 源码一致。当前统计为 538 个受版本控制的 TypeScript/TSX 文件、251,916 个 LF 分隔物理行，范围为 packages/、figma-plugin/、scripts/ 和 tests/。v0.4.9 正式标签保持不变。

通用生成路径根据解析出的演示内容来源增加一次 DEMO DATA 页面标题后缀，并保留原内容；长文本在已分配轨道内换行，全局顶栏操作适配响应式外壳；高严重度问题未解决时禁止完成。 默认由 AI 宿主负责推理的运行方式无需 provider API key；可选 provider 模式需另行配置。

- **4fea12d 生产源码完整验证：**3,105 项测试，3,104 通过、1 跳过、0 失败，共 453 个测试套件。Node 测试用时 385,593.2573 ms；命令总用时 388,356.2393 ms。回执 SHA-256：08ec103218bc0e65ca5efe268b14e6fcd3d5845f6ee5f8aec3a51e840cab7417。发布标签的生产目录与此已验证源码相同。
- **v0.4.10 私有镜像 main CI：**映射提交 5e932eee62adc07d821c94b1c1042c2c7c95a1b6；[run 37460767274](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460767274) 通过：3,099 项测试，3,083 通过、16 跳过、0 失败，共 453 个套件。Node 测试用时 378,394.047746 ms。日志 SHA-256：BC7BA27A6FA9BA31C6018578332B42E2757665B188C5FBE64F11E71DCD9103CF。
- **v0.4.10 私有镜像 tag CI：**同一映射提交；[run 37460770403](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460770403) 通过：3,099 项测试，3,083 通过、16 跳过、0 失败，共 453 个套件。Node 测试用时 383,879.596894 ms。日志 SHA-256：D8E9050E5ED6B7743752CC1E892D3C5149F5D9A2B1A9BF28A13A6772B6895EF2。
- canonical v0.4.10 标签映射到私有镜像 tag ref 90205406b29f87dcf8c6b725e83c270d7d90667b，剥离注释后指向镜像 main 5e932eee62adc07d821c94b1c1042c2c7c95a1b6。发布前的 4fea 源码维护 main CI 保留为历史记录：[run 37449461427](https://github.com/Nixz0824/AI2figma-source/actions/runs/37449461427)。

## 原生计时与审查结果

| 样例 | 耗时 | 计时终点 | 终态 | 完整性 | 回执 SHA-256 |
| --- | ---: | --- | --- | --- | --- |
| A · v0.4.8 | 17m30.088s | 记录的终态 | 超过 15 分钟上限后要求复核；未达到质量就绪 | VALID_MONOTONIC | 1151683F6F08A9DE7476BBC013AB96CA8F706AE6D07C59111F773BA4AF553111 |
| 0248B · candidate 0248 | 12m44.386s | 记录的终态 | 机器完成后仍需返工；Host 阶段计时缺失 | DEGRADED | F5DF30A741C4270584D8E014D141F9BDD74E46021D0FB8F523BD5FC7159BF058 |
| d8B2 · canonical d8 | 16m21.281s | 记录的终态 | 超过 15 分钟上限后要求复核；之后的视觉收尾不改写回执 | VALID_MONOTONIC | 657E3445A050BD4203F712AF51C7D4D8C879D3EF8FD4228558D39A86D2338C11 |
| 4fea · v0.4.10 源码 | 12m40.816s | 独立审查后达到质量就绪 | Host 完成，独立审查接受；目前唯一已验收的质量就绪计时点 | VALID_MONOTONIC | 5E2FE92709D5522D56D7C8096BA94AFE475D42A96F4575EE0C4C8F202B9B9453 |

前三次耗时截止于各自记录的终态。A 和 d8B2 实际超过 15 分钟上限；表中保留实测值，没有把上限值当作终点。4fea 的计时则在 Host 完成且独立审查接受后结束。前三次属于失败或降级观测，因此没有已验收的旧版与新版性能对照，不报告提速百分比或中位数。

已验收样例来自会话 e2e-lunamax-4fea-native-2026-10-06-01，运行在干净的 4fea12d2511dc3f70a828b9322c84ee6993e8076 源码上。会话于 2026-10-06T11:27:00.652Z 开始，在 2026-10-06T11:39:41.470Z 达到 qualityReady；连续总时长为 760,815.878 ms。Host 终态 COMPLETE，overall 为 84.52，没有 must-fix 项。visual_balance 仍有一项非阻塞 should-fix；另有 MAJOR 级诊断指出两个同级区块的视觉权重相同。一次 information_density 枚举选择在 Figma 写入前被拒绝，改为 compact；这段拒绝与修正时间保留在总时长内。计时回执中的 userAcceptance 为 null。

独立审查接受五项：必要信息、预算重点、可读性、表格对齐和原生图层可编辑。v0.4.10 当时的报告记录了 91 个原生节点和 0 个 IMAGE 节点，但其读回受到深度限制，详见下方更正。独立审查 PNG SHA-256：220919c0fed104aafdc2d66e51be7598e39b23a02a33cd756b669610516ac425；原树证据 SHA-256 仍为 a09242a4dd8aa929268595a847ae1c0795b81a5eb34687dd6e8666f91e09ee0b。

<a id="native-readback-correction-2026-10-07"></a>
## 原生树读回更正（2026-10-07）

91 是深度受限快照的返回数，不是既有 1440×900 画框 253:1518 的完整节点总数。10 月 7 日完整读回得到 112 个唯一节点、0 个图片节点、无截断。三个截断父节点下共有 21 个既有后代未返回：ChartScale（3 个）、ChartCanvas（11 个）和 ChartCategories（7 个）。探测为只读；这些节点不是本次新写入。历史视觉验收、12:40.816 计时、原复核 PNG 和上文树证明哈希均保持不变。完整树 SHA-256 为 188905c49142c730e0c6ea17a891b1437d02c4f32853d8afc03bd618111438d1；刷新后的 scale-one 截图 SHA-256 为 bc5fb66ae13cbcf7126f9d51de793ec24775afe574c6ece151399450b388c6c8。

连续时钟覆盖从请求到质量就绪。四段手动记录的 Host spans 共 194,887.494 ms；独立审查 spans 共 226,607.797 ms；runtime active 为 4,837.979 ms；Host waiting 为 555,796 ms；user wait 为 0 ms。手动 Host 与审查时段的并集覆盖连续总时长的 53.9%，其余 46.1% 未分类。这些时钟范围不同，不可相加；Host waiting 包含 reasoning 或 idle，不等于纯推理时间。没有把未分类时段归因于单一原因。

Host runtime commit 为干净的 4fea12d。加载的 Figma 插件 manifest 来自原始 candidate-0248 perf-oct6 部署；bundle 字节经核验与 d8、4fea 构建等价。会话记录的 plugin.sourceCommit=4fea12d 是 canonical 等价源码标注，不证明插件曾在 4fea12d 上重新构建或加载。Bundle SHA-256：a0afccd2cb438bf280d26d79ad3d06275456f6de1e5f955fd093fdf585feb25e。

<a id="current-main-metric-focus-oct-7"></a>
## 较早的 main 快照：主指标与完整树读回（2026-10-07）

代码快照 `06da0c4` 的 main 增加了显式主指标选择器和有界完整树读回。这是一次独立的合成数据 fixture 范围内原生复核，不是 v0.4.10 计时样例的新版对照。

| 证据 | 结果 |
| --- | --- |
| 主指标焦点 | `budget-today.primary_item_id=budget-remaining` 将“剩余预算” `$715.33` 设为主指标（Inter Bold 30 px）；“本月已用” `$1,284.67` 和“今日调用” `1,248 次` 保持次级（Inter Semi Bold 16 px）。 |
| 完整原生树 | 117 个唯一节点；读回完整；子节点计数缺口 0、图片节点 0。6 次补读补回 21 个节点。 |
| 复核状态 | 范围内独立复核：`SCOPED_NATIVE_PASS`。Host 运行仍处于 `REVIEW_REQUIRED` 的 `visual_review` 阶段，且未提交 Host 视觉复核。这不代表用户签收或整体最佳结论。 |
| canonical 验证 | 代码快照 `06da0c4` 上的本地 `npm run verify`：3,155 项测试，3,154 项通过、1 项跳过、0 项失败，共 454 个套件。 |
| 计时与后续项 | 没有新的端到端计时样例。需将图表零刻度与零基线对齐，并将表格数值列右对齐。 |

fixture 全部使用合成内容。本公开报告不包含 Figma 截图或源码。[canonical 详细报告](https://github.com/Nixz0824/AI2figma-source/blob/03ed440c86853d9b0e099de568250d2ac09d4b3e/docs/PRIMARY_METRIC_NATIVE_READBACK_2026-10-07.md)位于私有源码仓库，需要有权访问该仓库才能查看。

<a id="current-main-mobile-existing-oct-7"></a>
## 当前 main 移动端与 Existing 工作流复核（2026-10-07）

本更新描述干净的 canonical 源码 `f4414ef`、最初的移动端/Existing fixture 施工，以及另一次全新 scoped-placement smoke。首轮原生捕获使用 `41faa4a` HEAD、scoped-placement 源码 WIP 和编译运行时 manifest SHA-256 `93d300e3490bbc7c00f316e8ae8496d1f065f90412da6f2ba21cf19d3866e99c`；它不能证明任一提交对应的精确编译运行行为。新 smoke 的 runtime manifest SHA-256 为 `ce54d58dceebf439e361c3dc8fe2318965d23ccbb0aa5c8f413e0ca371b8dc7b`。这些都是有界 fixture 复核，不是新增的端到端计时运行。本页不包含原生截图或源码。

| 证据 | 结果 |
| --- | --- |
| 工作流 smoke | `PASS_READ_ONLY_SMOKE` 分别记录：Greenfield `PROPOSAL_REQUIRED`；Existing 对 root `253:1518` 返回 `REVIEW_REQUIRED`、phase `BEFORE`。两次 Figma 写入均为 0，页面和旧 root 保持不变；旧 `AUTO` 路由不变。 |
| Existing 目标筛选 | Existing start 只忽略精确的回滚 stash 组合：直接子节点 `type=FRAME`、`name=fdr:stash`、`visible=false`、`locked=true`。不会一概排除所有 frame 或所有隐藏/锁定节点。 |
| 移动端适配行为 | 绘图区预算至少 64 px，溢出时 fail closed；移动端按钮至少 44 px 高。保护逻辑不会缩小文字或丢弃数据，并保留 `gap` 等显式布局意图。这些是通用源码规则；原生复核只覆盖一个 fixture。 |
| 移动端 fixture | 在 390 × 844 画布上，root `275:778` 含 76 个节点、0 个图片节点；两条活动记录及 helper 均可见，CTA 为 90 × 44 px。Root 对内容/适配给出有限通过，并指出单独成行的 `DATA` 标题仍需打磨。 |
| Existing 修改 | 一次 `update_typography` 将节点 `275:847` 从 `20 分钟 · 07:35 · 合成训练记录` 改为 `25 分钟 · 07:35 · 合成训练记录`。完整 76 节点 raw readback 只发现该 `characters` 差异；重连后锁数为 0、无活动事务。Receipt SHA-256：`95b2cb45f13f31e8d34a43a74033edad2f8b75f3d61ffb4e7d6025ec65b98417`。 |
| 复核状态 | Root 看过 AFTER 图片后接受了有限的单字段修改。Host 状态为 `COMPLETE`、`strictComplete=true`，但 `deliverableReady=false`；`typography` 与 `professional_polish` 仍为 should-fix。Host 的 59 节点树摘要受深度限制且不含文字；单字段结论来自另一份完整 raw readback。AFTER PNG SHA-256：`ef24a5efa7746fa017607a7a203ac5cb0ac4915a37f612286a027d79770add3d`。 |
| 受保护页面与放置 | `movableNodeIds` 限定自动 frame 移动范围；Host 只传新 root ID。此前按名称排序曾将旧 root `253` 从 x=0 移到 x=550；经批准用两次类型化位置修改恢复。完整 112 节点旧 root 读回无差异；投影 SHA-256 为 `188905c49142c730e0c6ea17a891b1437d02c4f32853d8afc03bd618111438d1`，受保护 PNG SHA-256 为 `bc5fb66ae13cbcf7126f9d51de793ec24775afe574c6ece151399450b388c6c8`。这种手动恢复不等于自动放置通过。 |
| 新 scoped-placement smoke | 新 root `281:854` 自动放在 x=2700、y=0，与已修改 root `275:778` 相距 160 px。76 节点新页面保留两条活动 helper、五个图表柱及日期标签，CTA 为 90 × 44 px。旧 root `253` 和已修改 root `275` 的完整读回 raw diff 均为 `[]`，PNG 与基线一致。Root 有限认可适配与放置；完成 visual review 后，Host 为 `COMPLETE`、`strictComplete=true`、`deliverableReady=false`、overall 84.25，`typography` 与 `professional_polish` 仍为 should-fix，`userAcceptance=false`。自然名称顺序将新 `pkic` 排在 `8d2e` 之后，所以没有复现此前 lex-before 排序。Receipt SHA-256：`30f5d0d5b6b86bb24531f792b0bf5bfac5f4921f866f562d25e165550cea7c04`；scale-one PNG SHA-256：`6172f97b4f67da9d313b2467baa3c5fbe3e8354b61b6db542886013f7c7d64a1`。 |
| 本地验证 | 干净源码 `f4414ef` 上 `npm run verify` 在 454 个测试套件中完成 3,178 项：3,177 项通过、1 项跳过、0 项失败。 |
| 清理与计时 | 清理 receipt 记录一次原子 delete，仅删除本次拥有的 root `281:854` 和 `275:778`（`stashed=true`），随后以零操作 transaction retirement。最终页面只剩受保护的 root `253:1518`；其完整 112 节点投影和 PNG 与基线哈希一致。Bridge 无活动事务或锁。清理 receipt SHA-256：`a09cc3bd3d6b95b6abec7465df8984b45536934e836a87ec85ff33b435b06a80`。没有新的合格端到端计时样例或用户签收；4fea 的 12:40.816 仍是唯一已验收计时点，不支持提速结论。 |

## 另一次未计时的披露验证

另一次未计时运行 host_0muwk42jg1gn1bek 使用与原 B 提案字节一致的输入（SHA-256 581177dd3571030bc7c8a10aa936ec19927f151c784ca9e2647722ead8e596c3），生成页面标题“AI API 用量与费用控制台 · DEMO DATA”。独立审查接受五项检查；树有 104 个节点、0 个 IMAGE、无子节点数缺口。Host 的 strictComplete 为 true，但 deliverableReady 仍为 false。这是单页质量证据，不是计时样例。

用户完全退出并重启 Codex；Figma 与 plugin/Bridge 保持运行。旧 MCP 进程已退出；唯一新 MCP 进程 PID 23140 于 18:45:06 +08:00 启动，来自干净冻结的 4fea 构建，生成标题与本地 4fea 编译相符。此进程依据只用于说明该项有界未计时样例的来源。

acceptance-evidence-with-tree.json SHA-256：e39ba721462014fbf523b4e90b665009a2eac1a810d97380b6a943c1fc18409b；full-native-tree.json：9eb4f09ae7eb4a1e3d205d0e9b9f9ec2056abf61f44909305f3f86248c5898dd；greenfield.png：a0472a867fbf94b6c86da7aafe1d6a495764482032c0f022ea87f5fa1c136bae。公开文档不嵌入截图。

## v0.4.9 发布指标（历史）

v0.4.9 canonical 发布树有 402 个提交。该版本有 537 个受版本控制的 TypeScript 文件、250,786 个 LF 分隔物理行，涵盖 packages/ 下 13 个 workspace、figma-plugin、scripts/ 与 tests/。这不是仅生产代码的行数，也不是软件质量指标。

v0.4.9 canonical npm run verify：3,085 项测试，3,084 通过、1 跳过、0 失败，共 453 个套件。Guard、TypeScript build 和 plugin build 均通过。清理后的镜像 main 与 release tag CI 均通过。

## v0.4.9 文件与行数

| 范围 | 文件 | 行数 |
| --- | ---: | ---: |
| packages/core | 17 | 5,497 |
| packages/protocol | 51 | 34,863 |
| packages/design | 18 | 12,944 |
| packages/decision | 7 | 770 |
| packages/orchestrator | 63 | 58,210 |
| packages/tools | 6 | 1,504 |
| packages/bridge | 9 | 3,482 |
| packages/model | 14 | 3,601 |
| packages/memory | 4 | 1,083 |
| packages/browser | 7 | 1,388 |
| packages/cli | 5 | 1,792 |
| packages/mcp-server | 5 | 986 |
| packages/bench | 18 | 5,466 |
| figma-plugin | 22 | 4,777 |
| scripts | 71 | 23,815 |
| tests | 220 | 90,608 |
| **合计** | **537** | **250,786** |

## 历史验证

- **v0.4.9 canonical 完整验证：**3,085 项测试 / 3,084 通过 / 1 跳过 / 0 失败 / 453 套件；退出码 0。Oct 5 Node 测试用时 392,074.7201 ms。日志 SHA-256：345f45d08d21e8e4a52ef11d6a2fa5f27a2b7db21ab31546c0e1359d1547c59c。
- **v0.4.9 清理镜像 CI：**main 与 release tag 各运行 3,079 项测试 / 3,063 通过 / 16 跳过 / 0 失败 / 453 套件。main run 37313859741：382,873.79346 ms；tag run 37313862915：379,846.3941 ms。两者映射到清理后 HEAD 7e7857df949a526fc93a3c648084b6020920fd36。
- **v0.4.8 canonical 完整验证：**3,079 项测试 / 3,078 通过 / 1 跳过 / 0 失败 / 452 套件；退出码 0。Oct 5 Node 测试用时 390,027.6074 ms。
- **v0.4.8 清理镜像 CI：**main 与 release tag 各运行 3,073 项测试 / 3,057 通过 / 16 跳过 / 0 失败 / 452 套件。main run 37295332019：373,877.570165 ms，Actions job 约 411 秒；tag run 37295336675：374,256.20633 ms，job 约 412 秒。
- **v0.4.7 canonical 完整验证：**3,055 项测试 / 3,054 通过 / 1 跳过 / 0 失败 / 452 套件；退出码 0。
- **v0.4.7 清理镜像 CI：**3,049 项测试 / 3,033 通过 / 16 跳过 / 0 失败 / 452 套件。tag run 36902346689 与 main run 36902337954 均通过。
- **v0.4.6 清理镜像 CI：**3,007 项测试 / 2,991 通过 / 16 跳过 / 0 失败 / 452 套件；run 36832313819 通过。
- 清理镜像中的跳过项包括 provider-gated 检查，以及清理历史后本地 source input 被移除的检查。R6 test 2b 会先检查四个非 EXTERNAL 图片路径；缺失时精确报告并跳过，存在时继续运行字节、像素、EXACT_RENDERED 和 checked=4 断言。
- 决策影子层有 33 个专用测试、4 个观察点；运行时不依赖这些回答。
- 当前协议提供 52 个类型化 Figma 方法和 32 个 MCP 工具；系统共有 14 个工作区（packages/ 下 13 个，加 figma-plugin）。
- 一次真实移动端 ADAPTATION 案例按独立策略达到 ADAPTATION_COMPLETE，但 strictComplete=false；严格保真账本为 NOT_COMPARABLE_TARGET。这不构成严格保真通过。
- 每次变更都会在 CI 中运行完整测试套件。

## 功能范围

- 115 项参考重建支持矩阵（原生绘制 / 复用 / 转移 / 延后）
- 5 种平台外壳：桌面侧栏、顶部导航、单列、移动端堆叠、平板堆叠
- 区域保真账本提供确定性的像素指标：MAE、变更像素比例、亮度、边缘
- 资源落位：本地组件复用、Community 转移、媒体放置、轮廓矢量导入
- Host 工作流：修改现有页面、从需求建页、参考重建、参考适配
- 类型化决策影子记录路由、问题分级、风险门和修正重要性，并保留一致度、置信度、延迟、成本与校准报告；当前不驱动运行时动作

## 通用生成历史

- v0.4.7 的可选 visualTokens 把受支持的颜色与排版选择从 proposal 传到确定性 token 解析和原生构建。运行时核验精确字体 face，并应用字号、行高和字距。
- 原生文字构建会复用已加载字体 promise 和解析后的父节点。符合条件的 Host Reference Stage-A 候选读回与 PNG 导出经过批处理，减少该探测路径的传输往返。三场景 compiled-proposal 验证了原生参数、viewport、关系和包含关系；实测收益只限于候选读回与导出。
- Greenfield 页面根据 item 或 chart data 的演示内容标记生成一次 DEMO DATA 页面标题后缀，保留原 product type 与内容字段，并使用既有文本换行轨道。
- v0.4.9 Host planning 增加完整 start DTO、按运行状态保护的 continue，以及 proposal/review/plan 离线校验。MCP initialize 加 tools/list 从 41,238 bytes 降至 24,585 bytes，默认发现载荷减少 40.4%。reference guide 按需返回：文本 20,352 bytes，JSON-RPC 响应 20,600 bytes。这是上下文载荷指标，不是运行延迟或设计质量指标。
- v0.4.8 支持显式 chart data、受限表格/活动行/移动端布局，以及依赖内容、样式和几何证据的组件复用。组件复用在证据缺失时关闭。分组 section 保持原生顺序和标题边界。删除保护在写入前保护回滚 stash，并拒绝重叠的祖先/后代删除目标。两项固定 Native fixture 通过有限范围的树、文本、视口和精确回滚检查；这不证明整页设计质量或组件复用成功。
- Host visual closure：Oct 2 任务在 Oct 5 的计时窗口之后完成最终复审与只读捕获。独立审查接受了该范围内的结果，但该收尾未测时长。原始计时 receipt 仍为 REVIEW_REQUIRED、计时完整性降级，因此不构成速度或正常延迟证据。

## 历史 Host 视觉收尾与计时

Host 任务 host_0muqsigre0rrehmt 于 Oct 5 在计时结束后达到 COMPLETE。独立审查接受了有限结果；这是 Oct 2 任务的后续，不是新生成运行。收尾证明：.fdr/tmp/e2e-luna-max-2026-10-05-live/quality-closure-oct5.json，SHA-256 4e54ce6e3af69358aa5e5ae28ecf5148b1ba0812693ab140cf8d0514888bd69a。

根 frame 为 1440×900；其 1008×630 精确字节导出 SHA-256 为 f3516354cdbefaa252ec5a4310fc5c21c37cec3ca9202b0382b845b3b4719d85。审查确认 DEMO DATA 标签、预算值、七个趋势日期与柱、五条对齐记录、视口适配及原生可编辑元素。仍有低严重度图表轴线/网格对齐项。只读收尾未发现活动事务、锁或新改动。本次 Oct 5 收尾没有耗时或提速测量。

Oct 2 计时观察回执以 REVIEW_REQUIRED 和 TIME_CAP_15_MIN 结束，计时完整性为 DEGRADED。Host planning spans 包含依赖工具误用和等待。原始失败回执保持不变，也不测量 Oct 5 的计时后完成结果。

## 已知限制

- 不支持 URL 参考；仅处理本地 PNG/JPEG/WebP 和 Figma 节点。
- Community 组件、照片、图标等资源需要人工提供。
- Greenfield 图表需要明确标签、单位和有限数值；缺少 chartData 时显示无数据状态，格式错误或非有限数值会被 schema 拒绝。带正负值的坐标域中，零点不生成柱；合法全零序列保留零基线标记。
- 外部 blind holdout 当前失败；原始结果保存在私有仓库中。
- 同图视觉评分受模型判断影响，观测到的重复评估波动约为 ±7.5。
- 活动行和表格在有界宽度内换行；窄屏移动端活动行堆叠。当前 Native fixture 仅覆盖固定控制台和正负边界案例；图表轴线与网格对齐仍有 P2 polish 项。

## 相关文档

- [English homepage](README.md)
- [中文主页](README.zh-CN.md)
- [架构说明（英文）](ARCHITECTURE.md)
- [评估许可](LICENSE)
