# WorkloadHQ (MVP+)

WorkloadHQ is a workload-first task & project management web app for 15–30 team members running multiple projects.

## What’s implemented (so far)
- Auth: demo login via Credentials (password `demo`)
- Workspace dashboard + portfolio
- Project views: Table, Board (DnD status), Workload (capacity vs assigned effort)
- My Work: Inbox/Today/Upcoming + focus timer (client-only MVP)
- Prisma v7 + Postgres with a realistic seeded dataset
- Product docs/specs: `docs/`

## Local setup
### 0) Enable local Node.js (required if you don’t have npm installed)
This workspace includes a local Node toolchain under `../.tools/`. In a new terminal:
```bash
source scripts/use-local-node.zsh
```

### 1) Start Postgres
```bash
npm run db:up
```

Postgres runs on port `55432` (to avoid conflicts with local Postgres).

### 2) Configure env
```bash
cp .env.example .env
```

### 3) Migrate + seed
```bash
npx prisma migrate dev
npm run db:seed
```

### 4) Run the app
```bash
npm run dev
```

cd '/Users/karthiv/Desktop/MODDWELL/SELF STUDY/TASK MANAGEMENT TOOL/workloadhq'
source scripts/use-local-node.zsh
npm -v
npx -v
npm run db:up
cp .env.example .env
npx prisma migrate dev
npm run db:seed
npm run dev



Open `http://localhost:3000`.

## Demo login
- Use any seeded email from Admin → Users (e.g. `*.@moddwell.example`)
- Password is always `demo`

## Docs
See `docs/` for PRD, architecture, ERD, API contract, workload spec, and test plan.

## Notes
- Prisma v7 uses a Postgres driver adapter (`@prisma/adapter-pg`). Connection URL lives in `prisma.config.ts`.
- Calendar OAuth is stubbed in MVP; seeded calendar connections/events are included for UI overlays later.


demo users email id and role password: demo
Here are the seeded demo logins (email → role):

mohammad-crist@moddwell.example → ADMIN
brionna-hilll@moddwell.example → PROJECT_MANAGER
claudia-leffler@moddwell.example → PROJECT_MANAGER
laury-aufderhar-phd@moddwell.example → PROJECT_MANAGER
bryan-barton-i@moddwell.example → TEAM_LEAD
joel-bayer@moddwell.example → TEAM_LEAD
tracey-schowalter-haag@moddwell.example → TEAM_LEAD
bobbie-nienow@moddwell.example → TEAM_MEMBER
charlotte-schowalter@moddwell.example → TEAM_MEMBER
delmer-roob@moddwell.example → TEAM_MEMBER
dr.-christelle-lindgren@moddwell.example → TEAM_MEMBER
hope-shields@moddwell.example → TEAM_MEMBER
john-denesik-dds@moddwell.example → TEAM_MEMBER
keara-kunde@moddwell.example → TEAM_MEMBER
laron-bogisich@moddwell.example → TEAM_MEMBER
lew-bergnaum@moddwell.example → TEAM_MEMBER
lon-kozey@moddwell.example → TEAM_MEMBER
misael-blanda@moddwell.example → TEAM_MEMBER
miss-caroline-blanda-jr.@moddwell.example → TEAM_MEMBER
mrs.-desiree-schumm@moddwell.example → TEAM_MEMBER