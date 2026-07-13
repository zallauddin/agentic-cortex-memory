---
id: 90014
type: pattern
title: "Agent Context Management: The Compounding Knowledge Pattern"
confidence: 95
importance: 10
provenance: community
source_url: "https://support.claude.com/en/articles/14554000-claude-code-power-user-tips"
created_at: "2026-07-13"
tags: ["community", "source:anthropic", "context", "knowledge-management"]
synced_at: "2026-07-13T05:12:29.922Z"
---

# Compounding Knowledge Pattern

## Concept
Treat your agent's context file (CLAUDE.md, AGENTS.md, .cursorrules) as a **living knowledge base** that compounds over time.

## Implementation
1. When the agent makes a mistake → add a rule preventing it
2. When a pattern succeeds → codify it as a preferred approach
3. When a gotcha is discovered → document it with the fix
4. When a convention is established → make it explicit

## Structure
```markdown
# Project Context
- What this project does
- Key technologies & versions
- Build/test commands

# Canonical Patterns
- How we handle [X]
- Our preferred approach for [Y]

# Constraints (DO NOT)
- Never use [banned pattern]
- Always check [gotcha]
```

## Why It Works
- Every session builds on all previous sessions
- Mistakes are never repeated (they're encoded as constraints)
- The agent gets "smarter" the longer the project runs
- New team members inherit all accumulated knowledge instantly
