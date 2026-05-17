Fetch GitHub issue #$ARGUMENTS using the available GitHub MCP tools (look for tools whose names contain "get_issue", "fetch_issue", or similar).

**Step 1 — Post a 4-line summary (do this before touching any files):**

Line 1: What the issue achieves — the user-facing or business outcome
Line 2: What the backend will do — endpoints, data changes, business logic
Line 3: What the frontend will do — UI flows, components, routes
Line 4: Any open questions or blockers you spotted in the issue, ask them one by one. If there are some changes, iterate until you have no more further questions and both repo specs are aligned.

Stop here and wait for the user to confirm ("yes", "go ahead", "lgtm", or similar) before writing any files. Don't proceed if you are still uncertain about things on how to implement it

---

**Step 2 — After confirmation, generate the specs:**

1. Read the backend template: `specs/_templates/backend.md`
2. Read the frontend template: `specs/_templates/frontend.md`

3. Write `meal-prep-api/specs/issue-$ARGUMENTS-backend.md`:
   - Replace `{{ISSUE_NUMBER}}` with `$ARGUMENTS` and `{{ISSUE_TITLE}}` with the issue title
   - Fill every section with content derived from the issue (labels, body, comments)
   - Define the full API contract here — all endpoints, request/response shapes, error cases

4. Write `meal-prep/specs/issue-$ARGUMENTS-frontend.md`:
   - Replace `{{ISSUE_NUMBER}}` with `$ARGUMENTS` and `{{ISSUE_TITLE}}` with the issue title
   - Fill every section with content derived from the issue
   - **Do NOT redefine API endpoints.** The "API Contract" section must only reference `meal-prep-api/specs/issue-$ARGUMENTS-backend.md` and list which endpoints the UI calls and why — shapes and error codes live in the backend spec only

After writing both files, print the relative paths of the two files created.
