---
id: chartjs/usage
title: Chart.js Usage
type: stack
stack: chartjs
concern: visualization
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - chart.js
  - Chart(
  - react-chartjs-2
related_rules:
  - performance/large-lists
---
# Chart.js Usage

## When to read
Use this when Chart.js renders dashboard or reporting views.

## Core rules
- Register only needed controllers, elements, and scales.
- Keep chart config creation outside JSX noise.
- Destroy chart instances or use a wrapper that manages lifecycle safely.
- Do not animate heavy charts on every small state change.

## Good example
```typescript
Chart.register(LineController, LineElement, PointElement, LinearScale, CategoryScale)

```

## Bad example
```typescript
import Chart from 'chart.js/auto' // everywhere by default

```

## Exceptions
Prototypes can start with chart.js/auto before performance hardening.
