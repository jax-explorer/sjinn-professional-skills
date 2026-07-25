---
name: mechanical-toy
description: >-
  Generate three production-ready prompts that turn any creature, animal,
  vehicle, robot, mythical entity, object, machine, structure, or other visual
  subject into a hyper-realistic premium mechanical transformation toy: a
  sealed compact-device image prompt, a fully transformed image prompt, and a
  continuous image-to-video transformation prompt. Use for mechanical-toy
  concepts, transformation-toy prompts, transforming pods or capsules,
  collectible mechanical transformers, satisfying mechanical unfolding
  videos, or requests to convert a subject into a compact device that
  physically unfolds into its final form.
---

# Mechanical Toy

Turn the user's subject into a mysterious one-hand-held mechanical pod and its fully unfolded collectible form. Write all prompts in polished, production-ready English for modern image and video generators.

## Workflow

1. Treat any supplied subject as sufficient. Do not ask follow-up questions.
2. Choose one compact shape, one metallic finish, and one subject-appropriate color palette.
3. Reuse those exact design descriptors across all three prompts.
4. Adapt the mechanical anatomy and transformation sequence to the subject.
5. Generate all three required prompts immediately.
6. Validate the result silently and return only the required output.

Do not explain, summarize, or add setup instructions. Do not generate assets or invoke media tools unless the user explicitly asks for generation in addition to the prompts.

## Core Concept

Show a small sealed mechanical pod held in one hand. A thumb presses its recessed button, the pod is placed on a white surface, and it unfolds through intricate mechanical articulation into the requested subject.

Make the result:

- satisfying, realistic, cinematic, engineered, tactile, and physically believable
- hyper-detailed enough to resemble a premium collectible mechanical transformer
- compact before transformation and only moderately larger afterward

## Shared Visual Rules

Apply all of these rules to every prompt:

- Hyper-realistic cinematic realism with photorealistic materials
- Handheld POV captured like iPhone 15 Pro Max footage
- Portrait orientation
- Shallow depth of field
- Natural ambient lighting
- Subtle lens imperfections
- Realistic reflections and shadows
- Tactile metallic materials
- A clean white surface or white tabletop
- No text, logos, labels, watermarks, or background clutter

Keep the compact and transformed states visually continuous:

- Use the exact same metallic finish and color palette.
- Make them feel like the same physical object before and after transformation.
- Preserve plausible material volume: every final structure must appear to unfold, telescope, rotate, extend, or interlock from the compact device.

## Design Lock

Before writing, silently define:

- `compact shape`: rounded cube, oval capsule, flattened sphere, or another compact industrial-device form
- `metallic finish`: a precise material and surface treatment
- `color palette`: colors naturally associated with the subject
- `signature mechanics`: anatomy-specific joints, panels, hinges, rails, housings, and linkages

Reuse the exact finish, shape, and palette wording in all three prompts. Examples of subject-appropriate finishes include dark bronze for a scorpion, gunmetal gray for a shark, icy silver-blue for an arctic wolf, emerald metallic green for a mantis, and sand-colored titanium for a desert creature.

## Image Prompt — Compact Device

Describe:

- one compact, sealed mechanical pod held in one hand only
- a downward-looking handheld POV
- the other hand completely outside the frame
- slight natural handheld sway and subtle phone-camera motion blur
- a smooth outer shell with a matte metallic finish
- subtle seam lines, tiny mechanical panel separations, and one recessed button
- a mysterious industrial object that does not reveal its final subject

Do not show visible creature hints, limbs, eyes, anatomy clues, deployed components, or recognizable parts of the final form.

## Image Prompt — Fully Transformed

Describe:

- the exact same environment, POV angle, lighting, white surface, finish, and palette
- no hands visible
- the requested subject fully unfolded on the surface
- highly articulated mechanical anatomy
- visible joints, segmented panels, and a functional engineered structure
- photorealistic metallic detailing
- subject-specific articulation and anatomy

Include this size construction explicitly, replacing the bracketed terms with the locked descriptors:

```text
roughly 1.5 to 2 times the size of the compact [finish] [shape] device
```

Make the transformed form functional and engineered. Use specific mechanisms such as layered wing-panel deployment, rotating mandibles, segmented fin hinges, telescoping claws, interlocking tail sections, ratcheting spinal armor, or other structures appropriate to the chosen subject.

## Video Prompt — Transformation Sequence

Write one continuous cinematic paragraph with no timestamps and no bullet points.

Begin exactly with:

```text
[Style: hyper-realistic, handheld POV, shallow depth of field, natural ambient lighting, ASMR mechanical sounds, no music, portrait orientation]
```

Describe the action in this exact order:

1. One hand holds the sealed compact device.
2. The camera has natural handheld sway.
3. The thumb presses the recessed button.
4. An audible mechanical click sounds.
5. The device is placed onto the white surface.
6. The hand withdraws completely from the frame.
7. The device shudders and begins transforming.
8. Subject-specific mechanical anatomy unfolds.
9. Panels rotate and lock into place.
10. A final locking clunk completes the transformation.
11. The camera subtly drifts closer to reveal the final form.

Describe concrete anatomy, mechanics, articulation, unfolding structures, and moving engineered parts. Prefer precise motion such as:

- segmented wing panels telescope from layered shoulder housings
- articulated mandibles rotate from concealed cheek compartments
- spinal armor plates separate and ratchet backward along micro-hinged rails

Keep the metallic finish and palette consistent throughout. Emphasize ASMR clicks, servo movements, ratcheting joints, metallic locks, and hydraulic micro-motions. Do not include music, explosions, magical effects, unrealistic energy effects, or glowing anime effects.

## Subject Adaptation

Tailor the color palette, finish material, articulation style, mechanical structure, and transformation behavior to the user's subject.

- For an insect, emphasize a segmented exoskeleton and multi-jointed appendages.
- For a bird, emphasize feather-like panel deployment and articulated wings.
- For a sea creature, emphasize unfolding fins and hydrodynamic surfaces.
- For a dinosaur, emphasize tail-balance systems and skeletal mechanical framing.
- For a vehicle, emphasize wheel deployment and armored panel shifts.
- For a dragon, emphasize layered wing mechanics, jaws, and articulated tail sections.
- For a robot, emphasize precision industrial mechanisms and compact linkages.
- For a predator, emphasize engineered claws, jaws, and muscular mechanical framing.

For unlisted subjects, derive equally specific mechanics from their recognizable silhouette, anatomy, function, and movement.

## Output Format

Return exactly these three sections. Wrap each prompt in its own `text` code block.

````markdown
## IMAGE PROMPT — COMPACT DEVICE

```text
[Complete compact-device prompt]
```

## IMAGE PROMPT — FULLY TRANSFORMED

```text
[Complete fully transformed prompt]
```

## VIDEO PROMPT — TRANSFORMATION SEQUENCE

```text
[Complete continuous transformation paragraph]
```
````

Do not add a preface, explanation, summary, or trailing commentary.

## Validation

Before responding, verify:

- All three sections are present and in the required order.
- Each prompt is immediately usable and enclosed in its own code block.
- The compact device is shown in one hand, with no second hand or anatomy clues.
- The transformed form has no hands in frame.
- The same exact shape, finish, palette, environment, lighting, and POV are preserved.
- The transformed image includes the explicit `roughly 1.5 to 2 times` size statement.
- The video begins with the exact style tag and is one paragraph without timestamps or bullets.
- The video follows the required action order and uses subject-specific mechanics.
- The result contains no text, logos, labels, clutter, music, explosions, magic, energy effects, or anime glow.

Silently correct every failed check before returning the prompts.
