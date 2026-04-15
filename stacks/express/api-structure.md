---
id: express/api-structure
title: Express API Structure
type: stack
stack: express
concern: api
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - express()
  - req
  - res
  - next
related_rules:
  - security/input-validation
  - security/auth-boundaries
---
# Express API Structure

## When to read
Use this when Express handles HTTP routing and middleware.

## Core rules
- Keep routing, validation, domain logic, and persistence in separate layers.
- Validate request input before controller logic.
- Return one response shape per endpoint family.
- Use centralized error middleware for translation and logging.

## Good example
```typescript
router.post('/projects', validate(CreateProjectSchema), createProjectHandler)

```

## Bad example
```typescript
app.post('/projects', async (req, res) => {
  // validate, authorize, write db, map response, log errors all here
})

```

## Exceptions
A tiny internal script server can keep a flatter shape until endpoints multiply.
