---
id: nuxt/app-structure
title: Nuxt App Structure
type: stack
stack: nuxt
concern: routing
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - pages/
  - useAsyncData
  - defineNuxtRouteMiddleware
related_rules:
  - nuxt/data-fetching
  - security/client-server-boundaries
---
# Nuxt App Structure

## When to read
Use this when Nuxt handles routing, rendering, and app composition.

## Core rules
- Let file-based routing drive page structure instead of custom route indirection.
- Keep page logic thin and move reusable logic into composables and server utilities.
- Use route middleware deliberately for navigation concerns, not as a catch-all business layer.
- Keep app-wide plugins and modules explicit and minimal.

## Good example
```vue
<script setup lang="ts">
const route = useRoute()
const projectId = computed(() => route.params.projectId as string)
</script>
```

## Bad example
```vue
<script setup lang="ts">
// giant page with routing, fetching, auth, and presentation all mixed together
</script>
```

## Exceptions
Small content sites can stay flatter if there is little shared app logic.
