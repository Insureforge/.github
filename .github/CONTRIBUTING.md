# Contributing

## Workflow

- Create an issue first for anything non-trivial so we can align on scope.
- Use short-lived branches off the default branch.
- Keep PRs focused and easy to review.

## PR expectations

- Tests: add/update tests for behavior changes.
- CI: PR must pass required checks.
- Security: never commit secrets; use env vars and local secret stores.
- Tenancy: ensure tenant-scoped behavior is explicit and validated.

## Commit/PR hygiene

- Prefer descriptive commits and PR titles.
- Call out migrations, config changes, and rollout notes in the PR description.

