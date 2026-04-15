---
id: formik/usage
title: Formik Usage
type: stack
stack: formik
concern: forms
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - Formik
  - useFormik
  - validationSchema
related_rules:
  - yup/schema-design
---
# Formik Usage

## When to read
Use this when Formik still owns form state and submission flows.

## Core rules
- Initialize values and validation in one place.
- Keep submit handlers focused on orchestration, not field-level branching.
- Use schema validation for real forms instead of scattered custom checks.
- Avoid mixing Formik state with parallel local state for the same fields.

## Good example
```tsx
const formik = useFormik({
  initialValues: { name: '' },
  validationSchema: CreateProjectSchema,
  onSubmit: saveProject,
})
```

## Bad example
```tsx
const [name, setName] = useState('')
const formik = useFormik({ initialValues: { name: '' } })
```

## Exceptions
Single-field interactions can stay outside Formik when no real form workflow exists.
