# ClinicIQ — Sprint 01: DISPATCH
## Front-End Completion Sprint — Every page, every tab, every builder, every flyout
## Codebase: Next.js 16 + React 19 + Tailwind v4 + shadcn/ui + Zustand

---

## SPRINT GOAL

Complete all front-end UI for the ClinicIQ platform MVP. Fix all issues identified in the April 8 review session. Build the remaining 6 builder views. Finish all pages. Everything functional with mock data.

---

## CODEBASE ARCHITECTURE (verified from repo)

```
ClinicIQFrontend/
├── app/
│   ├── (auth)/          # Auth pages (login, signup, forgot-password)
│   ├── (platform)/      # All platform pages
│   │   ├── chat/        # IQ workspace (/chat is the IQ route)
│   │   ├── workflows/   # Engines page (currently named "workflows")
│   │   ├── home/        # Home/CEO dashboard
│   │   ├── settings/    # Settings (account, billing, notifications)
│   │   ├── teams/       # Teams
│   │   ├── drive/       # Drive
│   │   ├── onboarding/  # Onboarding
│   │   └── [10 more]    # analytics, channels, hub, notifications, etc.
│   └── layout.tsx       # Root layout
├── components/
│   ├── layout/          # platform-shell, sidebar-rail, workspace-panel, engine-build-panel
│   ├── chat/            # chat-panel, chat-input, chat-message, chat-welcome
│   ├── dashboard/       # All dashboard sections (pulse, iq-score, attention, engines, etc.)
│   ├── builders/        # 6 builder views built (content, funnel, webinar, email, ad, lead-magnet)
│   ├── flyouts/         # more-flyout, new-flyout + sub-panels
│   ├── settings/        # 8 settings tabs (profile, appearance, billing, etc.)
│   ├── onboarding/      # Full onboarding flow
│   ├── ui/              # 56 shadcn/ui components
│   └── [artifacts, billing, team, profile, context]
├── stores/              # Zustand: ui-store, chat-store, build-queue-store, onboarding-store
├── types/index.ts       # All TypeScript types
├── hooks/               # use-chat, use-mobile, use-onboarding, use-toast
└── lib/                 # utils, api, services, mock-data
```

**Key routes:** `/chat` (IQ workspace), `/workflows` (engines), `/home`, `/settings/*`, `/teams`, `/drive`, `/onboarding`

**3-panel layout:** `SidebarRail` (72px) + main content + `WorkspacePanel` (right panel with tabs). Resizable panels. WorkspacePanel only shows on `/chat`.

**Right panel tabs (workspace-panel.tsx):** Dashboard, Brand, Strategy, Builders, Content, Files, Calendar, Schedules, Channels, Services, Training, Settings + dynamic ⚡ Engine tab.

**Builders already built:** Content, Funnel, Webinar, Email, Ad Creative, Lead Magnet (6 of 12).

**Builders NOT built:** Program, Podcast, Sales Script, Website, Campaign, Challenge (6 remaining).

---

## AGENTS — 5 Parallel Agents

Keeping this tight — 5 agents, not 10. The codebase is well-structured enough that fewer, more focused agents will ship faster than many agents stepping on each other.

| Agent | Code Name | Territory | Wave | Chains |
|-------|-----------|-----------|------|--------|
| **ALPHA** | Core Fixes | Layout, chat, dashboard, flyouts — all the fixes from today | 1 | 8 |
| **BRAVO** | Builders | 6 remaining builder views + polish existing 6 | 2 | 6 |
| **CHARLIE** | Pages | Home, Teams, Drive, and all /more subpages | 2 | 7 |
| **DELTA** | Settings + Polish | Settings page expansion, responsive, final polish | 3 | 5 |
| **ECHO** | Red Team | Break everything, file issues | 4 | 1 |

---

## WAVE STRUCTURE

### Wave 1: ALPHA (Core Fixes) — No dependencies
Everything from today's review session. These are fixes to existing components, not new pages.

### Wave 2: BRAVO (Builders) + CHARLIE (Pages) — Parallel, depends on Wave 1
Both depend on Wave 1 fixes (the layout/chat/dashboard need to be right before building on top). BRAVO and CHARLIE work in parallel — zero file overlap.

