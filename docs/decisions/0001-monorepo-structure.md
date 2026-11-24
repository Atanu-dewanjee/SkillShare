# ADR 0001: Use a Single Monorepo for All Apps

- **Status:** Accepted
- **Date:** 2026-11-25

## Context

SkillSphere has three applications:

- a NestJS REST API (backend),
- a Next.js admin portal,
- a Flutter mobile app.

They are developed by a small university team, they change together often (for example, a new API endpoint plus the screen that uses it), and there is one GitHub repository.

## Decision

Keep all applications in **one repository** with this layout:

```text
apps/
  api/      NestJS backend
  admin/    Next.js admin portal
  mobile/   Flutter mobile app
docs/       Cross-cutting documentation and ADRs
```

Each app is **self-contained**: it has its own dependencies, configuration, scripts, and tests, and can be built and run on its own from its folder.

Root-level files are limited to repository-wide concerns: `README.md`, `CONTRIBUTING.md`, `.gitignore`, `.gitattributes`, `.editorconfig`, and (later) Docker Compose for local infrastructure and CI configuration.

## Consequences

- ✅ One place to clone, one issue tracker, one history. A feature that touches the API and the mobile app can be done in a single branch and pull request.
- ✅ Simple for a student team; no need to coordinate versions across repositories.
- ✅ Self-contained apps can later be split into separate repositories if ever needed.
- ⚠️ CI must run only the checks relevant to the changed app, otherwise it gets slow. This will be handled with path filters when CI is set up.
- ⚠️ Mobile and web apps cannot import backend TypeScript code directly. API contracts are shared through documentation (and possibly OpenAPI later), not through code imports.
