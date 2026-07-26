---
name: sticker-cooking-comedy
description: Create funny short videos that composite a photorealistic live-action cooking kitchen with a flat chibi 2D anime sticker IP character, using GPT-Image-2 only when a supplied character image needs conversion, requiring user approval of that conversion before continuing, and using SJinn Seedance 2.0 for the final video. Use for live-action kitchen and 2D anime sticker composites, chibi IP cooking videos, kitchen pranks, salt-sabotage gags, cartoon sticker and human-hand interactions, or similar cooking comedy requests, whether the user supplies a character image or only describes the IP.
---

# Sticker Cooking Comedy

Create a funny short video that combines a photorealistic live-action cooking kitchen with a pure flat 2D anime sticker IP character. Keep the wok, food, oil, steam, salt, utensils, and human hands photographic. Keep the IP character flat, chibi, and sticker-like throughout.

## Default Output

Use these defaults unless the user specifies otherwise:

- 10 seconds;
- 9:16 vertical;
- 720p;
- Seedance 2.0 `quality` mode;
- one continuous first-person cooking POV with subtle handheld micro-shake;
- four comedy beats: prank, harmless reaction, exaggerated escalation, freeze-frame reversal;
- realistic kitchen ambience plus cartoon sound effects, with no dialogue or background music.

## Workflow

Follow these steps in order:

1. Decide whether the supplied image is already a chibi 2D anime sticker.
2. Extract a character identity anchor.
3. Use GPT-Image-2 only when a conversion is necessary.
4. If a conversion occurs, show the converted image and pause for explicit user approval.
5. After approval, write the timestamped Seedance 2.0 prompt.
6. Generate the video with SJinn.
7. Review character consistency, live-action versus sticker contrast, and four-beat timing.

When the user explicitly asks to create or generate a video, complete the generation directly for Route A and Route C. Route B must stop at the conversion approval gate even if the user originally requested a complete video. If the user asks only for prompts, do not call generation tools.

## Step 1: Choose the Image Route

Choose exactly one route.

### Route A: The supplied image is already a chibi 2D anime sticker

Use the image directly without redrawing it when it has all of these traits:

- clearly simplified chibi proportions;
- flat color regions, watercolor, crayon, or paper grain instead of realistic volume;
- a readable cartoon outline or complete sticker silhouette;
- no photorealistic skin, fur, feathers, or 3D toy rendering.

A white sticker border is helpful but not required. A small amount of painted shading does not automatically make the image 3D; classify the dominant character by its overall visual treatment.

### Route B: The supplied image is not a chibi 2D anime sticker

If the image is a photograph, live-action person, realistic animal, 3D model, blind-box toy, clay figure, plush toy, realistic painting, or ordinary non-chibi illustration, convert it into a character reference with SJinn `gpt-image-2`. Show the result and obtain explicit user approval before passing it to Seedance 2.0.

### Route C: No image is supplied

Do not generate a separate character image. Describe the IP directly in the Seedance 2.0 video prompt and explicitly define it as a pure flat chibi 2D anime sticker.

If an image contains several equally prominent characters and the target is ambiguous, ask one concise question before spending credits. If one subject is clearly dominant, use that subject.

## Step 2: Build the Character Identity Anchor

Record these fields before writing a generation prompt:

```text
Character name:
Species or human identity:
Chibi body proportions:
Face shape, eyes, mouth, blush, and signature expression:
Hair, fur, or feather color and exact length:
Top, bottoms, and footwear:
Hat, earrings, apron, and other accessories:
Visible text, numbers, or logos:
Primary color palette:
Drawing medium, outline color, paper texture, and sticker border:
Character scale and placement in frame:
Details that must never change:
```

Use only facts visible in the reference image. Do not infer hidden traits. Repeat fragile details such as long hair, hats, visible numbers, earrings, clothing, and forbidden accessories in both the global character block and the timed beats where those details move.

