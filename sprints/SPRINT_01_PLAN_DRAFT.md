# ClinicIQ — Sprint 01: Front-End Build-Out
## DRAFT — Needs codebase structure to finalize execution traces

---

## SPRINT GOAL

Complete all front-end UI pages and components for the ClinicIQ platform MVP. Every screen, every tab, every flyout, every builder view — fully functional with mock data, matching the specs in `prompts/`.

---

## WHAT NEEDS TO BE BUILT (from the spec backlog)

### Already Built (by Claude Code — needs verification):
- [ ] Sign-up page (`/signup`)
- [ ] Onboarding screen (`/onboarding`) — conversation flow + progress card
- [ ] IQ Workspace (`/iq`) — 3-panel layout, chat, right panel with tabs
- [ ] Engines page (`/engines`) — engine library, my engines, template cards
- [ ] Settings page (`/settings`) — profile, billing, team, notifications, API

### Needs Fixing (from today's session):
- [ ] **IQ Chat** — Kill welcome splash screen, IQ always speaks first (CLAUDE_CODE_IQ_CHAT_FIX.md)
- [ ] **Dashboard tab** — Revert to original + add Revenue Pulse, Engines, Calendar, Competitive Radar, Performance Spotlight, Proof Bank nudge (CLAUDE_CODE_DASHBOARD_FINAL.md)
- [ ] **Builders tab** — Remove workflow pills, show all 12 builders (CLAUDE_CODE_BUILDERS_TAB_FIX.md)
- [ ] **Engines flow** — Build with IQ stays on /iq, ⚡ Engine tab in right panel, tabs never hide (CLAUDE_CODE_ENGINES_FLOW_FIX_v3.md)
- [ ] **More flyout** — Strip to 5 items, zero redundancy (CLAUDE_CODE_MORE_FLYOUT_FINAL.md)
- [ ] **+ New flyout** — Ask IQ, Quick Capture, Upload, New Conversation (CLAUDE_CODE_NEW_FLYOUT_REDESIGN.md)
- [ ] **Settings page** — Expand to 8 tabs, all forms functional (CLAUDE_CODE_SETTINGS_PAGE_v2.md)

### Not Yet Built:
- [ ] **Home page** (`/home`) — Full CEO dashboard
- [ ] **Teams page** (`/teams`) — Members, roles, activity, settings
- [ ] **Drive page** (`/drive`) — File manager (Genspark Drive clone)
- [ ] **12 Builder views** — Each builder's right-panel experience (prompts/builders/01–12)
- [ ] **More flyout pages** — /notifications, /hub, /whats-new, /analytics, /channels, /services, /training
- [ ] **Responsive** — Tablet + mobile layouts for all pages

---

## PROPOSED AGENT ROSTER

| Agent | Code Name | Territory | Wave |
|-------|-----------|-----------|------|
| **DESIGN** | HOTEL | Design system, shared components, tokens, icons | 1 |
| **DATA** | FOXTROT | Mock data layer, types/interfaces, state management | 1 |
| **LAYOUT** | ALPHA | Core layout: sidebar, 3-panel shell, routing, navigation | 2 |
| **DASHBOARD** | BRAVO | Dashboard tab, Home page, all metric/chart components | 2 |
| **BUILDERS** | CHARLIE | All 12 builder views (right panel experiences) | 3 |
| **PAGES** | DELTA | Engines page, Teams page, Drive page, Settings page | 3 |
| **FLYOUTS** | ECHO | + New flyout, More flyout, notification panel, all flyout subpages | 3 |
| **RESPONSIVE** | FOXTROT-2 | Mobile/tablet layouts, bottom tab bar, responsive breakpoints | 4 |
| **RED TEAM** | ROMEO | Adversarial review — break everything before merge | 5 |
| **LEAD** | GOLF | Merge authority, integration testing, ship decision | 6 |

---

## WAVE STRUCTURE

### Wave 0: ORCHESTRATOR
- Read codebase structure
- Write execution traces for every agent
- Generate DISPATCH.md + per-agent task docs
- Generate activation prompts

### Wave 1: Foundation (no dependencies)
- **DESIGN (HOTEL):** Establish/verify design tokens, shared components (Button, Card, Badge, Toggle, Input, Modal, Toast), icon library, color system
- **DATA (FOXTROT):** Define TypeScript interfaces for all mock data (engines, content, emails, ads, funnels, notifications, billing, team, training), create mock data files, set up state management patterns

