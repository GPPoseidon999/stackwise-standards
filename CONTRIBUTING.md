# Contributing to stackwise-standards

[English](#english) | [中文](#中文)

## English

`stackwise-standards` is the central rule repository for [stackwise](https://github.com/GPPoseidon999/stackwise). All engineers are welcome to contribute new stack rules or improve existing ones.

### Repository layout

```text
stackwise-standards/
|- stacks/        # One folder per framework / library / tool
|- concerns/      # Cross-cutting rules: testing, performance, build, security, …
|- meta/          # stack-map.json and default-concerns.json
|- _templates/    # Copy-paste skeletons for new rules (not synced to product repos)
`- CHANGELOG.md   # Synced to agents/rules/CHANGELOG.md by stackwise sync
```

> Any file or directory whose name starts with `_` is treated as a template
> and is excluded from the active-rules manifest by `stackwise sync`.

### Adding a rule to an existing stack

1. Find the folder under `stacks/<stack-name>/` or `concerns/<concern-name>/`.
2. Copy `_templates/stack-rule.md` (or `_templates/concern-rule.md`) and rename
   it to a focused, single-topic filename (e.g. `error-handling.md`).
3. Fill in the YAML frontmatter completely. Every required field is listed in
   the template as a commented `# Required:` hint.
4. Write the rule body in short English markdown — aim for under 60 lines.
5. Add a bullet to the `[Unreleased]` section of `CHANGELOG.md`.
6. Open a pull request with a title like `feat(react): add error-handling rule`.

### Adding a new stack

1. Create `stacks/<new-stack>/` and add at least one `.md` rule file.
2. Add the npm package → stack name mapping to `meta/stack-map.json`.
3. Open a pull request with a title like `feat: add <new-stack> stack`.

### Adding a new concern

1. Create `concerns/<new-concern>/` and add at least one `.md` rule file.
2. If this concern should be enabled by default for all projects, add it to `meta/default-concerns.json`.
3. Open a pull request with a title like `feat(concerns): add <new-concern>`.

### Frontmatter template

Every rule file must begin with YAML frontmatter:

```yaml
---
id: <stack>/<filename-without-extension>
title: Short Readable Title
type: stack          # "stack" or "concern"
stack: <stack-name>  # only for type: stack
concern: <topic>     # the concern name this rule addresses
priority: high       # critical | high | medium | low
always_apply: true   # true = always load this rule first
applies_to:
  - implementation   # implementation | review | testing | e2e
signals:
  - .tsx             # file extension or code keyword that triggers this rule
related_rules:
  - <stack>/<other-rule>
---
```

### Rule writing guidelines

- **One file, one topic.** Do not combine unrelated rules in a single file.
- **Short and concrete.** Prefer one good example over a long prose explanation.
- **English only.** All rule files must be written in English for broad usability.
- **No vendor lock-in.** Rules should describe best practices, not enforce a specific tooling setup.
- **Stable IDs.** Never change the `id` field after a rule is merged — downstream projects depend on it.

### Priority guide

| Priority | Meaning |
| --- | --- |
| `critical` | Must follow; violation causes bugs or security issues |
| `high` | Strong best practice; follow unless there is a clear reason not to |
| `medium` | Recommended; project-specific trade-offs are acceptable |
| `low` | Advisory; improves code quality but not always applicable |

### Pull request checklist

- [ ] Frontmatter is complete and valid
- [ ] Rule body is in English
- [ ] File is placed in the correct `stacks/` or `concerns/` folder
- [ ] `meta/stack-map.json` updated if a new stack is introduced
- [ ] `meta/default-concerns.json` updated if a new default concern is added
- [ ] Rule is atomic (one topic per file)

---

## 中文

`stackwise-standards` 是 [stackwise](https://github.com/GPPoseidon999/stackwise) 的中央规范仓库。欢迎所有工程师贡献新的技术栈规则或改进现有规则。

### 仓库结构

```text
stackwise-standards/
|- stacks/        # 每个框架 / 库 / 工具一个文件夹
|- concerns/      # 横切规则：测试、性能、构建、安全等
|- meta/          # stack-map.json 和 default-concerns.json
|- _templates/    # 新规则骨架（不会被同步到业务项目）
`- CHANGELOG.md   # 由 stackwise sync 同步为 agents/rules/CHANGELOG.md
```

> 任何以 `_` 开头命名的文件或目录都被视为模板，`stackwise sync` 不会把它写入 active-rules 清单。

### 为现有技术栈添加规则

1. 找到 `stacks/<stack-name>/` 或 `concerns/<concern-name>/` 下的对应文件夹。
2. 复制 `_templates/stack-rule.md`（或 `_templates/concern-rule.md`），重命名为
   聚焦单一主题的文件名（例如 `error-handling.md`）。
3. 按模板里的注释填满所有 `# Required:` 字段。
4. 规则正文用简短英文 Markdown 编写，尽量控制在 60 行以内。
5. 在 `CHANGELOG.md` 的 `[Unreleased]` 区块补一条记录。
6. 以 `feat(react): add error-handling rule` 这样的格式提交 PR。

### 添加新技术栈

1. 创建 `stacks/<new-stack>/` 并至少添加一个 `.md` 规则文件。
2. 在 `meta/stack-map.json` 中添加 npm 包名 → 技术栈名称的映射。
3. 以 `feat: add <new-stack> stack` 格式提交 PR。

### 添加新 Concern

1. 创建 `concerns/<new-concern>/` 并至少添加一个 `.md` 规则文件。
2. 如果该 concern 应该对所有项目默认启用，则将其加入 `meta/default-concerns.json`。
3. 以 `feat(concerns): add <new-concern>` 格式提交 PR。

### Frontmatter 模板

每个规则文件都必须以 YAML frontmatter 开头：

```yaml
---
id: <stack>/<filename-without-extension>
title: Short Readable Title
type: stack          # "stack" 或 "concern"
stack: <stack-name>  # 仅 type: stack 时填写
concern: <topic>     # 该规则所属的 concern 名称
priority: high       # critical | high | medium | low
always_apply: true   # true = 优先加载
applies_to:
  - implementation   # implementation | review | testing | e2e
signals:
  - .tsx             # 触发该规则的文件扩展名或代码关键词
related_rules:
  - <stack>/<other-rule>
---
```

### 规则编写原则

- **一个文件，一个主题。** 不要把不相关的规则合并到同一个文件。
- **简短具体。** 一个好的示例胜过长篇文字解释。
- **仅用英文。** 所有规则文件必须用英文编写，以便更广泛地使用。
- **不绑定特定工具。** 规则应该描述最佳实践，而不是强制要求特定的工具配置。
- **保持 ID 稳定。** 规则合并后不要修改 `id` 字段——下游项目依赖它。

### PR 检查清单

- [ ] Frontmatter 完整有效
- [ ] 规则正文使用英文
- [ ] 文件放在正确的 `stacks/` 或 `concerns/` 目录下
- [ ] 若引入新技术栈，已更新 `meta/stack-map.json`
- [ ] 若添加新默认 concern，已更新 `meta/default-concerns.json`
- [ ] 规则是原子化的（每个文件只有一个主题）
