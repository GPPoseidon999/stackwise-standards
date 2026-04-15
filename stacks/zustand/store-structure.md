---
id: zustand/store-structure
title: Zustand Store Structure
type: stack
stack: zustand
concern: state
priority: high
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - zustand
  - create(
  - set(
related_rules:
  - performance/rerender-control
---
# Zustand Store Structure

## When to read
Use this when Zustand manages cross-component client state.

## Core rules
- Split stores by domain, not by random helper groupings.
- Define state, actions, and selectors close together.
- Use selectors in components instead of reading the whole store.
- Keep async flows in store actions when they belong to store ownership.

## Good example
```typescript
export const useProjectStore = create<ProjectStore>()((set) => ({
  project: null,
  setProject: (project) => set({ project }),
}))

```

## Bad example
```typescript
const useStore = create((set) => ({ a: 1, b: 2, c: 3 }))
const state = useStore()

```

## Exceptions
Page-local UI state can stay in useState.
