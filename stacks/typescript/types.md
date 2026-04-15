---
id: typescript/types
title: TypeScript Types
type: stack
stack: typescript
concern: typing
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - as any
  - @ts-ignore
  - .ts
related_rules:
  - typescript/naming
  - security/input-validation
---
# TypeScript Types

## When to read
Use this when defining interfaces, unions, assertions, and return types.

## Core rules
- Do not use as any.
- Prefer interface for object shapes and type for unions or helpers.
- Use unknown plus narrowing at trust boundaries.
- Add explicit return types when inference is not obvious.

## Good example
```typescript
function parseProject(data: unknown): Project {
  if (!isProject(data)) throw new Error('Invalid project')
  return data
}

```

## Bad example
```typescript
const project = payload as any
// @ts-ignore
function getData(a, b) { return fetchData(a, b) }

```

## Exceptions
Tests can relax typing slightly for mock data when readability wins.
