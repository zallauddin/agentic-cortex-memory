---
id: 90029
type: instruction
title: "Agent Self-Improvement: Root Cause Analysis from Errors"
confidence: 95
importance: 9
provenance: community
source_url: "https://github.com/zallauddin/agentic-cortex"
created_at: "2026-07-13"
tags: ["community", "source:research", "self-improvement", "rca", "error-analysis"]
synced_at: "2026-07-13T05:35:14.163Z"
---

# Root Cause Analysis for Agent Errors

When an agent encounters an error, surface-level fixes ("add a null check") mask
the real problem. Always drill to the systemic cause.

## The RCA Process

**1. Record the Error** — Save the full error with context.
- What was the agent trying to do?
- What was the exact error message?
- What tool/call produced the error?
- What was the state before the error?

**2. Classify the Error Type**
- Knowledge gap: agent didn't know about a library function, API, or convention
- Process flaw: agent followed a workflow that doesn't work for this scenario
- Code issue: agent wrote code that has a bug, logic error, or type mismatch
- Environment issue: tool, network, permission, or configuration problem
- Assumption error: agent assumed something that wasn't true

**3. Identify the Root Cause**
Ask "Why?" repeatedly until you reach a systemic issue:
- Why did the error occur? → The function returned undefined
- Why was undefined returned? → The API changed its response format
- Why didn't we detect the API change? → No contract test exists
- Why no contract test? → Testing only covers internal logic, not external boundaries
→ Root cause: Missing boundary/contract testing for external API dependencies

**4. Create a Systemic Fix**
- The fix should prevent the CLASS of error, not just the instance
- Format: "When [trigger condition], always [preventive action]"
- Record the fix as a learning with confidence 75-85
- Link the learning to the error via 'derives_from' relation

**5. Verify the Fix**
- Does the fix address the root cause (not just the symptom)?
- Would the fix have prevented the original error?
- Does the fix introduce new failure modes?
