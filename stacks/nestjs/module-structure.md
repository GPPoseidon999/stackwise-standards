---
id: nestjs/module-structure
title: NestJS Module Structure
type: stack
stack: nestjs
concern: api
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - @Module
  - @Injectable
  - @Controller
related_rules:
  - security/input-validation
  - security/auth-boundaries
---
# NestJS Module Structure

## When to read
Use this when NestJS owns backend modules, providers, and controllers.

## Core rules
- Group code by business module, not by decorator type only.
- Keep DTO validation at the boundary and domain logic in services.
- Avoid large god modules with too many unrelated providers.
- Use guards, pipes, and interceptors deliberately instead of hand-rolled controller checks.

## Good example
```typescript
@Module({ controllers: [ProjectsController], providers: [ProjectsService] })
export class ProjectsModule {}

```

## Bad example
```typescript
@Module({ controllers: [A, B, C, D], providers: [EverythingService] })
export class AppModule {}

```

## Exceptions
A very small proof of concept can start flatter before module boundaries settle.
