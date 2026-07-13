---
id: 90025
type: pattern
title: "Agent Self-Improvement: The Compound Engineering Loop"
confidence: 95
importance: 10
provenance: community
source_url: "https://every.to/source-code/compound-engineering"
created_at: "2026-07-13"
tags: ["community", "source:research", "self-improvement", "compound-engineering", "meta-learning"]
synced_at: "2026-07-13T05:35:14.162Z"
---

# The Compound Engineering Loop

A four-step cycle that makes every agent session build on all previous ones.

## The Cycle

**1. Plan** — Research the codebase and define a clear, testable scope before writing any code.
- Read relevant existing code, tests, and conventions
- State assumptions explicitly
- Define verifiable success criteria before starting

**2. Work** — Implement the plan in atomic, reversible steps.
- Each commit should be one logical change
- Keep changes small enough to reason about locally
- Match existing conventions, even if they differ from preference

**3. Review** — Subject code to external, objective validation.
- Run the full test suite — never skip tests
- Run linters and formatters
- Use a separate "reviewer" agent or perspective for code review
- Check: correctness, clarity, consistency, completeness

**4. Compound** — Persist what was learned for future sessions.
- If a mistake happened: add a rule preventing it in the context file
- If a pattern worked: codify it as a preferred approach
- If a gotcha was discovered: document the specific scenario and fix
- Update CLAUDE.md / AGENTS.md / .cursorrules with the new knowledge

## Why This Works
- Every completed session makes all future sessions better
- Mistakes are encoded as constraints, not repeated
- Patterns are codified as defaults, not rediscovered
- New team members inherit all accumulated knowledge on first bootstrap
