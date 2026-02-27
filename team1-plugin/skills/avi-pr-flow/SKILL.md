---
description: Automate PR workflow with commit, push, create PR, and review cycle
argument-hint: "[optional PR title]"
disable-model-invocation: true
allowed-tools:
  - Bash(git *)
  - Bash(gh *)
---

You are helping me with a complete PR workflow. Follow these steps:

## 1. Check Branch Safety
- Get current branch
- If "main" or "master", STOP with error

## 2. Review Code
- Run `/pr-review-toolkit:review-pr`
- Fix any suggestions before committing

## 3. Commit and Push
- Stage all changes
- Generate meaningful commit message from staged diff
- Commit and push to remote

## 4. Create or Find PR
- Check if PR exists for current branch
- If no PR:
  - Extract ticket from branch name (e.g., ME-12345)
  - Use $ARGUMENTS as title if provided, otherwise generate: `<ticket>: <summary>`
  - Generate PR body with summary and key modifications
  - Create PR and extract PR number

## 5. Request Bugbot Review
- Comment "bugbot review"
- Poll for bugbot/cursor response (60s intervals, max 5 attempts)
- If timeout, report to me

## 6. Handle Bugbot Feedback
- Fetch and display all review comments
- If no issues → skip to CircleCI check
- If issues found:
  - Ask me to fix and wait for confirmation
  - After confirmation: commit, push
  - Reply "Fixed! ✅" to all comment IDs
  - Request bugbot review again (poll 60s, max 5 attempts)

## 7. Check CircleCI
- Check pipeline status using CircleCI MCP (current repo + branch)
- If running: poll 60s, max 15 attempts (display "waiting...")
- If failed: show logs, ask for fixes, commit/push after confirmation, re-check
- If success: report "CI passed ✅"

## 8. Show Final Status
- Display PR state and reviews

## Notes
- Stop on any command failure and report error
- Keep me informed at each step