### Wave 3: DELTA (Settings + Polish) — Depends on Wave 2
Settings expansion uses patterns established by the other agents. Responsive work needs all pages built first.

### Wave 4: ECHO (Red Team) — Depends on Wave 3
Adversarial review after everything is merged.

---

## AGENT ALPHA — Core Fixes (Wave 1)

**Territory:**
```
components/chat/chat-welcome.tsx          # Kill welcome splash
components/chat/chat-panel.tsx            # IQ speaks first
components/chat/chat-input.tsx            # Quick action chips below input
components/dashboard/dashboard-tab.tsx    # Revert + add new sections
components/dashboard/pulse-section.tsx    # Revenue Pulse
components/dashboard/iq-score-section.tsx # Add milestone gamification
components/dashboard/engines-section.tsx  # Active Engines section
components/dashboard/this-week-section.tsx # Calendar glance
components/dashboard/competitive-radar.tsx # New component
components/dashboard/performance-spotlight.tsx # Winner vs loser
components/dashboard/recommends-section.tsx # + proof bank nudge
components/dashboard/brand-growth-bar.tsx # Audience reach bar
components/dashboard/attention-section.tsx # Severity sorting
components/layout/workspace-panel.tsx     # Builders tab fix (all 12, no workflow pills)
components/flyouts/new-flyout.tsx         # Redesign: Ask IQ, Quick Capture, Upload
components/flyouts/new/*                  # Quick capture sub-panels
components/flyouts/more-flyout.tsx        # Strip to 5 items
components/flyouts/more/*                 # Sub-panels
components/layout/sidebar-rail.tsx        # Rename Workflows → Engines, icon update
```

### Chain A1 [P1]: Kill IQ Welcome Splash + IQ Speaks First
**Trace:** `components/chat/chat-welcome.tsx` → `components/chat/chat-panel.tsx`
**Signal:** Center chat shows splash screen ("What can I help you build?") with suggestion cards instead of IQ's first message.
**Fix:**
1. Delete or gut `chat-welcome.tsx` — remove the splash screen entirely (big icon, heading, subtitle, quick action pills, suggestion cards)
2. In `chat-panel.tsx` — ensure IQ's first message always renders as a chat bubble. Use mock data for Dr. Sarah Chen's morning briefing.
3. Move quick action hints to subtle chips below the chat input in `chat-input.tsx`: "💡 Quick Post · ✉️ Email · 📢 Ad · 📊 Performance · ⚡ New Engine" — 12px, muted, clickable.
**Verify:** Load `/chat` — no splash screen, IQ's first message visible as a chat bubble, chips visible below input.

### Chain A2 [P1]: Dashboard Tab — Revert + Revenue Pulse + New Sections
**Trace:** `components/dashboard/dashboard-tab.tsx` → all dashboard sub-components
**Signal:** Dashboard was redesigned (lost the original card layout). Need to revert to original and layer additions.
**Fix:** Rebuild `dashboard-tab.tsx` to render sections in this order:
1. `PulseSection` — $12,400 / 23 leads / 4 calls (NEW)
2. Greeting + IQ Score pill with milestone (EXISTING + milestone)
3. 4 Score Cards row (EXISTING — Ad 64, Funnel 78, Social 82, Email 58)
4. `BrandGrowthBar` — 14,200 total reach (NEW)
5. `AttentionSection` + `IqScoreSection` side by side (EXISTING)
6. `EnginesSection` + `ThisWeekSection` side by side (NEW)
7. `RecommendsSection` + `CompetitiveRadar` stacked left + `PerformanceSpotlight` right (MODIFIED)
8. Performance by Category with tabs (EXISTING)
9. Activity Feed (EXISTING)
- Add `CompetitiveRadar` component (new file)
- Modify `PerformanceSpotlight` to show winner AND loser (green + red)
- Add milestone to `IqScoreSection` ("🎯 4 pts to 75 — unlock Audience Insights")
- Add proof bank nudge to bottom of `RecommendsSection`
**Verify:** Dashboard tab shows all sections, 2-column layout for paired sections, no scroll-only layout.

