# Product direction and roadmap · 2026-10-21

English | [简体中文](#中文路线)

This public roadmap summarizes the active product direction. It is not a release schedule; each step depends on verified evidence and the required Figma or human-review access.

## Active scope

- **Reference-led pages:** use an actual supplied image or Figma material, preserve source identity, build supported content as editable native layers, and report unresolved assets or evidence.
- **Existing edits:** inspect a supplied Figma page or selected nodes, scope the change, apply typed operations, and verify the result.
- **Paused legacy path:** no-reference `workflow="greenfield"` development remains paused. The existing implementation is retained. A new page built from a real supplied reference remains active.

## Near-term order

1. Explain source-text comparability per text element, reusing the existing source-ink measurement path. Missing evidence must remain explicit rather than being treated as a visual pass or failure.
2. Align the shared meaning of target layout ownership, parent flow, and resolved positioning across planning, construction, and readback. Start with a field already reproduced in real input; leave unknown cases to existing readback checks.
3. Keep repeated evidence qualification and artifact checks in small shared modules, while the orchestration layer coordinates stage state and persistence.
4. Validate on a representative real-reference task. Report editable adaptation, strict fidelity, and human acceptance as separate results.
5. Measure whole-task time from input preparation through canvas closeout, including feedback time, correction rounds, and blockers. Compare only tasks with compatible inputs and acceptance scope.

The current weighted estimate and the latest verified clock observations are in [METRICS](METRICS.md) and [指标](METRICS.zh-CN.md). They do not create a target date or relax any acceptance condition.

## Outcome boundaries

An editable result or `ADAPTATION_COMPLETE` does not by itself prove strict source fidelity. `NOT_COMPARABLE` means the evidence cannot establish a strict comparison; it is neither a visual pass nor a confirmed rendering defect. A model review score is not human acceptance. Only the user or an explicitly designated human reviewer can accept the specific reviewed capture.

## Release and source access

The product remains v0.4.10; this roadmap is documentation, not a new release. The canonical source is maintained privately and its scrubbed snapshot is available to authorized users in the [private source repository](https://github.com/Nixz0824/AI2figma-source). This public repository contains product documentation and conceptual diagrams, not application source or private design evidence.

---

## 中文路线

本公开路线图概述当前产品方向，不是发布日期承诺；各项工作取决于可核验证据以及所需的 Figma 或人工评审条件。

### 当前范围

- **基于真实参考的新页面：**使用用户实际提供的图片或 Figma 材料，保持来源身份，将支持的内容构建为可编辑原生图层，并明确记录尚未解决的素材和证据。
- **Existing 修改：**检查用户提供的 Figma 页面或选中节点，限定修改范围，通过类型化操作执行，并读回验证。
- **已暂停的历史路径：**无参考 `workflow="greenfield"` 开发继续暂停，现有实现保留；基于真实参考的新页面仍在范围内。

### 近期顺序

1. 复用现有源图 ink 测量路径，逐个文字说明来源墨迹可比性；证据缺失时明确标记，不把它当作视觉通过或失败。
2. 在计划、施工与读回之间统一目标布局 owner、父级 flow 和解析后定位的共用含义。先处理真实输入中已复现的字段；事实未知时继续使用原读回检查。
3. 将重复的证据资格和 artifact 检查留在小型共享模块，由 orchestrator 协调阶段状态与持久化。
4. 使用有代表性的真实参考任务验证。可编辑适配、严格保真和人类验收分开报告。
5. 从输入准备记录到画布收口的整轮时钟，并记录首次反馈、修正轮次和阻断；只比较输入和验收范围相符的任务。

当前固定权重估计和最新可核验时钟见[指标](METRICS.zh-CN.md)及[英文指标](METRICS.md)。它们不是发布日期目标，也不降低任何验收条件。

### 结果边界

可编辑结果或 `ADAPTATION_COMPLETE` 本身不证明严格源保真。`NOT_COMPARABLE` 表示证据不足以完成严格比较；它既不是视觉通过，也不是已确认的渲染缺陷。模型 review 分数不等于人类验收。只有用户或明确指定的人类评审者能接受某一份具体复核 capture。

### 发布与源码访问

正式产品仍为 v0.4.10；本路线图是文档更新，不是新版本。Canonical 源码保持私有，脱敏快照向获授权的用户提供于[私有源码仓库](https://github.com/Nixz0824/AI2figma-source)。本公开仓库展示产品文档与概念图，不包含应用源码或私人设计证据。
