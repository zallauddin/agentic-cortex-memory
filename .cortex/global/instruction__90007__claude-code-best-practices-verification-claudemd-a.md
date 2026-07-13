---
id: 90007
type: instruction
title: "Claude Code Best Practices: Verification, CLAUDE.md, and Parallelism"
confidence: 95
importance: 10
provenance: community
source_url: "https://support.claude.com/en/articles/14554000-claude-code-power-user-tips"
created_at: "2026-07-13"
tags: ["community", "source:anthropic", "claude-code", "verification"]
synced_at: "2026-07-13T05:12:29.920Z"
---

# Claude Code Power-User Best Practices

## Verification Is Primary
- If you adopt only ONE practice, make it verification
- Ensure the agent can close the feedback loop (run tests, check output, use a browser)
- Never declare a task complete without verifying the result

## Compounding Engineering with CLAUDE.md
- Maintain a shared `CLAUDE.md` (or `AGENTS.md` or `AGENT.md`) in your repository root
- Every time the agent makes a mistake, explicitly tell it to update the file
- This creates a compounding learning effect — the agent gets smarter with every mistake
- **Format**: project purpose, canonical patterns, do/don't constraints, build/test commands

## Plan Mode for Complex Tasks
- For multi-file, multi-step changes, use Plan Mode first
- Iterate on the approach before letting the agent execute
- This prevents wasted compute on wrong paths

## Parallelization for Scale
- Run 3–5 parallel agent sessions in separate git worktrees
- This is the primary productivity unlock for large changes
- Use subagents for focused tasks (security check, code simplification)

## Safety via Pre-approvals
- Use `/permissions` to pre-approve known safe commands
- Check permission settings into your repository
- This reduces friction without compromising safety
