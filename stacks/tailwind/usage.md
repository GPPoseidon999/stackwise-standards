---
id: tailwind/usage
title: Tailwind Usage
type: stack
stack: tailwind
concern: styling
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - className=
  - tailwind
related_rules:
  - shadcn/component-usage
---
# Tailwind Usage

## When to read
Use this when styling with utility classes.

## Core rules
- Keep class order predictable.
- Extract repeated class groups into components or helpers.
- Prefer design tokens over arbitrary magic values.
- Do not hide a full page of styling inside one giant className string.

## Good example
```tsx
<button className="inline-flex items-center rounded-md bg-slate-900 px-4 py-2 text-sm text-white">Save</button>

```

## Bad example
```tsx
<button className={`p-[13px] ${active ? 'bg-[#111]' : 'bg-[#333]'} text-white`}>Save</button>

```

## Exceptions
Temporary prototype styling can be rough, but shared components should be cleaned up.
