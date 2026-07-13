---
id: 29
type: error
title: "hybridSearch is_active bug fixed"
confidence: 100
importance: 8
provenance: observed
created_at: "2026-07-03 22:01:22"
tags: ["search", "bug", "is_active", "soft-delete", "source:sourcecode-agentic-cortex"]
synced_at: "2026-07-13T02:32:30.835Z"
---

The hybridSearch function's phase 2 and 3 queries bypassed the buildWhereClause is_active=1 filter. The FTS-expansion query (SELECT id FROM observations WHERE embedding IS NOT NULL) and fallback query omitted the is_active check, allowing soft-deleted (forgotten) observations with embeddings to appear in search results. Fix adds is_active=1 to both queries.
