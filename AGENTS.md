<!-- nx configuration start-->
<!-- Leave the start & end comments to automatically receive updates. -->

# General Guidelines for working with Nx

- For navigating/exploring the workspace, invoke the `nx-workspace` skill first - it has patterns for querying projects, targets, and dependencies
- When running tasks (for example build, lint, test, e2e, etc.), always prefer running the task through `nx` (i.e. `nx run`, `nx run-many`, `nx affected`) instead of using the underlying tooling directly
- Prefix nx commands with `bunx` (e.g., `bunx nx build @org/api`) - this repo uses Bun
- You have access to the Nx MCP server and its tools, use them to help the user
- For Nx plugin best practices, check `node_modules/@nx/<plugin>/PLUGIN.md`. Not all plugins have this file - proceed without it if unavailable.
- NEVER guess CLI flags - always check nx_docs or `--help` first when unsure

## Scaffolding & Generators

- For scaffolding tasks (creating apps, libs, project structure, setup), ALWAYS invoke the `nx-generate` skill FIRST before exploring or calling MCP tools

## When to use nx_docs

- USE for: advanced config options, unfamiliar flags, migration guides, plugin configuration, edge cases
- DON'T USE for: basic generator syntax (`nx g @nx/react:app`), standard commands, things you already know
- The `nx-generate` skill handles generator discovery internally - don't call nx_docs just to look up generator syntax

<!-- nx configuration end-->

# Repo-specific guidance

## Package manager

- **Bun** — lockfile is `bun.lock`, always use `bunx nx <target>` or `bunx nx run-many ...`
- Install: `bun install --frozen-lockfile`
- `.npmrc` has `shamefully-hoist=true` (needed for Astro deps)

## Projects

| Name           | Path               | Stack                                        | Target config location  | Entrypoint                    |
| -------------- | ------------------ | -------------------------------------------- | ----------------------- | ----------------------------- |
| `@org/web`     | `apps/web/`        | Next.js 16 (App Router) + Tailwind CSS       | inferred (nx plugin)   | `src/app/layout.tsx`          |
| `@org/api`     | `apps/api/`        | NestJS 11 (webpack / tsc)                    | `package.json` nx.*    | `src/main.ts`                 |
| `@org/api-e2e` | `apps/api-e2e/`    | Jest (e2e)                                   | `package.json` nx.*    | `src/api/api.spec.ts`         |
| `@org/astro-site` | `apps/astro-site/` | Astro 4 + React                              | `project.json`          | `src/pages/`                  |
| `@org/ui`      | `packages/ui/`     | React component lib (shadcn)                  | inferred (nx plugin)   | `src/index.ts`                |

## Path aliases

- `@org/web` has `@/*` → `./src/*` (local alias in its `tsconfig.json`)
- `@org/ui` → `packages/ui/src`, `@org/ui/*` → `packages/ui/src/*`
- All defined in `tsconfig.base.json` except `@/*` (app-local)

## Commands

| Action               | Command                                                |
| -------------------- | ------------------------------------------------------ |
| Dev server (web)     | `bunx nx dev @org/web`                                 |
| Dev server (astro)   | `bunx nx dev astro-site`                          |
| Serve API            | `bunx nx serve @org/api` (builds then serves via node) |
| Build project        | `bunx nx build <project>`                              |
| Lint                 | `bunx nx eslint:lint <project>`                        |
| Typecheck            | `bunx nx typecheck <project>`                          |
| Test                 | `bunx nx test <project>`                               |
| E2E                  | `bunx nx e2e @org/api-e2e`                             |
| Astro check          | `bunx nx check astro-site`                        |
| Full CI locally      | `bunx nx run-many -t lint test build typecheck e2e-ci` |
| Add shadcn component  | `bunx --bun shadcn@latest add <component> -c apps/web` |
| Format check         | `bunx nx format:check`                                 |
| Format write         | `bunx nx format:write`                                 |
| Graph                | `bunx nx graph`                                        |

## Architecture notes

- **Web app** proxies to API — the NestJS API at `/api` prefix serves the backend
- **`@org/api`** targets (`build`, `serve`, `prune`) are defined in `package.json` under `nx.targets`, not a `project.json`
- **`@org/astro-site`** is the `defaultProject` in `nx.json`; uses `@nxtensions/astro` plugin
- **`@org/ui`** is a shared shadcn component library. Add components via `bunx --bun shadcn@latest add <component> -c apps/web`. The CLI reads `apps/web/components.json` and `packages/ui/components.json` to install shared components into `packages/ui/src/components/` and app-specific files into `apps/web/src/components/`
- **Tailwind CSS v4** is used (CSS-first config, no `tailwind.config.js`). The shadcn theme CSS variables are defined in `apps/web/src/app/global.css` (Next.js) and `apps/astro-site/src/styles/global.css` (Astro), and `packages/ui/src/styles/globals.css` (CLI reference)
- **`astro-site:build`** has a pre-existing failure (Bun + Astro module loader compat issue); `astro check` passes with 0 errors
- **`DESIGN.md`** defines the brand design system ("Kindred Motion") with color tokens, typography, spacing, and component patterns
- No `jest.preset.js` exists in the repo root — `@org/api-e2e`'s `jest.config.cts` references it, which may fail. The e2e target depends on `@org/api:build` + `@org/api:serve` (runs via `@nx/jest:jest`)
- Lint uses Nx ESLint flat config with `@nx/enforce-module-boundaries`
- Prettier uses `singleQuote: true`
- Nx Cloud is connected (`nxCloudId` in `nx.json`) — self-healing CI is available
- Custom skills under `.opencode/skills/` and `.github/skills/` (monitor-ci, nx-workspace, nx-generate, link-workspace-packages, etc.)
