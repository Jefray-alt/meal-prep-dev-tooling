# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Workspace layout

| Directory | Purpose |
|-----------|---------|
| `~/meal-prep/` | React 19 / Vite frontend ("mise") — has its own `CLAUDE.md` |
| `~/meal-prep-api/` | NestJS 11 REST API — scaffold stage, growing feature-by-feature |
| `specs/_templates/` | Markdown templates (`frontend.md`, `backend.md`) for writing feature specs |

Each sub-project is its own git repo. Always `cd` into the correct directory before running package scripts.

## API commands (~/meal-prep-api/)

```bash
npm run start:dev   # watch mode
npm run build       # compile to dist/
npm run lint        # ESLint + Prettier (auto-fixes)
npm run test        # Jest unit tests (*.spec.ts in src/)
npm run test:e2e    # Jest e2e tests (test/*.e2e-spec.ts)
npm run test:cov    # coverage report
```

Single test file: `npx jest src/path/to/file.spec.ts` from inside `~/meal-prep-api/`.

## Frontend commands (~/meal-prep/)

See `~/meal-prep/CLAUDE.md` for the full breakdown. Quick reference:

```bash
npm run dev         # Vite dev server
npm run test        # Vitest watch
npm run test:run    # Vitest single run
npm run lint -- --fix  # auto-fix ESLint/perfectionist ordering
```

## Architecture

**App name:** mise — an AI-assisted meal-prep planner.

**State pattern:** Pages (`src/pages/`) own all state; components (`src/components/`) are purely presentational. Validation logic lives in the page file alongside the page component (`validate()` in `Create.tsx`).

**API:** NestJS app on port 3000 (env `PORT` overrides). Currently only the generated AppModule scaffold — no domain modules yet.

## Spec workflow

Before implementing a feature, create specs from the templates in `specs/_templates/`:
- `backend.md` — API contract, data model changes, business logic
- `frontend.md` — user flows, error states, API calls consumed

Specs live next to the code they describe (e.g. `~/meal-prep-api/specs/issue-N-backend.md`).
