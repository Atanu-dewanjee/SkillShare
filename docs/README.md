# SkillSphere Documentation

Project documentation that doesn't belong to a single app.

## Contents

| Folder / File | Purpose |
| --- | --- |
| [`decisions/`](decisions/) | **Architecture Decision Records (ADRs):** short documents that record an important technical decision, why we made it, and its consequences. |

More sections (architecture overview, database design, API reference) will be added as the project grows.

## Writing an ADR

1. Copy the format of an existing ADR in [`decisions/`](decisions/).
2. Give it the next number: `NNNN-short-title.md`.
3. Keep it short: **Context → Decision → Consequences**.
4. Never rewrite an accepted ADR. If a decision changes, add a new ADR that *supersedes* the old one.
