---
name: ppt-image-first
description: Build presentation plans for PPT / slides / decks through a conversation-first workflow, then propose multiple visual directions with preview images before writing deck specs. Use when the user asks to create a PPT, presentation, deck, 答辩稿, 路演 deck, 产品介绍 PPT, 汇报 PPT, or when the user has only a topic or rough materials and needs help clarifying structure, style, and page planning before generation.
---

# PPT Image First

Use this skill to turn a vague PPT request into a generation-ready, image-first deck plan.

## I/O Contract

- Input: a PPT topic, rough goal, existing notes/materials, or complete report-like narrative.
- Optional anchors: audience, page count or duration, school/company/lab/course/brand identity, use occasion, source files, and style constraints.
- Output: a confirmed content basis, visual style previews as local image files, deck specs, generated page visuals, folder-based review, and the final PPT after approval.
- Confirmation gates: `需求确认`, `风格确认`, `生成前确认`, and final review approval.
- Default ratio: generate preview images and final page visuals in `16:9` unless the user explicitly requests another ratio.
- Preview, candidate-selection, and review surfaces are local image folders plus chat feedback. Do not build or open HTML UI pages for those stages.

## Workflow Phases

Follow these phases in order and do not skip the confirmation gates:

1. Intake: clarify lightly, identify anchors, output a short baseline judgment, then get `需求确认`.
2. Content basis: create or extract `content_report.md` unless the user already supplied complete report-like content; show a synthesized judgment, not the raw file by default.
3. Style preview: align style boundaries, propose directions, generate one `正文页` preview image per direction into a local `previews/` folder, give the user the folder path, support refinement, then get `风格确认`.
4. Planning lock: run `风格反演确认`, then write `design_spec.md`, `slide_blueprint.md`, and `spec_lock.md` in that order; summarize and get `生成前确认`.
5. Generation and review: generate page visuals into a local folder, let the user review the images directly in the folder and give feedback in chat, retouch as needed, and export the final PPT only after approval.

Read `references/workflow.md` for stage-by-stage execution details.

## Progressive Loading

- Intake and baseline: read `references/conversation_framework.md` only when you need the conversation-first intake pattern.
- Style proposals: read `references/style-system.md` when producing proposal cards or interpreting V1-V8 internally.
- Preview flow: read `references/preview-flow.md` before producing style previews or reviewing generated page images.
- Content basis: read `templates/content_report_reference.md` before writing `content_report.md`.
- Planning files: read `templates/design_spec_reference.md`, `templates/slide_blueprint_reference.md`, and `templates/spec_lock_reference.md` immediately before writing those files.

## Working Principles

- Treat the user like a client and yourself like the proposing design agent.
- Do not force the user to configure design parameters manually; translate their natural-language intent into design decisions.
- Ask for real-world identity anchors when relevant, but treat them as grounding context rather than style questions.
- Keep intake lightweight; do not turn content basis or style alignment into a long questionnaire.
- Use style vectors internally, but present front-stage options as concise proposal cards plus preview images.
- Use the content basis for previews and planning rather than generic placeholder structures.
- Mark inferred claims carefully; do not present unsupported precise data, experiment results, citations, or institutional conclusions as user-provided facts.
- Show summaries, proposal cards, previews, and review surfaces by default; show raw planning files only when useful or requested.

## Hard Rules

- Preview-first: final style confirmation should be based on generated preview images, not text-only choices.
- One preview image per direction: each style direction gets exactly one `正文页` preview image. All directions in the same round must use the same page role so the user can compare them fairly.
- Folder delivery: write preview and generated page images to a local folder and give the user the absolute folder path immediately. Do not assemble HTML preview, candidate-picker, or review pages, and do not open a browser for those stages.
- Folder review: the user reviews generated pages directly in the image folder and gives feedback in chat, keyed by slide ID or filename. Do not require a special JSON payload, annotation file, or browser-based review surface.
- Do not write `slide_blueprint.md` before style direction and `风格反演确认` are complete.
- Keep generation image-first when the confirmed direction depends on generated page visuals; do not silently fall back to shape-by-shape PPT construction or hand-drawn code substitutes.
- User-requested edits such as adding, replacing, correcting, or supplementing visible text are still image-generation/editing tasks by default. Do not use PIL, Pillow, canvas, SVG, HTML screenshots, PPT native text boxes, or deterministic overlays to patch final page visuals unless the user explicitly asks for a code/PPT-overlay workaround.
- Treat generated page visuals as complete by default; post-generation overlays default to zero unless they are traceable to approved blueprint fields.
- Keep slide identifiers, candidate codes, filenames, and generation batch labels outside the image-generation prompt body. They may appear in planning files, filenames, mapping tables, and chat instructions, but the prompt sent to the image model should contain only audience-facing content and visual direction.
- Before full generation, ask whether the user wants one final image per slide or multiple final candidates per slide.
- Multi-candidate selection happens in the folder and in chat: give the candidate folder path, let the user reply with one line per slide such as `S01-03`, and map those codes to filenames. Do not build a candidate-picker HTML page.
- Do not export the final PPT immediately after first-pass generation; export only after the reviewed pages are approved.

## Output Hierarchy

Use these layers consistently:

- `content_report.md` = upstream content basis when the user did not provide complete report-like material.
- `design_spec.md` = global deck rationale and confirmed visual system.
- `slide_blueprint.md` = page-by-page intent and content plan.
- `spec_lock.md` = execution constraints and final generation guardrails.

`content_report.md` supports the 3 core planning files; it does not replace them. `spec_lock.md` is always the last core planning file.

## Removed Workflow UI

This branch removed the former HTML workflow shells and the coordinate-markup review pipeline. There are no bundled preview, candidate-picker, or review pages, and no review-markup script. Previews, candidate selection, and review are all folder-based and chat-based.

Do not recreate those HTML pages or a coordinate-markup review payload unless the user explicitly asks for a browser-based variant.
