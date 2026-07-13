---
id: 90010
type: instruction
title: "AI Coding Agent: Security Review Checklist"
confidence: 95
importance: 10
provenance: community
source_url: "https://github.com/affaan-m/ecc"
created_at: "2026-07-13"
tags: ["community", "source:ecc", "security"]
synced_at: "2026-07-13T05:12:29.921Z"
---

# Security Review Checklist for AI-Generated Code

## Authentication & Authorization
- Never implement your own auth — use established libraries (OAuth, Passport, NextAuth)
- Always hash passwords with bcrypt/argon2 — never store plain text
- Validate permissions on every protected endpoint, not just UI visibility
- Use short-lived JWTs with refresh token rotation
- Implement rate limiting on auth endpoints

## Input Validation
- NEVER trust user input — validate on the server regardless of client-side validation
- Use parameterized queries 100% of the time — never concatenate strings into SQL
- Sanitize all output to prevent XSS: use framework escaping (`dangerouslySetInnerHTML` is a red flag)
- Validate file uploads: type, size, content — never trust the MIME type alone

## Secrets Management
- NEVER hardcode secrets, API keys, or tokens in source code
- Use environment variables with fallback to a secrets manager
- Add `.env` and `.env.local` to `.gitignore`
- Rotate secrets regularly; revoke immediately if exposed

## Dependency Security
- Pin dependency versions exactly (no `^` or `~` ranges without lockfiles)
- Run `npm audit` / `pip audit` in CI
- Review every new dependency — prefer well-maintained, popular packages
- Keep dependencies updated (Dependabot/Renovate)

## Common Vulnerabilities
- CSRF: use anti-CSRF tokens for state-changing operations
- CORS: restrict origins to known domains — never use `*` with credentials
- SQL Injection: use ORM/query builder parameterization; never raw string interpolation
- Path Traversal: validate and sanitize file paths; use `path.resolve` to prevent escape
- ReDoS: avoid regex with nested quantifiers on user input
