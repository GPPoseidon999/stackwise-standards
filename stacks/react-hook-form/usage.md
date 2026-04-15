---
id: react-hook-form/usage
title: React Hook Form Usage
type: stack
stack: react-hook-form
concern: forms
priority: high
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - useForm
  - Controller
  - handleSubmit
related_rules:
  - zod/schema-design
---
# React Hook Form Usage

## When to read
Use this when forms have validation, submission, or shared field state.

## Core rules
- Initialize defaults in useForm, not through scattered later mutation.
- Use a schema resolver for real validation.
- Use register for simple inputs and Controller only for controlled widgets.
- Keep submit handlers focused on orchestration, not inline validation logic.

## Good example
```typescript
const form = useForm<FormValues>({
  resolver: zodResolver(FormSchema),
  defaultValues: { name: '' },
})

```

## Bad example
```typescript
const form = useForm()
function onSubmit(values) {
  if (!values.name) setError('name', { message: 'Required' })
}

```

## Exceptions
Single-field lightweight interactions may stay local without a form library.
