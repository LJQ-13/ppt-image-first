# Style System

## Core principle

Do not rely on rigid templates as the primary style system for PPT visual design.
Use a parameterized style vector internally, then synthesize multiple coherent style proposals.

This rule is about the deck's visual language, not about workflow UI files.
This workflow has no workflow UI files: previews, candidate selection, and review are all folder-based and chat-based. Do not reintroduce an HTML shell for those stages unless the user explicitly asks for a browser-based variant.

## Style vectors

- `V1` Layout System
- `V2` Texture & Material
- `V3` Lighting & Depth
- `V4` Color Palette
- `V5` Containers & Motifs
- `V6` Density & Rhythm
- `V7` Text–Visual Balance
- `V8` Brand Constraint Level

## Control split

### User-controlled dimensions
These should primarily follow the user's intent or hard constraints:
- `V6` Density & Rhythm
- `V7` Text–Visual Balance
- `V8` Brand Constraint Level
- `V4` Color Palette when brand or industry constraints are explicit

### AI-proposed dimensions
These should be synthesized by the agent into candidate directions:
- `V1` Layout System
- `V2` Texture & Material
- `V3` Lighting & Depth
- `V5` Containers & Motifs

## V5 rule

`V5` must use two different grammars:
- **Cover pages** → visual metaphors
- **Body pages** → information containers

Do not describe body pages as one fixed layout. Describe the body-page **visual grammar** instead:
- how information is organized
- where unity comes from
- how different page types vary while staying in one system

## Intra-direction continuity

Within one style direction, the deck's pages must read as one visual family rather than loosely related images.

Because the preview stage produces only one `正文页` image per direction, continuity across page roles cannot be verified visually at preview time.
That means:
- the single preview image defines the direction's body-page visual grammar
- cover, TOC, and multi-page rhythm consistency is carried by the planning files and the deck-level continuity anchor, not by preview evidence
- do not claim that a direction is "verified consistent across page roles" when only the body page was generated

Continuity should come from a shared visual system, including as appropriate:
- the same or clearly related color palette
- the same lighting logic and depth behavior
- the same material language
- the same container language and edge treatment
- the same decorative grammar
- the same title / label / emphasis tone
- the same level of restraint or expressiveness

Allowed variation:
- the cover may be more atmospheric and metaphor-driven
- the table-of-contents page may be more structural
- the body page may be more informational

Not allowed:
- changing the style language so much that pages look like different template families
- introducing a new material system or illustration language only on one page
- making the cover futuristic, the TOC editorial, and the body dashboard-heavy unless that transition still clearly belongs to one shared system

Think of each direction as one deck identity expressed across page roles, not separate design attempts.

## Deck-level continuity anchor

After one style direction is confirmed, do one short reverse-engineering pass on the selected preview before writing planning files or generating final visuals.

Use that pass to infer what the chosen direction became in the actual image, not just what the prompt originally asked for.
The confirmed continuity anchor should therefore be based on:
- the selected preview image as the primary evidence
- the original generation prompt as supporting context
- the user's confirmation of which extracted elements they actually want to preserve

After that, convert the direction into a single deck-level continuity anchor.

This anchor must be explicit enough that every later slide can inherit it.
At minimum it should lock what the preview actually shows:
- base brightness range and background tendency
- dominant palette and secondary palette roles
- lighting model and depth strength
- material language
- container grammar and edge treatment
- decoration grammar
- title / label / emphasis tone
- restraint vs expressiveness level

For aspects the preview never covered — cover atmosphere, TOC structure, cross-page rhythm — write them as intent derived from the proposal card and content basis, and mark them as unverified rather than locked evidence.

Use this anchor to prevent "same style but different mood" drift.
For example, do not let one slide become dark, glossy, and high-contrast while the next becomes bright, airy, and nearly flat unless that range was explicitly defined as part of the confirmed system.

The continuity anchor is not a long image prompt.
It is the stable deck identity that all per-slide image prompts, page blueprints, and execution constraints must inherit.

Per-slide prompts may vary by page role and content, but they must stay inside the same anchor.
Do not treat slides as independent prompt-writing tasks.

## Proposal card

Each style proposal must stay lightweight:
- proposal name
- one-line positioning
- cover direction
- body-page visual grammar
- suitable scenarios
- risk note

The proposal card is only the presentation interface. It must not constrain the creative generation process.

The cover direction in the card is a stated design intent. It is not backed by a generated cover preview, because the preview stage produces only a body page.
