# Sprint 02: Platform Completion
## Give this entire document to the orchestrator.

---

## SPRINT GOAL

Complete every remaining UI surface in the ClinicIQ platform to production-ready quality with mock data. When this sprint ships, every route renders, every tab has real content, every builder has a full interactive view, and the platform feels like a $1B product from edge to edge. Zero placeholder screens. Zero "coming soon" stubs. Zero empty tabs.

---

## CODEBASE STATE (what already exists)

**Stack:** Next.js 16 + React 19 + Tailwind v4 + shadcn/ui (56 components) + Zustand + Lucide icons

**Layout:** 3-panel on `/chat` (SidebarRail + chat + WorkspacePanel with tabs). Full-width on all other routes.

**What's built and working:**
- Auth pages (login, signup, forgot-password)
- Onboarding flow (full — conversation + progress panel)
- IQ Workspace `/chat` with 3-panel layout, resizable panels
- WorkspacePanel with 12 static tabs + dynamic ⚡ Engine tab
- 6 builder views: Content (grid + detail + approval), Funnel (map + page detail), Webinar (outline + section detail), Email (sequence map + email detail), Ad Creative (hook angle tabs + scoring + detail), Lead Magnet (quiz flow + question detail)
- Engines/Workflows page with templates, my engines, running view, history
- Settings page with horizontal tabs (Profile, Billing, Team, Notifications, API)
- Flyouts (+ New and More) with sub-panels
- Chat components (panel, input, messages, streaming)
- Dashboard tab with sections (pulse, IQ score, attention, engines, calendar, spotlight, recommends)
- Stores: ui-store, chat-store, build-queue-store, onboarding-store

**What's NOT built or needs significant work (this is the sprint):**

### 6 Missing Builder Views
These builders are listed in the Builders tab (all 12 show) but 6 have no view component — clicking them does nothing:
- `components/builders/program/` — does not exist
- `components/builders/podcast/` — does not exist
- `components/builders/sales-script/` — does not exist
- `components/builders/website/` — does not exist
- `components/builders/campaign/` — does not exist
- `components/builders/challenge/` — does not exist

### Right Panel Tabs That Need Depth
These tabs exist but are thin — basic placeholder content. They need to feel like real, data-rich views:
- **Brand tab** — needs full Voice DNA display, avatar cards with 4 psychological layers, offer stack with transformation framing, mechanism + One Big Domino, proof bank with stories
- **Strategy tab** — needs Brand North Star summary, Monthly Master Plan with goals vs actuals, messaging briefs, performance insights with actionable recommendations
- **Content tab** — needs to be a mini content library with filter pills, thumbnail grid, status badges, click-to-preview
- **Calendar tab** — needs a real calendar view (week/month toggle) with scheduled content shown as colored dots/blocks

### Full Pages That Need Depth
These routes exist but are stubs or thin:
- **Home `/home`** — needs to be the full CEO dashboard: revenue charts (line chart for trend), performance metrics with real chart components, full weekly calendar, activity feed, active engines, IQ recommendations
- **Teams `/teams`** — needs member table, invite modal with email + role dropdown, role definitions (Owner/Admin/Editor/Viewer), activity feed tab
- **Drive `/drive`** — needs Genspark-style file manager: folder tree (Content, Webinars, Funnels, Emails, Ads, Lead Magnets, Strategy Docs, Brand Assets), breadcrumb navigation, list/grid toggle, file cards with icon + name + date + size, upload zone, search

### Dashboard Tab Additions
The dashboard tab has the new sections (pulse, engines, calendar, spotlight) but needs verification and polish:
- Revenue Pulse at top with real $ formatting and trend arrows
- IQ Score with milestone gamification ("🎯 4 pts to 75 — unlock Audience Insights")
- Brand Growth bar (total audience reach across platforms)
- Competitive Radar section (2 competitor intel items)
- Performance Spotlight must show WINNING (green) AND FIX THIS (red) — not just winners
- Proof Bank nudge inside Recommends section (conditional, shows when score < 60)

