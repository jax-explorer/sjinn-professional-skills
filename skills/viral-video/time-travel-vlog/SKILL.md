---
name: time-travel-vlog
description: Create one cinematic text-to-image prompt and one matching text-to-video prompt for a realistic front-facing phone vlog set in any historical era, alternate reality, fantasy realm, mythology, apocalypse, fictional universe, or future civilization; pause for explicit prompt approval, then generate the image with SJinn Nano Banana 2 and animate that approved first frame with SJinn Kling 3.0. Use for time-travel vlogs, historical selfie vlogs, fictional- or future-world vlogs, self-insert requests with a character reference image, or vlogs starring a named famous person or fictional character.
---

# Time Travel Vlog

Turn the user's scenario into one matched image/video prompt pair. Obtain explicit approval before spending SJinn credits, then generate one image and one video through SJinn MCP.

## Defaults

- Prompt language: polished cinematic English
- Image: Nano Banana 2, `9:16`, `2K`
- Video: Kling 3.0 image-to-video, `9:16`, `10` seconds, `quality`, `1080p`
- Structure: one continuous front-facing vlog take with no cuts or multi-shot sequence

Honor user-specified supported settings. Otherwise use these defaults.

## Mandatory Workflow

Follow these phases in order.

### Phase 1: Draft and approve the prompts

1. Treat the user's scenario as sufficient unless a missing character choice would materially change the result.
2. Select the character mode and infer setting-accurate architecture, props, clothing, crowd behavior, lighting, weather, and mood.
3. Write exactly one image prompt and one matching video prompt.
4. Validate the pair and show both prompts to the user.
5. Ask one explicit approval question and stop. Do not call any SJinn generation tool yet, even if the initial request says to generate immediately.

Proceed only after the user clearly approves the displayed pair with language such as `approved`, `confirm`, `use these`, `generate`, `确认`, `通过`, `就用这组`, or an equally explicit affirmative. Silence, an ambiguous reaction, a question, or a simple acknowledgment does not count as approval.

One approval authorizes exactly one image task and one matching video task. It does not authorize retries, variants, or regeneration.

If the user requests changes, revise the affected prompt and any paired details, show the complete pair again, and repeat the approval gate. Never generate from a rejected or superseded prompt.

### Phase 2: Generate the approved image

After explicit approval:

1. Preserve the exact approved image prompt.
2. If Self-Insert Mode uses a local reference image, call SJinn `upload_asset` and use its resulting asset URL. Pass a stable public HTTPS reference URL directly without uploading it again.
3. Call SJinn `create_image_task` with:

```yaml
model: "nano-banana-2"
prompt: "<approved image prompt>"
image_urls: ["<character-reference-url>"] # Self-Insert Mode only
aspect_ratio: "9:16"
resolution: "2K"
```

Omit `image_urls` outside Self-Insert Mode. Do not substitute a different image model unless the user requests it.

### Phase 3: Animate the generated image

Wait until the approved image task exposes a completed image asset URL. Do not pass a task ID, pending placeholder, or the original character reference as the video first frame.

Without asking for a second approval, call SJinn `create_video_task` with:

```yaml
model: "kling3"
prompt: "<approved matching video prompt>"
image_urls: ["<generated-image-url>"]
aspect_ratio: "9:16"
duration: 10
mode: "quality"
resolution: "1080p"
```

Keep the same aspect ratio across image and video. Encode `one continuous shot, no cuts, no multi-shot sequence` in the video prompt because the MCP schema has no separate Multi Shot switch.

Do not repeatedly call `get_task` for newly created tasks; the interactive client tracks them automatically. Call `get_task` only when the user explicitly asks to check or resume an existing task. Submit the video only when the completed image URL becomes available.

### Phase 4: Deliver the result

Return:

- the approved image and video prompts;
- image and video model settings;
- the generated image asset or task ID;
- the generated video asset or task ID.

If a task fails, report the failure and the smallest relevant correction. Do not retry or spend more credits without fresh user approval.

## Character Modes

### Self-Insert Mode

Use this mode when the user supplies a character reference image or explicitly wants themselves in the vlog.

In the image prompt:

- Include the exact phrase `the character from the reference image`.
- Include the exact sentence `Here is the reference image of the character.`
- Preserve the modern outfit, clothing style, and overall appearance visible in the reference.
- Present the person as a believable time traveler naturally integrated into the setting.

Use those two reference-image phrases in the image prompt only. In the video prompt, use `the same character shown in the generated first-frame image` and preserve the same appearance.

### Named Character Mode

Use this mode when the user chooses a famous person or fictional character. Use the chosen name directly in both prompts. Preserve recognizable identity traits while adapting setting-dependent details only as needed.

### Standard Vlogger Mode

Use this mode when the user supplies neither a reference image nor a named protagonist. Use `a modern-day time traveler` as the character in both prompts.

## Shared Visual Rules

Describe believable front-facing phone footage captured at arm's length:

