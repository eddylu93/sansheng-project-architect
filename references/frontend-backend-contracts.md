# Frontend and Backend Contracts

Use this reference whenever frontend and backend need to coordinate behavior.

## Contract Requirements

Every cross-boundary feature must define:

- Endpoint, event, command, or query name.
- Request shape.
- Response shape.
- Error shape.
- Auth and permission requirement.
- Loading, empty, success, partial success, and failure states.
- Pagination, sorting, filtering, and search semantics when relevant.
- Idempotency, retries, and deduplication when relevant.
- Versioning or compatibility expectations for public APIs.

## API Contract Template

````markdown
# Contract: <Feature>

## Operation
- Type: REST / GraphQL / RPC / Event / Webhook / Local bridge
- Name:
- Owner:

## Request
```json
{}
```

## Response
```json
{}
```

## Errors
| Code | Meaning | Frontend behavior |
| --- | --- | --- |

## Auth and Permissions
- Required role:
- Forbidden case:

## UI State Mapping
| Backend state | UI state | User action |
| --- | --- | --- |

## Compatibility Notes
- Breaking changes:
- Migration:
````

## Frontend Plan Checklist

- Page map and route map.
- Component boundaries and reuse rules.
- State ownership: local, URL, server cache, global store, persisted settings.
- API client pattern and error mapping.
- Form validation and server validation alignment.
- Optimistic updates, cache invalidation, and stale data behavior.
- Accessibility requirements for interactive controls.

## Backend Plan Checklist

- Domain/service boundary.
- Persistence model and migrations.
- Input validation.
- Permission checks.
- Error hierarchy.
- Logging and audit events.
- Background jobs or queues.
- Rate limiting and abuse prevention when relevant.

## Pushback Rules

Block planning when:

- The frontend assumes data the backend cannot provide.
- Backend errors are not mapped to user actions.
- Permission checks exist only in frontend code.
- The contract omits empty, loading, or failure states.
- Shared types are copied manually without an ownership rule.
