# Codex Execution Package

Use this reference when the deliverable is a development document package for a later Codex run. The package must reduce ambiguity, prevent scope drift, and give Codex a safe implementation path.

## Required Principle

The package is not a proposal and not a transcript. It is an execution contract.

Another Codex instance should be able to read the package and know:

- What environment must exist before coding.
- Which claims are verified and which are assumptions.
- What to build.
- What not to build.
- What must be verified first.
- Which files or modules are likely involved.
- Which order to implement work in.
- How to verify each phase.
- When to stop and ask the user.

## Required Files

```text
docs/dev-plans/<feature-name>/
├── README.md
├── 00-environment-readiness.md
├── 01-idea-interview.md
├── 02-scope-contract.md
├── 03-product-requirements.md
├── 04-architecture.md
├── 05-backend-plan.md
├── 06-frontend-plan.md
├── 07-ui-design-plan.md
├── 08-api-contracts.md
├── 09-task-breakdown.md
├── 10-risks-and-backlog.md
└── 11-evidence-matrix.md
```

## README.md Template

```markdown
# Codex Execution Entrypoint: <Feature>

## Read First
1. `00-environment-readiness.md`
2. `02-scope-contract.md`
3. `11-evidence-matrix.md`
4. `09-task-breakdown.md`
5. `10-risks-and-backlog.md`

## Implementation Order
1. <Phase>
2. <Phase>
3. <Phase>

## Hard Scope Boundary
- Build:
- Do not build:

## Pre-Coding Checks
- <Check that must pass before implementation>

## Stop Conditions
Stop and ask the user if:
- <Unknown would change scope>
- <Credential or external access is missing>
- <API field contradicts the plan>

## Verification Commands
- <Command or manual check>
```

## Task Breakdown Rules

Each task must include:

- Purpose.
- Inputs.
- Expected files or modules.
- Dependencies.
- Acceptance criteria.
- Verification method.
- Out-of-scope warnings.

Use this format:

```markdown
## Task <n>: <Name>

### Purpose
<Why this exists.>

### Inputs
- <Document, API, schema, user decision>

### Expected Work
- <Concrete implementation work>

### Acceptance Criteria
- <Observable result>

### Verification
- <Command, UI check, API check, or manual check>

### Do Not
- <Scope guard>
```

## Quality Gate

Before saying the package is ready, check:

- Environment readiness report lists required tools, missing dependencies, and setup blockers.
- Evidence matrix identifies verified facts, assumptions, unknowns, and sources.
- Scope contract exists and contains explicit non-goals.
- Architecture does not serve backlog items.
- Frontend/backend contracts include errors and states.
- UI plan covers loading, empty, error, permission, and responsive states.
- Tasks are ordered and independently verifiable.
- External dependencies and credentials are listed as pre-coding checks.
- Stop conditions are explicit.

If any item fails, the package is not ready for implementation.