### Wave 2: Core Layout (depends on Wave 1)
- **LAYOUT (ALPHA):** Fix/verify the 3-panel layout shell, sidebar with all items (correct icons, correct routes), routing for all pages, right panel tab system (tabs never hide), chat component (IQ always speaks first)
- **DASHBOARD (BRAVO):** Dashboard tab rebuild (FINAL spec), Home page (/home), all metric components (IQ Score gauge, Revenue Pulse, Performance Spotlight, Competitive Radar, etc.)

### Wave 3: Features (depends on Wave 2)
- **BUILDERS (CHARLIE):** All 12 builder right-panel views using the Pattern A/B/C system from prompts/builders/01–12
- **PAGES (DELTA):** Engines page (full — library, my engines, detail, flow), Teams page, Drive page, Settings page (8 tabs)
- **FLYOUTS (ECHO):** + New flyout (Ask IQ, Quick Capture, Upload), More flyout (5 items), all subpages (/notifications, /hub, /whats-new, /training, /channels, /services)

### Wave 4: Polish (depends on Wave 3)
- **RESPONSIVE (FOXTROT-2):** Mobile and tablet layouts for every page, bottom tab bar for mobile, responsive breakpoints, flyout behavior on mobile

### Wave 5: Review
- **RED TEAM (ROMEO):** Break everything — find broken routes, inconsistent styling, missing states, accessibility gaps, edge cases

### Wave 6: Merge + Ship
- **LEAD (GOLF):** Merge all branches in order (DESIGN → DATA → LAYOUT → DASHBOARD → BUILDERS → PAGES → FLYOUTS → RESPONSIVE), build + test after every merge, ship decision

---

## TERRITORY MAP (file-level ownership)

**⚠️ DRAFT — Needs actual file structure to finalize**

```
src/
├── components/
│   ├── ui/              → DESIGN (shared components)
│   ├── layout/          → LAYOUT (sidebar, panels, shell)
│   ├── dashboard/       → DASHBOARD (metric cards, charts, gauges)
│   ├── builders/        → BUILDERS (12 builder views)
│   ├── flyouts/         → FLYOUTS (New, More, notifications)
│   └── chat/            → LAYOUT (IQ chat component)
├── pages/
│   ├── iq/              → LAYOUT (workspace shell)
│   ├── home/            → DASHBOARD (CEO dashboard)
│   ├── engines/         → PAGES (engines page + detail)
│   ├── teams/           → PAGES
│   ├── drive/           → PAGES
│   ├── settings/        → PAGES (8 tabs)
│   ├── notifications/   → FLYOUTS
│   ├── hub/             → FLYOUTS
│   ├── whats-new/       → FLYOUTS
│   ├── training/        → FLYOUTS
│   └── signup/          → LAYOUT (already built)
├── data/
│   ├── mock/            → DATA (all mock data)
│   └── types/           → DATA (TypeScript interfaces)
├── styles/
│   └── tokens/          → DESIGN (design tokens, colors, spacing)
└── lib/
    └── state/           → DATA (state management)
```

---

## SUCCESS CRITERIA

The sprint is ACHIEVED when:
1. Every route in the platform renders correctly with mock data
2. Every tab on the right panel works and shows its content
3. Every flyout opens, shows content, and closes properly
4. Every builder view follows its Pattern (A, B, or C) from the spec
5. Navigation between all pages works without broken links
6. The 3-panel layout never breaks (sidebar + chat + right panel always visible on /iq)
7. All designs match the spec colors, typography, spacing, and component patterns
8. Mobile/tablet responsive layouts work for all pages

---

## WHAT I NEED FROM RYAN TO FINALIZE

1. **The front-end repo** — GitHub URL or local path to the React codebase Claude Code has been building
2. **File structure** — `find src -name "*.tsx" | head -50` output (or similar)
3. **How many Claude Code sessions** are you running? (This determines how many parallel agents we can dispatch)
4. **Any pages that are "done" and locked** — that we should NOT touch in this sprint

Once I have the codebase structure, I'll write the real execution traces and generate the full DISPATCH.md + per-agent task docs + activation prompts.
