---
id: graphql/operation-design
title: GraphQL Operation Design
type: stack
stack: graphql
concern: data
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - gql
  - query
  - mutation
  - fragment
related_rules:
  - apollo/cache-and-client
---
# GraphQL Operation Design

## When to read
Use this when authoring GraphQL queries, mutations, and fragments.

## Core rules
- Request only the fields the screen or command needs.
- Use stable fragments for shared entity shapes.
- Keep mutation inputs explicit and business-oriented.
- Do not overload one giant query for unrelated screens.

## Good example
```graphql
query ProjectCard($id: ID!) {
  project(id: $id) {
    id
    name
    status
  }
}

```

## Bad example
```graphql
query AppBootstrap {
  viewer { ...everything }
  projects { ...everything }
  teams { ...everything }
}

```

## Exceptions
A one-off admin query can be broad during diagnosis, but production UI queries should stay scoped.
