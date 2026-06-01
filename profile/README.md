# InsureForge

Backend-first .NET insurance integration accelerator for MGAs, with authenticated web UIs for intake and form/report design.

## What we build

- **Carrier integrations**: canonical models + mapping pipelines to carrier formats (sync + async).
- **Authenticated intake**: MGAs/brokers capture structured submissions with tenant-scoped security.
- **Document generation**: template-driven PDFs/reports with deterministic artifacts + traceability.

## Repositories

Core repos:

- **DataForge** (`Insureforge/DataForge`): MVP API + React intake UI, local Docker stack (Keycloak + MongoDB + RabbitMQ + Postgres)
- **FormForge** (`Insureforge/FormForge`): template designer + async rendering backend (Clean Architecture)
- **FormForge Designer UI** (`Insureforge/FormForge.DesignerUi`): React/Vite UI for template drafts, preview, publish, and artifact inspection
- **Application Tenants** (`Insureforge/Application-Tenants`): `Insureforge.Application.Tenanting` library for environment + tenant dependency resolution (fail-fast validation)

Org utilities:

- **Org defaults** (`Insureforge/.github`): org profile + shared PR/issue templates, workflow templates, CODEOWNERS starter
- **Sandbox** (`Insureforge/demo-repository`): scratch repo for quick experiments

## Shared security model

- OIDC via Keycloak; APIs validate bearer tokens for browser and service clients.
- Tenant scope is derived from the required `tenant_id` claim.

## Team & membership

- **Where members show up**: the public “People” list is managed in the org’s People settings (org profile README can’t directly render GitHub’s “Invite your people” widget).
- **How to join (internal)**: request access in your onboarding issue and include which repos/permissions you need (Read/Triage/Write/Maintain/Admin).
- **How to contribute (external)**: open an issue first (integration request, bug, or proposal) so we can route it to the right service.

## Local development

DataForge quickstart (Docker Desktop):

```bash
docker compose up --build
```

Default endpoints:

- UI: http://localhost:5173
- API + Swagger: http://localhost:58236/swagger
- Keycloak: http://localhost:8080
- RabbitMQ management: http://localhost:15672

FormForge Designer UI (separate repo):

```bash
npm install
npm run dev
```

## Engineering dashboard

### Per-developer metrics (GitHub-native)

GitHub doesn’t provide an org-profile “metrics widget”, but we can standardize the metrics we track using:

- **PR throughput**: PRs merged per week (by author).
- **Cycle time**: time from first commit → merge (or open → merge), plus review wait time.
- **Review load**: reviews given, time-to-first-review.
- **Quality signals**: CI pass rate, flaky tests count, escaped defects.

Recommended sources:

- Repo-level **Insights → Pull requests** and **Insights → Code frequency**.
- **GitHub Actions**: workflow run history + failure rate by workflow.
- Optional: **Projects (beta)** board views for “In progress / In review / Blocked / Done”.

### Workflows (CI/CD)

- Keep a minimal baseline in every repo: `build` (compile), `test` (unit/integration), and `lint/format` where applicable.
- Prefer **required status checks** + branch protection on the default branch.
- Publish artifacts when it helps downstream (e.g., OpenAPI specs, UI bundles, migration scripts).
