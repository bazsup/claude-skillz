# claude-skillz

A custom Claude Code skill marketplace. Add it once, install any skill on demand.

## For users

### Setup (one time)

```
/plugin marketplace add bazsup/claude-skillz
```

### Available skills

| Skill | Description |
|-------|-------------|
| `tactical-ddd` | Design, refactor, and review code using tactical domain-driven design principles |

### Install a skill

```
/plugin install tactical-ddd@claude-skillz
```

### Uninstall a skill

```
/plugin uninstall tactical-ddd@claude-skillz
```

---

## For contributors

### Adding a new skill

1. **Create the plugin directory structure:**

   ```
   plugins/
   └── your-skill-name/
       ├── .claude-plugin/
       │   └── plugin.json
       └── skills/
           └── your-skill-name.md
   ```

2. **Write `.claude-plugin/plugin.json`:**

   ```json
   {
     "name": "your-skill-name",
     "version": "1.0.0",
     "description": "One-line description of what the skill does",
     "author": {
       "name": "bazsup"
     },
     "repository": "https://github.com/bazsup/claude-skillz",
     "license": "MIT",
     "keywords": ["relevant", "tags"]
   }
   ```

3. **Write `skills/your-skill-name.md`** with YAML frontmatter:

   ```markdown
   ---
   name: your-skill-name
   description: "One-line description. Triggers on: keyword1, keyword2, ..."
   version: 1.0.0
   ---

   # Your Skill Title

   Skill content here...
   ```

4. **Register it in `.claude-plugin/marketplace.json`** — add an entry to the `plugins` array:

   ```json
   {
     "name": "your-skill-name",
     "description": "One-line description of what the skill does",
     "category": "development",
     "source": "./plugins/your-skill-name",
     "homepage": "https://github.com/bazsup/claude-skillz"
   }
   ```

5. **For local development**, also copy the skill to `.claude/skills/your-skill-name.md`.

6. **Push to GitHub** — no publishing step needed. The skill is immediately available via the marketplace.

### Repository structure

```
claude-skillz/
├── .claude-plugin/
│   └── marketplace.json        ← marketplace registry
└── plugins/
    └── tactical-ddd/           ← one directory per skill
        ├── .claude-plugin/
        │   └── plugin.json
        └── skills/
            └── tactical-ddd.md
```
