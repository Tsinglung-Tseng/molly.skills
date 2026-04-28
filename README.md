# molly.skills

A Claude Code Plugin Marketplace — Obsidian automation skills + macOS productivity CLIs for daily knowledge work.

## Install

```bash
/plugin marketplace add tsinglungtseng/molly.skills
```

## Plugins

| Plugin | Description |
|--------|-------------|
| [obs-note](plugins/obs-note/) | Turn conversations into structured Obsidian notes with automatic bidirectional linking |
| [apple-cli](plugins/apple-cli/) | Drive macOS Calendar / Reminders / Notifications via `osascript` — pure CLI, no MCP server |

## Usage

After installing the marketplace:

```bash
/plugin install obs-note@molly-skills
/plugin install apple-cli@molly-skills
```

Then invoke in Claude Code:

```
/obs-note
/apple-cli
```

## Configuration

Each skill has a `config.example.yaml`. Copy it to `config.yaml` in your local skill directory and fill in your paths:

```bash
cp ~/.claude/skills/obs-note/config.example.yaml ~/.claude/skills/obs-note/config.yaml
```

## License

MIT
