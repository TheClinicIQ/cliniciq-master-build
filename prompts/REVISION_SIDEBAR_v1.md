# Revision Prompt — Left Sidebar Complete Redesign
## Paste this into the MagicPath chat

---

Completely redesign the LEFT SIDEBAR to match this specific pattern: a narrow icon rail with hover-triggered flyout panels.

## SIDEBAR RAIL — Narrow, Icon-Centric

Width: **72px** (narrow rail, NOT a full sidebar). Background: white. Subtle right border (#E5E7EB). All items are vertically stacked, center-aligned. Each item is an icon (28px) with a tiny label (10px) beneath it.

### Sidebar Items (top to bottom, center-aligned):

**Top section:**
1. **ClinicIQ logo** — Small teal "IQ" mark, no text. This is the brand icon at the very top.
2. **+ New** — A "+" icon in a teal rounded square (24x24px). Label: "New" in tiny gray text below.

**Main navigation (middle section, evenly spaced):**
3. **🏠 Home** — House outline icon. Label: "Home"
4. **💬 Chat** — Speech bubble icon. Label: "Chat". Small teal dot notification badge when IQ Claw has something to say.
5. **⚡ Builders** — Lightning bolt or grid icon. Label: "Builders"
6. **🧬 Brand** — DNA helix or fingerprint icon. Label: "Brand"
7. **📋 Strategy** — Clipboard or compass icon. Label: "Strategy"
8. **📁 Content** — Folder icon. Label: "Content". Shows red badge with "3" when items need review.
9. **📊 Analytics** — Bar chart icon. Label: "Analytics"
10. **•••  More** — Three dots icon. Label: "More"

**Bottom section (pinned to bottom):**
11. **⚙️** — Gear icon, no label. Settings.
12. **👤** — User avatar circle (teal with initials "SC"). This is the profile button.

### Icon Styling:
- All icons are outlined/stroke style, not filled. Consistent 1.5px stroke weight.
- Color: Gray (#9CA3AF) for inactive, teal (#00D4AA) for active/selected
- The currently active item has its icon in teal + a small teal indicator bar on the left edge of the rail (3px wide, rounded, same height as the icon)
- Hover state: icon turns teal, subtle light teal background circle appears behind the icon

## FLYOUT PANELS — Hover/Click Triggered

When the user hovers over (or clicks) certain sidebar items, a large flyout panel slides out to the right of the rail. The flyout overlays the chat area partially.

### Flyout Panel Styling:
- Width: **480px**
- Height: auto (content-dependent), max height 90vh with scroll
- Background: white
- Border-radius: 16px
- Shadow: large soft shadow (0 8px 32px rgba(0,0,0,0.12))
- Subtle border: #E5E7EB
- Appears anchored to the right edge of the sidebar rail, vertically aligned with the hovered item
- Smooth slide-in animation from left (200ms ease-out)
- Closes when mouse leaves the flyout area OR when user clicks elsewhere

### FLYOUT: "+ New" Button
When hovering over the "+" New button, the flyout shows:

**Header:** "Start Something New"

**Quick Actions section (horizontal row of 3 pill buttons):**
[📝 Quick Post] [✉️ Quick Email] [📢 Quick Ad]

**Recent Chats section:**
"RECENT CONVERSATIONS"
- 📝 Content batch for April Week 2 — Today
- 📊 Weekly performance review — Today
- 📋 Webinar script revisions — Yesterday
(Shows last 5 conversations with icons and dates)

### FLYOUT: ⚡ Builders
When hovering over the Builders icon, the flyout shows:

**Header:** "⚡ Builders"
**Subtitle:** "Choose a builder or just tell IQ Claw what you need"

**3-column grid of builder cards (icon + label):**

Row 1:
📝 Content Builder | 🔗 Funnel Builder | 🎥 Webinar Builder

Row 2:
✉️ Email Builder | 📢 Ad Creative | 🧲 Lead Magnet

Row 3:
🎓 Program Builder | 🎙️ Podcast Builder | 📞 Sales Scripts

Row 4:
🌐 Website Builder | | (empty cell)

Each builder: circular colored icon (48px) with label below (12px gray text). Clicking one opens a new IQ Claw chat pre-seeded with that builder context.

**Quick Launch section at bottom of flyout:**
"QUICK LAUNCH"
Three larger pill buttons:
[📝 Create Content Batch] [🚀 Launch Campaign] [📊 Monthly Refresh]

### FLYOUT: 🧬 Brand
When hovering over the Brand icon, the flyout shows:

**Header:** "🧬 Your Brand Foundation"

**Compact overview cards:**

Voice DNA — ✅ Locked
"Direct, systems-thinker, signal-based language"
[View / Edit →]

Avatars — 2 active
"Stressed Mom Sarah" (selected) | "Weekend Warrior Mike"
[Manage Avatars →]

Offers — 3 tiers
Entry: Free Assessment | Core: $4,800 | Premium: $12,000
[Edit Offers →]

Mechanism — ✅ Named
"The Signal Reset Protocol"
[View / Edit →]

Proof Bank — Score: 62/100
3 stories | 2 videos | 12 testimonials
[Add Proof →]

### FLYOUT: 📋 Strategy
When hovering over the Strategy icon, the flyout shows:

**Header:** "📋 Growth Strategy"

Brand North Star — ✅ Active
"The hormone doctor who finds what everyone else missed"
[View →]

Monthly Master Plan — April 2026
"Hormone Reset Campaign — Cortisol focus"
🟢 On track | 68% through month
[View Plan →] [Refresh →]

Performance Insights:
"• Cortisol content outperforms by 2.3x — lean in"
"• Tuesday > Thursday by 30% — shift schedule"
"• Story hooks convert 40% better for your audience"
[Full Analysis →]

### FLYOUT: 📁 Content
When hovering over the Content icon, the flyout shows:

**Header:** "📁 Content Library"
**Stats line:** "156 total assets | 3 pending review | 12 scheduled"

Filter row: [All] [Posts] [Carousels] [Emails] [Ads]

Grid of 6 content thumbnails (3x2) with status badges and dates.

[View Full Library →] button at bottom

### FLYOUT: 📊 Analytics
When hovering over the Analytics icon, the flyout shows:

**Header:** "📊 Performance Overview"
**Time range:** [7D] [30D] [90D] toggle

Quick metrics in a compact grid:
Engagement: 14.2K ↑12%
Saves: 892 ↑23%
Email opens: 16.2% ↓4%
Ad spend: $45/day
ROAS: 3.8x
New leads: 8 this week

Top performing: "Cortisol carousel — 4.2% engagement"

[Open Full Analytics →]

### FLYOUT: ••• More
When hovering over the More icon, the flyout shows:

**Compact list:**
📡 Channels — Connected platforms (IG, FB, Meta Ads, GHL)
🔌 Services — Integrations (Zoom, Slack, Stripe, Calendly)
📖 Training — Platform mastery (35% complete)
📅 Calendar — Content schedule

Each with a one-line summary and [Open →] link.

## IMPORTANT DESIGN NOTES:

1. **Show the Builders flyout as open in the design** — this is the most visually impressive state and demonstrates the pattern.

2. **The sidebar rail replaces the entire current left sidebar.** No more 240px wide sidebar with full text lists. This is an icon rail + flyout system.

3. **Chat history moves INTO the Chat flyout or the "+ New" flyout** — it no longer lives permanently visible in the sidebar. When the user hovers on the Chat icon or the + New icon, they see their recent conversations.

4. **The chat panel should expand to fill the space** the old wide sidebar freed up. New proportions: 72px sidebar rail | ~55% center chat | ~45% right panel.

5. The flyout panels give the user FULL access to everything without cluttering the always-visible interface. The default state is clean and minimal — just the icon rail.

6. On mobile: the sidebar rail becomes a bottom tab bar with 5 key items (Home, Chat, Builders, Content, More). Flyouts become full-screen overlays.
