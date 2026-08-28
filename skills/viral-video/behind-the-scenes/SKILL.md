---
name: behind-the-scenes
description: Create one matched image and video of a tiny hand-built city or landmark model being destroyed by a real practical disaster effect inside an enormous blue-screen soundstage, then generate the 9:16 still with SJinn GPT-Image-2 and an 8-second image-to-video clip with SJinn Seedance 2 Mini. Use for behind-the-scenes miniature disaster shoots, practical-FX city destruction, skyline-to-model transformations, or place-plus-disaster requests; do not use for depictions of a real full-size disaster.
---

# Behind the Scenes — Set Piece Studio

Turn a place, landmark, skyline image, disaster, or natural-language combination of those elements into one locked miniature practical-effects set. Draft one English image prompt and one perfectly matched English video prompt, generate the still, and use that still as the video's first frame.

## Defaults

- Image: SJinn GPT-Image-2, `9:16`
- Video: SJinn Seedance 2 Mini (`seedance2` with `mini` mode), `9:16`, `8` seconds, `720p`
- Camera: low at the in-floor tank lip beside the steel dolly track
- Sound: synchronized diegetic production sound only
- Quantity: exactly one image and one video

Honor an explicit supported aspect ratio, duration, or vantage. Otherwise keep these defaults. Never silently substitute another image or video model.

## Required Reference

Before drafting prompts, read [references/set-piece-studio-style-bible.md](references/set-piece-studio-style-bible.md) in full. It is authoritative for place conversion, disaster selection, exact disaster tags, prompt clauses, negatives, timing, sound, scale cues, and the silent quality check.

## Input Interpretation

Treat any usable place, disaster, skyline image, or prior scene context as sufficient. Silently extract:

- place or visual reference;
- disaster;
- optional vantage;
- optional visual details and generation settings.

Infer missing information:

- Place only: choose one scene-appropriate disaster using the Style Bible.
- Disaster only: invent an original generic metropolitan, coastal, desert, mountain, or industrial miniature suitable for it.
- Uploaded skyline only: infer a strong disaster from its visible terrain and architecture.
- “Do this with…”: reuse the most recent established place or reference.

Ask one concise question only when there is no usable place, image, disaster, or prior visual context.

## Non-Negotiable Concept

The scene is always a tiny hand-built model inside a gigantic working soundstage. It is never a real full-size city and never a polished CGI disaster visualization.

Keep the visual identity locked across both prompts:

- identical generic architecture, materials, colors, shoreline or terrain, and model weathering;
- identical practical disaster, FX machinery, in-floor tank, blue wall, orange tracking crosses, crew wardrobe, lighting, camera position, and scale relationships;
- the model in the lower third, with the effect, empty air, and immense blue wall dominating the upper two-thirds;
- at least one full-size crew member standing approximately as tall as the miniature towers;
- imperfect amateur phone-footage texture.

The user's real place name is input only. Never repeat any real city, landmark, building, franchise, character, celebrity, company, brand, logo, or trademarked sign inside either generation prompt. Convert the place to generic silhouette, proportions, roof shapes, facade materials, colors, geometry, density, terrain, and non-branded structural cues.

## Prompt Phase

1. Read the Style Bible.
2. Resolve one IP-safe place design and one supported disaster family.
3. Copy the selected disaster's FX setup and exact tag from the Style Bible.
4. Draft exactly one image prompt and one video prompt in English using the required clauses verbatim.
5. If a reference image exists, begin the image prompt with exactly `Set your uploaded image as reference image 1.` and include the required reference-use paragraph.
6. Run the silent quality check. Fix every mismatch before generation.

Do not expose reasoning, the internal place conversion, alternatives, or menus. Do not ask the user to choose details that can be inferred.

## Generation Phase

Unless the user explicitly asks for prompts only, execute one image task followed by one video task.

### 1. Prepare an optional reference image

For a local uploaded image, use SJinn `upload_asset` and keep the returned stable asset URL. Pass a stable public HTTPS URL directly. Do not pass the user's skyline image to the video task; it is only a structural reference for rebuilding the generated miniature still.

### 2. Generate the image

Call SJinn `create_image_task`:

```yaml
model: "gpt-image-2"
prompt: "<complete image prompt>"
image_urls: ["<uploaded-reference-url>"] # only when a reference image exists
aspect_ratio: "9:16"
```

Omit `image_urls` when there is no uploaded reference. Do not add aspect-ratio commands, model names, captions, or UI syntax to the prompt text.

Wait until the task exposes a completed image asset URL. Never use a task ID, pending placeholder, or the original skyline image as the video's first frame. Use the host's task-completion mechanism; do not busy-poll. Call `get_task` only when the user explicitly asks to check or resume an existing task.

### 3. Generate the video from the completed still

Call SJinn `create_video_task`:

```yaml
model: "seedance2"
mode: "mini"
prompt: "<complete matched video prompt>"
image_urls: ["<completed-gpt-image-2-url>"]
aspect_ratio: "9:16"
duration: 8
resolution: "720p"
```

In SJinn, `model: "seedance2"` plus `mode: "mini"` selects Seedance 2 Mini. Do not omit `mode`, use `fast` or `quality`, or substitute Seedance 2.5. If the connected tool does not expose `mini` mode, report the limitation and stop rather than substituting another model or mode.

If the user overrides supported settings, apply the same aspect ratio to both tasks and proportionally rescale the four video beats to the requested duration. Seedance 2 Mini supports only its exposed resolution choices; default to `720p`.

One request authorizes one image task and one video task. If either task fails, report the failure and stop. Do not retry, regenerate, create variants, or spend more credits without a fresh user request.

## Delivery

After both tasks are submitted or completed, return:

1. `An original miniature-FX homage — landmarks are stylized, not real places, brands, or people.`
2. `🖼 IMAGE PROMPT` and the exact submitted image prompt in a `text` code block.
3. `🎬 VIDEO PROMPT` and the exact submitted video prompt in a `text` code block.
4. The image and video model settings.
5. The generated assets, task IDs, or current statuses.

Keep exactly one prompt under each prompt heading. For a prompt-only request, return only the disclaimer and the two prompt blocks.
