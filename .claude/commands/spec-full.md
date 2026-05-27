$ARGUMENTS contains a spec reference followed by any optional extra context (e.g. "1", "add-pantry-filter", "1 use soft deletes on the API side").

Parse $ARGUMENTS: the **first word** is `SPEC_REF`; everything after is `USER_CONTEXT`.

Determine the file prefix from `SPEC_REF`:
- If `SPEC_REF` is **digits only** → `FILE_PREFIX = issue-$SPEC_REF`
- Otherwise → `FILE_PREFIX = $SPEC_REF` (it is already a slug)

---

**Step 1 — Read both specs:**

Read these files in parallel:
- `meal-prep-api/specs/$FILE_PREFIX-backend.md`
- `meal-prep/specs/$FILE_PREFIX-frontend.md`

If either file is missing, stop and tell the user which one is absent and what its expected path is, then ask them to run `/spec $SPEC_REF` to generate it.

---

**Step 2 — Post a combined implementation plan before touching any files:**

Print a concise plan in two sections:

**Backend (`meal-prep-api/`)**
- What this implements (business outcome from the spec Goal section)
- New NestJS artefacts — module(s), controller(s), service(s), DTO(s), entity/migration
- API endpoints being added (method + path)
- Test files to be created

**Frontend (`meal-prep/`)**
- New or modified routes and the page-level component(s) that own them
- New or modified presentational components
- API calls made and how errors are surfaced to the user
- State — local or any shared store slices touched

**Extra** (if USER_CONTEXT is non-empty): How you will honour the user's extra instructions

**Open questions**: Any ambiguities in either spec — ask them one by one.

Stop here and wait for the user to confirm ("yes", "go ahead", "lgtm", or similar) before writing any files. If there are open questions, iterate until resolved.

If only one spec file exists (e.g. the feature has no backend changes), proceed with just the frontend section and skip the backend implementation steps.

---

**Step 3 — Implement backend first (after confirmation):**

All work is scoped to `meal-prep-api/`. Read `meal-prep-api/CLAUDE.md` and the root `CLAUDE.md` for project conventions, and scan the existing source to match established patterns before writing code.

After writing all backend files, run lint and tests from `meal-prep-api/` and fix any failures. Print the relative paths of every file created or modified.

---

**Step 4 — Implement frontend:**

All work is scoped to `meal-prep/`. Read `meal-prep/CLAUDE.md` and the root `CLAUDE.md` for project conventions, and scan the existing source to match established patterns before writing code.

Use the backend spec as the authoritative source for API shapes, endpoints, and error codes — do not redefine them in the frontend code.

After writing all frontend files, run lint and tests from `meal-prep/` and fix any failures. Print the relative paths of every file created or modified.
