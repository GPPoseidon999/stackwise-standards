---
id: fastify/api-structure
title: Fastify API Structure
type: stack
stack: fastify
concern: api
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - fastify
  - app.route
  - schema:
related_rules:
  - security/input-validation
  - security/auth-boundaries
---
# Fastify API Structure

## When to read
Use this when Fastify handles HTTP APIs or backend services.

## Core rules
- Define route schema close to the route and validate input at the edge.
- Keep handlers thin and move business logic into services.
- Use plugins to compose infrastructure and cross-cutting concerns.
- Keep reply shape stable within an endpoint family.

## Good example
```typescript
app.post('/projects', {
  schema: { body: CreateProjectSchema },
  handler: createProjectHandler,
})
```

## Bad example
```typescript
app.post('/projects', async (request, reply) => {
  // validate, authorize, write db, map response, log errors
})
```

## Exceptions
Very small internal tools can stay flatter until the API surface grows.
