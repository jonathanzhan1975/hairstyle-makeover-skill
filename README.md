# Hairstyle Makeover Skill

`hairstyle-makeover` is a Codex skill for realistic hairstyle recommendation and portrait try-on planning.

It is built around one practical idea:

> Do not ask the model to "make a new person look good".
> Ask it to keep the same person, define clear edit boundaries, and only change the hair.

This skill takes a single portrait photo and helps Codex:
- analyze hairstyle-relevant facial and hair cues
- recommend ranked hairstyle options
- output `perfect / good / less ideal` recommendations when needed
- prepare strong "same person, only change hair" edit prompts
- plan or generate multi-style, multi-angle hairstyle try-on boards

The workflow is inspired by the article:
- [一直想要的发型、穿搭推荐，在ChatGPT Image2上实现了](https://mp.weixin.qq.com/s/6Y4tLi8z0COhT2oyDFjv9g)

That article emphasizes a few important principles which this skill adopts:
- person consistency matters more than flashy styling
- prompt structure matters more than long prompt length
- clearly separate what may change from what must stay the same
- keep recommendations practical and moderate
- present the result like a recommendation board, not just a raw model output

## What This Skill Does

Given a portrait, this skill can:

1. Judge whether the photo is good enough for hairstyle analysis.
2. Read hairstyle-relevant features such as face-shape tendency, hairline visibility, top flatness, side bulk, density impression, and current hairstyle issues.
3. Turn those observations into a hairstyle strategy.
4. Recommend ranked hairstyle options, from highly suitable to less suitable.
5. Generate structured image-edit prompts that preserve:
   - same person
   - same age impression
   - same glasses, beard, and clothing
   - same background and lighting direction
6. Create plans for:
   - 3-style recommendation sets
   - 4-style comparison boards
   - 8-style ranked hairstyle boards
   - 4-angle previews for each hairstyle

## Why This Skill Exists

Most hairstyle demos do one of two things:
- they generate a hairstyle image but do not explain why it is suitable
- or they analyze the face but do not produce realistic edit prompts

This skill tries to connect both sides:
- portrait analysis
- recommendation logic
- image-edit prompt design
- recommendation-board formatting

The goal is not just "AI beauty advice".
The goal is a repeatable workflow for realistic hairstyle makeover work.

## Core Method

This repository follows the same broad logic validated in the article-inspired experiments:

### 1. Analyze first

Do not jump straight to generation.

First determine:
- whether the image is usable
- what currently works
- what looks flat, heavy, severe, or under-styled
- how much styling change the portrait can tolerate

### 2. Translate analysis into strategy

Instead of recommending random styles, define:
- where volume should increase
- whether the forehead should open more or stay framed
- whether the style should stay conservative or become more expressive
- how much texture is safe before the result stops feeling like the same person

### 3. Rank styles, do not just list them

This skill supports recommendation tiers such as:
- `perfect`
- `good`
- `less ideal`

And also larger ranked boards when the user wants to compare many options.

### 4. Lock the person's identity

Every good edit prompt must explicitly preserve:
- face identity
- age impression
- skin tone
- glasses
- facial hair
- pose
- outfit
- background

Only the hairstyle is allowed to change.

### 5. Prefer realistic try-on boards

The preferred output is not a glossy poster.
It is a believable "same person, different hairstyle" comparison board that ordinary users can trust.

## Repository Structure

```text
hairstyle-makeover/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── analysis-rubric.md
    ├── extension-notes.md
    ├── hairstyle-library.md
    ├── output-template.md
    └── prompt-patterns.md
```

## Files

### `SKILL.md`

The main skill instructions.

It defines:
- when to use the skill
- the end-to-end workflow
- ranking modes
- prompt-generation rules
- multi-angle image board guidance

### `references/analysis-rubric.md`

Portrait diagnosis rules:
- photo quality checks
- head and face cues
- hair cues
- current-style diagnosis
- recommendation priorities

### `references/hairstyle-library.md`

Recommendation inventory and ranking guidance.

It includes practical families such as:
- natural business side part
- natural 3:7 layered side part
- light volumized layered short hair
- classic Ivy League short hair
- soft Korean side part
- textured short crop
- brushed-up short hair
- short neat crew cut

### `references/prompt-patterns.md`

Structured prompt templates for:
- single hairstyle try-on edits
- multi-angle hairstyle boards
- recommendation-tier labels

### `references/output-template.md`

User-facing formatting guidance for:
- short recommendation outputs
- full recommendation reports
- small-card style summaries

### `references/extension-notes.md`

Notes for expanding the skill later into:
- glasses recommendation
- beard shaping
- broader image makeover work

## Example Use Cases

### 1. Recommend three styles

Example request:

```text
Use $hairstyle-makeover to analyze this portrait and recommend one perfect, one good, and one less ideal hairstyle.
```

### 2. Generate a four-style try-on board

Example request:

```text
Use $hairstyle-makeover to analyze this portrait, recommend four strong hairstyle options, and prepare same-person try-on prompts.
```

### 3. Generate an eight-style ranked board

Example request:

```text
Use $hairstyle-makeover to create an eight-style ranked hairstyle board with four viewing angles for each style.
```

## Recommended Output Style

This skill is designed for results that feel:
- practical
- moderate
- believable
- suitable for ordinary users
- compatible with small-card / social-post presentation

It intentionally avoids:
- overdesigned fashion styling
- dramatic identity drift
- excessive prompt bloat
- vague "you can try anything" advice

## Design Principles

This project is intentionally conservative in a good way.

It assumes the best hairstyle recommendation system should:
- improve the same person, not replace them
- explain why a style fits
- rank options instead of dumping a list
- generate prompts with explicit constraints
- make image outputs look like real try-on previews

## What Is Not Included

- The portrait photos used in local experiments are not included in this repository.
- Generated try-on images from local testing are not included in this repository.
- The repository focuses on the skill logic, not a full web product.

## Validation

The skill structure was validated with the standard skill validator:

```bash
python .../quick_validate.py path/to/hairstyle-makeover
```

## Future Improvements

Potential next steps:
- add preset style packs such as business, natural, youthful, and style-forward
- add image-layout templates for recommendation boards
- add more age-group-specific ranking heuristics
- add expansion modules for glasses and broader image makeover work

## Credits and Inspiration

Methodology inspiration:
- [一直想要的发型、穿搭推荐，在ChatGPT Image2上实现了](https://mp.weixin.qq.com/s/6Y4tLi8z0COhT2oyDFjv9g)

This repository does not re-upload the local portrait experiments used during development.
It focuses on the reusable skill and workflow derived from that methodology.
