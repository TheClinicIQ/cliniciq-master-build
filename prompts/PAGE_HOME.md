# ClinicIQ — Home Page
## New component in MagicPath

---

Design the Home page for ClinicIQ — this is the landing page the expert sees when they click "Home" on the left sidebar. It's the command center overview of their entire business at a glance.

## LAYOUT

Same left sidebar rail (72px) as the workspace component — same 8 items, same styling, same order. But now "Home" is the ACTIVE item (white circle highlight behind the house icon), not "IQ".

The rest of the screen (after the 72px sidebar) is a single full-width content area — NO chat panel, NO right panel split. This is a full-page dashboard. Light background (#F8F9FA).

## TOP SECTION — Greeting Bar

Full-width white card at the top with subtle bottom border:

Left side:
- "Good evening, Dr. Sarah" — large bold text (24px)
- "Tuesday, April 7, 2026" — gray text below

Right side:
- A teal pill button: [💬 Open IQ Claw] — clicking this navigates to the IQ chat workspace
- Next to it: a subtle gray pill showing "IQ Score: 72/100" with a small teal circular progress indicator

## MAIN CONTENT — Two-column layout below the greeting

Left column (~60% width) | Right column (~40% width)

---

### LEFT COLUMN

**Section 1: 🔥 Needs Your Attention**
White card, subtle border, rounded corners.

3 alert rows stacked vertically:

Row 1: 🔴 red dot + "Ad Set B fatiguing — CTR dropped 40% in 3 days" + [Fix Now →] teal link on right
Row 2: 🟡 amber dot + "Email open rates declining — 22% → 16% over 2 weeks" + [Review →] on right
Row 3: 📋 blue dot + "3 content items pending your review" + [Review Content →] on right

**Section 2: 📊 Performance Overview**
White card. Header: "This Week vs. Last Week" with a [7D | 30D | 90D] toggle on the right.

A row of 4 metric cards side by side:

| Engagement | Saves | Email Opens | New Leads |
|------------|-------|-------------|-----------|
| **14.2K** | **892** | **16.2%** | **8** |
| ↑ 12% (green) | ↑ 23% (green) | ↓ 4% (red) | ↑ 33% (green) |

Below the metric cards: a simple line chart showing engagement trend over the last 7 days. Teal line on a clean white grid. X-axis: Mon-Sun. Y-axis: engagement count. The chart should look like a real data visualization — not a placeholder box.

**Section 3: 📅 This Week's Schedule**
White card. Header: "Content Calendar" with [View Full Calendar →] teal link on right.

Horizontal week view — 7 columns (Mon through Sun), compact:

Mon: Two small teal cards stacked — "📝 Post 10am" "📝 Post 2pm"
Tue: One teal card — "📝 Post 10am"
Wed: Two teal + one purple — "📝 Post" "📝 Story" "✉️ Email"
Thu: One orange card — "🎥 Webinar 2pm"
Fri: One teal card — "📝 Post 10am"
Sat: Empty (light gray dash)
Sun: Empty (light gray dash)

Below: "5 posts · 1 story · 1 email · 1 webinar scheduled this week"

**Section 4: 🚀 Recent Activity**
White card. Header: "Activity Feed" with [View All →] on right.

A timeline/feed of recent events, newest first. Each entry: small icon + description + timestamp on right.

- 📝 "IQ Claw generated 5 posts for April Week 2" — 2 hours ago
- ✅ "You approved 3 posts for this week" — 5 hours ago
- 📊 "Weekly performance report delivered" — Yesterday
- ✉️ "Welcome email sequence updated with new hook" — Yesterday
- 🔴 "Ad Set B flagged for creative fatigue" — Yesterday

Each row: subtle bottom border, compact spacing (32px row height).

---

### RIGHT COLUMN

**Section 1: 🧬 Brand Health**
White card. Header: "Your Brand" with [View Full Profile →] teal link.

Compact status list:

- Voice DNA — ✅ Locked — teal checkmark
- Avatars — 2 active — "Stressed Mom Sarah, Weekend Warrior Mike"
- Mechanism — ✅ Named — "The Signal Reset Protocol"
- Offers — 3 tiers — Entry / Core / Premium
- Proof Bank — 62/100 — amber progress bar — "Add more stories to strengthen"

**Section 2: ✅ What's Working**
White card. Header: "Top Performers"

3 compact cards stacked:

Card 1: 🥇 "Cortisol carousel" — 4.2% engagement — "2x your average" — small green sparkline chart
Card 2: 🥈 "Sleep story post" — 3.8% engagement — small green sparkline
Card 3: 🥉 "Mechanism explainer" — 3.1% engagement — small green sparkline

**Section 3: 💡 IQ Claw Suggestions**
White card. Header: "Recommendations" with a teal IQ avatar icon.

3 suggestion rows:

- "Your cortisol content outperforms everything by 2.3x — I'd double down on that angle this month." [Apply →]
- "Tuesday posts beat Thursday by 30%. Want me to shift your posting schedule?" [Apply →]
- "Your proof bank is below 70. Adding 2 more patient stories would unlock stronger ad copy." [Add Stories →]

Each suggestion: light teal left border (4px), white background, subtle padding. The [Apply →] links are teal.

**Section 4: ⚡ Quick Actions**
White card. A 2x2 grid of action buttons:

[📝 Create Content] [🎥 Build Webinar]
[✉️ Write Emails] [📊 Run Analysis]

Each button: white card with subtle border, icon on top (24px), bold label below. Teal hover state. Clicking any of these opens IQ Claw chat pre-seeded with that task.

---

## BOTTOM BAR (subtle, full width)

A thin bar at the very bottom:
Left: "ClinicIQ Pro Plan" in gray text
Center: "Last sync: 2 minutes ago" with a green dot
Right: "Help & Support" link + "⌘K Quick Search" hint text

---

## DESIGN NOTES

- This page should feel like a CEO dashboard — the expert opens it and in 10 seconds knows: what needs attention, what's working, what's coming this week, and what IQ Claw recommends.
- Every card is white on the #F8F9FA background. Clean separation. No visual clutter.
- The greeting is personal and warm. The data is specific and actionable.
- Every section has a "go deeper" link that either opens IQ Claw chat or navigates to the relevant right-panel tab on the IQ workspace page.
- The left column is the operational view (what's happening). The right column is the strategic view (brand health, top performers, recommendations, quick actions).
- Teal accent color throughout for interactive elements. Red for alerts. Green for positive. Amber for warnings.
- The line chart should look realistic — not a flat placeholder. Show actual-looking data points with a smooth curve.
