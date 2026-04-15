---
id: react-query/data-fetching
title: React Query Data Fetching
type: stack
stack: react-query
concern: data-fetching
priority: high
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - useQuery
  - useMutation
  - queryKey
related_rules:
  - performance/async-waterfalls
  - testing/mock-boundaries
---
# React Query Data Fetching

## When to read
Use this when TanStack Query owns client-side server state.

## Core rules
- Use stable semantic query keys.
- Keep query functions pure and side-effect free.
- Handle loading, error, and empty states explicitly.
- Update cache via invalidation or deliberate cache writes, not ad hoc local patching.

## Good example
```typescript
useQuery({
  queryKey: ['project', projectId],
  queryFn: () => fetchProject(projectId),
})

```

## Bad example
```typescript
useQuery({
  queryKey: ['data'],
  queryFn: async () => { toast.info('loading'); return fetchProject(projectId) },
})

```

## Exceptions
Very short-lived local data may not need React Query at all.
