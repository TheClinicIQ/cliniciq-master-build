# ClinicIQ — Dashboard Tab Redesign
## Rebuild the right-panel Dashboard tab to feel like a billion-dollar CEO command center

---

## CONTEXT

The Dashboard tab lives in the right panel of the IQ workspace — next to the center chat. It is NOT the full-screen Home page. It's the **compact, glanceable command center** the expert sees while they're working with IQ Claw. It needs to answer one question instantly: **"How's my business doing right now, and what needs my attention?"**

The current version has the right bones but needs to be tightened. Too much scroll depth, some sections are redundant, and the hierarchy doesn't lead the eye to what matters most.

---

## WHAT'S WRONG WITH THE CURRENT VERSION

1. **Greeting and date** at the top waste prime real estate — the expert already sees IQ's greeting in the chat. Don't repeat it here.
2. **Four score cards across the top** compete for attention equally — but they shouldn't. The expert needs one overall number, not four.
3. **"Overall Health Score" donut** is buried in the second row — it should be the very first thing they see.
4. **"Needs Your Attention"** is excellent but the alerts lack severity weight — a fatiguing ad set and 5 posts awaiting approval shouldn't look the same.
5. **"Recommendations"** and **"What's Working"** are good but take too much vertical space for what they show.
6. **"Performance by Category"** with tabbed detail metrics is too deep for the right panel — that's Home page depth. The right panel should surface the headline, not the table.
7. **"Activity Feed"** is filler. If IQ is narrating in the chat, the activity feed is redundant.
8. **No engines/workflow status** — the expert should see their active growth engines at a glance.
9. **No upcoming calendar** — what's publishing today/this week should be visible.

---

## THE REDESIGN — Top to Bottom

The Dashboard tab scrolls vertically inside the right panel. Every section earns its space by being immediately actionable or immediately informative. No filler. No redundancy with the chat.

---

### SECTION 1: IQ SCORE (Hero — top of panel, always visible)

The single most prominent element on the Dashboard. This is the expert's overall platform health score — a composite of all category scores.

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│              ┌─────────┐                            │
│              │         │                            │
│              │   71    │    IQ Score                │
│              │  /100   │    +3 from last week       │
│              │         │                            │
│              └─────────┘                            │
│              (circular gauge)                       │
│                                                     │
│   Ad 64  ·  Funnel 78  ·  Social 82  ·  Email 58  │
│   (🔴)      (🟢)         (🟢)          (🟡)        │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Circular gauge: 80px diameter, thick stroke (8px). Color matches score: emerald (80+), amber (60–79), red (<60). This one shows amber at 71.
- Score number: 32px, bold, #1F2937, centered inside the gauge
- "/100" below number: 14px, #6B7280
- "IQ Score" right of gauge: 18px, bold, #1F2937
- "+3 from last week" below: 13px, emerald text with TrendingUp icon (if positive), red with TrendingDown (if negative)
- Category scores below: horizontal row, 12px each, #6B7280 text. Colored dot (6px) next to each: emerald (75+), amber (50–74), red (<50)
- Clicking any category score → switches to the relevant tab (clicking "Email 58" → switches to Dashboard tab but scrolls down to the detail section, or navigates to a future Analytics view)
- Card: no card border — this bleeds to the edges of the right panel. White bg, 24px padding top/bottom. 1px #E5E7EB bottom border as divider.

---

### SECTION 2: NEEDS ATTENTION (Action items — sorted by severity)

The most operationally critical section. What needs the expert to do something RIGHT NOW.