Preserve readable reference text exactly. Do not invent text when none exists.

## Step 3: Convert with GPT-Image-2 When Necessary

For a local image, call SJinn `upload_asset` first. Pass a stable public HTTPS URL directly.

Call SJinn `create_image_task` only for Route B:

```yaml
model: "gpt-image-2"
image_urls: ["<original-image-url>"]
aspect_ratio: "1:1"
prompt: "<filled conversion prompt below>"
```

Do not redraw Route A images. Do not create a character image for Route C.

### GPT-Image-2 Conversion Prompt Template

```text
Transform the main character in the supplied reference into a production-ready chibi 2D anime sticker character sheet for video identity locking.

Strictly preserve the same recognizable identity and every visible design detail: {{face and features}}, {{hair or fur and exact length}}, {{clothing and footwear}}, {{accessories}}, {{exact visible text or numbers}}, and {{original palette}}. Do not redesign the character.

Show exactly one complete character, front-facing, full-body, centered, in a neutral natural pose. Keep both hands or paws, the complete hairstyle, footwear, and every accessory unobstructed. Use a plain warm-white background, {{chibi proportions}}, a clear continuous {{outline color}} cartoon outline, flat color regions, subtle {{watercolor / colored-pencil / crayon / paper}} texture, and a clean white sticker-cut border around the entire silhouette.

This is a pure flat printed 2D sticker reference, not a scene. No kitchen, utensils, props, ground shadow, environmental volumetric lighting, photorealistic skin, realistic fur, realistic feathers, 3D volume, plastic toy, blind-box figure, clay, plush material, extra character, extra limbs, redesigned clothing, or invented text. If the original contains "{{exact visible text}}", preserve it exactly and legibly.
```

If the source contains no text, remove both text-related clauses from the template.

### Mandatory Conversion Approval Gate

Pause the workflow as soon as the GPT-Image-2 conversion finishes:

1. Show the generated conversion image to the user.
2. List the character identity anchor for comparison, emphasizing face, hair or fur, clothing, accessories, text, and palette.
3. Ask exactly one clear question: `Do you approve this chibi 2D anime sticker image for the video?`
4. Do not draft the complete Seedance prompt and do not call `create_video_task`.

Proceed only after the user gives an explicit approval such as "approved," "looks good," "continue," "use this one," or an equally clear affirmative in any language. Silence, an ambiguous reaction, a question, or a simple acknowledgment does not count as approval.

If the user requests changes:

- merge the requested changes into the conversion prompt;
- regenerate only the character image;
- show the new version and repeat the same approval gate;
- never use a rejected or superseded image.

Do not approve the conversion on the user's behalf even when it appears correct. This is the only mandatory workflow pause in Route B.

## Step 4: Write the Seedance 2.0 Prompt

Route B may enter this step only after the user approves the converted image. Route A and Route C do not require this approval gate.

Write prompts in the language requested by the user; otherwise use English. When a reference image exists, use the Seedance `@Image1` label and keep it aligned with the first item in `image_urls`.

Enforce all of these rules:

1. Keep the kitchen layer photorealistic and live-action.
2. Keep the character layer pure flat 2D without volumetric relighting from the kitchen.
3. Seat the character on a small wooden stool beside the stove at about half the wok's diameter in height.
4. Show exactly one IP character, one stool, and one wok.
5. Preserve the positions of the wok, character, bottles, sink, and window.
6. Treat timestamps as action beats inside one continuous shot, not as unrelated new scenes.
7. Keep salt, food, steam, jar, spatula, and human hands physically realistic.
8. Keep the bump, spiral eyes, fountain tears, puffed cheeks, X eyes, stars, and spirit puff as flat cartoon effects.
9. Use harmless absurd slapstick only. Do not show realistic hitting, burns, choking, or pain.
10. Give each beat one dominant action. Avoid simultaneous complex interactions.
11. Lock action ownership: from 00:00 to 00:03, only the 2D IP character's hands or paws may hold, lift, rotate, tilt, and pour the salt jar. The human hand may only stir with the spatula and must not touch, support, or tilt the jar. A human hand may first touch the jar only after the character finishes pouring.

