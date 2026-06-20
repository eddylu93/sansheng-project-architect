# Architecture Planning

Use this reference after scope lock. Do not design architecture for backlog items.

## Architecture Checklist

Cover these areas:

- System context: users, clients, server components, external systems.
- Module boundaries: responsibilities, inputs, outputs, forbidden dependencies.
- Data model: entities, relationships, lifecycle, ownership, retention.
- State ownership: client state, server state, cache, database, background jobs.
- Control flow: primary happy path, retry path, failure path, admin path.
- Integration points: API clients, credentials, rate limits, webhooks, import/export, third-party failure.
- Security: auth, authorization, audit events, secret storage, sensitive data handling.
- Operations: logs, metrics, health checks, backups, migrations, rollback.
- Performance: expected volume, latency expectations, expensive operations, pagination.
- Deployment: environments, configuration, build outputs, migration order.

## Architecture Document Template

```markdown
# Architecture Plan

## Scope Basis
This architecture implements only the accepted MVP scope from `01-scope-contract.md`.

## System Context
- Users:
- Clients:
- Backend services:
- Storage:
- External systems:

## Module Boundaries
| Module | Owns | Inputs | Outputs | Must Not Own |
| --- | --- | --- | --- | --- |

## Core Data Model
| Entity | Purpose | Source of Truth | Lifecycle |
| --- | --- | --- | --- |

## Core Flow
1. <Step>
2. <Step>
3. <Step>

## Failure and Recovery
- User-visible failures:
- Backend failures:
- External dependency failures:
- Recovery path:

## Security and Permissions
- Roles:
- Protected actions:
- Audit needs:

## Operational Requirements
- Logs:
- Metrics:
- Health checks:
- Migration/rollback:

## ADR Candidates
- <Decision that is expensive to reverse>
```

## ADR Triggers

Write or recommend an ADR when choosing:

- Framework, major library, hosting, database, queue, auth strategy, payment provider, AI provider, or storage provider.
- REST vs GraphQL vs tRPC or other API architecture.
- Sync vs async processing.
- Multi-tenant vs single-tenant data model.
- Client-heavy vs server-heavy state ownership.
- Any decision expensive to reverse after users or data exist.

## Architecture Pushback

Push back when:

- A module owns too many responsibilities.
- A future backlog item is driving MVP architecture.
- A UI shortcut bypasses permission or data integrity.
- A backend API is shaped around one component instead of a stable domain operation.
- A data model cannot answer who owns, edits, deletes, or audits a record.
