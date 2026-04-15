---
id: date-fns/usage
title: date-fns Usage
type: stack
stack: date-fns
concern: utilities
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - date-fns
  - format(
  - parseISO
related_rules:
  - dayjs/usage
---
# date-fns Usage

## When to read
Use this when pure functional date utilities are needed.

## Core rules
- Parse date inputs explicitly.
- Centralize formatting patterns.
- Keep timezone assumptions visible in code.
- Avoid repeated parse work in render paths.

## Good example
```typescript
const createdAt = parseISO(project.createdAt)
return format(createdAt, 'yyyy-MM-dd HH:mm')

```

## Bad example
```typescript
return new Date(project.createdAt).toString()

```

## Exceptions
A quick debug log can use native Date directly.
