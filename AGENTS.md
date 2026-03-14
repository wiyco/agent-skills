# AGENTS.md

This file provides guidance to agents (Claude Code, Gemini, Codex) when working with code in this repository.

<!-- Shared via symbolic links: AGENTS.md => CLAUDE.md, GEMINI.md -->

## Commands

```bash
npm run typecheck        # tsgo -b
npm run dev              # Start development server (port 3000)
npm run build            # Production build (tsgo -b + vite build)
npm run lint             # ESLint check (0 warnings required)
npm run lint:fix         # ESLint auto-fix
npx eslint src/path/to/file.ts --fix  # Individual ESLint auto-fix
npm run format           # Prettier check
npm run format:fix       # Prettier auto-fix
npx prettier src/path/to/file.ts --write # Individual Prettier auto-fix
npm run check:fix        # Auto-fix Lint + Format (run before committing)

npm run test             # Run all tests (Vitest)
npm run test:unit        # Unit tests only
npx vitest run src/path/to/file.test.ts # Run individual unit test
npm run test:unit:watch  # Unit tests watch mode
npm run test:coverage    # Unit tests with coverage
npm run test:integration # Integration tests (Vitest + RTL + MSW)
npm run test:e2e         # E2E tests (Playwright)
# Always specify reporter for E2E tests
npm run test:e2e -- src/routes/settings/settings.spec.ts --reporter=line
```

## Architecture

SPA

### Routing

### API Client

### Data Fetching

### State Management

### Authentication

### Path Aliases

Configured in both `vite.config.ts` and `tsconfig.app.json`.

- `~assets/*`
- `~components/*`
- `~lib/*`
- `~routes/*`
- `~constants/*`
- `~types/*`
- `~tests/*`

## Testing

| Type        | Location                      | File Naming       | Tools              |
| ----------- | ----------------------------- | ----------------- | ------------------ |
| Unit        | `src/` (same as target file)  | `*.test.{ts,tsx}` | Vitest             |
| Integration | `tests/integration/`          | `*.test.{ts,tsx}` | Vitest + RTL + MSW |
| E2E         | `tests/e2e/`                  | `*.spec.{ts,tsx}` | Playwright         |

## Code Style

- Use functional components + Hooks.
- React Compiler (babel) is enabled. Follow immutability and purity rules.
- Type assertions and the use of the `any` type are prohibited. Use appropriate type definitions or type guards to maintain type safety.

## Design Rules

- Use Tailwind CSS and only apply colors defined in the Tailwind configuration. Always confirm before applying custom colors.
- Dark mode colors are applied automatically. The color palette is defined in `src/styles/global.css`.
- Use the `cn()` function for dynamic or long classNames.
- Do not apply duplicate color classes that are already applied by default. Keep class additions to a minimum.
- Support SP (mobile) responsive layouts whenever possible.

## Principles

- Naming convention: Use kebab-case.
- Async: Use `async/await` rather than Promise chains.
- UI Components: Compound pattern is recommended.
- Component Structure: Create a directory named after the component and export it via index.
- Coding: Always verify facts for unclear requirements or specifications. Do not implement based on speculation. Review designs with attention to maintainability and readability.

## Guidelines

### Commits

- Do not mix refactoring with new features or fixes in the same commit.
- Split commits when changes to nested structures result in large diffs.
- Commit messages must follow the Conventional Commits specification.

### PRs

- Suggest splitting into a separate PR if the implementation diff exceeds 1000 lines.
- Minimize changes to existing implementations to avoid regressions.

### Review

- Prompt for verification of behavior in SP (mobile) and dark mode.

## Knowledge

Refer to `.md` files in `docs/` for other domain knowledge.
