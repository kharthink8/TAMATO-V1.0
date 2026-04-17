# WorkloadHQ (MVP+)

WorkloadHQ is a workload-first task & project management web app for 15–30 team members running multiple projects.

This demo workspace is tailored for an in-house **Branding & Digital Marketing** department: brand initiatives, campaign launches, social ops, paid performance, SEO, email/CRM, web updates, approvals, and reporting.

## What’s implemented
- Auth: demo login via Credentials (password `demo`)
- Views: Board, Table, Calendar, Timeline, Gantt, Workload
- My Work: Inbox/Today/Upcoming + focus timer (MVP)
- Org hierarchy: Departments, teams, reporting managers (Admin/Super Admin)
- Approvals: Submit → approve/reject → close (with approval chain + audit log)
- Prisma + Postgres with a realistic seeded dataset
- Product docs/specs: `docs/`

## Local setup
### Prerequisites
- macOS + **Docker Desktop** (must be running)
- No global Node/npm required (this repo ships a local Node toolchain in `../.tools/`)

### 1) Enable local Node/npm
```bash
source scripts/use-local-node.zsh
```

### 2) Start Postgres (Docker)
```bash
npm run db:up
```

Postgres runs on port `55432` (to avoid conflicts with local Postgres).

### 3) Configure env
```bash
cp .env.example .env
```

### 4) Reset + seed demo data
```bash
npm run db:reset
npm run db:seed
```

### 5) Run the app
```bash
npm run dev
```

Open `http://localhost:3000`.

## Demo login
- Password is always `demo`
- `/login` includes a demo-user dropdown (no copy/paste needed)
- Approvers can use `/approvals` for their queue
- Admin/Super Admin: `/admin/users`, `/admin/org`, `/admin/audit`

### Seeded demo users
| Name | Email | Role | Team |
|---|---|---|---|
| Aisha Raman | aisha.raman@moddwell.example | Super Admin | Brand Strategy Team |
| Dinesh Kumar | dinesh.kumar@moddwell.example | Admin | Operations & Web Team |
| Karthik Menon | karthik.menon@moddwell.example | Department Head | Brand Strategy Team |
| Rhea Varma | rhea.varma@moddwell.example | Department Head | Creative Studio |
| Sanjana Iyer | sanjana.iyer@moddwell.example | Department Head | Content & Social Team |
| Vivek Nair | vivek.nair@moddwell.example | Department Head | Performance & Lifecycle Team |
| Ananya Rao | ananya.rao@moddwell.example | Team Lead | Operations & Web Team |
| Nila Krishnan | nila.krishnan@moddwell.example | Team Member | Brand Strategy Team |
| Devika Shah | devika.shah@moddwell.example | Team Member | Creative Studio |
| Arun Joel | arun.joel@moddwell.example | Team Member | Creative Studio |
| Meera Doss | meera.doss@moddwell.example | Team Member | Creative Studio |
| Ishaan Paul | ishaan.paul@moddwell.example | Team Member | Content & Social Team |
| Pranav Bedi | pranav.bedi@moddwell.example | Team Member | Content & Social Team |
| Harini Joseph | harini.joseph@moddwell.example | Team Member | Content & Social Team |
| Sneha Kapoor | sneha.kapoor@moddwell.example | Team Member | Performance & Lifecycle Team |
| Farah Ali | farah.ali@moddwell.example | Team Member | Performance & Lifecycle Team |
| Rahul Deshpande | rahul.deshpande@moddwell.example | Team Member | Performance & Lifecycle Team |
| Keerthi Soman | keerthi.soman@moddwell.example | Team Member | Operations & Web Team |
| Zoya Khan | zoya.khan@moddwell.example | Team Member | Operations & Web Team |
| Naveen Raj | naveen.raj@moddwell.example | Team Member | Operations & Web Team |

## Troubleshooting
- **`npm: command not found`**: run `source scripts/use-local-node.zsh` (it must be sourced, not executed).
- **Docker errors** like `failed to connect ... docker.sock ... no such file`: Docker Desktop isn’t running yet. Start it (`open -a Docker`), wait until it’s “Running”, then re-run `npm run db:up`.
- **`ERR_CONNECTION_REFUSED` on `http://localhost:3000`**: the web server isn’t running. Start it with `npm run dev` and keep that terminal open.
- **Sign-in “Server configuration error”**: open `http://localhost:3000/api/health` and ensure it returns `ok: true`. If not, verify `.env` (`DATABASE_URL`, `NEXTAUTH_SECRET`), ensure Postgres is running, then restart `npm run dev`.

## Docs
See `docs/` for PRD, architecture, ERD, API contract, workload spec, and test plan.

## Notes
- Prisma uses a Postgres driver adapter (`@prisma/adapter-pg`). Connection URL lives in `prisma.config.ts`.
- Calendar OAuth is stubbed in MVP; seeded calendar connections/events are included for UI overlays.
