# ClinicIQ — "More" Flyout — Complete Build Spec for Claude Code
## Build the full More menu: every item functional, premium, billion-dollar feel

---

## WHAT THIS IS

The "More" flyout is the overflow menu that opens when the expert clicks the MoreHorizontal (•••) icon labeled "More" in the left sidebar. It contains everything important that doesn't need its own sidebar slot: inbox, notifications, integrations, analytics, help, account settings, and platform utilities.

The current version is a skeleton — Inbox, Hub, Dark Mode, Help, Download App, and a profile card. This prompt rebuilds it completely with every item functional.

---

## FLYOUT PANEL — Container Styling

- **Trigger:** Click the "More" item on the sidebar (MoreHorizontal icon + "More" label)
- **Position:** Anchored to the right edge of the sidebar rail, vertically aligned with the "More" button. Flyout extends to the right, overlaying the left edge of the center chat panel.
- **Width:** 340px
- **Max height:** 80vh (scrollable if content overflows, but it shouldn't with this design)
- **Background:** White (#FFFFFF)
- **Border:** 1px #E5E7EB
- **Border-radius:** 16px
- **Shadow:** 0 8px 32px rgba(0,0,0,0.12)
- **Close behavior:** Click outside the flyout, or click the "More" button again, or press Escape. Flyout slides out with a 200ms ease transition.
- **Open animation:** Fade in + slide right from the sidebar edge, 200ms ease.

---

## FLYOUT CONTENT — Top to Bottom

### SECTION 1: COMMUNICATION (top)

**Header:** None — these are the primary items, they don't need a label.

**Item 1: Inbox**
- Icon: Mail icon (Lucide `Mail`, 20px, #374151)
- Label: "Inbox" (14px, #1F2937)
- Right side: notification badge — small rounded-full pill (18px height, min-width 18px, emerald #10B981 bg, white text, bold, 11px). Shows unread count: "3". Hidden when count is 0.
- Click → navigates to `/inbox` (a full-page inbox view)
- **What the inbox contains:** Messages from IQ Claw (engine completions, content ready for review, performance alerts, weekly digests), team notifications (if Teams is set up), and system notifications (integration disconnects, billing alerts). This is the platform's notification center — not email.

**Item 2: Notifications**
- Icon: Bell icon (Lucide `Bell`, 20px, #374151)
- Label: "Notifications" (14px, #1F2937)
- Right side: red (#EF4444) dot (8px) when unread notifications exist. No dot when clear.
- Click → opens a **notification dropdown** inline inside the flyout (replaces the flyout content temporarily):

```
┌─────────────────────────────────────────┐
│  [← Back]          Notifications        │
│  ─────────────────────────────────────  │
│                                         │
│  🟢 Content batch complete              │
│     8 posts ready for review    2m ago  │
│                                         │
│  🟡 Ad Set B fatigue warning            │
│     CTR dropped 40%           15m ago   │
│                                         │
│  🟢 Welcome sequence sent               │
│     23 new leads received      1h ago   │
│                                         │
│  ⚪ Weekly digest ready                  │
│     April 1–7 performance      3h ago   │
│                                         │
│  ⚪ Engine scheduled                     │
│     Monthly Content runs Apr 25 1d ago  │
│                                         │
│           [View all notifications →]    │
└─────────────────────────────────────────┘
```

- Each notification: colored dot (8px, left — emerald for positive, amber for warning, gray for info) + title (13px, bold, #1F2937) + subtitle (12px, #6B7280) + timestamp (11px, #9CA3AF, right-aligned)
- Unread notifications: white bg. Read: #FAFBFC bg.
- Row height: 52px. Hover: #F3F4F6.
- Click a notification → navigates to the relevant page/section.
- [← Back] returns to the main More flyout.
- Max 5 shown. [View all notifications →] links to `/inbox`.

---

### DIVIDER (1px, #E5E7EB, 8px margin top/bottom)

---

### SECTION 2: PLATFORM TOOLS

**Header:** "PLATFORM" (10px, uppercase, #9CA3AF, letter-spacing 0.05em, padding 4px 16px)

**Item 3: Analytics**
- Icon: BarChart3 icon (Lucide, 20px, #374151)
- Label: "Analytics" (14px, #1F2937)
- Right side: trend indicator — "↑ 12%" in emerald (12px) with TrendingUp icon (14px) if trending positive, "↓ 8%" in red if negative
- Click → navigates to `/analytics` (full-page analytics dashboard with detailed performance breakdowns by channel: ads, funnels, social, email. Tabbed view with charts, tables, date range filters. This is the deep-dive version of what the Dashboard tab surfaces as headlines.)

**Item 4: Channels**
- Icon: Radio icon (Lucide `Radio`, 20px, #374151)
- Label: "Channels" (14px, #1F2937)
- Right side: "3 connected" (12px, #6B7280)
- Click → navigates to `/channels` (full-page channel management: connected social platforms — Instagram, Facebook, YouTube, TikTok, LinkedIn, Twitter. Each platform shows: connection status, follower count, last post date, posting schedule, [Connect] / [Disconnect] buttons. Also includes publishing settings: auto-publish vs. review-first, posting times, cross-posting rules.)

**Item 5: Services**
- Icon: Plug icon (Lucide `Plug`, 20px, #374151)
- Label: "Services" (14px, #1F2937)
- Right side: "5 active" (12px, #6B7280)
- Click → navigates to `/services` (full-page integrations hub: connected tools — GHL/GoHighLevel, Stripe, Calendly, Zoom, Mailchimp, ActiveCampaign, Slack, Zapier, Google Calendar, etc. Each integration shows: connection status with green/red dot, last sync time, data flowing (leads synced, payments tracked), [Connect] / [Configure] / [Disconnect] buttons. Grouped by category: CRM, Payments, Scheduling, Email Marketing, Communication, Calendar.)

**Item 6: Hub**
- Icon: Layout icon (Lucide `LayoutGrid`, 20px, #374151)
- Label: "Hub" (14px, #1F2937)
- Right side: ChevronRight icon (16px, #9CA3AF)
- Click → navigates to `/hub` (the ClinicIQ marketplace/resource center: featured templates, community templates shared by other practitioners, new builder capabilities, platform updates/changelog, educational content on using the platform effectively. Think: App Store meets changelog meets learning center.)

**Item 7: Training**
- Icon: GraduationCap icon (Lucide, 20px, #374151)
- Label: "Training" (14px, #1F2937)
- Right side: mini progress bar (48px wide, 4px height, emerald fill at 35%) + "35%" (12px, #6B7280)
- Click → navigates to `/training` (platform mastery system: structured learning path for getting the most out of ClinicIQ. Modules like "Master Your Voice DNA," "Build Your First Engine," "Optimize Your Funnel," "Read Your Analytics," "Advanced: Paid Traffic Scaling." Each module: progress bar, lessons with checkmarks, estimated time, completion badge. Think: mini LMS built into the platform.)

---

### DIVIDER (1px, #E5E7EB, 8px margin top/bottom)

---

### SECTION 3: PREFERENCES

**Header:** "PREFERENCES" (10px, uppercase, #9CA3AF, letter-spacing 0.05em, padding 4px 16px)

**Item 8: Appearance**
- Icon: Sun icon (Lucide `Sun`, 20px, #374151) — changes to Moon icon when dark mode is on
- Label: "Appearance" (14px, #1F2937)
- Right side: segmented toggle with 3 options: [☀️ Light] [🌙 Dark] [💻 System]
  - Active option: #1F2937 bg, white text, rounded-md
  - Inactive options: transparent bg, #6B7280 text
  - Toggle container: #F3F4F6 bg, rounded-lg, padding 2px
  - Each option: 11px text, padding 4px 8px
- Light is active by default (v1 is light mode only, but the toggle is there ready for dark mode implementation — Dark and System options show a tooltip on hover: "Coming soon")
- **Note:** For v1, only Light mode works. Dark and System are visible but disabled with a "Coming soon" tooltip. This future-proofs the UI without requiring the dark theme to be built now.

**Item 9: Notification Settings**
- Icon: BellRing icon (Lucide, 20px, #374151)
- Label: "Notification Settings" (14px, #1F2937)
- Right side: ChevronRight icon (16px, #9CA3AF)
- Click → navigates to `/settings/notifications` (notification preferences: toggle on/off for each notification type — engine completions, content ready, performance alerts, weekly digest, team activity. Channel preferences: in-app, email, SMS, push. Quiet hours setting.)

**Item 10: Language**
- Icon: Globe icon (Lucide, 20px, #374151)
- Label: "Language" (14px, #1F2937)
- Right side: "English" (12px, #6B7280) + ChevronRight
- Click → opens inline language selector (replaces flyout content like notifications):
  - [← Back] + "Language" header
  - List of languages with radio buttons: English (selected), Español, Português, Français, Deutsch, 中文, 日本語, 한국어
  - Selecting a language → confirms with a toast "Language updated" and reloads the UI
  - For v1: only English is fully supported. Others show a "Beta" badge next to them.

---

### DIVIDER (1px, #E5E7EB, 8px margin top/bottom)

---

### SECTION 4: SUPPORT & RESOURCES

**Header:** "SUPPORT" (10px, uppercase, #9CA3AF, letter-spacing 0.05em, padding 4px 16px)

**Item 11: Help & Support**
- Icon: HelpCircle icon (Lucide, 20px, #374151)
- Label: "Help & Support" (14px, #1F2937)
- Right side: ChevronRight icon (16px, #9CA3AF)
- Click → opens inline support panel (replaces flyout content):

```
┌─────────────────────────────────────────┐
│  [← Back]          Help & Support       │
│  ─────────────────────────────────────  │
│                                         │
│  ┌─────────────────────────────────┐    │
│  │  🔍 Search help articles...     │    │
│  └─────────────────────────────────┘    │
│                                         │
│  QUICK HELP                             │
│                                         │
│  📖  Getting Started Guide              │
│  🎥  Video Tutorials                    │
│  📋  FAQ                                │
│  🧬  Understanding Your IQ Score        │
│  ⚡  How Growth Engines Work            │
│                                         │
│  ─────────────────────────────────────  │
│                                         │
│  CONTACT                                │
│                                         │
│  💬  Chat with Support                  │
│      Avg response: < 5 min              │
│                                         │
│  ✉️  Email Support                      │
│      support@cliniciq.com               │
│                                         │
│  📞  Schedule a Call                    │
│      Book a 15-min strategy call        │
│                                         │
└─────────────────────────────────────────┘
```

- Search input: rounded-lg, border #E5E7EB, placeholder "Search help articles...", Search icon left
- Quick Help items: 14px, #1F2937, icon 18px left. Hover: #F3F4F6 bg. Click → opens help article in a new tab or in-app article viewer.
- Contact items: icon + title (14px, bold) + subtitle (12px, #6B7280). "Chat with Support" opens a live chat widget. "Email Support" opens mailto. "Schedule a Call" opens Calendly embed or link.

**Item 12: What's New**
- Icon: Sparkles icon (Lucide, 20px, #374151)
- Label: "What's New" (14px, #1F2937)
- Right side: "NEW" badge (tiny emerald pill, 10px text, #10B981 bg, white text) — shown when there are unread changelog entries. Hidden otherwise.
- Click → navigates to `/whats-new` (changelog / release notes page: each entry shows date, title, description, and screenshots of new features. Sorted newest first. Expert can mark all as read. Think: Notion-style changelog.)

**Item 13: Download App**
- Icon: Smartphone icon (Lucide, 20px, #374151)
- Label: "Download App" (14px, #1F2937)
- Right side: ChevronRight icon (16px, #9CA3AF)
- Click → opens inline panel:

```
┌─────────────────────────────────────────┐
│  [← Back]          Download App         │
│  ─────────────────────────────────────  │
│                                         │
│  Get ClinicIQ on your phone             │
│  (14px, #6B7280, centered)              │
│                                         │
│  ┌─────────────────────────────────┐    │
│  │  🍎  Download for iOS           │    │
│  │      App Store                   │    │
│  └─────────────────────────────────┘    │
│                                         │
│  ┌─────────────────────────────────┐    │
│  │  🤖  Download for Android       │    │
│  │      Google Play                 │    │
│  └─────────────────────────────────┘    │
│                                         │
│  ── or scan QR code ──                  │
│                                         │
│  ┌───────────┐                          │
│  │  QR CODE  │  Scan with your          │
│  │  ███████  │  phone camera            │
│  │  ███████  │                          │
│  └───────────┘                          │
│                                         │
└─────────────────────────────────────────┘
```

- Two download buttons: white bg, border #E5E7EB, rounded-xl, padding 14px 16px, full-width. Icon + platform name (14px, bold) + store name (12px, #6B7280). Hover: border emerald + subtle shadow.
- QR code: 120px × 120px placeholder (generate a real QR or show a placeholder graphic). Centered with helper text to the right.
- For v1: these can link to placeholder URLs or "#" — the app doesn't exist yet. The UI should look complete.

---

### DIVIDER (1px, #E5E7EB, 8px margin top/bottom)

---

### SECTION 5: ACCOUNT (bottom — always visible, slightly differentiated)

This section has a slightly different background (#FAFBFC) to visually separate it from the menu items above.

```
┌─────────────────────────────────────────┐
│                                         │
│  [SC]  Dr. Sarah Chen                   │
│        Pro Plan · Joined Mar 2026       │
│                                         │
│  [Manage Account]        [Sign Out]     │
│  (emerald text, 12px)   (red text, 12px)│
│                                         │
└─────────────────────────────────────────┘
```

- User avatar: 36px emerald circle (#10B981) with white initials "SC" (14px, bold)
- Name: 14px, bold, #1F2937
- Subtitle: "Pro Plan · Joined Mar 2026" (12px, #6B7280). Plan name is a link (emerald, hover underline) → `/settings/billing`
- [Manage Account] — emerald text, 12px, bold → navigates to `/settings/account`
- [Sign Out] — red (#EF4444) text, 12px → triggers sign out confirmation modal: "Sign out of ClinicIQ?" with [Cancel] and [Sign Out] buttons.
- Background: #FAFBFC, padding 16px, rounded-b-2xl (only bottom corners rounded to match flyout container).

---

## FLYOUT ITEM ROW — Standard Styling

Every item row in the flyout follows this pattern:

- Height: 44px
- Padding: 0 16px
- Layout: icon (20px, left, #374151) → 12px gap → label (14px, #1F2937) → flex-grow → right content (badge, detail text, arrow, toggle)
- Hover: background #F3F4F6, rounded-md (within 4px horizontal padding), 150ms transition
- Active/pressed: background #ECFDF5 (light emerald tint), 100ms
- Cursor: pointer
- Focus-visible: 2px emerald outline, 2px offset

---

## INLINE PANEL PATTERN

When an item opens an inline panel (Notifications, Language, Help & Support, Download App), the flyout content transitions:

- Current content slides left and fades out (200ms ease)
- New panel slides in from the right and fades in (200ms ease)
- [← Back] button in top-left of the inline panel — click returns to the main flyout with reverse animation
- The flyout container size stays the same (340px width) — no resizing
- The inline panel has the same internal padding and styling as the main flyout

---

## KEYBOARD NAVIGATION

- Arrow Up/Down to move between items
- Enter to select/activate
- Escape to close flyout (or go [← Back] if in an inline panel)
- Tab cycles through interactive elements within the flyout

---

## ROUTES CREATED BY THIS PROMPT

These routes need to exist as pages (can be placeholder/skeleton pages for v1, but the navigation must work):

| Route | Page | Minimum v1 Content |
|-------|------|-------------------|
| `/inbox` | Notification center | List of notifications grouped by date, mark as read, filter by type |
| `/analytics` | Deep analytics dashboard | Tabbed view: Ads, Funnels, Social, Email. Charts + tables with date range filter. Can use mock data. |
| `/channels` | Social channel management | Grid of platform cards (IG, FB, YT, TikTok, LinkedIn). Each: status, follower count, [Connect] button. |
| `/services` | Integration hub | Grid of service cards grouped by category. Each: logo, status dot, [Connect] / [Configure]. |
| `/hub` | Marketplace / resource center | Featured templates grid + "What's New" section + community section. Can be placeholder. |
| `/training` | Platform training / LMS | Module list with progress bars and completion badges. 5 modules minimum. |
| `/whats-new` | Changelog | 3–5 changelog entries with dates, titles, descriptions. Newest first. |
| `/settings/account` | Account settings | Name, email, password change, avatar upload, timezone, delete account |
| `/settings/billing` | Billing / plan | Current plan card, usage stats, payment method, invoice history, upgrade/downgrade |
| `/settings/notifications` | Notification preferences | Toggle grid: notification type × channel (in-app, email, SMS). Quiet hours. |

**Each page:** Same layout as all other full-width pages — sidebar rail (72px) + full-width content. "More" is NOT highlighted in the sidebar when on these pages — instead, show a back arrow or breadcrumb at the top of the content area.

---

## MOCK DATA

```typescript
const mockNotifications = [
  { id: "n1", type: "success", title: "Content batch complete", subtitle: "8 posts ready for review", time: "2m ago", read: false },
  { id: "n2", type: "warning", title: "Ad Set B fatigue warning", subtitle: "CTR dropped 40%", time: "15m ago", read: false },
  { id: "n3", type: "success", title: "Welcome sequence sent", subtitle: "23 new leads received", time: "1h ago", read: true },
  { id: "n4", type: "info", title: "Weekly digest ready", subtitle: "April 1–7 performance", time: "3h ago", read: true },
  { id: "n5", type: "info", title: "Engine scheduled", subtitle: "Monthly Content runs Apr 25", time: "1d ago", read: true },
];

const mockChannels = [
  { platform: "Instagram", handle: "@dr.sarahchen", followers: "8.2K", connected: true, lastPost: "2h ago" },
  { platform: "Facebook", handle: "Dr. Sarah Chen Health", followers: "3.1K", connected: true, lastPost: "1d ago" },
  { platform: "YouTube", handle: "Dr. Sarah Chen", subscribers: "1.2K", connected: true, lastPost: "1w ago" },
  { platform: "TikTok", handle: "@drsarahchen", followers: null, connected: false, lastPost: null },
  { platform: "LinkedIn", handle: "Dr. Sarah Chen, ND", followers: "890", connected: false, lastPost: null },
];

const mockServices = [
  { name: "GoHighLevel", category: "CRM", connected: true, lastSync: "5m ago", icon: "database" },
  { name: "Stripe", category: "Payments", connected: true, lastSync: "1h ago", icon: "credit-card" },
  { name: "Calendly", category: "Scheduling", connected: true, lastSync: "2h ago", icon: "calendar" },
  { name: "Zoom", category: "Communication", connected: true, lastSync: "1d ago", icon: "video" },
  { name: "Mailchimp", category: "Email", connected: true, lastSync: "3h ago", icon: "mail" },
  { name: "ActiveCampaign", category: "Email", connected: false, lastSync: null, icon: "mail" },
  { name: "Slack", category: "Communication", connected: false, lastSync: null, icon: "message-square" },
  { name: "Google Calendar", category: "Calendar", connected: false, lastSync: null, icon: "calendar" },
];

const mockTrainingModules = [
  { id: "t1", title: "Getting Started", description: "Platform basics and your first content", progress: 100, lessons: 5, badge: "🟢 Complete" },
  { id: "t2", title: "Master Your Voice DNA", description: "Refine your voice profile for better output", progress: 60, lessons: 4, badge: null },
  { id: "t3", title: "Build Your First Engine", description: "Launch a complete growth engine", progress: 20, lessons: 6, badge: null },
  { id: "t4", title: "Optimize Your Funnel", description: "Read metrics and improve conversion", progress: 0, lessons: 5, badge: null },
  { id: "t5", title: "Advanced: Paid Traffic", description: "Scale with paid ads the right way", progress: 0, lessons: 7, badge: "🔒 Complete Module 3 first" },
];
```

---

## DESIGN SYSTEM (matching platform)

- **Flyout bg:** White #FFFFFF, border #E5E7EB, rounded-2xl, shadow-xl
- **Section headers:** 10px, uppercase, #9CA3AF, letter-spacing 0.05em
- **Item icons:** Lucide React, 20px, #374151
- **Item labels:** 14px, #1F2937
- **Detail text:** 12px, #6B7280
- **Badges:** emerald bg for counts, red dot for unread, emerald pill for "NEW"
- **Hover states:** #F3F4F6 background, 150ms transition
- **Dividers:** 1px #E5E7EB, 8px margin vertical
- **Transitions:** All inline panel transitions 200ms ease

---

## THE PRINCIPLE

The "More" flyout is where the expert finds everything that powers the platform behind the scenes — integrations, analytics, notifications, training, help, account. It should feel like opening the control panel of a luxury car: everything is there, everything works, everything is exactly where you'd expect it. Premium, organized, zero clutter.
