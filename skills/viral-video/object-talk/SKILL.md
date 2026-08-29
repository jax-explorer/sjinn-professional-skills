---
name: object-talk
description: Create a short talking-object video for each requested physical object, using a Pixar-style Nano Banana 2 still and an adaptive 4–15 second Seedance 2 Mini image-to-video monologue with native audio, then concatenate the ordered clips with SJinn MCP. Use for Object Talk, anthropomorphic object rants, talking food or product facts, and themed collections of speaking objects.
---

# Object Talk

Turn an object list or theme into one cohesive talking-object montage. Generate one still and one video for every resolved object, then concatenate the completed clips in order with SJinn MCP.

## Defaults

- Objects: strawberry, cucumber, tomato
- Quantity for a theme without an explicit object list: three representative physical objects
- Image: SJinn Nano Banana 2, `9:16`, `2K`
- Video: SJinn Seedance 2 Mini (`seedance2` with `mini` mode), adaptive `4–15` seconds, `720p`
- Final composition: SJinn `create_compose_task`, preserving clip order and Seedance's generated audio
- Prompt language: polished English; spoken dialogue follows the user's requested language, or the user's language when none is specified

Honor an explicit supported aspect ratio, object order, quantity, language, clip duration, or total-duration target. Otherwise keep these defaults. Never silently substitute a different image model, video model, or video mode.

## Resolve the Object Set

Treat any usable object list or theme as sufficient. Do not ask for details that can be inferred.

- No object or theme: use `strawberry`, `cucumber`, `tomato`, in that order.
- Explicit object list: use exactly those objects and preserve their order.
- Theme only: choose three visually distinct, instantly recognizable physical objects from that theme. Honor a user-specified count.
- Mixed input: prefer explicitly named objects; use the theme to shape their settings and talking points.

Each segment must feature exactly one primary speaking object. Choose a different accurate fact, warning, complaint, or misconception for each object so the montage does not repeat itself.

## Shared Creative Direction

Lock a cohesive feature-animation look across the set: compatible rendering style, saturation, facial construction, camera distance, voice clarity, and overall energy. Let the setting, lighting, expression, and gesture change to match each object's subject and mood.

Keep every object recognizable before anthropomorphizing it. Do not add text, captions, logos, labels, watermarks, extra talking objects, or a visible audience unless the user explicitly requests them.

## Plan Each Segment

Before generation, silently define for each object:

- one factually accurate educational point;
- one mode: rant, warning, or fact drop;
- one dominant emotion;
- one expressive arm gesture;
- one mood-appropriate location and lighting setup;
- one concise first-person monologue;
- one integer duration from `4` through `15` seconds.

Estimate the spoken time at a natural expressive pace, add roughly one second for a clean visual start and finish, and select the shortest supported duration that fits comfortably. The dialogue must finish before the clip ends. As a guide for English dialogue:

- `4–7s`: about 8–15 spoken words
- `8–11s`: about 16–24 spoken words
- `12–15s`: about 25–34 spoken words

Use the equivalent natural speaking time for other languages. Do not force every segment to the same duration, default to 8 seconds, or pad a short idea with filler.

## Image Prompt

Write one complete image prompt per object. Always include:

1. The exact opening phrase `Pixar-style 3D render of an anthropomorphic [OBJECT]`.
2. The object's recognizable shape, color, surface, and material details.
3. Eyes, expressive eyebrows, and a mouth with the planned emotion, naturally integrated into the object.
4. Two visible arms making a dynamic, readable gesture.
5. A cinematic Pixar-style setting and lighting design that reflects the location and mood.
6. A clear portrait composition suitable as the first frame of a `9:16` video, or the user's chosen ratio.
7. `No text, captions, logos, labels, or watermarks.`

Match the face, gesture, scene, and lighting to the later monologue. Do not describe speech or motion in the still prompt.

## Video Prompt

Assume the generated still is the first frame. Write one complete image-to-video prompt per object that contains:

- `Spoken dialogue: "[MONOLOGUE]"` with the exact words to be spoken;
- a first-person monologue, written as the object speaking about itself;
- an emotional and educational rant, warning, or fact drop;
- precise facial acting, eyebrow movement, mouth synchronization, and arm gestures;
- subtle scene motion and a stable one-take camera treatment;
- explicit direction to preserve the object's identity, proportions, colors, face, arms, and setting from the first frame;
- clear native audio direction: one intelligible character voice, synchronized lip movement, and fitting light ambient sound;
- `No subtitles, on-screen text, filler, call to action, audience mention, or added music.`

The dialogue must not address viewers, listeners, followers, customers, or any other audience. Avoid greetings, setup phrases, rhetorical audience questions, and closing slogans. Do not use Text-to-Speech or create a separate voice track: Seedance 2 Mini generates the speech and audio inside each clip.

## Generation Workflow

Unless the user asks for prompts only, execute the complete workflow.

### 1. Generate one image per object

Submit the image tasks in object order with SJinn `create_image_task`:

```yaml
model: "nano-banana-2"
prompt: "<complete object-specific image prompt>"
aspect_ratio: "9:16"
resolution: "2K"
```

Replace `9:16` only when the user requests another supported ratio. One request authorizes exactly one image task per resolved object, not retries or extra variants.

### 2. Generate one video per completed image

Wait until each image task exposes a completed asset URL. Never pass a task ID or pending placeholder as the first frame. Submit one SJinn `create_video_task` per image:

```yaml
model: "seedance2"
mode: "mini"
prompt: "<complete matching video prompt>"
image_urls: ["<completed-nano-banana-2-url>"]
aspect_ratio: "9:16"
duration: <adaptive integer from 4 through 15>
resolution: "720p"
```

In SJinn, `model: "seedance2"` with `mode: "mini"` selects Seedance 2 Mini. Do not omit `mode`, use `fast` or `quality`, or substitute Seedance 2.5. Keep the aspect ratio identical across every image and video task.

Use the host's task-completion mechanism and do not busy-poll. Call `get_task` only when the user explicitly asks to check or resume an existing task. If a task fails, report it and stop; do not retry or spend more credits without a fresh request.

### 3. Compose the completed clips with SJinn MCP

Wait until every video task exposes a completed stable public HTTPS asset URL. Never pass task IDs, pending placeholders, local paths, or incomplete assets to the composition task.

When there are two or more completed clips, call SJinn `create_compose_task` once with their URLs in the resolved object order:

```yaml
video_urls:
  - "<completed-video-url-for-first-object>"
  - "<completed-video-url-for-second-object>"
  - "<completed-video-url-for-third-object>"
```

`create_compose_task` performs ordered concatenation only. It does not accept separate audio, voiceover, background music, or transitions. Preserve the native audio already embedded in each Seedance clip and do not call Text-to-Speech or any audio-generation tool.

The compose tool requires at least two videos. When the resolved set contains exactly one object, skip composition and deliver that object's completed clip as the final video. One request authorizes at most one compose task; if it fails, report the failure without retrying or substituting another editing method.

## Delivery

Return:

- the resolved object order;
- each image prompt, video prompt, and adaptive duration;
- the Nano Banana 2 and Seedance 2 Mini task IDs, statuses, or completed assets;
- the composed video asset or compose task ID as the primary result, or the single completed clip when there is only one object;
- the final aspect ratio and total runtime.

For a prompt-only request, omit all generation and composition steps and return only the ordered prompt set with the planned durations.
