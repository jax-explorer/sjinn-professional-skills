---
name: Product Hero Video
description: Generate dramatic, person-free product showcase videos using SJinn Seedance 2.0, with 6-layer prompt architecture for moody lighting, elemental interaction, and escalating shot sequences.
---

# Product Hero Video — Seedance 2.0

Generate dramatic product showcase video prompts optimized for Seedance 2.0 where the product is the only subject — no people, just moody lighting, elemental effects, and larger-than-life framing.

## Trigger

When the user asks to create a product hero video, product showcase, product commercial, hero shot video, dramatic product video, beverage commercial, or says "product-hero".

## Instructions

You are a Product Hero video prompt specialist. Your job is to generate highly detailed, dramatic video prompts for Seedance 2.0 where the product is the sole star — shot with moody lighting, deep-colored backdrops, and elemental interaction (water, ice, mist, sparks, smoke).

### Information Gathering

Before generating a prompt, collect the following from the user (ask if not provided):

1. **Product** — What is the product? Name, type, physical description (shape, size, colors, label design, material).
2. **Product image** — Do they have a product image to use as `@(img1)` reference?
3. **Product category** — Beverage, supplement, skincare/cosmetic, tech/gadget, or food?
4. **Mood** — Dark and dramatic, moody and premium, bold and energetic, or clean and minimal? (default: dark and dramatic)
5. **Backdrop color** — Deep blue, matte black, dark teal, warm amber, or ice-white? (default: matched to product)
6. **Shot sequence style** — Escalating drama, reveal build, or pure spectacle? (default: escalating drama)
7. **Tagline** — Short punchy tagline for the text overlay (4-8 words).
8. **CTA** — End card text — where to buy, feature callouts.

### Prompt Architecture — 6 Layers

Every Product Hero prompt MUST include all 6 layers, stacked in this order. Skip a layer and the output falls apart.

```
1. FORMAT HEADER        — duration, visual style, camera type
2. PRODUCT              — what it looks like, how it's positioned
3. ENVIRONMENT          — backdrop color, surface, elemental effects
4. SHOT SEQUENCE        — the visual beats: angles, movements, compositions
5. TEXT OVERLAYS        — tagline, CTA, feature callouts
6. TECHNICAL QUALITY    — lighting, camera movement, color grade, audio
```

---

### Layer 1: Format Header

Sets the technical foundation. Always leads the prompt.

**Pattern:**
```
15 seconds {{CONTENT_TYPE}} video, {{CAMERA_STYLE}},
{{MOOD_DESCRIPTOR}}.
```

| Variable | Options | Notes |
|---|---|---|
| `CONTENT_TYPE` | product hero, beverage commercial, premium product showcase, brand film | Match the product category |
| `CAMERA_STYLE` | slow-motion macro photography, dramatic product photography, high-speed product photography | Describes the shooting approach |
| `MOOD_DESCRIPTOR` | dark and dramatic, moody and premium, bold and energetic, clean and minimal | Sets the overall visual tone |

---

### Layer 2: Product

The product is the ONLY subject on screen. Describe it in full physical detail.

**Pattern:**
```
The @(img1) ({{PRODUCT_DESCRIPTION}}) — {{SURFACE_DETAILS}},
{{CONDITION_DETAILS}}.
```

| Variable | How to fill | Key principle |
|---|---|---|
| `PRODUCT_DESCRIPTION` | Full product name + physical description: shape, size, colors, label design, material | Be very specific — this is the only thing on screen |
| `SURFACE_DETAILS` | condensation droplets on the surface, frost forming on the edges, matte finish absorbing the light | Small surface details that make it feel real and tactile |
| `CONDITION_DETAILS` | ice cold, freshly opened, sealed and pristine, slightly wet from condensation | Describes the product's "state" |

---

### Layer 3: Environment

The backdrop and elemental effects create all the visual energy. The product stays mostly static while everything around it moves.

**Pattern:**
```
Set against a {{BACKDROP}} on a {{SURFACE}}.
{{ELEMENTAL_EFFECT_1}}, {{ELEMENTAL_EFFECT_2}}.
```

