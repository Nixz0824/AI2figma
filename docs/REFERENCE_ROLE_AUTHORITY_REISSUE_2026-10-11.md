# Reference role-authority reissue — 2026-10-11

> Latest integrated code checkpoint `ab7bc578b5b74a215aa9e83817f06f6a17531379` (tree `670d01c7b017573f4ec21e5f91b8d9c84923ab73`) passed local `npm run verify`: 3,296 tests across 465 suites, 3,292 passed, 4 skipped, 0 failed. This is local source verification, not GitHub CI or live acceptance. The published product remains v0.4.10, with no new product tag.

## English

| Area | Record | Boundary |
|---|---|---|
| Current local gate | `ab7bc578b5b74a215aa9e83817f06f6a17531379`, tree `670d01c7b017573f4ec21e5f91b8d9c84923ab73`; 3,296 tests / 465 suites, 3,292 passed, 4 skipped, 0 failed. | Local source verification only; not GitHub CI. |
| V2.3 vector evidence | The settled sidecar binds icon/vector identity and position evidence to the reference source hash and target capture/pose. | Existing runs are not retrofitted with a newly introduced sidecar. |
| Fill authority | Fill values are bound to approved hard `ROLE_TOKEN` authority and the target's complete paint evidence. | A reissue cannot approve an unapproved target or turn a strict `FAIL` into a pass. |
| Earlier reissues | Attempts on `a9f6448`, `8ebe59d`, and `d9aa6df` were refused at successive readback gates; later diagnostics traced them to verifier context, omitted settled-icon bounds, and legal `VERTICAL` Auto Layout reflow after icon insertion. | These remain failed historical attempts. The failure-time `CORRECTION_REQUIRED` snapshot is preserved; the final reviewed snapshot is separately `HUMAN_ACCEPTED`. |
| Settled icon and Auto Layout guard | `ab7bc57` binds settled icon identity to fresh-tree root-local bounds and accepts same-pose `AUTO_LAYOUT` reflow only when the approved parent flow, owner, and fresh capture agree. | Static, unknown-owner, parent, size, paint, capture, or nonempty binding changes still reject; no protocol, original image, or raw paint fingerprint was changed. |
| Capability reissue | Capability advanced from 1.2 to 1.3. Runtime returned `unavailable` / `NO_ACTIONABLE_CORRECTION_FAMILY` after one echo and opened `HUMAN_ACTION_REQUIRED` / `reference_human_acceptance`. | Total operations 0; capture matched; Figma/model/vision writes and calls were 0, transaction null, locks 0, mutations 0. |
| Human acceptance | Original capture `2ba5…` is recorded as `HUMAN_ACCEPTED`; all 20 eligibility checks passed under `HOST_REFERENCE_NO_ACTIONABLE_CORRECTION`. Receipt SHA-256: `95aca656211a4bebcb95463c9a111c7aedba8ff1f825e0d8a129d72b47551ca5`. | This accepts the reviewed capture only; `strictV2Pass=false`, so it is not strict `COMPLETE`. Later canvas edits require their own captures and receipts. |
| Preserved run state | Old and active capability/ledger bytes remain unchanged; correction round is 0. The local `reference-human-review-packet-1.json` records the accepted capture. | Packet, screenshot, and raw receipts remain local-only. |
| Product release | v0.4.10 remains the published version; no new tag is planned. | Local source verification is not GitHub CI or a product release. |

Same-day process history: local full gates passed at `a9f6448`, `df846f0`, `8ebe59d`, `d9aa6df`, and `ab7bc57`; earlier refusals stayed fail-closed, and the final accepted snapshot was recorded on `ab7bc57`.

After acceptance, the user separately requested matching the pale board's four corners to the black cards; one typed radius edit changed 0 to 54.65599822998047, preserved other geometry and the accepted snapshot, and produced a separate capture (SHA-256 `2644aebc8e7d554dbd2c43d164d841395c94d068fe38f788b86b41814c834df3`) and local receipt (SHA-256 `d59c84c2a5cbcaf0e0564253d69680821b97a7bcfeb45732bd09e03e42592435`).