### Chain A3 [P1]: Builders Tab — All 12, No Workflow Pills
**Trace:** `components/layout/workspace-panel.tsx` → builders tab section
**Signal:** Builders tab shows only 6 builders + has "Content Batch, Launch Campaign, Monthly Refresh" workflow pills.
**Fix:**
1. In workspace-panel.tsx, find the builders tab content section
2. Remove the workflow-type pills entirely
3. Ensure all 12 builders render in a 2×6 grid: Content, Funnel, Webinar, Email, Ad Creative, Lead Magnet, Program, Podcast, Sales Script, Website, Campaign, Challenge
4. Each card: emoji + name (bold) + one-line description + hover emerald border
5. Click → dispatch custom event `workspace-tab:builder-{name}` to trigger the right builder view
**Verify:** Builders tab shows 12 builders in 2-column grid, no workflow pills, each clickable.

### Chain A4 [P2]: Sidebar — Rename Workflows → Engines
**Trace:** `components/layout/sidebar-rail.tsx`
**Signal:** Sidebar shows "Workflows" with GitBranch icon. Should be "Engines" with Zap icon.
**Fix:** In sidebar-rail.tsx, change the nav item: label "Workflows" → "Engines", icon GitBranch → Zap, route stays `/workflows` (renaming the route is a separate concern).
**Verify:** Sidebar shows "Engines" with ⚡ icon, links to /workflows.

### Chain A5 [P2]: + New Flyout Redesign
**Trace:** `components/flyouts/new-flyout.tsx` → `components/flyouts/new/*`
**Signal:** Current flyout shows quick action pills + 12 builder grid + recent. Needs to become: Ask IQ input + New Conversation + Quick Capture (4 cards) + Upload + Recent.
**Fix:** Rebuild `new-flyout.tsx` and create sub-panels:
1. Section 1: Ask IQ textarea (3 rows, placeholder "What do you need?", mic + send button, suggestion examples below)
2. Section 2: New Conversation button (MessageSquarePlus icon)
3. Section 3: Quick Capture — 2×2 grid: Patient Story, Voice Note, Proof, Competitive Intel
4. Each capture card opens an inline panel (slide-in animation): `capture-patient-story.tsx`, `capture-voice-note.tsx`, `capture-proof.tsx`, `capture-competitive-intel.tsx`
5. Section 4: Upload drop zone
6. Section 5: Recent (last 5 conversations)
**Verify:** + New flyout opens with all 5 sections. Each Quick Capture card opens its inline panel. Upload zone accepts drag-and-drop.

### Chain A6 [P2]: More Flyout — Strip to 5 Items
**Trace:** `components/flyouts/more-flyout.tsx` → `components/flyouts/more/*`
**Signal:** More flyout has 9+ items. Strip to 5: Notifications, Hub, Help & Support, What's New, Download App.
**Fix:** Rebuild `more-flyout.tsx`:
1. Remove: Analytics, Channels, Services, Training, Appearance, Notification Settings, Language, Manage Account
2. Keep: Notifications (with inline panel), Hub (navigate to /hub), Help & Support (inline panel), What's New (navigate to /whats-new), Download App (inline panel)
3. Account footer: avatar + name + plan + [Sign Out] only. No "Manage Account" — gear icon handles that.
**Verify:** More flyout opens with exactly 5 items + account footer. Inline panels work.

### Chain A7 [P2]: Engine Flow — Build with IQ → ⚡ Engine Tab
**Trace:** `components/layout/engine-build-panel.tsx` → `components/layout/workspace-panel.tsx` → `stores/ui-store.ts`
**Signal:** "Build with IQ" creates a custom split-panel layout instead of using the standard 3-panel. Tabs disappear.
**Fix:**
1. Ensure workspace-panel.tsx NEVER hides the tab bar. The ⚡ Engine tab is a dynamic tab that appears when `buildingEngine` is set in ui-store.
2. The tab bar always renders all STATIC_TABS + the dynamic Engine tab (when active).
3. `engine-build-panel.tsx` renders INSIDE the tab content area (not as a panel replacement).
4. When "Build with IQ" is clicked from /workflows, navigate to /chat with engine context, set `buildingEngine` in store, which adds ⚡ Engine tab and auto-selects it.
5. IQ's first message in chat should be engine-specific (not the morning briefing).
**Verify:** Click "Build with IQ" on an engine → navigates to /chat → tab bar visible with all tabs + ⚡ Engine → Engine tab shows progress → can freely switch between tabs.

