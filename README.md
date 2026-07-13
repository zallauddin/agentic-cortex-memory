# Agentic Cortex — Team Memory Repository

> **Shared, machine-readable knowledge for AI coding agents.**  
> 48 observations across 11 sources — coding standards, architecture patterns, security rules, self-improvement protocols, multi-agent patterns, and battle-tested project lessons.

---

## What Is This?

This repository is a **team memory vault** for AI coding agents (Claude Code, Cursor, OpenCode, Codex, etc.). It contains structured `.md` files that agents pull at bootstrap and push to when they discover new knowledge. Every observation is a single, verifiable unit of knowledge with YAML frontmatter metadata.

**How it works:**

```
Agent bootstraps
    ↓
Pulls this repo into ~/.agentic-cortex/memory-repo
    ↓
Reads .cortex/global/*.md → injects into context
    ↓
Agent now knows: coding standards, gotchas, patterns, security rules
    ↓
When agent discovers something new → auto-pushes to this repo
```

---

## File Format

Every observation lives in `.cortex/global/` as a Markdown file with YAML frontmatter:

```markdown
---
id: 90000
type: instruction
title: "Clean Code: Naming Conventions for AI Agents"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/ciembor/agent-rules-books"
created_at: "2026-07-07"
tags: ["community", "source:agent-rules-books", "clean-code", "naming"]
synced_at: "2026-07-07T12:34:56.789Z"
---

# Clean Code Naming Rules

## Names Must Reveal Intent
- Use intention-revealing names...
```

### Frontmatter Fields

| Field | Type | Description |
|---|---|---|
| `id` | int | Globally unique identifier. IDs ≥ 90000 are community-imported. |
| `type` | string | `instruction`, `pattern`, `decision`, `error`, `learning`, `fact`, `context`, `event` |
| `title` | string | Human-readable summary |
| `confidence` | 0–100 | How certain this knowledge is (95+ = well-evidenced) |
| `importance` | 1–10 | How critical this is for agents to know (10 = essential) |
| `provenance` | string | `community`, `project`, `session`, or `derived` |
| `source_url` | string | Link to original source (optional) |
| `tags` | string[] | Categorization: `source:*`, `clean-code`, `security`, `self-improvement`, etc. |
| `synced_at` | ISO 8601 | When this observation was written to the repo |

### Filename Convention

```
{type}__{id-padded-5}__{slug}.md
```

Example: `instruction__90000__clean-code-naming-conventions-for-ai-agents.md`

---

## Observation Inventory (48 Total)

### 🏗️ Project Battle-Tested (11 observations)

Lessons extracted from real development sessions across the `agentic-cortex` and `markethub` projects.

| ID | Type | Title | Source |
|---|---|---|---|
| 0003 | decision | CLI Deduplication Completed | agentic-cortex |
| 0004 | decision | MCP Concurrency Queue with Read/Write Split | agentic-cortex |
| 0006 | decision | CLI Test | agentic-cortex |
| 0023 | instruction | Setup PostgreSQL | agentic-cortex |
| 0028 | decision | Self-Improve ResetState Added for Testability | agentic-cortex |
| 0029 | error | HybridSearch isActive Bug Fixed | agentic-cortex |
| 0049 | learning | Pattern: Testing | agentic-cortex |
| 0050 | learning | Pattern: Fact | agentic-cortex |
| 0051 | learning | Pattern: Observation | agentic-cortex |
| 0052 | learning | Pattern: Decision | agentic-cortex |
| 0053 | learning | Pattern: Event | agentic-cortex |

### 📚 agent-rules-books (12 observations)

Canonical coding rules distilled from classic software engineering books, adapted for AI coding agents.

