---
id: cypress/e2e-patterns
title: Cypress E2E Patterns
type: stack
stack: cypress
concern: e2e
priority: medium
always_apply: false
applies_to:
  - e2e
  - testing
  - review
signals:
  - cy.
  - cypress
  - intercept(
related_rules:
  - testing/e2e-scope
---
# Cypress E2E Patterns

## When to read
Use this when browser flows are tested with Cypress.

## Core rules
- Lean on retryability instead of fixed waits.
- Use intercept for controlled network behavior.
- Keep custom commands focused and transparent.
- Use stable selectors or testing-library style queries.

## Good example
```typescript
cy.intercept('GET', '/api/projects/*').as('getProject')
cy.findByRole('button', { name: 'Save' }).click()

```

## Bad example
```typescript
cy.get('.page > div:nth-child(3) > button').click()
cy.wait(3000)

```

## Exceptions
Temporary waits can help local debugging but should not ship.
