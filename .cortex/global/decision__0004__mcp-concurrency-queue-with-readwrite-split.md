---
id: 4
type: decision
title: "MCP concurrency queue with read/write split"
confidence: 100
importance: 8
provenance: observed
created_at: "2026-07-03 15:15:21"
tags: ["mcp", "concurrency", "architecture", "source:sourcecode-agentic-cortex"]
synced_at: "2026-07-13T02:32:30.833Z"
---

The MCP server now serializes state-modifying tool calls per project (save, edit, forget, reflect, import, relate, share, session start/end) while allowing read-only tools (search, get, list, context, health) to execute concurrently. Prevents SQLite busy errors.
