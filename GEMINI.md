# GEMINI.md

## Project Overview

`@involvex/prettier-config` is a shared [Prettier](https://prettier.io) configuration package used across `involvex` projects. It provides a consistent code style and leverages several plugins to automate formatting tasks like import organization and `package.json` sorting.

- **Main Configuration:** `index.json`
- **Key Plugins:**
  - `prettier-plugin-organize-imports`: Automatically organizes imports.
  - `prettier-plugin-packagejson`: Sorts and formats `package.json` files.
  - `prettier-plugin-sort-imports`: Sorts imports according to defined rules.

## Building and Running

The project is a static configuration package and does not require a build step.

### Key Commands:

- **Install Dependencies:** `npm install` or `bun install`.
- **Test:** `npm run test` (currently returns `true`, acting as a placeholder).
- **Format Code:** Use `npx prettier --write .` to format the repository itself.
- **Check Formatting:** Use `npx prettier --check .` to verify formatting.

## Development Conventions

This project enforces a specific set of stylistic rules defined in `index.json`:

### Formatting Rules:

- **Indentation:** Always use tabs (`useTabs: true`).
- **Semicolons:** No semicolons at the end of statements (`semi: false`).
- **Quotes:** Use single quotes for strings (`singleQuote: true`).
- **Trailing Commas:** Use trailing commas wherever possible (`trailingComma: "all"`).
- **Brackets:** No spaces inside object brackets (`bracketSpacing: false`).
- **Arrow Functions:** Avoid parentheses around single parameters (`arrowParens: "avoid"`).

### Naming & Style (per `AGENTS.md`):

- **Variables & Functions:** `camelCase`
- **Types, Interfaces & Classes:** `PascalCase`
- **Constants:** `UPPER_CASE`
- **Config Keys:** `snake_case` (where appropriate for configuration files)

## Project Structure

- `index.json`: The core Prettier configuration exported by this package.
- `package.json`: Manifest file defining dependencies and package metadata.
- `AGENTS.md`: Detailed documentation and best practices for AI agents working on this repo.
- `readme.md`: General overview and installation instructions.
