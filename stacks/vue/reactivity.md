---
id: vue/reactivity
title: Vue Reactivity
type: stack
stack: vue
concern: state
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - ref(
  - reactive(
  - computed(
related_rules:
  - performance/rerender-control
---
# Vue Reactivity

## When to read
Use this when Vue refs, reactive objects, and computed values drive UI state.

## Core rules
- Prefer `ref` for simple values and `reactive` for cohesive object state.
- Use `computed` for derived values instead of duplicating mutable state.
- Keep watchers deliberate and avoid using them as a default control-flow tool.
- Move shared reactive logic into composables.

## Good example
```typescript
const filter = ref('')
const filteredProjects = computed(() => filterProjects(projects.value, filter.value))
```

## Bad example
```typescript
const filteredProjects = ref([])
watch([projects, filter], () => {
  filteredProjects.value = filterProjects(projects.value, filter.value)
})
```

## Exceptions
Some integration code must use watchers when coordinating with non-reactive APIs.
