# Claude Code Team Plugin Marketplace (Template)

A forkable template for engineering teams to create their own [Claude Code](https://claude.com/code) plugin marketplace. Fork this repo, customize the placeholders, and give your team shared engineering standards, onboarding tools, and automated workflows.

## Quick Start

1. **Fork this repo** (or click "Use this template" on GitHub)
2. **Rename the marketplace** in `.claude-plugin/marketplace.json` — change `"name"` to match your GitHub repo (e.g., `"my-org-claude-plugins"`)
3. **Customize the plugin** — replace `{YOUR_*}` placeholders in `team1-plugin/` (see [Customization Guide](#customization-guide))
4. **Add the marketplace** in Claude Code:
   ```
   /plugin marketplace add your-org/your-repo-name
   ```
5. **Install the plugin**:
   ```
   /plugin install team1-plugin@your-marketplace-name
   ```

## What's Included

### team1-plugin

| Component | Description |
|-----------|-------------|
| **CLAUDE.md** + SessionStart hook | Engineering standards auto-loaded every session |
| `/team1-plugin:setup-dependencies` | Check and install required dev tools (onboarding) |
| `/team1-plugin:create-pr-flow [title]` | Run checks, commit, push, and create a PR |

See [`team1-plugin/README.md`](team1-plugin/README.md) for details.

## Repository Structure

```
.
├── .claude-plugin/
│   └── marketplace.json          # Marketplace manifest (rename "name" to your repo)
├── team1-plugin/                 # Your first plugin
│   ├── .claude-plugin/
│   │   └── plugin.json           # Plugin manifest
│   ├── hooks/
│   │   └── hooks.json            # SessionStart hook → loads CLAUDE.md
│   ├── skills/
│   │   ├── setup-dependencies/
│   │   │   └── SKILL.md          # Onboarding dependency checker
│   │   └── create-pr-flow/
│   │       └── SKILL.md          # PR workflow automation
│   ├── CLAUDE.md                 # Engineering standards (customize this!)
│   ├── README.md
│   └── EXAMPLES.md
└── README.md                     # This file
```

## Customization Guide

### 1. Marketplace name
Edit `.claude-plugin/marketplace.json`:
- `"name"` — must match your GitHub repo name (used in install commands)
- `"owner"` — your team or org name

### 2. Plugin identity
Edit `team1-plugin/.claude-plugin/plugin.json`:
- `"name"` — rename if you want a different plugin name
- `"author"` — your team name

### 3. Engineering standards
Edit `team1-plugin/CLAUDE.md` — replace all `{YOUR_*}` placeholders:
- `{YOUR_TEAM}`, `{YOUR_COMPANY}` — team and company name
- `{YOUR_LANGUAGE}` — preferred language
- `{YOUR_LINT_COMMAND}`, `{YOUR_BUILD_COMMAND}`, `{YOUR_TEST_COMMAND}`, `{YOUR_FORMAT_COMMAND}` — your actual CLI commands
- `{YOUR_PATTERN}`, `{YOUR_PACKAGE_NOTES}` — branch naming and conventions

### 4. Setup dependencies
Edit `team1-plugin/skills/setup-dependencies/SKILL.md`:
- Replace `{YOUR_TOOL}`, `{YOUR_PLUGIN}`, `{YOUR_MCP}` with your team's actual dependencies
- Add or remove checks as needed

### 5. PR flow
Edit `team1-plugin/skills/create-pr-flow/SKILL.md`:
- Replace `{YOUR_*_COMMAND}` placeholders (must match your CLAUDE.md)
- Replace `{YOUR_TICKET_PREFIX}` with your ticket system prefix

## Adding More Plugins

1. Create a new directory: `my-second-plugin/`
2. Add `.claude-plugin/plugin.json` inside it
3. Add skills, hooks, or agents as needed
4. Register it in `.claude-plugin/marketplace.json`:
   ```json
   {
     "name": "my-second-plugin",
     "source": "./my-second-plugin",
     "description": "What this plugin does"
   }
   ```

## Testing Locally

Test your plugin without installing:
```bash
claude --plugin-dir ./team1-plugin
```

Validate the marketplace:
```bash
claude plugin validate .
```

## Resources

- [Create plugins](https://code.claude.com/docs/en/plugins) — Anthropic's plugin authoring guide
- [Plugin marketplaces](https://code.claude.com/docs/en/plugin-marketplaces) — Marketplace creation and distribution
- [Skills reference](https://code.claude.com/docs/en/skills) — SKILL.md format and frontmatter
- [Plugins reference](https://code.claude.com/docs/en/plugins-reference) — Complete technical specifications
