---
id: antd/component-usage
title: Ant Design Component Usage
type: stack
stack: antd
concern: ui
priority: medium
always_apply: false
applies_to:
  - implementation
  - review
signals:
  - antd
  - Form
  - Table
  - App
related_rules:
  - build/import-boundaries
---
# Ant Design Component Usage

## When to read
Use this when Ant Design is the primary component system.

## Core rules
- Prefer theme tokens, variants, and official component APIs before deep overrides.
- Keep business wrappers outside the shared antd layer.
- Avoid global style hacks that fight built-in layout and state behavior.
- For data-heavy screens, review Table and Form performance early.

## Good example
```tsx
import { Button, Form, Input } from 'antd'

export function ProjectForm() {
  return (
    <Form layout="vertical">
      <Form.Item label="Name" name="name">
        <Input />
      </Form.Item>
      <Button htmlType="submit" type="primary">
        Save
      </Button>
    </Form>
  )
}
```

## Bad example
```tsx
import * as Antd from 'antd'

<Antd.Button style={{ color: '#123456', marginTop: 13 }}>Save</Antd.Button>
```

## Exceptions
Tiny internal admin tools can use small local overrides if they stay isolated.
