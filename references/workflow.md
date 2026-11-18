# Workflow

## Stage 1 — Intake and baseline judgment

Goal: understand what the deck is for without over-questioning.

Collect only the essentials:
- what the PPT is for
- who the audience is
- rough length or duration
- what materials already exist
- whether there are concrete identity anchors such as school, company, laboratory, research group, course, product line, or brand entity that should ground the deck

When giving example choices in the first intake round, use broad common examples.
Recommended examples:
- purpose: 汇报 / 路演 / 答辩 / 产品介绍 / 培训 / 复盘 / 方案提案
- audience: 老板 / 客户 / 投资人 / 老师 / 同事 / 评审

Do not require the user to specify the desired overall tone in the first intake round.
If they volunteer it, you can use it.
If they do not, continue and surface style direction later in the dedicated style stage.

Then output a short baseline judgment:
- deck goal
- target audience
- recommended deck type
- recommended page range
- narrative spine
- usable identity anchors
- missing critical information

### Confirmation point 1 — 需求确认
Stop and let the user confirm or correct the baseline judgment.

---

## Stage 1.25 — Pre-style content research and report basis

After `需求确认` and before style-boundary alignment, create a content basis for the deck.

This stage should be the default rather than an exception.
Only compress it into extraction-only mode when the user has already provided a complete report, paper, project document, experiment record, full outline, or another complete narrative that is already strong enough to support page planning.

Use this stage to decide whether the work is:
- `整理但不扩写` — when the user already provided strong report-like content
- `补强并报告化生成` — when the user only provided a topic, thin materials, partial materials, or scattered notes

Goal:
- create an upstream content basis before style work
- make later previews content-bearing rather than generic
- give `design_spec.md`, `slide_blueprint.md`, and `spec_lock.md` a grounded content source
- avoid empty topic shells, placeholder logic, and shallow page planning

Output:
- the default artifact is `content_report.md`
- write it as a small research-style report / report-like article rather than a short outline
- if the user already provided a complete narrative, compress the work into extraction and structuring instead of extra expansion
- show the user a synthesized judgment by default instead of dumping the full report immediately

The content report should include:
- source status and material status
- problem background / topic framing
- core problem or core objective
- narrative body with connected reasoning rather than only bullets
- section candidates and page-content candidates
- visualizable content candidates
- claim status and open questions

Rules:
- do not turn this stage into a long questionnaire
- at most give one lightweight supplement opening
- distinguish `user_provided`, `inferred`, and `needs_confirmation`
- do not invent precise data, experimental results, citations, rankings, or institutional conclusions without support
- even if the user says not to expand content, still run this stage as extraction/structuring rather than skipping the content basis entirely
- later previews should use this content basis rather than a fresh generic topic outline

---

## Stage 1.5 — Style-boundary alignment

After `需求确认` and after any needed content-basis step, run one short style-boundary alignment step.

Ask only these 3 short questions in this stage:
1. `整体更偏亮色系、暗色系，还是中间态？`
2. `你希望这套 PPT 走常规专业路线，还是可以接受明显风格化的设计路线？`
3. `这次想先看几套风格方向预览？`

Show this helper note together with question 2:
`如果你没有特别偏好，默认选“常规专业路线”就行；只有当你明确想要更强设计感时，再选“明显风格化路线”。`

Show this helper note together with question 3:
`默认推荐先看 3 套，通常足够比较；如果你只想快速收敛，也可以少一点，如果你想多看一些方向，也可以多一点。`

Rules for this step:
- keep it short
- do not expand into a design questionnaire
- do not ask raw V1-V8 questions
- do not branch into subtype follow-up questions if the user allows the stylized route
- use the answers as boundary conditions for later style proposals rather than as a complete style definition
- if the user does not express a clear preference for question 2, default to `常规专业路线`
- if the user gives no clear answer on brightness, infer a middle brightness tendency unless the deck context strongly suggests otherwise
- if the user gives no clear answer on preview-count, default to `3` directions

---

## Stage 2 — Style proposal and preview

