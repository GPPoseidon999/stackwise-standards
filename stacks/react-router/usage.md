---
id: react-router/usage
title: React Router Usage
type: stack
stack: react-router
concern: routing
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - useNavigate
  - useParams
  - <Route
related_rules:
  - security/input-validation
---
# React Router Usage

## When to read
Use this when routing is handled fully on the client.

## Core rules
- Keep route paths in one central module.
- Use semantic path helpers instead of string concatenation.
- Validate params from useParams before use.
- Wrap auth routing once instead of duplicating per page.

## Good example
```typescript
export const PATHS = {
  project: (id: string) => `/projects/${id}`,
} as const

```

## Bad example
```typescript
navigate('/projects/' + id)

```

## Exceptions
Small demos can stay simple, but shared apps should centralize route definitions.
