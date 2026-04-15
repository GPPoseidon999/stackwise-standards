---
id: jotai/atom-structure
title: Jotai Atom Structure
type: stack
stack: jotai
concern: state
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - atom(
  - useAtom
  - jotai
related_rules:
  - performance/rerender-control
---
# Jotai Atom Structure

## When to read
Use this when Jotai manages shared client state.

## Core rules
- Keep atoms small and domain-focused.
- Prefer derived atoms for computed state over duplicating data.
- Group related atoms and actions in one module.
- Avoid turning Jotai into one giant global bag of atoms.

## Good example
```typescript
export const projectAtom = atom<Project | null>(null)
export const projectNameAtom = atom((get) => get(projectAtom)?.name ?? '')
```

## Bad example
```typescript
export const appStateAtom = atom({
  user: null,
  projects: [],
  filters: {},
  modals: {},
})
```

## Exceptions
Prototype code can start with a coarse atom before state shape is understood.
