---
id: playwright/e2e-patterns
title: Playwright E2E Patterns
type: stack
stack: playwright
concern: e2e
priority: high
always_apply: false
applies_to:
  - testing
  - review
  - e2e
signals:
  - "page."
  - "@playwright/test"
  - getByRole
related_rules:
  - testing/e2e-scope
---
# Playwright E2E Patterns

## When to read
Use this when Playwright covers browser journeys.

## Core rules
- Use semantic locators such as role and label first.
- Keep flows independent and deterministic.
- Avoid waitForTimeout in committed tests.
- Extract repeated navigation or setup into page objects or helpers.

## Good example
```typescript
await page.getByRole('button', { name: 'Create project' }).click()
await expect(page.getByText('Project created')).toBeVisible()

```

## Bad example
```typescript
await page.click('.page > div:nth-child(2) > button')
await page.waitForTimeout(3000)

```

## Exceptions
Temporary waits are acceptable while debugging locally, but remove them before merge.
