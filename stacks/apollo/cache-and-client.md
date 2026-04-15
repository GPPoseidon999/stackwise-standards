---
id: apollo/cache-and-client
title: Apollo Client and Cache
type: stack
stack: apollo
concern: data-fetching
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - ApolloClient
  - InMemoryCache
  - fetchPolicy
related_rules:
  - graphql/operation-design
  - testing/mock-boundaries
---
# Apollo Client and Cache

## When to read
Use this when Apollo Client owns GraphQL fetching and normalization.

## Core rules
- Create the client and cache once at the app boundary.
- Define type policies deliberately instead of relying on accidental cache behavior.
- Use fetch policies intentionally per use case.
- Keep local cache writes explicit and reviewable.

## Good example
```typescript
const client = new ApolloClient({
  link,
  cache: new InMemoryCache({ typePolicies: { Project: { keyFields: ['id'] } } }),
})

```

## Bad example
```typescript
const client = new ApolloClient({ link, cache: new InMemoryCache() }) // no cache strategy thought through

```

## Exceptions
A throwaway internal tool can start with default cache behavior before hardening policies.