### Flyout Refinements
- **+ New flyout** — should be: Ask IQ textarea at top, New Conversation button, Quick Capture (4 cards: Patient Story, Voice Note, Proof, Competitive Intel — each with inline capture panel), Upload drop zone, Recent conversations
- **More flyout** — should be exactly 5 items: Notifications (with inline panel), Hub (→ /hub), Help & Support (with inline panel), What's New (→ /whats-new), Download App (with inline panel). Account footer with Sign Out. No Analytics, no Channels, no Services, no Training, no Manage Account (those live on right panel tabs or Settings).

---

## THE 15 WORK ITEMS — Organized for Parallel Execution

### WAVE 1 — Builders (6 items, fully parallel, zero file overlap)

Each builder needs: a `*-builder-view.tsx` (main view), 1–2 sub-components, a `types.ts` with mock data. Study the existing 6 builders for patterns — match their quality exactly.

**1. Program Builder** (`components/builders/program/`)
Pattern A: outline view → module detail. Show program architecture (name, transformation promise, 6–8 modules). Module list — click to expand lesson scripts, worksheets, action items. Mock: "Signal Reset Protocol — 8 modules, 12 weeks"

**2. Podcast Builder** (`components/builders/podcast/`)
Pattern A: architecture view → episode detail. Show name, tagline, format, episode plan (8 episodes). Episode list — click for full script with Hook/Bridge/Value/CTA sections. Repurposing section per episode (carousel + Reels + blog outline). Mock: "The Root Cause Reset — weekly, solo format"

**3. Sales Script Builder** (`components/builders/sales-script/`)
Pattern A: script outline → section detail. Sections: Discovery, Transition, Offer Presentation, Value Stack, Objection Handling (5 objections — each with emotional acknowledgment → logical reframe → proof close), Close. + DM script variant tab. Mock: consult close script for Hormone Reset Protocol

**4. Website Builder** (`components/builders/website/`)
Pattern A: page list → page preview. Pages: Homepage, About, Services, Testimonials, Contact, Blog. Each page has sections (hero, about, services grid, testimonial carousel, CTA). Section editor as expandable accordion. Mock: Signal Reset Health website

**5. Campaign Builder** (`components/builders/campaign/`)
Pattern C: timeline view → phase detail. Three phases: Pre-Launch (1–2 weeks of build-up content), Launch Day (coordinated content + email + ads), Post-Launch (follow-up, proof, bridge to next offer). Each phase shows grouped assets with builder icons. Mock: "April Hormone Reset Campaign"

**6. Challenge Builder** (`components/builders/challenge/`)
Pattern C: day-by-day map → day detail. Vertical timeline, each day = card with topic, deliverable, email subject, social post hook. Day detail expands to full content. Graduation bridge card at the end (challenge → core offer transition). Mock: "7-Day Cortisol Reset Challenge"

**Wire all 6 into `workspace-panel.tsx`:** Add imports and case statements for `"program-builder"`, `"podcast-builder"`, `"sales-script-builder"`, `"website-builder"`, `"campaign-builder"`, `"challenge-builder"`.

### WAVE 2 — Right Panel Tabs + Dashboard Polish (4 items, parallel)

**7. Brand Tab Rebuild** (in `workspace-panel.tsx` → `BrandTab` function or extract to component)
Replace the current thin Brand tab with a full brand bible view:
- **Voice DNA section:** tone (e.g., "Direct, systems-thinker, reassuring"), rhythm, formality, humor level, signature phrases (emerald-outlined pills), banned words (red-outlined pills with strikethrough), voice confidence score (progress bar at 78/100), authority style. [Edit Voice DNA →] link.
- **Patient Avatars section:** 2 avatar cards side by side. Primary avatar (emerald border): name ("Stressed Mom Sarah"), demographics, 4 layers — Pain (daily reality), Fear, Desire, Internal dialogue (italic quotes). Secondary avatar (gray border). [+ Add Avatar] button. Usage stats ("12 posts targeting · 3 ads · Best performer").
- **Offer Stack section:** 3 tiers stacked vertically, each a mini-card with colored left border (green=entry, blue=core, purple=premium). Each: tier label, offer name, price, Before State → After State transformation, format/duration. Mock: Free Cortisol Assessment → Hormone Reset $4,800 → VIP Intensive $12,000.
- **Mechanism section:** mechanism name ("The Signal Reset Protocol") + named badge, One Big Domino statement in an indented block with emerald left line, character type badge ("Cause-Driven").
- **Proof Bank section:** score (62/100) + progress bar, quick stats (3 stories · 2 videos · 12 testimonials), top story preview card, [+ Add Story] button.
- **Brand Assets section:** logo preview, 3 color swatches with hex codes, font name with sample "Aa" preview.

