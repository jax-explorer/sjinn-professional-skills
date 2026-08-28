# Set Piece Studio — Style Bible & Prompt Kit

Read this file before producing any Behind the Scenes prompt pair. Its fixed language and disaster tags are part of the set identity.

## Contents

1. Place conversion
2. Studio and camera lock
3. Disaster selection and exact tags
4. Image prompt construction
5. Video prompt construction
6. Hard negatives and quality check

## 1. Place Conversion

Use a real place or landmark name only to understand the request. In generation prompts, replace it with original generic visual language covering:

- skyline silhouette and tower spacing;
- building proportions, setbacks, roof shapes, and structural geometry;
- facade materials, weathering, and dominant colors;
- waterfront, terrain, street density, bridges, monuments, or observation structures described by shape only;
- distinctive visual rhythm without names, logos, protected signage, or exact branded design.

For an uploaded image, the image prompt must begin with exactly:

```text
Set your uploaded image as reference image 1.
```

Immediately follow it with:

```text
Use the uploaded image only as a guide for silhouette, architectural massing, colour relationships and composition. Reconstruct everything as a weathered hand-built miniature model. Remove all logos and wordmarks. Replace visible signage with original fictional text. Do not reproduce identifiable people. Never treat the reference as a real full-size environment.
```

Do not name the real source location anywhere else in either prompt.

### Default Disaster Inference

When the user supplies a place but no disaster, infer one without asking:

- coastal skyline or harbor: tsunami;
- riverfront or low-lying dense district: flood;
- dry desert or arid skyline: sandstorm;
- snowbound or cold high-rise district: blizzard;
- mountain basin or volcanic terrain: volcano;
- dense masonry or high-rise core: earthquake;
- industrial district: explosion or firestorm;
- ambiguous metropolitan scene: meteor.

Choose only one disaster family.

## 2. Studio and Camera Lock

Every prompt pair must visibly preserve all of these facts:

- A tiny weathered hand-built city or landmark model sits on a raised internal shoreline inside a massive in-floor effects tank approximately 30 metres across.
- The tank is sunk flush into the concrete floor. It is never a table and has no visible legs.
- The rim has grey hazard-striped coping, wet concrete, coiled hoses, and cables.
- A colossal blue chroma-key wall rises about five storeys, extends beyond the top of frame, and is covered by many small orange `+` tracking crosses in a dense grid.
- Chroma is always blue, never green.
- Full-size crew stand close enough to appear approximately as tall as the model towers. Include generic black `EFFECTS CREW` and grey `SPECIAL EFFECTS` shirts.
- Show a camera crane or jib, steel dolly track, FX hoses, and disaster-appropriate pumps, fans, pyro equipment, or actuator rigs.
- Place the model in the lower third. The towering blue wall, physical effect, airborne matter, and empty studio air fill the upper two-thirds.
- The frame cannot contain the whole room. The soundstage feels too large for the phone frame.
- The effect rises many miniature storeys while empty air remains visible above it. The disaster itself reveals scale.

Default camera: low at the tank lip beside the steel dolly track.

Allowed user-requested alternatives:

- raised gantry above the tank;
- crane-follow low over the model.

Maintain wide amateur phone framing, flat cool LED illumination, phone sensor grain, mild handheld movement, imperfect auto exposure, clipped highlights in bright spray or fire, natural practical haze, and unpolished BTS realism. Never turn the frame into a glossy commercial photograph.

## 3. Disaster Selection and Exact Tags

Use the selected family's physical setup and append its exact tag verbatim wherever `[DISASTER TAG]` appears. These tags are the complete authoritative tag set.

### Tsunami

- Physical setup: large water tank, elevated dump tanks, high-volume pumps, wave paddles, breakaway waterfront structures, and small floating miniature debris.
- Generic disaster text: `tsunami wave`
- Exact tag: `PRACTICAL TSUNAMI FX — real dump-tank water, pump-driven wave paddles, wet breakaway miniature structures, physical spray and floating miniature debris; no digital water simulation.`

### Volcano

- Physical setup: hidden smoke machines, ash hoppers, ember blowers, practical flame bars, pyro pots, and breakaway vent structures.
- Generic disaster text: `volcanic eruption`
- Exact tag: `PRACTICAL VOLCANO FX — real smoke machines, ash hoppers, ember blowers, practical flame bars, pyro pots and breakaway miniature vents; no digital lava or smoke simulation.`

### Explosion

