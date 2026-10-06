# README asset art direction

Audience: developers and AI-agent hosts working with native Figma designs. Claim: AI2figma carries agent reasoning through validated local operations into editable Figma layers.

## Shared visual language

- Four opaque Mode A PNGs show the mechanism as original workshop concept art, not real product screenshots: a blueprint becomes typed operations, a native layer board, and a review/readback loop.
- Use confident black manga ink with varied weight and circular halftone on warm off-white paper. Keep the round-glasses stick figure and chubby warm-yellow Border Collie secondary to the work artifacts.
- Reserve muted blue-gray for input/content paths and muted sage green for validation or accepted results. Avoid glossy effects, neon color, generic card grids and dashboard imagery.
- The EN and zh-CN image pairs use the same scene geometry and roles. The exact visible labels and evidence surfaces are described here; per-file dimensions and SHA-256 hashes are recorded in the asset manifest.

## Deterministic SVG diagrams

- `architecture-{en,zh}.svg` shows Agent Host → MCP → typed local Bridge → Figma plugin → Figma document. The runtime records evidence; the Figma document edge is labeled as readback.
- `workflow-{en,zh}.svg` uses horizontal process lanes for Existing, Greenfield and Reference, without nested cards.
- `generation-time-{en,zh}.svg` is a zero-based 0–20 minute horizontal bar chart with a marked 15-minute cap. The first three rows use actual terminal time; 4fea uses request-to-quality-ready and independent review acceptance. Over-cap times are not backdated.
- The 4fea runtime-active value 4,837.979 ms is a separate ledger clock, not end-to-end generation latency. This is one accepted point; no speedup, median or trend is claimed.

Chart principles: Cleveland & McGill's common zero-baseline length comparison; Cairo's truthful endpoint and cap disclosure; Tufte's data-ink restraint. The source receipt SHA-256 is `5e2fe92709d5522d56d7c8096ba94afe475d42a96f4575ee0c4c8f202b9b9453`; source rows and integrity states are preserved in the manifest.

Long descriptions, full setup steps, limits, timing definitions and commands remain in README Markdown. No README file is modified by this asset branch.

## Mode A PNG reproduction recipes

The original image-generation tool call text was not included in the handoff. The prompts below are **reproduction recipes reconstructed from the approved final brief and visible assets**, not verbatim generation-call records. Each recipe is complete when read as the shared prompt followed by its asset-specific prompt and the shared style anchor. All four outputs are finished Mode A PNGs with labels rendered inside the image; no cutout or separate text overlay is used.

### Shared prompt

    Create a finished explanatory bitmap illustration for the AI2figma README. In about 10 seconds, show the real mechanism: a workshop blueprint is translated into schema-validated typed operations, then into native editable Figma layers that can be visually reviewed and read back. This is original concept art, not a real product screenshot. Use a wide 2.86:1 horizontal panorama with a warm off-white, lightly textured workshop and wooden work surface. Make the transformation understandable from the blueprint, operation checklist and validation press, editable layer board, arrows, and review evidence even when the labels are ignored. Include a minimal stick-figure worker with a round head, thin round glasses, dot eyes, a simple smile, and thin line-drawn limbs, plus a chubby warm-yellow Border Collie; keep both secondary to the work artifacts. Use confident manga/comic ink with varied black line weight and restrained circular halftone. Keep the palette mostly black, white, and halftone gray, with warm yellow on the dog, muted blue for input/content, and muted sage green for validation or accepted results. Render only the exact labels listed in the asset-specific prompt, each once, integrated into its named evidence surface. Use modern sans-serif medium or bold lettering large enough to read. No other legible text, no 3D, glossy gradients, photorealism, generic card grid, dashboard, decorative clutter, tiny text, or watermark. PNG, opaque finished scene, Mode A; do not use a chroma-key background or background removal.

### oil-hero-en-v1.png

    Use the shared prompt. Compose three connected regions from left to right: at left, the glasses-wearing agent works over a blue-gray design blueprint beside the Border Collie; at center, the blueprint's checklist feeds through a mechanical typed-operation validation press with a sage-green approval mark; at right, the output is a native editable layer board with visible selection handles and a layer list. Connect the evidence with clear blue-gray arrows. Integrate these exact labels once each: “AI2figma” on the large workshop wall sign; “Agent” on the small desk nameplate beside the worker; “Typed operations” on the foremost checklist at the validation press; “Editable layers” on the header of the layer board. Add no other legible wording.

### oil-hero-zh-v2.png

    Use the shared prompt and the same composition and evidence surfaces as oil-hero-en-v1.png, with Chinese label lettering. Integrate these exact labels once each: “AI2figma” on the large workshop wall sign; “智能体” on the small desk nameplate beside the worker; “类型化施工” on the foremost checklist at the validation press; “可编辑图层” on the header of the layer board. Preserve the same left-to-right blueprint → typed-operation validation → editable layer board transformation and add no other legible wording.

### oil-process-en-v1.png

    Use the shared prompt. Show one continuous panoramic workshop workbench as a process loop, not a set of cards: a large blue-gray plan blueprint at the left; a stack of typed work sheets passing through a central validation stamp/press with a sage-green check; an editable native layer board at the right-center; and a reviewer with a magnifying glass at the far right. Place the recurring glasses-wearing stick figure and warm-yellow Border Collie as small helpers at the plan and review ends. Use blue-gray arrows for forward movement and a broad sage-green curved arrow returning from review toward the plan so planning, building, review, and rework read as one loop. Integrate these exact labels once each: “Plan” on the blueprint's blue title strip; “Validate” on the validation press nameplate; “Build” on the green front rail of the editable layer board; “Review” on the sage-green sign above the reviewer. Add no other legible wording.

### oil-process-zh-v1.png

    Use the shared prompt and the same continuous process-loop composition and evidence surfaces as oil-process-en-v1.png, with Chinese label lettering. Integrate these exact labels once each: “规划” on the blueprint's blue title strip; “校验” on the validation press nameplate; “构建” on the green front rail of the editable layer board; “复核” on the sage-green sign above the reviewer. Preserve the forward path and the green review-to-plan return arrow; add no other legible wording.

### Shared oil-visual style anchor

    Professional editorial manga/comic ink illustration. Clean confident black ink outlines with varied line weights, expressive but controlled. Use classic circular halftone screentone for gray and shadow areas. Minimal cute stick-figure protagonist with round head, thin round glasses, dot eyes, simple smile, and thin line-drawn limbs. Include a chubby warm-yellow Border Collie companion. Use an off-white lightly textured real environment, not a blank white canvas. Typography is modern sans-serif, medium or bold, large and readable. Color is restrained: black, white, halftone gray, warm yellow for the dog, plus at most two muted semantic accent colors. No 3D, no glossy gradients, no photorealism, no generic card grid, no dashboard, no decorative clutter, no tiny text, no long paragraphs, no watermark.

Outputs: assets/readme/oil-hero-en-v1.png, assets/readme/oil-hero-zh-v2.png, assets/readme/oil-process-en-v1.png, and assets/readme/oil-process-zh-v1.png. All are Mode A. No cutout was used.