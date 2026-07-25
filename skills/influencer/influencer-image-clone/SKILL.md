---
name: influencer-image-clone
description: Recreate an adult influencer, creator, model, or the user from one or more reference photos as a new photorealistic still image with consistent visible identity, facial structure, hair, styling, and camera characteristics. Use when the user provides a portrait or full-body reference and asks to clone, recreate, match, restage, or place the same person in a different pose, outfit, setting, or social-media image. Generate images only; never generate video.
---

# Influencer Image Clone

Recreate an adult subject from reference photos as a new still image. Preserve visible identity while changing only the scene attributes the user requests.

## Boundaries

- Require at least one reference image. Ask the user to attach one if none is available.
- Produce still images only. Do not write video prompts, generate video, create a start frame, animate the result, or call a video tool.
- Describe only visible features. Do not identify the person, guess their name, or infer sensitive traits.
- Refer to the person as “the adult subject” or “the person in the reference image,” never by a celebrity or real-person name in the generation prompt.
- Keep age-ambiguous subjects fully clothed, non-sexual, and in neutral contexts. Reject sexualized transformations of anyone who appears under 18 or whose age is unclear.
- Do not promise an exact biometric copy. Aim for strong visual continuity and report obvious identity drift honestly.

## Inputs

Collect or infer:

1. **Reference image** — required; use the clearest face view as the primary identity anchor.
2. **Target result** — exact recreation or requested changes to pose, expression, outfit, setting, crop, or aesthetic.
3. **Aspect ratio** — match the primary reference by default.
4. **Resolution** — use `2K` by default.

Do not block on optional details. If the user says only “clone this image,” preserve the original composition, styling, expression, lighting, and background.

Map the reference to the closest aspect ratio supported by the connected image tool when an exact match is unavailable, and disclose the chosen ratio.

For multiple references:

- Put the clearest, most frontal face image first.
- Use additional images to confirm side profile, hair, body silhouette, or styling.
- Ensure every reference depicts the same intended subject. If a frame contains multiple people and the target is ambiguous, ask which person to recreate.
- Keep reference order unchanged across iterations.

## Workflow

### 1. Inspect the reference

Visually inspect every reference before writing the prompt. Record only what is visible and separate observations into two groups.

**Identity anchors — freeze across generations:**

- Overall face shape and facial proportions
- Eye shape, spacing, eyelids, iris color when visible, and brow density or arc
- Nose bridge, width, tip, and nostril shape
- Lip shape, relative fullness, cupid’s bow, and resting mouth
- Cheek structure, jawline, chin, ears, and natural asymmetry
- Skin tone and visible stable details such as freckles, dimples, moles, or beauty marks
- Hairline, natural hair color, texture, length, parting, and recurring signature styling

**Scene attributes — preserve or change according to the request:**

- Expression, gaze, head angle, posture, hand position, and body pose
- Makeup, grooming, clothing, jewelry, and accessories
- Crop, camera height, lens feel, depth of field, and aspect ratio
- Light direction, softness, intensity, color temperature, and shadow behavior
- Background, environment, palette, and overall social/editorial aesthetic

Do not invent details hidden by hair, makeup, cropping, blur, or occlusion. Prefer “not clearly visible” over guessing.

### 2. Define the transformation

For an exact recreation, preserve both identity anchors and scene attributes.

For a restaged image:

- Freeze the identity anchors.
- Apply the user’s text to scene attributes only.
- Treat the reference as authoritative for identity and the user’s text as authoritative for requested changes.
- Preserve unspecified scene attributes when practical.

Keep a reusable **identity block** containing the stable facial and hair description. Reuse it verbatim in later generations; change only the target-scene block.

### 3. Write the recreation prompt

Write one dense English paragraph of roughly 100–180 words in this order:

1. Declare the primary reference as the identity anchor and request the same adult subject.
2. State the frozen identity block with concrete facial and hair geometry.
3. Describe the target outfit, pose, expression, and environment.
4. Describe framing, camera position, and depth of field.
5. Describe lighting as physical direction, quality, temperature, and resulting shadows.
6. Add realistic surface cues such as visible skin texture, individual hair strands, fabric weave, or natural asymmetry.
7. End with a concise identity-consistency constraint.

