---
# Required: stable identifier in the form "<concern>/<filename-without-extension>".
# Never change this after the rule is merged — downstream projects depend on it.
id: <concern>/<rule-name>

# Required: short human-readable title (Title Case).
title: <Short Readable Title>

# Required: "concern" for files under concerns/.
type: concern

# Required: the concern category — must match the directory name under
# concerns/ (e.g. security, testing, performance, build).
concern: <concern>

# Required: critical | high | medium | low.
#   critical → must follow; violation causes bugs or security issues
#   high     → strong best practice; follow unless there is a clear reason not to
#   medium   → recommended; project-specific trade-offs are acceptable
#   low      → advisory; improves code quality but not always applicable
priority: high

# Required: true → loaded into the always-on rule slice; false → loaded only
# when a `signals:` match is hit. Cross-cutting concerns are usually
# always_apply: true, but use judgment — every always-on rule eats budget.
always_apply: true

# Required: which pipeline phases should consume this rule.
# Allowed values: implementation, review, testing, e2e
applies_to:
  - implementation
  - review
  - testing

# Optional but recommended: file extensions, function calls, or symbols
# that suggest this rule applies. Used to pull the rule into context on
# demand for non-always_apply concerns.
signals:
  - <keyword-or-symbol>
  - <api-or-pattern>

# Optional: other rule ids the reader should consult alongside this one.
# Cross-stack references are encouraged for concerns (e.g. security/input-validation
# linking to zod/schema-design).
related_rules:
  - <stack>/<rule>
  - <concern>/<rule>
---

# <Title>

## When to read

One short paragraph describing when this concern is in scope. Concern rules
should be readable without knowledge of any specific stack.

## Core rules

- One bullet per rule. State the constraint, not the reason.
- Prefer concrete prescriptions ("validate at the boundary", "never log
  secrets") over abstract guidance.

## Anti-patterns

- One bullet per common mistake, paired with the correct alternative.

## Example

```ts
// A short, framework-agnostic example. If a stack-specific example is
// needed, link to the matching stack rule in `related_rules` above
// instead of inlining it here.
```

## See also

- `<concern>/<related-rule>` — one-line reason to read it next.
- `<stack>/<related-rule>` — stack-specific application of this concern.
