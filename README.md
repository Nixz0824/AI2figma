# AI2figma
English | [简体中文](README.zh-CN.md)

**An AI agent can build or update a Figma page; AI2figma applies the changes as editable layers and records the result.**

v0.4.10 · Default host mode needs no provider API key.

<p align="center">
  <img src="assets/readme/oil-hero-en-v1.png" width="100%" alt="Conceptual illustration of AI2figma routing an agent plan through typed validation into editable Figma layers">
</p>
<p align="center"><em>Conceptual illustration, not a product screenshot.</em></p>

AI2figma is a local runtime for Figma Desktop. It connects an AI host to Figma locally, checks each structured write before applying it, and records the result. The public repository contains product documentation and evaluation information; source code is private.

## Current stage and recent closeout · Oct 21, 2026

No-reference `workflow="greenfield"` development remains paused; its implementation and historical evidence are retained. Active work focuses on Existing edits and pages built from an actual supplied reference, including `reference_greenfield`. The product remains v0.4.10; this maintenance and documentation update is not a new feature release.

| Checkpoint | Local verification | Native fixture status |
| --- | --- | --- |
| Oct 21 shared Reference preflight · canonical checkpoint `9fe65d1` | `npm run verify`: 3,487 tests, 3,486 passed, 1 existing skip, 0 failed. | A proven source-backed placement conflict is rejected before construction; the accepted control plan remains `READY` with zero issues. The real-input preflight itself made zero Bridge/Figma/provider calls. This is local source verification, not GitHub CI or a Figma delivery. |
| Oct 20 Pokecut Reference adaptation | Read-only evidence revalidation on the accepted capture. | `ADAPTATION_COMPLETE`; acceptance issues 0 after correcting coordinate interpretation. Strict V1 is 7 PASS / 1 `NOT_COMPARABLE_TARGET`, V2 is 0/7 PASS, and human acceptance remains false. |
| Oct 19 Monotime Reference adaptation | Native result and formal visual review. | `ADAPTATION_COMPLETE`; source calibration is partial, strict V1 is 3/4 PASS, V2 is 0/4 PASS, and human acceptance is false. |
| Oct 18 Packing normal Reference entry | Prior local source gate: 3,462 tests, 3,461 passed, 1 existing skip, 0 failed. | `ADAPTATION_COMPLETE`; 52 target checks and 7 relations passed. Strict comparability and human acceptance remain separate. |
| Oct 18 Banking Home Existing closeout | Scoped Existing inspection and final readback. | Existing route is `COMPLETE`; its separate Reference route remains `HUMAN_ACTION_REQUIRED`, so this is not Reference completion. |
| Oct 16 Commerce Existing closeout | Local `npm run verify`: 3,402 tests, 3,401 passed, 1 existing skip, 0 failed. | Scoped Existing asset completion and KPI spacing are `COMPLETE`; strict Reference fidelity and human acceptance remain separate. |
| Oct 11 role-authority closeout · `ab7bc57` | `npm run verify`: 3,296 tests, 3,292 passed, 4 skipped, 0 failed, 465 suites. | Original capture `2ba5…` is `HUMAN_ACCEPTED`; strict V2 remains unresolved and the reissue made 0 Figma writes. |
| `08ef304` | Official plain `npm run verify`: 3,201 tests, 3,197 passed, 4 skipped, 0 failed, 454 suites; guard, TypeScript build, and plugin build passed. | Root returned `SCOPED_NATIVE_PASS`; the Host run remains `REVIEW_REQUIRED`, not complete. The fixture has no timing result. |
| First reference-led batch · test checkpoint `0b3fccd` (production source remains `8eb298a`) | Official plain local `npm run verify` (2026-10-09): 3,222 tests, 3,218 passed, 4 skipped, 0 failed, 456 suites. | At that recorded checkpoint, Native was `DECOMPOSITION_REQUIRED`; no Figma drawing, Native PASS, or new timing was claimed. |

