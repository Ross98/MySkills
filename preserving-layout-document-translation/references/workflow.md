# Workflow and QA

## 1. Preflight

1. Keep the source read-only and fingerprint it when practical.
2. Inspect page count, size, orientation, rotation, crop/media boxes, encryption, forms/signatures, links, bookmarks, annotations, attachments, file size, and generation method. A signed file requires confirmation because editing normally invalidates its signature.
3. Extract text with an appropriate parser, then render the full document at no less than 120 DPI. Use 300 DPI when text is baked into images or fine labels matter.
4. Compare extraction with visible pages. Inventory editable text, baked-in text, existing translated text, names, images, tables, charts, drawings, and protected tokens.
5. Create a terminology/protected-token list and page state table.

For DOCX, use the document-rendering workflow and inspect every rendered page. For PDF, use PDF inspection/rendering tools. Prefer workspace-bundled dependencies when system tools are absent.

### SVG and draw.io preflight

For structured SVG or draw.io exports, create two inventories before editing:

1. **Visible text channels:** XHTML `foreignObject`, native SVG `<text>`, text baked into raster fallback images, and any other rendered text mechanism. A complete list from only one channel is not complete coverage.
2. **Transform units:** identify top-level ordinary elements and top-level logical groups. If a top-level group has no direct geometry, calculate its bounds from all rendered descendant shapes in global page coordinates. Record critical grouped assemblies separately.

When draw.io metadata is embedded, decide whether the deliverable must reopen as an updated draw.io diagram or only remain a visually editable SVG. If draw.io editability is required, update and verify the embedded model as well as the rendered SVG; preserving stale metadata is not sufficient.

## 2. Choose the least damaging method

- Editable text: replace the text object where feasible.
- Flat/simple-color regions: cover only the actual glyph bounds, including antialiasing edges, with exact sampled/source color.
- Rotated or slanted text: match rotation and clip to the original shape.
- Circles, arcs, arrows, tables, and irregular shapes: use original paths/masks; no broad rectangular patches.
- Photographs, gradients, thin lines, diagrams, or dense infographics: evaluate per region. OCR plus generic inpainting is unsafe when it creates stains, gaps, or damaged geometry; stop that route when artifacts appear.
- Mostly rasterized pages: explain the rasterization tradeoff if it materially changes searchability, copyability, accessibility, clarity, or file size. Preserve the vector source and write a separate output.
- “Images unchanged”: edit only permitted external text bands. Do not alter labels inside the image unless the user explicitly includes them.

## 3. Place translated text

1. Use actual source bounds, not coordinates estimated from a low-resolution preview.
2. Measure text width using the target font and size before writing.
3. Check the full original background rectangle’s top, bottom, left, and right edges. A replacement background must not leave steps or color seams.
4. Prefer concise faithful translation, then line wrapping, spacing adjustment, or smaller font. Do not silently move adjacent modules or images.
5. Inspect the next one or two lines for existing equivalent-language subtitles before adding a title.
6. When deleting a line, include opening/closing punctuation, brackets, and antialiased edges; OCR boxes are only hints.

## 4. Page and asset state

Keep two independent fields:

- `asset`: `missing | processing | available | failed`
- `selection`: `use-translated | use-original | skipped | blocked`

Also record translation/QA state such as `pending | translated | layout-checked | qa-failed | qa-passed`, issue notes, stable asset path, and last verified output version. A network failure or long-running job does not equal completion. Save successful pages immediately; avoid duplicate resubmissions that can create conflicting assets.

## 5. Structured-diagram relayout

When changing a diagram from side-by-side to stacked or otherwise moving complete regions:

1. Confirm the region order and which legend or annotation block belongs to each region.
2. Classify top-level transform units using global rendered bounds, not local child coordinates.
3. Move an ordinary element once. For a nested assembly, move only its outermost group once; do not separately transform its descendants.
4. Recalculate page bounds after transforms. Check that every critical group intersects the final page and that regions do not overlap.
5. Verify region order and critical nested-group transforms with automated assertions where practical.
6. Compare source and output module inventories. Matching text counts do not prove that shapes, internal connectors, or complete assemblies survived.

Place each legend immediately after its associated region unless the user explicitly requests a combined legend area.

## 6. Iterative QA

After every page change:

1. rebuild the output;
2. render that page from the latest output at 120 DPI or higher;
3. inspect at magnification for source-language remnants, punctuation, duplicate titles, overflow, clipping, overlap, color mismatch, background steps, patch borders, damaged images/lines, blur, or shifted geometry;
4. fix and rerender until clean.

After final assembly:

1. verify adopted page list, page count, order, dimensions, orientation, rotation, and crop/media boxes;
2. reopen and render the final file, then inspect a contact sheet for consistency and every page individually;
3. compare source and output side by side or by overlay where useful;
4. verify every inventoried text block is translated or has an explicit preservation reason;
5. verify protected tokens exactly and terminology consistently;
6. check font substitution, missing glyphs, and font embedding where the format supports it;
7. confirm existing links, bookmarks, annotations, and attachments remain intact unless the user excluded them;
8. confirm the requested filename and ensure the build script uses the same output path;
9. report skipped, original, failed, or blocked pages plainly.

For SVG/draw.io output, additionally verify:

- every inventoried visible text channel;
- every critical grouped assembly, including its internal shapes and connectors;
- no translated object lies outside the final viewBox/page;
- legend-to-region order matches the confirmed design;
- the claimed editability level matches what was actually updated and reopened.

Technical checks do not replace visual checks, and visual checks do not replace technical checks.
