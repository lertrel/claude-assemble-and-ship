## Build your first plugin
 
This is your workspace for the **Unit 9, Lesson 3** task: assemble a couple of components into a working Claude Code plugin and test it locally.
 
### What's in here
 
Two ready-made components live in `building-blocks/`:
 
- `summarize-changes.md` — a slash command that summarises what changed on a branch
- `code-reviewer.md` — a subagent that reviews recent changes
Your job is to organise them into a proper plugin. (Made your own command or subagent earlier in the course? Use those instead — the steps are the same.)
 
### Target structure
 
```
.
├── .claude-plugin/
│   └── plugin.json            # name + version (the manifest)
├── commands/
│   └── summarize-changes.md
├── agents/
│   └── code-reviewer.md
└── README.md                  # what your plugin does
```
 
Remember the one rule that trips people up: **only `plugin.json` goes inside `.claude-plugin/`** — the component folders sit at the root.
 
### Steps
 
1. Create `.claude-plugin/plugin.json` with a `name` and a `version`.
2. Make the component folders and move the pieces into place: `building-blocks/summarize-changes.md` → `commands/`, and `building-blocks/code-reviewer.md` → `agents/`. Delete the empty `building-blocks/` folder afterwards.
3. If a component runs a bundled script, reference it through `${CLAUDE_PLUGIN_ROOT}` — never a hardcoded path.
4. Replace this README with one that describes *your* plugin: what it does, the commands it adds, how to use them.
5. From the repo root, load it with `claude --plugin-dir .`. Run the command as `/your-plugin:summarize-changes`, and trigger the subagent by asking Claude to review your recent changes (it should reach for `code-reviewer`). Use `/reload-plugins` after edits.
6. Commit and push.
### Done when
 
- `claude --plugin-dir .` loads the plugin, the command runs by its namespaced name, and the reviewer subagent fires when you ask for a review.
- The repo holds a valid `.claude-plugin/plugin.json`, the `commands/` and `agents/` folders, and a README describing the plugin.
