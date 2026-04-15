---
id: nextjs/data-fetching
title: Next.js Data Fetching
type: stack
stack: nextjs
concern: data-fetching
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - fetch(
  - revalidate
  - cache:
related_rules:
  - performance/async-waterfalls
---
# Next.js Data Fetching

## When to read
Use this when fetching page data, route handler data, or server action data.

## Core rules
- Fetch first-load data on the server when possible.
- Set cache and revalidation behavior explicitly.
- Run independent fetches in parallel.
- Use client-side data libraries only for truly interactive client state.

## Good example
```tsx
const [profile, teams] = await Promise.all([
  fetchProfile(userId),
  fetchTeams(userId),
])

```

## Bad example
```tsx
const profile = await fetchProfile(userId)
const teams = await fetchTeams(userId)

```

## Exceptions
Sequential fetches are fine when later calls depend on earlier output.
