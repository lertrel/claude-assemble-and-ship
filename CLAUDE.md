# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This repo is a Claude Code plugin (qa-kit) assembled from pre-made components. The plugin adds a summarize-changes command and a code-reviewer subagent.

## Validation

Run the validation script locally to check the plugin structure:

```bash
node .github/scripts/validate-plugin.js
```

The CI workflow (`.github/workflows/validate.yml`) runs this same script on every push and PR.

## Required Plugin Structure

```
.
├── .claude-plugin/
│   └── plugin.json          # Only the manifest goes here
├── commands/
│   └── summarize-changes.md
├── agents/
│   └── code-reviewer.md
└── README.md
```

The manifest must be valid JSON with a non-empty `name` field:
```json
{ "name": "qa-kit", "version": "0.1.0" }
```

Component folders (`commands/`, `agents/`, `skills/`, `hooks/`) must be at the **repo root**, not inside `.claude-plugin/`.

## Architecture

- **`.claude-plugin/plugin.json`** — declares plugin identity; no component files go here
- **`commands/`** — slash commands as markdown files; invoked as `/plugin-name:command-name`
- **`agents/`** — subagent definitions as markdown files with YAML frontmatter specifying model and tools
- **`.github/scripts/validate-plugin.js`** — Node.js script that validates the plugin structure; checks for manifest existence, valid JSON, non-empty name, and at least one populated component directory
