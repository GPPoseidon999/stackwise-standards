---
id: nextjs/app-router
title: Next.js App Router
type: stack
stack: nextjs
concern: routing
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - app/
  - page.tsx
  - layout.tsx
related_rules:
  - nextjs/data-fetching
  - security/client-server-boundaries
---
# Next.js App Router

## When to read
Use this when building routes, layouts, loading states, and server components.

## Core rules
- Prefer server components by default.
- Use client components only for browser-only behavior.
- Keep layout.tsx focused on structure, not auth logic.
- Validate params and searchParams before using them.

## Good example
```tsx
export default async function Page({ params }: PageProps) {
  const input = ParamsSchema.parse(params)
  return <ProjectView project={await getProject(input.projectId)} />
}

```

## Bad example
```tsx
'use client'
export default function Page() {
  const data = fetch('/api/projects')
  return <div>...</div>
}

```

## Exceptions
Client components are fine when local interactivity truly requires them.
