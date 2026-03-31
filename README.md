# molly.skills

A Claude Code Plugin Marketplace — Obsidian automation skills for daily knowledge work.

## Install

```bash
/plugin marketplace add tsinglungtseng/molly.skills
```

## Skills

| Skill | Description |
|-------|-------------|
| [obs-note](skills/obs-note/) | Turn conversations into structured Obsidian notes with automatic bidirectional linking |

## Usage

After installing the marketplace:

```bash
/plugin install obs-note@molly-skills
```

Then invoke in Claude Code:

```
/obs-note
```

## Configuration

Each skill has a `config.example.yaml`. Copy it to `config.yaml` in your local skill directory and fill in your paths:

```bash
cp ~/.claude/skills/obs-note/config.example.yaml ~/.claude/skills/obs-note/config.yaml
```

## License

MIT
