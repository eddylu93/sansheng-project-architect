# Scope Contract

Use this reference to interrogate vague product ideas, prevent scope creep, and lock the MVP boundary before architecture or implementation.

## Interview Areas

Ask only 1-3 questions at a time. After each answer, summarize the current scope and unresolved gaps.

Required areas:

- Problem: What painful or expensive problem does this solve?
- User: Who uses it, how often, and in what environment?
- Trigger: What causes the user to open this product or feature?
- Core workflow: What is the shortest successful path from start to value?
- Output: What artifact, decision, action, or state should exist when the workflow succeeds?
- Data: What entities exist, who owns them, and how are they created, changed, archived, or deleted?
- Permissions: Who can view, create, approve, edit, export, or delete?
- Integrations: Which external systems, APIs, credentials, files, or imports are required?
- Constraints: Deadline, budget, stack, platform, compliance, deployment, and maintainability limits.
- Non-goals: What should explicitly not be solved in this version?
- Acceptance: What observable evidence proves MVP success?

## Idea Classification

Classify every idea into exactly one bucket:

- `MVP`: Required for the core workflow. Without it, the product fails its main job.
- `V1`: Valuable soon, but not required for MVP validation.
- `Backlog`: Possible future value, not currently proven.
- `Explicitly Not Doing`: Outside the product boundary or harmful to focus.
- `High-Risk Spike`: Unknown cost, feasibility, compliance, or technical risk; research before commitment.

If an idea cannot be tied to a core workflow or acceptance criterion, do not put it in MVP.

## Scope Contract Template

```markdown
# Scope Contract: <Project or Feature>

## Problem
<One clear problem statement.>

## Target Users
- <User role>:

## MVP Must Do
- <Capability> - acceptance: <observable result>

## MVP Must Not Do
- <Explicit exclusion and reason>

## V1 Deferred
- <Capability and why it is deferred>

## Backlog
- <Idea>

## High-Risk Spikes
- <Question to validate>
- Decision needed by: <date or phase>

## Core Workflow
1. <Step>
2. <Step>
3. <Success end state>

## Data Boundary
- Entities:
- Source of truth:
- Retention/archive rule:

## Permission Boundary
- Roles:
- Allowed actions:

## Acceptance Criteria
- <Testable criterion>

## Change-Control Rule
New ideas after this contract require a change proposal. To accept a new item, name what gets removed, delayed, or simplified.
```

## Strict Rejection Patterns

Reject or defer ideas when:

- The user says "顺便", "也可以", "以后可能", "先加上", or "不复杂吧" without proving MVP impact.
- The idea creates a new module, data entity, permission rule, integration, or UI surface without acceptance criteria.
- The idea optimizes a workflow that is not yet proven.
- The idea requires architecture for a future version before MVP validates the current one.
- The idea mixes a separate product into the current project.

## Response Pattern

Use this response when pushing back:

```text
这个想法不能直接进入 MVP。
原因：
- 它服务的核心目标不明确。
- 它会增加 <data/API/UI/permission/ops> 复杂度。
- 当前没有验收标准。

建议：放入 <V1/Backlog/High-Risk Spike>。
如果你坚持纳入 MVP，需要先回答：
1. 不做它，MVP 是否失败？
2. 它替代或删除哪个现有 MVP 功能？
3. 可验收结果是什么？
```