### Complete Seedance 2.0 Prompt Template

```text
[FORMAT AND COMPOSITE STYLE]
A 10-second vertical 9:16 comedy short in one continuous live-action first-person cooking POV with subtle handheld micro-shake.

Build two deliberately contrasting visual layers:
1. The real kitchen, iron wok, beef and greens, oil sheen, steam, salt grains, glass salt jar, spatula, wooden stool, condiment bottles, sink, window, and adult human hands remain photorealistic live-action objects with believable physics.
2. The IP character remains a pure flat chibi 2D anime sticker with {{drawing medium}}, {{outline}}, and {{sticker border}}.

Real kitchen lighting must never remodel the character into a volumetric 3D object. The character must never acquire realistic skin, fur, feathers, plastic, clay, plush material, or a realistic cast shadow.

[REFERENCE CHARACTER LOCK - KEEP ONLY WHEN A REFERENCE EXISTS]
Use @Image1 only as the exact character-design and drawing-style reference. Do not use @Image1 as the first frame or kitchen background. Preserve the same identity, face, body proportions, {{hair or fur and exact length}}, {{clothing}}, {{accessories}}, exact visible text "{{text}}", palette, outline, paper texture, and sticker silhouette from @Image1 in every frame. Never add, remove, recolor, shorten, merge, or replace these details.

[REAL KITCHEN]
Show a lived-in home kitchen from a slightly downward cook's-eye viewpoint. Place a black iron wok on the left-center burner, stir-frying glossy beef and green vegetables with continuous sizzling and natural rising steam. Show a white tiled wall and outlet behind it, soy sauce and cooking-oil bottles against the wall, a stainless-steel sink on the right, and soft daylight from a side window. Preserve the same kitchen layout, camera position, and left-right orientation throughout.

[CHARACTER]
{{character name}} is {{complete character identity anchor}}. Seat the same character on a small wooden stool beside the stove at about half the wok's diameter in height. The character behaves like a slightly flexible flat paper sticker with limited cartoon squash-and-stretch, a continuously readable silhouette, no duplication, no wardrobe change, and no model-sheet drift. Adult human hands enter from the right only when required and retain realistic skin texture, pores, and lighting.

[PROP AND ACTION OWNERSHIP HARD LOCK]
The glass salt jar is a photorealistic prop, but the 2D IP character is the only performer of the pouring action. The jar begins in the character's lap or arms. Its movement path, lift, rotation pivot, and tilt remain visibly connected to the character's two clearly visible 2D hands or paws. The salt stream must begin at the mouth of the jar held by the character.

From 00:00 to 00:03, show only one real human hand. That hand continuously grips the spatula and stirs. It never releases the spatula and never touches, lifts, blocks, supports, steadies, or tilts the salt jar. Show no real fingers, real palm, off-screen human hand, or human hand hidden behind the sticker near the jar. Do not let two real hands pour the salt. Do not let the jar float and pour by itself.

Only after the salt stream has stopped, the salt mound is visibly complete, and the timeline has entered 00:03 may a second real human hand enter for the first time and take the jar from the 2D character's hands or paws. Keep the spatula hand and the jar-snatching hand functionally separate.

[00:00-00:03 - SALT SABOTAGE]
One real human hand continuously holds the spatula and stir-fries the beef and greens without touching any salt container. {{character name}} makes a sly troublemaking expression and independently wraps two clearly visible 2D hands or paws around a photorealistic glass salt jar larger than its head. The character raises its arms, rotates the jar, points the opening toward the wok, and personally pours the entire jar of white salt into the food. The two 2D hands or paws visibly carry the jar's weight and rotation without human assistance. Dense realistic salt grains flow only from the mouth of the character-held jar, forming a clear white mound on the food. The jar and salt obey realistic physics, but the operator remains the flat 2D sticker character.
SFX: continuous food sizzling and dense salt-grain rustling.

[00:03-00:05 - JAR SNATCH AND LIGHT BONK]
The pouring is complete, the salt stream has fully stopped, and the salt mound is clearly formed. Only now does a second real human hand appear for the first time and take the jar from the character's still-visible 2D hands or paws. The human hand never participates in pouring. The separate spatula hand then gives the top of the character's head one extremely light cartoon tap with the flat of the spatula. This is harmless absurd slapstick. A flat red cartoon bump pops up with "DUANG"; the paper body bounces once, the eyes widen, and the hands or paws hold the head. {{fragile moving details such as hat, long hair, or earrings}} remain complete and unchanged.
SFX: a light metallic "DUANG" and one cartoon spring sound.

[00:05-00:08 - CRY AND TASTE]
The character's eyes become flat spiral eyes, and two blue 2D sticker tear fountains spray sideways. The human scoops one bite of beef and greens from the salt mound and offers it to the open cartoon mouth. The bite pops into the mouth with impossible but harmless cartoon timing. The cheeks instantly inflate into two round sticker balloons. Do not show force, choking, injury, or realistic distress.
SFX: exaggerated cartoon crying, spatula scraping over salt, and one soft "pop".

[00:08-00:10 - SALTY K.O.]
The character swallows, turns pale through a flat color swap, freezes for half a beat, and gets two cartoon X eyes. The character falls backward from the stool like a lightweight paper cutout with its limbs briefly raised. Flat dizzy stars spin beside the red bump, and one translucent cartoon spirit puff rises from the nose. Preserve {{fragile ending details such as long hair, hat, clothing, and accessories}} through the fall. Freeze the final 0.3 seconds.
SFX: a short stiffening clunk, a paper-flat thud, and a brief comic ascension tone.

[CONTINUITY AND EXCLUSIONS]
Treat every timestamp as a consecutive action beat inside the same uninterrupted shot. Do not switch to a new kitchen. The same wok contents and salt mound must persist and evolve continuously. Keep character scale, compositing order, and scene geography fixed. Show exactly one character, one stool, and one wok.

No new scene, orbiting camera, new clothing, new accessories, altered text, 3D character, realistic animal or person conversion, extra limbs, fused human hand and prop, flicker, morphing, duplicated character, watermark, subtitles, dialogue, or background music. Absolutely no real human hand pouring salt, supporting the salt jar, hiding behind the IP character to operate the jar, tilting the jar from off-screen, or allowing the jar to float and pour by itself.
```