Use language close to this structure:

```text
Using the first reference image as the primary identity anchor, create a new
photorealistic still of the same adult subject. Preserve [identity block].
[Target clothing, pose, expression, and setting]. [Framing and camera behavior].
[Physical lighting description]. Retain natural skin texture, individual hair
strands, and realistic fabric detail. Keep the subject’s facial geometry,
feature spacing, hairline, skin tone, and distinctive visible marks consistent
with the reference; do not substitute a different face or beautify away
identity-defining details.
```

Prompt rules:

- Use exact visual language: “warm chestnut waves past the shoulders,” not “nice brown hair.”
- Describe lighting physically: “soft window light from camera-left creating a gentle shadow along the right cheek,” not merely “moody light.”
- Include at least two texture or camera-realism cues.
- State the framing in prose, such as close-up, waist-up portrait, or full-body vertical composition.
- Use “same adult subject from the reference,” not “inspired by,” “lookalike,” or a person’s name.
- Avoid generic boosters such as “masterpiece,” “perfect,” “stunning,” “8K,” or “flawless.”
- Avoid poreless skin, plastic texture, excessive face symmetry, glamour retouching, distorted hands, duplicate limbs, logos, watermarks, and unintended readable text.
- Do not change ethnicity, facial geometry, age presentation, body shape, or other identity-defining features unless the user explicitly requests an allowed transformation.

### 4. Obtain prompt approval

Before consuming generation credits, show:

1. A compact reference breakdown with **Identity anchors** and **Scene attributes**
2. The complete recreation prompt
3. The model, aspect ratio, resolution, and number of references

Ask whether anything needs adjustment before generation. If the user already said to skip approval or explicitly requested immediate generation, treat that as approval and proceed.

### 5. Generate with SJinn

Use the SJinn MCP tools:

1. For a local reference file, call `upload_asset` and use the returned HTTPS asset URL. Pass an existing stable public HTTPS URL directly.
2. Call `create_image_task` with:

```yaml
model: nano-banana-pro
prompt: <approved recreation prompt>
image_urls:
  - <primary reference URL>
  - <optional supporting reference URLs>
aspect_ratio: <matched reference ratio or user choice>
resolution: <2K default or user choice>
```

3. Return the task status or result supplied by SJinn. In clients that track submitted tasks automatically, do not poll repeatedly. Call `get_task` only when the user asks to check an existing task.

Never call `create_video_task` or any other video-generation tool.

### 6. Perform still-image QA

When the generated image is available, compare it with the primary reference and inspect:

- Face shape, eye spacing, nose, lips, jawline, skin tone, marks, and hairline
- Requested expression, pose, outfit, setting, crop, and lighting
- Hands, fingers, teeth, eyes, jewelry, garment edges, and background geometry
- Unwanted text, logos, watermarks, face blending, over-smoothing, or extra limbs

If QA passes, present the image and a brief result note.

If QA fails:

- Identify the specific drift or defect.
- Keep the identity block and reference order frozen.
- Change only the prompt clause responsible for the failure.
- Ask before spending credits on another generation unless the user pre-authorized retries.
- Limit pre-authorized automatic retries to two.

## Output Formats

Before generation:

```markdown
## Reference breakdown

**Identity anchors:** ...
**Scene attributes:** ...
**Requested changes:** ...

## Recreation prompt

...

**Settings:** SJinn nano-banana-pro · 2K · <aspect ratio> · <reference count> reference(s)
```

After generation:

```markdown
## Influencer Image Clone

**Settings:** SJinn nano-banana-pro · 2K · <aspect ratio>
**Prompt:** ...
**Result:** <image URL, task ID, or status>
**QA:** <passed, pending, or concise issue>
```

## Iteration

- Change one scene variable at a time when diagnosing drift.
- Reuse the exact identity block and source image order for a series.
- If the face drifts, strengthen concrete facial geometry and remove conflicting beauty adjectives.
- If the result copies the face but misses the shot, revise only pose, framing, lighting, wardrobe, or environment.
- If the result is over-retouched, request natural skin texture, fine facial asymmetry, individual hair strands, and ordinary camera rendering.
- If references conflict, reduce them to the clearest primary image plus only the supporting view needed for the requested shot.
