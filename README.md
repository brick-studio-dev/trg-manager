# TRG Manager — Modern Management System

Management app for auto repair shops: clients, vehicles, repairs and
invoicing in one place, built to replace the spreadsheet or paper notebook
many shops still use. Deployed and in real use (login required, no public
sign-up).

Stack: **React + Vite** → **Vercel** (free) + **Supabase** (free)

---

## 🆕 What's new in this version

- **Redesigned dashboard**: vehicles, clients, this month's repairs (with trend and mini-chart), and revenue billed this year (with trend and mini-chart)
- **Simplified new repair flow**: no promised date or VAT field, optional direct amount
- **Optional vehicle photo**: upload and change photo from the vehicle record

---

## 🚀 Step-by-step setup guide

### 1. Create a Supabase project

1. Go to [supabase.com](https://supabase.com) → **New project**
2. Pick a name (e.g. `taller-trg`) and region **EU West**
3. Wait 1-2 min for the DB to be created

### 2. Create the database

1. In the Dashboard → **SQL Editor** → **New query**
2. Copy and paste the full contents of `supabase/schema.sql`
3. Click **Run** → should show "Success"

### 3. Create an admin user

In Supabase → **Authentication** → **Users** → **Add user**:
- Email: yours
- Password: a secure password
- Check "Auto Confirm User"

### 4. Configure environment variables

```bash
cp .env.example .env.local
```

Fill in with the values from **Supabase → Settings → API**:
```
VITE_SUPABASE_URL=https://xxxxxxxxx.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGci...
```

### 5. Install and run locally

```bash
npm install
npm run dev
```

---

## ☁️ Deploy to Vercel (free)

1. Go to [vercel.com/new](https://vercel.com/new) and import this GitHub repository.
2. Vercel auto-detects the **Vite** preset (build command `vite build`, output `dist`).
3. Add the environment variables (`VITE_SUPABASE_URL`, `VITE_SUPABASE_ANON_KEY`) before deploying.
4. Every `git push` to `main` automatically deploys a new version.

---

## ⚠️ Important: pause after inactivity

**Supabase** pauses free projects after ~7 days of inactivity. To restore it: open the dashboard → **"Restore project"**.

Vercel doesn't need manual reactivation: since it's directly connected to the repo, every change deploys on its own.

---

## 📂 Project structure

```
taller-trg/
├── supabase/
│   └── schema.sql
├── src/
│   ├── lib/supabase.js
│   ├── context/AuthContext.jsx
│   ├── components/
│   │   ├── Layout.jsx
│   │   ├── EstadoBadge.jsx
│   │   └── MiniSparkline.jsx
│   └── pages/
│       ├── LoginPage.jsx
│       ├── DashboardPage.jsx
│       ├── ReparacionesPage.jsx
│       ├── ReparacionDetallePage.jsx
│       ├── NuevaReparacionPage.jsx
│       ├── ClientesPage.jsx
│       ├── ClienteDetallePage.jsx
│       ├── VehiculosPage.jsx
│       └── VehiculoDetallePage.jsx
├── vite.config.js
├── tailwind.config.js
└── package.json
```
