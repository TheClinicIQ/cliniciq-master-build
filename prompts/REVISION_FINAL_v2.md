# FINAL Revision — Workspace Redesign
## Paste this into MagicPath. Start fresh, do not carry over previous versions.

---

Rebuild this component completely from scratch.

## LAYOUT
Three panels: Left sidebar (72px) + Center chat + Right panel. A draggable resize handle between the center chat and right panel so the user can drag the chat wider or narrower. Default split: chat ~45%, right panel ~55% of remaining space after sidebar.

Light theme. White background. Light gray (#F8F9FA) for sidebar and right panel. Teal accent (#00D4AA).

---

## LEFT SIDEBAR — Exactly 72px wide. Replicate Genspark's sidebar exactly.

Light gray background (#F8F9FA). Teal accent line at the very top edge. All items center-aligned vertically. Each item: outlined icon (24px) centered with a small label (10px, dark gray) beneath it. Equal vertical spacing between items.

### Items, top to bottom, in this EXACT order:

1. **Brand logo** — A rounded dark square (~36px) containing a sparkle/star icon pattern (like Genspark's logo but for ClinicIQ). No label beneath it.

2. **+ New** — A thin "+" plus icon. Label: "New"

3. **Home** — House outline icon with small circle detail at top. Label: "Home"

4. **IQ** — A planet with an orbital ring icon (circle with diagonal elliptical ring around it — same icon style as Genspark's "Claw"). Label: "IQ". **THIS IS THE ACTIVE/SELECTED ITEM** — show it with a white circular background highlight behind the icon to indicate it's selected.

5. **Workflows** — A workflow/org-chart icon (diamond hub with connected branching dots). Label: "Workflows"

6. **Teams** — Two people outlines side by side. Label: "Teams"

7. **Drive** — Folder icon with a small screen/window element on it. Label: "Drive"

8. **More** — Three horizontal dots (•••). Label: "More"

**That's it. 8 items total. Nothing else on the sidebar. No Settings gear. No profile avatar. No Analytics. No Brand. No Strategy. No Content. None of that — all of that goes on the right panel.**

Active item styling: "IQ" has a white circle background behind its icon. All other icons are gray outline (#6B7280). Hover: icon turns slightly darker.

---

## CENTER PANEL — IQ Claw Chat (narrower than before, resizable)

A vertical resize/drag handle on the right edge of the chat panel — a thin line or subtle dots that the user can grab to drag the panel wider or narrower. Default width: ~45% of the space after the sidebar.

### Top Bar
Left: Teal IQ avatar circle + "IQ Claw" bold + green dot + "Online" in green text.
Right: Gray pill "📁 Content batch Apr Wk 2" + three-dot menu (•••).
Bottom border: #E5E7EB.

### Chat Messages

**Message 1 — IQ Claw:**
Light gray bubble (#F3F4F6), dark text (#1F2937).

"Morning, Dr. Sarah.

🔴 **One thing needs your eye** — your Meta ad set B is fatiguing. CTR dropped 40% over the last three days. I already have 2 replacement hooks ready.

🟢 **Good news** — your cortisol carousel hit 4.2% engagement this week. That's double your average. I've queued 3 more in the same format.

📋 **5 posts for next week** ready to review. 3 are solid, 2 need your eye on the hooks.

Where do you want to start?"

Three teal-outlined pill buttons below:
[Fix the ad hooks] [Review content] [Show me analytics]

**Message 2 — IQ Claw:**
"Post 1 of 5. Instagram authority piece targeting the 'Stressed Mom Sarah' persona. PAS framework. I used your 'your body is telling you exactly what's wrong' line as the opener because it hit 2x saves last month. Take a look."

**Instagram preview card:**
White card, subtle border, 12px rounded corners.
- Header: "SC" avatar + "dr.sarahchen"
- Image: lifestyle photo placeholder with teal italic overlay: "Your body is telling you exactly what's wrong."
- Caption preview: "Are you feeling constantly drained despite doing 'all the right things'?..."
- Tags: "Persona: Stressed Mom" | "Framework: PAS" | "Scheduled: Thu 10am"
- Buttons: [✅ Approve] [✏️ Tweak] [🗑️ Veto]

### Input Bar (bottom, fixed)
Rounded white card (24px radius), subtle border:
"Message IQ Claw..." placeholder + 🎙️ mic icon + teal send ➤ button.
Helper text below: "IQ Claw can analyze patterns across all your active channels in real-time."

---

## RIGHT PANEL — The Full Platform Lives Here

Light gray background (#F8F9FA). Subtle left border. This panel contains EVERYTHING that isn't the chat or the Genspark-style sidebar. All platform features, all views, all tools — they live here as tabs.

### Tab Bar — Horizontal, single row across the top of the right panel

**🏠 Dashboard | 🧬 Brand | 📋 Strategy | ⚡ Builders | 📁 Content | 📅 Calendar | 📡 Channels | 🔌 Services | 📖 Training | ⚙️ Settings**

10 tabs. If they don't fit, make the tab bar horizontally scrollable with subtle scroll indicators (left/right arrows) at the edges. Active tab: teal text + bottom underline. Inactive: gray text.

**"Dashboard" is the active tab by default.**

### 🏠 DASHBOARD TAB (active — show this content)

**⚠️ NEEDS ATTENTION**
Card: "Ad Set B fatiguing" — "-40% CTR" in red — "Fix Now →" teal link
Card: "Email open rates" — "22% → 16%" in amber — "Review →" teal link

**✅ WHAT'S WORKING**
Card: "Cortisol carousel" — green bar — "4.2% engagement, 2x average"
Card: "Welcome sequence" — "42% Open" green — "Exceeding benchmark"

**📈 QUICK METRICS**
Engagement: 14.2K ↑12% (green)
Saves: 892 ↑23% (green)
Email opens: 16.2% ↓4% (red)
Ad spend: $45/day
New leads: 8 this week

**📅 THIS WEEK**
Mon: 📝 2 posts | Tue: 📝 1 post | Wed: 📝 2 posts + ✉️ email | Thu: 🎥 Webinar | Fri: 📝 1 post

### 🧬 BRAND TAB
Voice DNA card (✅ Locked): tone, signature phrases, banned words, [Edit →]
Avatars: 2 persona cards (Stressed Mom Sarah — selected, Weekend Warrior Mike) with [Select] [Edit →]
Offers: Entry ($0), Core ($4,800), Premium ($12,000) with transformation descriptions and [Edit →]
Mechanism: "The Signal Reset Protocol" + One Big Domino + [Edit →]
Proof Bank: Score 62/100, story count, testimonial count, [Add Proof →]
Brand Assets: Logo preview, color swatches, font, [Edit →]

### 📋 STRATEGY TAB
Brand North Star: positioning + always/never rules + [View →]
Monthly Master Plan: "April 2026 — Hormone Reset" + status + [View →] [Refresh →]
Active Messaging Briefs: 2 brief cards with asset counts
Performance Insights: 3 bullet points from Layer 4 + [Full Analysis →]

### ⚡ BUILDERS TAB
Header: "Choose a builder or tell IQ Claw what you need"
2-column grid of 10 builder cards, each with emoji icon + name + one-line description + [Start →]:
📝 Content Builder | 🔗 Funnel Builder | 🎥 Webinar Builder | ✉️ Email Builder | 📢 Ad Creative | 🧲 Lead Magnet | 🎓 Program Builder | 🎙️ Podcast Builder | 📞 Sales Scripts | 🌐 Website Builder

Quick Launch row at top: [📝 Content Batch] [🚀 Launch Campaign] [📊 Monthly Refresh]

### 📁 CONTENT TAB
Filter pills: [All] [Posts] [Carousels] [Reels] [Emails] [Ads] [Lead Magnets]
Sort: "Newest ▾"
2-column thumbnail grid with status badges (✅ Published, 🕐 Scheduled, 📝 Draft, 📋 Review)
"Showing 24 of 156 assets" + [Load More]

### 📅 CALENDAR TAB
Week/Month toggle
Weekly grid: Mon-Sun with colored content cards placed on days
Summary: "5 posts | 1 story | 1 email | 1 webinar this week"

### 📡 CHANNELS TAB
Platform cards: Instagram ✅, Facebook ✅, YouTube ⚪, TikTok ⚪, LinkedIn ⚪
Each with connection status, follower count, engagement rate, [Connect →] or ⚙️

### 🔌 SERVICES TAB
Integration cards: GoHighLevel ✅, Zoom ✅, Stripe ✅, Mailchimp ✅, Slack ⚪, Calendly ⚪, Zapier ⚪, Google Analytics ⚪, Meta Business ✅
Each with connection status, brief description, [Connect →] or ⚙️

### 📖 TRAINING TAB
"Platform Mastery — 35% complete" progress bar
Checklist: ✅ Complete onboarding, ✅ Review first batch, 🔲 Connect Instagram, 🔲 Launch campaign, 🔲 Review analytics
Quick Tips: 3 tip cards

### ⚙️ SETTINGS TAB
Account: Name, email, plan
Brand: Voice DNA status, colors, logo
Integrations: quick links
Billing: plan, usage

---

## DESIGN FEEL

Premium. Clean. Minimal sidebar like Genspark. The chat is the conversation with your chief of staff. The right panel is your entire business command center. The sidebar is just navigation — nothing more. Think: Genspark's simplicity on the left, Bloomberg's depth on the right, and a brilliant chief of staff in the middle.
