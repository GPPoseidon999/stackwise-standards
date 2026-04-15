# standards-repo

[English](#english) | [中文](#中文)

## English

`standards-repo` is the central source of truth for reusable engineering standards used by `stackwise`.

Product repositories should not keep long-lived copies of shared rules. Instead, `stackwise` syncs a project-specific subset from this repository into local `.standards/`.

### Goals

- Keep stack rules in one place
- Keep cross-cutting concerns in one place
- Make rule selection metadata-driven
- Let product repos sync only what they need

### Structure

```text
standards-repo/
|- stacks/      # Framework, library, and tool rules
|- concerns/    # Testing, performance, build, security, etc.
`- meta/        # Mapping and default selection metadata
```

### Sync model

1. `stackwise` detects stacks from a product repo.
2. Matching `stacks/` rules are copied into `.standards/stacks/`.
3. Default `concerns/` rules are copied into `.standards/concerns/`.
4. Metadata is written to `.standards/active-rules.json`.

### Rule design principles

- One file, one topic
- Short markdown optimized for local AI context
- Stable frontmatter metadata on every rule file
- Keep stack rules and concern rules separate

### Frontmatter example

```md
---
id: react/component-structure
title: React Component Structure
type: stack
stack: react
concern: structure
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - .tsx
  - component
related_rules:
  - react/hooks
---
```

### Metadata fields

| Field | Meaning |
| --- | --- |
| `id` | Stable rule identifier |
| `title` | Short readable title |
| `type` | `stack` or `concern` |
| `stack` | Stack name for stack rules |
| `concern` | Topic name such as `testing` or `security` |
| `priority` | `critical`, `high`, `medium`, or `low` |
| `always_apply` | Whether the rule should be loaded first |
| `applies_to` | Task types such as implementation, review, testing, e2e |
| `signals` | File or code patterns used for selection |
| `related_rules` | Extra rules to load together |

### Contribution guide

When adding or editing rules:

1. Choose `stacks/` or `concerns/` first.
2. Keep the rule atomic.
3. Add complete frontmatter metadata.
4. Use short English markdown.
5. Update `meta/stack-map.json` if a new stack is introduced.

## 中文

`standards-repo` 是 `stackwise` 使用的中央规范真相源。

业务项目不应该各自长期维护一份共享规范副本，而应该通过 `stackwise` 从这个仓库按需同步规则到本地 `.standards/`。

### 目标

- 在一个地方集中维护技术栈规范
- 在一个地方集中维护横切 concern
- 通过 metadata 驱动规则选择
- 让业务项目只同步自己需要的部分

### 目录结构

```text
standards-repo/
|- stacks/      # 框架、库、工具规则
|- concerns/    # 测试、性能、构建、安全等横切规则
`- meta/        # 映射关系与默认选择元数据
```

### 同步模型

1. `stackwise` 从业务项目中检测技术栈。
2. 将匹配的 `stacks/` 规则复制到 `.standards/stacks/`。
3. 将默认 `concerns/` 规则复制到 `.standards/concerns/`。
4. 将 metadata 写入 `.standards/active-rules.json`。

### 规则设计原则

- 一个文件只表达一个主题
- Markdown 保持简短，适合本地 AI 上下文
- 每个规则文件都带稳定 frontmatter metadata
- 技术栈规则和横切规则分开维护

### Frontmatter 示例

```md
---
id: react/component-structure
title: React Component Structure
type: stack
stack: react
concern: structure
priority: high
always_apply: true
applies_to:
  - implementation
  - review
signals:
  - .tsx
  - component
related_rules:
  - react/hooks
---
```

### Metadata 字段说明

| 字段 | 含义 |
| --- | --- |
| `id` | 稳定规则标识 |
| `title` | 简短可读标题 |
| `type` | `stack` 或 `concern` |
| `stack` | 技术栈规则对应的栈名 |
| `concern` | 主题名，如 `testing`、`security` |
| `priority` | `critical`、`high`、`medium`、`low` |
| `always_apply` | 是否默认优先加载 |
| `applies_to` | 适用任务类型，如实现、评审、测试 |
| `signals` | 用于选择规则的文件或代码信号 |
| `related_rules` | 需要一起加载的其他规则 |

### 贡献说明

新增或修改规则时建议遵循：

1. 先确定放在 `stacks/` 还是 `concerns/`
2. 保持规则原子化
3. 补全 frontmatter metadata
4. 使用简短英文 Markdown
5. 若引入新技术栈，同时更新 `meta/stack-map.json`
