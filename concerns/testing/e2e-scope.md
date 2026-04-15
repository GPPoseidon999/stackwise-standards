---
id: testing/e2e-scope
title: E2E Scope
type: concern
concern: testing
priority: medium
always_apply: false
applies_to:
  - e2e
  - review
signals:
  - page.
  - cy.
  - browser
  - journey
related_rules:
  - playwright/e2e-patterns
  - cypress/e2e-patterns
---
# E2E Scope

## When to read
Use this when deciding what end-to-end tests should cover.

## Core rules
- E2E tests should protect real user journeys and production-critical integrations.
- Do not push every edge case down into E2E when unit or integration tests are cheaper.
- Keep flows short, deterministic, and independently executable.
- Use stable fixtures and environment setup so failures are actionable.

## Good example
```text
Good E2E targets: sign in, create resource, pay, invite, permission change

```

## Bad example
```text
Bad E2E targets: every validation branch, every pure formatter, every reducer branch

```

## Exceptions
A platform-specific regression can justify a narrow E2E even if lower-level tests already exist.
