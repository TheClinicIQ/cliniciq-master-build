# Cleanup & Optimization Prompt
## Paste this into the MagicPath chat for the workspace component

---

Fix these redundancies and optimize the layout:

## 1. CLOSE THE BUILDERS FLYOUT
The Builders flyout panel (the large panel showing all 10 builders + Quick Launch) should NOT be permanently open. It should be shown as CLOSED/HIDDEN in the default state. The default view should show the clean narrow sidebar rail with the chat and right panel fully visible without any overlay.

Show the sidebar in its default collapsed state — just the icon rail, no flyout open. The flyout only appears on hover/click interaction, which we can't show in a static design. Show the clean state.

## 2. REDUCE RIGHT PANEL TABS FROM 10 TO 6
Remove these tabs from the right panel (they're redundant with the left sidebar):
- Remove "⚡ Builders" — already in left sidebar flyout, that's the primary access point
- Remove "⚙️ Settings" — already in left sidebar bottom, doesn't need to be a tab
- Remove "📖 Training" — move into "More" on the left sidebar
- Remove "🔌 Services" — merge with "📡 Channels" into one "Connections" tab

New right panel tab bar (6 tabs, no scrolling needed):
**🏠 Home | 🧬 My Brand | 📋 Strategy | 📁 Content | 📅 Calendar | 📡 Connections**

"Connections" combines Channels (IG, FB, YouTube) + Services (GHL, Zoom, Stripe, Slack) in one tab with two sections.

## 3. DIFFERENTIATE LEFT SIDEBAR VS RIGHT PANEL
The left sidebar flyouts are QUICK PEEKS — summary views with links to "see more."
The right panel tabs are FULL VIEWS — the complete detailed version.

This means:
- Left sidebar "Brand" flyout = compact summary of Voice DNA + Avatars + Offers with [View Full →] links
- Right panel "My Brand" tab = the full detailed view with all sections, edit buttons, and selections
- Left sidebar "Analytics" flyout = 5 key metrics at a glance
- Right panel has no separate Analytics tab — analytics lives in the Home dashboard and the full analytics view opens when you click [Full Analysis →] from the left flyout or from the dashboard

## 4. FIX THE LEFT SIDEBAR ITEMS
The left sidebar icon rail should have exactly these items (top to bottom):

**Top:**
- IQ logo mark
- [+] New (creates new chat)

**Middle navigation:**
- 🏠 Home — no flyout, just selects Home tab on right panel
- 💬 Chat — flyout shows recent conversation history (last 5-8 chats with timestamps)
- ⚡ Builders — flyout shows 3x4 grid of 10 builders + Quick Launch row
- 🧬 Brand — flyout shows compact Voice DNA, Avatars, Offers, Mechanism summary
- 📋 Strategy — flyout shows Brand North Star summary, Monthly Plan status, top 3 insights
- 📁 Content — flyout shows "156 assets | 3 pending review" + 4 recent thumbnails. Badge shows "3"
- 📊 Analytics — flyout shows 5 key metrics with trend arrows
- ••• More — flyout shows: Channels, Services, Training, Calendar as a compact list

**Bottom (pinned):**
- ⚙️ Settings gear icon
- 👤 SC avatar circle (profile)

## 5. MAKE THE CHAT PANEL THE RIGHT WIDTH
With the flyout closed, the three-panel proportions should be:
- Left sidebar rail: 72px
- Center chat: approximately 55% of remaining space
- Right panel: approximately 45% of remaining space

The chat should feel like the primary workspace. The right panel should feel substantial but not equal — it's a support panel, not a co-equal workspace. The chat is where the action happens.

## 6. SHOW THE "HOME" TAB ACTIVE ON THE RIGHT PANEL
The right panel should show the Home tab selected with this content:

**⚠️ NEEDS ATTENTION**
- Ad Set B fatiguing — -40% CTR (red) — [Fix Now →]
- Email open rates declining — 22% → 16% (amber) — [Review →]

**✅ WHAT'S WORKING**
- Cortisol carousel — 4.2% engagement, 2x average (green bar)
- Welcome sequence — 42% open rate (green)

**📈 QUICK METRICS**
Engagement: 14.2K ↑12%
Saves: 892 ↑23%
Email opens: 16.2% ↓4%
Ad spend: $45/day
New leads: 8 this week

**📅 COMING UP**
Mon: 2 posts | Tue: 1 post | Wed: 2 posts + email | Thu: Webinar | Fri: 1 post

## SUMMARY OF CHANGES:
1. Flyout closed — show clean default state
2. Right panel: 6 tabs (Home, My Brand, Strategy, Content, Calendar, Connections)
3. Left sidebar: clean icon rail with 8 nav items + Settings + Profile
4. Chat panel is primary (55%), right panel is support (45%)
5. No duplicate access points for the same content — left = quick peek, right = full view
6. Home tab active on right panel showing the dashboard
