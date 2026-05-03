---
name: hairstyle-makeover
description: Analyze a portrait photo for hairstyle-focused image makeover work. Use when Codex needs to inspect a person's current hair, recommend ranked hairstyle options, generate practical "perfect / good / less ideal" guidance, prepare structured image-edit prompts that keep the same person, or create multi-angle hairstyle try-on plans and outputs for realistic portrait edits.
---

# Hairstyle Makeover

Use this skill to turn a single portrait into a practical hairstyle recommendation package.

The default outcome is:
1. Judge whether the photo is usable.
2. Analyze head, face, hair, and styling constraints.
3. Recommend ranked hairstyle options.
4. Generate image-edit prompts that keep the same person and only change hair.
5. If image editing is available, generate try-on images with multiple hairstyles and angles.

## Workflow

### 1. Check photo usability

Read [references/analysis-rubric.md](references/analysis-rubric.md) first.

Assess:
- face visibility
- hairline visibility
- crown and side visibility
- blur, filter, and lighting quality
- whether the image is suitable for multi-angle hairstyle planning

If the image is imperfect, continue with conservative recommendations and explicitly note the weak spots.

### 2. Extract hairstyle-relevant traits

Use the analysis rubric to describe:
- face-shape tendency
- forehead and hairline exposure
- crown height and top-volume needs
- hair density impression
- current hairstyle strengths
- current hairstyle problems
- age impression and styling tolerance

Do not pretend to measure exact geometry. Prefer phrases such as "visually tends toward" and "from this photo".

### 3. Build a hairstyle strategy

Before recommending specific cuts, convert the analysis into strategy:
- what should stay stable
- what should be corrected
- where volume should increase or decrease
- whether the forehead should be more open or more framed
- how conservative or expressive the styling should be

For portraits similar to the validated experiment in this project, prioritize:
- same-person realism
- moderate edits
- practical daily wear
- clean text and understandable recommendation tiers

### 4. Recommend ranked hairstyles

Read [references/hairstyle-library.md](references/hairstyle-library.md).

Default recommendation shapes:
- 3-option mode: `perfect`, `good`, `less ideal`
- 4-option mode: `most recommended`, `strong option`, `alternative`, `style-forward option`
- 8-option mode: full ranked board from most recommended to least recommended

Each hairstyle recommendation must include:
- concise hairstyle name
- tier or ranking
- one-line positioning
- why it suits the person
- what it fixes or improves
- practical risk or tradeoff

Avoid recommending eight tiny variants of the same haircut. Keep the options distinct.

### 5. Generate edit prompts

Read [references/prompt-patterns.md](references/prompt-patterns.md).

For every hairstyle option, generate a structured edit prompt that clearly separates:
- the goal
- what must stay unchanged
- what hair attributes may change
- realism requirements
- forbidden changes

The prompt must strongly preserve:
- same face identity
- same age impression
- same skin tone
- same glasses, beard, and clothing when visible
- same body shape, pose, and background unless the user requests otherwise

Never let hairstyle prompts silently become full beauty-retouch prompts.

### 6. Create image outputs when available

If an image editing/generation tool is available, use the prompts to generate:
- single-variant try-on images
- comparison boards
- multi-angle boards

For multi-angle outputs:
- keep the hairstyle constant within a row
- vary angle only
- label angles cleanly
- keep the person recognizable in every panel

If image generation is not available, return the finished prompts and the intended layout.

### 7. Format the final result

Read [references/output-template.md](references/output-template.md).

Default presentation style:
- ordinary-user friendly
- lightly polished, small-card friendly
- practical rather than technical
- concise, calm, and specific

When the user wants article-style output, emphasize:
- consistency
- moderate edits
- clear ranking
- practical explanation instead of hype

## Decision Rules

- Prefer hairstyle edits that feel like a believable improvement of the same person.
- Prefer natural realism over dramatic fashion styling.
- Prefer moderate volume and structure over extreme texture.
- If the person already has a workable parting direction, treat that as useful prior information.
- When uncertain, rank conservative options above trend-heavy options.

## Common Requests

### Rank three hairstyles

Return:
- `perfect`
- `good`
- `less ideal`

Explain the ranking in plain language.

### Create a four-style board

Return four distinct styles and, if possible, a matching four-panel or multi-row image output.

### Create an eight-style ranked board

Return eight ranked styles ordered from strongest match to weakest match. When generating images, show the board in recommendation order.

### Generate multi-angle previews

Within each hairstyle row, keep the same style and vary only the viewing angle:
- front
- left three-quarter
- right three-quarter
- side

## Resources

- Use [references/analysis-rubric.md](references/analysis-rubric.md) for portrait diagnosis.
- Use [references/hairstyle-library.md](references/hairstyle-library.md) for hairstyle types and ranking guidance.
- Use [references/prompt-patterns.md](references/prompt-patterns.md) for structured image-edit prompts.
- Use [references/output-template.md](references/output-template.md) for user-facing recommendation formatting.
- Use [references/extension-notes.md](references/extension-notes.md) when extending the skill beyond hairstyle work.
