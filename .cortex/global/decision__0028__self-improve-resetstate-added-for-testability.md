---
id: 28
type: decision
title: "self-improve resetState() added for testability"
confidence: 100
importance: 7
provenance: observed
created_at: "2026-07-03 22:01:22"
tags: ["testing", "self-improve", "resetState", "module-state", "source:sourcecode-agentic-cortex"]
synced_at: "2026-07-13T02:32:30.835Z"
---

The _analyzedErrorIds Set in self-improve.js persisted across test runs, causing learnFromError to skip RCA in subsequent tests when fresh in-memory DBs reused row IDs. Added resetState() export that clears the Set. Integration tests call it in beforeEach before api.close()/api.init().
