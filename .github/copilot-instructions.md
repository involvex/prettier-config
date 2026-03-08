# Copilot instructions for @involvex/prettier-config

Purpose

- Short, focused guidance for Copilot-powered sessions working on this repository: commands, project shape, and repository-specific conventions.

Quick commands (what exists and how to run them)

- Install dependencies: `npm install` (also `bun install` listed in docs).
- Prettier (format / check):
  - Check formatting: `npx prettier --check .`
  - Format repository: `npx prettier --write .`
- npm scripts: `package.json` contains only `"test": "true"` (placeholder). There are no lint or build scripts configured.
- Tests: `npm run test` exists but is a placeholder (returns `true`). There is no test runner configured in this repo. To run a single test you must add a test runner (examples):
  - Vitest: `npx vitest run path/to/test.spec.ts`
  - Jest: `npx jest path/to/test.spec.js`
    (these are examples — the repo currently has none).

High-level architecture (big picture)

- This repository is a single-purpose, sharable Prettier configuration package.
  - The package `main` is `index.json` and `files` publishes `index.json` only — the package is a configuration artifact, not an application.
  - `index.json` is the canonical Prettier configuration (rules + listed plugins).
  - Plugins configured in `index.json` are listed as dependencies in `package.json` so consumers using this package get the plugin behavior.
- Typical consumer usage:
  - Install: `npm i --save-dev @involvex/prettier-config`
  - Point Prettier at this package in the consumer `package.json`: `"prettier": "@involvex/prettier-config"` (or reference the shipped `index.json` directly during development).
- Package constraints to be aware of:
  - `peerDependencies` requires `prettier@>=3.0.0` — ensure the consumer Prettier version satisfies this.
  - The repo’s `files`/`main` are intentionally minimal so publishing should keep index.json as the exported artifact.

Key repository conventions (repo-specific, not general best-practices)

- Prettier configuration (index.json):
  - `useTabs: true` — tabs for indentation
  - `semi: false` — no semicolons
  - `singleQuote: true`
  - `quoteProps: "as-needed"`
  - `bracketSpacing: false`
  - `arrowParens: "avoid"`
  - `trailingComma: "all"`
- Plugins used and their roles (declared in index.json + package.json):
  - `prettier-plugin-organize-imports` — organizes imports
  - `prettier-plugin-packagejson` — sorts/normalizes package.json
  - `prettier-plugin-sort-imports` — sorts imports
- Naming / style conventions documented here are authoritative for code and config in this org (see AGENTS.md / GEMINI.md):
  - Variables & functions: `camelCase`
  - Types / interfaces / classes: `PascalCase`
  - Package/config keys (where used): `snake_case`
  - Constants: `UPPER_CASE`
- Change-scope guidance (for PRs):
  - Primary edits should be to `index.json` and, if needed, `package.json` metadata (e.g., bump version, adjust dependencies). Avoid adding runtime code — this repo is a config package.
  - If adding or removing plugins in `index.json`, also update `package.json` dependencies and verify peerDependency compatibility.

Files and docs to consult (most relevant)

- `index.json` — canonical Prettier config (single source of truth)
- `package.json` — package metadata, dependencies, scripts (note: `test` is a placeholder)
- `readme.md` — install / usage snippet for consumers
- `AGENTS.md` and `GEMINI.md` — repo-specific conventions and guidance; read for naming conventions and recommended commands

PR checklist (suggested minimal steps for contributors)

- Update `index.json` for formatting changes.
- If plugins were added/removed, update `package.json` dependencies accordingly.
- Run `npx prettier --check .` and fix formatting (`npx prettier --write .`).
- Bump `package.json` version appropriately for published config changes.
- Update `AGENTS.md` / repo docs if conventions or plugin sets change.

Notes for Copilot sessions

- When suggesting edits, prefer minimal changes to `index.json` and `package.json` rather than adding new source files.
- Use `AGENTS.md` and `GEMINI.md` as authoritative references for style choices and for commands mentioned in PR descriptions.
- There is no test framework configured — any test-related suggestions should include adding and wiring an explicit test runner.

(End of file)
