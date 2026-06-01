# InsureForge

Backend-first .NET insurance integration accelerator for MGAs, with authenticated web UIs for intake and form/report design.

## Repositories

- **DataForge** (`Insureforge/DataForge`): MVP API + React intake UI, local Docker stack (Keycloak + MongoDB + RabbitMQ + Postgres)
- **FormForge** (`Insureforge/FormForge`): generic carrier form/report template designer + async rendering backend (Clean Architecture)
- **FormForge Designer UI** (`Insureforge/FormForge.DesignerUi`): React/Vite UI for template drafts, preview, publish, and artifact inspection
- **Application Tenants** (`Insureforge/Application-Tenants`): `Insureforge.Application.Tenanting` library for environment + tenant dependency resolution (fail-fast validation)

## Shared security model

- OIDC via Keycloak; APIs validate bearer tokens for browser and service clients.
- Tenant scope is derived from the required `tenant_id` claim.

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

## Links

- Website: https://www.insureforge.io
