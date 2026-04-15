---
id: mui/component-usage
title: MUI Component Usage
type: stack
stack: mui
concern: ui
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - @mui/
  - sx=
  - <Button
related_rules:
  - build/import-boundaries
---
# MUI Component Usage

## When to read
Use this when Material UI is the base component system.

## Core rules
- Use theme tokens and variants before custom ad hoc styles.
- Keep business wrappers outside the base layer.
- Prefer direct imports for tree shaking.
- Preserve semantic accessibility attributes through wrappers.

## Good example
```tsx
import Button from '@mui/material/Button'
<Button variant="contained">Save</Button>

```

## Bad example
```tsx
import * as MUI from '@mui/material'
<MUI.Button sx={{ color: '#123456' }}>Save</MUI.Button>

```

## Exceptions
A simple internal admin page can use small sx overrides when it stays local.
