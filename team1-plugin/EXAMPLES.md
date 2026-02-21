# Examples

## setup-dependencies

**Successful check:**
```
/team1-plugin:setup-dependencies

✓ Node.js v20.11.0
✓ npm 10.2.4
✓ git 2.43.0
✓ gh 2.42.0 (authenticated)
✓ your-plugin installed
✓ your-mcp configured
```

**Missing dependency:**
```
/team1-plugin:setup-dependencies

✓ Node.js v20.11.0
✓ npm 10.2.4
✓ git 2.43.0
✗ gh CLI not found
  Install: brew install gh && gh auth login
```

## create-pr-flow

**Typical workflow:**
```
/team1-plugin:create-pr-flow

Step 1: Checking branch...
✓ On branch PROJ-123-add-validation

Step 2: Running Definition of Done...
✓ Lint passed
✓ Build passed
✓ Tests passed
✓ Formatter passed

Step 3: Committing and pushing...
✓ Committed: "PROJ-123: Add input validation"
✓ Pushed to origin

Step 4: Creating PR...
✓ PR #42 created: https://github.com/your-org/your-repo/pull/42

Step 5: Checking CI...
✓ Pipeline passed
```

**Error - on main branch:**
```
/team1-plugin:create-pr-flow

⛔ STOP: You're on main branch.
Create a feature branch first: git checkout -b PROJ-XXX-description
```
