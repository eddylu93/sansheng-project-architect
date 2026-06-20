# Evidence and Verification

Use this reference for every planning package. The goal is to prevent Codex from inventing facts and to make later implementation traceable.

## Core Rule

Every factual claim that affects scope, architecture, API design, data fields, security, deployment, cost, or verification must have evidence.

Do not write guesses as facts. If a claim is not verified, label it as `Assumption`, `Unknown`, or `Needs Verification`.

## Evidence Types

- `User-confirmed`: The user stated or approved it in conversation. Use for business goals, scope choices, and preferences.
- `Official docs`: Vendor, framework, platform, API, or standards documentation. Use for API capabilities, auth flows, limits, and required fields.
- `Local code`: Existing repo files with paths and line references. Use for current implementation facts.
- `Test result`: Command output, API response, logs, screenshots, or reproducible checks. Use for environment and integration claims.
- `Source research`: GitHub repos, articles, examples, or third-party references. Use for patterns only, not final truth when official docs exist.
- `Engineering judgment`: Reasoned technical recommendation. Must include rationale and uncertainty.
- `Assumption`: Reasonable but unverified. Must include how to verify.
- `Unknown`: Not enough information. Must not drive final implementation.

## Cross-Check Rules

Use at least two evidence paths for critical external dependencies when practical:

- Official documentation plus test result.
- User confirmation plus local code.
- Local code plus command output.
- Official documentation plus source response sample.

If only one evidence path exists, mark confidence as `Partial` unless the claim is a user preference or direct local-code fact.

## Evidence Matrix Template

```markdown
# Evidence Matrix

| Claim | Evidence Type | Source | Status | Confidence | Notes |
| --- | --- | --- | --- | --- | --- |
| <Claim> | Official docs / User-confirmed / Test result / Assumption | <URL, file path, command, or conversation summary> | Verified / Partial / Unverified | High / Medium / Low | <What this affects> |
```

## Status Rules

- `Verified`: Evidence directly supports the claim.
- `Partial`: Evidence supports part of the claim, or the claim has not been tested in this exact environment.
- `Unverified`: No direct evidence yet.
- `Contradicted`: Evidence conflicts with the claim; do not proceed without resolving it.

## Required Evidence Before Development

Require evidence for:

- OAuth flow, token lifetime, refresh process, scopes, and callback requirements.
- API endpoints, request/response shapes, rate limits, pagination, and error codes.
- Data fields used by rules, dashboards, reports, calculations, or alerts.
- Authentication, authorization, and permission assumptions.
- Local development tool requirements.
- Deployment requirements.
- External notification channels.
- Database choice and required migrations.
- Any claim that affects MVP scope.

## Stop Conditions

Stop and ask the user or require a spike when:

- A required API field is unknown.
- A feature depends on credentials or access that are not available.
- Official docs and test results disagree.
- The user asks to build based on an unverified external capability.
- A local environment blocker prevents the chosen stack from running.

## Language Rules

Use precise wording:

- Say `The docs indicate...` when based on documentation.
- Say `The test result showed...` when based on command/API output.
- Say `The user confirmed...` when based on conversation.
- Say `I infer...` or `Engineering judgment...` when recommending without direct proof.
- Say `Unknown until spike` when evidence is missing.

Avoid:

- "应该可以" as a final conclusion.
- "API 支持" without a specific source.
- "实时" unless latency was verified or officially documented.
- "简单" unless complexity impact is explained.
