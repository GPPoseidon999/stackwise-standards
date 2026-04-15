---
id: zod/schema-design
title: Zod Schema Design
type: stack
stack: zod
concern: validation
priority: high
always_apply: false
applies_to:
  - implementation
  - review
  - testing
signals:
  - z.object
  - safeParse
  - parse(
related_rules:
  - security/input-validation
  - react-hook-form/usage
---
# Zod Schema Design

## When to read
Use this when Zod validates forms, API input, config, or third-party data.

## Core rules
- Model schemas around business meaning, not giant generic payloads.
- Use schema parsing at the boundary instead of scattered manual checks.
- Infer TypeScript types from the schema.
- Use safeParse for recoverable flows and parse for fail-fast paths.

## Good example
```typescript
const CreateProjectSchema = z.object({
  name: z.string().min(1).max(50),
  visibility: z.enum(['private', 'public']),
})

```

## Bad example
```typescript
if (!body.name || body.name.length > 50) throw new Error('invalid')

```

## Exceptions
External schemas can be adapted instead of fully rewritten when ownership lives elsewhere.
