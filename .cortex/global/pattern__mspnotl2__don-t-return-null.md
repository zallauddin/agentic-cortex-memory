---
id: mspnotl2
type: pattern
title: Don't Return Null
confidence: 75
importance: 5
provenance: cortex-auto
tags:
  - expert-principle
  - null-safety
  - source:clean-code-error-handling
  - crystallized
  - auto-discovered
  - null-safety
  - cortex-auto
created_at: '2026-08-12'
synced_at: '2026-08-12T05:35:59.174Z'

---

# Don't Return Null

Returning null from methods creates null-check clutter in every caller. If you're tempted to return null, throw an exception or return a Special Case object instead.

- **Category:** null-safety
- **Tier:** yellow
- **Confidence:** 75%
- **Source:** clean-code-error-handling
