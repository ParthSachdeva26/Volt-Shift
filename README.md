# Volt-Shift (Project 96)

> **Machine Learning-Based Approach for Reduction of Energy Consumption in Hybrid Energy Storage Electric Vehicles (HESS)**

Volt-Shift is an interactive powertrain simulation platform and energy management laboratory for battery + supercapacitor electric vehicles. It enables engineers and researchers to evaluate real-time power splitting strategies under standard driving cycles (WLTC Class 3b, US06, UDDS, HWFET), minimizing total energy consumption and protecting the battery from aggressive current degradation.

---

## Team & Roles

| Contributor | Role | Focus Areas |
|---|---|---|
| **Parth Sachdeva** ([@ParthSachdeva26](https://github.com/ParthSachdeva26)) | **Frontend Engineering & UI** | Next.js 14 App Router, in-browser simulation engine (FISTA MPC & ML policy), Tailwind CSS design system, and interactive telemetry charts. |
| **Raj Maheshwari** ([@rajmaheshwari3001-dev](https://github.com/rajmaheshwari3001-dev)) | **Backend Architecture & Security** | Supabase database schema, PostgreSQL 17 migrations, 30-assertion Row Level Security (RLS) test suite, and seed synchronization tooling. |

---

## Repository Layout

```
Volt-Shift/
├── frontend/               # Next.js 14 web application (Vercel)
│   ├── src/app/            # App Router: simulation lab, vehicle tuner, drive cycles, auth
│   ├── src/components/     # UI design system, interactive SVG/Canvas charts, landing narrative
│   ├── src/lib/hess/       # In-browser client-side physics and ML controller engine
│   └── tests/              # Parity tests and validation suites
├── backend/                # Supabase database & server tooling
│   ├── supabase/migrations/# SQL migrations (0001_init, 0002_seed, 0003_harden_functions)
│   └── scripts/            # 30-assertion RLS test suite, migration runner, health scan
└── docs/                   # Architectural & research documentation
    ├── 01-research-and-discovery.md
    ├── 02-design-system.md
    └── 03-backend.md
```

---

## Core Capabilities

1. **Client-Side Simulation Lab (`/simulate`):**
   - Run physics-accurate HESS simulations directly in the browser in `< 50 ms`.
   - Side-by-side comparison of **Rule-Based**, **Model Predictive Control (MPC)**, **Distilled ML Policy**, and **Battery-Only** baselines.
   - Live telemetry: battery current ($I_{\text{bat}}$), supercapacitor voltage ($V_{\text{sc}}$), power split ($P_{\text{bat}}$ vs $P_{\text{sc}}$), and DC/DC converter losses.

2. **Vehicle & Powertrain Tuner (`/vehicles`):**
   - Interactive configuration of vehicle mass, frontal area, drag coefficient ($C_d$), Li-ion battery pack capacity, and supercapacitor module sizing.

3. **Enterprise Database & Security (`backend/`):**
   - Complete PostgreSQL schema with automated user profile triggers and immutable telemetry logs.
   - Verified by a **30-assertion Row Level Security (RLS)** test suite ensuring strict tenant isolation across anonymous, authenticated, and service roles.

---

## Getting Started

### 1. Frontend Development
```bash
cd frontend
cp .env.example .env.local
npm install
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) to view the application.

To run frontend tests and linting:
```bash
npm test          # Runs ML parity and controller tests
npm run typecheck # Verifies TypeScript type safety
```

### 2. Backend Verification
```bash
cd backend
cp .env.example .env
npm install
npm run db:test   # Runs the 30-assertion RLS security test suite
```

---

## Tech Stack

- **Frontend:** Next.js 14, React 18, TypeScript, Tailwind CSS, Lucide Icons, SVG/Canvas Charting.
- **Backend / Database:** PostgreSQL 17, Supabase Auth, Row Level Security (RLS).
- **Control & Simulation:** In-browser FISTA accelerated projected-gradient MPC solver, Random Forest distilled policy.
