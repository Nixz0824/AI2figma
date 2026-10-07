# AI2figma
English | [简体中文](README.zh-CN.md)

**An AI agent can build or update a Figma page; AI2figma applies the changes as editable layers and records the result.**

v0.4.10 · Default host mode needs no provider API key.

<p align="center">
  <img src="assets/readme/oil-hero-en-v1.png" width="100%" alt="Conceptual illustration of AI2figma routing an agent plan through typed validation into editable Figma layers">
</p>
<p align="center"><em>Conceptual illustration, not a product screenshot.</em></p>

AI2figma is a local runtime for Figma Desktop. It connects an AI host to Figma locally, checks each structured write before applying it, and records the result. The public repository contains product documentation and evaluation information; source code is private.

## One measured native result

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

## Three ways to use it

| Workflow | Starting point | Result |
| --- | --- | --- |
| Update a page | An existing Figma page and a requested change | A scoped edit with before/after evidence and rollback protection |
| Create a page | A written brief | A native Figma page with resolved layout, text, tables, and charts |
| Rebuild a reference | A local image or supplied Figma material | A measured plan that reconstructs supported regions as editable layers |

## How the local runtime works

<p align="center">
  <img src="assets/readme/oil-process-en-v1.png" width="100%" alt="Conceptual illustration of the local workflow: plan, validate, build native Figma layers, and review">
</p>
<p align="center"><em>Conceptual illustration of the workflow, not a product screenshot.</em></p>

An agent proposes a change. The local runtime checks the structured operations, applies them through the Figma plugin, then reads the document back and records evidence. Typed operations, transaction tracking, locks, rollback support, and readback evidence help control writes; unresolved outcomes fail closed instead of being retried automatically.

The runtime owns validation and document operations; the AI host owns planning. The default mode uses the AI host for reasoning and needs no provider API key; optional provider modes are configured separately. No model runs arbitrary JavaScript inside Figma.

On current source main, the standard stdio MCP server starts or reuses the local Bridge when the first runtime-backed tool is called. MCP initialization, tool discovery, and static workflow guides do not start it. In Figma Desktop, import and run the plugin through the normal Development plugin flow; Bridge health does not mean the plugin is connected. The host does not open the plugin or switch files, and it closes only the Bridge instance it created.

A run record connects the requested scope to its operations, final tree, review state, and integrity hashes. Recorded transactions include rollback support; uncertain writes are checked against Figma state and fail closed instead of being retried silently.

## v0.4.10 release checks

| Check | Result |
| --- | --- |
| v0.4.10 source snapshot | 414 source commits; 538 TypeScript/TSX files; 251,916 LF-delimited physical lines (repository size, not a quality measure) |
| Canonical production-source verification | 3,105 tests; 3,104 passed, 1 skipped, 0 failed across 453 suites |
| Private mirror main CI | 3,099 tests; 3,083 passed, 16 skipped, 0 failed across 453 suites · [run 37460767274](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460767274) |
| Private mirror v0.4.10 tag CI | 3,099 tests; 3,083 passed, 16 skipped, 0 failed across 453 suites · [run 37460770403](https://github.com/Nixz0824/AI2figma-source/actions/runs/37460770403) |

The release tag includes the verified 4fea production source plus a documentation record. One non-blocking layout-balance suggestion remains. Independent review is not user sign-off. These checks describe this page and release pipeline; they do not claim pixel equivalence or quality across every design.

Current main offers explicit Greenfield/Existing selection, scoped placement that keeps existing frames fixed, and mobile first-screen fit with 44 px buttons, guarded charts, and complete activity helpers. It also includes [primary-metric selection and full-tree readback](METRICS.md#current-main-metric-focus-oct-7).

Local verification at `f4414ef` passed 3,178 tests (3,177 passed, 1 skipped, 0 failed). Root gave limited fixture acceptance for mobile fit, scoped placement, and one Existing text edit; owned-root cleanup is verified. No new end-to-end timing sample, speedup, or user sign-off is claimed; see the [detailed review](METRICS.md#current-main-mobile-existing-oct-7).

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

- [Metrics, historical runs, and evidence references](METRICS.md)
- [中文说明](README.zh-CN.md)
- [Architecture overview (English)](ARCHITECTURE.md)
- [System map (SVG)](assets/readme/architecture-en.svg)
- [Workflow diagram (SVG)](assets/readme/workflow-en.svg)
- [Evaluation license](LICENSE)