The current fixed-weight estimate is **72.5/100 (about 73%)** across active Reference and Existing scope: Reference 75 (40%), Existing 75 (20%), Runtime 90 (20%), whole-task efficiency 40 (10%), and release/acceptance 55 (10%). It is a subjective evidence-based estimate, not a statistical completion rate. One recent Reference task took **6 h 10 m 37.315 s** from preparation intent to canvas closeout, including planning, review, correction, and waiting; this is one full-cycle observation, not a benchmark average or speedup claim. See the [current metrics](METRICS.md#current-project-snapshot-oct-21) and [roadmap](ROADMAP.md).

The Oct 21 gate is local canonical verification, not GitHub CI. Historical local verification rows retain their original scopes; the passive-preload diagnostic ran tests only and is not equivalent to the full plain gate. The formal version remains v0.4.10, with no new release or tag. The [private source mirror main](https://github.com/Nixz0824/AI2figma-source/tree/main) is a scrubbed snapshot with a different commit identity from canonical history.

The following CLI note and three scoped changes describe the historical Oct 8 reference-maintenance batch; they are separate from the Oct 21 preflight above. The reference CLI entry is `fdr host start "<request>" --references-file <json>`:

- On one controlled Existing fixture with the same call and query, Bridge RPCs fell from 9 to 6. This is a call-count result, not an end-to-end speed measurement.
- Dense-text row placement is more reliable; unmatched or multiline text keeps its original geometry.
- For screenshot input, the host agent selects a complete viewport and preserves the original while recording any crop. The new helper is a PNG preprocessing step; Host retains its existing support for other image formats. A clear, complete artboard needs no user-made clean export; whole-image no-op preserves the PNG bytes, exact replay adds zero writes, and ambiguous or clipped candidates remain unresolved rather than guessed.

See the [scoped batch details](METRICS.md#first-reference-batch-oct-8).

## Oct 11 role-authority closeout · reviewed snapshot accepted

Latest local source checkpoint `ab7bc57` passed `npm run verify`: 3,296 tests, 3,292 passed, 4 skipped, 0 failed, 465 suites. This is local verification, not GitHub CI. The original reviewed capture (`2ba5…`) is `HUMAN_ACCEPTED`; the reissue made no Figma writes. This acceptance is not strict `COMPLETE`: V2 remains failed on incomparable text ink and 14 asset-node ink gaps, and no total-generation before/after timing is recorded.

After that acceptance, the user separately requested matching the pale board's four corners to the black cards. One typed radius edit changed 0 to 54.656 and produced a separate capture and receipt; it did not rewrite the accepted capture. The product remains v0.4.10 with no new tag. See the [Oct 11 role-authority report](docs/REFERENCE_ROLE_AUTHORITY_REISSUE_2026-10-11.md) and [metrics](METRICS.md#reference-role-authority-reissue-2026-10-11). The Oct 10 coordinate-integrity and v2.4 source-measurement records remain separate historical evidence.

## Historical v0.4.10 native timing

<details>
<summary>Four historical native-entry observations</summary>

<p align="center">
  <img src="assets/readme/generation-time-en.svg" width="100%" alt="Four October 6 native observations: three ended in timeout or rework, and one reached independent quality acceptance in 12 minutes 40.816 seconds">
</p>

The v0.4.10 sample was a 1440×900 page with no image nodes. Its contemporaneous readback returned 91 native nodes, but was depth-limited; a complete Oct 7 readback found 112 nodes, including 21 existing descendants omitted below three cutoff parents. See the [readback correction](METRICS.md#native-readback-correction-oct-7). The independent review accepted five checks: required information, budget focus, readability, table alignment, and editable elements. One non-blocking visual-balance suggestion remains.

| Native observation | Time (m:s) | Recorded outcome |
| --- | ---: | --- |
| Early run · v0.4.8 | `17:30.088` | Review was still required after the 15-minute cap |
| Intermediate run · candidate 0248 | `12:44.386` | The run finished, but review required rework; timing coverage was incomplete |
| Canonical d8 run | `16:21.281` | Review was still required after the 15-minute cap; later visual closure did not change the timing record |
| v0.4.10 production source | `12:40.816` | Independent review accepted; timing record is valid |

The first three observations end at their recorded terminal outcomes; the last ends after quality readiness and review. These are not an accepted old/new comparison. We report one accepted timing point, not a speedup or a median.

</details>

## Active workflows

| Workflow | Starting point | Result |
| --- | --- | --- |
| Update a page | An existing Figma page and a requested change | A scoped edit with before/after evidence and rollback protection |
| Rebuild a reference | A local image or supplied Figma material | A measured plan that reconstructs supported regions as editable layers |

<details>
<summary>Legacy / paused no-reference Greenfield</summary>

The legacy `workflow="greenfield"` path creates a page from a brief without a reference. Its development is paused; existing code and records are retained. New pages based on a real supplied reference remain active.

</details>

## How the local runtime works

<p align="center">
  <img src="assets/readme/oil-process-en-v1.png" width="100%" alt="Conceptual illustration of the local workflow: plan, validate, build native Figma layers, and review">
</p>
<p align="center"><em>Conceptual illustration of the workflow, not a product screenshot.</em></p>

<p align="center"><img src="assets/readme/workflow-en.svg" width="100%" alt="Two active workflows: Existing edits and reference-led pages; no-reference Greenfield is shown as paused legacy."></p>

An agent proposes a change. The local runtime checks the structured operations, applies them through the Figma plugin, then reads the document back and records evidence. Typed operations, transaction tracking, locks, rollback support, and readback evidence help control writes; unresolved outcomes fail closed instead of being retried automatically.

The runtime owns validation and document operations; the AI host owns planning. The default mode uses the AI host for reasoning and needs no provider API key; optional provider modes are configured separately. No model runs arbitrary JavaScript inside Figma.

On current source main, the stdio MCP server starts or reuses the local Bridge at `127.0.0.1:17321` when the first runtime-backed tool is called. MCP initialization, tool discovery, and static workflow guides do not start it. In Figma Desktop, import and run the plugin through the normal Development plugin flow; Bridge health does not mean the plugin is connected. The host cannot launch the plugin or open an arbitrary Figma file. Once the plugin is connected to the chosen document, an explicit Reference start can prepare a dedicated blank page within that file; Existing edits use the supplied page or selection.

The package supports Node 20.11 or newer; Node 24 is recommended for native TypeScript source commands. Run `npm run build` before using the compiled MCP launcher; it loads `packages/mcp-server/dist/bin.js` in the same process. Figma Desktop and a connected development plugin are required for document operations.

A run record connects the requested scope to its operations, final tree, review state, and integrity hashes. Recorded transactions include rollback support; uncertain writes are checked against Figma state and fail closed instead of being retried silently.

## v0.4.10 release checks

| Check | Result |
| --- | --- |
| v0.4.10 source snapshot | 414 source commits; 538 TypeScript/TSX files; 251,916 LF-delimited physical lines (repository size, not a quality measure) |
| Canonical production-source verification | 3,105 tests; 3,104 passed, 1 skipped, 0 failed across 453 suites |
| Private mirror main CI | 3,099 tests; 3,083 passed, 16 skipped, 0 failed across 453 suites · [run 37460767274](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460767274) |
| Private mirror v0.4.10 tag CI | 3,099 tests; 3,083 passed, 16 skipped, 0 failed across 453 suites · [run 37460770403](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460770403) |

The release tag includes the verified 4fea production source plus a documentation record. One non-blocking layout-balance suggestion remains. Independent review is not user sign-off. These checks describe this page and release pipeline; they do not claim pixel equivalence or quality across every design.

The `08ef304` checkpoint retains the no-reference Greenfield implementation as a legacy path; development is paused. Existing edits and reference-led new pages remain in scope. This does not claim every reference route is complete or optimized. See the [Oct 8 stage records](METRICS.md#stage-closure-oct-8).

The earlier bounded mobile/Existing review at `f4414ef` had a local verification result of 3,178 tests (3,177 passed, 1 skipped, 0 failed). Root gave limited fixture acceptance for mobile fit, scoped placement, and one Existing text edit; owned-root cleanup is verified. This is historical scoped evidence, not the current gate total; see the [detailed review](METRICS.md#current-main-mobile-existing-oct-7).

The current-main font-query fix preserves all 18 Inter faces while reducing the offline compact UTF-8 response from 30,784 to 749 bytes (97.57%); see the [measurement details](METRICS.md#current-main-font-payload-oct-7).

<p align="center">
  <img src="assets/readme/font-payload-en.svg" width="100%" alt="Compact Inter font-query response: 30,784 bytes before and 749 bytes after scoping labels, with all 18 Inter faces preserved">
</p>

An Oct 7 E2E timing attempt that predates this fix was rejected by automatic review before Host (`PRE_HOST_REQUEST_BLOCKED`), producing no design or accepted timing. Its 115,803 ms pre-Host window is an incomplete observation and is not counted as generation timing.

Source commit `6576101` checks content, style, and geometry around Existing edits, and binds its undo to the expected transaction ID. At production HEAD `657610181b1d1587fe7556c989c6b42d1a2a4a55`, `npm run verify` passed 3,190 tests across 454 suites (3,189 passed, 1 skipped, 0 failed); guard, TypeScript build, and plugin build passed. The captures do not exclude user edits atomically. The connected plugin still uses the Oct 6 bundle, so this source wave has no native acceptance yet; an updated bundle is required. See [current source and deployment limits](METRICS.md#current-main-existing-integrity-oct-7).

## Plan the first evaluation

Once access is provided, start with a small, reviewable task:

1. State the goal, target viewport, and information that must remain visible.
2. In Figma, inspect the text, tables, and charts as editable native layers.
3. Review the resulting page and its evidence before expanding the scope.

## Request an evaluation

The source is private. Personal, non-commercial evaluation is free; an official build may be provided on request. To start, [open an evaluation issue](https://github.com/Nixz0824/AI2figma/issues/new) with your operating system, Figma Desktop setup, and the workflow you want to evaluate. Do not include credentials or private design files in a public issue.

## License and boundaries

Commercial use requires a separate written license. Source code is not distributed, and the license prohibits redistribution and using the materials or outputs to train models. Read the [evaluation license](LICENSE) before requesting a build.

Reference inputs must be local; URL references are not supported. Photos, icons, and external components must be supplied manually. Reference adaptation uses a separate completion policy; completion under that policy does not mean strict fidelity passed.

The timing example uses a bounded synthetic-data task. The page is a single reviewed sample, not a user screenshot, benchmark average, pixel-perfect reconstruction claim, or promise that every design will pass the same checks.

## More detail

- [Product direction and roadmap (Oct 21, 2026)](ROADMAP.md)
- [Documentation index](docs/DOCUMENTATION_INDEX.md)
- [Metrics, historical runs, and evidence references](METRICS.md)
- [Reference role-authority reissue (Oct 11, 2026)](docs/REFERENCE_ROLE_AUTHORITY_REISSUE_2026-10-11.md)
- [Generation timing observation (Oct 8, 2026)](docs/GENERATION_TIMING_2026-10-08.md)
- [Scoped native handoff (Oct 8, 2026)](docs/GREENFIELD_NATIVE_HANDOFF_2026-10-08.md)
- [Greenfield pause and stage archive (Oct 8, 2026)](docs/GREENFIELD_PAUSE_2026-10-08.md)
- [中文说明](README.zh-CN.md)
- [Architecture overview (English)](ARCHITECTURE.md)
- [System map (SVG)](assets/readme/architecture-en.svg)
- [Workflow diagram (SVG)](assets/readme/workflow-en.svg)
- [Evaluation license](LICENSE)