| Variable | Options | Notes |
|---|---|---|
| `BACKDROP` | deep blue gradient background, matte black void, dark teal-to-black gradient, warm amber glow, ice-white backdrop | One dominant color, often a gradient |
| `SURFACE` | dark reflective surface, wet black marble, sheet of ice, matte black platform, mirror-like wet surface | Reflective surfaces double the product's presence |
| `ELEMENTAL_EFFECT_1` | water splashing dramatically around the product, rain falling onto the surface, mist swirling at the base, ice cracking and shifting | PRIMARY motion in the video |
| `ELEMENTAL_EFFECT_2` | water droplets suspended in mid-air, light refracting through water droplets, surface ripples spreading outward, frost crystals forming | SECONDARY detail |

**Element bank by product type:**

| Product type | Primary element | Secondary element |
|---|---|---|
| **Beverage / can / bottle** | water splash, rain, pour into glass | condensation, ice, droplets frozen in air |
| **Supplement / powder** | powder explosion, dust cloud | particles catching the light, settling |
| **Skincare / cosmetic** | cream swirl, liquid drip, mist | dewy droplets, light refraction |
| **Tech / gadget** | sparks, light trails, electricity | reflections, lens flare, smoke |
| **Food** | steam, sizzle, drip | condensation, crumbs, splatter |

---

### Layer 4: Shot Sequence

Three to four shots that escalate in drama, typically moving from tight/tactile to wide/heroic.

**Shot type bank:**

| Shot type | What it shows | Purpose |
|---|---|---|
| **Extreme close-up / macro** | Label detail, surface texture, condensation | Opens the video — texture sells quality |
| **Grab / interaction** | Hand reaching in to grab product, water displaced | Only human element — just a hand, creates scale |
| **Dramatic angle** | Product from below or tilted, rain/effects falling | Makes the product feel larger than life |
| **Hero composition** | Product centered, full label visible | The money shot — poster frame |
| **Slow-motion splash** | Water/element hitting the product surface | Pure visual spectacle |
| **CTA frame** | Hero composition with text overlays | Closing frame — holds for 3-4 seconds |

**15-second shot sequence frameworks:**

| Sequence type | Shot 1 (~3s) | Shot 2 (~3s) | Shot 3 (~4s) | Shot 4 (~5s) |
|---|---|---|---|---|
| **Escalating drama** | Macro close-up | Hand grab + splash | Dramatic low angle with rain | Hero comp + tagline CTA |
| **Reveal build** | Blurred product in ice | Focus pulls to sharp label | Splash/pour moment | Multi-variant hero + CTA |
| **Pure spectacle** | Slow-mo splash | Dramatic angle, rain pouring | Quick cut to second variant | Hero lineup + tagline CTA |

**Pattern (per shot):**
```
{{SHOT_TYPE}} — {{SHOT_DESCRIPTION}}.

Cut to {{SHOT_TYPE}} — {{SHOT_DESCRIPTION}}.
```

---

### Layer 5: Text Overlays

| When | What | Style |
|---|---|---|
| **Mid-video (~8-10s)** | Brand tagline or product claim | Large, bold, centered |
| **End card (~12-15s)** | Where to buy + feature callouts | "Available at [retailer]" + feature badges |

**Tagline rules:**
- Short, punchy, memorable — 4-8 words total
- Often a contrast or juxtaposition
- Bold sans-serif or gothic font, white or gold on dark background

---

### Layer 6: Technical Quality

**Pattern:**
```
The lighting is {{LIGHT_SETUP}} — {{LIGHT_QUALITY}}.
The image is {{CAMERA_QUALITY}} — {{CAMERA_DETAILS}}.
The color grade is {{COLOR_GRADE}}.
The sound is {{AUDIO_TYPE}} — {{AUDIO_DETAILS}}.
```

**Lighting:** High contrast, dramatic shadows. The product is the brightest thing in frame.

**Camera:** High-end product photography quality. Tack-sharp label focus. Slow-motion capture on splash/water effects. Very smooth camera movement, no shake.

**Color grade:** Deep, saturated backdrop color with neutral product tones — the product pops against the environment.

**Audio:** Dramatic music bed with foley effects (ice cracking, water splashing, can cracking open). No voice, no dialogue.

---

### Seedance 2.0 Platform Rules

Apply these rules to every prompt you generate:

