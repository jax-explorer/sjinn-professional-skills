---
name: gta-style-video
description: "Turn a scenario or reference into a GTA-style third-person gameplay video prompt and, when requested, generate it with SJinn Seedance 2.5. Use for GTA style video, GTA风格视频, 游戏实机感短片, everyday-life stealth missions, survival rescues, fantasy action-adventures, and open-world exploration trailers with persistent HUDs. Supports continuous gameplay, a single-cut payoff, and exploration montages; not for game programming or ordinary cinematic videos without gameplay."
---

# GTA Style Video

Turn the user's idea into a short sequence that feels controlled by a player: a clear objective, visible decisions, obstacles with physical solutions, a responsive third-person camera, and a persistent HUD that reflects what actually happens.

“GTA-style” describes the gameplay presentation. Do not automatically add crime, guns, police, a modern city, franchise characters, or logos. An office escape, a sunken temple, a rescue, and a wholesome winter adventure can all use this grammar.

## Scope and defaults

- If asked to write, improve, or translate a prompt, deliver the prompt only. If asked to create this skill, edit skill files only. Neither request authorizes media generation.
- If asked to generate a video, finish the brief and prompt, show a concise production summary, and submit within the user's existing authorization. Do not add a mandatory approval round when the user has already requested generation.
- Default format: **30 seconds, 16:9, photorealistic third-person gameplay**, using **SJinn `seedance2.5`, 720p** when generation is requested and that model is available. Explicit user choices override defaults within the selected tool's limits.
- Write generation prompts in English by default; explain decisions in the user's language. Keep dialogue and visible text in their separately selected languages.
- With no dialogue request, use ambience, SFX, and music without invented speech. Default HUD language is English; no subtitles or caption bars. User-requested subtitles, Japanese UI, stylization, title cards, and silence override these defaults.
- Prefer direct text-to-video, with supplied character/environment references when useful. Do not require an extra first-frame image generation, character sheet, or reference approval for every request.

## 1. Extract the playable premise

Use the supplied brief before asking questions. A short theme is enough to develop an original scenario. Infer a compact location and ordinary mechanics; ask only for a missing must-have that materially changes the result.

Establish:

| Field | What to decide |
|---|---|
| Player | One clearly identified playable character; supporting cast and exact count |
| Objective | A visible success condition: exit, rescue, activate, discover, deliver, or reach |
| Pressure | A pursuer, detection risk, unstable environment, scarce resource, or mystery |
| Mechanics | A small set of visible verbs: crouch, peek, scan, climb, distract, support, dodge |
| Route | Connected spaces, start/end positions, and any permitted location/time jumps |
| Presentation | Camera/edit mode, visual treatment, duration, ratio, and required ending |
| Languages | Dialogue language, HUD language, and environmental signage separately |
| Assets | Actual references and their roles; distinguish them from example placeholders |

Build the sequence around **goal → obstacle → player response → world/HUD consequence → payoff**. Do not mistake walking through pretty scenery beneath a minimap for gameplay. A cozy sequence can use discovery, climbing, warmth, and route finding instead of combat.

Clean copied social-media formatting: `[17:00](https://...)` becomes the literal clock value `17:00`, not a video timestamp or a link in the prompt. A link named `@Image1` is not evidence that an image was supplied. Use real attached assets or omit the reference binding. Preserve genuine platform-provided asset tokens exactly.

## 2. Select one camera/edit contract

| Mode | Use when | Contract |
|---|---|---|
| **Continuous mission** | A local escape, traversal, rescue, or encounter | One physically connected route and one unbroken third-person shot by default; if the user permits cuts, enumerate them and preserve state at every cut. No unexplained time or place jumps. |
| **Mission + payoff cut** | A tense mission ending in a reaction or joke | For a 30s clip, default to continuous gameplay at 0–27s and one locked shot at 27–30s. Exactly one hard cut at 27s. For another duration, allocate a readable ending; do not copy the 27s boundary blindly. |
| **Exploration trailer** | Several locations, times of day, seasonal memories, or discovery beats | Declare an intentional montage with exact cut boundaries. Each gameplay shot remains connected to the player. Location and time changes are allowed at those cuts; identity and interface persist. Use a title card only when requested or appropriate to a trailer brief. |

Honor an explicit mode. Do not apply the office example's single-cut rule to the winter montage, or turn a requested continuous mission into a trailer to hide continuity problems. Define a special cinematic reveal or final frontal shot as an explicit exception to ordinary gameplay framing.

