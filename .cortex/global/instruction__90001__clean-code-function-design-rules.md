---
id: 90001
type: instruction
title: "Clean Code: Function Design Rules"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/ciembor/agent-rules-books"
created_at: "2026-07-13"
tags: ["community", "source:agent-rules-books", "clean-code", "functions"]
synced_at: "2026-07-13T05:12:29.917Z"
---

# Clean Code Function Rules

## Functions Should Be Small
- Functions should rarely be longer than 20 lines
- Each function should do ONE thing, do it well, and do it only
- If a function tries to do more than one thing, extract helper functions

## One Level of Abstraction Per Function
- Statements within a function should all be at the same level of abstraction
- Mixing high-level (business logic) with low-level (file I/O) in one function is a code smell
- The Stepdown Rule: code should read like a top-down narrative

## Function Arguments
- Zero arguments is ideal; one is fine; two is acceptable; three should be avoided
- More than three arguments needs special justification
- Avoid boolean flag arguments — they signal the function does two things
- If a function needs many arguments, some should likely be grouped into an object

## Command-Query Separation
- A function should either DO something (command) or ANSWER something (query), never both
- Functions that change state should not return values
- Functions that return values should not change observable state

## Prefer Exceptions to Error Codes
- Use try/catch instead of returning error codes
- Extract the try/catch body into its own function
- Error handling is ONE thing — a function that handles errors should do nothing else

## Don't Repeat Yourself (DRY)
- Duplication is the root of all evil in software
- Every piece of knowledge should have a single, unambiguous representation
