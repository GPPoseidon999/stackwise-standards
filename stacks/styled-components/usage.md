---
id: styled-components/usage
title: styled-components Usage
type: stack
stack: styled-components
concern: styling
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - styled.
  - ThemeProvider
related_rules:
  - tailwind/usage
---
# styled-components Usage

## When to read
Use this when styling through styled-components.

## Core rules
- Keep styling at the bottom of the file or in a dedicated styling module.
- Use theme tokens instead of hard-coded brand values.
- Use transient props for style-only props.
- Do not embed business logic in style declarations.

## Good example
```typescript
const StyledButton = styled.button<{ $fullWidth?: boolean }>`
  width: ({ $fullWidth }) => ($fullWidth ? '100%' : 'auto');
`

```

## Bad example
```typescript
const Button = styled.button`
  background: #1fc7d4;
`

```

## Exceptions
A very small one-off layout wrapper may stay minimal.
