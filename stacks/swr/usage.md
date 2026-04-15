---
id: swr/usage
title: SWR Usage
type: stack
stack: swr
concern: data-fetching
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - useSWR
  - mutate(
  - revalidate
related_rules:
  - performance/async-waterfalls
---
# SWR Usage

## When to read
Use this when SWR owns simple client-side cache and revalidation flows.

## Core rules
- Keep keys stable and semantic.
- Keep fetchers side-effect free.
- Use mutate for cache updates instead of scattered local patches.
- Turn off or change revalidation behavior deliberately when defaults do not fit.

## Good example
```typescript
const { data } = useSWR(['project', projectId], ([, id]) => fetchProject(id))

```

## Bad example
```typescript
useSWR(['project', projectId, Date.now()], () => fetchProject(projectId))

```

## Exceptions
Static build-time data does not need SWR.
