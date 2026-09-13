---
name: veo3-story-video
description: Create one complete story or vlog video with consistent characters and locations using SJinn Nano Banana 2 reference images and storyboard frames, Veo 3.1 Fast image-to-video clips, and SJinn MCP video composition. Use for veo3 story video, Veo story generation, multi-scene character-consistent stories, 故事视频, or 连续剧情短片, including stories based on uploaded character images.
---

# Veo3 Story Video

Turn the user's topic, story, or character references into **one finished video**. Build an original script, lock each character and location with reference images, generate one first frame and one Veo clip per storyboard scene, then concatenate the clips in storyboard order with SJinn MCP `create_compose_task`.

If the user requests only a script, storyboard, prompts, or a skill definition, provide that deliverable without starting media generation. For a video request, proceed through the workflow without adding a separate prompt-approval gate unless the user requests one.

## Defaults and model selection

| Setting | Default |
| --- | --- |
| Image generation and editing | SJinn `nano-banana-2`, `2K` |
| Video generation | SJinn `veo3.1-fast` (Veo 3.1 Fast) |
| Final composition | SJinn MCP `create_compose_task`, preserving clip order and native audio |
| Aspect ratio | `16:9` for scene frames and video; `9:16` when requested |
| Total runtime | Approximately 30 seconds: four planned 8-second scenes, approximately 32 seconds total |
| Scene length | Plan every scene for 8 seconds |
| Style | User's requested style; otherwise randomly choose Animation, 3D, or Pixar-style feature animation once for the whole story |
| Audio | Veo's native dialogue/narration, ambience, and sound effects |
| External TTS / LipSync | Disabled unless the user explicitly requests them |
| Script and spoken language | User's language unless otherwise requested |

Always pass both model identifiers explicitly. Do not substitute Nano Banana Pro, GPT-Image, another Veo tier, Seedance, or Kling. Fast is part of the model name, not a `mode` parameter. Verify the active tool schema before submitting tasks; the current Veo connector cannot accept a duration selector and does not guarantee audio or identity consistency. Plan for 8 seconds, then verify actual output.

Supported SJinn generation arguments and asset handling are included below under SJinn generation and task handling; the composition call is defined in step 7. Skip those execution details for a script-only request.

## 1. Resolve the story and timing

Use the user's input as the brief. Infer missing low-impact details and continue. If no topic is supplied, invent an original, visually clear short-video premise with an immediate hook, escalation, and payoff; do not promise virality. Honor the requested genre, audience, characters, ending, and style.

Use `VLog_Script_Generator` for a vlog or `Short_Video_Story_Script_Generator(custom_v1)` for a story **only if that generator is actually available**. Discover its real schema before calling it. If neither is available, write the script directly using this skill's format and constraints; these legacy names are not mandatory dependencies. Normalize any generator output to the same rules.

Reconcile duration and word count as follows:

- Default to four 8-second scenes. Treat the source brief's 30 seconds / 100 words as approximate; use at most 96 English spoken words across four scenes, usually fewer to leave room for acting.
- For a requested duration `T`, plan `ceil(T / 8)` scenes and state the planned runtime. For example, approximately five minutes uses 38 scenes / 304 seconds. Do not force 1,000 words into that runtime.
- The final runtime is the sum of the actual generated clip durations. The current Veo connector has no duration selector, and `create_compose_task` has no trimming or retiming parameters. If an exact runtime is required, explain this limitation before generation and resolve whether an approximate runtime is acceptable; do not promise an exact 30-second cut from four 8-second clips or silently introduce a local editing workflow.
- Keep **narration plus dialogue combined** to at most 24 English words per full 8-second scene. This is an upper estimate, not a quota; expressive delivery and pauses need fewer words. For other languages, including Chinese, estimate natural speaking time rather than treating characters as English words.
- Split any overlong spoken passage or action into additional sequential 8-second scenes. If the user supplied a script that must remain verbatim, preserve its text and split it; state any resulting runtime increase rather than silently cutting the script.
- A scene may contain multiple shots only when all shots and speech fit within its 8-second window. The original brief's 10-second / 30-word allowance does not extend a scene. Prefer one readable action and one clear camera treatment per clip.