- Physical setup: synchronized miniature pyrotechnic squibs, air mortars, smoke pots, breakaway facades, and physical debris.
- Generic disaster text: `explosion`
- Exact tag: `PRACTICAL EXPLOSION FX — synchronized miniature pyrotechnic squibs, air mortars, smoke pots, breakaway facades and real physical debris; no digital blast simulation.`

### Tornado / Dust

- Physical setup: giant industrial fans, directional dust cannons, overhead drop tubes, air jets, and lightweight physical debris.
- Generic disaster text: `tornado`
- Exact tag: `PRACTICAL TORNADO FX — giant industrial fans, directional dust cannons, overhead drop tubes, air jets and lightweight physical debris forming a real wind-driven vortex; no digital storm simulation.`

### Flood

- Physical setup: high-volume pumps, low dump tanks, rising-water gates, small wave mechanisms, drainage spillways, and floating miniature debris.
- Generic disaster text: `flood surge`
- Exact tag: `PRACTICAL FLOOD FX — high-volume pumps, low dump tanks, rising-water gates, small wave mechanisms, drainage spillways and real floating miniature debris; no digital water simulation.`

### Meteor

- Physical setup: a physical impact projectile or concealed strike point, pyro flash, compressed-air debris mortars, dust charges, and breakaway structures.
- Generic disaster text: `meteor impact`
- Exact tag: `PRACTICAL METEOR FX — a physical impact strike, pyro flash, compressed-air debris mortars, dust charges and breakaway miniature structures; no digital impact simulation.`

### Earthquake

- Physical setup: concealed mechanical actuator rigs beneath model sections, cable pulls, collapsing breakaway facades, dust charges, and falling miniature masonry.
- Generic disaster text: `earthquake collapse`
- Exact tag: `PRACTICAL EARTHQUAKE FX — concealed mechanical actuator rigs, cable pulls, collapsing breakaway facades, dust charges and real falling miniature masonry; no digital shake or destruction simulation.`

### Firestorm

- Physical setup: practical gas flame bars, pyrotechnic fire pots, smoke machines, ember blowers, air jets, and fire-safe breakaway structures.
- Generic disaster text: `firestorm`
- Exact tag: `PRACTICAL FIRESTORM FX — real gas flame bars, pyrotechnic fire pots, smoke machines, ember blowers, air jets and fire-safe breakaway miniature structures; no digital fire simulation.`

### Sandstorm

- Physical setup: industrial fans, dust cannons, overhead drop tubes, air jets, sand-colored practical particulate, and lightweight physical debris.
- Generic disaster text: `sandstorm`
- Exact tag: `PRACTICAL SANDSTORM FX — industrial fans, dust cannons, overhead drop tubes, air jets, sand-coloured practical particulate and lightweight physical debris; no digital storm simulation.`

### Blizzard

- Physical setup: high-output wind machines, cellulose snow cannons, overhead falling-snow rigs, ice mist, and wind-driven practical snow.
- Generic disaster text: `blizzard`
- Exact tag: `PRACTICAL BLIZZARD FX — high-output wind machines, cellulose snow cannons, overhead falling-snow rigs, ice mist and real wind-driven practical snow; no digital snow simulation.`

### Monster Stomp

- Physical setup: exactly one gigantic original creature represented by a practical articulated leg-and-foot rig, cable puppetry, a pneumatic stomp ram, dust charges, and breakaway structures.
- Generic disaster text: `original creature stomp`
- Exact tag: `PRACTICAL MONSTER-STOMP FX — one original non-franchise creature, an articulated leg-and-foot rig, cable puppetry, a pneumatic stomp ram, dust charges and breakaway miniature structures; no named creature and no digital destruction simulation.`

Never combine disaster families unless the user explicitly asks for a combination. For a monster, never imitate or name an existing franchise creature.

## 4. Image Prompt Construction

Write exactly one complete English image prompt. Start with one place-specific paragraph that defines the IP-safe miniature architecture, materials, colors, terrain, practical disaster setup, FX machinery, and camera vantage.

Append this signature clause verbatim, replacing all three bracketed fields. `[THE PLACE]` must contain only generic shape, color, material, density, and terrain language. `[DISASTER]` must use the selected family's generic disaster text. `[DISASTER TAG]` must use its exact tag.