Once the request direction is confirmed:
- derive style vectors internally
- use the existing content basis as the source for preview content; if `content_report.md` exists, do not replace it with a fresh generic topic outline
- propose the user-requested number of style directions as lightweight proposal cards
- if the user gave no clear count, propose `3` directions by default
- generate exactly one preview image per direction
- use `正文页` (body page) as the preview page role by default; a body page is the only page role that can show visual style and content carrying capacity at the same time
- keep the same page role across all directions in the same round so the user can compare them fairly
- write the preview images into a local folder such as `<project>/previews/`, with filenames that map cleanly to direction codes, for example `A_正文页.png`, `B_正文页.png`, `C_正文页.png`
- do not assemble an HTML preview page, do not open a browser, and do not create a replacement preview UI
- after the images are written, give the user the absolute folder path so they can open the folder and look at the images directly
- show the proposal cards together with the filename mapping before asking for final selection

Each proposal must include:
- proposal name
- one-line positioning
- cover direction
- body-page visual grammar
- suitable scenarios
- risk note

The preview image must be content-bearing enough to evaluate.
Do not treat empty shells, placeholder copy, or mostly blank UI scaffolds as acceptable preview outputs.
If `content_report.md` or another content basis summary exists, the preview should draw from it directly: body-page content should come from the section/page candidates rather than generic placeholder topic logic.

Because only the body page is previewed, the cover direction in the proposal card is a design intent, not verified evidence.
Do not describe it as if the user has already seen the cover.

## Stage 2.5 — Style refinement

If the user is not ready to confirm a final direction yet, enter a style refinement round before `风格确认`.

In each refinement round:
- let the user choose one current direction as the base direction
- before deriving more options from that base, run one short refinement-time style inversion pass on that base direction
- in that pass, read the chosen preview image together with the original prompt and summarize what this direction actually became in the generated image
- surface which parts appear stable and suitable to inherit into the next round, and which parts may be one-off effects
- let the user say what they want adjusted on top of that now-clarified base
- derive another user-requested number of candidate directions from that base
- if the user gives no clear count for the refinement round, default to `3` derived directions
- generate exactly one new `正文页` preview image per derived direction
- write the round's images into the same `previews/` folder with a round prefix, for example `R2_A_正文页.png`
- give the user the absolute folder path again after each round
- do not assemble HTML or open a browser during refinement

During refinement, proactively give a few lightweight tweak prompts to help the user think, such as:
- `对比度高一点`
- `色彩再鲜艳一点`
- `更克制一点`
- `更有高级感一点`
- `信息感更强一点`
- `画面更轻一点`
- `文字多一点还是图片多一点`

Do not turn these prompts into a rigid option list.
Use them as guidance cues so the user can react in natural language.

Repeat refinement rounds until the user is ready to confirm one final direction.

When presenting a refinement round result, explicitly remind the user that there are 2 valid next paths:
- `继续沿某个方向再推一轮`
- `就以当前某个方向结束风格阶段，进入后续定稿与生成`
Do not phrase the result as if the only next step is immediate final selection.

### Confirmation point 2 — 风格确认
Stop and let the user choose, mix, or revise the style direction.

---

## Stage 2.75 — Style inversion confirmation

After `风格确认` and before writing any planning files, run one short `风格反演确认` stage.

In this stage:
- read the chosen preview image as visual evidence rather than treating the original prompt text as the whole truth
- compare the actual image with the original generation prompt and identify what the model really produced
- extract stable style facts such as brightness range, palette role usage, material feel, lighting/depth behavior, container grammar, edge treatment, decoration grammar, information density, text-image balance, and overall restraint level
- also extract theme-specific or scene-specific liked elements that may matter to the user, such as school emblems, campus buildings, company marks, laboratory context, domain imagery, clouds, devices, chart language, or other subject anchors
- distinguish between what this image reliably shows and what only works as a one-off local flourish
- because only one body page was previewed, explicitly mark style aspects that were never previewed — cover atmosphere, TOC structure, multi-page rhythm — as unverified intent rather than locking them as evidence-based facts

When reporting the inversion result to the user:
- do not ask an open-ended style interview
- first present a short structured judgment in 3 groups:
  - `明确应延续的`
  - `效果好但需要确认是否整套延续的`
  - `只在当前图里偶然成立，不建议直接锁死的`
- then let the user confirm, remove, or promote items between those groups
- if the user gives no correction, keep the first group by default and do not automatically hard-lock the second group

