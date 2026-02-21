---
description: Check required development dependencies for the team
disable-model-invocation: true
---

Check all required dependencies for this team's development environment:

1. **Check Node.js**: Run `which node` and `node --version` - minimum version: {YOUR_MIN_VERSION}
2. **Check npm**: Run `which npm`
3. **Check git**: Run `which git`
4. **Check gh CLI**: Run `which gh` - if not found, suggest `brew install gh && gh auth login`
   - If found, verify auth: `gh auth status`
5. {YOUR_TOOL}: Run `which {tool}` - fail if not found
6. {YOUR_PLUGIN}: Run `grep "{plugin-name}@{marketplace}" ~/.claude/settings.json` - warn if not found
7. {YOUR_MCP}: Use ToolSearch with query "{mcp-name}" - fail if no tools found

Report status for each check. If any required checks fail, provide install commands.
