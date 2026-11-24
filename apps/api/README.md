# SkillSphere API (`apps/api`)

The backend for SkillSphere: a **NestJS** application exposing a **REST** API.

> **Status:** Placeholder. The NestJS project will be generated here in a later stage. This README will then be replaced with setup and run instructions.

## Responsibilities

- REST API consumed by the mobile app and the admin portal.
- Authentication with access and refresh tokens.
- Business logic: skills, learning requests, bookings, credits ledger, reviews, reports, and moderation.
- Real-time private chat via **Socket.IO**.
- Background jobs (emails, push notifications, scheduled tasks) via **BullMQ** on **Redis**.
- Data access to **PostgreSQL** through **Prisma**.
- File uploads through a cloud-compatible storage abstraction.

## Planned Technologies

NestJS · TypeScript · Prisma · PostgreSQL · Redis · BullMQ · Socket.IO · Jest
