# ADR 0002: Use npm, Without Workspaces, for JavaScript/TypeScript Apps

- **Status:** Accepted
- **Date:** 2026-11-25

## Context

Two apps use the Node.js ecosystem: `apps/api` (NestJS) and `apps/admin` (Next.js). We must choose a package manager and decide whether to link the apps with a workspace tool (npm/pnpm/Yarn workspaces, Turborepo, Nx).

The Flutter app (`apps/mobile`) uses Dart's own package manager (`pub`) and is unaffected by this decision.

At this point the API and admin portal share no code.

## Decision

- Use **npm** (bundled with Node.js) as the package manager.
- Use **Node.js 22 LTS** as the baseline runtime version.
- Each Node app has its **own** `package.json` and `package-lock.json` inside its folder. There is **no root `package.json`** and **no workspace tooling** for now.
- Always commit `package-lock.json` so installs are reproducible.

## Alternatives Considered

| Option | Why not now |
| --- | --- |
| pnpm | Faster and stricter, but an extra tool for every contributor to install and learn. Its benefits matter most in large workspaces. |
| Yarn | No clear advantage over npm for this project. |
| npm workspaces / Turborepo / Nx | Useful when apps share packages. We have no shared packages yet, so this would add complexity with no benefit. |

## Consequences

- ✅ Zero extra setup: anyone with Node.js already has npm.
- ✅ Each app is installed, built, and tested independently (`cd apps/api && npm install`).
- ⚠️ Shared dev tools (e.g. Prettier, ESLint) are configured per app, with some duplication.
- 🔁 **Revisit** if we create a shared TypeScript package (for example, shared API types or validation rules). Then npm workspaces would be the first option to consider, and a new ADR would supersede this one.
