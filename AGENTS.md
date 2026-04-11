# Introduction

AGENTS.md is a centralized documentation file for Agentic coding agents operating within the `@involvex/prettier-config` repository. This file outlines project structure, setup instructions, and best practices to ensure consistency and efficiency.

## Overview

- Repository: `@involvex/prettier-config`
- Version: `0.0.5`
- Dependencies:
  - `prettier` (`3.8.2`)
  - `prettier-plugin-organize-imports`
  - `prettier-plugin-packagejson`
  - `prettier-plugin-sort-imports`
  - `prettier-plugin-markdown-html`
  - `prettier-plugin-yaml`
  - `prettier-plugin-toml`
  - `prettier-plugin-prisma`
  - `prettier-plugin-properties`

## Setup and Configuration

#### 1. Install Dependencies

Run the following command to install all required dependencies:

```bash
bun install
```

#### 2. Configure Prettier

Extend the `index.json` configuration file for project-specific Prettier settings.

#### 3. Linting and Testing

- Check code formatting: `bun run prettier-check`
- Format all files: `bun run prettier`
- Run tests: `bun test`

## Best Practices and Guidelines

#### 1. Code Style

- **Imports & Style**: Use `prettier-plugin-organize-imports` and `prettier-plugin-sort-imports` for automatic import organization and sorting.
- **Formatting**: Use Prettier with the following settings in `index.json`:
  - `"useTabs": true` - Use tabs for indentation
  - `"semi": false` - Omit semicolons
  - `"singleQuote": true` - Use single quotes for strings
  - `"quoteProps": "as-needed"` - Only quote object properties when necessary
  - `"bracketSpacing": false` - No spaces inside object brackets
  - `"arrowParens": "avoid"` - No parentheses around single arrow function parameters
  - `"trailingComma": "all"` - Add trailing commas in multi-line objects and arrays
- **Types**: Use TypeScript where applicable. Prefer interfaces over types for public APIs.
- \*\*Naming Conventions":
  - camelCase for variables and functions
  - PascalCase for types, interfaces, and classes
  - snake_case for package.json keys and configuration files
  - UPPER_CASE for constants

#### 2. Error Handling

Implement try-catch blocks for error handling and logging. Aim for informative error messages without exposing sensitive information. Use consistent error types like Error or custom Error subclasses.

#### 3. Documentation

Maintain clear, concise documentation. Use Markdown for readability and include relevant sections (e.g., Introduction, Usage, Contributing). Annotate all exported functions and configurations.

## Security Considerations

Ensure that no sensitive files are committed to the repository. Utilize `.gitignore` to exclude unnecessary files and secure configuration data. Never commit authentication credentials or private keys.

## AGENTS.md Update

To update `AGENTS.md`, maintain the specified structure and ensure all relevant information is included. This file should be kept up-to-date to facilitate efficient collaboration among agents and the community.