## 3. Lock identity, geography, and state

**Character lock.** Bind every actual reference to a role: face/identity, wardrobe, location, style, or motion. State exclusions when necessary, such as “face only; use the adult office outfit below.” Without an image, use one stable text identity and never claim an exact reference match. Fix hair, outfit, body proportions, accessories, voice, and prop ownership. Supporting characters need distinct silhouettes and a location of first appearance; traits such as “only the boss is bald” belong only to scenarios that need them.

**Route and blocking.** Write the route as a compact chain of adjacent spaces. Explain corners, doors, stairs, occluders, and vertical travel. A new setting can remain compact; a user-specified large building cannot be traversed instantly. For cover, establish who is on each side and whether the material blocks vision: clear glass does not hide a person unless a solid frame, frosting, reflection, or other occluder actually breaks the sightline. Enemies follow established sight/sound and access routes.

**Persistent state.** Track only meaningful changing values: current objective, alert state, stamina, item ownership, rescue count, injury, wetness, damage, moved furniture, opened doors. Changes must have a cause. An injured companion remains slower, a thrown object stays where it landed, a wet explorer stays wet after surfacing, and a used ability does not silently reset. Companions remain accounted for after rescue; widen framing when group movement matters.

For a final reverse shot, specify the camera's physical side of the doorway and what is behind the actor. In the elevator variant the lens is inside beside the doorway, facing inward; doors close behind the camera. In the glass-exit variant the lens is outside, looking toward the entrance; the player is outside and the boss remains inside. Do not combine their geometry.

## 4. Budget actions before writing beautiful prose

Draft consecutive, non-overlapping ranges covering the entire runtime. For 30 seconds, about five to seven beats is a useful starting point, not a requirement. Every beat needs:

`time → location → trigger → player action → visible end state → camera → HUD change → audio`

Give each beat one dominant action plus a small reaction or transition. Budget footsteps, turning, door movement, interaction time, and speech. Do not fit several floors of travel, a fight, four exchanges of dialogue, and a rescue into four seconds. Keep voices brief and leave space for breathing and SFX; a natural read-through is more useful than an arbitrary character count.

When overloaded, simplify optional mechanics and repetitive dialogue first, keeping the mission's causal spine. Disclose meaningful changes. If all events, exact dialogue, duration, and no-cut constraints are explicit must-haves and cannot coexist, explain the conflict and ask which may change before generating. Never silently speed up the action, introduce hidden cuts, or omit required events.

