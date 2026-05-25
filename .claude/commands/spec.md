$ARGUMENTS is either a GitHub issue number or a free-text idea description.

---

## Route A — Issue number (digits only)

Fetch GitHub issue #$ARGUMENTS using the available GitHub MCP tools.

**Step 1 — Post a 4-line summary (do this before touching any files):**

Line 1: What the issue achieves — the user-facing or business outcome
Line 2: What the backend will do — endpoints, data changes, business logic (write "No backend changes" if none)
Line 3: What the frontend will do — UI flows, components, routes
Line 4: Any open questions or blockers you spotted in the issue, ask them one by one. Iterate until you have no further questions and both repo specs are aligned.

Stop here and wait for the user to confirm ("yes", "go ahead", "lgtm", or similar) before writing any files.

---

## Route B — Free-text idea

Interview the user to reach a shared, complete understanding of the feature before writing anything.

**Interview rules:**
- Ask only one question at a time — never a list of questions
- Each question must build on the previous answer; don't follow a fixed script
- Keep asking until you have clear answers for: what the feature does, who it's for, the key user flows, backend changes needed (if any), and any constraints or open decisions
- When you have enough to write both specs without guessing, post a short summary (same 4-line format as Route A) and wait for the user to confirm before writing any files

---

## Spec generation (both routes)

After confirmation:

1. Read the frontend template: `specs/_templates/frontend.md`
2. Only read the backend template (`specs/_templates/backend.md`) if the feature requires new or changed endpoints, data model changes, or new business logic. **Do NOT create a backend spec just to document existing, already-implemented endpoints.**

3. For Route A use `$ARGUMENTS` as the issue number; for Route B derive a short slug (e.g. `add-pantry-filter`) to use in place of the issue number in the filenames.

4. If backend changes are needed, write `meal-prep-api/specs/issue-$ARGUMENTS-backend.md` (Route A) or `meal-prep-api/specs/<slug>-backend.md` (Route B):
   - Replace `{{ISSUE_NUMBER}}` / `{{ISSUE_TITLE}}` with the issue number/title or slug/feature name
   - Fill every section with content derived from the issue or interview
   - Define the full API contract here — all endpoints, request/response shapes, error cases

5. Write `meal-prep/specs/issue-$ARGUMENTS-frontend.md` (Route A) or `meal-prep/specs/<slug>-frontend.md` (Route B):
   - Replace `{{ISSUE_NUMBER}}` / `{{ISSUE_TITLE}}` with the issue number/title or slug/feature name
   - Fill every section with content derived from the issue or interview
   - **Do NOT redefine API endpoints.** If a backend spec exists for this issue/slug, the "API Contract" section must only reference it. If the UI calls pre-existing endpoints with no spec file, name the endpoint and link to the relevant controller file instead.

After writing the files, print the relative paths of the files created.
