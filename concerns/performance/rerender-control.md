---
id: performance/rerender-control
title: Rerender Control
type: concern
concern: performance
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - useMemo
  - useCallback
  - Context
related_rules:
  - react/performance
  - zustand/store-structure
---
# Rerender Control

## When to read
Use this when state updates feel noisy or list performance degrades.

## Core rules
- Reduce subscription scope before adding memoization.
- Avoid high-frequency state in broad Context providers.
- Pass stable props to expensive child components.
- Use selectors in global state libraries instead of whole-store reads.

## Good example
```tsx
const userName = useUserStore((state) => state.user?.name)

```

## Bad example
```tsx
const state = useUserStore()
return <Row meta={{ active: true }} user={state.user} />

```

## Exceptions
Small, non-critical components may keep simpler code until real rerender cost appears.