**8. Strategy Tab Rebuild** (in `workspace-panel.tsx` → `StrategyTab` function or extract)
Replace thin Strategy tab:
- **Brand North Star card** (emerald left border, star icon): Category Claim ("The hormone doctor who finds what everyone else missed"), One Big Domino quote block, Content Pillars (5 pills: Authority, Transformation Stories, Mechanism Education, Myth-Busting, Patient Voice), ALWAYS rules (5 emerald checkmarks), NEVER rules (5 red x marks). [View Full →] link.
- **Monthly Master Plan card** (calendar icon, "On Track" green badge): Campaign name + theme, progress bar at 68% ("Day 17 of 30"), content mix bar (posts, carousels, reels, webinar, emails — segmented), goals vs actual mini-table (leads, webinar regs, consults, revenue, content published — with green/amber status dots). [View Full Plan →] [Refresh Strategy →].
- **Active Messaging Briefs** (2 brief cards): each with name, status, target avatar, awareness level, hook angle, assets produced progress bar. [View Brief →].
- **Performance Insights** (brain icon, "Updated 2h ago"): 3 insight rows with emerald left border + lightbulb icon + actionable text + [Apply →] button. These are Layer 4 intelligence recommendations.

**9. Content Tab Rebuild** (in `workspace-panel.tsx` → `ContentTab` function or extract)
Replace with a mini content library:
- **Filter row:** pill toggles: [All] [Posts] [Carousels] [Reels] [Emails] [Ads] [Scripts] — selected pill is primary colored
- **Thumbnail grid (2 columns):** each card shows: format icon + content preview (hook text or image placeholder), title, date, status badge (Draft=gray, Approved=emerald, Scheduled=blue, Published=green). Click → opens the builder detail view for that content piece.
- **Empty state** when no content: "No content yet. Start with the Content Builder or launch a Growth Engine."
- Mock: 8–10 content pieces of mixed formats and statuses.

**10. Calendar Tab Rebuild** (in `workspace-panel.tsx` → `CalendarTab` function or extract)
Replace with a real calendar:
- **Toggle:** [Week] [Month] — week is default
- **Week view:** 7-day grid (Mon–Sun), each day cell shows the date and content items scheduled for that day. Items are small colored pills (emerald=post, blue=email, purple=ad, amber=webinar). Click an item → shows a popover with title + time + format + [View →] link.
- **Month view:** standard month grid, each day cell shows colored dots (one per scheduled item). Click a day → expands to show that day's items.
- **Navigation:** [← Prev Week] [Today] [Next Week →] / [← Prev Month] [Today] [Next Month →]
- Mock: 2–3 weeks of scheduled content, 2–3 items per day.

### WAVE 3 — Full Pages (3 items, parallel)

**11. Home Page** (`app/(platform)/home/page.tsx`)
The CEO command center — full-width, no chat, no right panel. This is the big dashboard.
- Greeting + date + IQ Score pill (link to /chat)
- Revenue overview: large number ($38,400 this month) + line chart (30-day revenue trend) + comparison to last month. Three sub-metrics: new leads (142), consults booked (18), conversion rate (12.7%).
- Performance cards row: 4 cards (same as right panel — Ad 64, Funnel 78, Social 82, Email 58) but larger with mini sparkline charts inside each.
- Needs Attention: same alerts as right panel but with more detail and room.
- This Week calendar: full weekly calendar view (larger than the right panel version).
- Active Engines: full engine cards with performance metrics (not the compact right panel version).
- Content leaderboard: top 5 performing content pieces this month with engagement metrics.
- Activity feed: longer timeline of recent platform actions.
- Recommendations: 3 IQ suggestions with [Apply →].

