---
id: 90031
type: instruction
title: "Agent Self-Improvement: Error Taxonomy & Targeted Recovery"
confidence: 95
importance: 9
provenance: community
source_url: "https://arxiv.org/abs/2310.04438"
created_at: "2026-07-13"
tags: ["community", "source:research", "self-improvement", "error-taxonomy", "recovery"]
synced_at: "2026-07-13T05:35:14.165Z"
---

# Error Taxonomy for AI Coding Agents

Classifying errors enables targeted recovery strategies instead of generic retries.
Each error type has a specific recovery path.

## Error Taxonomy

**SyntaxError** — Code doesn't parse or compile.
- Recovery: Check syntax with linter/compiler, fix the specific syntax issue, recompile.
- Prevention: Run syntax check after every code change before proceeding.

**TypeError / NullReference** — Wrong type or null/undefined where value expected.
- Recovery: Trace the value origin, add type guard or null check, verify with type checker.
- Prevention: Use strict typing, exhaustive null checks, avoid 'any'.

**AssertionError** — Test assertion failed.
- Recovery: Understand what the test expects vs. what the code produces. Fix the mismatch.
- Prevention: Write the test BEFORE the implementation (TDD).

**TimeoutError** — Operation exceeded time limit.
- Recovery: Check if the resource is available, increase timeout (only if justified), add retry.
- Prevention: Set explicit timeouts on all external calls; never rely on defaults.

**AuthError / ForbiddenError** — Missing or invalid credentials.
- Recovery: Check environment variables, token validity, permission scope. Don't retry blindly.
- Prevention: Validate credentials at startup; fail fast if auth is misconfigured.

**ResourceExhaustion** — Out of memory, disk, connections, or rate limit.
- Recovery: Release resources, add backpressure, implement exponential backoff.
- Prevention: Bound all resource usage; stream large data instead of loading into memory.

**Hallucination** — Agent used a non-existent API, function, or library.
- Recovery: Verify the API exists in the installed version. If not, find the real API.
- Prevention: Always check package.json / go.mod / Cargo.toml before calling third-party APIs.

**LogicError** — Code compiles and runs but produces wrong results.
- Recovery: Trace through the logic with specific inputs, identify where expectation diverges from reality.
- Prevention: Write unit tests for business logic before integrating.

## The Recovery Protocol
1. Classify the error using the taxonomy above
2. Apply the type-specific recovery strategy (don't retry the same approach)
3. If recovery fails twice: escalate to human with the full error context and what was tried
4. After successful recovery: record the error type + fix as a learning
