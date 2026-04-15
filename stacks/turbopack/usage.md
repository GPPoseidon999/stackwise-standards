---
id: turbopack/usage
title: Turbopack Usage
type: stack
stack: turbopack
concern: build
priority: low
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - turbopack
  - next dev --turbo
related_rules:
  - build/code-splitting
  - build/import-boundaries
---
# Turbopack Usage

## When to read
Use this when Turbopack is part of the local or production build pipeline.

## Core rules
- Keep build assumptions explicit and verify compatibility for custom plugins or loaders.
- Prefer standard framework conventions over deep bundler customization.
- Review large dependency changes because fast dev builds can still hide output cost.
- Keep fallback build paths clear while Turbopack support evolves.

## Good example
```text
Use default framework-supported Turbopack settings and review deviations carefully.
```

## Bad example
```text
Assume every webpack-era customization will behave the same under Turbopack.
```

## Exceptions
Experimental apps can move faster, but production assumptions still need verification.
