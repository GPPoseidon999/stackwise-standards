---
id: axios/usage
title: Axios Usage
type: stack
stack: axios
concern: data-fetching
priority: high
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - axios
  - interceptors
  - http.get
related_rules:
  - security/input-validation
---
# Axios Usage

## When to read
Use this when Axios is the HTTP client.

## Core rules
- Create one shared instance per backend domain.
- Register interceptors centrally.
- Keep auth header and error translation out of UI code.
- Return typed domain results from service functions.

## Good example
```typescript
const http = axios.create({ baseURL: API_URL, timeout: 10_000 })
export async function fetchProject(id: string): Promise<Project> {
  return http.get(`/projects/${id}`)
}

```

## Bad example
```typescript
await axios.get('/api/projects', { headers: { Authorization: token } })

```

## Exceptions
A third-party API may use its own isolated instance.