### No-Image Replacement

Delete the entire reference character lock block and every `@Image1` mention. Replace the character block with a complete text description such as:

```text
A round chibi penguin 2D sticker with an oversized head and tiny body, black head and back, white belly, small orange beak and feet, black dot eyes, pink cheeks, and tiny wings; thick dark-navy outline, crayon grain, and a white sticker border. No clothing, hat, necklace, or other accessory. No realistic feathers or 3D volume at any time.
```

For a text-only IP, choose a small number of highly distinctive traits. Avoid stacking too many accessories.

### Complex Character Lock Example

Use a block like this for a character with long hair, a hat, visible text, and several clothing items:

```text
A two-head-tall chibi sticker girl with a round doll face, large dark-brown eyes, orange-pink blush, one small fang, and airy bangs; two separate black ponytails tied behind the ears and extending clearly below the waist; a beige baseball cap with the exact white number "31", gold round earrings, an off-white chunky-knit sweater, loose khaki trousers, and brown round-toe ankle boots; warm watercolor and colored-pencil paper texture, soft dark-brown outline, and a clean white sticker border. Never shorten, merge, or restyle the ponytails. Never remove, recolor, or replace the cap, number, earrings, clothing, or boots.
```

## Step 5: Generate with SJinn Seedance 2.0

