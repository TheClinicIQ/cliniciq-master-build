# ClinicIQ — Complete Application Build Prompt for Lovable

Build a full web application called **ClinicIQ** — an AI-powered growth platform for health practitioners. The application has a sign-up page, an onboarding flow, and a main workspace with multiple pages. Build everything described below as a working React application with routing, navigation, and realistic mock data. Use Tailwind CSS for styling. Use shadcn/ui components where appropriate.

---

## DESIGN SYSTEM (Global)

- **Theme:** Light mode only (no dark mode toggle for v1)
- **Background:** #F8F9FA for page backgrounds. #FFFFFF for cards and panels.
- **Text:** #1F2937 primary. #6B7280 secondary. #9CA3AF disabled/placeholder.
- **Accent:** #10B981 (teal/emerald) for CTAs, active states, positive indicators, links.
- **Alerts:** #EF4444 red for alerts/negative. #F59E0B amber for warnings. #22C55E green for positive metrics.
- **Borders:** #E5E7EB for card borders, dividers, panel separators.
- **Border radius:** 12px for cards, 8px for buttons, 24px for input fields and pills.
- **Font:** Inter. Clean, modern, sans-serif.
- **Icons:** Use Lucide React icons throughout.
- **Overall aesthetic:** Premium, clean, minimal. White cards on light gray backgrounds. Subtle shadows. No visual clutter. Think Stripe dashboard meets a high-end health brand.

---

## ROUTE STRUCTURE

```
/signup          → Sign-up page
/login           → Login page
/onboarding      → Onboarding flow (IQ Claw conversation)
/                → Main workspace (IQ Claw chat + right panel) — default logged-in route
/home            → Home dashboard
/workflows       → Workflows page
/teams           → Teams page
/drive           → Drive / file manager page
```

All routes except `/signup` and `/login` share the same left sidebar navigation.

---

## PAGE 1: SIGN-UP (`/signup`)

Full-page layout. No sidebar. Two columns on desktop (value prop left, form right). Single column stacked on mobile.

### Left Column
- **Headline:** "Your AI Growth Team Is Ready."
- **Subheadline:** "ClinicIQ builds, runs, and optimizes your entire growth engine — content, ads, funnels, email, webinars — in your voice, for your patients."
- Three proof points with check icons:
  - "Content that sounds like you wrote it on your best day"
  - "From onboarding to first content batch in under 30 minutes"
  - "174 AI agents working behind one conversation"
- Social proof at bottom: avatar stack of 3–4 small circles + "Trusted by 200+ health practitioners"

### Right Column — Form Card
White card with subtle shadow on the #F8F9FA background.

- Header: "Get Started — Free" + subtext "No credit card required"
- Fields:
  1. Full Name (text, placeholder: "Dr. Sarah Chen", required)
  2. Email (email, placeholder: "sarah@example.com", required)
  3. Password (password with show/hide toggle, required)
  4. Website URL (url, placeholder: "https://yourpractice.com", required, helper text: "We'll analyze your site to personalize your experience")
  5. Primary Specialty (select dropdown: Functional Medicine, Chiropractic, Physical Therapy, Naturopathic Medicine, Dentistry/TMJ, Med Spa/Aesthetics, Mental Health, Nutrition/Dietetics, Health Coaching, Other)
  6. Instagram Handle (text, placeholder: "@yourhandle", optional, helper text: "Helps us understand your voice faster")
- CTA button: "Start Building →" — full width, accent color, large (h-12)
- Below: "By signing up you agree to our Terms and Privacy Policy" (small gray text with links)
- Below that: "Already have an account? Log in" link

### Top Bar (minimal)
ClinicIQ logo on the left. "Log in" text link on the right. Nothing else.

On submit: navigate to `/onboarding`.

---

## PAGE 2: LOGIN (`/login`)

Simple centered card on #F8F9FA background. ClinicIQ logo above the card.

- Email field
- Password field with show/hide
- "Log In" button (full width, accent color)
- "Forgot password?" link
- "Don't have an account? Sign up" link

On submit: navigate to `/` (main workspace).

