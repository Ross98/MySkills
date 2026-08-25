---
name: preserving-layout-document-translation
description: Use when translating or revising layout-sensitive PDF, DOCX, brochure, technical specification, engineering drawing, scanned document, or image-heavy document where visible image text, page geometry, and visual fidelity matter.
---

# Preserving-Layout Document Translation

## Core rule

Treat translation and layout preservation as one deliverable. A file that builds successfully is not finished until its latest output passes page-by-page visual and technical QA.

Before acting, read [references/workflow.md](references/workflow.md). After the work, append a structured record using [references/postmortem.md](references/postmortem.md).

## Scope gate

Determine the requested mode before changing the source:

- strict in-place replacement;
- bilingual overlay;
- translated reflow/re-layout;
- redesign.

When the user says images, positions, page order, dimensions, or layout must not change, use strict in-place replacement. Do not redesign. Ask only when unreadable source, ambiguous protected content, unavoidable layout change, or destructive/irreversible processing creates a material choice.

## Non-negotiable invariants

- Preserve the original and write translated output separately.
- Inventory both editable text and visible text baked into images. Text extraction alone cannot prove coverage.
- Protect names, brands, model numbers, URLs, IPs, filenames, paths, versions, numbers, units, dimensions, drawing codes, and other tokens according to user instructions.
- Never approximate a complex text region with a large axis-aligned rectangle. Use real glyph bounds, rotation, clipping paths, and the original region boundary.
- Never guess colors. Read PDF fill colors or sample clean source pixels; keep page-specific colors local.
- OCR locates candidates; it does not prove complete removal and is not automatically a safe background-repair method.
- Measure translated text in the actual font before placement. Resolve overflow with faithful concise wording, wrapping, spacing, or font size while preserving neighboring content.
- Preserve only one final title when source and added translations would duplicate meaning.
- Save each completed page or asset immediately under stable page-based names.
- Track asset existence separately from whether the asset is selected for the current build. “Skipped” never means “delete completed work.”
- Inspect the newly generated output, never stale renders.

## Completion gate

Do not report completion until all intended pages are accounted for, the final file is reopened and rendered, every changed page is visually inspected, and page count/geometry plus protected tokens are verified. If any page is original, skipped, failed, or blocked, identify it explicitly; never call a partial translation complete.

## Required learning loop

After every translation task—even partial or blocked work—append the task’s observed problems, root causes, fixes, reusable rules, page/asset state, and actual verification result to:

`/Users/adam/Documents/Codex/2026-08-03/fan/outputs/今日PDF翻译与排版复盘.md`

Append only; preserve earlier records. Record facts from this run, not generic advice or claimed checks that were not performed.
