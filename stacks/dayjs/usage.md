---
id: dayjs/usage
title: dayjs Usage
type: stack
stack: dayjs
concern: utilities
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - dayjs(
  - .format(
  - .tz(
related_rules:
  - date-fns/usage
---
# dayjs Usage

## When to read
Use this when a chainable date API fits the codebase better than pure functions.

## Core rules
- Load plugins deliberately and centrally.
- Keep timezone handling explicit.
- Use one shared formatting layer for user-facing dates.
- Do not mix dayjs objects and raw strings throughout business logic.

## Good example
```typescript
return dayjs(project.createdAt).utc().format('YYYY-MM-DD HH:mm')

```

## Bad example
```typescript
return dayjs(project.createdAt).format()

```

## Exceptions
Small debug outputs can stay unformatted.