For Route A, pass the user's original sticker URL. For Route B, pass only the converted image URL that the user explicitly approved:

```yaml
model: "seedance2"
prompt: "<filled complete video prompt>"
image_urls: ["<approved-2D-sticker-reference-url>"]
aspect_ratio: "9:16"
duration: 10
mode: "quality"
resolution: "720p"
```

Never pass the Route B source image, an undisclosed conversion, a rejected conversion, or an unapproved conversion to Seedance. Omit `image_urls` entirely for Route C. Honor any user-specified duration, aspect ratio, or resolution supported by Seedance 2.0.

Do not repeatedly call `get_task` for a newly created task when the client tracks it automatically. Call `get_task` only when the user explicitly asks to check an existing task.

## Step 6: Deliver and Review

For the final delivery, include:

- the selected Route A, B, or C;
- the final character identity anchor;
- the conversion prompt and image result for Route B;
- the complete Seedance 2.0 prompt and parameters;
- the video task or completed result.

At the Route B approval gate, the interim reply must include only:

- the converted chibi 2D anime sticker image;
- the character identity anchor checklist;
- one explicit approval question.

Do not include the Seedance video prompt or claim that video generation has started in that interim reply.

If the completed video is playable, inspect representative frames near 0, 3, 5, 8, and 10 seconds. Verify:

- the kitchen remains photorealistic while the character remains flat 2D;
- face, hair or fur, clothing, accessories, and text remain unchanged;
- exactly one character appears, with no invented hats, necklaces, or props;
- from 00:00 to 00:03, both 2D hands or paws visibly hold and tilt the jar while the only real hand holds the spatula and stirs;
- a real hand first touches and removes the jar only after the salt stream stops and the salt mound forms;
- salt sabotage, light bonk, cartoon crying and feeding, and X-eye fall occur in order;
- the salt mound, wok contents, and kitchen layout remain continuous;
- no 3D conversion, flicker, morphing, duplication, or scene reset occurs;
- the final 0.3 seconds form a readable freeze-frame payoff.

When a defect appears, add only the most relevant repair clause:

| Failure | Repair clause |
|---|---|
| Character becomes 3D | `The character looks like flat ink printed on paper in every frame, with zero volumetric shading, fur, skin, plastic, clay, or toy depth.` |
| Clothing or accessory changes | `Treat {{details}} as immutable model-sheet anchors; keep them fully visible and identical before, during, and after pouring, bouncing, crying, and falling.` |
| Long hair shortens or merges | `Keep both separate hair tails continuously visible from their ties to below the waist, including during the bounce and fall; never shorten or merge them.` |
| An unwanted accessory appears | `The complete allowed accessory list is: {{list}}. No other hat, necklace, bow, bag, or garment exists.` |
| Character duplicates | `Exactly one sticker character exists; no reflection, clone, insert, illustration copy, or background duplicate.` |
| Kitchen resets between beats | `Use one uninterrupted take; the same salt mound and wok contents persist and evolve continuously across every timestamp.` |
| Real props become cartoon | `Keep the salt jar, spatula, salt, food, wok, stool, and human hands as photorealistic objects with real texture and physics.` |
| Human hand pours instead of the IP character | `From 00:00 to 00:03, the 2D IP character is the only performer of the pouring action: two clearly visible 2D hands or paws wrap around the jar and complete the lift, rotation, and tilt; the only real hand continuously holds the spatula and stirs, and a second real hand may first touch the jar only after the salt stream stops.` |
| Cartoon effects become realistic | `Keep the tears, bump, spiral eyes, puffed cheeks, X eyes, stars, and spirit puff as hard-edged flat 2D graphic overlays.` |
| Interaction looks harmful | `All contact is feather-light impossible cartoon slapstick, with no injury, choking, burns, or realistic pain.` |

Do not silently spend credits on another generation. Report the visible defect and the smallest repair first, then let the user decide whether to regenerate.
