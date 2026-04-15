---
id: mongoose/schema-and-model
title: Mongoose Schema and Model
type: stack
stack: mongoose
concern: data
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - new Schema
  - model(
  - .populate(
related_rules:
  - security/input-validation
---
# Mongoose Schema and Model

## When to read
Use this when Mongoose models MongoDB documents.

## Core rules
- Define schema constraints explicitly instead of relying on loose document shape.
- Keep model hooks and virtuals focused and predictable.
- Avoid unbounded populate chains in request paths.
- Map documents into response DTOs when external shape should differ from persistence shape.

## Good example
```typescript
const ProjectSchema = new Schema({
  name: { type: String, required: true, trim: true },
})

```

## Bad example
```typescript
const ProjectSchema = new Schema({}, { strict: false })

```

## Exceptions
Admin migration scripts may temporarily use looser schema assumptions outside normal runtime.
