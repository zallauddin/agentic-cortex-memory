---
id: 3
type: decision
title: "CLI deduplication completed"
confidence: 100
importance: 8
provenance: observed
created_at: "2026-07-03 15:15:20"
tags: ["refactoring", "deduplication", "cli", "source:sourcecode-agentic-cortex"]
synced_at: "2026-07-13T02:32:30.833Z"
---

CLI commands (search, export, context, bulk, conflicts, answer, session) now delegate to the shared API layer instead of duplicating core logic inline. Removed ~500 lines of duplicated code.
