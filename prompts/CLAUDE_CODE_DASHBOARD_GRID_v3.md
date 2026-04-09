# ClinicIQ — Dashboard Tab v3: Grid Layout
## Delete the current scrolling dashboard. Rebuild as a structured 2-column card grid.

---

## THE PROBLEM

The current Dashboard tab is a single-column vertical scroll. It feels like a blog post, not a command center. A billion-dollar platform dashboard uses a **card grid** — structured, dense, glanceable. Everything visible in one view or very close to it.

**Delete the entire current Dashboard tab content and rebuild from scratch using this spec.**

---

## LAYOUT: 2-Column Card Grid

The Dashboard tab content area uses a 2-column grid with some full-width spans. Cards are fixed-height where possible so rows align cleanly. 12px gap between all cards.

```
┌─────────────────────────────────────────────────────┐
│  $12,400        │     23        │      4            │  ← Row 0: The Pulse (full-width bar)
│  Revenue MTD    │  New Leads    │  Calls Booked     │
│  ↑ 18%          │  12 today     │  this week        │
├────────────────────────┬────────────────────────────┤
│                        │                            │
│    IQ Score            │    Needs Attention         │  ← Row 1: Health + Alerts
│    [71/100 gauge]      │    🔴 Ad Set B fatiguing   │
│    🎯 4 pts to 75     │    🟡 Email rates down     │
│    Ad 64 Fun 78        │    ⚪ 5 posts pending      │
│    Soc 82 Email 58     │                            │
│                        │                            │
├────────────────────────┬────────────────────────────┤
│                        │                            │
│    Active Engines      │    This Week               │  ← Row 2: Systems + Calendar
│    🎥 Webinar 🟢      │    Today:                  │
│    📅 Content 🔵 42%  │    · Reel 9am · Email 11am │
│    🧲 Lead Mag 🟡     │    Tomorrow:               │
│                        │    · Carousel · Ad refresh │
│                        │                            │
├────────────────────────┬────────────────────────────┤
│                        │                            │
│    Performance         │    IQ Recommends           │  ← Row 3: Insight + Action
│    Spotlight           │    1. More cortisol posts  │
│    🟢 Cortisol 4.2%   │    2. Refresh Set B ads    │
│    🔴 Thursday 0.8%   │                            │
│                        │    🛡️ Proof Bank 42/100   │
│                        │                            │
└────────────────────────┴────────────────────────────┘
```

---

## ROW 0: THE PULSE (Full-width bar — top of dashboard, always visible)

Not a card — a flush bar spanning the full width of the right panel.

```
┌──────────────────┬──────────────────┬──────────────────┐
│    $12,400       │      23          │       4          │
│  REVENUE MTD     │  NEW LEADS       │  CALLS BOOKED    │
│  ↑ 18% vs last   │  ↑ 12 today      │  this week       │
└──────────────────┴──────────────────┴──────────────────┘
```

**Design:**
- Full-width, no card border, white bg, padding 14px 16px
- 3 equal columns divided by 1px #E5E7EB vertical lines
- Each metric:
  - Value: 22px, bold, #1F2937 (Revenue gets $ prefix)
  - Label: 10px, uppercase, #9CA3AF, letter-spacing 0.05em
  - Trend: 11px — emerald + TrendingUp icon if positive, red + TrendingDown if negative, #9CA3AF if neutral
- Bottom: 1px #E5E7EB divider
- If integrations not connected: values show "—" with tiny "Connect →" link (11px, emerald)

---

## ROW 1: IQ SCORE (Left) + NEEDS ATTENTION (Right)

Two cards side by side. Equal height — use `align-items: stretch` on the row so both cards match the taller one.

### Left Card: IQ Score

White card, border 1px #E5E7EB, rounded-xl (12px), padding 16px. Min-height: 180px.

```
┌─────────────────────────────┐
│                             │
│    ┌────┐  IQ Score         │
│    │ 71 │  ↗ +3 last week  │
│    │/100│                   │
│    └────┘  🎯 4 pts to 75  │
│    (gauge)  unlock Insights │
│                             │
│  Ad 64· Fun 78· Soc 82· Em 58│
│  (🟡)  (🟢)   (🟢)   (🟡)  │
│                             │
└─────────────────────────────┘
```

