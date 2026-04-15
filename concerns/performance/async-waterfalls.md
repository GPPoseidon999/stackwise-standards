---
id: performance/async-waterfalls
title: Avoid Async Waterfalls
type: concern
concern: performance
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - await
  - fetch
  - Promise
related_rules:
  - react-query/data-fetching
  - nextjs/data-fetching
---
# Avoid Async Waterfalls

## When to read
Use this when loading several independent resources or composing server data.

## Core rules
- Run independent requests in parallel.
- Move first-load fetching up to the nearest useful boundary.
- Avoid nested component waterfalls caused by sequential effects.
- Cache or prefetch shared data instead of refetching it in sibling trees.

## Good example
```typescript
const [profile, teams] = await Promise.all([
  fetchProfile(userId),
  fetchTeams(userId),
])

```

## Bad example
```typescript
const profile = await fetchProfile(userId)
const teams = await fetchTeams(userId)

```

## Exceptions
Keep requests sequential only when later work truly depends on earlier results.