The read-only diagnostics checked the stored baseline tree, plan-relevant live parent, geometry and text, the authority target's complete paint, capture and hash, settlement, source, and approval. `receipt.liveTreeReadbackFingerprint` proves the approved target readback; it is not a fingerprint of every node in the 101-node live tree and does not establish that unrelated hidden nodes did not drift.

The prior capability 1.2 bytes and embedded `fidelityV2` 2.2 contract remain intact; the newly issued capability is 1.3. The historical source-calibration record marked `PARTIAL` is separate; no prior run is overwritten or retrofitted with the new sidecar. The v2.4 source-measurement record and Oct 10 coordinate-integrity report also remain separate historical evidence. See the [Oct 10 coordinate-integrity report](../REFERENCE_QA_COORDINATE_INTEGRITY_2026-10-10.md) and [v2.4 source-measurement report](../REFERENCE_TEXT_MEASUREMENT_2026-10-10.md).

The signed review snapshot is `HUMAN_ACCEPTED`, but strict visual completion remains unproven: text ink is incomparable, and the prior V2 ledger lacks asset-node ink bindings for 14 unique icons and marks. V2.3's settled sidecar does not backfill that immutable ledger; no successful total-generation run or genuine before/after comparison is recorded. Unique historical records and evidence remain preserved, and cleanup was limited to rebuildable paths listed in a local ignored receipt. Unknown and unique `.fdr` evidence remains untouched, and the Oct 6 inventory remains a dated snapshot rather than a current count. This report contains no user image, SVG, source-code bundle, or `.fdr` artifact.

## 中文

> 最新源码检查点 `ab7bc578b5b74a215aa9e83817f06f6a17531379`（tree `670d01c7b017573f4ec21e5f91b8d9c84923ab73`）通过本地 `npm run verify`：465 个套件、3,296 项测试，3,292 通过、4 跳过、0 失败。这是本地源码验证，不是 GitHub CI 或 live 验收。已发布产品仍为 v0.4.10，未计划创建新产品 tag。

| 范围 | 记录 | 边界 |
|---|---|---|
| 最新源码 gate | `ab7bc578b5b74a215aa9e83817f06f6a17531379`，tree `670d01c7b017573f4ec21e5f91b8d9c84923ab73`；465 个套件、3,296 项测试，3,292 通过、4 跳过、0 失败。 | 仅为本地源码验证，不是 GitHub CI。 |
| V2.3 vector evidence | settled sidecar 将图标/vector identity 与 position evidence 绑定到 reference source hash 及 target capture/pose。 | 不为既有运行追补新引入的 sidecar。 |
| Fill authority | 填充值绑定到已批准的 hard `ROLE_TOKEN` authority 与目标完整 paint evidence。 | reissue 不能批准未批准的目标，也不能把 strict `FAIL` 改成通过。 |
| Earlier reissue attempts | `a9f6448` 因 verifier context/坐标误报 stale；`8ebe59d` 的 2 项 pending button readback 来自漏掉的 settled direct `ICON` bounds；`d9aa6df` 的 tab-label 差异是插入图标后的合法 `VERTICAL` reflow。 | 这些是失败历史，不代表当前验收状态；失败时点的 `CORRECTION_REQUIRED` 快照予以保留，最终复核快照另记为 `HUMAN_ACCEPTED`。 |
| Capability reissue | Capability 从 1.2 更新到 1.3；runtime echo 一次后返回 `unavailable` / `NO_ACTIONABLE_CORRECTION_FAMILY`，打开 `HUMAN_ACTION_REQUIRED` / `reference_human_acceptance`。 | total operations 为 0；capture 匹配，Figma/model/vision writes 与 calls 均为 0，transaction null、locks 0、mutations 0。 |
| Human acceptance | 原 capture `2ba5…` 记录为 `HUMAN_ACCEPTED`；20/20 eligibility checks 在 `HOST_REFERENCE_NO_ACTIONABLE_CORRECTION` 下通过。Receipt SHA-256：`95aca656211a4bebcb95463c9a111c7aedba8ff1f825e0d8a129d72b47551ca5`。 | 仅接受复核 capture；`strictV2Pass=false`，不是 strict `COMPLETE`。之后画布变化需独立 capture 与 receipt。 |
| 保留状态 | 旧/active capability 与 ledger bytes 未改变；`correctionRound=0`。本地 `reference-human-review-packet-1.json` 记录已接受 capture。 | Packet、截图与原始 receipt 留在本地，不发布 `.fdr`。 |
| Settled icon / AUTO guard | `ab7bc57` 将 verified settlement identity 绑定到 fresh QualityTree node/parent/root 与 allowed-SVG-wrapper root-local bounds，并验证同 capture 下的 approved `AUTO_LAYOUT` parent/owner 后才允许合法 reflow。 | STATIC、unknown owner、parent/size/paint/capture drift 仍拒绝；empty `boundVariables` 可规范化，非空 binding 保持严格；不改色彩权限、旧 ledger、源图或 raw paint fingerprint。 |
| 产品发布 | 已发布版本仍为 v0.4.10；不计划创建新 tag。 | 本地源码验证不是 GitHub CI，也不是产品发布。 |

