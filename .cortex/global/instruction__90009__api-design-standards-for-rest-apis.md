---
id: 90009
type: instruction
title: "API Design Standards for REST APIs"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/affaan-m/ecc"
created_at: "2026-07-13"
tags: ["community", "source:ecc", "api", "rest"]
synced_at: "2026-07-13T05:12:29.920Z"
---

# REST API Design Standards

## Resource Naming
- Use plural nouns for collections: `/users`, not `/user` or `/getUsers`
- Use kebab-case for multi-word resources: `/payment-methods`
- Nest related resources: `/users/:id/orders`
- Avoid verbs in URLs (use HTTP methods instead)

## HTTP Methods (CRUD Mapping)
- `GET /items` — List items (with pagination, filtering, sorting)
- `GET /items/:id` — Get a single item
- `POST /items` — Create a new item
- `PUT /items/:id` — Full replace of an item
- `PATCH /items/:id` — Partial update of an item
- `DELETE /items/:id` — Delete an item

## Status Codes
- `200` — Success (GET, PUT, PATCH)
- `201` — Created (POST)
- `204` — No Content (DELETE)
- `400` — Bad Request (validation error)
- `401` — Unauthorized (missing/invalid auth)
- `403` — Forbidden (valid auth but insufficient permissions)
- `404` — Not Found
- `409` — Conflict (duplicate, version mismatch)
- `422` — Unprocessable Entity (semantic validation failure)
- `500` — Internal Server Error (never expose stack traces)

## Response Envelope
- Always return consistent JSON structure:
```json
{
  "data": { ... },
  "error": null,
  "meta": { "page": 1, "perPage": 20, "total": 100 }
}
```

## Error Responses
- Always include: `error.code`, `error.message`, `error.details` (for validation)
- Never expose internal implementation details or stack traces
- Use RFC 7807 Problem Details format for machine-readable errors