### Chain A8 [P3]: Engine Context Chat Messages
**Trace:** `components/chat/chat-panel.tsx` → `stores/chat-store.ts`
**Signal:** When arriving from "Build with IQ", IQ should send an engine-specific first message, not the generic briefing.
**Fix:**
1. In chat-panel.tsx, check for engine context (from ui-store `buildingEngine`)
2. If engine context exists, render engine-specific first message: "Let's build your [Engine Name]! Here's the plan: Step 1... Step 2... First up: [step 1 description]. Which avatar are we targeting?"
3. If no engine context, render the morning briefing first message
**Verify:** Navigate to /chat from engine → engine-specific first message. Navigate to /chat normally → morning briefing.

---

## AGENT BRAVO — Remaining 6 Builders (Wave 2)

**Territory:**
```
components/builders/program/          # NEW — all files
components/builders/podcast/          # NEW — all files
components/builders/sales-script/     # NEW — all files
components/builders/website/          # NEW — all files
components/builders/campaign/         # NEW — all files
components/builders/challenge/        # NEW — all files
components/layout/workspace-panel.tsx # Add imports + tab routing for new builders
```

**NOTE:** workspace-panel.tsx is shared with ALPHA. ALPHA finishes Wave 1 first. BRAVO's changes are ADDITIVE (new imports + new case statements in the tab switch). No conflict.

### Chain B1 [P1]: Program Builder View
**Trace:** NEW → `components/builders/program/`
**Pattern:** Pattern A (Brief → Generate → Rich Document View → Section Edit)
**Create:** `program-builder-view.tsx`, `program-outline.tsx`, `module-detail.tsx`, `types.ts`
**Spec:** Follow `prompts/builders/10_PROGRAM_BUILDER.md` (if exists) or build from the Pattern A template:
- Outline view: program architecture (name, transformation promise, 6–12 modules)
- Module list with expand/collapse
- Module detail: lesson scripts, worksheets, action items
- Mock data: "Signal Reset Protocol — 8 modules, 12 weeks"
**Wire into workspace-panel.tsx:** Add case `"builder-program"` in the tab content switch.
**Verify:** Click Program Builder in Builders tab → right panel shows program outline.

### Chain B2 [P1]: Podcast Builder View
**Pattern:** Pattern A (Brief → Generate → Document View)
**Create:** `components/builders/podcast/podcast-builder-view.tsx`, `episode-list.tsx`, `episode-detail.tsx`, `types.ts`
- Show architecture: show name, tagline, format, episode plan
- Episode list: 4 episodes with scripts/outlines
- Episode detail: full script with hook/bridge/value/CTA structure
- Repurposing section: carousel + Reels + blog post per episode
**Verify:** Click Podcast Builder → right panel shows podcast architecture + episode list.

### Chain B3 [P1]: Sales Script Builder View
**Pattern:** Pattern A (Brief → Generate → Document View)
**Create:** `components/builders/sales-script/sales-script-builder-view.tsx`, `script-section.tsx`, `objection-handler.tsx`, `types.ts`
- Script sections: Discovery, Transition, Offer Presentation, Value Stack, Objections (top 5), Close
- Each section expandable with full script text
- Objection handler: objection → emotional acknowledgment → logical reframe → proof close
- DM script variant tab
**Verify:** Click Sales Script Builder → right panel shows script outline with expandable sections.

### Chain B4 [P1]: Website Builder View
**Pattern:** Pattern A (Brief → Generate → Page Preview)
**Create:** `components/builders/website/website-builder-view.tsx`, `page-preview.tsx`, `section-editor.tsx`, `types.ts`
- Page list: Homepage, About, Services, Contact, Blog
- Page preview: styled mock of the rendered page
- Section editor: expandable accordion for each page section (hero, about, services, testimonials, CTA)
**Verify:** Click Website Builder → right panel shows page list with previews.

