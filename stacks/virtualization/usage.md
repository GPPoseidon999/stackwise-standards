---
id: virtualization/usage
title: Virtualization Usage
type: stack
stack: virtualization
concern: performance
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - useVirtualizer
  - react-virtualized
  - react-virtual
related_rules:
  - performance/large-lists
---
# Virtualization Usage

## When to read
Use this when long lists, tables, or grids should render only visible rows.

## Core rules
- Virtualize once row count or row weight makes full rendering expensive.
- Keep row height assumptions explicit and measurable.
- Separate virtualization logic from row presentation.
- Verify keyboard, focus, and scroll behavior after virtualization.

## Good example
```typescript
const rowVirtualizer = useVirtualizer({
  count: rows.length,
  getScrollElement: () => parentRef.current,
  estimateSize: () => 40,
})
```

## Bad example
```tsx
{rows.map((row) => (
  <HeavyRow key={row.id} row={row} />
))}
```

## Exceptions
Short lists and fixed tiny datasets do not need virtualization complexity.