Distinguish **storyboard scenes** (timeline segments) from **locations** (reusable physical environments). Several scenes may share one location reference.

## 2. Write the script and storyboard

Keep the following top-level labels and order. Use the user's language inside the fields. Number scenes consecutively; the timing fields must show the planned 8-second length and timeline range. Update the final runtime using completed clip metadata or playback when available; label an unverified duration as an estimate.

```text
video script:
[Title/topic and complete original script, with speaker labels where relevant.]
[Target runtime, planned scene count, and planned final runtime.]

Style Design:
[One defined style: medium/rendering, shapes/materials, palette, lighting, camera language.]

character design(Optional):
[Only characters without supplied identity references: stable character ID, appearance,
 proportions, face, hair/fur, outfit, accessories, personality, and voice description.]

Storyboard design:
Scene 1:
Duration: 8s planned; [planned timeline range]
Characters: [C01, C02, ... or none]
Location: [L01]
Narration: [Exact corresponding script text, or None — no narrator]
Dialogue: [Speaker ID: exact script text, or None]
Visual description: [Framing, action, setting, lighting, emotional beat, end state]
Audio: [Stable voice descriptions, language, ambience, timed sound effects]
Reference mapping: [Image 1 = C01; Image 2 = C02; Image 3 = L01]
Image prompt: [Complete scene first-frame prompt using those exact image numbers]
Video prompt: [Complete 8-second motion and native-audio prompt]

Scene 2:
[Same fields; continue through the final scene.]
```

Omit `character design(Optional):` when every character has a supplied identity reference or the story has no characters. For mixed input, design only the characters without references. Record identity anchors for supplied characters internally without redesigning them.

Every scene must contain a narration field and a visual description. When narration is used, copy its exact script wording; do not paraphrase it between the script, storyboard, and video prompt. A dialogue-only or silent story uses `Narration: None` and must not acquire an unsolicited voiceover. Do not duplicate narration as dialogue or invent additional spoken lines.

## 3. Lock each character

Assign a stable ID such as `C01` to every distinct story character, including recurring supporting characters. Keep one separate identity reference asset per character; do not build one shared cast sheet as the sole reference for several people.

- **Uploaded usable three-view or multi-view sheet:** inspect and reuse it directly. Do not regenerate an already adequate character reference. A sheet must show the same character clearly in multiple useful views. If an upload contains several characters, isolate each character into a separate usable reference without changing their appearance.
- **Uploaded ordinary portrait or single-view image(s):** use those images as editing references with `nano-banana-2` to generate one three-view sheet for that character. Preserve visible identity, proportions, hairstyle, outfit, and accessories; infer unseen details consistently. Do not perform a new character design.
- **No uploaded reference for that character:** design the character from the user's description, then generate a three-view sheet with `nano-banana-2`.

Use front, side, and back full-body views of the **same character**, consistently scaled, in a neutral pose and even lighting. A landscape `16:9` sheet is useful even when the final video is vertical. Preserve identity-defining facial details in the front and side views. Avoid labels, extra figures, or unrelated scenery inside the sheet.

Example reference-guided instruction:

```text
Image 1 is the identity reference for C01. Create one character turnaround sheet
with front, left-side, and back views of this same character. Preserve the face,
body proportions, hairstyle, outfit colors, materials, and accessories from
Image 1. Same scale and neutral pose in each view, plain neutral background,
even lighting, [locked story style]. No additional characters or text.
```

Inspect the completed reference before using it downstream. Never use a failed, pending, or visibly inconsistent asset as an identity lock.

## 4. Lock each location

List every distinct physical location as `L01`, `L02`, and so on. Generate one panoramic establishing image with `nano-banana-2` for each location before creating the scene frames. Use a wide view that makes the spatial layout readable; a 360-degree panorama is unnecessary unless requested.

Define architecture, room or terrain layout, doors/windows, major props and their positions, materials, palette, lighting direction, weather, and time of day. Keep these consistent whenever that location recurs. Avoid adding principal characters to location references so their identity remains controlled by the separate character sheets.

If the user supplies a location image, use it as a numbered editing reference for the panorama. For a deliberate change in time, weather, or set state, derive a named variant from the existing location reference and preserve its underlying layout.

## 5. Generate one first frame per scene

