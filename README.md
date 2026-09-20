# SJinn Professional Skills

A collection of AI video and image generation skills for [SJinn](https://sjinn.ai), designed for use with Claude Code.

Each skill is a structured prompt engineering system that guides Claude through gathering requirements, crafting optimized prompts, and generating assets via the SJinn MCP server.

## Skills

### UGC Video (`skills/marketing/ugc-video/`)

Generates authentic UGC-style (user-generated content) product review and testimonial video prompts optimized for Seedance 2.0.

- 9-layer prompt architecture (format, person, setting, product, script beats, tone, edit style, technical flaws, vibe)
- Automatic dialogue-to-duration mapping (4–15s)
- Product image references via `@(img1)` tokens
- Built-in authenticity signals: skin texture, technical flaws, lived-in environments

**Trigger:** "ugc-video", "UGC ad", "selfie-style video", "product review video", "testimonial video"

### Product Hero (`skills/marketing/product-hero/`)

Generates dramatic, person-free product showcase videos where the product is the sole star — moody lighting, elemental interaction, and escalating shot sequences.

- 6-layer prompt architecture (format, product, environment, shot sequence, text overlays, technical quality)
- Element bank by product type (beverage, supplement, skincare, tech, food)
- 3 shot sequence frameworks (escalating drama, reveal build, pure spectacle)
- Reflective surfaces, deep-colored backdrops, slow-motion elemental effects

**Trigger:** "product-hero", "product showcase", "product commercial", "hero shot video", "dramatic product video", "beverage commercial"

### Realistic Image (`skills/realistic/realistic-image/`)

Generates photorealistic images in "Raw Camera Casting Realism" style — unretouched, physically present, believable camera-file aesthetics for people, products, animals, and materials.

- Complete prompt expansion from short text, detailed text, reference image, or mixed input
- Realism stack: skin microstructure, vellus hair, pores, asymmetry, fabric weave, dust, scratches
- Anti-slop rules: no beauty-render polish, no generic quality boosters, no CGI smoothness
- Supports human portraits, animals, products, plants, architecture, and abstract subjects

**Trigger:** "realistic-image", "realistic photo", "raw photo", "casting photo", "unretouched portrait", "camera-style photo"

### Influencer Image Clone (`skills/influencer/influencer-image-clone/`)

Recreates the adult subject in one or more reference photos as a new photorealistic still image while preserving visible facial geometry, hair, skin details, and identity-defining features.

- Separates stable identity anchors from changeable pose, outfit, setting, and lighting
- Uses the reference image directly with SJinn Nano Banana Pro for stronger continuity
- Includes prompt approval, identity-drift checks, and still-image artifact QA
- Image-only workflow with no video generation or animation steps

**Trigger:** "influencer-image-clone", "clone this influencer photo", "recreate this person", "same person in a new setting", "match this creator"

### Mini Rescue (`skills/viral-video/mini-rescue/`)

Generates cinematic "giant hand saves the day" miniature-world rescue scenes — both image and video.

- Full image-to-video pipeline: generate still frame, then animate it
- 5-sentence video prompt structure with static camera
- Stylized 3D CGI figurines + real human hand rescue mechanic

**Trigger:** "mini-rescue", "miniature rescue", "tiny people rescue", "giant hand rescue"

### Object Talk (`skills/viral-video/object-talk/`)

Creates one expressive talking-object clip per object, then concatenates the ordered clips with SJinn MCP.

- Defaults to strawberry, cucumber, and tomato when no object or theme is supplied
- Creates Pixar-style 3D first frames with `nano-banana-2`
- Generates adaptive 4–15 second monologues with Seedance 2 Mini and native audio
- Composes the completed clips in order with SJinn `create_compose_task`
- Supports explicit object lists, themed three-object sets, and custom aspect ratios

**Trigger:** "object-talk", "Object Talk", "talking objects", "object rant", "talking food video"

### Veo3 Story Video (`skills/viral-video/veo3-story-video/`)

Creates one complete story or vlog video with consistent characters and locations.

- Creates or reuses a separate three-view reference for every character
- Generates a panoramic reference for every location and numbered-reference storyboard frames with `nano-banana-2`
- Plans 8-second scenes and animates each completed first frame with `veo3.1-fast`
- Defaults to 16:9 and approximately 30 seconds (four scenes, approximately 32 seconds)
- Uses native Veo audio with external TTS and LipSync disabled by default
- Concatenates completed clips in storyboard order with SJinn MCP `create_compose_task`, preserving their audio

**Trigger:** "veo3-story-video", "veo3 story video", "Veo story generation", "故事视频", "连续剧情短片"

### Behind the Scenes (`skills/viral-video/behind-the-scenes/`)

Creates amateur phone-footage-style miniature disaster shoots inside an enormous practical-FX soundstage.

- Converts real places and uploaded skylines into original, IP-safe miniature architecture
- Locks the same in-floor tank, colossal blue screen, orange tracking crosses, crew, hardware, and practical disaster across image and video
- Includes 11 physical disaster families with exact FX setups and prompt tags
- Generates one `9:16` still with GPT-Image-2, then an `8s` image-to-video clip with Seedance 2 Mini

**Trigger:** "behind-the-scenes", "miniature disaster set", "practical-FX city destruction", "BTS miniature shoot"

### Flying Dragon (`skills/viral-video/flying-dragon/`)

Generates hyper-photorealistic first-person dragon-riding scenes with a rider-locked POV, visible hands and harness, and a centered dragon spine.

- Full image-to-video pipeline with a generated POV start frame
- Aggressive banking, dives, climbs, acceleration, and physical momentum
- Environmental interaction and immersive diegetic sound

**Trigger:** "flying-dragon", "POV dragon ride", "dragon flight", "first-person dragon-riding video"

### GTA Style Video (`skills/viral-video/gta-style-video/`)

Turns a scenario into third-person gameplay with a clear mission, physical player actions, persistent character/world state, and a fixed HUD; generates with SJinn when requested.

- Three camera/edit modes: continuous mission, a single-cut comic payoff, and open-world exploration montage
- Separate controls for rendering style, spoken language, HUD language, and environmental signage
- Reusable office-stealth, survival-rescue, sunken-ruins, and winter-mystery recipes, including a complete office prompt
- Checks action density, traversable routes, cover geometry, cast continuity, and HUD changes before generation
- Defaults to one 30-second, 16:9, 720p `seedance2.5` task; prompt-only requests do not submit generation tasks

**Trigger:** "gta-style-video", "GTA style video", "GTA风格视频", "游戏实机感短片", "第三人称任务视频"

### Sticker Cooking Comedy (`skills/viral-video/sticker-cooking-comedy/`)

Creates funny short videos that composite a photorealistic live-action cooking kitchen with a flat chibi 2D anime sticker IP character.

- Uses an uploaded 2D chibi sticker directly without redrawing it
- Converts photographic, realistic, 3D, or non-chibi character images with `gpt-image-2`
- Pauses after conversion and requires the user to approve the sticker image before video generation
- Supports text-only IP descriptions when no character image is supplied
- Locks character identity, hairstyle, clothing, accessories, visible text, and flat sticker texture throughout
- Uses a 10-second four-beat gag: prank, harmless reaction, cartoon escalation, freeze-frame payoff
- Generates the final live-action/2D composite with `seedance2`

**Trigger:** "sticker-cooking-comedy", "真人厨房×2D动漫贴纸", "Q版IP炒菜", "厨房贴纸搞笑视频", "倒盐恶作剧"

## Setup

### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed
- SJinn account with API access

### SJinn MCP Server

The project connects to SJinn via MCP (already configured in `.mcp.json`):

```json
{
  "mcpServers": {
    "sjinn": {
      "type": "streamable-http",
      "url": "https://mcp.sjinn.ai/mcp"
    }
  }
}
```

For detailed installation guides, see:
- MCP setup: https://sjinn.ai/docs/mcp
- Basic Skills setup: https://sjinn.ai/docs/skills

### Usage

Open Claude Code in the project directory and use a trigger phrase:

```
> ugc-video
> product-hero
> influencer-image-clone
> mini-rescue
> object-talk
> veo3-story-video
> behind-the-scenes
> flying-dragon
> gta-style-video
> sticker-cooking-comedy
```

Claude will guide you through the input gathering and generation workflow.

## Project Structure

```
skills/
├── marketing/
│   ├── product-hero/
│   │   └── SKILL.md        # Product hero prompt system
│   └── ugc-video/
│       └── SKILL.md        # UGC video prompt system
├── influencer/
│   └── influencer-image-clone/
│       ├── agents/
│       │   └── openai.yaml # Codex UI metadata
│       └── SKILL.md        # Reference-based identity recreation
├── realistic/
│   └── realistic-image/
│       └── SKILL.md        # Raw Camera Casting Realism prompt system
└── viral-video/
    ├── behind-the-scenes/
    │   ├── agents/
    │   │   └── openai.yaml # Codex UI metadata and SJinn dependency
    │   ├── references/
    │   │   └── set-piece-studio-style-bible.md
    │   └── SKILL.md        # Miniature practical-FX disaster workflow
    ├── flying-dragon/
    │   ├── agents/
    │   │   └── openai.yaml # Codex UI metadata
    │   └── SKILL.md        # First-person dragon ride prompt system
    ├── gta-style-video/
    │   ├── agents/
    │   │   └── openai.yaml # Codex UI metadata and SJinn dependency
    │   └── SKILL.md        # Complete workflow, prompt template, recipes, and SJinn generation
    ├── mini-rescue/
    │   └── SKILL.md        # Mini rescue prompt system
    ├── object-talk/
    │   ├── agents/
    │   │   └── openai.yaml # Codex UI metadata and SJinn dependency
    │   └── SKILL.md        # Talking-object generation and SJinn composition workflow
    ├── veo3-story-video/
    │   ├── agents/
    │   │   └── openai.yaml # Codex UI metadata and SJinn dependency
    │   └── SKILL.md        # Story workflow, model arguments, and SJinn composition
    └── sticker-cooking-comedy/
        └── SKILL.md        # Live-action kitchen × 2D sticker comedy
```

## Models Used

| Skill | Model | Output |
|-------|-------|--------|
| UGC Video | `seedance2` | 4–15s vertical video |
| Product Hero | `seedance2` | 15s, 9:16, quality mode |
| Realistic Image | `nano-banana-pro` | 1:1, 2K still image |
| Influencer Image Clone | `nano-banana-pro` | Reference-guided 2K still image |
| Mini Rescue (image) | `nano-banana-2` | 9:16, 2K still frame |
| Mini Rescue (video) | `seedance2` | 10s, 9:16, quality mode |
| Object Talk (image) | `nano-banana-2` | One 9:16, 2K still per object |
| Object Talk (video) | `seedance2` (`mini` mode) | One adaptive 4–15s, 9:16, 720p clip per object; SJinn ordered composition |
| Veo3 Story Video (image) | `nano-banana-2` | Character sheets, location panoramas, and 2K scene first frames |
| Veo3 Story Video (video) | `veo3.1-fast` | Planned 8s scenes, 16:9 by default, with SJinn ordered composition |
| Behind the Scenes (image) | `gpt-image-2` | 9:16 miniature practical-FX still |
| Behind the Scenes (video) | `seedance2` (`mini` mode) | 8s, 9:16, 720p image-to-video clip |
| Flying Dragon (image) | `nano-banana-pro` | 9:16, 2K still frame |
| Flying Dragon (video) | `seedance2` | 10s, 9:16, quality mode |
| GTA Style Video | `seedance2.5` | 30s, 16:9, 720p third-person gameplay by default |
| Sticker Cooking Comedy (conversion, when needed) | `gpt-image-2` | 1:1 chibi 2D sticker reference, user-approved |
| Sticker Cooking Comedy (video) | `seedance2` | 10s, 9:16, 720p, quality mode |

## Adding New Skills

1. Create a directory under `skills/<category>/<skill-name>/`
2. Write a `SKILL.md` with trigger, instructions, prompt architecture, and generation workflow
3. Optionally add a Claude Code skill file in `.claude/skills/` for direct trigger support

## License

Private — all rights reserved.
