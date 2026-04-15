---
id: shadcn/component-usage
title: shadcn/ui Component Usage
type: stack
stack: shadcn
concern: ui
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - @/components/ui/
  - cn(
related_rules:
  - tailwind/usage
  - radix/component-usage
---
# shadcn/ui Component Usage

## When to read
Use this when composing business UI from shadcn/ui building blocks.

## Core rules
- Prefer composing existing base components over copying and forking them.
- Keep business wrappers outside the base ui layer.
- Preserve stable variant and size APIs across similar components.
- Use cn and token-driven classes instead of deep ad hoc overrides.

## Good example
```tsx
import { Button } from '@/components/ui/button'
export function SaveButton() {
  return <Button type="submit">Save</Button>
}

```

## Bad example
```tsx
export function Button() {
  return <button className="..." />
}

```

## Exceptions
A fully custom visual language can justify separate business components.