---

## PAGE 3: ONBOARDING (`/onboarding`)

Three-panel layout:
- Left: Sidebar rail (72px) — same sidebar as the main app but all items are **visually disabled** (grayed out, not clickable) except the IQ item which is active. This previews the full platform without letting them navigate away.
- Center: IQ Claw chat interface (fills ~55% of remaining space)
- Right: Onboarding progress panel (~45% of remaining space)

### Center Panel — IQ Claw Chat

Top bar: Teal circular IQ avatar + "IQ Claw" bold + green dot + "Online" text.

**Pre-populated first message from IQ Claw (visible on page load — never an empty chat):**

> "Hi Dr. Sarah. I've been looking at your practice before you arrived.
>
> You've been in functional medicine for about 11 years. Your website leads with a hormone reset protocol, and your Instagram — your cortisol content outperforms everything else by about 3x on saves.
>
> That 'your body isn't broken' line? That's the kind of mechanism language that stops people mid-scroll.
>
> Before I build anything, I need to understand your voice. Not your website copy — the way you actually talk.
>
> Imagine a patient sits down across from you. She's exhausted. She's been to five doctors. She tells you, 'Nobody can figure out what's wrong with me.'
>
> What do you say to her?"

IQ Claw messages: light gray bubble (#F3F4F6), dark text. Left-aligned with IQ avatar.

**Mock expert reply (right-aligned, accent-tinted bubble):**

> "Honestly? I'd say something like — 'That makes sense. Because they were looking at your symptoms one at a time instead of the whole picture. Your body is a system, and right now it's sending you signals. We just need to learn how to read them.'"

**IQ Claw follow-up:**

> "Strong. 'Symptoms one at a time vs. the whole picture' — that's a reframe your audience will remember. And 'your body is sending you signals' connects to the content that's already working on your Instagram.
>
> I'm hearing: systems-level thinking, signal-based language, reassuring but direct. You don't coddle — you explain.
>
> Now: what words do you never want to see in your marketing? The ones that make you cringe when a competitor uses them."

**Expert reply:**

> "'Wellness journey.' 'Holistic' — everyone uses it and it means nothing. 'Bio-hacking.' And 'optimal' anything."

**IQ Claw:**

> "Banned. They're dead to us.
>
> We're making good progress. I have enough to show you something. Give me 90 seconds."

Then a brief loading animation (pulsing dots or spinner), followed by:

> "Here's a preview of what your content will look like. Written in YOUR voice, targeting your ideal patient:"

**Inline Instagram post preview card:**
White card with border. Mock IG post layout:
- Header: "SC" avatar circle + "dr.sarahchen"
- Image area: placeholder lifestyle image with italic overlay text: "Your body is telling you exactly what's wrong."
- Caption preview: "She hadn't slept in 3 years. Not because she didn't try — because every doctor told her the same thing. 'It's just stress. Try melatonin.' Nobody tested her cortisol..."
- Below caption: "Does it feel like you?"

**Bottom input bar (fixed):**
Rounded input field with placeholder "Type your answer..." + microphone icon + accent send button.

### Right Panel — Onboarding Progress

Sticky card:

**"Building Your Profile"** header.
Progress bar: accent fill at 68%.

Checklist:
- ✅ Your story (complete — accent checkmark)
- ✅ Your voice (complete)
- ✅ Your patient avatar (complete)
- 🔄 Your offer stack (in progress — amber spinner icon)
- ○ Your proof bank (not started — gray circle)

"Est. ~8 min remaining" in gray text.

Divider.

**"WHAT WE KNOW SO FAR"** section — data that fills in as the conversation progresses:

- **Specialty:** Functional Medicine
- **Voice:** Direct, systems-thinker, signal-based language
- **Banned Words:** (shown as small gray tags/pills) wellness journey · holistic · bio-hacking · optimal
- **Signature Phrases:** "your body is sending you signals" · "the whole picture"
- **Primary Avatar:** Exhausted women, 35-50, dismissed by conventional medicine

Each item should have a subtle fade-in when it appears (simulating real-time capture).

Divider.

Small info card at bottom:
> "💡 Every word of content, every ad, every email your platform produces runs through this profile. The better I know you, the less you'll ever need to edit."

---

## LEFT SIDEBAR — Shared Component (all pages except signup/login)

72px wide. White or #F8F9FA background. Subtle right border (#E5E7EB).

All items center-aligned. Each item: Lucide icon (20px) centered, with tiny label (10px, #9CA3AF) beneath.

### Items top to bottom:

1. **Logo** — Small dark rounded square (~32px) with a star/sparkle icon inside. No label. Fixed at top with 16px padding.

2. **+ New** — Plus icon. Label: "New". Clickable — opens a flyout panel (see FLYOUTS section below).

3. **Home** — House icon. Label: "Home". Links to `/home`.

4. **IQ** — BrainCircuit or Globe icon (something that feels like "intelligence"). Label: "IQ". Links to `/`. **This is the main product — the equivalent of Genspark's "Claw" button.**

5. **Workflows** — GitBranch or Network icon. Label: "Workflows". Links to `/workflows`.

6. **Teams** — Users icon. Label: "Teams". Links to `/teams`.

7. **Drive** — FolderOpen icon. Label: "Drive". Links to `/drive`. Shows a small red badge with "3" when items need attention.

8. **More** — MoreHorizontal (three dots) icon. Label: "More". Clickable — opens a flyout panel.

**Bottom section (pinned to bottom with 16px padding):**

9. **Settings** — Settings (gear) icon. No label.
10. **Profile** — A 28px circle with accent background and white initials "SC". Below it in tiny text: "Dr. Sarah Chen"

### Active state
The current page's icon has a white circular background (#FFFFFF, 36px circle) behind it and the icon color changes to #1F2937 (dark). All inactive icons are #9CA3AF (gray). Hover: icon transitions to #6B7280.

### Sidebar behavior
- Always visible on desktop
- On mobile (< 768px): hidden, accessible via hamburger menu that slides it in as an overlay

---

## FLYOUT: "+ New" Button

When clicked, a panel slides out to the right of the sidebar (480px wide, white, rounded-xl, shadow-xl). Closes on click-outside or Escape key.

### Content:

**Section 1: "Quick Actions"** header
Three horizontal cards:
- 📝 Quick Post — "One post, any topic"
- ✉️ Quick Email — "Single email, any type"
- 📢 Quick Ad — "Hook + creative + copy"

**Section 2: "Builders"** header
3-column grid of builder icons (colored circular icons, 48px, with label below):

Row 1: Content Builder | Funnel Builder | Webinar Builder
Row 2: Email Builder | Ad Creative | Lead Magnet
Row 3: Program Builder | Podcast Builder | Sales Scripts
Row 4: Website Builder | Campaign Builder | Challenge Builder

Each icon has a distinct accent shade. Clicking any opens `/` with a pre-populated IQ Claw message about that builder.

**Section 3: "Recent"** header with "View All →" link
List of 5 recent conversations (icon + title + time ago).

---

## FLYOUT: "More" Button

When clicked, smaller flyout (280px wide).

List items:
- 📥 Inbox — "2 new" badge
- 🔗 Hub — arrow →

Divider.

- 🌙 Dark Mode — toggle switch (off)
- ❓ Help & Support — arrow →
- 📱 Download App — arrow →

Bottom: user profile card (avatar circle + name + "Pro Plan" + gear icon).

---

## PAGE 4: MAIN WORKSPACE — IQ CLAW (`/`)

Three-panel layout:
- Left: Sidebar (72px) — IQ is the active item
- Center: IQ Claw chat (~50% of remaining space)
- Right: Tabbed context panel (~50% of remaining space)
- A draggable vertical resize handle between center and right panels

### Center Panel — IQ Claw Chat

Top bar: IQ avatar + "IQ Claw" + green "Online" dot | Right side: pill showing "Content batch Apr Wk 2" + three-dot menu.

**Morning briefing message (IQ Claw):**

> "Morning, Dr. Sarah.
>
> 🔴 **One thing needs your eye** — your Meta ad set B is fatiguing. CTR dropped 40% over the last three days. I already have 2 replacement hooks ready.
>
> 🟢 **Good news** — your cortisol carousel hit 4.2% engagement this week. That's double your average. I've queued 3 more in the same format.
>
> 📋 **5 posts for next week** ready to review. 3 are solid, 2 need your eye on the hooks.
>
> Where do you want to start?"

Three pill buttons below: [Fix the ad hooks] [Review content] [Show me analytics]

**Content review message (IQ Claw):**

> "Post 1 of 5. Instagram authority piece targeting the 'Stressed Mom Sarah' persona. PAS framework. I used your 'your body is telling you exactly what's wrong' line as the opener because it hit 2x saves last month. Take a look."

**Inline Instagram preview card:**
- "SC" avatar + "dr.sarahchen"
- Image placeholder with overlay text: "Your body is telling you exactly what's wrong."
- Caption preview
- Tags row: "Persona: Stressed Mom" | "Framework: PAS" | "Scheduled: Thu 10am"
- Action buttons: [✅ Approve] [✏️ Tweak] [🗑️ Veto]

**Input bar (bottom, fixed):**
"Message IQ Claw..." + mic icon + send button.
Helper text: "IQ Claw can analyze patterns across all your active channels in real-time."

### Right Panel — Tabbed Context Panel

**Tab bar across the top** (horizontally scrollable with < > arrows if overflow):

Dashboard | Brand | Strategy | Builders | Content | Files | Calendar | Schedules | Channels | Services | Training | Settings

Each tab has a small icon above its label. Active tab: accent underline + darker text. Inactive: gray.

**"Dashboard" is active by default.** Show this content:

**⚠️ NEEDS ATTENTION**
- Card: "Ad Set B fatiguing" — "-40% CTR" red badge — "Fix Now >" accent link
- Card: "Email open rates" — "22% → 16%" amber badge — "Review >" accent link

**✅ WHAT'S WORKING**
- Card: "Cortisol carousel" — "4.2% engagement, 2x average" — small progress bar
- Card: "Welcome sequence" — "42% Open" green — "Exceeding benchmark"

**📈 QUICK METRICS**
- Engagement: 14.2K ↑12% | Saves: 892 ↑23% | Email opens: 16.2% ↓4% | Ad spend: $45/day | New leads: 8 this wk

**📅 THIS WEEK**
Mon: 2 posts | Tue: 1 post | Wed: 2 posts + email | Thu: Webinar | Fri: 1 post

#### Brand Tab
- Voice DNA card: ✅ Locked — tone, signature phrases, banned words, [Edit →]
- Avatars: 2 persona cards ("Stressed Mom Sarah" selected, "Weekend Warrior Mike") with [Select] [Edit →]
- Offers: Entry ($0), Core ($4,800), Premium ($12,000) with Before→After descriptions, [Edit →]
- Mechanism: "The Signal Reset Protocol" + One Big Domino, [Edit →]
- Proof Bank: Score 62/100, 3 stories, 2 videos, 12 testimonials, [Add Proof →]
- Brand Assets: Logo, 3 color swatches, font name, [Edit →]

#### Strategy Tab
- Brand North Star: positioning + always/never rules + [View →]
- Monthly Master Plan: "April 2026 — Hormone Reset Campaign" + 🟢 On track + [View →] [Refresh →]
- Messaging Briefs: 2 brief cards with asset counts
- Performance Insights: 3 bullet points from analytics + [Full Analysis →]

#### Builders Tab
- Header: "Choose a builder or tell IQ Claw what you need"
- Quick Launch pills: [Content Batch] [Launch Campaign] [Monthly Refresh]
- 2-column grid of 12 builder cards (icon + name + description + [Start →])

#### Content Tab
- Filter pills: All | Posts | Carousels | Reels | Emails | Ads | Lead Magnets
- Sort: "Newest ▾"
- 2-column thumbnail grid with status badges (✅ Published, 🕐 Scheduled, 📝 Draft, 📋 Review)
- "Showing 24 of 156 assets" + [Load More]

#### Files Tab
- Breadcrumb: "/ My Drive"
- Toolbar: [+ New Folder] | Sort: "Modified ▾" | Search field
- List/grid view toggle
- Folder list: Content, Webinars, Funnels, Emails, Ads, Lead Magnets, Strategy Docs, Brand Assets
- File rows with: icon, name, size, modified date, actions (•••)
- Bottom: "1.2 GB of 10 GB used" progress bar

#### Calendar Tab
- Week/Month toggle
- Weekly grid: Mon–Sun columns with colored content cards
- Summary: "5 posts · 1 story · 1 email · 1 webinar this week"

#### Schedules Tab
- [+ New Schedule] button
- Filter pills: All | Active | Paused
- Schedule cards with: title, frequency, description, next run time, on/off toggle, ••• menu
- Show 5–6 mock schedules: Morning Briefing (daily 8am), Performance Scan (every 6h), Weekly Content Batch (Mon 7am), Weekly Summary (Fri 5pm), Email Health Check (Wed 9am), Monthly Strategy Refresh (1st of month)

#### Channels Tab
- Platform cards: Instagram ✅ (12.4K followers, 3.2% eng), Facebook ✅, YouTube ⚪ [Connect →], TikTok ⚪ [Connect →], LinkedIn ⚪ [Connect →]

#### Services Tab
- Integration cards: GoHighLevel ✅, Zoom ✅, Stripe ✅, Mailchimp ✅, Slack ⚪ [Connect →], Calendly ⚪, Zapier ⚪, Google Analytics ⚪, Meta Business ✅

#### Training Tab
- "Platform Mastery — 35% complete" progress bar
- Checklist: ✅ Complete onboarding, ✅ Review first batch, ☐ Connect Instagram, ☐ Launch campaign, ☐ Review analytics
- 3 tip cards

#### Settings Tab
- Account: Name, email, plan
- Brand: Voice DNA status, colors, logo
- Integrations: quick links
- Billing: plan, usage

---

## PAGE 5: HOME (`/home`)

Sidebar (72px, Home active) + full-width content area. No chat panel. No right panel.

### Top Bar
- "Good evening, Dr. Sarah" large bold + "Tuesday, April 7, 2026" gray
- Right: [Open IQ Claw] accent button + "IQ Score: 72/100" badge with circular progress

### Two-Column Layout

**Left Column (~60%):**

1. **🔥 Needs Your Attention** — 3 alert rows with colored dots and action links (Fix Now →, Review →, Review Content →)

2. **📊 Performance Overview** — "This Week vs. Last Week" + [7D | 30D | 90D] toggle
   - 4 metric cards: Engagement 14.2K ↑12%, Saves 892 ↑23%, Email Opens 16.2% ↓4%, New Leads 8 ↑33%
   - Line chart below (teal line, Mon-Sun, values 8K→14K)

3. **📅 Content Calendar** — Weekly strip Mon–Sun with colored content tags + "View Full Calendar →"

4. **🚀 Activity Feed** — 5 recent entries with icons and timestamps

**Right Column (~40%):**

1. **🧬 Brand Health** — Voice DNA ✅, Avatars 2, Mechanism ✅, Offers 3, Proof Bank 62/100

2. **✅ What's Working** — Top 3 performers with sparkline charts

3. **💡 Recommendations** — 3 IQ Claw suggestions with accent left-border and [Apply →] links

4. **⚡ Quick Actions** — 2×2 grid: Create Content, Build Webinar, Write Emails, Run Analysis

### Bottom Bar
"ClinicIQ Pro Plan" | "● Last sync: 2 minutes ago" | "Help & Support" · "⌘K Quick Search"

---

## PAGE 6: WORKFLOWS (`/workflows`)

Sidebar (72px, Workflows active) + full-width content.

### Header
"Workflows" + "Launch, manage, and track your automated growth engine"
Right: [+ New Workflow] button + "● 12 active · 2 running now" badge

### Tabs: All Workflows | Running (2) | Completed | Templates

### Content:

**Running Now** (green pulse dot) — 2 workflow cards with progress bars:
1. "Content Batch — April Week 2" — 65% — "4 of 7 complete · ~3 min remaining" — [View Progress →]
2. "Email Sequence — Post-Webinar" — 40% — "1 of 4 complete · ~6 min remaining" — [View Progress →]

**Builders** — 4×3 grid of 12 builder cards (icon + name + description + "Last run: X ago" + entire card clickable)

**Recent** — Table: Status | Workflow | Type | Started | Duration | Items | Actions (View/Rerun)
Show 5 rows of mock completed workflows.

### Bottom Bar (same as Home)

---

## PAGE 7: TEAMS (`/teams`)

Sidebar (72px, Teams active) + full-width content.

### Header
"Teams" + "Manage your team, roles, and permissions"
Right: "● 4 members · 2 online" + [+ Invite Member] button

### Tabs: Members | Roles | Activity | Settings

### Members Tab (default):
Search bar + Role filter dropdown + List/Grid toggle

Table: Member | Role | Status | Last Active | Permissions | Actions
4 rows:
1. Dr. Sarah Chen (SC) — Owner — 🟢 Online — Now — Full Access
2. Josh Axe (JA) — Admin — 🟢 Online — Now — Full Access
3. Maria Lopez (ML) — Editor — ⚪ Offline — 2h ago — Can edit, no billing
4. Tom Wilson (TW) — Viewer — ⚪ Offline — Yesterday — View only

"4 of 5 seats used" progress bar + "Upgrade to add more" link

---

## PAGE 8: DRIVE (`/drive`)

Sidebar (72px, Drive active) + full-width file manager.

### Header
Breadcrumb: "/ My Drive" (updates when navigating folders)
Right: [↑ Upload] button + List/Grid view toggle

### Toolbar
[+ New Folder] + Sort: "Modified ▾" + Search: "Search files..."

### File Browser (list view default)
Folders listed first:
- 📁 Content — Apr 7
- 📁 Webinars — Apr 5
- 📁 Funnels — Apr 3
- 📁 Emails — Apr 6
- 📁 Ads — Apr 4
- 📁 Lead Magnets — Mar 28
- 📁 Strategy Docs — Apr 1
- 📁 Brand Assets — Mar 30

Then files:
- 📄 Monthly_Master_Plan_April.md — 12.4 KB — Apr 1
- 📄 Brand_North_Star.md — 8.2 KB — Mar 30
- 🖼️ Logo_Primary.png — 245 KB — Mar 25

Each row: hover state, ••• menu (Download, Rename, Move, Delete).

### Bottom
"11 items · 156 files total" + "1.2 GB of 10 GB used" progress bar

---

## RESPONSIVE / MOBILE BEHAVIOR

On screens < 768px:
- Sidebar hides behind a hamburger menu (top-left)
- On the IQ workspace: right panel hides, chat fills screen. A bottom tab bar appears with 5 items: 💬 Chat | 📊 Dashboard | 📁 Content | 🔄 Workflows | ••• More
- On full-page screens (Home, Workflows, Teams, Drive): content stacks vertically, cards go full-width

---

## IMPORTANT BUILD NOTES

1. **All mock data should be realistic and consistent** — same practitioner (Dr. Sarah Chen), same metrics, same content across all screens. The data should tell a coherent story.

2. **Navigation must work** — clicking sidebar items navigates between routes. Active states update. Flyouts open and close.

3. **The right panel tabs must switch content** — clicking each tab shows its content. Dashboard is default.

4. **No empty states** — every screen, every tab, every panel has mock data. IQ Claw always has a message. The dashboard always has metrics. The calendar always has events.

5. **The aesthetic matters as much as the function** — this needs to look like a premium product, not a prototype. Clean spacing. Consistent sizing. Proper visual hierarchy. Every card, every button, every text element should feel intentional.

6. **The chat interface should feel real** — messages have timestamps, avatar icons, proper spacing between conversation turns. The input bar should look like a real messaging app (think iMessage or Slack).