Use `nano-banana-2` image editing with the relevant character sheet(s) and location panorama. Generate a normal single scene frame, never a turnaround sheet or storyboard grid. Each frame must match the final video ratio and depict the beginning of the planned action.

For **every image call**, map the actual `image_urls` array to 1-based image numbers in the prompt. Numbering is local to that call, not a global character number. For example:

```text
Image 1 is C01's three-view identity sheet. Image 2 is C02's three-view identity
sheet. Image 3 is the L01 location panorama. Create a single [16:9] cinematic
first frame in [locked style]. C01 stands on the left, [pose and expression];
C02 stands on the right, [pose and expression]. Preserve each character's own
face, proportions, outfit, and accessories; do not mix their identities.
Use Image 3 for the room geometry, prop placement, materials, and lighting.
[Framing, lens/perspective, foreground/background, action starting state.]
This is one scene image, not a multi-view sheet, collage, or split-screen.
```

Use only relevant characters; a location-only scene does not need character references. If a prior scene frame is also supplied for continuity, give it a separate image number and explain its role. Keep poses, props, screen direction, and location state continuous across adjacent beats.

Review each frame for identity swaps, missing characters, changed wardrobe, incorrect location layout, and a usable starting pose before submitting its video task.

## 6. Animate the completed frames

Submit one `veo3.1-fast` image-to-video task per scene with the **completed scene image** as `first_frame_url`. Do not feed the three-view sheet or panorama directly into the video first-frame field. Veo receives the assembled scene frame; the reference library conditions the preceding image-editing step.

Each video prompt must include:

- An 8-second action plan with a readable opening, main beat, and settled ending that joins naturally to the next scene through a straight cut.
- Camera movement, framing, acting, and environmental motion consistent with the first frame and visual style.
- Explicit preservation of each character's appearance, clothing, accessories, relative scale, and the established set layout.
- Exact narration and dialogue, labeled by narrator or character, in the requested language. Reuse the same voice descriptions for recurring speakers and keep overlapping speech out unless required by the script.
- Native-audio direction for speech, ambience, and sound effects. If no speech is intended, explicitly request no narration or dialogue. Keep music consistent if requested; otherwise favor ambience over separate music that restarts in each clip.

Do not call standalone TTS, audio-generation, or LipSync tools by default. Veo's built-in mouth motion during speech does not require a separate LipSync pass. Native audio and cross-clip voice/character continuity remain generation goals, so inspect the results rather than promising perfect consistency. If speech is missing or incorrect, report the issue; do not silently replace it with TTS.

## 7. Compose and deliver one video

Wait until every scene video has a completed stable public HTTPS asset URL. Inspect the clips using available previews and media metadata for character/location continuity, aspect ratio, speech, audio, and actual duration before composition. Use the same aspect ratio throughout the project; report a material mismatch or missing required speech rather than treating it as a completed scene.

For **two or more clips**, call SJinn MCP `create_compose_task` once with the completed URLs in exact storyboard order:

```yaml
video_urls:
  - "<completed-scene-1-video-url>"
  - "<completed-scene-2-video-url>"
  - "<completed-scene-3-video-url>"
  - "<completed-scene-4-video-url>"
```

Include every scene exactly once in playback order, regardless of task completion order. Pass the generated HTTPS URLs directly; do not download and re-upload them for composition. Never pass task IDs, pending placeholders, image URLs, or local paths as video URLs. If a video exists only locally, complete its SJinn upload before adding its resulting URL to the list.

The compose tool accepts only `video_urls` and requires at least two videos. It concatenates whole clips and preserves their embedded native audio; it does not accept a model selector, separate audio, voiceover, background music, transitions, trim points, or a target duration. Do not add unsupported parameters or separate TTS/LipSync stages. For **exactly one clip**, skip composition and deliver that completed video directly.

Use SJinn composition for this workflow, without a local editing dependency or fallback. If composition fails, keep all completed clip URLs and the compose task ID for a requested retry. A pending compose task is not a completed final video; follow the task-state rules below for completion and resumption.

Inspect the completed composed video across every join and at the ending. Confirm scene order, intact speech, native audio, consistent aspect ratio, and final runtime using the available player or media metadata. If a check cannot be performed, state that limit instead of claiming verification.

