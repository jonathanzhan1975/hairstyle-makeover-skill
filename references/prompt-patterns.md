# Prompt Patterns

Use these patterns when turning hairstyle recommendations into image-edit prompts.

## Core principle

The prompt must explicitly define:
- what changes
- what stays the same

If this boundary is weak, the model may change face, age, skin, or overall appearance instead of only the hair.

## Base prompt skeleton

```text
Use the attached portrait as the identity reference. Edit the hairstyle of the exact same person.

Keep the exact same face identity, facial proportions, age impression, skin tone, glasses, facial hair, clothing, pose, body shape, lighting direction, and background. Only change the hairstyle.

Change the hair to: [STYLE DEFINITION]

Make the result look like a realistic real-life hairstyle try-on photo. Keep believable hair density, natural texture, and practical styling. Avoid fashion-poster exaggeration.

Do not change the eyes, nose, mouth, jawline, head shape, ethnicity, expression, skin texture, glasses, beard, outfit, or background. Do not beautify the face. Do not make the person younger. Do not add makeup. Do not create dramatic curls, extreme fades, or glossy salon styling.
```

## Multi-angle board pattern

```text
Use the attached portrait photo as the identity reference. Create a realistic hairstyle try-on board for the exact same person.

Each row is one hairstyle option. Each row must show the same hairstyle from these angles: front, left three-quarter, right three-quarter, side.

Keep the person clearly the same in every panel: same facial identity, same glasses, same age impression, same skin tone, same facial hair, same clothing style, and same natural realism. Only change hairstyle and viewing angle.
```

## Style insertions

### Natural business side part

```text
a refined business-style short haircut with clean lines, understated structure, slightly more lift at the crown, mature and professional, neat sides but not harshly faded
```

### Natural 3:7 layered side part

```text
a natural 3:7 side-part layered short haircut with light top volume, subtle layering, tidy sides, and a soft natural side sweep
```

### Light volumized layered short hair

```text
a short layered haircut with gentle lift at the top and front, airy but not spiky, with natural density and controlled texture
```

### Classic Ivy League short hair

```text
a classic Ivy League short haircut with a slightly longer top, subtle side part, clean and balanced shape, polished but natural
```

### Soft Korean side part

```text
a soft Korean-inspired side-part hairstyle with very subtle texture, moderate top volume, a cleaner silhouette, understated and age-appropriate
```

### Textured short crop

```text
a short textured crop with mild separation and soft movement on top, tidy sides, restrained texture, and practical realism
```

### Brushed-up short hair

```text
a short haircut brushed slightly upward in the front with light top structure, clean and realistic, more shaped than dramatic
```

### Short neat crew cut

```text
a neat short crew cut, practical and simple, clean around the sides, short but not aggressively shaved
```

## Recommendation-board labeling

When generating a comparison board, keep labels short and clean. Prefer:
- `PERFECT`
- `GOOD`
- `LESS IDEAL`

For large boards, sort from strongest recommendation to weakest recommendation.
