---
id: react/hooks
title: React Hooks
type: stack
stack: react
concern: hooks
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - useEffect
  - useState
  - useMemo
related_rules:
  - react/component-structure
  - performance/async-waterfalls
---
# React Hooks

## When to read
Use this when writing custom hooks or effectful React logic.

## Core rules
- Custom hooks should have a clear single purpose.
- Keep effect dependencies complete and explicit.
- Do not make the effect function itself async.
- Move data fetching into reusable hooks when shared across components.

## Good example
```tsx
useEffect(() => {
  async function load() {
    setUser(await fetchUser(userId))
  }
  load()
}, [userId])

```

## Bad example
```tsx
useEffect(async () => {
  setUser(await fetchUser(userId))
}, [])

```

## Exceptions
A component-local effect can stay inline when it is tiny and not reusable.
