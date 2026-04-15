---
id: react/performance
title: React Performance
type: stack
stack: react
concern: performance
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - key=
  - React.lazy
  - Context
related_rules:
  - performance/rerender-control
  - performance/large-lists
---
# React Performance

## When to read
Use this when rendering lists, splitting bundles, or tuning client updates.

## Core rules
- Use stable keys for list items.
- Lazy load route-level and heavy optional UI.
- Avoid broad Context providers for frequently changing state.
- Measure before adding memoization noise.

## Good example
```tsx
{items.map((item) => <Row key={item.id} item={item} />)}

```

## Bad example
```tsx
{items.map((item, index) => <Row key={index} item={item} />)}

```

## Exceptions
A static list that never reorders may use an index key.
