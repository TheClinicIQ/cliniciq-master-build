# ClinicIQ — Main App Interface Prompt
## For Lovable / AI Builder Platform
---

## What To Build

The main ClinicIQ interface — the screen the expert sees every day after onboarding is complete. This is where IQ Claw operates as their chief of staff. Same three-panel layout as onboarding, but now the sidebar is fully active, the right panel shows the contextual dashboard instead of the progress card, and IQ Claw opens with a morning briefing instead of onboarding questions.

This is the "second login" experience — the expert walks in and IQ Claw is already working.

## Design System (Same as Onboarding — Consistent Throughout)

- **Dark theme.** Background: #0F1419. Panel backgrounds: #161B22 (sidebar, right panel), #0F1419 (center chat area).
- **Accent color:** Teal/cyan (#00D4AA) for CTAs, active states, positive indicators.
- **Alert colors:** Red (#EF4444) for alerts/fires. Amber (#F5A623) for warnings/attention. Green (#22C55E) for positive/wins.
- **Text:** White (#FFFFFF) primary. Light gray (#94A3B8) secondary. Dark gray (#4B5563) for disabled/placeholder.
- **Typography:** Same clean sans-serif throughout. Inter or Plus Jakarta Sans.
- **Borders/dividers:** Very subtle, #1E2530 or similar. Panels are separated by hairline borders or subtle shadows, not heavy lines.

## Left Panel — Full Sidebar (240px wide, collapsible)

The sidebar is now fully active and expanded. It has three sections stacked vertically:

### Section 1: Top — Brand + New Chat

```
┌──────────────────────┐
│  ▣ ClinicIQ          │  ← Logo / wordmark
│                      │
│  [+ New Chat]        │  ← Teal outlined button
└──────────────────────┘
```

- ClinicIQ logo/wordmark at the very top
- "New Chat" button below it — teal outline, white text, rounded. Creates a new IQ Claw conversation thread.

### Section 2: Middle — Chat History

A scrollable list of previous conversations with IQ Claw, ordered most recent first. Each entry shows:

```
┌──────────────────────┐
│  Today               │  ← Date group header
│                      │
│  📝 Content batch    │  ← Conversation title
│  for April Week 2    │     (auto-generated from
│                      │      first message topic)
│  📊 Weekly           │
│  performance review  │
│                      │
│  Yesterday           │
│                      │
│  🔄 Webinar script   │
│  revisions           │
│                      │
│  ✉️ Email sequence    │
│  for new leads       │
│                      │
│  Last Week           │
│                      │
│  🚀 Campaign launch  │
│  plan - hormone      │
│  reset               │
│                      │
│  ... (scrollable)    │
└──────────────────────┘
```

**Design details:**
- Each conversation entry is a card/row with subtle hover state (slightly lighter background)
- The currently active conversation is highlighted with a teal left border or teal background tint
- Conversation titles are auto-generated from the topic of the first message (editable by the expert if they click the title)
- Small emoji/icon prefix based on topic category (content 📝, analytics 📊, email ✉️, ads 📢, etc.)
- A search bar at the top of the chat history: "Search conversations..." with a magnifying glass icon
- Older conversations collapse into date groups (Today, Yesterday, Last Week, Last Month, Older)

### Section 3: Bottom — Module Navigation + Profile

Below the chat history (separated by a subtle divider line), the module shortcuts:

```
┌──────────────────────┐
│  ─────────────────── │
│                      │
│  📄 Content          │  ← Opens Content Library
│  🔗 Funnels          │     in the right panel
│  ✉️ Email            │
│  📢 Ads              │
│  🎓 Programs         │
│  🎙️ Podcast          │
│  📊 Analytics        │
│                      │
│  ─────────────────── │
│                      │
│  🔄 Workflows        │  ← Opens Workflows panel
│                      │
│  ─────────────────── │
│                      │
│  ⚙️ Settings          │
│  👤 Dr. Sarah Chen   │  ← Avatar + name
└──────────────────────┘
```

**Module navigation behavior:**
- Clicking any module (Content, Funnels, Email, etc.) does NOT navigate to a new page. It opens a **library view in the right panel** showing all assets of that type. The center panel (IQ Claw chat) remains visible and contextually aware.
- The Workflows shortcut opens a workflows panel in the right panel (see Right Panel section below).
- Settings opens a settings page (can be a separate route).
- Expert profile at the very bottom with their avatar/photo and name.

**Sidebar collapse behavior:**
- A collapse toggle (hamburger or « icon) at the top collapses the sidebar to icon-only mode (64px wide) — same as during onboarding. This gives more room to the chat on smaller screens.
- On mobile: sidebar is hidden behind a hamburger menu, slides in as an overlay.

## Center Panel — IQ Claw Chat (Primary Interface)

This is the heart of the platform. Same chat interface as onboarding, but now showing post-onboarding daily interactions.

### Top Bar

```
┌─────────────────────────────────────────────────────────────────┐
│  🤖 IQ Claw  ● Online    │    📝 Content batch for April Wk 2  │
└─────────────────────────────────────────────────────────────────┘
```

- Left: IQ Claw avatar + name + green online dot
- Right: Current conversation title (matches the selected chat history item)

### The Morning Briefing (Default State When Expert Opens App)

When the expert opens ClinicIQ for the first time that day, IQ Claw has already prepared a morning briefing. This is the first thing they see — never an empty chat.

**Example morning briefing message (mock for prototype):**

```
┌─────────────────────────────────────────────────────────────────┐
│  🤖 IQ Claw                                          8:47 AM   │
│                                                                 │
│  Morning, Dr. Sarah.                                            │
│                                                                 │
│  🔴 One thing needs your eye — your Meta ad set B is            │
│  fatiguing. CTR dropped 40% over the last three days.           │
│  I already have 2 replacement hooks ready.                      │
│                                                                 │
│  🟢 Good news — your cortisol carousel hit 4.2%                 │
│  engagement this week. That's double your average.              │
│  I've queued 3 more in the same format.                         │
│                                                                 │
│  📋 You've got 5 posts for next week ready to review.           │
│  3 are solid, 2 need your eye on the hooks.                     │
│                                                                 │
│  Where do you want to start?                                    │
│                                                                 │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │
│  │ Fix the ad  │  │ Review      │  │ Show me     │             │
│  │ hooks       │  │ content     │  │ analytics   │             │
│  └─────────────┘  └─────────────┘  └─────────────┘             │
└─────────────────────────────────────────────────────────────────┘
```

**Design details for the briefing:**
- Red dot (🔴) for alerts, green dot (🟢) for wins, blue clipboard (📋) for action items
- The three quick-action buttons at the bottom are teal-outlined chips/pills. Clicking one is equivalent to typing that request — it sends a message to IQ Claw and triggers the relevant flow.
- Quick-action buttons have subtle hover state (fill with teal, text goes white)

### Content Review Flow (Example of What Happens After Clicking "Review Content")

**IQ Claw:**
> "Post 1 of 5. Instagram authority piece targeting the 'Stressed Mom Sarah' persona. PAS framework — leads with the sleep problem, agitates with the 'doctor told her it's just stress' angle, solves with your cortisol testing.
>
> I used your 'your body is telling you exactly what's wrong' line as the opener because it hit 2x saves last month.
>
> Take a look."

**Below this message, an inline content preview card:**

```
┌─────────────────────────────────────────────────────────────────┐
│  ┌──────────────────────────────────────────────┐               │
│  │                                              │               │
│  │   [Mock Instagram post preview]              │               │
│  │                                              │               │
│  │   Image: warm, lifestyle photography         │               │
│  │   with text overlay:                         │               │
│  │   "Your body is telling you                  │               │
│  │    exactly what's wrong."                    │               │
│  │                                              │               │
│  │   Caption preview below the image:           │               │
│  │   "She hadn't slept in 3 years..."           │               │
│  │                                              │               │
│  └──────────────────────────────────────────────┘               │
│                                                                 │
│  Persona: Stressed Mom Sarah  │  Framework: PAS                 │
│  Awareness Level: 2           │  Scheduled: Thu 10am            │
│                                                                 │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐                   │
│  │ ✅ Approve │  │ ✏️ Tweak   │  │ 🗑️ Veto   │                   │
│  └───────────┘  └───────────┘  └───────────┘                   │
└─────────────────────────────────────────────────────────────────┘
```

**The content preview card:**
- Shows a mock of the actual post (image + caption preview)
- Metadata tags below: persona, framework, awareness level, scheduled time
- Three action buttons: Approve (green tint), Tweak (amber tint), Veto (red tint)
- Clicking "Approve" sends a confirmation, IQ Claw says "Approved. Next." and shows Post 2.
- Clicking "Tweak" opens the chat input focused with a placeholder: "What would you change?"
- Clicking "Veto" prompts IQ Claw: "Got it. Was it the angle, the tone, or something specific?"

### Input Area (Same as Onboarding)

```
┌─────────────────────────────────────────────────────────────────┐
│  [Message IQ Claw...]                               🎙️  ➤      │
└─────────────────────────────────────────────────────────────────┘
```

- Persistent at the bottom
- Placeholder: "Message IQ Claw..."
- Voice input (🎙️) and send (➤) buttons

## Right Panel — Contextual Dashboard (320px wide)

The right panel changes based on what the expert is currently doing. It has a default state and several contextual states.

### Default State: The Dashboard

This is what shows when the expert first opens the app or isn't actively in a specific flow.

```
┌─────────────────────────────┐
│  📊 DASHBOARD               │
│  ─────────────────────────  │
│                             │
│  🔥 NEEDS ATTENTION         │
│                             │
│  🔴 Ad Set B fatiguing      │
│     CTR: -40% (3 days)      │
│     [Fix Now →]             │
│                             │
│  🟡 Email open rates        │
│     declining (22% → 16%)   │
│     [Review →]              │
│                             │
│  ─────────────────────────  │
│                             │
│  ✅ WHAT'S WORKING          │
│                             │
│  🟢 Cortisol carousel       │
│     4.2% engagement         │
│     2x your average         │
│                             │
│  🟢 Email welcome seq       │
│     42% open rate           │
│                             │
│  ─────────────────────────  │
│                             │
│  📅 THIS WEEK               │
│                             │
│  Mon  📝 2 posts (10am, 2pm)│
│  Tue  📝 1 post (10am)      │
│  Wed  📝 2 posts + story    │
│  Thu  🎥 Webinar live       │
│  Fri  📝 1 post (10am)      │
│                             │
│  ─────────────────────────  │
│                             │
│  📈 QUICK METRICS           │
│                             │
│  Engagement   ↑ 12%         │
│  Saves        ↑ 23%         │
│  Email opens  ↓ 4%          │
│  Ad spend     $45/day       │
│  New leads    8 this week   │
│                             │
└─────────────────────────────┘
```

**Design details:**
- Three sections answering: What's on fire? What's working? What's coming this week?
- Red/amber/green color coding for status
- "[Fix Now →]" and "[Review →]" are small teal links that, when clicked, send a message to IQ Claw in the center panel (e.g., clicking "Fix Now" on the ad alert sends "Let's fix the ad set B issue")
- The weekly calendar is a compact list view, not a full calendar grid
- Quick metrics show directional arrows with percentage changes, color-coded (green for up, red for down)
- All numbers are specific. Never "performing well" — always "4.2% engagement, 2x average."

### Contextual State: Content Library (When "Content" Is Clicked in Sidebar)

```
┌─────────────────────────────┐
│  📄 CONTENT LIBRARY         │
│  ─────────────────────────  │
│                             │
│  [All] [IG] [FB] [Ads]     │  ← Filter tabs
│  [Email] [Blog]            │
│                             │
│  Sort: Newest ▾             │
│                             │
│  ┌────────┐ ┌────────┐     │
│  │ 📸     │ │ 📸     │     │
│  │        │ │        │     │
│  │Post 1  │ │Post 2  │     │
│  │✅ Apr 7│ │✅ Apr 8│     │
│  └────────┘ └────────┘     │
│                             │
│  ┌────────┐ ┌────────┐     │
│  │ 📸     │ │ 📸     │     │
│  │        │ │        │     │
│  │Post 3  │ │Post 4  │     │
│  │🕐 Apr 9│ │🔄 Draft│     │
│  └────────┘ └────────┘     │
│                             │
│  ... (scrollable grid)      │
│                             │
│  Showing 24 of 156 assets   │
│  [Load More]                │
└─────────────────────────────┘
```

- Thumbnail grid of all content assets
- Filter tabs across the top
- Status badges on each thumbnail (✅ Published, 🕐 Scheduled, 🔄 Draft, 📋 Pending Review)
- Clicking any asset opens it in a detail view within the right panel AND sends context to IQ Claw: "You're looking at Post 3. Want me to do anything with it?"

### Contextual State: Workflows Panel (When "Workflows" Is Clicked in Sidebar)

```
┌─────────────────────────────┐
│  🔄 WORKFLOWS               │
│  ─────────────────────────  │
│                             │
│  CONTENT                    │
│  ┌─────────────────────┐    │
│  │ 📝 Create Content   │    │
│  │    Batch             │    │
│  │ Generate a full week │    │
│  │ of content           │    │
│  │          [Start →]   │    │
│  └─────────────────────┘    │
│                             │
│  ┌─────────────────────┐    │
│  │ ⚡ Quick Post        │    │
│  │ One post, any topic  │    │
│  │          [Start →]   │    │
│  └─────────────────────┘    │
│                             │
│  CAMPAIGNS                  │
│  ┌─────────────────────┐    │
│  │ 🚀 Launch Campaign  │    │
│  │ Full launch sequence │    │
│  │ content + email +    │    │
│  │ ads + funnels        │    │
│  │          [Start →]   │    │
│  └─────────────────────┘    │
│                             │
│  ┌─────────────────────┐    │
│  │ 🎥 Build Webinar    │    │
│  │ Script + slides +    │    │
│  │ follow-up sequence   │    │
│  │          [Start →]   │    │
│  └─────────────────────┘    │
│                             │
│  STRATEGY                   │
│  ┌─────────────────────┐    │
│  │ 📊 Monthly Strategy │    │
│  │    Refresh           │    │
│  │ Performance review + │    │
│  │ next month plan      │    │
│  │          [Start →]   │    │
│  └─────────────────────┘    │
│                             │
│  ┌─────────────────────┐    │
│  │ 🎯 Build Email      │    │
│  │    Sequence          │    │
│  │ Any type: welcome,   │    │
│  │ nurture, promo, etc  │    │
│  │          [Start →]   │    │
│  └─────────────────────┘    │
│                             │
│  ┌─────────────────────┐    │
│  │ 📢 Create Ad Set    │    │
│  │ Hooks + creatives +  │    │
│  │ copy variants        │    │
│  │          [Start →]   │    │
│  └─────────────────────┘    │
│                             │
└─────────────────────────────┘
```

- Workflow cards grouped by category (Content, Campaigns, Strategy)
- Each card has: icon, title, short description, [Start →] button
- Clicking [Start →] opens a new chat with IQ Claw pre-seeded with that workflow context. Example: clicking "Create Content Batch" opens a new chat where IQ Claw says: "Content batch for next week. I'll pull from your Monthly Master Plan. Any specific topics, angles, or patient stories you want featured — or should I run with what's performing best?"
- These workflows are the Builder agents exposed as user-friendly one-click triggers

### Contextual State: Analytics View (When "Analytics" Is Clicked in Sidebar)

```
┌─────────────────────────────┐
│  📊 ANALYTICS               │
│  ─────────────────────────  │
│                             │
│  [7 Days] [30 Days] [90D]  │
│                             │
│  ┌─────────────────────┐    │
│  │                     │    │
│  │  [Engagement chart  │    │
│  │   line graph]       │    │
│  │                     │    │
│  └─────────────────────┘    │
│                             │
│  Content Performance        │
│  Engagement  3.2% avg       │
│  Saves       ↑ 23%          │
│  Reach       12.4K/week     │
│                             │
│  Email Performance          │
│  Open rate   38.2%          │
│  Click rate  4.1%           │
│  Unsub rate  0.3%           │
│                             │
│  Ad Performance             │
│  CTR         2.1%           │
│  CPC         $1.42          │
│  ROAS        3.8x           │
│                             │
│  Top Performing             │
│  1. Cortisol carousel (4.2%)│
│  2. Sleep story post (3.8%) │
│  3. Mechanism explainer(3.1%)│
│                             │
│  [Ask IQ Claw to analyze →] │
└─────────────────────────────┘
```

- Time range toggle at the top
- Compact chart (sparkline or small line graph)
- Key metrics grouped by channel
- "Ask IQ Claw to analyze" button at the bottom sends a prompt to the center panel chat

## Mobile Layout (< 768px)

On mobile, the three-panel layout collapses to a single-panel view:

- **Default view:** IQ Claw chat fills the full screen
- **Sidebar:** Accessible via hamburger menu (☰) top-left, slides in as overlay
- **Right panel:** Accessible via a tab bar at the bottom of the screen:
  ```
  ┌─────┬─────┬─────┬─────┬─────┐
  │ 💬  │ 📊  │ 📄  │ 🔄  │ ⚙️  │
  │Chat │Dash │Lib  │Work │More │
  └─────┴─────┴─────┴─────┴─────┘
  ```
  - Chat (default, full screen)
  - Dashboard (the three-question dashboard)
  - Library (content library grid)
  - Workflows (workflow cards)
  - More (settings, profile, analytics)
- Each tab replaces the full screen content. The chat input bar remains fixed at the bottom of the Chat tab.

## Empty States (There Are None)

**IQ Claw never shows an empty state.** Every screen, every panel, every view has something in it:

- New chat? IQ Claw speaks first with context about what's happening.
- Empty content library? IQ Claw says "Your first content batch is being generated. I'll have it ready within the hour."
- Empty analytics? IQ Claw says "Nothing to report yet — your first posts go live Monday. I'll have performance data by Wednesday."
- Empty workflow history? The workflow cards are always visible with [Start →] buttons.

## Notification Indicators

- The sidebar module icons show small notification badges (red dot with number) when items need attention:
  - Content: "3" (3 items pending review)
  - Ads: "1" (1 alert)
  - Email: "2" (2 sequences need refresh)
- IQ Claw's avatar in the sidebar shows a subtle pulse animation when it has something proactive to share

## Keyboard Shortcuts (Desktop)

- `/` — Focus the chat input
- `Cmd+K` or `Ctrl+K` — Quick search across all conversations and content
- `Cmd+N` or `Ctrl+N` — New chat
- `Esc` — Close right panel overlay / return to dashboard default

## What NOT To Build

- No traditional dashboard with 12 metric widgets as the landing page
- No separate "Builder" pages for each content type — everything routes through IQ Claw
- No drag-and-drop visual builders (V1 — content is generated, not manually designed)
- No complex settings pages with dozens of toggles
- No onboarding tutorials or feature tours — the interface is self-evident through the conversation
- No empty states. Ever. IQ Claw always has something to say.

## The Whole Interface In One Sentence

A dark-themed three-panel AI workspace where the left sidebar holds chat history and module shortcuts, the center panel is an always-active IQ Claw conversation that opens with a contextual morning briefing and handles everything through natural language, and the right panel is a chameleon dashboard that shifts between status overview, content library, workflow launcher, and analytics depending on what the expert is doing — all of it designed so the expert never has to learn the platform, they just talk to their chief of staff.
