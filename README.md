# Mosaic Plugins

Official plugins for [Mosaic](https://edit.mosaic.so) — AI-powered video editing.

## Install

### Claude Code

```bash
claude plugin marketplace add usemosaic/mosaic-plugins
claude plugin install mosaic-video-editor@mosaic-plugins
```

### OpenClaw

Install from ClawHub:

```bash
openclaw skills install mosaic-video-editor
```

Or install as a plugin bundle:

```bash
openclaw plugins install mosaic-video-editor --marketplace usemosaic/mosaic-plugins
```

Then restart the gateway:

```bash
openclaw gateway restart
```

## API key

You need a Mosaic API key (prefixed `mk_`) to use this plugin. Get one at [edit.mosaic.so](https://edit.mosaic.so).

**OpenClaw:**

```bash
openclaw config set env.vars.MOSAIC_API_KEY "mk_your_key_here"
```

**Claude Code:**

The skill will ask for your API key on first use, or you can set it in `~/.claude/settings.json`:

```json
{
  "env": {
    "MOSAIC_API_KEY": "mk_your_key_here"
  }
}
```

## What you can do

- Create and manage video editing agents
- Run automated video workflows (clips, captions, motion graphics, reframe, etc.)
- Upload video/audio/image assets
- Publish to YouTube, TikTok, Instagram, and more
- Manage credits and billing

## Publishing to ClawHub

```bash
npm i -g clawhub
clawhub login
clawhub publish ./skills/mosaic-video-editor --slug mosaic-video-editor --name "Mosaic Video Editor" --version 1.2.0 --tags latest
```
