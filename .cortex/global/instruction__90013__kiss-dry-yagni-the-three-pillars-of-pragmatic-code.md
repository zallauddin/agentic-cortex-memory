---
id: 90013
type: instruction
title: "KISS, DRY, YAGNI: The Three Pillars of Pragmatic Code"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/ciembor/agent-rules-books"
created_at: "2026-07-13"
tags: ["community", "source:agent-rules-books", "principles", "kiss", "dry", "yagni"]
synced_at: "2026-07-13T05:12:29.922Z"
---

# KISS, DRY, YAGNI

## KISS — Keep It Simple, Stupid
- The simplest solution that meets the requirements is the best solution
- Complexity is a liability — every line of code is a potential bug
- Prefer boring, well-understood solutions over clever, novel ones
- If you can't explain the solution to a junior developer in 5 minutes, it's too complex
- **Anti-pattern**: over-engineering with abstractions for hypothetical future needs

## DRY — Don't Repeat Yourself
- Every piece of knowledge must have a single, unambiguous, authoritative representation
- **This is NOT about code duplication** — it's about knowledge duplication
- Two pieces of code that look similar but represent different knowledge are NOT duplication
- Two pieces of code that look different but represent the same knowledge ARE duplication
- When extracting shared code: ensure the abstraction is worth the indirection

## YAGNI — You Aren't Gonna Need It
- Don't build features, abstractions, or optimizations until you actually need them
- "We might need it later" is the most expensive phrase in software
- Extra code must be: written, tested, documented, maintained, understood, and eventually deleted
- Build for today's requirements; design so tomorrow's are not impossible
- **Corollary**: premature optimization is the root of all evil (Knuth)
