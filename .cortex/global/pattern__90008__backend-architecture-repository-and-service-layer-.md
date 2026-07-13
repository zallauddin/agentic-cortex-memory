---
id: 90008
type: pattern
title: "Backend Architecture: Repository and Service Layer Patterns"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/affaan-m/ecc"
created_at: "2026-07-13"
tags: ["community", "source:ecc", "backend", "architecture", "patterns"]
synced_at: "2026-07-13T05:12:29.920Z"
---

# Backend Architecture Patterns

## Repository Pattern
- Separate data access logic from business logic
- Every data source gets its own repository class/module
- Repositories are the ONLY place that executes database queries
- Return domain objects, not raw query results
- Never expose the underlying database driver outside the repository

## Service Layer
- Services encapsulate business logic and orchestration
- A service method should represent one complete business operation
- Services call repositories — never the reverse
- Handle transactions at the service layer, not in repositories

## N+1 Query Prevention
- Always batch-load related data instead of looping queries
- Use JOINs or eager loading (`include`, `with`, `preload`) for known relationships
- For GraphQL: implement DataLoader pattern for batching
- Review every loop that contains a database call — it's likely an N+1 bug

## Transaction Management
- Wrap multi-step mutations in transactions
- Keep transactions as short as possible (no I/O, no network calls inside transactions)
- Use optimistic concurrency when conflicts are rare; pessimistic when they're common
- Always handle rollback explicitly
