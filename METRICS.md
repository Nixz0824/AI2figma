# METRICS — AI2figma v0.4.10 — generic native content and layout correctness
English | [简体中文](METRICS.zh-CN.md)

<a id="reference-qa-coordinate-integrity-2026-10-10"></a>
## Reference QA and coordinate integrity (Oct 10, 2026)

The combined source checkpoint is `8a3f6b653163e5f9fa21f95b7e6612b34fafe874`. It includes the baseline text-origin QA and exact AUTO-coordinate identity corrections. The full local gate passed on the same commit and tree before fast-forward to canonical; the post-fast-forward build also passed. The formal product remains v0.4.10; no new product tag is recorded.

| Evidence | Current result | Boundary |
|---|---|---|
| Combined code verification | `npm run verify` exit 0; 3,274 tests, 3,270 passed, 4 skipped, 0 failed; 459 suites. Node test-runner duration: 392,952.6874 ms. | Same code commit/tree as `8a3f6b6`; duration is test-runner time only, not application or end-to-end time. Post-fast-forward canonical build exited 0. This is not GitHub CI. |
| Comparable text baseline | Matching, explicit typography on non-empty single-line HUG text uses the shared declared y origin; incomplete/different evidence and potentially wrapping text retain the existing box-center check. | Baseline drift QA only. |
| AUTO coordinate identity | Exact forward check: `origin + local === expected`; non-AUTO keeps strict reverse identity. | No tolerance was added; the 0.5 px physical write gate is unchanged. |
| Prior Reference diagnostic | 12 flows were AUTO; icon write-side page bounds passed the 0.5 px physical gate. The receipt's maximum arithmetic reconstruction delta was `2.48689957516035065e-14 px`; separate Figma position evidence reports a maximum deviation of about `0.00017518 px`. | The arithmetic delta is not a measured Figma position error. Strict protocol round-trip artifact validation rejected coordinate identity; this run remains historical `RECONCILIATION_REQUIRED` evidence. |
| Fresh Native outcome | Technical visual review `REVIEWED`; state `CORRECTION_REQUIRED`; 14/14 vector checks `VECTOR_VERIFIED`; external-raster 8/8 PASS. | Not formal acceptance. |
| Live text-construction parity | 23/24 rows passed; one cardholder-text row failed due to ambiguous ink ownership and color families. | Separate live construction check; the offline v2.4 source-measurement record remains separate. |
| Strict fidelity | `fidelityV2` 0/8 PASS, 8/8 FAIL; 18 root TEXT glyphs `NOT_COMPARABLE`. | All 8 failures stem from non-comparable text-ink evidence (38 ancestor occurrences across 18 unique texts), not a pixel-threshold miss; `strictComplete=false`. |
| Open correction | One cap operation conflicts with the source style/role token; 7 regions remain unhandled. | Unapproved and not applied; current status remains `CORRECTION_REQUIRED`. |
| Partial timing | Construction 3.427 s; asset-call stage 5.668 s; Host SDK active-call sum 92.365 s; observed checkpoint interval 36 min 10.345 s. | The interval includes planning, review, waits, and the correction pause. These are partial measurements, not accepted total-generation timing; no before/after or speedup claim. |

An observed source/ink rectangle describes painted source evidence, not target text layout size. In the Oct 10 review, 19 single-line TEXT elements inside flow parents were semantically HUG but both dimensions were owned by `MEASURED_OBSERVATION`, making their effective sizing FIXED and causing wraps. `AUTO_LAYOUT` ownership compiled the intended `WIDTH_AND_HEIGHT` sizing as HUG. Review effective sizing against its owner and check parent-flow capacity before calibration or writes. This is not a rule that every TEXT must be HUG; fixed-width and multiline text remain valid when intentional. The source-measurement record remains separate and unchanged. See the [dated report](REFERENCE_QA_COORDINATE_INTEGRITY_2026-10-10.md).

<a id="source-text-measurement-2026-10-10"></a>
## Source text measurement 2.4.0 (Oct 10, 2026)

The recorded local release gate was `npm run verify`; it ran with approved elevated execution and workspace-local `TEMP`, `TMP`, and `TMPDIR` at the time recorded in the receipt (2026-10-09T17:13:58.680Z). The product version remains v0.4.10; no new product tag is recorded. This is not a GitHub CI result.

| Evidence | Current state |
|---|---|
| Local release gate | 3,267 passed, 0 failed, 4 skipped (3,271 tests; 459 suites). |
| Offline source windows | 24/24 measured, 0 failed. During the source-only measurement phase: 0 probe calls, 0 artifact writes, 0 probe-image reads; the JSON diagnostic report was saved separately. |
| Live v2.4 verification | Pending; no accepted Native result is recorded. |
| Final canvas | Pending review; no accepted final canvas is recorded. |
| End-to-end timing | None recorded for v2.4. |

