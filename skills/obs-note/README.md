# obs-note

A Claude Code skill that turns conversations into well-structured Obsidian notes.

## Features

- Structured file naming: `[Category]_[Topic]_[Details].md`
- Correct Obsidian frontmatter with comprehensive metadata
- Mermaid diagram support with proper escaping
- Two-round self-check (Gleaning) for content completeness and format compliance
- PageIndex MCP integration for automatic bidirectional note linking
- Extensible note types (location, people) loaded on demand

## Installation

Copy the `obs-note/` directory into your Claude Code skills folder:

```bash
cp -r obs-note ~/.claude/skills/obs-note
```

## Configuration

1. Copy the example config:

```bash
cp config.example.yaml config.yaml
```

2. Edit `config.yaml` with your settings:

```yaml
vault_root: "/path/to/your/obsidian/vault"
lang: zh  # zh | en
```

## Usage

In Claude Code:

```
/obs-note
```

Then describe the content you want organized into a note.

## Note Types

The skill supports extensible note types via `types/` directory. Type-specific rules are loaded on demand only when needed:

| Type | Trigger | File |
|------|---------|------|
| Location | `type: location` / restaurant / attraction | `types/location.md` |
| People | `#type/people` / `#function/biography` | `types/people.md` |

To add a custom type, create a new `.md` file in `types/` and add a row to the type table in `SKILL.md`.

## Optional Dependencies

- **PageIndex MCP**: For automatic related-note discovery and bidirectional linking. The skill degrades gracefully if unavailable.
- **Amap Maps MCP**: For location notes — coordinate lookup and navigation links.

## License

MIT
