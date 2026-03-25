# Mosaic Video Editor

Official plugin for [Mosaic](https://edit.mosaic.so) — AI-powered video editing from your terminal.

Create and run video editing agents, upload media, add captions, motion graphics, clips, voice dubbing, and publish to YouTube, TikTok, Instagram, and more.

## Quick start

The fastest way to get set up is the one-click install at [edit.mosaic.so](https://edit.mosaic.so). It generates your API key and gives you a single command to copy and paste.

## Manual install

### Claude Code

```bash
# Add the marketplace and install the plugin
claude plugin marketplace add mosaic-ai-labs/skills
claude plugin install mosaic-video-editor@mosaic-skills
```

Then set your API key in `~/.claude/settings.json` so it's available in every session:

```json
{
  "env": {
    "MOSAIC_API_KEY": "mk_your_key_here"
  }
}
```

Get an API key at [edit.mosaic.so](https://edit.mosaic.so) under Automations > API.

### OpenClaw

```bash
# Install from ClawHub
openclaw skills install mosaic-video-editor

# Set your API key
openclaw config set env.vars.MOSAIC_API_KEY "mk_your_key_here"

# Restart the gateway
openclaw gateway restart
```

Get an API key at [edit.mosaic.so](https://edit.mosaic.so) under Automations > API.

## What you can do

- **Clips** — cut short-form clips from long videos
- **Captions & Cinematic Captions** — auto-generated subtitles with styling
- **Motion Graphics** — animated overlays, callouts, kinetic text
- **Voice Translation** — AI dubbing in 30+ languages
- **Reframe** — resize for any platform (9:16, 1:1, 16:9)
- **AI B-Roll, Music, Voiceover** — generate supplementary media
- **Social Publishing** — post to YouTube, TikTok, Instagram, LinkedIn
- **Credits & Billing** — check balance, configure auto top-ups

## API reference

Full endpoint docs: [docs.mosaic.so/api](https://docs.mosaic.so/api/introduction)
