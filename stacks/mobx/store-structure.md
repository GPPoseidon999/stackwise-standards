---
id: mobx/store-structure
title: MobX Store Structure
type: stack
stack: mobx
concern: state
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - makeAutoObservable
  - observable
  - action
related_rules:
  - performance/rerender-control
---
# MobX Store Structure

## When to read
Use this when MobX stores manage reactive application state.

## Core rules
- Keep observable state, computed values, and actions close together.
- Mutate observable state through actions, especially across async flows.
- Split stores by domain instead of one application super-store.
- Keep React bindings thin and let stores own domain transitions.

## Good example
```typescript
class ProjectStore {
  projects: Project[] = []

  constructor() {
    makeAutoObservable(this)
  }

  setProjects(projects: Project[]) {
    this.projects = projects
  }
}
```

## Bad example
```typescript
class AppStore {
  everything = {}
}
```

## Exceptions
Very small apps can start with one store before clear domain boundaries emerge.