Rules:
- trust the confirmed preview evidence more than the raw prompt wording when they differ
- only lock features that are clearly visible in the selected preview or explicitly confirmed by the user
- do not mistake rendering accidents, one-off decorations, typo-like artifacts, or isolated composition tricks for deck-level style facts
- do not upgrade cover-only or TOC-only ideas into locked deck-wide facts when those page roles were not previewed
- use the confirmed inversion result to make the later planning files more concrete than the original prompt alone could support
- record the single-preview coverage limit in the planning files

## Stage 3 — Planning files

Do not enter this stage while style refinement is still active.
Do not enter this stage before `风格反演确认` is finished.
After the style is confirmed and the inversion result is confirmed, generate the 3 planning artifacts in this exact order:
1. `design_spec.md`
2. `slide_blueprint.md`
3. `spec_lock.md`

Then output a short pre-generation summary instead of dumping all files.

The summary should cover:
- project overview
- chosen style result
- deck-level continuity anchor
- preview coverage limit (only the body page was previewed)
- page structure summary
- execution readiness

### Confirmation point 3 — 生成前确认
Stop and let the user confirm whether generation can start.

---

## Stage 4 — Generation

Only after the 3rd confirmation point may you proceed into downstream generation.

Before the first full generation pass, ask one short branch question:
- `最终页这次是每页先出 1 张直接进评审，还是每页先出多张候选再挑？`

Rules for this branch:
- keep it short and operational
- if the user wants the multi-candidate path, also ask how many candidates per slide they want
- if the user chooses the single-candidate path, skip the candidate-selection stage entirely
- if the user gives no clear preference, default to one final image per slide and go directly into review

Generation in this skill should stay image-first.
That means:
- when image generation is available, use an available image-generation toolchain from the environment such as a tool, MCP server, or skill to produce the page visuals
- do not silently fall back to a traditional element-by-element PPT workflow as the main rendering path when image generation is available
- do not skip image generation and directly assemble the final deck only from default PPT shapes, text boxes, layout primitives, custom-drawn vectors, SVG-like code, or programmatic page reconstruction unless the user explicitly asks for that approach
- if the confirmed direction depends on generated page visuals, actually generate those visuals and use them in the final deck
- do not hand-build substitute page art yourself with code just because it is easier or more controllable than calling the image-generation path
- do not justify code overlays by saying they are more accurate, more controllable, safer for text, faster, or less likely to cause layout drift; those reasons are not valid grounds for bypassing the image-generation path
- do not silently switch to textless or background-only generated images just to avoid rendering text problems
- when a requested revision changes visible page content, including titles, labels, annotations, bottom cards, captions, metrics, explanatory text, or result summaries, handle it through image edit/regeneration by default
- if image editing/regeneration is unavailable or unsuitable, stop and tell the user before using any deterministic overlay method
- if you choose to keep PPT text editable while using generated visuals, that must still preserve the confirmed style direction and must not collapse into generic background art plus ordinary default slides
- treat generated page visuals as complete outputs by default, not as underlays for a second design pass
- post-generation overlays should default to zero
- do not treat generated images as mere background plates and then invent a second layer of titles, metrics, bullets, labels, callouts, captions, badges, or decorative elements on top unless those overlay contents were already defined by the confirmed content plan and are explicitly traceable to approved blueprint fields
- do not add self-authored editable copy just because the generated page looks sparse or because editable text feels safer
- do not add explanatory boxes, correction notes, patch text, or rescue text to compensate for weak generation output; fix the generation path instead
- when editable overlays are necessary, they should come from the approved slide content and should be used to realize the confirmed page, not to redesign it after the fact
- PIL/Pillow may be used only for mechanical format conversion, dimension checks, or packaging support; it must not create, replace, correct, or overlay audience-facing slide content in preview images, selected final images, reviewed pages, or final PPT visuals
- if image generation quality, text rendering limits, or tooling constraints force a tradeoff, tell the user explicitly before changing generation strategy

The final generation should remain faithful to the confirmed preview logic rather than drifting into a different production method.
Unless the user explicitly requests another presentation ratio, generate preview images and final page visuals in `16:9`.
Do not let the image-generation path default to a generic art ratio such as `3:2`.

