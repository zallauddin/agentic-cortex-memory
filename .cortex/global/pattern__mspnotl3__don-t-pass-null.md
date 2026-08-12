---
id: mspnotl3
type: pattern
title: Don't Pass Null
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
synced_at: '2026-08-12T05:35:59.175Z'

---

# Don't Pass Null

Passing null to methods is worse than returning null. In most languages, there is no good way to deal with null passed by a caller accidentally.

- **Category:** null-safety
- **Tier:** yellow
- **Confidence:** 75%
- **Source:** clean-code-error-handling
