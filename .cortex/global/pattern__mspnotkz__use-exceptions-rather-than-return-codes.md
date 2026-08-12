---
id: mspnotkz
type: pattern
title: Use Exceptions Rather Than Return Codes
confidence: 75
importance: 5
provenance: cortex-auto
tags:
  - expert-principle
  - error-handling
  - source:clean-code-error-handling
  - crystallized
  - auto-discovered
  - error-handling
  - cortex-auto
created_at: '2026-08-12'
synced_at: '2026-08-12T05:35:59.171Z'

---

# Use Exceptions Rather Than Return Codes

Returning error codes from functions clutters the caller with immediate error handling. Use exceptions instead so the happy path is clear and error handling is centralized.

- **Category:** error-handling
- **Tier:** yellow
- **Confidence:** 75%
- **Source:** clean-code-error-handling
