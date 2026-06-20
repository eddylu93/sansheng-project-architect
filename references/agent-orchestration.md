# Agent Orchestration

Use this reference when a project benefits from multiple focused sub-agents or workstreams.

## When to Create Sub-Agents

Recommend sub-agents only when coordination cost is justified:

- Multiple domains must progress in parallel.
- Architecture decisions need independent review.
- Frontend, backend, UI, QA, data, or deployment work can be separated cleanly.
- A risky technical choice needs spike research before commitment.
- The project has more than five major modules or multiple external integrations.

Do not create sub-agents for a small single-feature change.

## Non-Negotiable Rule

All sub-agents obey the scope contract. A sub-agent may discover a missing requirement, but must return a change proposal instead of silently expanding scope.

## Standard Agent Set

```markdown
## product-scope-agent
- Owns: requirement interrogation, scope lock, backlog, acceptance criteria.
- Inputs: raw idea, user answers.
- Outputs: scope contract, non-goals, change proposals.
- Forbidden: technical implementation details beyond scope impact.

## system-architecture-agent
- Owns: architecture, module boundaries, data flow, ADR candidates.
- Inputs: accepted scope contract.
- Outputs: architecture plan, risk list, ADR recommendations.
- Forbidden: designing for backlog items.

## backend-agent
- Owns: API, database, permissions, jobs, errors, logs, security.
- Inputs: scope contract, architecture plan, frontend/backend contract needs.
- Outputs: backend plan, API draft, migration needs, operational checks.
- Forbidden: adding endpoints without user workflow and acceptance criteria.

## frontend-agent
- Owns: page map, component boundaries, state management, route behavior, API consumption.
- Inputs: scope contract, UI plan, API contract.
- Outputs: frontend plan, state plan, component/task breakdown.
- Forbidden: assuming backend data or permissions not in the contract.

## ui-design-agent
- Owns: visual direction, interaction states, responsive behavior, accessibility.
- Inputs: product brief, scope contract, frontend surface map.
- Outputs: UI design plan and quality risks.
- Forbidden: decorative UI that weakens core workflow clarity.

## qa-verification-agent
- Owns: acceptance criteria, test plan, regression plan, readiness gate.
- Inputs: scope contract, architecture plan, task breakdown.
- Outputs: verification plan and go/no-go checklist.
- Forbidden: approving work without observable evidence.
```

## Sub-Agent Brief Template

```markdown
# Sub-Agent Brief: <name>

## Mission
<One sentence.>

## Inputs
- <Document or artifact>

## Must Produce
- <Artifact>

## Must Not Do
- Do not expand scope.
- Do not contradict the scope contract.
- Do not assume missing requirements; mark them as open questions.

## Escalation
If a new requirement appears, return a Change Proposal:
- New requirement:
- Why it matters:
- Scope impact:
- Recommendation:
```

## Coordination Output

When recommending sub-agents, produce:

- Agent list
- Dependency order
- Inputs and outputs for each agent
- Shared source of truth
- Merge process for conflicting recommendations
- Scope-change escalation path
