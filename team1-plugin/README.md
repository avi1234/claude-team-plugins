# team1-plugin

Plugin for {YOUR_TEAM} engineers at {YOUR_COMPANY}.

## What it provides

- **CLAUDE.md** - Engineering standards loaded automatically at session start
- **Skills:**
  - `/team1-plugin:setup-dependencies` - Verify required dependencies
  - `/team1-plugin:create-pr-flow` - Automate PR workflow (commit, push, create PR, CI check)

## Prerequisites

- **gh CLI** - `brew install gh`
- {YOUR_PREREQUISITES}

Run `/team1-plugin:setup-dependencies` to verify.

## Installation

```bash
/plugin install team1-plugin@claude-team-plugins
```

## Troubleshooting

**Session hook not loading:**
- Restart Claude Code session
- Verify plugin is installed: `/plugin`

**setup-dependencies fails:**
- Ensure gh CLI is installed and authenticated

**create-pr-flow errors:**
- Must be on a feature branch (not main/master)
- Ensure all prerequisites are installed
