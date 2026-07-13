---
id: 90026
type: pattern
title: "Agent Self-Improvement: Grounded Reflection (Never Self-Evaluate)"
confidence: 95
importance: 10
provenance: community
source_url: "https://addyosmani.com/blog/self-improving-coding-agents/"
created_at: "2026-07-13"
tags: ["community", "source:research", "self-improvement", "grounded-reflection", "verification"]
synced_at: "2026-07-13T05:35:14.162Z"
---

# Grounded Reflection: External Verification Over Self-Evaluation

## The Core Problem
Agents suffer from "coherence bias" — they agree with their own incorrect reasoning.
Naive self-reflection ("Is this correct?") produces unreliable results because the
same model that made the error cannot reliably detect it.

## The Rule: Never Self-Evaluate
- Never ask an agent "Is this correct?" about its own output
- Never trust an agent's own assessment of its code quality
- Self-critique without external evidence is worse than no critique at all

## Grounded Verification Methods
1. **Execution-grounded validation**: Run the tests. If they pass, the code works. If they fail, it doesn't.
2. **Linter/formatter output**: Run eslint, prettier, mypy, gofmt. Don't guess — check.
3. **Build/compilation**: Does it compile? A passing build is not proof of correctness, but a failing build is proof of incorrectness.
4. **Browser automation**: For UI changes, actually render and inspect the result.
5. **Separate reviewer agent**: Use a different model or a fresh context to review. The reviewer should see only the diff, not the conversation that produced it.

## Concrete Practice
- Before claiming a bug is fixed: reproduce the bug with a test, then show the test passing
- Before claiming a feature works: write a test that exercises the feature end-to-end
- Before claiming code is clean: run the linter and formatter
- When uncertain: say "I would need to verify X by running Y" — don't guess