`textEvidence.sourceRect` allocates source pixels; semantic bounds continue to define line boxes and target layout. Shared edges are rounded once, adjacent windows remain disjoint, and real pixel conflicts fail closed. Root TEXT pixels are attributed only when the measured ink window, actual paint, and painted ancestor agree; blank margins remain surface pixels. The [dated report](REFERENCE_TEXT_MEASUREMENT_2026-10-10.md) has the fractional-window and watcher details. No speedup or A/B claim is made.

<a id="stage-closure-oct-8"></a>
## Stage closure and reference-first scope (Oct 8, 2026)

No-reference `workflow="greenfield"` development is paused after this stage closeout; its existing implementation and evidence are retained. Default future work to Existing edits and new pages built from an actual supplied reference. The formal release version remains v0.4.10; this documentation snapshot is not a new feature release.

At source checkpoint `08ef30426465d041a7c760fcfa84fd6ed7e54755`, the official plain local `npm run verify` passed 3,201 tests: 3,197 passed, 4 skipped, 0 failed, 454 suites. Guard, TypeScript build, and plugin build passed; the run used no preload or `NODE_OPTIONS`. The four skips are three approved R06 local T12 fixtures and one provider-gated test because `FDR_REAL_MODEL` was unset. A separate passive-preload diagnostic ran tests only; it is not equivalent to this full local gate.

The scoped native fixture received `SCOPED_NATIVE_PASS`, while its Host run remained `REVIEW_REQUIRED` and did not submit a Host visual review. It is not a completed Host workflow and has no timing result. The separate 19:08.377 timing measurement belongs to frozen source `f285dc0`, exceeded the previously used 15-minute efficiency target, and is not a controlled comparison or timing claim for `08ef304`.

- [Generation timing observation (Oct 8)](docs/GENERATION_TIMING_2026-10-08.md)
- [Scoped native handoff (Oct 8)](docs/GREENFIELD_NATIVE_HANDOFF_2026-10-08.md)
- [Greenfield pause and stage archive (Oct 8)](docs/GREENFIELD_PAUSE_2026-10-08.md)

<a id="first-reference-batch-oct-8"></a>
## First reference-led optimization batch (Oct 8)

This main-branch maintenance batch focuses source work on actual references; it does not change the formal v0.4.10 release. The production source remains at HEAD `8eb298a5bc7e517d277f0da280225439c6e1b0a2`. The latest source/test checkpoint, `0b3fccdb6ea0948ae204159c801b0580f6a848bf`, changes one test fixture only. This metadata correction was recorded on 2026-10-09 (Asia/Shanghai); the batch date remains Oct 8.

