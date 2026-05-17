$ARGUMENTS contains the issue number followed by any optional extra context from the user (e.g. "1" or "1 use soft deletes and transactions").

Parse $ARGUMENTS: the **first word** is the issue number (`ISSUE_NUMBER`); everything after is `USER_CONTEXT`.

---

**Step 1 — Read the spec:**

Read `meal-prep-api/specs/issue-$ISSUE_NUMBER-backend.md`.

If the file does not exist, stop and tell the user: "No backend spec found at `meal-prep-api/specs/issue-$ISSUE_NUMBER-backend.md`. Run `/spec $ISSUE_NUMBER` first to generate it."

---

**Step 2 — Post an implementation plan before touching any files:**

Print a concise plan:
- Line 1: What this implements (business outcome from the spec Goal section)
- Line 2: New NestJS artefacts — module(s), controller(s), service(s), DTO(s), entity/migration
- Line 3: API endpoints being added (method + path)
- Line 4: Test files to be created
- Line 5 (if USER_CONTEXT is non-empty): How you will honour the user's extra instructions
- Line 6: Any open questions or ambiguities in the spec — ask them one by one

Stop here and wait for the user to confirm ("yes", "go ahead", "lgtm", or similar) before writing any files. If there are open questions, iterate until resolved.

---

**Step 3 — Implement (after confirmation):**

All work is scoped to `meal-prep-api/`. Read `meal-prep-api/CLAUDE.md` and the root `CLAUDE.md` for project conventions, and scan the existing source to match established patterns before writing code.

After writing all files, run lint and tests from `meal-prep-api/` and fix any failures. Print the relative paths of every file created or modified.
