---
id: echarts/usage
title: ECharts Usage
type: stack
stack: echarts
concern: visualization
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - echarts
  - setOption
  - dispose
related_rules:
  - performance/large-lists
---
# ECharts Usage

## When to read
Use this when ECharts powers dashboards or analytics views.

## Core rules
- Import ECharts modules on demand.
- Dispose chart instances on unmount.
- Use ResizeObserver or controlled container resizing.
- Keep chart option generation outside JSX noise.

## Good example
```typescript
const chart = echarts.init(container)
chart.setOption(option)
return () => chart.dispose()

```

## Bad example
```typescript
import * as echarts from 'echarts'
window.addEventListener('resize', () => chart.resize())

```

## Exceptions
Quick prototypes may tolerate broad imports, but production code should tighten them.
