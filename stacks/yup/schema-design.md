---
id: yup/schema-design
title: Yup Schema Design
type: stack
stack: yup
concern: validation
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - yup.
  - object(
  - validationSchema
related_rules:
  - formik/usage
  - security/input-validation
---
# Yup Schema Design

## When to read
Use this when Yup handles form or request validation.

## Core rules
- Keep schema shape aligned with the real payload or form model.
- Centralize validation in schema modules instead of ad hoc checks.
- Reuse shared field fragments when multiple forms need the same constraints.
- Keep coercion and defaults explicit so downstream code is predictable.

## Good example
```typescript
const CreateProjectSchema = yup.object({
  name: yup.string().required().max(50),
  slug: yup.string().required(),
})
```

## Bad example
```typescript
if (!values.name || values.name.length > 50) {
  errors.name = 'Invalid'
}
```

## Exceptions
A codebase migrating from Yup to Zod can keep old schemas temporarily behind clear boundaries.
