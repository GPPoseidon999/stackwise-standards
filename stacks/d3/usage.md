---
id: d3/usage
title: D3 Usage
type: stack
stack: d3
concern: visualization
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - d3
  - scaleLinear
  - select(
related_rules:
  - performance/large-lists
---
# D3 Usage

## When to read
Use this when D3 is responsible for custom charting or data-driven SVG work.

## Core rules
- Keep data transforms separate from DOM rendering code.
- Let React own the tree unless direct D3 DOM control is clearly required.
- Build scales, axes, and layout helpers from stable inputs.
- Clean up listeners and observers created by D3 integrations.

## Good example
```tsx
const x = d3.scaleLinear().domain([0, max]).range([0, width])
const bars = data.map((item) => ({ ...item, x: x(item.value) }))
```

## Bad example
```tsx
useEffect(() => {
  d3.select(containerRef.current).append('svg').append('g').append('rect')
}, [data])
```

## Exceptions
Standalone static SVG generation can use direct D3 rendering without React coordination.
