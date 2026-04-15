---
id: koa/api-structure
title: Koa API Structure
type: stack
stack: koa
concern: api
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - new Koa
  - ctx.
  - middleware
related_rules:
  - security/input-validation
  - security/auth-boundaries
---
# Koa API Structure

## When to read
Use this when Koa middleware and routes handle backend requests.

## Core rules
- Keep middleware single-purpose and ordered deliberately.
- Validate and authorize before domain work.
- Keep response mapping out of low-level utility middleware.
- Pass typed state through context only when ownership is clear.

## Good example
```typescript
router.post('/projects', validate(CreateProjectSchema), authorize('project:create'), createProjectHandler)
```

## Bad example
```typescript
app.use(async (ctx) => {
  // parse, validate, authorize, write db, shape response
})
```

## Exceptions
Tiny webhook receivers may keep a flatter stack if the path stays narrow.