| ID | Type | Book | Content |
|---|---|---|---|
| 90000 | instruction | **Clean Code** | Naming conventions: reveal intent, avoid disinformation, searchable names |
| 90001 | instruction | **Clean Code** | Function design: small functions, one level of abstraction, command-query separation |
| 90002 | instruction | **Clean Code** | Comments & formatting: why over what, consistent style, no commented-out code |
| 90012 | instruction | **SOLID** | Single Responsibility, Open/Closed, Liskov, Interface Segregation, Dependency Inversion |
| 90013 | instruction | **KISS/DRY/YAGNI** | Simplicity first, knowledge deduplication, don't build what you don't need |
| 90018 | instruction | **Clean Code (mini)** | Full canonical rules: 14 decision rules + 8 trigger rules + final checklist |
| 90019 | instruction | **Clean Architecture (mini)** | Full canonical rules: dependency direction, use-case boundaries, humble adapters |
| 90020 | instruction | **Refactoring (mini)** | Full canonical rules: behavior-preserving steps, code smells, safety nets |
| 90021 | instruction | **Pragmatic Programmer (mini)** | Full canonical rules: orthogonality, tracer bullets, domain languages, automation |
| 90022 | instruction | **Legacy Code (mini)** | Full canonical rules: seams, characterization tests, dependency breaking |
| 90023 | instruction | **Release It! (mini)** | Full canonical rules: timeouts, circuit breakers, bulkheads, production readiness |

### 🧠 Anthropic (4 observations)

Official guidance from Anthropic on building effective coding agents.

| ID | Type | Title |
|---|---|---|
| 90005 | pattern | **Agent Design Pattern**: Start Simple, Add Complexity Only When Needed |
| 90006 | instruction | **ACI Tool Design**: Agent-Computer Interface principles — ergonomics, namespacing, poka-yoke |
| 90007 | instruction | **Claude Code Best Practices**: Verification, CLAUDE.md compounding, plan mode, parallelization |
| 90014 | pattern | **Compounding Knowledge**: Treat context files as living knowledge bases |

### 🔧 ECC / Everything Claude Code (4 observations)

Community-curated coding standards from the ECC skills ecosystem.

| ID | Type | Title |
|---|---|---|
| 90008 | pattern | **Backend Architecture**: Repository pattern, service layer, N+1 prevention, transactions |
| 90009 | instruction | **API Design**: REST naming, HTTP methods, status codes, response envelopes, error format |
| 90010 | instruction | **Security Checklist**: Auth, input validation, secrets, dependencies, common vulnerabilities |
| 90011 | instruction | **Frontend Patterns**: Component composition, state management, hooks, performance, a11y |

### 🎯 cursor.directory (2 observations)

The most popular community rules for AI coding agents.

| ID | Type | Title |
|---|---|---|
| 90004 | instruction | **Anti-Sycophancy Code Discipline**: 17 rules — verify libraries, no invented APIs, honest status |
| 90024 | instruction | **TypeScript/Node.js Rules**: Strict typing, error handling, backend patterns, project structure |

### 🎓 Karpathy Guidelines (1 observation)

Andrej Karpathy's four principles for LLM-assisted coding.

| ID | Type | Title |
|---|---|---|
| 90017 | instruction | **Think, Simplify, Be Surgical, Verify**: State assumptions, minimum code, touch only what you must, loop until verified |

### 🌐 Community Best Practices (2 observations)

General-purpose agent knowledge.

| ID | Type | Title |
|---|---|---|
| 90015 | decision | **Code Quality Gates**: 6 mandatory verification steps (syntax, tests, lint, security, behavior, review) |
| 90016 | instruction | **Effective Prompting**: Structure, do's/don'ts, skeleton-first pattern |

### 🔄 Agent Self-Improvement (8 observations)

Meta-learning patterns for how agents should learn from their mistakes and improve over time.

| ID | Type | Title | Source |
|---|---|---|---|
| 90025 | pattern | **The Compound Engineering Loop** — Plan → Work → Review → Compound | every.to |
| 90026 | pattern | **Grounded Reflection** — Never self-evaluate; verify against external truth | Addy Osmani |
| 90027 | pattern | **The Reflexion Pattern** — Actor → Evaluator → Self-Reflection → Memory | Shinn et al. (2023) |
| 90028 | pattern | **Atomic Instinct Learning** — Granular instincts with confidence decay (0.3–0.95) | ECC |
| 90029 | instruction | **Root Cause Analysis from Errors** — 5-step RCA: record, classify, drill, fix, verify | agentic-cortex |
| 90030 | instruction | **Learning Verification & Confidence Calibration** — Reinforce +5, contradict -15, decay -2/mo | agentic-cortex |
| 90031 | instruction | **Error Taxonomy & Targeted Recovery** —
