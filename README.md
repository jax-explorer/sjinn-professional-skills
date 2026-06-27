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

### Mini Rescue (`skills/viral-video/mini-rescue/`)

Generates cinematic "giant hand saves the day" miniature-world rescue scenes — both image and video.

- Full image-to-video pipeline: generate still frame, then animate it
- 5-sentence video prompt structure with static camera
- Stylized 3D CGI figurines + real human hand rescue mechanic

**Trigger:** "mini-rescue", "miniature rescue", "tiny people rescue", "giant hand rescue"

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
> mini-rescue
```

Claude will guide you through the input gathering and generation workflow.

## Project Structure

```
skills/
├── marketing/
│   └── ugc-video/
│       └── SKILL.md        # UGC video prompt system
└── viral-video/
    └── mini-rescue/
        └── SKILL.md        # Mini rescue prompt system
```

## Models Used

| Skill | Model | Output |
|-------|-------|--------|
| UGC Video | `seedance2` | 4–15s vertical video |
| Mini Rescue (image) | `nano-banana-2` | 9:16, 2K still frame |
| Mini Rescue (video) | `seedance2` | 10s, 9:16, quality mode |

## Adding New Skills

1. Create a directory under `skills/<category>/<skill-name>/`
2. Write a `SKILL.md` with trigger, instructions, prompt architecture, and generation workflow
3. Optionally add a Claude Code skill file in `.claude/skills/` for direct trigger support

## License

Private — all rights reserved.