```
┌─────────────────────────────────────────────────────┐
│  ⚠️ NEEDS ATTENTION                          3 items│
│  ─────────────────────────────────────────────────  │
│                                                     │
│  🔴  Ad Set B fatiguing — CTR down 40%              │
│      Creative has been running 14 days              │
│                                    [Fix Now →]      │
│                                                     │
│  🟡  Email open rates declining (22% → 16%)         │
│      Welcome sequence underperforming               │
│                                    [Review →]       │
│                                                     │
│  ⚪  5 posts awaiting your approval                  │
│      From last week's content batch                 │
│                                 [Review Content →]  │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Header: "NEEDS ATTENTION" (11px, uppercase, #6B7280, letter-spacing 0.05em) + item count badge
- Items sorted by severity: 🔴 Critical (red left border 4px, red dot) → 🟡 Warning (amber left border, amber dot) → ⚪ Info (gray left border, gray dot)
- Each item: left colored dot (8px) + title (14px, bold, #1F2937) + subtitle (12px, #6B7280) + action link (13px, emerald, bold, right-aligned)
- Each item is a compact row — 56px height, padding 10px 16px
- Items are mini cards with subtle border (#F3F4F6 bg), rounded-lg, 6px gap between items
- Clicking the action link → tells IQ Claw to handle it (pre-fills chat: "Fix the Ad Set B fatigue issue")
- When zero items need attention: section collapses to a single line: "✅ All clear — nothing needs your attention" (emerald text, 13px)
- Max 5 items shown. If more: "View 3 more →" link at bottom.

---

### SECTION 3: ACTIVE ENGINES (What's running / what's live)

Quick status of the expert's growth engines — the systems doing the real work.

```
┌─────────────────────────────────────────────────────┐
│  ⚡ ACTIVE ENGINES                                   │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  🎥 Evergreen Webinar Funnel         🟢 Active     │
│     Opt-in 38% 🟢  Show 22% 🟡  Convert 9% 🟢     │
│                                                     │
│  📅 Monthly Content — April           🔵 Running    │
│     Step 2 of 4 · ████████░░ 42%                   │
│                                                     │
│  🧲 Lead Magnet Funnel              🟡 Review      │
│     30 assets ready for approval                    │
│                                                     │
│                            [View all engines →]     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Header: "ACTIVE ENGINES" (11px, uppercase, #6B7280) + Zap icon (14px, #6B7280)
- Each engine: one row, 48px height
  - Left: engine emoji (16px) + engine name (13px, bold, #1F2937)
  - Right: status badge (tiny pill — same color scheme as engines page)
  - Below name: compact metrics (running engines show progress bar, active engines show key metric chips, review engines show "X assets ready")
- Max 3 engines shown. [View all engines →] links to /engines.
- If zero engines: "No active engines yet. [Browse Engine Library →]" — links to /engines Engine Library tab
- Clicking an engine name → navigates to /engines/[id] detail page

---

### SECTION 4: THIS WEEK (Calendar glance — what's publishing)

What's going out this week. Gives the expert a sense of momentum — the platform is working even when they're not.

```
┌─────────────────────────────────────────────────────┐
│  📅 THIS WEEK                          Apr 7–13    │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  Today                                              │
│  · 📝 Instagram Reel — Cortisol tips        9:00 AM│
│  · ✉️ Weekly broadcast email               11:00 AM│
│                                                     │
│  Tomorrow                                           │
│  · 📝 Carousel — Sleep & hormones          9:00 AM │
│  · 📢 Ad Set A creative refresh             Auto   │
│                                                     │
│  Thursday                                           │
│  · 📝 Story — Client transformation        10:00 AM│
│  · 🎥 Webinar replay email                  2:00 PM│
│                                                     │
│                            [View full calendar →]   │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Header: "THIS WEEK" (11px, uppercase, #6B7280) + Calendar icon + date range (12px, #9CA3AF)
- Grouped by day: day label (13px, bold, #1F2937) then items below
- Each item: builder emoji (14px) + description (12px, #374151) + time (12px, #9CA3AF, right-aligned)
- Today's items: slight emerald left border (2px) to distinguish from future days
- Max 3 days shown (Today + 2 more). [View full calendar →] links to Calendar tab.
- If nothing scheduled: "No content scheduled this week. [Plan your week →]" (IQ pre-fill prompt)
- Items are plain rows, no card borders — keeps it light and scannable
- 32px row height, 4px gap between items, 12px gap between day groups

---

### SECTION 5: WHAT'S WORKING (Quick wins — keep doing this)

The expert's top performers. Reinforces that the platform is generating results. Short and punchy — 2 items max.

```
┌─────────────────────────────────────────────────────┐
│  🏆 WHAT'S WORKING                                  │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  📝 Cortisol carousel                  4.2% eng 🟢 │
│     Outperforming average by 2.3x                   │
│     ▁▂▃▅▇█▇▅ (sparkline)                          │
│                                                     │
│  ✉️ Welcome sequence                  42% open 🟢  │
│     Above 25% benchmark                             │
│     ▁▂▄▆▇█▇▆ (sparkline)                          │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Header: "WHAT'S WORKING" (11px, uppercase, #6B7280) + Trophy icon
- Each item: compact card, #F0FDF4 background (light emerald tint), rounded-lg, padding 10px 14px
  - Left: builder emoji + content name (13px, bold, #065F46)
  - Right: metric value (13px, bold, #065F46) + green dot
  - Below: one-line context (12px, #065F46) + tiny sparkline chart (32px wide, emerald stroke)
- Exactly 2 items. No more. These are the highlights, not a full report.
- 8px gap between items.

---

### SECTION 6: IQ RECOMMENDATIONS (Smart suggestions — 2 max)

AI-powered actions the expert can take with one click. Not a list of 3+ — just the top 2 highest-impact moves.

```
┌─────────────────────────────────────────────────────┐
│  💡 IQ RECOMMENDS                                   │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  1  Create 3 more cortisol carousels —              │
│     this format is outperforming by 2x              │
│                                    [Apply →]        │
│                                                     │
│  2  Refresh ad creative for Set B —                 │
│     fatigue detected after 14 days                  │
│                                    [Apply →]        │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Header: "IQ RECOMMENDS" (11px, uppercase, #6B7280) + Lightbulb icon
- Each recommendation: number circle (20px, #1F2937 bg, white text, bold) + text (13px, #374151) + [Apply →] link (emerald, 12px, bold)
- Exactly 2 recommendations. The two highest-leverage actions right now.
- Clicking [Apply →] → tells IQ Claw to execute the recommendation (pre-fills chat)
- Rows: 48px height, 6px gap, no background (just text rows with subtle bottom border #F3F4F6)

---

## WHAT WAS REMOVED AND WHY

| Removed | Why |
|---------|-----|
| Greeting + date header | Redundant with IQ's chat greeting. Wastes top real estate. |
| Four score cards across the top | Replaced by single IQ Score gauge with inline category scores below. One number to rule them all. |
| "Overall Health Score" donut in row 2 | Promoted to Section 1 — it's now the hero element. |
| "Performance by Category" with tabs and detail metrics | Too deep for the right panel. That depth lives on the Home page (/home). The right panel gives you the score; Home gives you the breakdown. |
| "Activity Feed" timeline | Redundant. IQ Claw narrates activity in the center chat. The right panel doesn't need to repeat it. |
| Third recommendation | Two is enough for the right panel. Keep it tight. |

---

## FULL SECTION ORDER

1. **IQ Score** — the number (hero, always visible without scrolling)
2. **Needs Attention** — what's broken / what needs action
3. **Active Engines** — what systems are running
4. **This Week** — what's publishing
5. **What's Working** — top 2 performers
6. **IQ Recommends** — top 2 smart moves

**Total scroll depth:** The expert should see Sections 1–3 without scrolling (above the fold on a standard right panel). Sections 4–6 are one scroll down. Nothing should feel buried or endless.

---

## DESIGN SYSTEM (matching existing platform)

- **Section headers:** 11px, uppercase, #6B7280, letter-spacing 0.05em. Icon (14px, #6B7280) to the left.
- **Section dividers:** 1px #E5E7EB, 16px margin top/bottom between sections.
- **Cards within sections:** White bg (#FFFFFF) if used, 1px border #E5E7EB, rounded-lg (8px). Or no cards for lightweight sections (This Week, Recommendations).
- **Metric chips:** 12px text, #374151, #F3F4F6 bg, rounded-md, padding 2px 6px. Colored dot (6px) for status.
- **Action links:** Emerald (#10B981) text, bold, 12–13px. Arrow on hover. Clicking sends a command to IQ Claw in the center chat.
- **Section padding:** 16px horizontal, 12px vertical within sections.
- **Responsive:** On narrow right panels (< 320px), category score row in Section 1 wraps to 2×2 grid. Everything else stacks naturally.

---

## THE PRINCIPLE

This dashboard is the **executive briefing** — not the full report. The expert glances right, gets the score, sees what needs attention, knows what's running, knows what's publishing, sees what's winning, and gets two smart moves to make. Then they turn back to IQ in the center chat and act on it.

**Every pixel earns its space. If it doesn't make the expert smarter or faster in 2 seconds, it doesn't belong.**
