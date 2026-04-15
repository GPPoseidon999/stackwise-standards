---
id: security/input-validation
title: Input Validation
type: concern
concern: security
priority: critical
always_apply: true
applies_to:
  - implementation
  - review
  - testing
signals:
  - req.body
  - params
  - searchParams
  - dangerouslySetInnerHTML
related_rules:
  - zod/schema-design
  - security/auth-boundaries
---
# Input Validation

## When to read
Use this whenever data crosses a trust boundary.

## Core rules
- Validate all request, form, URL, and third-party payloads before business logic.
- Treat client validation as UX only, not as the final security gate.
- Sanitize or reject untrusted HTML before rendering it.
- Convert unknown inputs into typed domain objects at the edge.

## Good example
```typescript
const parsed = CreateProjectSchema.safeParse(req.body)
if (!parsed.success) return res.status(400).json({ message: 'Invalid input' })

```

## Bad example
```typescript
createProject(req.body)
return <div dangerouslySetInnerHTML={{ __html: apiHtml }} />

```

## Exceptions
Static internal constants do not need runtime validation when they cannot be user-controlled.
