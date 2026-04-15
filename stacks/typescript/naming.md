---
id: typescript/naming
title: TypeScript Naming
type: stack
stack: typescript
concern: naming
priority: medium
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - .ts
  - .tsx
  - interface
related_rules:
  - typescript/types
---
# TypeScript Naming

## When to read
Use this for variables, functions, types, files, and folders.

## Core rules
- Use camelCase for variables and functions.
- Use PascalCase for components, types, and interfaces.
- Use clear boolean prefixes such as is, has, and can.
- Prefer explicit names over cryptic abbreviations.

## Good example
```typescript
const isLoading = true
interface ProjectCardProps {
  onSelect: () => void
}

```

## Bad example
```typescript
const loading = true
const x = getProject()

```

## Exceptions
Math formulas and tight loops may still use x, y, i, or j.
