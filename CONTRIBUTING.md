# Contributing to SkillSphere

This guide explains how we work on SkillSphere: branches, commits, pull requests, and safety rules. Please read it before your first change.

## Repository Layout

| Path | Contents |
| --- | --- |
| `apps/api/` | NestJS REST API, Socket.IO, BullMQ workers |
| `apps/admin/` | Next.js admin portal |
| `apps/mobile/` | Flutter mobile app |
| `docs/` | Documentation and [Architecture Decision Records](docs/decisions/) |

Each app is self-contained. Run its commands from inside its folder (for example `cd apps/api`). See [ADR 0001](docs/decisions/0001-monorepo-structure.md).

## Prerequisites

| Tool | Needed for | Version |
| --- | --- | --- |
| Git | Everything | Recent |
| Node.js + npm | `apps/api`, `apps/admin` | Node.js 22 LTS ([ADR 0002](docs/decisions/0002-package-manager-npm.md)) |
| Flutter SDK | `apps/mobile` | Latest stable |
| Docker Desktop | Local PostgreSQL and Redis | Recent |

## Branching

- `main` is the primary branch. It should always be in a working state.
- **Never commit directly to `main`.** Create a short-lived branch for each change:

  ```bash
  git switch main
  git pull
  git switch -c <type>/<short-description>
  ```

- Branch name examples:

  | Prefix | Use for | Example |
  | --- | --- | --- |
  | `feat/` | A new feature | `feat/skill-search` |
  | `fix/` | A bug fix | `fix/refresh-token-expiry` |
  | `chore/` | Setup, tooling, maintenance | `chore/monorepo-structure` |
  | `docs/` | Documentation only | `docs/api-overview` |
  | `test/` | Adding or fixing tests | `test/credits-ledger` |
  | `refactor/` | Code changes with no behavior change | `refactor/auth-guards` |

## Commit Messages

We use [Conventional Commits](https://www.conventionalcommits.org/):

```text
<type>(<optional scope>): <short summary in present tense>

<optional body: what changed and why>
```

- **Types:** `feat`, `fix`, `chore`, `docs`, `test`, `refactor`, `perf`, `ci`, `build`, `style`.
- **Scopes (optional):** `api`, `admin`, `mobile`, `docs`.
- Examples:
  - `feat(api): add endpoint to create skill offers`
  - `fix(mobile): prevent double booking on slow networks`
  - `docs: describe credit ledger rules`

Keep commits **small and focused**: one logical change per commit.

## Pull Requests

1. Push your branch: `git push -u origin <branch-name>`.
2. Open a pull request into `main` on GitHub.
3. Describe **what** changed, **why**, and **how you tested it**.
4. Make sure tests and linters pass for the apps you changed.
5. Merge only after review. Delete the branch after merging.

## Safety Rules

- 🔒 **Never commit secrets.** Passwords, API keys, tokens, private keys, and `.env` files stay out of Git. Commit a `.env.example` with placeholder values instead.
- 🚫 **Never force-push** to `main` or to a shared branch.
- 📦 **Never commit generated files**: `node_modules/`, build output, coverage reports, and similar (see [`.gitignore`](.gitignore)).
- 🧾 **Credits are not money.** Every credit change must go through the ledger; never update a balance directly.
- ❌ Respect the [out-of-scope list](README.md#project-scope) for Version 1.

## Formatting and Line Endings

- [`.editorconfig`](.editorconfig) sets shared basics (UTF-8, LF, 2-space indent). Install the EditorConfig extension if your editor doesn't support it natively.
- [`.gitattributes`](.gitattributes) stores text files with LF endings in the repository, so Windows and macOS/Linux contributors don't create line-ending-only changes.
- App-specific formatters (Prettier, `dart format`) will be added with each app.

## Recording Decisions

For significant technical decisions (a new library, a change in architecture), add an ADR in [`docs/decisions/`](docs/decisions/). See [docs/README.md](docs/README.md).
