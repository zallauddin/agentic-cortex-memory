---
id: 90005
type: pattern
title: "Agent Design Pattern: Start Simple, Add Complexity Only When Needed"
confidence: 95
importance: 8
provenance: community
source_url: "https://www.anthropic.com/engineering/building-effective-agents"
created_at: "2026-07-13"
tags: ["community", "source:anthropic", "agent-patterns", "architecture"]
synced_at: "2026-07-13T05:12:29.919Z"
---

# Agent Architecture: Simplicity First

From Anthropic's Building Effective Agents guide, the core principle is:

> Start with the simplest possible solution and optimize only when needed. Agentic systems trade latency and cost for better task completion. Consider if the extra complexity is justified.

## The Design Spectrum

**Prompt Chaining** (simplest)
- Fixed, sequential steps where each step has a clear gate
- Use when: task can be cleanly decomposed into fixed subtasks
- Example: generate outline → approve → write sections → review

**Routing**
- Classify input, send to specialized handler
- Use when: inputs fall into distinct categories needing different treatment
- Example: route "fix bug" to debugger agent, "add feature" to feature agent

**Parallelization**
- Run independent subtasks simultaneously
- Use when: subtasks don't depend on each other (sectioning) OR need voting/consensus
- Example: linting + testing + security scan in parallel

**Orchestrator-Workers**
- Central LLM dynamically delegates to specialized workers
- Use when: can't predict number of steps or which workers are needed upfront
- Example: complex refactoring that spans multiple files/modules

**Evaluator-Optimizer**
- One LLM generates, another critiques in a loop
- Use when: clear evaluation criteria exist and iterative refinement adds value
- Example: code review → fix → re-review cycle