### Chain B5 [P2]: Campaign Builder View
**Pattern:** Pattern C (Step-by-step Wizard → Component Map)
**Create:** `components/builders/campaign/campaign-builder-view.tsx`, `campaign-timeline.tsx`, `campaign-asset.tsx`, `types.ts`
- Campaign timeline: pre-launch (1–2 weeks) → launch day → post-launch
- Each phase shows the assets being produced (content, emails, ads, funnel)
- Assets are grouped by phase, clickable to view details
- Coordinate across multiple builder outputs
**Verify:** Click Campaign Builder → right panel shows campaign timeline with phase groupings.

### Chain B6 [P2]: Challenge Builder View
**Pattern:** Pattern C (Step-by-step Wizard → Day-by-Day Map)
**Create:** `components/builders/challenge/challenge-builder-view.tsx`, `day-map.tsx`, `day-detail.tsx`, `types.ts`
- Challenge architecture: theme, duration (5/7/14/21 days), transformation arc
- Day-by-day map: vertical timeline, each day = a card with topic, deliverable, email, social post
- Day detail: expand to see full content for that day
- Graduation bridge: the transition from challenge → core offer
**Verify:** Click Challenge Builder → right panel shows day-by-day challenge map.

---

## AGENT CHARLIE — Pages (Wave 2)

**Territory:**
```
app/(platform)/home/page.tsx           # Home/CEO dashboard — full page
app/(platform)/teams/page.tsx          # Teams page
app/(platform)/drive/page.tsx          # Drive/file manager page
app/(platform)/hub/page.tsx            # Hub — community + marketplace
app/(platform)/notifications/page.tsx  # Full notification history
app/(platform)/whats-new/page.tsx      # Changelog
app/(platform)/training/page.tsx       # Training/LMS
app/(platform)/analytics/page.tsx      # Analytics deep dive (placeholder)
app/(platform)/channels/page.tsx       # Channel management (placeholder)
app/(platform)/services/page.tsx       # Integration hub (placeholder)
```

### Chain C1 [P1]: Home Page — CEO Dashboard
**Trace:** `app/(platform)/home/page.tsx`
**Signal:** Home page exists but may be bare. Build the full CEO command center.
**Fix:** Build full-page dashboard (NOT the right-panel Dashboard tab — this is the standalone Home page):
- Full-width layout (no right panel, no chat)
- Greeting + date + IQ Score pill
- Revenue metrics row (larger than the right-panel Pulse — full charts)
- Performance overview with charts (line chart for revenue trend, bar chart for content performance)
- Alerts/attention section
- Weekly calendar (full view)
- Active engines with more detail than right panel version
- Activity feed (longer than right panel)
- Top performers (content leaderboard)
- IQ recommendations
**Verify:** Navigate to /home → full CEO dashboard renders with all sections.

### Chain C2 [P1]: Teams Page
**Trace:** `app/(platform)/teams/page.tsx`
**Build:** Full-width teams management page with tabs: Members | Roles | Activity | Settings
- Members tab: table with name, email, role, status, actions (edit, remove)
- [+ Invite Member] button → modal with email + role dropdown
- Roles tab: role definitions (Owner, Admin, Editor, Viewer) with permission matrix
- Activity tab: team activity feed
- Settings tab: team-level settings
- Mock data: Dr. Sarah Chen (Owner) as only member
**Verify:** Navigate to /teams → full page with tabs, member table, invite modal works.

### Chain C3 [P1]: Drive Page
**Trace:** `app/(platform)/drive/page.tsx`
**Build:** Full-width file manager (Genspark Drive clone):
- Breadcrumb navigation
- Folder structure: Content, Webinars, Funnels, Emails, Ads, Lead Magnets, Strategy Docs, Brand Assets
- List/grid view toggle
- File cards: icon + name + type + date + size
- Upload button + drag-and-drop zone
- Search + filter
- Mock data: 15–20 files across folders
**Verify:** Navigate to /drive → file manager renders, folder navigation works, view toggle works.

