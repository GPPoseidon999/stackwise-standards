---
id: tanstack-table/usage
title: TanStack Table Usage
type: stack
stack: tanstack-table
concern: data-grid
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - useReactTable
  - columnDef
  - getCoreRowModel
related_rules:
  - performance/large-lists
  - virtualization/usage
---
# TanStack Table Usage

## When to read
Use this when TanStack Table powers tables or data grids.

## Core rules
- Treat the table as headless state and render your own stable UI layer.
- Keep column definitions close to the feature that owns the table.
- Memoize heavy table inputs only when profiling shows churn.
- Pair large row counts with virtualization instead of rendering everything.

## Good example
```typescript
const table = useReactTable({
  data,
  columns,
  getCoreRowModel: getCoreRowModel(),
})
```

## Bad example
```typescript
const table = useReactTable({
  data: rows.map(expensiveTransform),
  columns: buildColumnsFromRuntimeConfig(config),
})
```

## Exceptions
Small static tables can stay simple without extra optimization layers.
