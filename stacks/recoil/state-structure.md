---
id: recoil/state-structure
title: Recoil State Structure
type: stack
stack: recoil
concern: state
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - atom(
  - selector(
  - useRecoilState
related_rules:
  - performance/rerender-control
---
# Recoil State Structure

## When to read
Use this when Recoil manages application state and derived values.

## Core rules
- Keep atoms focused and selectors pure.
- Use selectors for derived data instead of duplicating state.
- Group related atoms and selectors by domain.
- Avoid large cross-cutting atoms that trigger broad rerenders.

## Good example
```typescript
export const projectFilterAtom = atom({
  key: 'projectFilter',
  default: '',
})

export const filteredProjectsSelector = selector({
  key: 'filteredProjects',
  get: ({ get }) => filterProjects(get(projectsAtom), get(projectFilterAtom)),
})
```

## Bad example
```typescript
export const appAtom = atom({
  key: 'app',
  default: { user: null, projects: [], filters: {}, modals: {} },
})
```

## Exceptions
Short-lived prototypes may use coarse state before domain structure settles.
