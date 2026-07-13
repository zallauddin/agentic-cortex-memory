---
id: 90000
type: instruction
title: "Clean Code: Naming Conventions for AI Agents"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/ciembor/agent-rules-books"
created_at: "2026-07-13"
tags: ["community", "source:agent-rules-books", "clean-code", "naming"]
synced_at: "2026-07-13T05:12:29.916Z"
---

# Clean Code Naming Rules

## Names Must Reveal Intent
- Use intention-revealing names that answer: why it exists, what it does, and how it is used
- A variable name should describe the thing it holds, not how it was computed
- Avoid single-letter names except for loop counters in very short scopes (i, j, k)
- Avoid the "Hungarian notation" prefixing pattern entirely

## Avoid Disinformation
- Do not refer to a grouping of accounts as `accountList` unless it is actually a List type
- Avoid names that vary only in subtle ways (e.g., `XYZControllerForEfficientHandling` vs `XYZControllerForEfficientStorage`)
- Never use lowercase-L or uppercase-O as variable names (they look like 1 and 0)

## Make Meaningful Distinctions
- `a1`, `a2` are NOT meaningful distinctions — they provide no clue about intent
- `ProductInfo` and `ProductData` are noise words — `Info` and `Data` are indistinct
- If names must be different, they should also mean something different

## Use Pronounceable & Searchable Names
- Names should be easy to pronounce (enables verbal discussion)
- Single-letter names are NOT searchable — use full words
- The length of a name should correspond to the size of its scope

## Class & Method Names
- Classes and objects: noun or noun phrase (`Customer`, `Account`, `AddressParser`)
- Methods: verb or verb phrase (`postPayment`, `deletePage`, `save`)
- Accessors: prefix with `get`, `set`, `is` / `has` for booleans
