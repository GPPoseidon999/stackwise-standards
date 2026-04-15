---
id: framer-motion/usage
title: Framer Motion Usage
type: stack
stack: framer-motion
concern: motion
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - motion.
  - AnimatePresence
  - layout
related_rules:
  - performance/rerender-control
---
# Framer Motion Usage

## When to read
Use this when Framer Motion drives transitions or layout animation.

## Core rules
- Animate user-relevant state changes, not every render.
- Keep motion props readable and reusable for repeated patterns.
- Prefer subtle defaults over long or heavy transitions.
- Review layout animations for list and dashboard performance.

## Good example
```tsx
<motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }} />
```

## Bad example
```tsx
<motion.div animate={{ x: Math.random() * 20, rotate: 360, scale: 1.3 }} transition={{ duration: 2.5 }} />
```

## Exceptions
Marketing pages can use richer motion language when performance budgets still hold.