Read the matching recipe in [Scenario recipes](#scenario-recipes) for office stealth, survival rescue, fantasy traversal, or winter discovery. These are adaptable structures, not compulsory casts or plots.

## 5. Make camera, HUD, and audio behave like a game

**Camera.** Start with the player already acting. Default to chest-height following roughly 1.5–2 m behind, slightly offset from the spine, with soft follow lag on turns. Crouching lowers the camera; group threats widen it; interaction can tighten it. Keep the decisive action visible. Travel through open space without clipping furniture or doors; do not rotate to a frontal movie shot during ordinary running. Smooth field-of-view changes are not permission for hidden cuts. Values are directing guidance, not guaranteed lens controls.

**HUD.** Choose one layout and retain it across every shot. Default: health/stamina top-left, objective top-center, clock or alert indicator top-right, circular minimap bottom-left, context buttons bottom-right, brief notifications at right-center. Preserve a user-specified alternative instead of adding a second map. Use only relevant meters, such as warmth for winter or oxygen underwater. Screen-space elements stay anchored; world-space markers intentionally follow the relevant character or object. Keep the map consistent with the route and turn its player arrow with movement. Advance objectives, alerts, rewards, and counters only after visible triggers. Limit simultaneous notifications and keep text short enough to read.

**Visual treatment.** Choose a coherent look: live-action photorealism; realistic AAA game rendering; or stylized, hand-painted animation with believable light and materials. Resolve a hybrid by assigning treatments to specific parts instead of stacking contradictory instructions. Do not add “no animation” to a requested animated-film aesthetic. Describe relevant contact, weight, inertia, fabric, breath, water, snow, and light sources rather than relying on “AAA/8K” adjectives. Lighting follows location and time; an explicit montage may progress from afternoon to night to dawn.

**Audio.** Distinguish dialogue, ambience, physical action SFX, UI feedback, and music. Tie alert stings, heartbeat, and victory sounds to actual state changes. Match acoustics to the space: underwater muffling, stairwell echoes, or office sound damped by closing doors. Name speakers and quote their exact lines in the selected language. Spoken dialogue is not an instruction to generate subtitles. Avoid competing speech at the decisive action beat.

## 6. Compile, review, and deliver

Use [Gameplay prompt architecture](#gameplay-prompt-architecture) to compile one directly usable prompt. Keep global locks in one place and use timed beats for changes. Remove unused template fields, missing-reference tokens, source URLs, duplicate constraints, and irrelevant negatives.

Before delivery, check:

- Objective, action, and visible outcome form a clear causal chain.
- Runtime is fully covered; cut count matches the mode; physical travel and dialogue fit.
- Player/cast count, identity, inventory, injury, environment, and HUD state remain consistent.
- Camera can occupy its stated positions; cover and final-shot geometry work.
- Rendering style, speech language, HUD language, signs, subtitles, and title-card rules do not contradict each other.
- Generation settings use the selected tool's actual schema, not quality words embedded in prose.

For a prompt request, return a short settings line, an asset-role map only when assets exist, and **one complete prompt** in a code block. Add at most a few material assumptions or conflicts. If the user asks for the prompt alone, omit the commentary.

For a generation request, read [SJinn generation](#sjinn-generation) and submit the prepared prompt through available SJinn tools. Exact HUD typography, precise cut timing, and perfect identity continuity are generation targets, not guarantees. If the user requires frame-exact cuts or exact text, plan a separate editing/compositing pass and disclose that need before spending credits; never claim a prompt alone enforces it. Post-production must be separately supported by the available tools and preserve the approved shot contract.

Deliver the actual asset when available, or accurately label a submitted task as pending. Evaluate only footage that can be inspected. Correct the smallest observed failure; do not repeatedly generate variants without a user-provided retry budget.

## Gameplay prompt architecture

Use this section when compiling the final prompt. Fill the relevant blocks below, then remove brackets, editorial notes, and unused sections. This is a writing scaffold, not text to submit unchanged.

Put output duration, aspect ratio, model, and supported resolution in a separate settings line/tool call. Timed events and cut boundaries still belong inside the prompt because they direct action. Frame-rate language describes a desired motion feel unless the actual generation interface exposes an FPS control.

### Copyable structure

```text
PLAYABLE PREMISE
A third-person [genre] gameplay sequence in [place/time]. The player is [name], trying to [visible success condition] while [pressure]. The story advances through [two or three mechanics]. [Chosen rendering treatment and emotional tone].

REFERENCE ROLES / CHARACTER LOCK
[Only actual attached reference identifiers, their roles, and what must not transfer.]
PLAYER — [name, age when relevant, face/hair, outfit, proportions, accessories, voice]. Preserve this identity and prop ownership throughout.
SUPPORTING CAST — [separate names, distinguishable appearances, first locations, relevant behavior]. [Exact group count when it matters].

WORLD / ROUTE / STATE
[Start → connected locations → destination, or explicitly separated montage locations.]
[Critical geometry: doors, cover, water shaft, stairs, visibility, camera clearance.]
[Initial inventory, injury, resource, and environmental state; what persists after change.]
[Motivated lighting/weather by location or shot.]

CAMERA / EDIT CONTRACT
[Continuous / one payoff cut / enumerated montage boundaries.]
[Initial camera position, tracked player, follow response, allowed widening/tightening.]
[If applicable, exact final camera position, actor orientation, background and door motion.]

HUD CONTRACT
[Language and fixed anchor of each relevant element.]
[Initial objective and resource state.]
[Screen-space UI stays fixed; any world-space indicator follows its named target.]
[Subtitle policy, environmental sign language, and title-card behavior if relevant.]

TIMED GAMEPLAY
[00:00–00:XX] [BEAT NAME]
[Start position and trigger.] [One dominant player action and visible consequence.]
Camera: [how the existing gameplay camera follows this event].
HUD: [a short exact string/state update, caused by that event].
Audio: [physical sound, UI feedback, music change; speaker and exact dialogue if any].

[Continue consecutive time ranges through the requested endpoint.]
[Write CUT at each permitted cut; never imply a cut merely by starting a new beat.]

PHYSICAL / VISUAL LOCKS
[Scenario-specific contact, inertia, material, character performance and light continuity.]

AUDIO CONTINUITY
[Dialogue language or no dialogue; ambience; score progression; across-cut audio behavior.]

ENDING / EXCLUSIONS
[Visible final state: mission complete, discovery, cliffhanger, or active control continues.]
[A short set of actual failure risks: identity swaps, camera clipping, teleportation, arbitrary UI resets, etc.]
```

### Construct the beat from gameplay, not camera spectacle

Weak: “An epic camera zoom reveals an intimidating boss; the player looks scared.”

Useful: “The boss enters the T-junction ahead and glimpses NAGI. The alert indicator turns red. NAGI crouches behind the opaque cabinet, which blocks his sightline. The camera swings through the open left aisle to keep her and the cabinet edge visible. The boss searches her last seen position while the alert meter drains.”

This defines a trigger, a player choice, valid cover, a physical camera path, enemy behavior, and a UI consequence. Reuse that structure for a cracked bridge, a noise distraction, a locked gate, or a mysterious train signal.

### Beat budget and continuity notes

Use a small internal table for difficult sequences; do not force the user to read it unless it helps resolve a conflict:

| Range | Player location/end state | Cast/props | Objective/resource change | Cut? |
|---|---|---|---|---|
| 0–6s | Desk → first cover | Tote in player's hand | Exit objective appears | No |
| 6–12s | Cover → alcove | NPC walks past | Detection risk passes | No |
| 12–18s | Alcove → cabinet | Boss holds folder | Alert red → searching | No |
| 18–24s | Cabinet → gate | Tote still held | Route found | No |
| 24–27s | Gate → exterior | Boss behind glass | Access granted | No |
| 27–30s | Exterior, facing lens | Same tote and clothing | Mission complete | At 27s |

The table is a feasibility aid, not an additional required scene. Change durations and mechanics to match the actual brief.

### Constraint precedence inside the creative brief

Honor the user's explicit must-haves first within actual tool limits. Use supplied references only for their assigned roles. Preserve causal continuity and readable action before adding optional spectacle. Apply this skill's defaults only to unset fields. If two explicit must-haves conflict, surface the specific conflict rather than choosing silently.

Use local, targeted exclusions. “No plastic skin” can help a photographic office clip; “no anime” would damage the winter animated-film brief. “No dialogue” is appropriate for the silent temple example, not the Japanese office dialogue example. A requested title card is not a forbidden subtitle.

## Scenario recipes

Use the matching recipe. These adapt the supplied fantasy, school rescue, office escape, and winter exploration examples into reusable gameplay structures. The source examples are inspiration, not mandatory content for every video. Preserve explicit user requirements when adapting them.

### A. Office stealth comedy — worked prompt

Use for mundane stakes staged as a stealth mission: leaving work, avoiding another meeting, slipping past a queue, or catching the last train. Keep the threat socially ordinary; the camera, UI, and score create the exaggerated tension.

This version ends **outside the glass exit**. It is a complete text-only example; it does not pretend a face reference exists. Settings: `seedance2.5`, 30 seconds, 16:9, 720p. The single cut and exact HUD text are generation targets to inspect afterward.

```text
PLAYABLE PREMISE
A photographic third-person stealth-action game sequence inside a modern Japanese office at 17:00. NAGI has finished work and must exit before she receives another assignment. Play the mission completely seriously while the obstacles remain gently comic. Begin in playable movement, with a fixed game HUD already visible.

CHARACTER LOCK
NAGI: Japanese woman, 25, long straight black hair with blunt bangs, white short-sleeve office blouse, charcoal tailored trousers, black belt, white minimalist sneakers, clipped employee ID, small black work tote. One NAGI throughout; preserve her face, proportions, clothing and accessories. She carries the tote in her left hand and uses her right hand for interactions. Natural adult Japanese female voice.
SENIOR COWORKER: woman in her late 40s, short brown bob, glasses, pale-blue blouse, dark skirt, clipboard; begins beside the first desk cluster.
PARTY COWORKER: man in his late 20s, messy black hair, cream sweater, carrying a cake box with two balloons tied to its handle; begins in the break-room doorway.
DELIVERY WORKER: tall man in his early 30s, short black hair, dark uniform, pushing a supply cart; begins in the storage passage.
BOSS: short, stout man in his 60s, bald crown with a white side fringe, gold glasses, charcoal three-piece suit, thick blue folder. The boss is the only bald character. He first appears at the main-corridor junction.

ROUTE / GEOMETRY
Workstation → adjacent break-room threshold → short storage passage → main corridor → ID gate → glass exterior door. These are compact neighboring spaces, not distant rooms. From the main junction, the gate and door are only a few steps away. The low desk divider and opaque storage boxes provide cover. A solid structural pier beside the glass partition blocks the boss's sightline; clear glass alone never conceals NAGI. The ID reader opens a waist-high swing gate. The manually opened glass exit immediately beyond it has a visible push bar and a slow door closer.

CAMERA / CUT CONTRACT
From 0–27 seconds, one continuous third-person take: chest-height, roughly 1.5 meters behind NAGI, slightly camera-right, with gentle spring lag through turns. Lower with her crouch and widen slightly for the boss encounter. Move around furniture through open space, never through it. At exactly 27 seconds, make the only hard cut. From 27–30 seconds, hold a static exterior eye-level view facing the doorway and NAGI. NAGI is fully outside; the boss is behind her inside the building. The closing door remains behind her, never crossing between her face and the lens.

HUD
English game UI: health/stamina top-left, objective top-center, clock 17:00 and alert state top-right, circular office minimap bottom-left, context buttons bottom-right, one brief notification at a time at right-center. Keep these anchors across the cut. Map geometry matches the physical office route. NPC vision cones turn with those NPCs; the player's arrow follows NAGI. A red exclamation marker is world-anchored above the boss only while alerted. Japanese environmental signs may exist. No subtitles or caption bars.

[00:00–00:06] SHIFT OVER
The desk clock reaches 17:00. NAGI lifts her tote, crouches behind the desk divider, and lets the senior coworker's searching gaze pass above her. When the coworker turns toward a ringing phone, NAGI slips into the adjacent aisle. The camera lowers behind her and follows her steps.
HUD: SHIFT OVER, then OBJECTIVE: EXIT THE BUILDING. Stamina starts full; alert remains green.
Audio: phone ring, chair creak, restrained stealth synth. NAGI whispers: 「定時だ。」

[00:06–00:11] BALLOON PATROL
At the open break-room threshold, the party coworker crosses NAGI's path carrying cake and balloons. One balloon gently brushes her bangs. She freezes for a beat, waits for him to pass, then moves behind him into the storage passage. Her tote stays close to her left hip.
HUD: THREAT PASSED appears only once he has passed.
Audio: faint balloon squeak, footsteps, NAGI's held breath and tiny relieved exhale.

[00:11–00:16] SILENT INTERACTION
The delivery cart rolls past stacked opaque boxes in the narrow passage. NAGI crouches beside the stack to leave room. A small lightweight box tips off its low edge; she catches it in her free right hand before it hits the floor and places it back. The cart continues forward, clearing the passage. NAGI rises and follows into the main corridor.
HUD: SILENT INTERACTION +50 after the catch.
Audio: caster wheels rattle across a floor seam; no crash. Cart wheels rotate and swivel against the floor.

[00:16–00:22] BREAK LINE OF SIGHT
The boss appears at the main-corridor junction with his folder and sees NAGI. The red marker and alert sting activate. He begins: 「なぎさん、これ今日中に…」 NAGI ducks around the solid pier beside the glass partition. The pier fully occludes her while she takes two quick steps along its far side toward the gate. The boss pauses at her last seen position instead of teleporting ahead. The camera follows around the pier through the open aisle, keeping her movement legible.
HUD: ALERT → BREAK LINE OF SIGHT → ESCAPE ROUTE FOUND. Alert moves red to amber after his view is blocked; stamina decreases during the quick movement.
Audio: short heartbeat pulse, cloth movement, folder rustle.

[00:22–00:27] ACCESS GRANTED
NAGI reaches the adjacent reader. Holding the tote in her left hand, she presents her clipped ID with her right: one error beep. She adjusts the card angle and rescans; a green light and success chime unlock the swing gate. She passes through, takes the single step to the exterior door, presses its push bar and exits. The following camera clears the doorway with her. The boss walks into view inside but remains behind the gate. NAGI begins to turn just as the continuous shot ends.
HUD: SCAN ID → ACCESS GRANTED. The objective remains active until she crosses the threshold.
Audio: two distinct scanner responses, latch click, door hinge, outdoor air entering the mix.

HARD CUT AT 27 SECONDS — THE ONLY CUT
[00:27–00:30] OFF THE CLOCK
Locked exterior shot facing NAGI. The boss is visible inside through the glass behind her and calls: 「明日でいいから！」 She smiles toward the lens, answers brightly 「はい！」 and takes her first step away. The door closer eases the door shut behind her.
HUD: MISSION COMPLETE and STEALTH RANK: S; alert returns to green. Keep the other HUD anchors unchanged.
Audio: the same ambience and score continue across the cut; the boss's voice becomes muffled as the door closes; a brief comic victory fanfare resolves the tension.

VISUAL / PHYSICAL LOCKS
Photographic human faces and natural skin texture, realistic eyes and hair, fabric creasing during crouches, planted feet and attached contact shadows. The tote has weight; handles pull taut and the bag settles after each stop. Boxes, balloons, and cart have consistent scale and inertia. Late-afternoon daylight comes from the same window wall along the route, with motivated exterior light after the cut. No identity swaps, duplicate characters, invisible transport, camera clipping, extra cuts, floating feet, or unexplained HUD resets. All dialogue is Japanese; all HUD text is English.
```

**Elevator variation:** Replace the gate/glass-door ending, not just its noun. Put an already-waiting elevator at the corridor's end. The call button is beside the doorway; doors open fully; NAGI and the following camera enter; she turns toward the entrance. After the 27s cut, the lens is inside beside the doorway looking inward at her, with the metal rear wall behind her. Doors close behind the lens, narrowing corridor light on her face. Use the boss's off-camera call and a short reply. Never show exterior glass doors, a second exit, or doors sliding across her face in this variant.

### B. Survival rescue — mission purpose over combat

Use for getting vulnerable companions out of danger. In the school example, the protagonist is an 18-year-old student; use practical, ordinary uniform styling and non-graphic defensive action. The objective is rescue, not clearing the building.

Lock four distinct friends: A is the player; B and D support C, whose ankle injury limits movement. Account for all four after rescue. Carry a damaged broom handle as an improvised defensive tool; injury and damage persist. Keep Japanese dialogue separate from English HUD text.

**Compact 30-second adaptation:** start on the same floor, near the occupied classroom. This deliberately shortens the reference's multi-floor journey; disclose that change when proposing it, and do not use it when the full route is mandatory.

| Time | Gameplay / consequence |
|---|---|
| 0–5s | Already moving in the corridor, A hears B's brief call from the classroom. Objective: RESCUE YOUR FRIENDS. A observes an infected figure blocking the direct approach. |
| 5–10s | A throws a nearby tray down a side aisle. It lands and rings; the infected follows the sound, opening the route. The tray remains on the floor. |
| 10–15s | A reaches the adjacent classroom and opens its door. B and D already have C supported between them. Rescue count reaches 3; objective becomes REACH THE REAR EXIT. |
| 15–22s | They enter the corridor together at C's slower pace. A uses a brief block-and-push to redirect one lunge into a desk, creating space to continue. Stamina falls; nobody abandons C. |
| 22–27s | B and D help C through the nearby emergency door while A follows last. Pursuers navigate the same corridor from behind. |
| 27–30s | All four are outside; the door shuts. FRIENDS RESCUED updates to REACH THE EVACUATION POINT as the camera remains behind A and the group begins moving. |

Keep the camera attached to A and widen for the group. Limit speech to a few short exchanges. For the original entrance → blocked stairs → lab → preparation room → upstairs classroom → rear stairs route, plan more time or explicitly permitted cuts; do not claim that changing labels makes the full route traversable in 30 seconds.

### C. Sunken ruins — linked traversal and boss awakening

Use for fantasy action-adventure with no dialogue. Lock one explorer, lightweight weathered clothing, climbing harness, backpack, left-forearm golden water-control device, and a curved sword on the back. The device's side and sword ownership never swap.

Build one compact vertical environment: a ruined ledge above a flooded shrine, a submerged mechanism immediately below, and a surface platform reached through an adjacent open shaft. The guardian is colossal stone and coral with slow, heavy movement; it breaks walls when they are too small for it. Use a health/stamina layout plus an oxygen meter while submerged; never add modern weapons by default.

| Time | Gameplay / consequence |
|---|---|
| 0–5s | The explorer runs along a cracking ledge and makes one visible gap jump to the shrine entrance. The camera widens to reveal the submerged city, then returns behind them. |
| 5–10s | A DIVE prompt precedes a visible plunge into the nearby flooded opening. Camera and explorer enter water continuously; audio muffles and oxygen becomes relevant. |
| 10–15s | At the close submerged pedestal, the left device activates the machine. Golden channels light in sequence. Objective completes only after the rings turn. |
| 15–20s | The guardian's eyes ignite across the chamber. A heavy arm breaks free; the explorer turns toward the already-visible exit shaft. Boss health appears. |
| 20–26s | One water-current ability carries the explorer through the adjacent shaft to the surface platform. Show water propulsion, surface break and a reachable ledge; the device enters cooldown. |
| 26–30s | Still wet, the explorer pulls onto the platform. A gigantic stone hand grips its far edge. The player draws the sword; the camera settles behind them as the encounter begins. |

This budget ends at the **start** of combat. If a successful dodge and counterattack are mandatory, remove optional earlier traversal or extend the runtime with user agreement. Do not insert wall-running, rope swinging, a long swim, a complete puzzle, an escape, and multiple attacks into the same short beat. Maintain underwater lighting/refraction, muffled sound, water drag, and persistent wet clothes above the surface.

### D. Winter mystery — open-world exploration montage

Use for nostalgic friendship, village exploration, and discovery without violence. This is a montage across places and times; it is not one continuous mission take.

Lock three children: the player boy in a red knit cap, cream winter jacket, navy snow pants and blue backpack; a boy in a green puffer vest and wool scarf; a ponytailed girl in a lavender coat, pink backpack and mittens. Only the red-cap boy is player-controlled. Use a coherent animated-film treatment: softly stylized faces and painterly scenery with physically believable snow, wool, light and breath. Do not simultaneously demand documentary faces and prohibit stylization.

HUD: snowflake plus stamina/warmth top-left, Japanese objective top-center, date/time top-right, circular minimap bottom-left, Japanese action prompts bottom-right. Keep exactly this layout throughout. World signs and requested title typography are allowed; character chatter does not become subtitle bars.

| Time | Shot / clock / player action | Objective or payoff |
|---|---|---|
| 0–4s | 1月27日 10:24. Follow behind the red-cap boy sledding between wooden village houses; his friends establish the trio. Powder and warm window light sell winter. | 「雪山のてっぺんまで競争！」 |
| 4–8s | CUT. 14:10, frozen waterfall. From behind the player, approach translucent ice where an amber glow moves. Keep the camera on the accessible bank. | 「凍った滝の秘密を探せ」; investigate prompt |
| 8–12s | CUT. 16:32, cedar treehouse. The player climbs the last ladder rungs into the refuge where both friends study a map. Warmth increases near the kotatsu. | 「秘密基地をあたためよう」; unknown station marked on map |
| 12–17s | CUT. 19:15, winter festival. Follow the trio past lanterns to an old sign pointing toward an absent station. A distant train whistle interrupts their chatter. | 「存在しない駅への道を探そう」 |
| 17–23s | CUT. 20:08, disused mountain platform. The player turns on a flashlight and follows snow-covered rails toward one amber signal. Friends stay nearby. | 「夜の線路を追え」; flashlight prompt |
| 23–28s | CUT. Next dawn, 1月28日 05:12. On the overlook beside the signal tower, the player brushes snow from a switch and activates it. Light reveals a buried station roof; the camera widens from behind the trio. | 「雪の下の駅を発見！」; location 雪見ヶ峰 |
| 28–30s | Same sunrise view; **no new cut**. Title overlays the valley and the revealed station; HUD anchors persist with notifications cleared. | 「ぼくらの冬休み」 / 「— 雪の下の駅 —」 / 「冬休みは、まだ終わらない。」 |

Five hard cuts: 4, 8, 12, 17, and 23 seconds. A title appearing over the held final view is not a sixth cut. If the user requires 1月27日 to remain fixed, preserve it and establish non-chronological trailer shots instead of claiming a linear overnight journey. Do not silently change an explicitly fixed calendar.

Use sled scrape, cedar wind, soft village drums, a single distant train bell, firewood, and a gentle piano/string reveal. The mystery stays warm and magical. Avoid adding adult pursuers, zombies, weapons, threatening jump scares, or unwanted horror because the title mentions an impossible station.

## SJinn generation

Apply this section only when the user requests actual generation. These fields were checked against the available SJinn MCP tool schema on 2026-09-20. Reinspect the active tool schema before submitting; it takes precedence if changed. Do not infer provider capabilities from another product's Seedance interface.

### Standard request

Use available SJinn tool discovery; common operation names are `create_video_task`, `upload_asset`, `create_compose_task`, and `get_task`. Namespace prefixes depend on the client. A missing connector does not prevent writing the prompt; explain the missing generation capability without pretending a task was submitted.

For the usual 30-second request:

```yaml
model: "seedance2.5"
prompt: "<the completed gameplay prompt>"
duration: 30
aspect_ratio: "16:9"
resolution: "720p"
# image_urls: ["<actual reference asset URL>"]  # only when supplied/useful
```

For `seedance2.5` in the checked schema:

- Duration: 4–30 seconds. Default to an integer duration.
- Resolution: `480p` or `720p`; this skill explicitly requests `720p` unless the user chooses otherwise.
- Ratios: `21:9`, `16:9`, `9:16`, `1:1`, `4:3`, `3:4`.
- References: up to 30 images, 10 videos, and 10 audios. Use only needed assets.
- A prompt is required. Optional references use `image_urls`, `video_urls`, and `audio_urls`.
- **Omit `mode`**: this model does not support that field. Do not send `quality`, `fast`, or `mini`.
- **Omit `first_frame_url` and `last_frame_url`**: those fields belong to the Veo path in this unified tool. Describe an image's role in the prompt; do not promise a hard first-frame lock from `image_urls` alone.
- Do not invent `fps`, `seed`, `negative_prompt`, `camera_lock`, `cut_times`, or `generate_audio` parameters. Put directing instructions, exclusions, and audio direction inside `prompt`.

“AAA,” “Unreal Engine 5,” “60fps feel,” and “photographic” are visual/motion targets, not proof of a renderer, delivered frame rate, or live-action capture. Return the actual requested resolution instead of calling the result 4K/8K.

### References

1. Inspect supplied media when supported and bind each asset to a named role. Do not claim visual inspection when only a filename or user description is available.
2. Pass a stable public HTTPS **media asset** URL directly. A social post, task page, fake `@Image1` link, or local filesystem path is not a usable remote media URL.
3. For a local file, use `upload_asset` and follow its returned upload procedure. A presigned upload request is not a completed upload: transfer the actual file and confirm success before using the returned asset URL. If the tool opens an upload panel, continue when the user's upload supplies the completed asset.
4. Preserve valid platform-provided reference tokens and array order. If no binding syntax is exposed, explain roles by the ordered attached images in plain language; do not invent API token syntax.
5. Text-only generation needs no upload or compulsory still-image task. Create additional reference images only when requested or included in an authorized production plan.

### Duration and editing constraints

`seedance2` in the checked schema supports 4–15 integer seconds, not 30. If the user explicitly chooses it, honor that choice: offer a shorter sequence or a disclosed multi-clip plan when cuts are allowed. Never submit `seedance2` with `duration: 30` and never silently relabel joined clips as one continuous shot.

For work longer than the chosen model supports, plan separate clips only if the brief allows cuts. Each clip needs its own reachable start/end state and local timestamps. Continue from observed accepted footage, not an imagined last frame. Confirm changed production scope when it adds unapproved generations. A one-take requirement cannot be satisfied merely by concatenating separate generations.

`create_compose_task` accepts two or more completed stable HTTPS video URLs in playback order via `video_urls`. It concatenates existing clips; it has no separate audio, music, voiceover, transition, overlay, trimming, or exact-cut controls. Do not use it as if it could fix HUD typography or create the office's exact 27+3 shot structure.

When exact timing/text is required, use an actually available editing workflow to measure, trim, and composite. If none is available, deliver the generation prompt plus a clearly labelled finishing plan. The generated cut timing and text remain unverified until the output is inspected. A finishing pass cannot repair hidden cuts inside a required continuous section without replacing or regenerating that footage.

### Submit and report

An explicit generation request authorizes the described generation within its scope. A prompt-only request does not. Do not demand another approval just because this section mentions generation; do ask about a real unresolved constraint, added paid variants, or a materially different production plan.

After submission, record the returned task ID, model, settings, and status. A pending task is not a completed video. Let the interactive client track newly created tasks automatically. Do not poll them with `get_task`; that operation is reserved for an explicit user request to check an existing task. When completed assets become available, continue authorized dependent work using actual asset URLs. Do not fabricate results or use pending IDs as input media.

If output can be inspected, check cut count, shot positions, duration, character/prop continuity, HUD placement, and dialogue. Report unverified properties honestly. If the task fails, report its specific error and propose the smallest correction. Do not automatically resubmit or generate variants without an existing retry authorization; after an uncertain submission, establish the first task's status before risking a duplicate paid task.
