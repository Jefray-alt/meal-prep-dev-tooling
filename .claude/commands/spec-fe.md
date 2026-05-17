$ARGUMENTS contains the issue number followed by any optional extra context from the user (e.g. "1" or "1 keep the form on one page and skip the stepper").

Parse $ARGUMENTS: the **first word** is the issue number (`ISSUE_NUMBER`); everything after is `USER_CONTEXT`.

---

**Step 1 — Read the specs:**

1. Read `meal-prep/specs/issue-$ISSUE_NUMBER-frontend.md`.
   If the file does not exist, stop and tell the user: "No frontend spec found at `meal-prep/specs/issue-$ISSUE_NUMBER-frontend.md`. Run `/spec $ISSUE_NUMBER` first to generate it."

2. Check whether `meal-prep-api/specs/issue-$ISSUE_NUMBER-backend.md` exists.
   - If it does, read it — use it as the authoritative source for API shapes, endpoints, and error codes.
   - If it does not exist, that is fine — proceed using only the frontend spec.

---

**Step 2 — Post an implementation plan before touching any files:**

Print a concise plan:
- Line 1: What this implements (business outcome from the spec Goal section)
- Line 2: New or modified routes and the page-level component(s) that own them
- Line 3: New or modified presentational components
- Line 4: API calls made and how errors are surfaced to the user
- Line 5: State — local or any shared store slices touched
- Line 6 (if USER_CONTEXT is non-empty): How you will honour the user's extra instructions
- Line 7: Any open questions or ambiguities — ask them one by one

Stop here and wait for the user to confirm ("yes", "go ahead", "lgtm", or similar) before writing any files. If there are open questions, iterate until resolved.

---

**Step 3 — Implement (after confirmation):**

All work is scoped to `meal-prep/`. Read `meal-prep/CLAUDE.md` and the root `CLAUDE.md` for project conventions, and scan the existing source to match established patterns before writing code.

After writing all files, run lint and tests from `meal-prep/` and fix any failures. Print the relative paths of every file created or modified.
