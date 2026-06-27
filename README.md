# qa-kit

A Claude Code plugin that adds code-quality tooling to your workflow.

## What it does

**Commands**

- `/qa-kit:summarize-changes` — Summarises every file touched on the current branch with a one-line description of what changed. Produces output short enough to paste directly into a pull-request description.

**Subagents**

- `code-reviewer` — Reviews recent code changes for bugs, missing error handling, and unclear names. Returns findings grouped by severity (high / medium / low), one sentence per item.

## Usage

Load the plugin from the repo root:

```
claude --plugin-dir .
```

Run the summarise command by its namespaced name:

```
/qa-kit:summarize-changes
```

Trigger the code reviewer by asking Claude naturally:

```
Review my recent changes.
```

After editing any plugin file, reload without restarting:

```
/reload-plugins
```

## Structure

```
.
├── .claude-plugin/
│   └── plugin.json        # manifest: name + version
├── commands/
│   └── summarize-changes.md
├── agents/
│   └── code-reviewer.md
└── README.md
```