**12. Teams Page** (`app/(platform)/teams/page.tsx`)
Full-width teams management:
- Tab bar: Members | Roles | Activity | Settings
- **Members tab:** table with columns: Name, Email, Role (dropdown badge), Status (green/gray dot), Last Active, Actions (edit, remove). [+ Invite Member] emerald button → dialog with email input + role dropdown (Owner/Admin/Editor/Viewer) + [Send Invite]. Mock: Dr. Sarah Chen (Owner, active) as only member.
- **Roles tab:** 4 role cards (Owner, Admin, Editor, Viewer), each with description + permission checklist (can use builders ✅, can approve content ✅, can access billing ❌, etc.).
- **Activity tab:** timeline of team actions (invited, joined, approved content, ran builder). Mock: 5 entries.
- **Settings tab:** team name, default role for new members, notification preferences for team events.

**13. Drive Page** (`app/(platform)/drive/page.tsx`)
Genspark-style file manager:
- **Top bar:** breadcrumb navigation (IQ Drive > Content > April 2026), [Upload] button, [+ New Folder] button, search input, view toggle (list/grid icons).
- **Folder sidebar or top-level folder grid:** Content, Webinars, Funnels, Emails, Ads, Lead Magnets, Strategy Docs, Brand Assets, Workflows (engine outputs). Each folder has an icon + item count.
- **File list (default view):** table with: icon (by file type), Name, Type, Modified date, Size, Actions (download, share, delete). Sortable columns. Alternating row bg.
- **File grid (toggle view):** thumbnail cards — icon + name + date. Hover: shadow + border.
- **Upload zone:** drag-and-drop area at top (dashed border, "Drop files here or click to upload").
- Mock: 15–20 files across multiple folders.

### WAVE 4 — Flyouts + Dashboard Additions + Final Polish (2 items)

**14. Dashboard Tab Additions** (verify and polish `components/dashboard/*`)
Ensure every section from the spec is present and polished:
- Revenue Pulse (top): 3 metrics with $ formatting and trend arrows
- IQ Score: circular SVG donut gauge + milestone ("🎯 4 pts to 75 — unlock Audience Insights")
- Brand Growth bar: "📈 Total Reach: 14,200 (+340 this week)" + per-platform breakdown
- 4 Score cards with category-colored progress bars
- Needs Attention: severity-sorted (red → amber → gray), action links
- Active Engines + This Week: side by side
- Recommendations (3 items with [Apply →]) + Competitive Radar (2 competitor intel items)
- Performance Spotlight: one WINNING card (green, sparkline up) + one FIX THIS card (red, sparkline down)
- Performance by Category: tabbed (Ad Metrics, Funnel, Social, Email) with detail metrics
- Activity Feed
- Proof Bank nudge at bottom of Recommends (conditional, when score < 60): shield icon, score, progress bar, actionable nudge text, [Strengthen Proof →]

