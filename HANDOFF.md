# Insureforge GitHub Org Setup — Handoff

Date: 2026-05-31

This repo (`Insureforge/.github`) controls org-wide GitHub defaults and the org profile README.

## What was done

### Org profile README

- Updated `profile/README.md` to be more descriptive (what we build, team/membership notes, engineering dashboard, workflows).
- Removed the `Links / Website` section per request.

### Org-wide templates (applies org-wide)

Added the following under `.github/`:

- PR template: `.github/PULL_REQUEST_TEMPLATE.md`
- Issue forms: `.github/ISSUE_TEMPLATE/*`
  - `bug_report.yml`, `feature_request.yml`, `integration_request.yml`, `onboarding_access.yml`
  - `config.yml` disables blank issues and includes a security mailto link
- Defaults/docs:
  - `.github/SECURITY.md`
  - `.github/SUPPORT.md`
  - `.github/CONTRIBUTING.md`
- Code owners (starter placeholder): `.github/CODEOWNERS`
- Workflow templates (appear in “New workflow” UI):
  - `.github/workflow-templates/dotnet-ci.yml`
  - `.github/workflow-templates/node-ci.yml`
  - plus corresponding `*.properties.json` metadata

## Current state (important)

- These changes were pushed to `Insureforge/.github` on branch `dev`.
- The org’s onboarding panel (“We think you’re gonna like it here”) is GitHub UI and can only be hidden per-user via “hide the tasks we’ve suggested”.

## The problem discovered

You actually wanted these defaults in `Insureforge/.github-private` instead of `Insureforge/.github`.

GitHub behavior note:

- `Insureforge/.github` is special: `profile/README.md` renders on the org overview.
- The org-wide community health files and templates (`.github/*`) typically need to be in `Insureforge/.github` to apply org-wide. A repo named `.github-private` will not act as the org’s special `.github` repo.

## Recommended fix path

### Option A (recommended): keep `Insureforge/.github` public, move only sensitive material to `.github-private`

1. Keep `profile/README.md` and the non-sensitive templates in `Insureforge/.github` (public).
2. Put sensitive docs in `Insureforge/.github-private` (private), e.g.:
   - internal runbooks, incident response, escalation contacts
   - onboarding secrets/setup steps
   - deployment credentials/processes
3. In the public `.github` repo, link to internal docs with a note like:
   - “Internal: see `.github-private` → `docs/`”

### Option B: if you truly need everything private

You can make `Insureforge/.github` private, but then:

- The org profile README will stop being publicly visible.
- Org-wide templates may not behave as expected for public contributors.

## How to create/migrate `.github-private`

1. Create `Insureforge/.github-private` (private) on GitHub.
2. Clone it locally:
   - `git clone https://github.com/Insureforge/.github-private.git`
3. Copy the desired folders/files from this repo into that repo.
4. Commit + push to whatever default branch you want there (likely `dev`).

## Follow-ups you should do

- Update `.github/CODEOWNERS` to real users/teams (it currently references `@Insureforge/owners` as a placeholder).
- Pin the 4 core repos on the org homepage:
  - `DataForge`, `FormForge`, `FormForge.DesignerUi`, `Application-Tenants`
- Decide whether to enable Discussions and which categories you want.