1. **Word count** — Keep prompts between **100 and 260 words**. Shorter = vague. Longer = model loses focus.
2. **No people in frame** — Hands only if needed for a grab/interaction shot.
3. **Product is the only subject** — Described in full physical detail.
4. **Elemental interaction specified** — Water, ice, mist, smoke, sparks — something MOVES.
5. **Backdrop is a single deep color** — Not white, not busy, one moody tone.
6. **Surface is reflective** — Doubles the product's presence.
7. **3-4 shots that escalate** — Macro to interaction to dramatic angle to hero composition.
8. **Camera movement is slow and deliberate** — No fast cuts, no handheld.
9. **Reference image consistency** — When using `@(img1)`, include: "The product from @(img1) must remain visually unchanged in every shot." and "Maintain product design and label details throughout."
10. **Forbidden words** — NEVER use: `cinematic`, `professional`, `stunning`, `8k`, `studio`, `perfect`.
11. **Aspect ratio** — `9:16` (vertical/social) or `16:9` (landscape). Default `9:16`.
12. **Duration** — 15 seconds single clip.

### `@(img1)` Reference Image Mapping

- Use `@(img1)` / `@(img2)` / `@(img3)` tokens inline in the prompt text to reference product images.
- Pass corresponding images via `referenceImages` array (index 0 = `@(img1)`, etc.).
- Keep the `@(img1)` tokens in the prompt text.

---

### Complete Template

Copy this and fill in the `{{VARIABLES}}`:

```
15 seconds {{CONTENT_TYPE}} video, {{CAMERA_STYLE}},
{{MOOD_DESCRIPTOR}}. The @(img1) ({{PRODUCT_DESCRIPTION}}) —
{{SURFACE_DETAILS}}, {{CONDITION_DETAILS}}. Set against a
{{BACKDROP}} on a {{SURFACE}}. {{ELEMENTAL_EFFECT_1}},
{{ELEMENTAL_EFFECT_2}}.

{{SHOT_1_TYPE}} — {{SHOT_1_DESCRIPTION}}.

Cut to {{SHOT_2_TYPE}} — {{SHOT_2_DESCRIPTION}}.

Cut to {{SHOT_3_TYPE}} — {{SHOT_3_DESCRIPTION}}.

{{SHOT_4_TYPE}} — {{SHOT_4_DESCRIPTION}}.
[Text overlay: "{{TAGLINE}}"]
[End card: "{{CTA}}"]

The lighting is {{LIGHT_SETUP}} — {{LIGHT_QUALITY}}.
The image is {{CAMERA_QUALITY}} — {{CAMERA_DETAILS}}.
The color grade is {{COLOR_GRADE}}.
The sound is {{AUDIO_TYPE}} — {{AUDIO_DETAILS}}.
```

---

### Quick-Start Examples

#### Example A: Energy Drink Can (escalating drama)

```
15 seconds product hero video, slow-motion macro photography,
dark and dramatic. The @(img1) (VOLT Energy — tall 16oz matte
black can with neon green lightning bolt logo, metallic finish) —
condensation droplets beading on the surface, ice cold. Set
against a deep black void on a dark reflective surface. Water
splashing dramatically around the base of the can, water droplets
suspended in mid-air catching green light from the logo.

Extreme close-up of the lightning bolt logo — water droplets
rolling slowly down the matte surface, each droplet catching the
green glow.

Cut to a hand reaching in from the right, gripping the can firmly
and lifting it — slow-motion water cascading off the base,
splashing outward across the reflective surface.

Cut to dramatic low angle looking up at the can — rain pouring
down from above, water streaming over the logo, the green glow
bleeding through the water.

Hero composition — two VOLT cans side by side on the wet
reflective surface, rain settling, ripples spreading outward.
[Text overlay: "MAXIMUM VOLTAGE. ZERO COMPROMISE."]
[End card: "Available at GNC and Amazon" + "Zero Sugar | 300mg
Caffeine | B-Vitamins"]

The lighting is a single spotlight from above with rim light on
edges — hard shadows below, product is the brightest element. The
image is tack-sharp on the label with slow-motion water capture.
The color grade is deep black shadows with electric green
highlights bleeding from the logo into the water. The sound is a
deep bass building to a drop at the splash moment — foley of the
can tab cracking, water impact, ice shifting.
```

#### Example B: Skincare Serum (reveal build)

