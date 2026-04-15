---
id: recharts/usage
title: Recharts Usage
type: stack
stack: recharts
concern: visualization
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - recharts
  - ResponsiveContainer
  - LineChart
related_rules:
  - performance/large-lists
---
# Recharts Usage

## When to read
Use this when Recharts powers dashboards or reporting components.

## Core rules
- Keep chart data shaping outside JSX.
- Use ResponsiveContainer or a stable layout wrapper for sizing.
- Reuse tooltip, axis, and formatter helpers across similar charts.
- Avoid re-rendering large chart trees for tiny unrelated state changes.

## Good example
```tsx
<ResponsiveContainer width="100%" height={240}>
  <LineChart data={chartData}>
    <Line dataKey="value" stroke="#0f172a" />
  </LineChart>
</ResponsiveContainer>
```

## Bad example
```tsx
<LineChart data={rows.map((row) => expensiveTransform(row))}>
  <Line dataKey="value" />
</LineChart>
```

## Exceptions
Tiny one-off charts can keep inline configuration if they stay local.
