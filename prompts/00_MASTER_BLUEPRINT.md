# ClinicIQ — Master UI Blueprint
## The complete map of every screen, component, and interaction in the platform
**Purpose:** Single source of truth for the Lovable build. Every screen, every tab, every flyout, every flow — documented in one place so there's zero ambiguity.

---

## DESIGN SYSTEM (Applies to EVERYTHING)

- **Theme:** Light mode. No dark mode for v1.
- **Colors:** Black (#1F2937), white (#FFFFFF), grays (#F8F9FA background, #E5E7EB borders, #6B7280 secondary text, #9CA3AF disabled). Teal accent (#00D4AA) for CTAs, active states, positive indicators.
- **Alert colors:** Red (#EF4444) for alerts/negative. Amber (#F5A623) for warnings. Green (#22C55E) for positive.
- **Typography:** Inter or Plus Jakarta Sans. Clean sans-serif throughout.
- **Cards:** White background, subtle border (#E5E7EB), 12px rounded corners.
- **Overall feel:** Premium, clean, minimal. NOT a SaaS dashboard. Think: Genspark's simplicity meets a high-end health brand's confidence.

---

## SCREEN MAP — Every Screen in the Platform

### 1. SIGN-UP PAGE
- **Route:** `/signup`
- **Layout:** Full page, no sidebar. Two columns on desktop (value prop left, form right), stacked on mobile.
- **Collects:** Full name, email, password, website URL (required — triggers Web Scraper), primary specialty (dropdown), Instagram handle (optional)
- **CTA:** "Start Building →"
- **Post-submit:** Redirects to onboarding. Web Scraper begins running on the website URL.
- **Note:** Original prompt specified dark theme. **CHANGE TO LIGHT THEME** to match the rest of the platform. Same design, light background.

### 2. ONBOARDING SCREEN
- **Route:** `/onboarding`
- **Layout:** Three-panel layout introduced here for the first time.
  - Left: Sidebar rail (72px) — same 8 items as main app, but all grayed out / disabled except IQ (active). Icons visible as a preview of what's coming.
  - Center: IQ Claw chat — the onboarding conversation.
  - Right: Onboarding progress card (not the tabbed dashboard — a dedicated progress view).
- **First message:** IQ Claw has already analyzed the expert's website and IG (from Web Scraper). Opens with personalized intel: "I've been looking at your practice..."
- **Conversation flow:** Voice DNA extraction → Avatars → Offers → Mechanism → Proof Bank → 90-second demo moment
- **Right panel shows:** Progress bar (%), checklist (Your Story ✅, Your Voice ✅, Your Avatars 🔄, Your Offers ○, Your Proof Bank ○), "What We Know So Far" section that fills in live, estimated time remaining
- **Completion:** When 100%, IQ Claw delivers a transition message. Right panel transforms into the standard tabbed dashboard. Sidebar items unlock (no longer grayed out). Expert is now in the main app.

### 3. MAIN APP — IQ CLAW WORKSPACE
- **Route:** `/iq` or `/` (default logged-in route)
- **Layout:** Three-panel layout:
  - Left: Genspark-style sidebar rail (72px)
  - Center: IQ Claw chat
  - Right: Tabbed context panel
- **This is the primary daily interface.** Expert opens the platform and lands here.

### 4. HOME PAGE
- **Route:** `/home`
- **Layout:** Sidebar rail (72px) + full-width dashboard (no chat panel, no right panel split)
- **Content:** CEO command center — greeting, alerts, performance metrics with chart, weekly calendar, activity feed, brand health, top performers, IQ Claw suggestions, quick actions

### 5. WORKFLOWS PAGE
- **Route:** `/workflows`
- **Layout:** Sidebar rail + full-width content
- **Tabs:** All Workflows | Running | Completed | Templates
- **Content:** Currently running workflows with progress bars, 12 builder cards (4x3 grid), recent workflow runs table, workflow templates

### 6. TEAMS PAGE
- **Route:** `/teams`
- **Layout:** Sidebar rail + full-width content
- **Tabs:** Members | Roles | Activity | Settings
- **Content:** Member table with roles/status, invite modal, role definitions, activity feed, team settings

### 7. DRIVE PAGE
- **Route:** `/drive`
- **Layout:** Sidebar rail + full-width file manager
- **Content:** Genspark Drive clone — breadcrumb navigation, folder structure (Content, Webinars, Funnels, Emails, Ads, Lead Magnets, Strategy Docs, Brand Assets), list/grid view toggle, file metadata, upload, search, filter
- **Note:** Prompt not yet written — needs to be created for Lovable build

---

## LEFT SIDEBAR — Consistent Across ALL Screens

72px wide. Light gray background. Teal accent line at top edge. Items center-aligned, icon (24px) + tiny label (10px).

### Items (top to bottom, EXACT order):
1. **ClinicIQ logo** — Rounded dark square with brand mark. No label.
2. **+ New** — Plus icon. Label: "New". Flyout: Quick Actions (Quick Post, Quick Email, Quick Ad) + 3-column Builders grid (12 builders) + Quick Launch pills + Recent Chats list.
3. **Home** — House icon. Label: "Home". Navigates to `/home`.
4. **IQ** — Planet/orbital ring icon (Genspark Claw style). Label: "IQ". Navigates to `/iq`. Active when in the IQ Claw workspace.
5. **Workflows** — Workflow/org-chart icon. Label: "Workflows". Navigates to `/workflows`.
6. **Teams** — Two people icon. Label: "Teams". Navigates to `/teams`.
7. **Drive** — Folder icon. Label: "Drive". Navigates to `/drive`.
8. **More** — Three dots icon. Label: "More". Flyout: Inbox (with badge), Hub, divider, Dark Mode toggle, Help & Support, Download App.

**Bottom (pinned):**
- Settings gear icon (no label)
- User avatar circle with initials (links to profile)

### Active state: White circle background behind the icon for the current page. All others gray (#6B7280).

### Flyout behavior: Hover or click triggers a panel that slides out to the right of the sidebar rail. 280–520px wide depending on content. White background, 16px radius, soft shadow. Closes on mouse-leave or click-outside.

---

## RIGHT PANEL TABS — When in the IQ Claw Workspace (`/iq`)

The right panel only appears in the IQ Claw workspace view. Other pages (Home, Workflows, Teams, Drive) are full-width — no right panel.

### Tab bar (10 tabs, horizontally scrollable if needed):
🏠 Dashboard | 🧬 Brand | 📋 Strategy | ⚡ Builders | 📁 Content | 📅 Calendar | 📡 Channels | 🔌 Services | 📖 Training | ⚙️ Settings

### Tab content summary:

| Tab | What It Shows |
|-----|--------------|
| 🏠 Dashboard | Alerts, what's working, quick metrics, this week schedule, new leads |
| 🧬 Brand | Voice DNA, Avatars (selectable), Offers (3 tiers), Mechanism, Proof Bank, Brand Assets |
| 📋 Strategy | Brand North Star, Monthly Master Plan, Messaging Briefs, Layer 4 Performance Insights |
| ⚡ Builders | 12 builder cards in 2-column grid + Quick Launch row |
| 📁 Content | Content library with filter pills and thumbnail grid |
| 📅 Calendar | Weekly/monthly content calendar |
| 📡 Channels | Connected social platforms (IG, FB, YouTube, TikTok, LinkedIn) |
| 🔌 Services | Tech integrations (GHL, Zoom, Stripe, Mailchimp, Slack, Calendly, etc.) |
| 📖 Training | Platform mastery progress + checklist + quick tips |
| ⚙️ Settings | Account, brand, integrations, billing |

**Also added (from later prompts):**
- 📁 Files tab — full Genspark-style file manager with breadcrumbs, list/grid view, folders
- 🕐 Schedules tab — cron-based recurring tasks with progress, run history, create new

**Note:** Need to reconcile whether Files and Schedules are right-panel tabs or separate full pages. Current state: Files/Schedules were written as right-panel tab prompts, but Drive is a full sidebar page. **Decision needed: Does Drive (sidebar) replace the Files tab (right panel)? Probably yes — Drive is the full page, Content tab on the right panel is the quick-access view of published content.**

---

## THE 12 BUILDERS

| # | Builder | What It Produces |
|---|---------|-----------------|
| 1 | 📝 Content Builder | Posts, carousels, reels, stories |
| 2 | 🔗 Funnel Builder | Opt-in pages, sales pages, landing pages |
| 3 | 🎥 Webinar Builder | Script, slides, follow-up sequence |
| 4 | ✉️ Email Builder | Sequences, nurtures, promos, launches |
| 5 | 📢 Ad Creative Builder | Hooks, copy, creatives, variants |
| 6 | 🧲 Lead Magnet Builder | PDF guides, quizzes, assessments |
| 7 | 🎓 Program Builder | Course content, protocols, modules |
| 8 | 🎙️ Podcast Builder | Episodes, scripts, show notes |
| 9 | 📞 Sales Script Builder | Phone, DM, and close scripts |
| 10 | 🌐 Website Builder | Landing pages, service pages |
| 11 | 🚀 Campaign Builder | Full campaign: content + email + ads + funnels |
| 12 | 🏆 Challenge Builder | 5/7/14/30-day challenge sequences + landing pages |

Builders are accessible from:
- **"+ New" flyout** — 3-column grid in the flyout panel
- **Builders tab** on the right panel — 2-column grid
- **Workflows page** — 4-column grid with last-run timestamps
- **IQ Claw chat** — expert just describes what they need, IQ routes to the right builder

---

## USER FLOW MAP

```
Sign Up (/signup)
    ↓
Onboarding (/onboarding) — IQ Claw conversation + progress card
    ↓ (on completion)
Main App — IQ Claw Workspace (/iq) — morning briefing + right panel tabs
    ↕ (sidebar navigation)
Home (/home) — CEO dashboard
Workflows (/workflows) — builder management + workflow history
Teams (/teams) — team members + roles + activity
Drive (/drive) — file manager
```

---

## THE BUILDER FLOW — How Builders Actually Work (Critical for Lovable)

This is the exact interaction flow when an expert uses a builder:

### Step 1: Expert → IQ Claw (Chat)
Expert tells IQ Claw what they want: "I want to build a webinar" or "I need 28 social images for this month"

### Step 2: IQ Claw → Builder Link (Chat)
IQ Claw responds in chat with context + a link/button to the specific builder: "Got it. Here's the Webinar Builder →" or "Let's set up your content batch →"

### Step 3: Builder Selection Screen
Expert clicks through and sees a **selection screen** where they configure:
- **Voice DNA** — which voice profile to use
- **Avatar** — which patient persona to target
- **Offer** — which offer to pitch (if applicable)
- **Strategy / North Star** — which strategic direction to follow
- Any builder-specific options (e.g., number of assets, format, platform)

### Step 4: Builder Runs — Live in Right Panel
Expert confirms → the builder kicks off. The **right panel transforms into a live build view** showing the generation happening in real-time (code/progress visible). The expert watches it work.

### Step 5: Two-Stage Build (Where Applicable)
For builders that produce multiple assets (e.g., Content Builder for 28 images):
- **Stage 1 — Briefs:** The builder generates detailed briefs/prompts for each asset. Each brief specifies exact text overlay, visual concept, layout, persona, framework. Expert reviews and approves all briefs.
- **Stage 2 — Production:** Once briefs are approved, the next agent produces the actual finished assets.

### Step 6: Results Appear in Right Panel
When done, the right panel shows the finished asset(s). Expert can preview, review, and interact with each one.

### Step 7: Edit via IQ Claw Chat
Expert can edit any output by chatting: "change the hook on #3" or "make the intro shorter" — IQ Claw handles the revision and the right panel updates.

### Step 8: Save to IQ Drive
"Save to Drive" button on each asset → saves to the appropriate IQ Drive folder (Content/Images, Emails/Sequences, etc.). The Drive page and Files views show everything saved.

### Step 9: Schedule Recurring Production (Where Applicable)
For builders that produce recurring content (Content Builder, Email Builder, etc.):
- Expert clicks "Schedule" → picks a cadence (e.g., "28 new images every 28 days")
- The system automatically generates a fresh batch on schedule — new unique assets following the same strategy but with new content
- This is a PRODUCTION schedule, not just a publishing schedule — the system creates NEW assets on the cadence

### Right Panel States
The right panel is a chameleon:
- **Default:** Tabbed dashboard (Dashboard, Brand, Strategy, etc.)
- **During build:** Live build view showing generation progress
- **After build:** Asset preview/review view
- **When browsing tabs:** Whatever tab content is selected

---

## OPEN DECISIONS (Need to resolve before Lovable build)

1. **Sign-up page theme:** Original prompt was dark. We switched everything else to light. **Should sign-up be light too?** (I'd say yes for consistency.)

2. **Onboarding sidebar:** During onboarding, sidebar items are grayed/disabled. **Should we show all 8 items grayed out, or hide everything except the IQ icon?** (I'd say show them all grayed — it communicates "there's a full platform waiting for you after this conversation.")

3. **Right panel tabs count:** We have 10 tabs + Files + Schedules = 12 possible tabs. That's too many. **Consolidation proposal:**
   - Remove Files tab from right panel (Drive page handles this)
   - Remove Schedules tab from right panel (Workflows page handles this)
   - Consider merging Channels + Services into "Connections" (keeps it at 9 tabs)

4. **Builders duplication:** Builders appear in the + New flyout, the Builders right-panel tab, AND the Workflows page. **Is this intentional redundancy (multiple entry points) or clutter?** (I think it's OK — different contexts, same destination.)

5. **Dashboard vs. Home:** The Dashboard tab on the right panel and the Home page show overlapping information (alerts, metrics, calendar). **Differentiation:** Home is the full CEO view (fills the whole screen, has charts and activity feeds). Dashboard tab is the compact glanceable version (fits in the right panel alongside the chat). Different depth, same data.

6. **Mobile layout:** Not yet fully spec'd for Lovable. Need to define: bottom tab bar items, what happens to the right panel, chat-only mode, etc.

---

## WHAT'S NOT YET SPEC'D (Needs prompts before Lovable build)

1. **Drive page** — Full Genspark-style file manager. Prompt needs to be written.
2. **Login page** — Simple email/password login. Not yet written.
3. **Individual builder flow** — What happens when you click "Start →" on a builder? Does it open a new IQ Claw chat? Does it show a brief form first? Needs to be defined.
4. **Content detail view** — What happens when you click a piece of content in the library? Preview? Edit? Share? Needs to be defined.
5. **Settings page detail** — Account, billing, brand settings, integrations management. Partially covered in the Settings tab but needs full-page treatment.
6. **Notification system** — How do alerts and notifications appear? Toast? Badge? Notification center? Needs to be defined.
7. **Mobile responsive layout** — Bottom tab bar, full-screen modes, swipe gestures.

---

*This blueprint is the single reference document for the Lovable build. Every prompt written for Lovable should reference this document to ensure consistency across all screens and components.*