```text
Amateur behind-the-scenes phone photo inside an ENORMOUS cavernous film soundstage the size of an aircraft hangar. A tiny handbuilt MODEL of [THE PLACE — generic, never a real name] sits at model-railway scale on a raised shoreline inside a MASSIVE in-floor water tank sunk flush into the concrete floor (no table, no legs), ~30m across, grey hazard-striped coping and coiled cables round the rim. Towering behind and above: a COLOSSAL BLUE chroma-key wall rising ~5 storeys and running off the top of the frame, covered in many small orange "+" tracking crosses in a dense grid. A massive practical [DISASTER] tears across the model and erupts MANY STOREYS HIGH, spray/dust/ash cresting far up the screen with empty air still above. Full-size crew in black "EFFECTS CREW" and grey "SPECIAL EFFECTS" tees at the tank lip stand as TALL as the model towers, a distant row tiny against the far wall; camera crane/jib + steel dolly-track in shot. Wide phone framing — model in the LOWER THIRD, towering screen + air filling the top two-thirds, nothing fully contained. Flat cool LED wash, sensor grain, mild handheld, auto-exposure clipping the spray — a real phone clip, NOT a render. [DISASTER TAG]
```

Then append the complete hard negatives from section 6 verbatim.

## 5. Video Prompt Construction

Write exactly one complete English video prompt for one continuous amateur BTS phone clip. It must use the exact same set descriptors chosen for the image prompt and treat the generated image as the first frame. Do not redesign or relocate anything.

For the default eight-second clip, use this exact temporal structure and fill in concrete actions appropriate to the selected FX setup:

```text
0–2s — ESTABLISH: The giant quiet studio holds. The tiny miniature is calm. Crew wait around the tank. The cavernous room and towering blue screen dwarf everything.

2–4s — TRIGGER: A director calls "Action!" off-camera exactly as the physical FX machinery fires.

4–6.5s — HERO IMPACT: The practical disaster violently crosses the miniature. Physical water, debris, ash, fire, snow or dust rises many miniature storeys high. Breakaway structures react appropriately. Crew flinch or step backward. The crane or jib moves through frame. Real particles, water, smoke and debris interact naturally with the model.

6.5–8s — AFTERMATH: The violent movement loses energy. Mist, smoke, dust or haze hangs in the soundstage. Water sheets from the tank edge where appropriate. Loose debris settles. The handheld phone framing naturally re-settles into a loop-friendly end state.
```

Then add a single sound paragraph. It must specify the selected effect's roar or crash, crew shouts, the director saying `Action!` exactly at the trigger, machinery hum from the visible pumps, fans, pyro or actuator equipment, and appropriate physical impact sounds. The disaster roar begins with the physical impact, never before it. The paragraph's final literal words must be:

```text
no music, no narrator
```

After the sound paragraph, append the same completed signature clause used in the image prompt and then the same complete hard negatives. Do not include cuts, separate shots, narration, score, or a second disaster.

If the user explicitly changes duration, preserve Establish / Trigger / Hero Impact / Aftermath in the approximate proportions `25% / 25% / 31% / 19%`, rewrite all timestamps to cover the requested runtime exactly, and keep the director's `Action!` at the trigger boundary.

## 6. Hard Negatives and Quality Check

Append this paragraph verbatim to both prompts:

```text
Negatives: NOT a tabletop diorama / desk model / model on a table with legs; NOT a cramped small room or low ceiling; NOT the model filling the frame or close tight framing; NOT a short blue screen with its top/side edges in frame; NOT a few large sparse crosses; NOT the whole room contained; no CGI/3D render/game-engine/videogame, no cartoon/anime/illustration, no glossy Octane sheen, no plastic/waxy, no HDR overcook, no fantasy glow, no clean studio-photo look; stays a small MODEL in a huge studio, never the real full-size city; no captions/subtitles/on-screen text, no watermark, no logos, no aspect ratio, no AI tool names.
```

Before generation, silently verify:

- exactly one image prompt and one video prompt;
- prompts are English and contain no real place, landmark, franchise, brand, product, company, or person names;
- uploaded-image opening and reference paragraph are exact when required;
- the image and video describe identical architecture, materials, colors, machinery, camera, crew, lighting, and scale;
- small model, lower third, immense blue wall beyond frame, many small orange `+` crosses, flush in-floor tank, hazard coping, cables, crew scale cue, jib or crane, and dolly track are explicit;
- disaster is physical, uses one supported family, includes its exact tag, rises many model storeys, and leaves empty air above;
- video covers the full duration, says `Action!` at the trigger, starts the roar only on impact, ends in a loop-friendly aftermath, and its sound paragraph ends with `no music, no narrator`;
- both prompts end with the complete hard negatives.

Fix every failed item silently.