Present the completed composed video as the primary result through its native media component, or a usable result link when a preview is unavailable. Follow it with a concise runtime/ratio/model summary. Include the script and storyboard in the required format above, or link their saved local file if already lengthy. Expose character sheets, location references, and scene assets through a compact asset list when useful. If generation or composition is pending or blocked, report the exact stage and task ID, retaining completed assets for continuation.

## SJinn generation and task handling

Use these instructions when executing the media-generation pipeline. The examples match the SJinn MCP schema inspected when this skill was created; inspect the active schema for changes before submitting a job. Never infer a supported argument from another model's example.

### Images: Nano Banana 2

Use SJinn `create_image_task` for both text-to-image and reference-guided editing:

```yaml
model: "nano-banana-2"
prompt: "<complete task-specific image prompt>"
aspect_ratio: "16:9"
resolution: "2K"
image_urls:
  - "<completed-reference-image-1-url>"
  - "<completed-reference-image-2-url>"
```

Omit `image_urls` for generation without references. Use `9:16` for scene frames when the video is vertical; character sheets and wide location panoramas may remain landscape. Nano Banana 2 supports `auto`, `1:1`, `16:9`, `9:16`, `3:2`, `2:3`, `4:3`, `3:4`, and `21:9` in the inspected connector, but the final Veo video supports only `16:9` and `9:16`.

Write `Image 1 = ...`, `Image 2 = ...` in the prompt in exactly the order passed to `image_urls`. Include each reference's role: identity, environment, or continuity. Do not reuse an old prompt's numbering after changing the array.

### Video: Veo 3.1 Fast

Use SJinn `create_video_task` for each completed scene frame:

```yaml
model: "veo3.1-fast"
prompt: "<complete 8-second scene action, consistency, speech, and audio prompt>"
first_frame_url: "<completed-scene-first-frame-url>"
aspect_ratio: "16:9"
```

Change the ratio to `9:16` for a vertical project. These are the only supported aspect ratios for this model.

**Do not pass** `duration`, `resolution`, `mode`, `image_urls`, `video_urls`, or `audio_urls` to `veo3.1-fast`; the current connector returns `unsupported_parameter` for them. Do not invent fields such as `generate_audio`, `voice_id`, `lip_sync`, or `seed` if they are absent from the active schema. Request 8-second pacing and native audio in the prompt, then measure the resulting clip; the prompt is not a duration or audio guarantee.

The connector also supports `last_frame_url` when `first_frame_url` is present. Use it only when a planned transition needs an explicit end frame, generated with the same references. It is not needed for the default workflow. A last frame without a first frame is invalid. Omitting both fields selects text-to-video, which bypasses this skill's scene-frame workflow.

### Assets, dependencies, and task state

Use stable public HTTPS asset URLs directly. For local reference files, inspect them first and use SJinn `upload_asset` to prepare an upload. Its `files` entries contain a `filename` and optional `content_type`, not the file bytes. Complete the returned upload procedure using the actual local file and confirm success before using `asset_url`. An upload instruction is not a completed upload.

Keep a small production manifest in the working directory with:

- character and location IDs, identity anchors, and completed reference URLs;
- scene order, script text, prompts, exact per-call reference ordering, and planned durations;
- each generation and composition task ID, status, and completed asset URL;
- verified clip durations/audio observations, the ordered composition input URLs, and the final composed video URL.

The dependency order is: script → character/location references → scene first frames → scene videos → SJinn composition. A downstream task may start as soon as all of **its** inputs are complete and inspected. Never use a task ID, upload placeholder, pending URL, or character sheet in place of a completed scene image.

Use the host's completion mechanism for newly created SJinn tasks. The current connector's interactive component tracks them automatically; `get_task` is reserved for an explicit user request to check or resume a prior task. Do not busy-poll or substitute account-wide recent-task searches. If completed asset URLs have not been delivered to the agent, retain the pending stage and state what is awaiting completion; continue when actual results become available.

On an argument rejection before a task was created, correct only the unsupported argument and resubmit once. On a failed or uncertain generation or composition task, retain the task ID and report the failure instead of blindly submitting duplicate jobs. Preserve completed references and clips for any requested retry. Do not silently change models to bypass an error.
