---
description: Automate PR workflow with commit, push, create PR, and CI check
argument-hint: "[optional PR title]"
disable-model-invocation: true
---

You are helping me with a complete PR workflow. Follow these steps:

## 1. Check Branch Safety
- Get current branch
- If "main" or "master", STOP with error

## 2. Run Definition of Done
1. `{YOUR_LINT_COMMAND}`
2. `{YOUR_BUILD_COMMAND}`
3. `{YOUR_TEST_COMMAND}`
4. `{YOUR_FORMAT_COMMAND}`

If any check fails, STOP and report the error. Do not proceed.

## 3. Commit and Push
- Stage all changes
- Generate meaningful commit message from staged diff
- Commit and push to remote

## 4. Create or Find PR
- Check if PR exists for current branch
- If no PR:
  - Extract ticket from branch name (e.g., {YOUR_TICKET_PREFIX}-12345)
  - Use $ARGUMENTS as title if provided, otherwise generate: `<ticket>: <summary>`
  - Generate PR body with summary and key modifications
  - Create PR and extract PR number

## 5. Check CI
- Check pipeline status for current repo + branch
- If running: poll 60s intervals, max 15 attempts (display "waiting...")
- If failed: show logs, ask for fixes, commit/push after confirmation, re-check
- If success: report "CI passed"

## 6. Show Final Status
- Display PR URL, state, and CI status

## Notes
- Stop on any command failure and report error
- Keep me informed at each step
