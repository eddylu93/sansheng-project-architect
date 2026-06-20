# Sansheng Project Architect

`sansheng-project-architect` is a Codex skill for planning software projects before implementation. It acts as a strict product manager and system architect: it interrogates vague ideas, locks MVP scope, rejects feature creep, verifies evidence, and produces a Codex-readable development document package for a later implementation run.

## What It Does

- Checks development environment readiness before planning implementation.
- Forces ideas into clear MVP, V1, backlog, non-goal, and spike buckets.
- Requires evidence for factual claims, API capabilities, data fields, and technical assumptions.
- Plans architecture, frontend/backend contracts, UI quality standards, tasks, risks, and verification gates.
- Defines execution boundaries so planning, simulation, safe checks, and credentialed live execution are not confused.
- Produces a structured document package that another Codex run can read and execute.
- Plans sub-agent collaboration when a project is large enough to justify it.

## Intended Output

The skill is designed to produce:

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

## Use Cases

- Starting a new product, tool, app, or internal system.
- Turning a rough idea into a scoped implementation plan.
- Preventing projects from becoming bloated before development starts.
- Creating development docs that Codex can execute later.
- Planning full-stack projects with backend, frontend, UI, API, auth, deployment, and verification concerns.

## Usage

After installing the skill in a Codex skills directory, invoke it by name:

```text
Use $sansheng-project-architect to plan this project before development.
```

The skill should not be used to jump directly into coding. Its job is to produce a scoped, evidence-backed, executable planning package first.

## Installation

Clone this repository into your Codex skills directory:

```bash
git clone git@github.com:eddylu93/sansheng-project-architect.git ~/.codex/skills/sansheng-project-architect
```

If the folder already exists, update it with:

```bash
cd ~/.codex/skills/sansheng-project-architect
git pull
```
