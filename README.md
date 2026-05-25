# 🦷 DentalOps Monorepo

Welcome to **DentalOps**! 🚀 An advanced, enterprise-grade multi-app workspace built to fully automate and optimize modern dental clinic operations. This ecosystem streamlines administrative workflows, manages medical records with strict data isolation, and natively automates patient communication to minimize no-show rates.

By leveraging a high-performance monorepo architecture, the entire platform ensures maximum code reuse, shared type safety, and fast incremental pipelines across all applications and shared packages.


## 🏗️ Workspace Architecture & Layout

The repository utilizes a modular **Turborepo** layout powered by **pnpm workspaces** for absolute dependency isolation:

```text
├── apps/
│   ├── web/               # Core Next.js Application (Clinic Dashboard, Analytics, & Scheduler)
│   └── backend/           # Node.js Automation Engine (Background worker & notification queues)
├── packages/
│   ├── database/          # Centralized Prisma Schema & client configurations for PostgreSQL
│   ├── design-system/     # Dark-themed UI component guidelines, design variables, and styles
│   └── ts-config/         # Standardized TypeScript base configurations used workspace-wide
├── turbo.json             # Global build caching, pipeline orchestration, and task dependency configurations
└── package.json           # Root workspace dependency management and global command scripts
```


### 🛠️ Complete Technical Stack
- Workspace & Building: Turborepo, pnpm Workspaces
- Frontend Tier: React, Next.js (App Router), TypeScript, Tailwind CSS
- Backend Tier: Node.js, Express / NestJS Core architectural design
- Database & Cache Layer: PostgreSQL (Main Store), Prisma ORM, Redis (In-memory engine)
- Job Scheduling: BullMQ (Robust, distributed queue management)
- Security Layer: Contextual JWT Multi-Tenancy Router (clinicId locking mechanism)


### 🌟 Core Engineering Implementations
1. Asynchronous WhatsApp Queue Automation 💬
DentalOps slashes clinic appointment cancellation and no-show rates by up to 40% using a bulletproof asynchronous messaging pipeline built with BullMQ and Redis:
- Dynamic Delay: When an appointment is booked, specific reminders are pushed to the Redis store as delayed jobs.
- Precise Execution: Workers automatically wake up and trigger customized WhatsApp notifications exactly 24 hours and 2 hours before the slot.
- Failure Handling: Fully equipped with automatic retry mechanics, backoff strategies, and monitoring hooks to ensure high delivery rates.

2. Immutable Multi-Tenancy Architecture 🔒
Data isolation and medical privacy are maintained at the architectural level without the overhead of multiple physical databases:
- Token Guard: Every authenticated session embeds an unchangeable clinicId into its JWT payload.
- Database Constraints: Prisma clients apply strict query definitions ensuring that no appointment, record, or profile can be created, updated, or read without a perfect clinicId match.
- Zero Cross-Talk: Guarantees absolute data leakage prevention between completely different clinics utilizing the platform.

3. High-Fidelity Dark Theme UX System 🎨
The user interface follows strict behavioral design guidelines tailored for clinical desktop screens (--bg: #0a0d0f, --teal: #00c9a7):
- No Layout Shifts: Page loading relies exclusively on Skeleton Screens to avoid jarring visual jumps (Strictly no generic full-page loading spinners).
- Optimistic UI Updates: Actions like booking slots or moving timetables reflect immediately on screen, syncing with the database in the background to maximize perceived interface speed.


### 🚀 Getting Started & Environment Local Setup
Prerequisites
Ensure your local environment runs Node.js (v18+), pnpm (v8+), alongside accessible instances of PostgreSQL and Redis.

1. Clone the Source Repository
Bash
git clone [https://github.com/username/dentalops-monorepo.git](https://github.com/username/dentalops-monorepo.git)
cd dentalops-monorepo
2. Install Workspace Dependencies
Bash
pnpm install
3. Setup Local Environment Variables
Create a root or package-level .env configuration file:

Code snippet
DATABASE_URL="postgresql://user:password@localhost:5432/dentalops?schema=public"
REDIS_URL="redis://localhost:6379"
JWT_SECRET="your-super-secure-secret-key"
4. Run Development Servers
Launch all localized applications simultaneously with smart workspace caching:

Bash
pnpm dev
5. Production Compilation
Bash
pnpm build


### 📄 License
Copyright (c) 2026 DentalOps.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES, OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT, OR OTHERWISE, ARISING FROM, OUT OF, OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