同日过程：`a9f6448`、`df846f0`、`8ebe59d`、`d9aa6df` 与 `ab7bc57` 的本地 full gate 均通过；早期实际 reissue 曾因 verifier context、settled icon bounds 和合法 Auto Layout reflow 拒绝，失败时点的 `CORRECTION_REQUIRED` 快照按历史保留；最终 `ab7bc57` capture 获用户正式接受。

验收后，用户另行要求将浅色画板的四角圆角调整为与黑色卡片一致；一次 typed radius edit 将数值从 0 改为 54.65599822998047，其他几何和已验收快照均保持不变，并生成独立的新 capture（SHA-256 `2644aebc8e7d554dbd2c43d164d841395c94d068fe38f788b86b41814c834df3`）与本地 receipt（SHA-256 `d59c84c2a5cbcaf0e0564253d69680821b97a7bcfeb45732bd09e03e42592435`）。

只读诊断核验了 stored baseline tree、与 plan 相关的 live parent、geometry 和 text、authority 目标的完整 paint、capture 与 hash、settlement、source 和 approval。`receipt.liveTreeReadbackFingerprint` 证明的是已批准目标的 readback；它不是 101 节点 live tree 中每个节点的指纹，也不能证明无关隐藏节点没有漂移。

既有 capability 1.2 bytes 与 embedded `fidelityV2` 2.2 契约保持原样；新发出的 capability 为 1.3。标为 `PARTIAL` 的历史 source-calibration 记录是独立记录；不会覆盖此前运行，也不会给它们追补新 sidecar。v2.4 源码测量记录与 10 月 10 日坐标完整性报告继续作为独立历史证据保留。详见[10 月 10 日坐标完整性报告](../REFERENCE_QA_COORDINATE_INTEGRITY_2026-10-10.md)与[v2.4 源码测量报告](../REFERENCE_TEXT_MEASUREMENT_2026-10-10.md)。

已签收的复核快照为 `HUMAN_ACCEPTED`，但 strict visual completion 未证明：text ink 不可比较，旧 V2 ledger 也缺少 14 个唯一图标/标记的 asset-node ink binding。V2.3 settled sidecar 不会追补旧 immutable ledger；没有成功的总生成运行或真实前后对照。独有历史记录与证据继续保留，有限清理只针对本地 ignored receipt 列出的可重建路径。未知项和独有 `.fdr` 证据均未动；Oct 6 inventory 仍是带日期的快照，不代表当前数量。本报告不包含用户图片、SVG、源码包或 `.fdr` artifact。
