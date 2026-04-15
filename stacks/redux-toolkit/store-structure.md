---
id: redux-toolkit/store-structure
title: Redux Toolkit Store Structure
type: stack
stack: redux-toolkit
concern: state
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - createSlice
  - createAsyncThunk
related_rules:
  - testing/test-case-design
---
# Redux Toolkit Store Structure

## When to read
Use this when Redux Toolkit manages shared client state.

## Core rules
- Split slices by domain.
- Keep thunks and selectors close to the slice that owns them.
- Handle pending, fulfilled, and rejected states for async flows.
- Do not store trivial local UI state globally.

## Good example
```typescript
const projectSlice = createSlice({
  name: 'project',
  initialState,
  reducers: {},
})

```

## Bad example
```typescript
async function handleSubmit() {
  await dispatch(fetchProject(projectId))
}

```

## Exceptions
Simple page-local toggles can stay local.