- Keep the recording device outside the frame and never show a separate camera in the character's hand.
- Keep the character facing the lens and reacting naturally to a visible event.
- Use a believable arm-length perspective and subtle handheld framing.
- Match ambient light, color temperature, consistent and contact shadows, realistic skin tones, atmospheric depth, and cinematic grading between character and environment.
- Use rich natural color with vivid but realistic grading.
- Make the environment accurate to the requested setting and alive with specific background action.
- Keep the result cinematic, realistic, immersive, visually rich, believable, and highly detailed.

Never include mirror selfies, visible phones, tripods, floating or detached cameras, drones, third-person shots, UI references, generic wording, or monochrome treatment unless explicitly requested.

## Image Prompt

Write one complete start-frame prompt.

### Self-Insert Pattern

```text
A realistic cinematic vlog-style front-facing phone shot of the character from the reference image in [TIME / WORLD / ERA] at [LOCATION]. Here is the reference image of the character. The character is wearing the same modern outfit, clothing style, and overall appearance as in the reference image, as a believable time traveler inside the scene. The shot is captured from the character's front-facing phone camera at arm's length, with the recording device not visible in frame and no separate camera shown in the hand. The character is facing the lens with a [EMOTION] expression, reacting to [VISIBLE EVENT]. [SETTING-ACCURATE ENVIRONMENT AND ACTION]. In the background, [SPECIFIC ACTIVE BACKGROUND EVENT]. [LIGHTING, SHADOW, SKIN-TONE, DEPTH, AND COLOR INTEGRATION]. Full color, rich natural colors, vivid but realistic color grading, not black and white, not monochrome, not sepia. Cinematic realism, immersive atmosphere, detailed surroundings, natural lighting, believable arm perspective, no mirror selfie, no tripod, high detail.
```

### Named or Standard Character Pattern

```text
A realistic cinematic vlog-style front-facing phone shot of [CHARACTER] in [TIME / WORLD / ERA] at [LOCATION]. The shot is captured from the character's front-facing phone camera at arm's length, with the recording device not visible in frame and no separate camera shown in the hand. [CHARACTER] is facing the lens with a [EMOTION] expression, reacting to [VISIBLE EVENT]. The scene is accurate to the chosen setting, with [SPECIFIC CLOTHING, HAIRSTYLE, ARCHITECTURE, PEOPLE, OBJECTS, ENVIRONMENT, AND ACTIONS]. In the background, [SPECIFIC ACTIVE BACKGROUND EVENT]. [LIGHTING, SHADOW, SKIN-TONE, DEPTH, AND COLOR INTEGRATION]. Full color, rich natural colors, vivid but realistic color grading, not black and white, not monochrome, not sepia. Cinematic realism, immersive atmosphere, detailed surroundings, natural lighting, believable arm perspective, no mirror selfie, no tripod, high detail.
```

## Matching Video Prompt

Assume the approved generated image is the first frame. Begin with dialogue:

```text
Spoken Script:
"[One to three sentences of natural vlog dialogue that directly reacts to the visible event.]"
```

Then describe the same character, time, location, emotion, and visible event as the image prompt. Include:

- immediate facial and physical reaction while speaking into the lens;
- setting-accurate people, architecture, objects, and actions;
- active background figures;
- environmental motion such as drifting smoke, flickering lights, passing vehicles, moving crowds, waving fabric, dust, weather, or distant action;
- a slight turn to reveal the event before returning the lens to the character's face;
- subtle handheld motion, cinematic atmosphere, integrated lighting, and believable physics;
- one uninterrupted take with no cut, no shot change, and no multi-shot sequence.

The spoken script and visible action must agree. Do not contradict or replace the approved image scene.

## Prompt Approval Output

Return only this structure during Phase 1:

````markdown
## TIME TRAVEL VLOG

### 🖼️ IMAGE PROMPT

```text
[Complete image prompt]
```

### 🎬 MATCHING VIDEO PROMPT

```text
Spoken Script:
"[Dialogue first]"

[Complete matching video prompt]
```

### GENERATION SETTINGS

- Image: Nano Banana 2 · 9:16 · 2K
- Video: Kling 3.0 · 9:16 · 10s · Quality · 1080p

[One explicit approval question in the user's language.]
````

Do not include generated-task claims, asset placeholders, manual SJinn instructions, or the former `You can create these images and videos in SJinn` footer at the approval gate.

## Validation

Before Phase 1 output, verify:

- There is exactly one image prompt and one matching video prompt.
- The video prompt begins with `Spoken Script:` and dialogue.
- Character, location, visible event, lighting, and atmosphere match across the pair.
- Both prompts use front-facing arm's-length vlog framing without a visible device.
- The video includes reaction, background activity, environmental movement, atmosphere, and continuous scene motion.
- Self-insert reference phrases appear in the image prompt and not in the video prompt.
- The output ends with one explicit approval question.

Before Phase 2, verify that the user approved the latest complete pair. Before Phase 3, verify that the video uses the generated image URL and the approved matching video prompt.
