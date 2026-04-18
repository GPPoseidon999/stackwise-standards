# Changelog

All notable changes to `stackwise-standards` are documented in this file.

The format is loosely based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
This file is synced into product repositories at `agents/rules/CHANGELOG.md` by
`stackwise sync`, so consumers can see what changed since their last sync.

---

## [Unreleased]

### Added
- `_templates/stack-rule.md` and `_templates/concern-rule.md` — copy-paste skeletons
  for new rule files. Files prefixed with `_` are treated as templates and are
  excluded from the active-rules manifest by `stackwise sync`.
- `CHANGELOG.md` — this file. Tracks repository-wide changes between syncs.

### Changed
- `meta/stack-map.json` — added missing package-name aliases to match
  `stackwise-cli`'s detector (`shadcn-ui`, `@ant-design/react`,
  `react-router`, `apollo-client`, `apollo-cache-inmemory`, `apollo-link-http`,
  `decimal.js`, `bn.js`).
- README and CONTRIBUTING — refreshed to describe the v2.7 layout
  (`agents/rules/` instead of `.standards/`).

---

## [0.1.0] — initial public layout

### Added
- `stacks/` — 58 stacks covering frontend frameworks, state, data fetching,
  forms, validation, styling, charts, web3, testing, build, routing,
  utilities, backend frameworks, and ORMs.
- `concerns/` — `security`, `testing`, `performance`, `build` (13 cross-cutting
  rule files).
- `meta/stack-map.json` — npm package → stack folder mapping.
- `meta/default-concerns.json` — concerns enabled by default for all projects.
- `README.md`, `CONTRIBUTING.md` — bilingual (English + 中文) docs.
