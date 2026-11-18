# Preview Flow

## Purpose

The preview stage lets the user judge a style direction visually before planning the full deck.

## Fixed preview set

Each style direction must generate exactly **1 preview image**.

- The preview page role is `正文页` (body page) by default.
- Reason: the body page is the only page role that shows visual style and content carrying capacity at the same time. A cover mainly shows atmosphere, and a TOC page mainly shows structure.
- All directions presented in the same round must use the same page role so the comparison stays fair.
- The image must be generated in a `16:9` slide ratio unless the user explicitly asks for another presentation format.

A valid preview image must contain plausible filled content rather than placeholder-only structure.
That means:
- believable headings, bullets, labels, cards, numbers, or relationships with enough content to judge usability
- do not generate placeholder text such as “在此输入…”, “title here”, “lorem ipsum”, or empty label boxes intended to be filled later
- do not generate large empty containers, blank dashboard shells, or decorative modules with no real information inside
- do not silently switch to textless image generation just to avoid text rendering problems

Text sketches, ASCII boxes, pseudo-layouts, and purely verbal examples do **not** count as previews in this workflow.

If `content_report.md` or another approved content-basis summary exists, preview content must draw from it.
That means:
- the body page should use page-content candidates, visualizable content, or report-derived arguments rather than generic filler structure
- do not create a second unrelated topic outline during preview generation when a content basis already exists
- if part of the preview content is inferred rather than user-provided, keep it general and avoid unsupported precise claims

## Delivery

- Write preview images into a local folder, for example `<project>/previews/`.
- Filenames must map cleanly to direction codes, for example `A_正文页.png`, `B_正文页.png`, `C_正文页.png`.
- Refinement rounds use a round prefix, for example `R2_A_正文页.png`.
- After the images are written, give the user the absolute folder path. The folder is the comparison surface.
- Do not assemble a preview HTML page, do not open a browser, and do not create any replacement preview UI.

## Presentation principle

For each style direction, show in chat:
- the lightweight proposal card text
- the preview filename that maps to that direction

Do not ask the user to open images one by one; they can browse the folder directly.
Do not describe the cover direction as if the user has already seen it — only the body page has been previewed.

## Comparison principle

The number of style directions may vary by user preference, but all directions in the same round must use the same page role so the user can compare them fairly.

## Coverage note

Because only a body page is previewed:
- cover-specific and TOC-specific style claims remain design intent, not verified preview evidence
- do not lock cover atmosphere, TOC structure, or multi-page rhythm as facts derived from the preview
- the planning files should record this coverage limit explicitly

## Hard rule

Style selection should default to preview-first.
That means:
- do not jump directly from proposal text to asking the user to choose a final direction
- first show the preview images when generation is possible
- previews should be generated as real images by default
- if real image previews are not yet available, explicitly tell the user that preview display is part of the workflow and say what is blocking it right now

The user must never be left with the impression that style choice is text-only by default.

## Generation expectation

If an image-generation path is available in the environment, use it for previews.
Prefer whatever image-generation capability is currently available in the environment when preview images are needed, but do not assume a specific model, provider, or tool brand.
The image prompts should inherit both the style direction and the current content basis, rather than only the visual style request.
Do not downgrade to text mockups silently.
Only fall back to text-only examples when:
- the user explicitly asks for rough mockups only, or
- real image generation is unavailable right now and you have clearly told the user so.

## Speed and QA rule

The preview stage is a directional comparison step, not a polishing pass.
That means:
- generate the planned preview set directly instead of repeatedly testing one image at a time unless the generation path itself is unverified
- at most one minimal chain check is enough when the local generation path has not yet been confirmed in the current turn
- after the chain is confirmed, generate the remaining previews in batch without repeated intermediate spot-check loops
- do not regenerate an image just to slightly improve a candidate unless the result is clearly broken, unreadable, or off-direction
- do not run multiple rounds of manual re-checking before showing the user the preview set
- once each direction has a usable preview image, write the files and give the user the folder path
- apply the same speed rule during style refinement rounds; refinement is another comparison loop, not a polishing detour

Favor speed, comparability, and directionality over internal perfectionism at this stage.