| Verification record | Source identity | Result |
| --- | --- | --- |
| Latest local plain full gate | Tree `b56f09bcbc4f831be6cd79c21eac9fa83f99430f`; test checkpoint `0b3fccdb6ea0948ae204159c801b0580f6a848bf` | `npm run verify` passed 3,222 tests: 3,218 passed, 4 skipped, 0 failed, 456 suites. Node test-runner duration: 390,863.402 ms. This is not application generation time or total command wall time. |
| Private mirror exact verification | Commit `17d502bb97a7feb111bfc0b7696c158f42a3fde2`; [successful CI run 37808800764](https://github.com/Nixz0824/AI2figma-source/actions/runs/37808800764) (private repository; access may be required) | 3,216 tests: 3,200 passed, 16 skipped, 0 failed, 456 suites. Node test-runner duration: 392,466.348923 ms. |
| Initial Oct 8 local full gate | Production HEAD `8eb298a5bc7e517d277f0da280225439c6e1b0a2` | 3,222 tests: 3,218 passed, 4 skipped, 0 failed, 456 suites. Historical Node test-runner duration: 404,787.1937 ms; not application generation time or total command wall time. |

The earlier mirror CI run 37805692910 failed because the scrubbed mirror did not contain its private T12 image fixture. Checkpoint `0b3fccd` replaces that test dependency with neutral self-contained RGBA; no production source files changed. The original image and earlier receipt remain preserved. The test-runner durations above are not generation timings.

| Area | Scoped result | Boundary |
| --- | --- | --- |
| CLI entry | Reference input uses `fdr host start "<request>" --references-file <json>`. | One documented entry; local image paths remain local inputs. |
| Dense text placement | Caller-opt-in `rowPitchAware` placement uses at least three stable measured baseline rows and two or more similar compact row pitches. The scoped checks cover 1×/2× inputs. | Unmatched or multiline text retains original bounds, font, and content. This is not a claim of scale independence or coverage of every reference. |
| Existing fixture RPC count | Under the same controlled call and query, Bridge RPC count fell from 9 to 6. | A scoped transport count, not an end-to-end time result or benchmark average. |
| Screenshot viewport | The host agent inspects the supplied image and selects an explicit viewport. A clear, complete artboard does not require a user-created clean export. Preparation preserves `original.png` and writes `reference.png`, `references.json`, and `lineage.json` with the source hash, dimensions, `SOURCE_PIXEL` rectangle, derived hash, and exact pixel correspondence. | A whole-image selection is a byte-preserving no-op; exact replay adds zero writes. Ambiguous or clipped candidates remain unresolved instead of being guessed. The crop preserves screenshot pixels and does not claim a native 1× export. |

The native workflow remains `DECOMPOSITION_REQUIRED`; this batch has not drawn to Figma and has no Native PASS or accepted timing result. The latest `continue` request (the third, at 2026-10-08T15:33:17Z) was blocked before execution by the automatic approval usage/resource limit; this was not a safety rejection. The no-reference Greenfield pause remains in force. This public report includes no user screenshot, source icon, or application source code.

<a id="current-main-font-payload-oct-7"></a>
## Current main: scoped font-query payload (Oct 7)

The current-main font-query fix keeps the unscoped inventory unchanged and returns only labels matching a requested family. The focused Figma plugin READ suite passed 26/26; font assertions are included in it. Offline serialization of the 18 Inter face records and their labels reduced compact UTF-8 JSON from 30,784 to 749 bytes (97.57%); pretty JSON fell from 41,532 to 1,237 bytes (97.02%). All 18 Inter faces remain in the response.

<p align="center">
  <img src="assets/readme/font-payload-en.svg" width="100%" alt="Compact Inter font-query response: 30,784 bytes before and 749 bytes after scoping labels, with all 18 Inter faces preserved">
</p>

Bars share a zero-based linear byte scale. Common-scale length supports accurate comparison (Cleveland & McGill, 1984), and the zero baseline keeps bar lengths honest (Cairo, 2019). The local sealed metadata input has SHA-256 `947ad6037d97d84447aad0f7941304db91b2bde6b4750bcc60b16aee32ca6c72`.

An Oct 7 E2E timing attempt that predates this fix was rejected by automatic review before Host (`PRE_HOST_REQUEST_BLOCKED`). No design or accepted timing resulted; its 115,803 ms pre-Host window is an incomplete observation and is not counted as generation timing. The existing v0.4.10 `12:40.816` accepted sample remains unchanged.

<a id="current-main-existing-integrity-oct-7"></a>
## Current main: Existing integrity and undo guard (Oct 7)

Source commit `6576101` adds this guard and includes the earlier `c5f700e` font-query fix.

| Source surface | Current behavior | Limit or status |
| --- | --- | --- |
| Existing edits | Checks content, style, and geometry using separate agent-lock snapshots; keeps BEFORE/AFTER/rollback captures coherent; checks before lock and before undo; fails closed when the baseline is missing or incomplete. | Adds no model context. The snapshots do not make exclusion of concurrent user edits fully atomic. |
| Existing undo | The existing `undo_last_agent_batch` method accepts optional `expectedTransactionId`. Existing supplies its captured ID; inside the plugin handler, it is checked before rollback, preventing this flow from undoing a later foreign transaction. | The method count remains 52. Legacy `{}` callers that omit the ID keep their behavior. |
| Focused checks | The focused build passed and the focused suite passed 117/117. Coverage includes Existing text/style/fill/bounds/native-lock drift, deep leaves, bounded baseline-read refusal, BEFORE/AFTER brackets, correction and owned-KEEP rollback, unrelated locks and mixed node IDs, expected-undo mismatch without rollback, adapter forwarding, and selected-reference cases. | Focused results do not replace the full release gate. |
| Final source gate | At production HEAD `657610181b1d1587fe7556c989c6b42d1a2a4a55`, `npm run verify` passed 3,190 tests across 454 suites: 3,189 passed, 1 skipped, 0 failed. Guard, TypeScript build, and plugin build passed. Log SHA-256: `674118d66562997f94c4a89a93635e7c0d8a5b5485b9d4ee53c2c19f1f19b8ab`. | The earlier 3,178-test result at `f4414ef` belongs to the bounded mobile/Existing review and is not the current gate total. |
| Deployment | No new native acceptance or accepted timing followed the earlier pre-Host blocked attempt. Both the font-response change and this guard need an updated plugin bundle. | The connected deployment remains the Oct 6 bundle; it has not exercised this source wave. |

These are source-level behavior claims. The current connected plugin has not exercised this source wave.

## v0.4.10 release (Oct 6 2026)

Canonical v0.4.10 tag points to bfb8b8f2a7da987621d2103a0d69d247b7a9f3dc (414 commits). Compared with v0.4.9, v0.4.10 includes generic demo-provenance disclosure, shared native wrapping, responsive global header actions and the high-severity completion gate. The final tag commit adds only this accepted-sample report to canonical source 4fea12d2511dc3f70a828b9322c84ee6993e8076; the tag runtime-production directories match that already-verified source. The current inventory is 538 tracked TypeScript/TSX files and 251,916 LF-delimited physical lines across packages/, figma-plugin/, scripts/ and tests/. The v0.4.9 release tag remains unchanged.

The generic generation path derives one DEMO DATA page-title suffix from parsed demo-content provenance, preserves source content, wraps long text in allocated tracks, adapts global header actions, and blocks completion while high-severity findings remain. The default mode uses the AI host for reasoning and needs no provider API key; optional provider modes are configured separately.

- **Canonical production-source verification at 4fea12d:** 3,105 tests / 3,104 passed / 1 skipped / 0 failed / 453 suites. Node test duration: 385,593.2573 ms; command duration: 388,356.2393 ms. Receipt SHA-256: 08ec103218bc0e65ca5efe268b14e6fcd3d5845f6ee5f8aec3a51e840cab7417. The release-tag production directories are identical to this verified source.
- **v0.4.10 scrubbed mirror main CI:** mapped HEAD 5e932eee62adc07d821c94b1c1042c2c7c95a1b6; [run 37460767274](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460767274) passed 3,099 tests / 3,083 passed / 16 skipped / 0 failed / 453 suites. Node test duration: 378,394.047746 ms. Log SHA-256: BC7BA27A6FA9BA31C6018578332B42E2757665B188C5FBE64F11E71DCD9103CF.
- **v0.4.10 scrubbed mirror tag CI:** the same mapped HEAD; [run 37460770403](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460770403) passed 3,099 tests / 3,083 passed / 16 skipped / 0 failed / 453 suites. Node test duration: 383,879.596894 ms. Log SHA-256: D8E9050E5ED6B7743752CC1E892D3C5149F5D9A2B1A9BF28A13A6772B6895EF2.
- The canonical v0.4.10 tag maps to scrubbed mirror tag ref 90205406b29f87dcf8c6b725e83c270d7d90667b, peeled to mirror HEAD 5e932eee62adc07d821c94b1c1042c2c7c95a1b6. The pre-release source-maintenance main CI remains historical: [run 37449461427](https://github.com/Nixz0824/AI2figma-source/actions/runs/37449461427).

## Native timing and review results

| Observation | Elapsed | Endpoint | Outcome | Integrity | Receipt SHA-256 |
| --- | ---: | --- | --- | --- | --- |
| A · v0.4.8 | 17m30.088s | Recorded terminal state | Review required after the 15-minute cap; not quality-ready | VALID_MONOTONIC | 1151683F6F08A9DE7476BBC013AB96CA8F706AE6D07C59111F773BA4AF553111 |
| 0248B · candidate 0248 | 12m44.386s | Recorded terminal state | Machine complete, then independent rework required; Host timing span missing | DEGRADED | F5DF30A741C4270584D8E014D141F9BDD74E46021D0FB8F523BD5FC7159BF058 |
| d8B2 · canonical d8 | 16m21.281s | Recorded terminal state | Review required after the 15-minute cap; later visual closure did not rewrite the receipt | VALID_MONOTONIC | 657E3445A050BD4203F712AF51C7D4D8C879D3EF8FD4228558D39A86D2338C11 |
| 4fea · v0.4.10 source | 12m40.816s | Quality-ready after independent review | Host complete; review accepted; one accepted quality-ready timing point | VALID_MONOTONIC | 5E2FE92709D5522D56D7C8096BA94AFE475D42A96F4575EE0C4C8F202B9B9453 |

The first three elapsed times end at their recorded terminal states. A and d8B2 actually ran longer than the 15-minute cap; the table preserves those observations rather than substituting the cap value. The 4fea clock ends only after Host COMPLETE and independent review acceptance. The first three are failed or degraded observations, so there is no accepted old/new pair, speedup percentage, or median.

The accepted session was e2e-lunamax-4fea-native-2026-10-06-01 on clean runtime commit 4fea12d2511dc3f70a828b9322c84ee6993e8076. It started at 2026-10-06T11:27:00.652Z and reached qualityReady at 2026-10-06T11:39:41.470Z: 760,815.878 ms total. Host state was COMPLETE, overall 84.52, with no must-fix item. visual_balance remained a non-blocking should-fix item; an overdesign diagnostic also marked equal visual weight between two sibling sections as MAJOR. An information-density enum choice was rejected before Figma writes, corrected to compact, and counted in the elapsed time. The receipt userAcceptance field is null.

Independent review accepted five checks: required information, budget focus, readability, table alignment, and native editable elements. The contemporaneous v0.4.10 report recorded 91 native nodes and 0 IMAGE nodes, but its readback was depth-limited; see the correction below. The accepted review PNG SHA-256 is 220919c0fed104aafdc2d66e51be7598e39b23a02a33cd756b669610516ac425; the original tree-proof SHA-256 remains a09242a4dd8aa929268595a847ae1c0795b81a5eb34687dd6e8666f91e09ee0b.

<a id="native-readback-correction-oct-7"></a>
## Native readback correction (Oct 7, 2026)

The 91-node figure is the count returned by a depth-limited snapshot, not the complete count in the existing 1440×900 frame 253:1518. A complete Oct 7 readback found 112 unique nodes, 0 image nodes, and no truncation. Three cutoff parents omitted 21 existing descendants: ChartScale (3), ChartCanvas (11), and ChartCategories (7). The probe was read-only; these nodes were not newly written. The accepted visual result, 12:40.816 timing, original review PNG, and historical tree-proof hash above remain unchanged. The full-tree SHA-256 is 188905c49142c730e0c6ea17a891b1437d02c4f32853d8afc03bd618111438d1; the refreshed scale-one capture SHA-256 is bc5fb66ae13cbcf7126f9d51de793ec24775afe574c6ece151399450b388c6c8.

The continuous clock is request-to-qualityReady. The four manually bracketed Host spans total 194,887.494 ms; Root review spans total 226,607.797 ms; runtime active is 4,837.979 ms; Host waiting is 555,796 ms; user wait is 0 ms. Manual Host/Root span union covers 53.9% of the full clock; 46.1% remains unclassified. These clocks have different scopes and are not additive. Host waiting includes reasoning or idle time and is not pure inference. No single cause is assigned to the unclassified remainder.

The Host runtime commit was clean 4fea12d. The loaded plugin manifest came from the original candidate-0248 perf-oct6 deployment; its bundle bytes were verified equivalent to the d8 and 4fea builds. The session plugin.sourceCommit value of 4fea12d is a canonical-equivalence annotation, not evidence that the plugin was rebuilt or reloaded at 4fea12d. Bundle SHA-256: a0afccd2cb438bf280d26d79ad3d06275456f6de1e5f955fd093fdf585feb25e.

<a id="current-main-metric-focus-oct-7"></a>
## Earlier main snapshot: metric focus and complete readback (Oct 7, 2026)

At code snapshot `06da0c4`, main added an explicit primary-metric selector and bounded complete-tree readback. This separate synthetic-data fixture is a scoped native review, not a timed successor to the v0.4.10 sample.

| Evidence | Result |
| --- | --- |
| Metric focus | `budget-today.primary_item_id=budget-remaining` selected Remaining `$715.33` as primary (Inter Bold 30 px); Used `$1,284.67` and Calls `1,248` remained secondary (Inter Semi Bold 16 px). |
| Complete native tree | 117 unique nodes; complete readback; 0 child-count gaps and 0 image nodes. Six supplemental reads supplied 21 nodes. |
| Review state | Scoped independent review: `SCOPED_NATIVE_PASS`. The Host run remained `REVIEW_REQUIRED` at `visual_review`, with no Host visual review submitted. This is not user acceptance or an overall-best claim. |
| Canonical verification | Local `npm run verify` at code snapshot `06da0c4`: 3,155 tests; 3,154 passed, 1 skipped, 0 failed across 454 suites. |
| Timing and follow-up | No new end-to-end timing sample. Align the chart zero tick with its zero baseline and right-align numeric table columns. |

All fixture content was synthetic. No Figma screenshot or source code is included in this public report. The [detailed canonical report](https://github.com/Nixz0824/AI2figma-source/blob/03ed440c86853d9b0e099de568250d2ac09d4b3e/docs/PRIMARY_METRIC_NATIVE_READBACK_2026-10-07.md) requires access to the private source repository.

<a id="current-main-mobile-existing-oct-7"></a>
## Current-main mobile and Existing workflow review (Oct 7, 2026)

This update describes clean canonical source `f4414ef`, an initial mobile/Existing fixture exercise, and a separate fresh scoped-placement smoke. The initial native capture used `41faa4a` HEAD plus scoped-placement source WIP and compiled runtime manifest SHA-256 `93d300e3490bbc7c00f316e8ae8496d1f065f90412da6f2ba21cf19d3866e99c`; it does not prove exact compiled behavior for either commit. The fresh smoke used runtime manifest SHA-256 `ce54d58dceebf439e361c3dc8fe2318965d23ccbb0aa5c8f413e0ca371b8dc7b`. These are bounded fixture reviews, not a new timed end-to-end run. No native screenshot or source code is included here.

| Evidence | Result |
| --- | --- |
| Workflow smoke | `PASS_READ_ONLY_SMOKE` records separate results: Greenfield `PROPOSAL_REQUIRED`; Existing `REVIEW_REQUIRED` at phase `BEFORE` for root `253:1518`. Both made 0 Figma writes; the page and old root stayed unchanged. Legacy `AUTO` routing remains unchanged. |
| Existing target filter | Existing start omits only the exact rollback-stash tuple: a direct child with `type=FRAME`, `name=fdr:stash`, `visible=false`, and `locked=true`. It does not blanket-exclude all frames or all hidden/locked nodes. |
| Mobile fit behavior | Mobile plot budget is at least 64 px and overflow fails closed; mobile buttons are at least 44 px high. The guards do not shrink text or discard data, and preserve explicit layout intent such as `gap`. These are general source rules; native review covered one fixture. |
| Mobile fixture | At 390 × 844, root `275:778` contains 76 nodes and 0 image nodes; both activity records and helper text are visible, and the CTA is 90 × 44 px. Root gave a limited content/fit pass and flagged the isolated `DATA` heading as a polish item. |
| Existing edit | One `update_typography` operation changed node `275:847` from `20 分钟 · 07:35 · 合成训练记录` to `25 分钟 · 07:35 · 合成训练记录`. A complete 76-node raw readback found only that `characters` diff; reconnect showed 0 locks and no active transaction. Receipt SHA-256: `95b2cb45f13f31e8d34a43a74033edad2f8b75f3d61ffb4e7d6025ec65b98417`. |
| Review state | Root accepted the limited single-field edit after reviewing the AFTER image. Host reports `COMPLETE` and `strictComplete=true`, with `deliverableReady=false`; `typography` and `professional_polish` remain should-fix. The Host's 59-node tree digest is depth-limited and omits text; the one-field result comes from the separate complete raw readback. AFTER PNG SHA-256: `ef24a5efa7746fa017607a7a203ac5cb0ac4915a37f612286a027d79770add3d`. |
| Protected page and placement | `movableNodeIds` scopes automatic frame movement; Host supplies only the new root ID. A prior name-sort regression moved old root `253` from x=0 to x=550; recovery used two authorized typed position edits. The complete 112-node old-root readback had no differences; its projection SHA-256 is `188905c49142c730e0c6ea17a891b1437d02c4f32853d8afc03bd618111438d1` and protected PNG SHA-256 is `bc5fb66ae13cbcf7126f9d51de793ec24775afe574c6ece151399450b388c6c8`. This manual recovery is not a passing automatic-placement result. |
| Fresh scoped-placement smoke | Root `281:854` was placed at x=2700, y=0 with a 160 px gap after edited root `275:778`. The 76-node new frame retained both activity helpers, five bars/date labels, and its 90 × 44 px CTA. Complete readbacks for old root `253` and edited root `275` both had raw diff `[]` and PNGs matching their baselines. Root accepted limited fit/placement. After visual review, Host reported `COMPLETE`, `strictComplete=true`, `deliverableReady=false`, overall 84.25, with `typography` and `professional_polish` still should-fix and `userAcceptance=false`. The natural name order placed new `pkic` after `8d2e`, so this did not reproduce the earlier lex-before ordering. Receipt SHA-256: `30f5d0d5b6b86bb24531f792b0bf5bfac5f4921f866f562d25e165550cea7c04`; scale-one PNG SHA-256: `6172f97b4f67da9d313b2467baa3c5fbe3e8354b61b6db542886013f7c7d64a1`. |
| Local verification | On clean source `f4414ef`, `npm run verify` completed 3,178 tests across 454 suites: 3,177 passed, 1 skipped, 0 failed. |
| Cleanup and timing | The cleanup receipt records one atomic delete of only owned roots `281:854` and `275:778` (`stashed=true`), followed by a zero-operation retirement transaction. The final page contains only protected root `253:1518`; its complete 112-node projection and PNG match their baseline hashes above. The bridge has no transaction or locks. Cleanup receipt SHA-256: `a09cc3bd3d6b95b6abec7465df8984b45536934e836a87ec85ff33b435b06a80`. No new qualified end-to-end timing sample or user sign-off exists; 4fea at 12:40.816 remains the only accepted timing point. No speedup claim is supported. |

## Separate untimed disclosure check

A separate untimed run, host_0muwk42jg1gn1bek, used the original B proposal bytes (SHA-256 581177dd3571030bc7c8a10aa936ec19927f151c784ca9e2647722ead8e596c3) and rendered the title “AI API 用量与费用控制台 · DEMO DATA”. The independent reviewer accepted five checks; the tree had 104 nodes, 0 IMAGE nodes, and no child-count gaps. Host strictComplete was true, while deliverableReady remained false. This is quality evidence for one page and is not a timing sample.

The user fully restarted Codex; Figma and the plugin/Bridge stayed running. Earlier MCP processes had exited, and the only new MCP process, PID 23140, started at 18:45:06 +08:00 from the clean frozen 4fea build. Its generated title matched a fresh local 4fea compile. This process evidence applies to that bounded untimed run.

The acceptance-evidence-with-tree.json SHA-256 is e39ba721462014fbf523b4e90b665009a2eac1a810d97380b6a943c1fc18409b; full-native-tree.json is 9eb4f09ae7eb4a1e3d205d0e9b9f9ec2056abf61f44909305f3f86248c5898dd; greenfield.png is a0472a867fbf94b6c86da7aafe1d6a495764482032c0f022ea87f5fa1c136bae. No screenshot is embedded in the public documentation.

## v0.4.9 release metrics (historical)

Canonical release tree: `v0.4.9` (402 canonical commits). This inventory counts 537 tracked TypeScript files
and 250,786 LF-delimited physical lines across the 13 workspaces under `packages/`, the `figma-plugin` workspace,
`scripts/`, and `tests/`. It is not a production-only LOC count or a software-quality metric.

Canonical v0.4.9 `npm run verify`: **3,085 tests / 3,084 pass / 1 skip / 0 fail / 453 suites**; exit 0.
Guard, TypeScript build and plugin build passed. Scrubbed-history CI for v0.4.9 passed on both `main` and the release tag.

## v0.4.9 file inventory (historical)

| Area | Files | Lines |
|---|---:|---:|
| `packages/core` | 17 | 5,497 |
| `packages/protocol` | 51 | 34,863 |
| `packages/design` | 18 | 12,944 |
| `packages/decision` | 7 | 770 |
| `packages/orchestrator` | 63 | 58,210 |
| `packages/tools` | 6 | 1,504 |
| `packages/bridge` | 9 | 3,482 |
| `packages/model` | 14 | 3,601 |
| `packages/memory` | 4 | 1,083 |
| `packages/browser` | 7 | 1,388 |
| `packages/cli` | 5 | 1,792 |
| `packages/mcp-server` | 5 | 986 |
| `packages/bench` | 18 | 5,466 |
| `figma-plugin` | 22 | 4,777 |
| `scripts` | 71 | 23,815 |
| `tests` | 220 | 90,608 |
| **Total** | **537** | **250,786** |

## Verification

- **v0.4.9 canonical full verify:** 3,085 test cases / 3,084 passed / 1 skipped / 0 failed / 453 suites; exit 0. Oct 5 Node test-runner duration 392,074.7201 ms. Log SHA-256: `345f45d08d21e8e4a52ef11d6a2fa5f27a2b7db21ab31546c0e1359d1547c59c`.
- **v0.4.9 scrubbed mirror CI:** main and release tag each ran 3,079 tests / 3,063 passed / 16 skipped / 0 failed / 453 suites. Main run `37313859741`: Node duration 382,873.79346 ms. Tag run `37313862915`: Node duration 379,846.3941 ms. Both passed on scrubbed HEAD `7e7857df949a526fc93a3c648084b6020920fd36`.
- **v0.4.8 historical canonical full verify:** 3,079 test cases / 3,078 passed / 1 skipped / 0 failed / 452 suites; exit 0. Oct 5 Node test-runner duration 390,027.6074 ms.
- **v0.4.8 historical scrubbed mirror CI:** main and release tag each ran 3,073 tests / 3,057 passed / 16 skipped / 0 failed / 452 suites. Main run `37295332019`: Node duration 373,877.570165 ms, Actions job about 411 s. Tag run `37295336675`: Node duration 374,256.20633 ms, Actions job about 412 s. Both passed.
- Historical v0.4.7 canonical full verify: 3,055 test cases / 3,054 passed / 1 skipped / 0 failed / 452 suites; exit 0.
- Historical v0.4.7 scrubbed mirror CI: 3,049 test cases / 3,033 passed / 16 skipped / 0 failed / 452 suites. Tag run `36902346689` and main run `36902337954` both completed successfully.
- **v0.4.6 historical scrubbed mirror CI:** 3,007 test cases / 2,991 passed / 16 skipped / 0 failed / 452 suites; run `36832313819` completed successfully.
- Scrubbed mirror skips include provider-gated checks and checks whose local source inputs are omitted by history scrub. R6 test 2b preflights its four non-`EXTERNAL` image paths, skips only when an exact path is absent, and retains the byte, pixel, `EXACT_RENDERED` and `checked=4` assertions whenever those images are present.
- **33 dedicated decision-shadow tests**; 4 shadow points; no runtime behavior depends on any answer
- **52** typed Figma protocol methods, **32** MCP tools
- **14** workspaces: 13 under `packages/`, plus `figma-plugin`
- One live mobile ADAPTATION run reached `ADAPTATION_COMPLETE` under its independent acceptance policy with
  `strictComplete=false`; the retained strict fidelity ledger is `NOT_COMPARABLE_TARGET`. This is not a strict
  fidelity PASS.
- CI runs the full suite on every change

## Functional scope

- **115-element** reference construction support matrix (native draw / reuse / transfer / defer)
- **5 platform shells**: desktop sidebar, top navigation, single column, mobile stack, tablet stack
- Region fidelity ledger with deterministic pixel metrics (MAE, changed-pixel ratio, luminance, edge)
- Asset settlement: local component reuse, Community transfer, media placement, outline vector import
- Host workflows: existing design, greenfield, reference reconstruction, reference adaptation
- Typed decision shadow (routing / finding triage / risk gate / correction materiality) with
  per-artifact agreement, confidence, latency and cost evidence; classification report for calibration

## General generation

- Optional typed `visualTokens` carry supported color and typography choices through deterministic token resolution into native construction. The runtime checks exact font faces and applies font size, line height, and letter spacing.
- Native text construction reuses loaded font promises and resolved parents. Eligible Host Reference Stage-A candidates use batched child reads and PNG exports, reducing transport round trips along that probe path.
- Evidence: three compiled-proposal scenes validated native parameters, viewport, relations, and containment. Measured transport improvement is scoped to eligible candidate reads and exports.
- Greenfield pages derive one page-level `DEMO DATA` title suffix from existing parsed demo-content markers on items or chart data. The source product type and content values stay unchanged; the native title uses its existing wrapping track.
- v0.4.9 Host planning: the CLI exposes complete start DTOs, state-guarded continuation, and offline proposal/review/plan validation. MCP initialize plus `tools/list` changed from 41,238 B to 24,585 B (40.4% less default discovery payload). The full reference guide remains available on demand: 20,352 B of text, 20,600 B as a JSON-RPC response. This measures context payload only; it is not a runtime latency or quality result.
- v0.4.8: explicit chart data, bounded table/activity/mobile layouts, and content/style/geometry-aware component reuse with fail-closed evidence checks. Grouped sections preserve native order and header bounds. Delete guards protect rollback stashes and refuse overlapping parent/descendant targets before writes. Two fixed Native fixtures passed scoped tree/text/viewport audits and exact rollback; they do not establish whole-page design quality or successful component reuse.
- Host visual closure: the Oct 2 task reached COMPLETE after post-clock final review and fresh capture on Oct 5. Root accepted the bounded result; no elapsed time was measured on that pass. The original timed receipt remains REVIEW_REQUIRED with degraded timing integrity, so no speedup or normal-latency claim is made.

## Host visual closure and timing

Host task host_0muqsigre0rrehmt reached COMPLETE after a post-clock final review and read-only capture on Oct 5. Root accepted the bounded output. This continued the Oct 2 task after its timed interval; it was not a new generation run. Closure proof: .fdr/tmp/e2e-luna-max-2026-10-05-live/quality-closure-oct5.json, SHA-256 4e54ce6e3af69358aa5e5ae28ecf5148b1ba0812693ab140cf8d0514888bd69a.

The root frame was 1440×900; its exact-byte 1008×630 export SHA-256 is f3516354cdbefaa252ec5a4310fc5c21c37cec3ca9202b0382b845b3b4719d85. Root review confirmed the DEMO DATA label, budget values, seven trend dates and bars, five aligned recent-call rows, viewport fit, and native editable elements. A low-severity chart-axis/grid alignment item remains. Read-only postflight found no active transaction, locks, or mutations. No elapsed time or speedup was measured for this Oct 5 closure.

The Oct 2 timed observer receipt ended REVIEW_REQUIRED at TIME_CAP_15_MIN with timingIntegrity=DEGRADED. Its Host planning spans include dependency-tool misuse and waiting. The original failed receipt remains unchanged and does not measure the Oct 5 post-clock completion.



## Known limits

- No URL references; local PNG/JPEG/WebP and Figma nodes only
- Assets (Community components, photos, icons) must be supplied by a human
- Greenfield charts use explicit labels, units, and finite numeric values. Absent chartData renders the no-data state; malformed and non-finite input fails schema validation. Zero-valued points in a signed domain do not create bars, while valid all-zero series retain zero-baseline markers.
- The external blind holdout currently fails; raw results are preserved in the private tree
- Vision scoring is a model judgment with observed ±7.5 noise on identical images
- Activity and table content wraps within bounded section widths; narrow mobile activity rows stack. Current Native fixtures cover fixed dashboard and signed-boundary cases only. Chart-axis and grid alignment remains a P2 polish item.

## Related documentation

- [English homepage](README.md)
- [中文主页](README.zh-CN.md)
- [Architecture overview (English)](ARCHITECTURE.md)
- [Evaluation license](LICENSE)
