---
# Required: stable identifier in the form "<stack>/<filename-without-extension>".
# Never change this after the rule is merged — downstream projects depend on it.
id: <stack>/<rule-name>

# Required: short human-readable title (Title Case).
title: <Short Readable Title>

# Required: "stack" for files under stacks/, "concern" for files under concerns/.
type: stack

# Required for type: stack — the stack folder name (must match the directory).
stack: <stack-name>

# Required: the concern this rule addresses. Free-form, but prefer a value
# that already appears in concerns/ (e.g. structure, hooks, performance,
# security, testing, build).
concern: <topic>

# Required: critical | high | medium | low.
#   critical → must follow; violation causes bugs or security issues
#   high     → strong best practice; follow unless there is a clear reason not to
#   medium   → recommended; project-specific trade-offs are acceptable
#   low      → advisory; improves code quality but not always applicable
priority: high

# Required: true → loaded into the always-on rule slice; false → loaded only
# when a `signals:` match is hit. Use `true` sparingly; the always-on slice
# has a hard token budget.
always_apply: true

# Required: which pipeline phases should consume this rule.
# Allowed values: implementation, review, testing, e2e
applies_to:
  - implementation
  - review

# Optional but recommended: file extensions or code keywords that should
# pull this rule into context. Used by code-writer / code-reviewer when the
# rule is not always_apply.
signals:
  - .tsx
  - <keyword-or-symbol>

# Optional: other rule ids the reader should consult alongside this one.
related_rules:
  - <stack>/<other-rule>
---

# <Title>

## When to read

One short paragraph describing when this rule should be pulled into the
working context. Avoid restating what the rule says — that goes in the
sections below.

## Core rules

- One bullet per rule. Keep each line under ~120 characters.
- Prefer concrete prescriptions ("do X", "avoid Y") over abstract guidance.
- Cite the affected file shape, hook, or API by name where relevant.

## Anti-patterns

- One bullet per common mistake. Pair it with the correct alternative if it
  is not obvious from the Core rules.

## Example

```ts
// A short, self-contained example. Aim for under 25 lines.
// One good example beats three half-examples.
```

## See also

- `<stack>/<related-rule>` — one-line reason to read it next.