Before writing per-slide generation prompts, extract the confirmed direction into one explicit deck-level continuity anchor.
Every slide prompt must inherit that anchor first, then add only page-role and content-specific variation.
Do not write slide prompts as independent style descriptions.
If one slide would naturally become darker, brighter, flatter, glossier, or more atmospheric than the rest, explicitly test that change against the allowed variation range before keeping it.

Prompt assembly metadata isolation:
- maintain slide IDs, candidate codes, filenames, and generation batch labels in a separate mapping table or local variables
- do not concatenate those identifiers into the text prompt sent to the image model
- do not format per-slide prompt bodies with production headers; use a separate executor-side label for logs and filenames
- the prompt body should contain only the approved audience-facing slide content, page role, visual direction, continuity anchor, layout intent, and any visible labels that should actually appear in the slide
- after generation, reconnect outputs to slide IDs through filenames or the external mapping table, not through text embedded in the image prompt

If the user chose single-candidate generation:
- generate one final image per slide into `<project>/slides/`, using filenames such as `S01.png`, `S02.png`
- skip the candidate-selection stage entirely
- move directly into the folder review stage

If the user chose multi-candidate generation:
- generate the requested number of final candidates for each slide using the same approved page prompt for that slide
- keep the variation inside one approved page direction rather than treating the candidates as new style proposals
- write the candidates into `<project>/slides_candidates/` with filenames such as `S01-01.png`, `S01-02.png`
- do not assemble a candidate-picker HTML page, do not open a browser, and do not create any replacement selection UI
- give the user the absolute candidate folder path
- tell the user to reply in chat with one line per slide, in the form `S01-03`, using the candidate number in the filename
- wait for the returned selection codes before entering the review stage
- once the codes arrive, map them to the selected page images by filename and copy or reference that chosen set as the review input

### Confirmation point 4 — 初稿评审与返修
Do not jump directly from first-pass page generation to final delivery.
After the first full set of page visuals exists, enter a dedicated review-and-retouch loop.

---

## Stage 5 — Review and retouch

After the first full set of page visuals is ready:
- make sure every generated page is written into `<project>/slides/`
- give the user the absolute folder path and tell them to review the images directly in the folder
- do not assemble a review HTML page, do not open a browser, and do not create any replacement review UI
- treat the image folder as the main review surface instead of using the live PPT as the collaboration surface by default

When you present the review stage to the user, explicitly tell them:
- if the current result is satisfactory, they can say it is approved and the review stage can end
- if the current result is not satisfactory, they should describe the problem directly in chat, per slide, by slide ID or filename, for example `S03 右上角太空` or `S05 整页重做`
- no JSON payload, annotation file, or browser page is needed
- if they prefer, they can mark the images themselves and point to the marked files, but this is optional

When the user gives review feedback, classify it before acting:
- `full-page regeneration` → use when the user wants broader changes to composition, hierarchy, page concept, style intensity, or overall mood
- `local image edit` → use when the user wants targeted changes to a specific region, background element, rendered text area, spacing, emphasis object, or small visual detail
- `content/blueprint issue` → use when the user is actually changing approved content, narrative structure, or page intent rather than only changing the rendered page

Execution rules:
- prefer an available image-editing path from the environment for local image edits
- prefer full-page regeneration for broad or structural dissatisfaction instead of forcing many small edits
- do not solve review feedback by adding unapproved PPT overlays
- do not treat the PPT file itself as the fast-turnaround retouch surface unless the user explicitly asks for that workflow
- if the requested revision would change approved content rather than only visuals, surface that explicitly before editing
- after each retouch round, list which image files were updated (with filenames), give the folder path again, and repeat the same approval-or-feedback instruction
- repeat the review-and-retouch round until the user confirms that the pages are ready for final delivery
- do not export the final PPT before that approval
- once the user approves the reviewed pages, export the final PPT and immediately attempt to open it for them

## Important rules

- Do not write the planning files before the style direction is confirmed.
- Do not turn the interaction into a parameter form.
- Do not ask for repeated approval inside a stage.
- Keep the first confirmation quick, the second heavy, the third short, and the final review stage iterative.
- The preview stage produces exactly one `正文页` image per direction; do not add cover or TOC previews unless the user explicitly asks for them.
- Preview and review are folder-based; never fall back to assembling or opening an HTML shell.