- Circular gauge: 56px diameter, 5px stroke. Color: emerald (80+), amber (60–79), red (<60).
- Score: 24px, bold, inside gauge. "/100": 10px, #6B7280.
- Right of gauge: "IQ Score" (14px, bold), trend line (11px, emerald/red), milestone (11px, #6B7280, 🎯 emoji)
- Bottom row: category scores, 11px, colored dots (5px). Lowest category: subtle tinted bg pill to draw the eye.
- Milestones: 50→Foundation, 75→Audience Insights, 85→Growth Mode, 95→Elite Operator

### Right Card: Needs Attention

White card, same dimensions as IQ Score card. Border 1px #E5E7EB, rounded-xl, padding 16px.

```
┌─────────────────────────────┐
│  ⚠️ NEEDS ATTENTION    3    │
│                             │
│  🔴 Ad Set B fatiguing      │
│     CTR down 40%  [Fix →]  │
│                             │
│  🟡 Email rates declining   │
│     22% → 16%   [Review →] │
│                             │
│  ⚪ 5 posts pending          │
│     Content batch [Review →]│
│                             │
└─────────────────────────────┘
```

- Header: "NEEDS ATTENTION" (10px, uppercase, #9CA3AF) + count badge (14px circle, #EF4444 bg for critical, amber for warning, gray for info — use highest severity color)
- Each alert: colored dot (6px) + left border (3px) matching severity + title (12px, bold, #1F2937) + subtitle (11px, #6B7280) + action link (11px, emerald, right-aligned)
- Alert row: 44px height, #F9FAFB bg, rounded-md, 4px gap between alerts
- Severity order: 🔴 red → 🟡 amber → ⚪ gray
- Max 3 alerts. If more: "+2 more" link at bottom.
- Zero state: "✅ All clear" (emerald, centered, 12px)

---

## ROW 2: ACTIVE ENGINES (Left) + THIS WEEK (Right)

### Left Card: Active Engines

White card, rounded-xl, padding 16px.

```
┌─────────────────────────────┐
│  ⚡ ENGINES                  │
│                             │
│  🎥 Webinar Funnel    🟢   │
│     38% opt · 22% show     │
│                             │
│  📅 Content Apr      🔵   │
│     ████████░░ 42%         │
│                             │
│  🧲 Lead Magnet      🟡   │
│     30 assets → review     │
│                             │
│        [View all →]         │
└─────────────────────────────┘
```

- Header: "ENGINES" (10px, uppercase, #9CA3AF) + Zap icon (12px)
- Each engine row: 40px height
  - Left: emoji (14px) + name (12px, bold, #1F2937, truncate)
  - Right: status pill (tiny — 🟢 Active / 🔵 Running / 🟡 Review)
  - Below name: compact metric or progress bar (11px, #6B7280)
- Max 3 engines. [View all →] links to /engines.
- Zero state: "No engines yet [Browse Library →]"

### Right Card: This Week

White card, rounded-xl, padding 16px.

```
┌─────────────────────────────┐
│  📅 THIS WEEK    Apr 7–13  │
│                             │
│  Today                      │
│  · 📝 Reel — Cortisol  9am │
│  · ✉️ Broadcast       11am │
│                             │
│  Tomorrow                   │
│  · 📝 Carousel         9am │
│  · 📢 Ad refresh      Auto │
│                             │
│  Thu                        │
│  · 📝 Story           10am │
│                             │
│      [Full calendar →]      │
└─────────────────────────────┘
```

- Header: "THIS WEEK" (10px, uppercase, #9CA3AF) + date range (10px, #9CA3AF)
- Day labels: 12px, bold, #1F2937
- Items: emoji (12px) + title (11px, #374151, truncate) + time (11px, #9CA3AF, right-aligned)
- Today group: 2px emerald left border to distinguish
- Row height: 28px. Day gap: 8px.
- Max 3 days, max 2 items per day (truncate). [Full calendar →] links to Calendar tab.
- Zero state: "Nothing scheduled [Plan your week →]"

---

## ROW 3: PERFORMANCE SPOTLIGHT (Left) + IQ RECOMMENDS (Right)

### Left Card: Performance Spotlight

White card, rounded-xl, padding 16px.

```
┌─────────────────────────────┐
│  📊 SPOTLIGHT               │
│                             │
│  WINNING                    │
│  ┌────────────────────────┐ │
│  │ 📝 Cortisol    4.2% 🟢│ │
│  │ ↑ 2.3x average  ▁▃▅▇█│ │
│  └────────────────────────┘ │
│                             │
│  FIX THIS                   │
│  ┌────────────────────────┐ │
│  │ 📝 Thursday    0.8% 🔴│ │
│  │ ↓ 60% below    █▅▃▂▁ │ │
│  └────────────────────────┘ │
│                             │
└─────────────────────────────┘
```

- Header: "SPOTLIGHT" (10px, uppercase, #9CA3AF) + BarChart3 icon
- "WINNING" sub-label: 9px, uppercase, #065F46
- Winner card: #F0FDF4 bg, 2px emerald left border, rounded-md, padding 8px 10px
  - Name (12px, bold, #065F46) + metric (12px, bold, #065F46, right) + sparkline (28px wide, emerald)
  - Trend (10px, #065F46)
- "FIX THIS" sub-label: 9px, uppercase, #991B1B
- Loser card: #FEF2F2 bg, 2px red left border, rounded-md, padding 8px 10px
  - Name (12px, bold, #991B1B) + metric (12px, bold, #991B1B, right) + sparkline (28px, red, declining)
  - Trend (10px, #991B1B)

### Right Card: IQ Recommends + Proof Bank

White card, rounded-xl, padding 16px.

```
┌─────────────────────────────┐
│  💡 IQ RECOMMENDS           │
│                             │
│  ① More cortisol carousels  │
│    outperforming 2x [Apply]│
│                             │
│  ② Refresh Set B ads        │
│    fatigue 14 days [Apply] │
│                             │
│  ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ │
│  🛡️ Proof Bank 42/100      │
│  ████████░░░░░░░            │
│  Ask 3 patients for video   │
│  testimonials  [Strengthen] │
│                             │
└─────────────────────────────┘
```

- Header: "IQ RECOMMENDS" (10px, uppercase, #9CA3AF) + Lightbulb icon
- Each rec: number circle (16px, #1F2937 bg, white text, 10px bold) + text (11px, #374151) + [Apply →] (11px, emerald)
- 2 recommendations max. Row height: 36px.
- Dashed divider (1px dashed #E5E7EB) before proof bank section
- Proof Bank (conditional — only when score < 60):
  - Shield emoji + "Proof Bank: 42/100" (12px, bold, #374151)
  - Progress bar: full-width, 3px, amber fill
  - Nudge text (10px, #6B7280) + [Strengthen →] (10px, emerald)

---

## GRID CSS STRUCTURE

```css
.dashboard-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto auto auto auto;
  gap: 12px;
  padding: 12px 16px;
}

.pulse-bar {
  grid-column: 1 / -1; /* full width */
}

.iq-score { grid-column: 1; grid-row: 2; }
.needs-attention { grid-column: 2; grid-row: 2; }

.engines { grid-column: 1; grid-row: 3; }
.this-week { grid-column: 2; grid-row: 3; }

.spotlight { grid-column: 1; grid-row: 4; }
.recommends { grid-column: 2; grid-row: 4; }
```

Each row's cards should use `align-items: stretch` so both cards in a row match height. If one card has more content, the other stretches to match — no ragged rows.

---

## CARD SIZING

All cards in the same row should be the same height. The grid handles this with stretch alignment. Approximate heights:

- Row 0 (Pulse): ~70px
- Row 1 (IQ Score + Needs Attention): ~180px
- Row 2 (Engines + This Week): ~190px
- Row 3 (Spotlight + Recommends): ~200px

**Total height: ~640px + gaps.** This should fit within a standard right panel viewport without scrolling, or with minimal scroll on smaller screens.

---

## RESPONSIVE

- **Normal right panel (380px+):** 2-column grid as designed
- **Narrow right panel (< 380px):** Stack to single column. Cards go full-width. Pulse bar stays 3-column internally but text shrinks.
- **Very narrow (mobile):** Single column, cards stack vertically

---

## DESIGN SYSTEM

- **Card style:** White #FFFFFF, border 1px #E5E7EB, rounded-xl (12px). No shadow at rest. Subtle shadow on hover (optional).
- **Section headers inside cards:** 10px, uppercase, #9CA3AF, letter-spacing 0.05em
- **Metric values:** 22px for Pulse, 24px for IQ Score, 12px for everything else
- **Body text in cards:** 11–12px. Dense but readable.
- **Colors:** Emerald for positive/CTAs, amber for warnings/progress, red for critical/losing, gray for neutral/info
- **Sparklines:** 28px wide, 16px tall, 2px stroke, no axes/labels — just the line
- **Progress bars:** 3–4px height, rounded-full, colored fill on #E5E7EB track

---

## THE PRINCIPLE

This is a **cockpit, not a scroll.** The expert looks at the right panel and sees their entire business at a glance — money flowing, health score, alerts, engines running, content publishing, what's winning, what's losing, and two smart moves to make. All without scrolling. Every card is a window into a different part of the machine.