### Chain C4 [P2]: Hub Page
**Trace:** `app/(platform)/hub/page.tsx`
**Build:** Community + marketplace page with 3 sections:
- Shared Engines: grid of template cards from other practitioners (5 mock templates)
- Inspiration Feed: anonymized top-performing content (5 mock items)
- Community/Updates: platform updates + feature requests (3 mock entries)
- Tab navigation between sections
**Verify:** Navigate to /hub → 3-section page renders with mock data.

### Chain C5 [P2]: Notifications Page
**Trace:** `app/(platform)/notifications/page.tsx`
**Build:** Full notification history page:
- Filter pills: All | Alerts | Completions | Info | System
- Date range filter
- Notification list: colored severity dots, titles, subtitles, timestamps
- Mark as read/unread
- Mock data: 15 notifications
**Verify:** Navigate to /notifications → full notification list with filters.

### Chain C6 [P2]: What's New Page
**Trace:** `app/(platform)/whats-new/page.tsx`
**Build:** Changelog page:
- 5 changelog entries, newest first
- Each entry: date, title, description (1–2 paragraphs), optional screenshot placeholder
- "Mark all as read" button
**Verify:** Navigate to /whats-new → changelog renders.

### Chain C7 [P3]: Training Page
**Trace:** `app/(platform)/training/page.tsx`
**Build:** Platform training / LMS page:
- 5 training modules with progress bars
- Module 1: "Getting Started" (100% complete), Module 2: "Master Your Voice DNA" (60%), etc.
- Click module → lesson list with checkmarks
- Each lesson: title, description, estimated time, completion status
- Overall progress ring at the top
**Verify:** Navigate to /training → module list with progress, clickable lessons.

---

## AGENT DELTA — Settings Expansion + Polish (Wave 3)

**Territory:**
```
components/settings/appearance-tab.tsx     # Theme selector (Light/Dark/System)
components/settings/language-tab.tsx       # Language selector (8 languages)
components/settings/brand-tab.tsx          # Logo, colors, fonts
components/settings/api-advanced-tab.tsx   # API keys, webhooks, data export, reset
components/settings/profile-tab.tsx        # Expand: phone, timezone, website, security
components/settings/billing-tab.tsx        # Expand: plan card, payment, usage, invoices
components/settings/team-tab.tsx           # Expand: invite flow, roles, permissions
components/settings/notifications-tab.tsx  # Expand: toggle grid, quiet hours
app/(platform)/settings/page.tsx           # Settings page with all 8 tabs
```

### Chain D1 [P1]: Settings — Add Appearance + Language + Brand tabs
**Fix:** Ensure all 8 tabs exist and render: Profile, Appearance, Notifications, Language, Billing, Team, Brand, API & Advanced. Add any missing tab components.
**Verify:** All 8 settings tabs render with forms.

### Chain D2 [P1]: Settings — Expand Profile tab
**Fix:** Add: phone, timezone dropdown, website URL, Instagram handle, security section (change password form, 2FA toggle), danger zone (delete account with confirmation).
**Verify:** Profile tab has all fields, password change form expands, delete account shows confirmation.

### Chain D3 [P2]: Settings — Expand Billing tab
**Fix:** Add: current plan card (emerald border, name, price, features), payment method display, usage progress bars (builder runs, storage, team members), invoice history table with mock data.
**Verify:** Billing tab shows plan + payment + usage + invoices.

### Chain D4 [P2]: Settings — Expand Notifications tab
**Fix:** Add: toggle grid (8 notification types × 3 channels: In-App, Email, Push), quiet hours toggle with time pickers.
**Verify:** Notifications tab shows toggle grid, quiet hours section.

### Chain D5 [P3]: Settings — API & Advanced tab
**Fix:** Add: masked API key with reveal/copy/regenerate, webhook URL input with test button, data export button, connected OAuth accounts list, platform reset card (amber warning).
**Verify:** API tab has all elements, key reveal works, export button present.

---

## AGENT ECHO — Red Team (Wave 4)

