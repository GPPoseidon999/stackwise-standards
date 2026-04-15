---
id: security/client-server-boundaries
title: Client and Server Boundaries
type: concern
concern: security
priority: critical
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - 'use client'
  - layout.tsx
  - window
  - document
related_rules:
  - nextjs/app-router
  - security/secret-handling
---
# Client and Server Boundaries

## When to read
Use this in full-stack React and Next.js codebases.

## Core rules
- Keep auth, permission checks, and sensitive reads on the server.
- Use client components only for browser-specific behavior.
- Do not put auth redirects or permission checks in layout.tsx.
- Do not import server-only modules into client trees.

## Good example
```tsx
export default async function Page() {
  const session = await requireSession()
  return <ProjectPage projects={await listProjects(session.userId)} />
}

```

## Bad example
```tsx
'use client'
export default function Layout() {
  if (!localStorage.getItem('token')) redirect('/login')
}

```

## Exceptions
Pure client apps still need a server API to perform sensitive operations.
