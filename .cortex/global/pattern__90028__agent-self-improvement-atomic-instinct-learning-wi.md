---
id: 90028
type: pattern
title: "Agent Self-Improvement: Atomic Instinct Learning with Confidence Decay"
confidence: 95
importance: 9
provenance: community
source_url: "https://github.com/affaan-m/ecc"
created_at: "2026-07-13"
tags: ["community", "source:research", "self-improvement", "instinct-learning", "confidence-decay"]
synced_at: "2026-07-13T05:35:14.163Z"
---

# Atomic Instinct Learning

Inspired by ECC's continuous-learning-v2. Instead of saving large, monolithic
"skills" that are hard to verify, decompose successes and failures into granular,
testable "instincts" with confidence scores.

## Atomic Instinct Format
```
# INSTINCT: Always verify file exists after bash write
Trigger: PostToolUse hook fires after Write tool
Condition: tool_name === 'Write' || tool_name === 'write_to_file'
Action: Run 'ls <filepath>' to confirm file was created
Confidence: 0.85
Evidence: 12 successes, 1 failure (file creation delayed by 200ms — added retry)
```

## Confidence Scoring
- Every instinct starts at confidence 0.5 (neutral)
- Each successful application: confidence += 0.05 (capped at 0.95)
- Each failure/contradiction: confidence -= 0.15
- Below 0.30: instinct is retired (likely wrong or outdated)
- Above 0.85: instinct is "hardened" — changes require stronger evidence

## Evolution Path
1. **Observation**: A pattern is noticed across 3+ sessions
2. **Instinct**: Pattern is codified with trigger + action + confidence
3. **Rule**: At confidence 0.85+, instinct is promoted to a permanent context rule
4. **Skill**: Multiple related rules are composed into a reusable skill module

## Anti-Patterns
- Don't create instincts from a single occurrence — wait for repetition
- Don't harden instincts without diverse evidence (different projects, contexts)
- Don't keep instincts that fire but never change outcomes — they're noise
- Don't let confidence scores drift without periodic re-evaluation
