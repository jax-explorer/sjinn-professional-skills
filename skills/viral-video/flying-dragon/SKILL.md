---
name: flying-dragon
description: Generate and create hyper-photorealistic first-person dragon-riding images and videos with a rider-locked POV, visible hands and harness, centered dragon spine, aggressive flight motion, environmental interaction, and immersive sound via SJinn. Use for flying-dragon concepts, POV dragon rides, dragon-flight scenes, fantasy aerial rides, or requests to turn a dragon type, world, setting, mood, or biome into an image-to-video sequence.
---

# Flying Dragon

Transform any dragon-related concept into a cinematic POV start-frame prompt and a dynamic dragon-ride video prompt, then generate both assets with SJinn.

## Workflow

1. Accept the user's dragon concept as complete, even when it is only a dragon type, setting, theme, mood, biome, or vague idea.
2. Infer missing details and upgrade the concept into a vivid dragon design, dramatic environment, believable ride sequence, strong environmental storytelling, and large-scale spectacle.
3. Generate the image and video prompts immediately. Do not ask questions or explain creative choices.
4. Validate both prompts against the camera lock and required endings.
5. Submit the image prompt to SJinn, wait for the result, then use that image as the first frame for the video.

## Non-Negotiable Camera Lock

Keep the camera physically mounted to the rider at all times:

- Use first-person POV only.
- Keep the rider's hands visible at the bottom of frame, gripping reins, straps, or a leather harness.
- Keep the dragon's neck, spine, and back extending forward through the center of the frame.
- Make the viewer feel physically mounted on the dragon.
- Never use third-person framing, external cinematic shots, aerial establishing shots, cutaways, orbiting shots, chase cameras, drones, or detached camera movement.
- Never let the hands or centered dragon spine disappear, including during fast maneuvers.

If any requested detail conflicts with the camera lock, preserve the rider-locked POV and adapt the detail.

## Image Prompt

Write one hyper-detailed cinematic start-frame prompt.

Requirements:

- Begin with the words `First-person POV riding` and continue directly into the specific dragon description, for example: `First-person POV riding a colossal obsidian dragon...`
- Identify a specific dragon type and design.
- Describe scale texture, horns, spines, surface wetness, glow, and physically believable materials.
- Describe the reins, straps, saddle, buckles, stitching, or leather harness in tactile detail.
- Show both rider hands gripping the reins or harness at the bottom of frame.
- Keep the dragon's neck, spine, and back centered ahead.
- Describe atmosphere, weather, lighting, immense environmental scale, and environmental motion.
- Make the frame hyper-photorealistic, immersive, visceral, and physically real.
- End exactly with:

```text
Cinematic, hyper-photorealistic, dramatic lighting, sharp focus, no text, no watermarks.
```

## Video Prompt

Write one continuous, action-heavy ride sequence that assumes the generated image is the first frame.

Requirements:

- State that the rider-locked first-person POV remains fixed throughout.
- Keep both hands visible gripping the harness and the dragon spine centered throughout.
- Include hard banking turns, sudden dives, violent climbs, fast acceleration, heavy momentum, and physically believable body forces.
- Describe the dragon's wingbeats, muscle movement, harness tension, vibration, and inertial response.
- Include several relevant environmental interactions such as storm clouds, fog, lava heat, snow, water spray, debris, rain, ash, ice, or violent wind.
- Describe immersive diegetic sounds such as roaring wind, wingbeats, thunder, rain, fire, water impact, stone debris, or echoes.
- Use continuous POV motion without external shots or detached camera movement.
- End exactly with this complete final line:

```text
Cinematic, hyper-photorealistic, sharp focus throughout, no ghosting, no flickering, stable POV. Natural weight and physics. No music.
```

## Style

Always use:

- Hyper-photorealistic material detail
- Cinematic, dramatic lighting
- Immersive and visceral physical sensation
- Rich environmental detail
- High-speed motion
- Large-scale environments
- Natural weight, momentum, and physics

Avoid:

- Cartoon, anime, illustration, or stylized art
- Low detail or generic wording
- Third-person descriptions
- Static scenes
- Teleporting or weightless motion
- Camera shake that breaks the stable rider-locked POV

## Prompt Output Format

Return the prompt phase in exactly this structure, with no preface or explanation:

````markdown
🐉 DRAGON: [dragon type]
🏔️ SETTING: [setting]

---

### IMAGE PROMPT

```text
[Generate image prompt]
```

---

### VIDEO PROMPT

```text
[Generate video prompt]
```
````

## Validation

Before generation, verify:

- The image prompt begins with the words `First-person POV riding`.
- Both prompts keep visible hands, harness contact, and the centered dragon neck/spine.
- Neither prompt contains third-person, detached, external, aerial establishing, or cutaway shots.
- The video contains aggressive flight maneuvers, environmental interaction, physical forces, and diegetic sound.
- The image and video prompts use their exact required endings.
- The visual language stays hyper-photorealistic rather than cartoon, anime, or stylized.

Silently correct any failed check before submitting the prompts.

## Generate with SJinn

After writing and validating the prompts, execute this image-to-video pipeline.

### 1. Generate the start frame

Use the SJinn image-generation tool with:

| Parameter | Value |
|---|---|
| `model` | `nano-banana-pro` |
| `prompt` | The complete IMAGE PROMPT |
| `aspect_ratio` | `9:16` unless the user specifies another ratio |
| `resolution` | `2K` |

Wait for the task to complete and obtain the generated image URL.

### 2. Generate the dragon ride

Use the SJinn video-generation tool with:

| Parameter | Value |
|---|---|
| `model` | `seedance2` |
| `prompt` | The complete VIDEO PROMPT |
| `image_urls` | The generated image URL as the first frame |
| `aspect_ratio` | The same ratio used for the image |
| `duration` | `10` seconds unless the user specifies another supported duration |
| `mode` | `quality` |

Wait for the video task to complete.

### 3. Present the result

Preserve the exact prompt output block, then append:

```markdown
---

### GENERATED ASSETS

**Image:** [image URL or task ID]
**Video:** [video URL or task ID]
```

If SJinn generation is unavailable, return the exact prompt output block without replacing it with setup instructions.

## Iteration

Apply requested changes without asking the user to restate the concept:

- For a new dragon, setting, mood, or biome, regenerate both prompts and both assets.
- For start-frame changes, revise the image prompt and regenerate the full image-to-video chain.
- For motion, pacing, sound, or environmental-interaction changes, keep the image and regenerate only the video when the existing first frame remains valid.
- Preserve the camera lock and exact prompt endings in every revision.
