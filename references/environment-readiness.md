# Environment Readiness

Use this reference before product intake, architecture planning, or implementation. The goal is to prevent a later Codex implementation run from failing because the user's machine lacks required development tools.

## Execution Boundary

Checking versions and installed tools is allowed only when the user has asked to inspect the environment or start preparing executable docs. Do not install anything automatically unless the user explicitly asks.

If the user only wants a plan, produce an environment checklist instead of running local commands.

## What to Check

Choose checks based on the project type. Do not require tools that the project does not need.

Common checks:

- OS and architecture: macOS, Linux, Windows, ARM/x64.
- Shell and PATH health.
- Git.
- Node.js, npm, pnpm, yarn, bun.
- Python and pip/uv/poetry.
- Docker or local service alternatives.
- Database clients and local database availability: PostgreSQL, MySQL, Redis, SQLite.
- Browser/runtime tooling for frontend verification.
- Framework CLIs needed by the project.
- Native build dependencies when relevant.
- Existing repo package manager and lockfile.
- Required environment files: `.env`, `.env.local`, examples, secret names.
- Required external accounts: OAuth apps, cloud accounts, API credentials, webhooks.
- Ports likely to be used and obvious conflicts.

## Environment Report Template

```markdown
# Environment Readiness

## Target Development Machine
- OS:
- Architecture:
- Shell:

## Required Tooling
| Tool | Required | Detected | Status | Action |
| --- | --- | --- | --- | --- |
| Git | Yes | <version/missing> | Pass/Fail/Unknown | <install or verify action> |

## Required Accounts and Secrets
| Dependency | Required For | Status | Action |
| --- | --- | --- | --- |

## Local Services
| Service | Required | Status | Action |
| --- | --- | --- | --- |

## Blockers
- <Missing item that blocks development>

## Non-Blocking Warnings
- <Item that can wait>

## Recommended Setup Steps
1. <Command or manual action>

## Readiness
Ready / Not ready / Ready for docs only
```

## Status Rules

- `Pass`: tool is installed and version is acceptable.
- `Fail`: tool is missing, broken, or too old for the planned stack.
- `Unknown`: cannot verify without user input, credentials, or access.
- `Blocked`: implementation should not start until fixed.

## Pushback Rules

Block development when:

- The selected stack requires a runtime that is missing.
- The repo package manager cannot be identified.
- Required local services cannot run and no remote alternative exists.
- Required OAuth app, API key, webhook, or cloud account does not exist.
- The user expects Codex to implement with credentials that are unavailable.

Do not block planning when:

- The missing item is only needed for deployment.
- The user only asked for architecture or documentation.
- A safe mock or stub can be used for early planning, and the limitation is documented.
