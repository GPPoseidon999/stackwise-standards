---
id: radix/component-usage
title: Radix Component Usage
type: stack
stack: radix
concern: ui
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - "@radix-ui/"
  - asChild
  - Portal
related_rules:
  - shadcn/component-usage
---
# Radix Component Usage

## When to read
Use this when composing accessible primitives from Radix UI.

## Core rules
- Keep semantics intact when using asChild.
- Use data attributes for state styling instead of DOM-structure assumptions.
- Handle focus and layering correctly when Portal is involved.
- Expose stable app-level APIs instead of leaking primitive details everywhere.

## Good example
```tsx
<Dialog.Trigger asChild><button type="button">Open</button></Dialog.Trigger>

```

## Bad example
```tsx
<Dialog.Trigger><div onClick={openDialog}>Open</div></Dialog.Trigger>

```

## Exceptions
A thin prototype wrapper is acceptable before a component becomes shared.