**15. Flyout Polish** (verify `components/flyouts/*`)
- **+ New flyout:** Verify it has Ask IQ textarea (not builder grid), New Conversation button, Quick Capture (4 cards with inline panels), Upload drop zone, Recent conversations. If it still shows the old builder grid — replace it.
- **More flyout:** Verify it has exactly 5 items (Notifications, Hub, Help & Support, What's New, Download App) + account footer. No Analytics, Channels, Services, Training. If extras remain — remove them.

---

## BUILDER PATTERNS (for the 6 new builders)

The 6 existing builders follow 3 patterns. The new builders should match:

**Pattern A — Outline → Detail (single structured output):**
- Main view: vertical list of sections/modules/pages, each a collapsible card
- Click a section → detail view replaces the list (with [← Back] navigation)
- Detail view: full content displayed as rich text, editable
- Used by: Webinar (outline → section detail), and should be used by Program, Podcast, Sales Script, Website

**Pattern B — Grid → Detail (batch of similar assets):**
- Main view: 2-column grid of cards, each representing one asset
- Cards show preview, format, hook, status, approve/edit/regen buttons
- Click → detail view with full content + metadata + inline editing
- Used by: Content (7-post grid), Ad Creative (hook angle tabs → grid)

**Pattern C — Map/Timeline → Detail (sequenced/connected items):**
- Main view: vertical flow chart or timeline connecting items
- Each node shows status + summary. Timing/dependency lines between nodes.
- Click a node → detail view for that item
- Used by: Email (sequence map → email detail), Funnel (funnel map → page detail), and should be used by Campaign (timeline), Challenge (day map)

**Each new builder needs:**
1. `*-builder-view.tsx` — main view component (120–250 lines)
2. 1–2 sub-components for detail views (80–150 lines each)
3. `types.ts` — TypeScript interfaces + MOCK_DATA constant (150–200 lines)
4. Wired into `workspace-panel.tsx` tab content switch

**Study `components/builders/content/` as the reference implementation.** Match its quality, component structure, and interaction patterns.

---

## DESIGN RULES (from CLAUDE.md + design skill)

- Primary accent: #10B981 (emerald). Use `text-primary`, `bg-primary`, `border-primary`.
- Use semantic CSS variables: `text-foreground`, `bg-card`, `bg-muted`, `text-muted-foreground`. Never hardcode gray-*.
- Category colors: blue (ads), purple (funnel), pink (social), amber (email).
- KPI cards: colored top border + icon in colored badge + category-colored progress.
- Score displays: SVG donut ring, not number-in-a-box.
- Sparklines: SVG line path with gradient fill, not block bars.
- All section headers: icon wrapped in colored rounded-lg background.
- No flat gray boxes. No purple AI glows. No bare icons without context.
- Follow `.claude/skills/cliniciq-design/SKILL.md` for the full design system.

---

## SUCCESS CRITERIA

Sprint is ACHIEVED when:
- [ ] All 12 builders render interactive views when clicked from the Builders tab
- [ ] Brand tab shows full Voice DNA, avatars, offers, mechanism, proof bank
- [ ] Strategy tab shows North Star, Monthly Plan, briefs, insights
- [ ] Content tab is a filterable content library with thumbnails
- [ ] Calendar tab shows a real week/month view with scheduled content
- [ ] Home page is a full CEO dashboard with charts and metrics
- [ ] Teams page has member table, invite modal, roles, activity feed
- [ ] Drive page is a working file manager with folders, list/grid, upload
- [ ] Dashboard tab has all sections including Revenue Pulse, Competitive Radar, Performance Spotlight (winner + loser), Brand Growth, milestone
- [ ] + New flyout has Ask IQ, Quick Capture, Upload (not builder grid)
- [ ] More flyout has exactly 5 items (not 9+)
- [ ] `pnpm build` passes with zero errors
- [ ] No route returns 404 or blank screen
- [ ] No tab in the workspace panel shows empty/placeholder content

---

## SPEC DOCUMENTS

Full specs for each builder and component are in the spec repo:
https://github.com/TheClinicIQ/cliniciq-master-build/tree/main/prompts/

Key files:
- `prompts/builders/01_CONTENT_BUILDER.md` through `06_LEAD_MAGNET_BUILDER.md` — existing builder specs (reference for quality bar)
- `prompts/CLAUDE_CODE_DASHBOARD_FINAL.md` — dashboard additions
- `prompts/CLAUDE_CODE_MORE_FLYOUT_FINAL.md` — more flyout (5 items)
- `prompts/CLAUDE_CODE_NEW_FLYOUT_REDESIGN.md` — + new flyout redesign
- `prompts/CLAUDE_CODE_IQ_CHAT_FIX.md` — IQ always speaks first
- `prompts/CLAUDE_CODE_ENGINES_FLOW_FIX_v3.md` — engine build tab behavior
- `prompts/LOVABLE_BRAND_STRATEGY_TABS.md` — Brand and Strategy tab detailed spec
- `prompts/00_MASTER_BLUEPRINT.md` — master UI map for the whole platform
