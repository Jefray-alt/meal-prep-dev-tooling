# mise — Meal Prep Stack

An AI-assisted meal-prep planner. Monorepo containing a React 19 frontend (`meal-prep/`) and a NestJS 11 API (`meal-prep-api/`).

---

## Feature Development Workflow

Every feature follows three steps before a line of implementation code is written.

### 1. `/idea-to-prd` — Shape the idea

Start here when you have a rough concept. The skill interviews you until the idea is well-defined, then publishes a formatted PRD as a GitHub issue with a `prd` label.

```
/idea-to-prd
```

**Output:** a GitHub issue with a clear problem statement, goals, non-goals, and success criteria.

---

### 2. `/spec` — Turn the PRD into a spec

Run this with the issue number once the PRD is merged/approved. It reads the issue and produces a skeleton spec you refine before writing any code.

```
/spec <issue-number>
```

**Output:** a filled-in spec file committed next to the code it describes (`specs/issue-N-*.md`).

---

### 3. `/spec-fe` or `/spec-be` — Write the implementation spec

After the high-level spec is agreed on, generate a detailed implementation spec for the layer you are about to build. Use both if the feature spans the stack.

```
/spec-be <issue-number>   # → meal-prep-api/specs/issue-N-backend.md
/spec-fe <issue-number>   # → meal-prep/specs/issue-N-frontend.md
```

The backend spec covers API contract, data model changes, business logic, and test cases (see `specs/_templates/backend.md`).

The frontend spec covers user flows, error states, components, and test cases (see `specs/_templates/frontend.md`). It links to the backend spec rather than duplicating endpoint definitions.

**Output:** a complete, reviewable spec ready for implementation.

---

## Monorepo Layout

| Directory | Purpose |
|-----------|---------|
| `meal-prep/` | React 19 / Vite frontend |
| `meal-prep-api/` | NestJS 11 REST API |
| `specs/_templates/` | Spec templates (`backend.md`, `frontend.md`) |

See `CLAUDE.md` for commands, architecture details, and conventions.
