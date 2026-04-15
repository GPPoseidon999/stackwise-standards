---
id: nuxt/data-fetching
title: Nuxt Data Fetching
type: stack
stack: nuxt
concern: data-fetching
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - useAsyncData
  - useFetch
  - server/
related_rules:
  - performance/async-waterfalls
---
# Nuxt Data Fetching

## When to read
Use this when Nuxt pages or composables load server-backed data.

## Core rules
- Use Nuxt data primitives instead of ad hoc fetch logic in many components.
- Run independent requests in parallel.
- Keep server-only access and secrets inside server routes or server utilities.
- Make caching and refresh behavior explicit for critical pages.

## Good example
```typescript
const { data: project } = await useAsyncData('project', () => $fetch(`/api/projects/${projectId}`))
```

## Bad example
```typescript
onMounted(async () => {
  project.value = await $fetch(`/api/projects/${projectId}`)
})
```

## Exceptions
Purely client-driven widgets can fetch locally when SEO and first render are irrelevant.
