# SkillSphere

**A Multi-University Skill Exchange and Mentorship Platform**

SkillSphere is a platform where students from different universities exchange skills with each other. Every student can be a **learner** and a **mentor** at the same time: teach what you know, learn what you don't, and use an internal credit system to keep exchanges fair.

> **Status:** Early development. This repository currently contains only project documentation. Application code will be added in later stages (see [Development Roadmap](#development-roadmap)).

---

## Table of Contents

- [Purpose](#purpose)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Project Scope](#project-scope)
- [Planned Repository Structure](#planned-repository-structure)
- [Development Roadmap](#development-roadmap)
- [Engineering Practices](#engineering-practices)
- [Getting Started](#getting-started)
- [License](#license)

---

## Purpose

Students often have skills that peers at other universities want to learn, such as programming, languages, design, music, or exam preparation. These exchanges usually happen informally and are hard to discover, schedule, or trust.

SkillSphere provides one place to:

- **Discover** skills and mentors across universities.
- **Exchange** knowledge through structured learning requests and booked sessions.
- **Stay fair** with an internal, traceable credit system instead of money.
- **Stay safe** with reviews, reporting, and moderation tools.

---

## Key Features

### For Students

| Area | Capabilities |
| --- | --- |
| **Skill discovery** | Browse skills offered by other students; search and filter skills and mentors. |
| **Skill offers** | Publish your own skill offers for others to request. |
| **Learning requests** | Send requests; mentors can accept, decline, or negotiate them. |
| **Scheduling** | Set your availability and book sessions with mentors. |
| **Messaging** | Private, real-time one-to-one chat. |
| **Credits** | Earn and spend internal credits, recorded in a traceable ledger. |
| **Trust & safety** | Leave reviews; report users or content. |

### For Administrators and Moderators

- Manage user accounts.
- Review reports submitted by users.
- Hide inappropriate content.
- Restrict accounts when necessary.
- Monitor basic platform activity.

### Search and Matching

Skill search and matching use **transparent keyword, filter, and ranking logic**. There is no AI-based recommendation, so users and administrators can understand why a result appears.

### Credit System

Credits are an **internal platform unit only**. They are not real money, cannot be bought with cash, and cannot be withdrawn. Every credit movement is recorded in a **ledger** so balances can be audited and explained.

---

## Technology Stack

| Layer | Technology |
| --- | --- |
| Mobile app | [Flutter](https://flutter.dev/) (Android-first, iOS-ready) |
| Backend API | [NestJS](https://nestjs.com/) exposing a **REST** API |
| Database | [PostgreSQL](https://www.postgresql.org/) |
| ORM | [Prisma](https://www.prisma.io/) |
| Authentication | Access token + refresh token strategy |
| Real-time messaging | [Socket.IO](https://socket.io/) |
| Caching & real-time support | [Redis](https://redis.io/) |
| Background jobs | [BullMQ](https://docs.bullmq.io/) |
| Admin portal | [Next.js](https://nextjs.org/) |
| File storage | Cloud-compatible storage abstraction (e.g. S3-compatible) |
| Notifications | Email and push notification architecture |
| Testing | Unit, integration, and end-to-end tests where appropriate |
| Version control | Git and GitHub |

---

## Project Scope

### Included in Version 1

Everything listed under [Key Features](#key-features).

### Explicitly Out of Scope for Version 1

To keep the first version focused and achievable, the following will **not** be built:

- AI recommendations or AI tutoring
- Cash payments or cash withdrawals
- Cryptocurrency
- Built-in video conferencing
- Formal academic accreditation
- University SIS (Student Information System) integration
- Session completion history

---

## Planned Repository Structure

This is a **monorepo**: all parts of the system will live in this one repository. The structure below is a plan and will be created in a later step.

```text
SkillShare/
├── apps/
│   ├── mobile/      # Flutter mobile app
│   ├── api/         # NestJS REST API + Socket.IO + BullMQ workers
│   └── admin/       # Next.js admin portal
├── docs/            # Architecture notes, API docs, decisions
├── README.md
└── .gitignore
```

---

## Development Roadmap

The project is built incrementally. Each stage is small, reviewed, and committed separately.

| Stage | Focus | Status |
| --- | --- | --- |
| 1 | Repository initialization: README, `.gitignore`, Git/GitHub setup | ✅ Done |
| 2 | Monorepo folder structure and project conventions | ⏳ Next |
| 3 | Local development environment (Docker for PostgreSQL and Redis, env templates) | Planned |
| 4 | Backend foundation (NestJS app, configuration, health check) | Planned |
| 5 | Database schema design and Prisma setup | Planned |
| 6 | Authentication (registration, login, access/refresh tokens) | Planned |
| 7 | User profiles and university affiliation | Planned |
| 8 | Skill offers, search, filtering, and ranking | Planned |
| 9 | Learning requests (send, accept, decline, negotiate) | Planned |
| 10 | Availability and session booking | Planned |
| 11 | Credit system and ledger | Planned |
| 12 | Real-time private chat (Socket.IO) | Planned |
| 13 | Reviews and reporting | Planned |
| 14 | Notifications (email, push) and background jobs (BullMQ) | Planned |
| 15 | File storage abstraction | Planned |
| 16 | Flutter mobile app | Planned |
| 17 | Next.js admin portal and moderation tools | Planned |
| 18 | Testing hardening, CI, and documentation | Planned |

The order may be adjusted as the project evolves; changes will be recorded here.

---

## Engineering Practices

- **Conventional Commits** for commit messages (e.g. `feat:`, `fix:`, `chore:`, `docs:`).
- **Small, logical commits** that each do one thing.
- **No secrets in Git.** Configuration is supplied through environment variables; only example files such as `.env.example` are committed.
- **No generated files** (dependencies, build output, caches) are committed.
- **`main`** is the primary branch. History is never force-pushed without explicit agreement.
- **Security, maintainability, and clean architecture** are prioritized over speed.

---

## Getting Started

There is no runnable application yet. Setup instructions for each app (mobile, API, admin) will be added as they are built.

To get a copy of the repository:

```bash
git clone https://github.com/Atanu-dewanjee/SkillShare.git
cd SkillShare
```

---

## License

To be decided. Until a license is added, all rights are reserved by the project author(s).
