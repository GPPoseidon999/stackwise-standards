# stackwise-standards

[English](#english) | [中文](#中文)

## English

`stackwise-standards` is the central rule repository for [stackwise](https://github.com/GPPoseidon999/stackwise).

Product repositories should not keep long-lived copies of shared rules. Instead, `stackwise` syncs a project-specific subset from this repository into a local `.standards/` directory.

### How it works

1. `stackwise` detects stacks from a product repo's `package.json`.
2. Matching `stacks/` rules are copied into `.standards/stacks/`.
3. Default `concerns/` rules are copied into `.standards/concerns/`.
4. Metadata is written to `.standards/active-rules.json`.

### Structure

```text
stackwise-standards/
|- stacks/      # Framework, library, and tool rules
|- concerns/    # Testing, performance, build, security, etc.
`- meta/        # Mapping and default selection metadata
```

### Using a custom standards repository

Any team can fork this repository and maintain their own private rule set. Point `stackwise` at it with a single config change:

```json
{
  "standards_repo": "https://github.com/your-org/your-standards",
  "branch": "main"
}
```

### Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the full guide on adding stacks, rules, and concerns.

### Current stacks

**Frontend:** react, nextjs, vue, nuxt, typescript, tailwind, styled-components, shadcn, mui, antd, radix, framer-motion

**State management:** redux-toolkit, zustand, jotai, recoil, mobx, immer

**Data fetching:** react-query, swr, axios, ky, graphql, apollo

**Forms & validation:** react-hook-form, formik, zod, yup

**Routing:** react-router

**Backend:** express, fastify, koa, nestjs

**Database / ORM:** prisma, drizzle, typeorm, mongoose

**Testing:** jest, vitest, playwright, cypress

**Build:** vite, turbopack

**Charts & data viz:** echarts, chartjs, d3, recharts, tanstack-table, virtualization

**Date & utility:** date-fns, dayjs, lodash

**Web3 / DeFi:** ethers, web3, web3-react, wagmi, viem, bignumber

**Cross-cutting concerns:** testing, performance, build, security

### License

MIT

---

## 中文

`stackwise-standards` 是 [stackwise](https://github.com/GPPoseidon999/stackwise) 的中央规范仓库。

业务项目不应该各自长期维护一份共享规范副本，而应该通过 `stackwise` 从这个仓库按需同步规则到本地 `.standards/` 目录。

### 工作原理

1. `stackwise` 从业务项目的 `package.json` 中检测技术栈。
2. 将匹配的 `stacks/` 规则复制到 `.standards/stacks/`。
3. 将默认 `concerns/` 规则复制到 `.standards/concerns/`。
4. 将 metadata 写入 `.standards/active-rules.json`。

### 目录结构

```text
stackwise-standards/
|- stacks/      # 框架、库、工具规则
|- concerns/    # 测试、性能、构建、安全等横切规则
`- meta/        # 映射关系与默认选择元数据
```

### 使用私有规范仓库

任何团队都可以 fork 这个仓库，维护自己的私有规范。只需修改一行配置，指向你们自己的仓库：

```json
{
  "standards_repo": "https://github.com/your-org/your-standards",
  "branch": "main"
}
```

### 贡献规范

贡献新规则、新技术栈或新 concern 的完整指南，请参阅 [CONTRIBUTING.md](./CONTRIBUTING.md)。

### 协议

MIT
