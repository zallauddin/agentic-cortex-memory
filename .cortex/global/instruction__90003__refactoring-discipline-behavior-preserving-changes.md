---
id: 90003
type: instruction
title: "Refactoring Discipline: Behavior-Preserving Changes"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/ciembor/agent-rules-books"
created_at: "2026-07-13"
tags: ["community", "source:agent-rules-books", "refactoring"]
synced_at: "2026-07-13T05:12:29.918Z"
---

# Refactoring Discipline

## Primary Directive
Improve the internal structure of code **without changing its observable behavior.**
All code generation, edits, and reviews must optimize for:
- Small behavior-preserving changes
- Clearer names
- Lower duplication
- Explicit movement from bad design toward good design

## What Counts as Refactoring
- Renaming variables, functions, classes to reveal intent
- Extracting functions/methods to reduce duplication
- Moving code to improve cohesion (related things together)
- Replacing magic numbers with named constants
- Simplifying conditional logic (guard clauses, early returns, polymorphism)

## What Is NOT Refactoring
- Adding new features
- Fixing bugs (fix the bug first, then refactor)
- Changing public API signatures
- Performance optimization (that's tuning, not refactoring)

## Safety Rules
- **Tests Before Refactor**: If no tests exist, add characterization tests first
- Run tests after EVERY small change — never batch changes and test at the end
- If a test breaks during refactoring, revert immediately and understand why
- Use version control — commit after each successful refactoring step

## Code Smells to Watch For
- Long functions (> 20 lines)
- Duplicated code
- Long parameter lists (> 3 params)
- Feature envy (method uses more of another class than its own)
- Primitive obsession (using strings/ints instead of small objects)
- Switch statements (polymorphism often better)
- Speculative generality (code for future needs that may never arrive)
