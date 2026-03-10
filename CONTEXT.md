# RosterReady – Project Context

> **For Claude:** Read this file at the start of every session via:
> `https://raw.githubusercontent.com/MitchPeterson/rosterreadyv1/main/CONTEXT.md`
> Then read any specific HTML files you'll be editing before touching them.

---

## 🏢 What Is This?

**RosterReady** is a youth sports player evaluation SaaS app. The admin company (RosterReady) runs tryout evaluations for multiple client organizations (softball/baseball clubs). Built as a **multi-page static HTML frontend** — no backend, no database, all simulated data.

**Deployed at:** `https://rosterreadyv1.vercel.app`
**GitHub:** `https://github.com/MitchPeterson/rosterreadyv1` (public)
**Stack:** Plain HTML + CSS + JavaScript. No frameworks, no build step.

---

## 👤 Who Builds This

**Mitch Peterson** — solo builder, small fintech/SaaS background. Works in Claude sessions and uploads files manually to GitHub (Vercel auto-deploys on push).

---

## 📊 Data Hierarchy

```
RosterReady Admin (owns the system)
  │
  ├── Staff Pool (evaluators — owned by Admin, assigned to events)
  │
  └── Organizations (clients — softball/baseball clubs)
       └── Events (tryouts)
            ├── Stations (Hitting, Infield, Outfield, Pitching, Base Running, Catcher)
            ├── Players (registered per event)
            └── Staff Assignments (which staff work which stations)
```

---

## 🎨 Design System

- **Font:** `Georgia, 'Times New Roman', serif` — used everywhere
- **Logo file:** `RR_Logo.png` (root of repo) — NOT RR_Logo_2.png
- **Colors:**
  - Primary Red: `#E63946`
  - Deep Red: `#C1121F`
  - Light Blue: `#4A90E2`
  - Accent Teal: `#1ABC9C`
  - Accent Purple: `#9B59B6`
  - Dark: `#1a1a2e`
  - Background: `#f0f2f5`
  - Border: `#e2e8f0`
- **Style:** Card-based, rounded corners (14–16px), subtle shadows, clean white cards on light gray background

---

## 📁 File Inventory & Status

### ✅ Complete & Working

| File | Description | Notes |
|------|-------------|-------|
| `index.html` | Landing page — role selector (Player, Parent, Coach, Admin) | Working |
| `admin.html` | Org list + Add Org + Staff Management section | All buttons linked |
| `organization-create.html` | 5-step wizard to add new org | Full flow + success screen |
| `organization-details.html` | Org profile — 5 tabs: Overview, Events, Admins, Activity, Settings | Working |
| `organization-edit.html` | Edit org — section nav + sticky save bar | Working |
| `event-list.html` | All events for an org — upcoming/active/past | Working |
| `event-create.html` | 5-step event creation wizard | Working |
| `event-dashboard.html` | Manage one event — 6 tabs | Stations tab ✅, others partial |
| `player.html` | Player dashboard — 4 tabs | Existing, not recently edited |
| `parent.html` | Parent dashboard — 3 tabs | Existing, not recently edited |
| `coach.html` | Coach scoring interface | ⚠️ BROKEN — see below |

### ❌ Not Built Yet

| File | Description | Priority |
|------|-------------|----------|
| `staff.html` | Staff pool management page | 🟡 Medium |

---

## 🔗 Navigation Map

```
index.html
  └── admin.html
        ├── organization-create.html → organization-details.html
        ├── organization-details.html
        │     ├── organization-edit.html
        │     └── event-create.html
        └── [staff.html — NOT BUILT]

event-list.html → event-dashboard.html (6 tabs)
coach.html (standalone scoring view)
player.html (standalone player view)
parent.html (standalone parent view)
```

---

## 🚨 Known Bugs (Fix These First)

### 1. `coach.html` — Score Buttons Broken (HIGH)
Template literals used in plain HTML — they render as literal text `${[1,2,3...]}` instead of buttons. The score button row needs to be rewritten as real HTML.

### 2. `admin.html` — Manage Staff Pool links to wrong page (MEDIUM)
Currently `href="event-dashboard.html"` — should link to `staff.html` once built.

---

## 🔴 Next Session Priorities

**In order:**

1. **Fix `coach.html`** — rewrite score buttons as real HTML, make the scoring flow functional
2. **Players tab in `event-dashboard.html`** — roster list with name, jersey #, age group, check-in toggle
3. **Staff tab in `event-dashboard.html`** — show staff assigned per station with role
4. **Scores tab in `event-dashboard.html`** — grid of player scores per station (read-only summary view)
5. **Build `staff.html`** — staff pool management (add/edit/remove evaluators)
6. **Export Results** — CSV download of ranked player scores post-event

---

## 🏟️ Station Definitions (Spring 2024 Tryouts — 12U & 14U)

| # | Station | Ages | Criteria | Scoring |
|---|---------|------|----------|---------|
| 1 | ⚾ Hitting | 12U, 14U | Swing Mechanics, Contact Quality, Power | 1–10 |
| 2 | 🧤 Infield | 12U, 14U | Fielding Mechanics, Footwork & Range, Arm Strength | 1–10 |
| 3 | 🥎 Outfield | 12U, 14U | Catching Ability, Routes & Jumps, Throw Accuracy | 1–10 |
| 4 | ⚡ Pitching | 14U only | Velocity, Accuracy & Command, Pitch Mix | 1–10 |
| 5 | 🏃 Base Running | 12U, 14U | Raw Speed, Base Running IQ | 1–10 |
| 6 | 🎯 Catcher | 14U only | Receiving & Blocking, Pop Time to 2B | 1–10 |

**Scoring Rules:** Integers only (1–10) · Max 3 criteria per station · Aggregation: Median · Weighting: Equal

---

## 👥 Sample Data

### Organizations
- **Rosemount Thunder Softball** — 3 teams, 45 players, Pro Tier, Rosemount MN
- **Minnesota Valley Fastpitch** — 5 teams, 78 players

### Main Contact (Rosemount Thunder)
- Sarah Johnson — sarah@rts.org — Club Director — Owner access

### Staff Pool (12 members, sample)
- Coach Smith, Coach Martinez, Jamie Davis, T. Rodriguez, B. Kim, P. Lopez, A. Williams, M. Jackson, D. Thompson, L. Nguyen, R. Barnes, S. Chen

### Sample Players (Spring 2024 Tryouts)
- Sarah Johnson — Jersey #12 — Group 3 — 14U
- Emma Davis — Jersey #8 — Group 3 — 14U

---

## 📋 Session Log

| Date | What Was Built |
|------|---------------|
| Session 1 | index, player, parent, coach, admin, event-list, event-create, event-dashboard (initial) |
| Session 2 | organization-create, organization-details, organization-edit |
| Session 3 | Fixed logo (RR_Logo_2 → RR_Logo), fixed admin.html nav links, rebuilt event-dashboard with working Stations tab |