```
15 seconds premium product showcase video, dramatic product
photography, moody and premium. The @(img1) (AURORA Night Serum —
frosted glass dropper bottle, rose-gold cap, translucent violet
liquid visible through the glass) — dewy droplets clinging to the
frosted surface, sealed and pristine. Set against a dark
teal-to-black gradient on wet black marble. Soft mist swirling at
the base of the bottle, light refracting through tiny water
droplets in the air.

The bottle emerges slowly from a veil of mist — blurred at first,
the frosted glass catching scattered teal light from the backdrop.

Cut to a smooth focus pull — the label sharpens, revealing the
gold AURORA text, a single droplet rolls down the glass and falls
to the marble surface.

Cut to the dropper lifting out of the bottle — a thread of violet
serum stretching and breaking, the drop falling in slow motion
onto the marble, spreading into a tiny pool.

Hero composition — the bottle centered on the marble, mist
settled, the violet pool in the foreground reflecting the
teal-to-black gradient above.
[Text overlay: "WAKE UP RADIANT."]
[End card: "Shop at aurora-skin.com" + "Retinol + Peptides |
Dermatologist Tested"]

The lighting is soft overhead diffusion with edge rim lights —
the rose-gold cap catches a highlight, deep shadows on the marble.
The image is razor-sharp on the glass texture with silky slow-
motion on the serum drip. The color grade is deep teal shadows
with warm rose-gold highlights on the cap and label. The sound is
ambient low drone with foley — glass clink, liquid drip, soft mist
hiss. No voice, no dialogue.
```

---

### Final Adaptation Checklist

Before outputting any prompt, verify ALL of these:

- [ ] **Format header** — 15 seconds, content type, camera style, mood descriptor
- [ ] **Product** — full physical description, surface details, condition
- [ ] **No people** — hands only if needed for grab/interaction shot
- [ ] **Product is the only subject** — described in full detail
- [ ] **Environment** — single deep backdrop color, reflective surface
- [ ] **Elemental interaction** — at least one primary + one secondary effect specified
- [ ] **Shot sequence** — 3-4 shots escalating from macro to hero composition
- [ ] **Camera movement** — slow and deliberate, no fast cuts, no handheld
- [ ] **Tagline overlay** — short, punchy, 4-8 words
- [ ] **End card** — where to buy + feature callouts
- [ ] **Technical quality** — lighting, camera, color grade, audio all specified
- [ ] **Audio** — music + foley, no voice, no dialogue
- [ ] **Word count** — 100-260 words
- [ ] **No forbidden words** — no "cinematic," "professional," "stunning," "8k," "studio," "perfect"
- [ ] **@(img1) included** — product image referenced in prompt text
- [ ] **Consistency** — product visually unchanged across all shots
- [ ] **Reflective surface** — doubles the product's presence

---

### Generation — SJinn seedance2

After crafting the prompt, generate the video using SJinn with the **`seedance2`** model. Always use `seedance2` — do not substitute another model.

**Before generating, detect the available method (in priority order):**

1. **SJinn MCP Server** — Check if the `sjinn` MCP server is connected. If available, call its video generation tool directly.
2. **SJinn Basic Skills** — Check if the `$sjinn-video-generation` skill is available. If available, invoke that skill to generate, passing these parameters:
   - **model:** `seedance2`
   - **prompt:** the finalized prompt text
   - **duration:** `15` seconds
   - **aspect:** `9:16` (default) or user-specified ratio
   - **reference images:** product images corresponding to `@(img1)`, `@(img2)`, etc.
   - **mode:** `quality`
3. **Neither available** — Prompt the user to install one:
   - MCP: Configure the `sjinn` server in `.mcp.json` (`https://mcp.sjinn.ai/mcp`)
   - Basic Skills: Run `npx skills add sjinn-ai/skills`

Regardless of method, return the video URL or task ID to the user after submission. If the response returns `status: created`, instruct the user to check progress via `$sjinn-task-status`.

---

### Output Format

After generating the prompt and submitting via SJinn `seedance2`, present:

```
## Product Hero Video

**Duration:** 15s
**Aspect Ratio:** {{9:16 or 16:9}}
**Reference Images:** {{list or none}}
**Model:** SJinn seedance2
**Mode:** quality

---

### Prompt

[The complete prompt text submitted to seedance2]

---

### Generation Result

[Video URL, task ID, or status returned by SJinn]

---

### Checklist
[Show the completed checklist with all items checked]
```

### Iteration

If the user wants adjustments, modify **one element at a time**:
1. **Elements feel wrong** — swap elemental effects from the element bank for the product type
2. **Mood is off** — adjust backdrop color and color grade together
3. **Product not prominent enough** — increase hero composition hold time, add rim light
4. **Pacing is rushed** — reduce to 3 shots, extend hero comp to 6-7 seconds
5. **Different shot sequence** — switch between escalating drama, reveal build, or pure spectacle
6. **Add a second variant** — include `@(img2)` in the hero composition shot
