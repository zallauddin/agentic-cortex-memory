---
id: 90032
type: pattern
title: "Agent Self-Improvement: Retrospective Analysis (Post-Task Review)"
confidence: 95
importance: 10
provenance: community
source_url: "https://developersdigest.substack.com/p/self-improving-ai-agents"
created_at: "2026-07-13"
tags: ["community", "source:research", "self-improvement", "retrospective", "post-mortem"]
synced_at: "2026-07-13T05:35:14.165Z"
---

# Retrospective Analysis Protocol

After every non-trivial task, run a structured retrospective. This is the "Compound"
step of the Compound Engineering loop — the most frequently skipped, most valuable step.

## The Retrospective Template

**1. What was the original goal?**
- Restate the task as a single sentence
- What were the specific acceptance criteria?

**2. Did we achieve it?**
- Verified by: tests passing, build green, user approval, metrics, etc.
- If no: what's the gap? What remains?

**3. What went well?** (Preserve these patterns)
- Which approaches worked better than expected?
- Which tools or patterns were especially effective?
- What would you do the same way next time?

**4. What went wrong?** (Prevent recurrence)
- Which assumptions were incorrect?
- Where did the agent waste time or go down wrong paths?
- What errors occurred that should have been caught earlier?

**5. What should be persisted?** (Compound the knowledge)
- New constraint for CLAUDE.md / AGENTS.md: "Never use X because Y"
- New pattern to codify: "Always do Z before W"
- New gotcha to document: "Library A version 2.x breaks B when C"
- Update to existing learning: adjust confidence, add evidence

**6. What's the next action?**
- Is there follow-up work? Known debt? Unresolved questions?
- Record as a task or flag for the next session

## When to Run Retrospectives
- After any task that took more than 3 tool calls
- After any task where an error or unexpected behavior occurred
- At the end of every session (even short ones — 30 seconds of review saves hours later)
- Skip only for trivial single-step operations (read a file, answer a fact question)
