# Backend Spec — Issue #{{ISSUE_NUMBER}}: {{ISSUE_TITLE}}

## Goal
<!-- One sentence: what business outcome does this achieve? -->

## Scope
<!-- What is explicitly in/out of scope for the backend? -->

## Data Model Changes
<!-- New tables, columns, migrations, or schema changes -->

| Change | Type | Notes |
|--------|------|-------|
|        |      |       |

## API Contract

### `{{METHOD}} {{PATH}}`
**Auth:** <!-- required / public / admin -->

**Request**
```json
{}
```

**Response 200**
```json
{}
```

**Error cases**
| Status | Condition |
|--------|-----------|
| 400    |           |
| 401    |           |
| 404    |           |

## Business Logic
<!-- Step-by-step description of what the handler does -->

1.
2.
3.

## Background Jobs / Events
<!-- Any async work, queues, webhooks, or emitted events -->

## Security Considerations
<!-- Auth checks, rate limiting, input sanitisation, PII handling -->

## Tests

### Unit tests
<!-- What should be unit-tested? List the key cases for service/handler logic. -->

| Scenario | Expected outcome |
|----------|-----------------|
|          |                 |

### Integration / e2e tests
<!-- Which endpoints need e2e coverage? List happy path + critical error cases. -->

| `METHOD /path` | Case | Expected status |
|----------------|------|----------------|
|                |      |                |

## Open Questions
<!--
- [ ] Question one
- [ ] Question two
-->
