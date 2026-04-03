# AGENTS.md

## Project Structure

Excalidraw is a **monorepo** with a clear separation between the core library and the application:

- **`packages/excalidraw/`** - Main React component library published to npm as `@excalidraw/excalidraw`
- **`excalidraw-app/`** - Full-featured web application (excalidraw.com) that uses the library
- **`packages/`** - Core packages: `@excalidraw/common`, `@excalidraw/element`, `@excalidraw/math`, `@excalidraw/utils`
- **`examples/`** - Integration examples (NextJS, browser script)

## Development Workflow

1. **Package Development**: Work in `packages/*` for editor features
2. **App Development**: Work in `excalidraw-app/` for app-specific features
3. **Testing**: Always run `yarn test:update` before committing
4. **Type Safety**: Use `yarn test:typecheck` to verify TypeScript

## Development Commands

```bash
yarn test:typecheck  # TypeScript type checking
yarn test:update     # Run all tests (with snapshot updates)
yarn fix             # Auto-fix formatting and linting issues
```

## Architecture Notes

### Package System

- Uses Yarn workspaces for monorepo management
- Internal packages use path aliases (see `vitest.config.mts`)
- Build system uses esbuild for packages, Vite for the app
- TypeScript throughout with strict configuration

## Rules & Memory

### Cursor Rules

`.cursor/rules/` — правила для AI-агентів у форматі `.mdc`:

- `architecture.mdc` — архітектурні обмеження (state management, rendering, залежності)
- `conventions.mdc` — конвенції коду (компоненти, TypeScript, файли)
- `do-not-touch.mdc` — захищені файли, які не можна змінювати без явного дозволу
- `action-registration.mdc` — паттерн реєстрації actions через `register()`
- `branded-types.mdc` — branded types для типобезпечних примітивів
- `jotai-isolation.mdc` — ізольований імпорт Jotai через `editor-jotai`
- `batched-updates.mdc` — batched/throttled обгортки для event handlers

### Memory Bank

Проєкт використовує persistent memory bank для Claude Code. Файли зберігаються у `.claude/projects/` і містять контекст між сесіями: інформацію про користувача, зворотний зв'язок, проєктні рішення та посилання на зовнішні ресурси. Індекс — `MEMORY.md`.
