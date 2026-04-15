---
id: performance/large-lists
title: Large List Rendering
type: concern
concern: performance
priority: high
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - map(
  - list
  - table
  - virtual
related_rules:
  - performance/rerender-control
  - react/performance
---
# Large List Rendering

## When to read
Use this for tables, feeds, option menus, or any list with many rows.

## Core rules
- Use virtualization once list size or item weight becomes meaningful.
- Keep row components focused and avoid expensive derived props per row.
- Do not use array index keys when rows can reorder.
- Paginate or stream data before rendering very large datasets in one pass.

## Good example
```tsx
const rowVirtualizer = useVirtualizer({ count: rows.length, getScrollElement: () => parentRef.current, estimateSize: () => 40 })

```

## Bad example
```tsx
{rows.map((row, index) => <Row key={index} row={heavyTransform(row)} />)}

```

## Exceptions
Tiny static lists can stay simple and do not need virtualization.
