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

### Flying Dragon (`skills/viral-video/flying-dragon/`)

Generates hyper-photorealistic first-person dragon-riding scenes with a rider-locked POV, visible hands and harness, and a centered dragon spine.

- Full image-to-video pipeline with a generated POV start frame
- Aggressive banking, dives, climbs, acceleration, and physical momentum
- Environmental interaction and immersive diegetic sound

**Trigger:** "flying-dragon", "POV dragon ride", "dragon flight", "first-person dragon-riding video"

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
> flying-dragon
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
    ├── flying-dragon/
    │   ├── agents/
    │   │   └── openai.yaml # Codex UI metadata
    │   └── SKILL.md        # First-person dragon ride prompt system
    └── mini-rescue/
        └── SKILL.md        # Mini rescue prompt system
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
| Flying Dragon (image) | `nano-banana-pro` | 9:16, 2K still frame |
| Flying Dragon (video) | `seedance2` | 10s, 9:16, quality mode |

## Adding New Skills

1. Create a directory under `skills/<category>/<skill-name>/`
2. Write a `SKILL.md` with trigger, instructions, prompt architecture, and generation workflow
3. Optionally add a Claude Code skill file in `.claude/skills/` for direct trigger support

## License

Private — all rights reserved.
