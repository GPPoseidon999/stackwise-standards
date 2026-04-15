---
id: vue/component-structure
title: Vue Component Structure
type: stack
stack: vue
concern: structure
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - .vue
  - script setup
  - defineProps
related_rules:
  - vue/reactivity
---
# Vue Component Structure

## When to read
Use this when creating or refactoring Vue components.

## Core rules
- Prefer `script setup` for new components unless a clear reason exists not to.
- Keep props, emits, derived state, and template responsibilities readable and local.
- Move reusable logic into composables instead of large component files.
- Keep templates declarative and avoid burying business logic in bindings.

## Good example
```vue
<script setup lang="ts">
interface Props {
  projectId: string
}

defineProps<Props>()
</script>
```

## Bad example
```vue
<script>
export default {
  data() {
    return { everything: {} }
  },
}
</script>
```

## Exceptions
Legacy Vue 2 or migration code can still use the Options API where needed.
