---
id: 90011
type: instruction
title: "Frontend Component Patterns for AI-Generated Code"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/affaan-m/ecc"
created_at: "2026-07-13"
tags: ["community", "source:ecc", "frontend", "components"]
synced_at: "2026-07-13T05:12:29.921Z"
---

# Frontend Component Patterns

## Component Composition
- Prefer composition over inheritance — always
- Build components from the "inside out": atoms → molecules → organisms → pages
- Each component should have a single responsibility
- Use the compound component pattern for complex UI with shared state

## State Management
- Lift state to the closest common ancestor (not automatically to the top)
- Use `useReducer` over `useState` when state logic is complex (multiple sub-values)
- Keep server state and UI state separate — use React Query/SWR for server state
- Avoid prop drilling beyond 2 levels — use context or composition instead

## Custom Hooks
- Extract reusable logic into custom hooks
- Hook names MUST start with `use`
- A hook should do one thing well: `useQuery`, `useToggle`, `useDebounce`, `useLocalStorage`
- Never call hooks inside conditions, loops, or nested functions

## Performance
- Memoize expensive computations with `useMemo`
- Memoize callback references with `useCallback` when passed to memo'd children
- Use `React.memo` for components that re-render often with same props
- Lazy-load routes and heavy components: `React.lazy` + `Suspense`
- Avoid anonymous functions/objects as props (they break memoization)

## Accessibility (a11y)
- Every interactive element must be keyboard accessible
- Use semantic HTML: `<button>`, not `<div onClick>`
- Every image needs `alt` text (empty `alt=""` for decorative images)
- Label every form input: associate `<label>` with `<input>` via `htmlFor`/nesting
