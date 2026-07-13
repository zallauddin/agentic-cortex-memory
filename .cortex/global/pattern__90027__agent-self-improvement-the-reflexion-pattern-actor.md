---
id: 90027
type: pattern
title: "Agent Self-Improvement: The Reflexion Pattern (Actor-Evaluator-Reflection)"
confidence: 95
importance: 9
provenance: community
source_url: "https://arxiv.org/abs/2303.11366"
created_at: "2026-07-13"
tags: ["community", "source:research", "self-improvement", "reflexion", "actor-evaluator"]
synced_at: "2026-07-13T05:35:14.163Z"
---

# The Reflexion Pattern

From Shinn et al. (2023) — the foundational framework for verbal reinforcement
learning in language agents. Works without model weight updates.

## Three Components

**Actor** — Generates actions and text based on the current task and memory.
- Produces: code changes, tool calls, responses
- Operates within the current context window

**Evaluator** — Scores the trajectory against objective criteria.
- Uses external signals: test results, build status, lint output, user feedback
- Produces: a scalar reward or structured feedback
- NEVER uses the same LLM instance that generated the code

**Self-Reflection** — Converts feedback + trajectory into actionable advice.
- Input: what was attempted, what the outcome was, what the evaluator said
- Output: a concise "reflection" stored in episodic memory
- Format: "In situation X, action Y led to outcome Z. Next time, try W instead."

## The Loop
1. Actor takes action based on task + memory
2. Evaluator assesses the outcome using external signals
3. Self-Reflection generates a memory entry from the assessment
4. Next iteration: Actor starts with updated memory
5. Repeat until success criteria met or iteration budget exhausted

## Key Constraints
- Limit to 1-2 reflection passes — infinite loops degrade quality
- Reflections must cite specific evidence, not general impressions
- Failed reflections ("try harder next time") are noise — delete them
- Successful reflections should be promoted to permanent rules after 3+ confirmations
