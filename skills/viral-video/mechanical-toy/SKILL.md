---
name: mechanical-toy
description: >-
  Generate and create a hyper-realistic mechanical transformation toy from any
  creature, animal, vehicle, robot, mythical entity, object, machine, or
  structure. Draft a compact-device image prompt, a fully transformed image
  prompt, and a continuous transformation video prompt; pause for explicit
  prompt approval; generate approved 9:16 first and last frames with SJinn Nano
  Banana 2; pause for explicit frame approval; then animate the approved frames
  with SJinn Kling 3.0. Use for mechanical-toy concepts, transformation-toy
  prompts, transforming pods or capsules, collectible mechanical transformers,
  satisfying mechanical unfolding videos, or requests to convert a subject
  into a compact device that physically unfolds into its final form.
---

# Mechanical Toy

Turn the user's subject into a mysterious one-hand-held mechanical pod and its fully unfolded collectible form, then create the approved first frame, last frame, and transformation video through SJinn MCP.

## Defaults

- Prompt language: polished, production-ready English
- First and last frames: Nano Banana 2, `9:16`, `2K`
- Transformation video: Kling 3.0, two-image first/last-frame input, `10` seconds, `quality`

Honor user-specified supported settings. Otherwise use these defaults.

## Mandatory Workflow

Follow these phases in order. Never collapse or bypass either approval gate.

### Phase 1: Draft and approve all prompts

1. Treat any supplied subject as sufficient. Do not ask follow-up questions when details can be inferred.
2. Choose one compact shape, one metallic finish, one subject-appropriate color palette, and subject-specific mechanics.
3. Reuse those exact design descriptors across all three prompts.
4. Write the compact-device image prompt, fully transformed image prompt, and transformation video prompt.
5. Validate and show the complete prompt set plus generation settings.
6. Ask one explicit approval question in the user's language and stop. Do not call any SJinn generation tool yet, even if the initial request says to generate immediately.

Proceed only after the user clearly approves the latest displayed prompt set with language such as `approved`, `confirm`, `use these`, `generate`, `确认`, `通过`, `就用这组`, or an equally explicit affirmative. Silence, a question, an ambiguous reaction, or a simple acknowledgment does not count as approval.

Prompt approval authorizes exactly one compact-frame task and one matching transformed-frame task. It does not authorize retries or variants. If the user requests prompt changes, revise the affected details, show the complete three-prompt set again, and repeat this approval gate.

### Phase 2: Generate the approved first and last frames

After explicit prompt approval:

1. Call SJinn `create_image_task` for the compact-device first frame:

```yaml
model: "nano-banana-2"
prompt: "<approved compact-device image prompt>"
aspect_ratio: "9:16"
resolution: "2K"
```

2. Wait until the task exposes a completed image asset URL. Do not use a task ID or pending placeholder as a reference image.
3. Call SJinn `create_image_task` for the fully transformed last frame, using the completed compact image as its reference:

```yaml
model: "nano-banana-2"
prompt: "<approved fully transformed image prompt>"
image_urls: ["<completed compact-image-url>"]
aspect_ratio: "9:16"
resolution: "2K"
```

4. Wait until both completed frame assets are available. Present both frames together with their roles and settings.
5. Ask one explicit frame-approval question in the user's language and stop. Do not call `create_video_task` yet.

Do not repeatedly call `get_task` for newly created tasks; the interactive client tracks them automatically. Call `get_task` only when the user explicitly asks to check or resume an existing task.

If either task fails, report the failure and stop. Do not retry or spend more credits without fresh approval. A compact-frame retry invalidates the transformed frame and requires regenerating both; a transformed-frame-only retry may reuse the approved compact frame. After every retry, show both current frames and repeat the frame-approval gate.

### Phase 3: Approve and animate the frames

Proceed only after the user clearly approves the latest displayed pair with language such as `approved`, `confirm`, `use these frames`, `generate the video`, `确认`, `通过`, `使用这两张`, `生成视频`, or an equally explicit affirmative.

Frame approval authorizes exactly one video task. Call SJinn `create_video_task` with the compact frame first and the transformed frame second:

```yaml
model: "kling3"
prompt: "<approved transformation video prompt>"
image_urls:
  - "<approved compact-image-url>"
  - "<approved transformed-image-url>"
duration: 10
mode: "quality"
```

Omit `aspect_ratio` when passing images to Kling 3.0 because the approved `9:16` frames determine the video ratio. Do not pass a resolution parameter unsupported by Kling 3.0. Preserve the exact approved video prompt and frame order.

### Phase 4: Deliver the result

Return the approved three-prompt set, the frame and video settings, both generated frame assets or task IDs, and the generated video asset or task ID. If video generation fails, report the failure and the smallest relevant correction; do not retry without fresh user approval.

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

## Phase 1 Approval Output

Return exactly these prompt sections, the generation settings, and one approval question. Wrap each prompt in its own `text` code block.

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

## GENERATION SETTINGS

- First frame: Nano Banana 2 · 9:16 · 2K
- Last frame: Nano Banana 2 · compact frame reference · 9:16 · 2K
- Video: Kling 3.0 · approved first and last frames · 10s · Quality

[One explicit prompt-approval question in the user's language.]
````

Do not include generated-task claims, asset placeholders, manual SJinn instructions, or extra commentary at this gate.

## Phase 2 Frame Review Output

After both image tasks complete, show:

````markdown
## MECHANICAL TOY — FRAME REVIEW

### FIRST FRAME — COMPACT DEVICE

[Render or link the completed compact-device image and include its task ID when useful.]

### LAST FRAME — FULLY TRANSFORMED

[Render or link the completed transformed image and include its task ID when useful.]

### FRAME SETTINGS

- Nano Banana 2 · 9:16 · 2K
- Last frame generated with the first frame as its reference

[One explicit frame-approval question in the user's language.]
````

Do not submit the video task in the same turn as the frame-review output.

## Final Result Output

After the approved video task is submitted or completes, return the approved prompts, settings, both frame assets or task IDs, and the video asset or task ID. Clearly label the compact image as the first frame and the transformed image as the last frame.

## Validation

Before Phase 1 output, verify:

- All three sections are present and in the required order.
- Each prompt is immediately usable and enclosed in its own code block.
- The compact device is shown in one hand, with no second hand or anatomy clues.
- The transformed form has no hands in frame.
- The same exact shape, finish, palette, environment, lighting, and POV are preserved.
- The transformed image includes the explicit `roughly 1.5 to 2 times` size statement.
- The video begins with the exact style tag and is one paragraph without timestamps or bullets.
- The video follows the required action order and uses subject-specific mechanics.
- The result contains no text, logos, labels, clutter, music, explosions, magic, energy effects, or anime glow.
- The output ends with one explicit prompt-approval question.

Before Phase 2, verify that the user explicitly approved the latest complete prompt set. Before generating the last frame, verify that its reference is the completed compact-image URL. Before presenting frame review, verify that both frame assets are complete and no video task has been submitted.

Before Phase 3, verify that the user explicitly approved the latest displayed frame pair, both URLs refer to completed image assets, the compact image appears first in `image_urls`, and the exact approved video prompt is used.

Silently correct every failed prompt check before returning Phase 1. Stop and report an asset or approval failure rather than bypassing a gate.