### Chain E1 [P0]: Full Platform Audit
**Scope:** Every route, every tab, every flyout, every builder, every form, every modal.
**Check:**
1. **Routing:** Every sidebar item navigates correctly. No 404s. No broken links.
2. **Layout integrity:** 3-panel layout never breaks on /chat. Tab bar never disappears. Sidebar always visible.
3. **Builder completeness:** All 12 builders accessible from Builders tab. Each renders a view.
4. **Flyouts:** + New and More both open/close. All sub-panels work. No dead-end clicks.
5. **Settings:** All 8 tabs render. All forms have save buttons. No empty tabs.
6. **Dashboard:** All sections render (Pulse, IQ Score, Attention, Engines, This Week, Spotlight, Recommends, Performance by Category, Activity Feed).
7. **Engine flow:** "Build with IQ" → /chat → ⚡ Engine tab visible → tabs never hide.
8. **Mobile:** Bottom nav renders. Basic responsive behavior.
9. **Console:** No unhandled errors in browser console.
10. **Design consistency:** Colors match spec (#10B981 emerald, #1F2937 dark). No hardcoded grays. shadcn/ui components used correctly.

**Output:** File issues for each finding. Categorize as P0 (blocks ship) / P1 (fix before ship) / P2 (ship with known issue).

---

## MERGE ORDER

```
Wave 1: ALPHA (core fixes) → merge to main
Wave 2: BRAVO (builders) → merge to main
         CHARLIE (pages) → merge to main
Wave 3: DELTA (settings) → merge to main
Wave 4: ECHO findings → fix → merge
```

Build + test after every merge. `pnpm build` must pass. No unresolved TypeScript errors.

---

## ACTIVATION PROMPTS

### ALPHA Activation (Wave 1):

```
You are Agent ALPHA for the ClinicIQ front-end sprint. Your mission is to fix the core layout, chat, dashboard, flyouts, and engine flow issues identified in the April 8 review.

Read these files first:
- CLAUDE.md (project conventions)
- .claude/skills/cliniciq-design/SKILL.md (design skill — MUST follow)
- components/layout/platform-shell.tsx (3-panel layout)
- components/layout/workspace-panel.tsx (right panel tabs)
- components/chat/chat-panel.tsx (IQ chat)
- components/dashboard/dashboard-tab.tsx (dashboard)

Your territory (ONLY touch these files):
- components/chat/*
- components/dashboard/*
- components/layout/workspace-panel.tsx (builders tab section + engine tab)
- components/layout/sidebar-rail.tsx (rename Workflows → Engines)
- components/flyouts/*

You have 8 chains. Execute them one at a time, in order. Each chain: trace → diagnose → fix → verify (pnpm build passes, no TypeScript errors). Complete one chain fully before starting the next.

Spec documents for each fix are in the repo at: https://github.com/TheClinicIQ/cliniciq-master-build/tree/main/prompts/

Chain A1: Kill welcome splash, IQ speaks first
Chain A2: Dashboard — revert original + add Revenue Pulse, Engines, Calendar, Competitive Radar, Performance Spotlight, Brand Growth, Proof Bank nudge
Chain A3: Builders tab — all 12 builders, no workflow pills
Chain A4: Sidebar — "Workflows" → "Engines", GitBranch → Zap
Chain A5: + New flyout redesign (Ask IQ, Quick Capture, Upload)
Chain A6: More flyout — strip to 5 items
Chain A7: Engine flow — tabs never hide, ⚡ Engine is a tab
Chain A8: Engine context chat messages

BUILD IT RIGHT. No placeholders. No TODO comments. Working code only. Every component must render with mock data. pnpm build must pass after every chain.
```

### BRAVO Activation (Wave 2 — after ALPHA merges):

```
You are Agent BRAVO for the ClinicIQ front-end sprint. Your mission is to build the 6 remaining builder views.

Read these files first:
- CLAUDE.md
- .claude/skills/cliniciq-design/SKILL.md
- components/builders/content/content-builder-view.tsx (Pattern B example — study this)
- components/builders/funnel/funnel-builder-view.tsx (Pattern C example — study this)
- components/builders/webinar/webinar-builder-view.tsx (Pattern A example — study this)

Your territory (ONLY create/modify these):
- components/builders/program/* (NEW)
- components/builders/podcast/* (NEW)
- components/builders/sales-script/* (NEW)
- components/builders/website/* (NEW)
- components/builders/campaign/* (NEW)
- components/builders/challenge/* (NEW)
- components/layout/workspace-panel.tsx (add imports + case statements for new builders)

6 chains — one builder per chain. Study the existing builders for patterns. Match their quality exactly. Each builder needs: a main view component, sub-components, types.ts, and mock data.

Spec documents: https://github.com/TheClinicIQ/cliniciq-master-build/tree/main/prompts/builders/

Chain B1: Program Builder (Pattern A)
Chain B2: Podcast Builder (Pattern A)
Chain B3: Sales Script Builder (Pattern A)
Chain B4: Website Builder (Pattern A)
Chain B5: Campaign Builder (Pattern C)
Chain B6: Challenge Builder (Pattern C)

Every builder must render in the right panel when its card is clicked in the Builders tab. No empty states. Full mock data. pnpm build must pass.
```

### CHARLIE Activation (Wave 2 — parallel with BRAVO):

```
You are Agent CHARLIE for the ClinicIQ front-end sprint. Your mission is to build all the full-page views.

Read these files first:
- CLAUDE.md
- .claude/skills/cliniciq-design/SKILL.md
- app/(platform)/layout.tsx (platform layout)
- app/(platform)/workflows/page.tsx (example of a well-built page)

Your territory (ONLY touch these files):
- app/(platform)/home/page.tsx
- app/(platform)/teams/page.tsx
- app/(platform)/drive/page.tsx
- app/(platform)/hub/page.tsx
- app/(platform)/notifications/page.tsx
- app/(platform)/whats-new/page.tsx
- app/(platform)/training/page.tsx

7 chains — one page per chain. Each page: full-width layout (sidebar + content), complete with mock data, tabs where specified, all interactive elements functional.

Chain C1: Home page (CEO dashboard — full page, charts, metrics, calendar)
Chain C2: Teams page (member table, invite modal, roles, tabs)
Chain C3: Drive page (file manager, folders, list/grid, upload)
Chain C4: Hub page (shared engines, inspiration feed, community)
Chain C5: Notifications page (history, filters, mark as read)
Chain C6: What's New page (changelog, 5 entries)
Chain C7: Training page (5 modules, progress, lessons)

Every page must render correctly when navigated to from the sidebar. Full mock data. No empty states. pnpm build must pass.
```

### DELTA Activation (Wave 3):

```
You are Agent DELTA for the ClinicIQ front-end sprint. Your mission is to expand the Settings page and polish responsive behavior.

Read: CLAUDE.md, .claude/skills/cliniciq-design/SKILL.md, components/settings/*

Territory: components/settings/*, app/(platform)/settings/*

5 chains:
D1: Ensure all 8 settings tabs exist and render
D2: Expand Profile tab (phone, timezone, website, security, danger zone)
D3: Expand Billing tab (plan card, payment, usage, invoices)
D4: Expand Notifications tab (toggle grid, quiet hours)
D5: API & Advanced tab (API key, webhooks, data export, OAuth, platform reset)

Every settings tab fully functional with mock data. All forms have save buttons. pnpm build must pass.
```

---

## SUCCESS CRITERIA

Sprint is **ACHIEVED** when:
- [ ] All routes render (no 404s, no white screens)
- [ ] All 12 builders accessible and rendering views
- [ ] Dashboard shows all sections (Pulse through Activity Feed)
- [ ] IQ chat: no welcome splash, first message always present
- [ ] Tabs never disappear on the right panel
- [ ] + New flyout: Ask IQ, Quick Capture, Upload, Recent
- [ ] More flyout: 5 items only
- [ ] Engines flow: Build with IQ → /chat → ⚡ Engine tab
- [ ] Home, Teams, Drive, Hub, Notifications, What's New, Training pages complete
- [ ] Settings: 8 tabs, all forms rendered
- [ ] `pnpm build` passes with zero errors
- [ ] Red Team finds no P0 issues
