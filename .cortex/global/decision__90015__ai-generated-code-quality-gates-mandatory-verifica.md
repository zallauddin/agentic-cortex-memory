---
id: 90015
type: decision
title: "AI-Generated Code Quality Gates: Mandatory Verification Steps"
confidence: 95
importance: 10
provenance: community
created_at: "2026-07-13"
tags: ["community", "quality", "verification", "code-review"]
synced_at: "2026-07-13T05:12:29.922Z"
---

# Code Quality Gates for AI-Generated Code

Before accepting ANY AI-generated code change, apply these gates:

## Gate 1: Syntax & Compilation
- Does it parse/compile without errors?
- Run: `npm run build`, `cargo check`, `go build`, etc.

## Gate 2: Existing Tests
- Do ALL existing tests still pass?
- A change that breaks existing tests is a regression — reject until fixed

## Gate 3: Linting
- Does it pass the project's linter/formatter?
- Run: `npm run lint`, `eslint`, `prettier --check`, etc.

## Gate 4: Security Scan
- No hardcoded secrets, API keys, or tokens
- No `eval()`, no raw SQL concatenation, no `innerHTML` with user input
- Dependencies are not introducing known vulnerabilities

## Gate 5: Behavioral Correctness
- If new functionality: write (or ask for) a test that proves it works
- If bug fix: write a test that reproduces the bug and now passes
- Code that compiles but doesn't do what it claims is WORSE than no code

## Gate 6: Code Review
- Review the diff as if a junior developer submitted it
- Check: clarity, correctness, consistency, completeness
- If you don't understand a line, don't accept it
