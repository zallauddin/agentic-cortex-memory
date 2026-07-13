---
id: 90024
type: instruction
title: "TypeScript & Node.js Cursor Rules: Strict Patterns for AI Agents"
confidence: 95
importance: 9
provenance: community
source_url: "https://github.com/PatrickJS/awesome-cursorrules"
created_at: "2026-07-13"
tags: ["community", "source:cursor-directory", "typescript", "nodejs", "strict-mode", "cursor-rules"]
synced_at: "2026-07-13T05:21:04.607Z"
---

# TypeScript & Node.js AI Coding Agent Rules

Curated from the community at PatrickJS/awesome-cursorrules and cursor.directory.

## TypeScript Strictness
- Always use strict typing. Prefer interface over type for object definitions (allows declaration merging).
- Avoid any at all costs. Use unknown if the type is truly undefined and narrow it down with type guards.
- Avoid enums; use const objects or union types instead (enums add runtime overhead and break tree-shaking).
- Use discriminated unions for complex state modeling instead of optional fields.
- Enable strict mode in tsconfig: strict, noUncheckedIndexedAccess, noImplicitReturns.

## Code Style
- Use functional and declarative programming patterns. Prefer pure functions for business logic.
- Separate side-effect-heavy code (IO, database) from pure computation.
- Favor named exports over default exports (better IDE auto-import and refactoring support).
- Use kebab-case for directories and file names: components/auth-wizard, utils/format-date.

## Error Handling
- Handle errors at the boundary with early returns and guard clauses. Avoid deeply nested conditionals.
- Model expected errors as discriminated union return types: { success: true, data: T } | { success: false, error: string }.
- Do not use try/catch for expected business logic errors — return a result object instead.
- Use custom error classes or error factories for unexpected failures. Never throw raw strings.
- In async functions: always handle promise rejections. Use .catch() or try/catch around every await that can fail.

## Backend & Node.js Patterns
- Keep business logic in services/ or lib/. Controllers/routes should be thin — only parse input and format output.
- Use Zod (or equivalent) for validation at every boundary: API input, environment variables, database results.
- Server actions or API handlers must return a consistent response shape: { data, error, meta }.
- Use dependency injection (via function parameters or context) — never rely on global singletons or module-level state.
- Implement the Repository pattern: data access is only through repositories, never raw queries in services.

## Project Structure
- Organize by feature or domain, not by technical role: src/user/, src/order/, not src/controllers/, src/models/.
- Each feature module exports only its public API via an index file.
- Keep shared utilities minimal — avoid a dumping-ground utils/ folder.
- Configuration through environment variables, validated at startup with Zod schemas.

## Testing
- Follow AAA pattern: Arrange, Act, Assert. Keep tests readable as documentation.
- Unit tests for pure business logic; integration tests for database/repository layers; E2E for critical flows.
- Use test doubles (mocks/stubs) only for external boundaries (APIs, databases, file system).
- Test error paths as thoroughly as happy paths.
