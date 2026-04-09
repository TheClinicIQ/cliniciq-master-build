# ClinicIQ — Dashboard Tab Redesign v2
## Rebuild the right-panel Dashboard tab to feel like a billion-dollar CEO command center

---

## CONTEXT

The Dashboard tab lives in the right panel of the IQ workspace — next to the center chat. It is NOT the full-screen Home page. It's the **compact, glanceable command center** the expert sees while they're working with IQ Claw. It needs to answer three questions instantly:

1. **"Am I making money?"** — Revenue, leads, booked calls. Real numbers.
2. **"Is anything broken?"** — What needs my attention right now.
3. **"Is the platform working?"** — What's running, what's winning, what's next.

The current version has the right bones but needs to be tightened. Too much scroll depth, some sections are redundant, the hierarchy doesn't lead the eye to what matters most, and critically — **there are no revenue or pipeline numbers anywhere.** The expert runs a real business. The dashboard should feel like it.

---

## WHAT'S WRONG WITH THE CURRENT VERSION

1. **No revenue, no leads, no pipeline.** The expert generates real money and the dashboard doesn't show a single dollar sign. This is the #1 gap.
2. **Greeting and date** at the top waste prime real estate — the expert already sees IQ's greeting in the chat. Don't repeat it here.
3. **Four score cards across the top** compete for attention equally — but they shouldn't. The expert needs one overall number, not four.
4. **"Overall Health Score" donut** is buried in the second row — it should be prominent but not above the money.
5. **"Needs Your Attention"** is excellent but the alerts lack severity weight — a fatiguing ad set and 5 posts awaiting approval shouldn't look the same.
6. **"Recommendations"** and **"What's Working"** are good but take too much vertical space for what they show. And "What's Working" only shows winners — it should also show what's dying so the expert knows what to fix.
7. **"Performance by Category"** with tabbed detail metrics is too deep for the right panel — that's Home page depth. The right panel should surface the headline, not the table.
8. **"Activity Feed"** is filler. If IQ is narrating in the chat, the activity feed is redundant.
9. **No engines/workflow status** — the expert should see their active growth engines at a glance.
10. **No upcoming calendar** — what's publishing today/this week should be visible.
11. **No gamification** — the IQ Score should feel like something to improve, not just observe.

---

## THE REDESIGN — Top to Bottom

The Dashboard tab scrolls vertically inside the right panel. Every section earns its space by being immediately actionable or immediately informative. No filler. No redundancy with the chat. **7 sections.**

---

### SECTION 1: THE PULSE (Money + Pipeline — the first thing they see)

Three numbers. Always visible. No scrolling required. This is what makes the expert addicted to checking the platform every morning. Not scores — **dollars and pipeline.**

```
┌──────────────────┬──────────────────┬──────────────────┐
│    $12,400       │      23          │       4          │
│  Revenue MTD     │  New Leads       │  Calls Booked    │
│  ↑ 18% vs last   │  12 today        │  this week       │
└──────────────────┴──────────────────┴──────────────────┘
```

**Design:**
- Three equal-width columns inside a single row, no card borders — bleeds to the panel edges
- Each metric:
  - Value: 24px, bold, #1F2937 (Revenue gets a $ prefix)
  - Label: 11px, uppercase, #6B7280, letter-spacing 0.05em
  - Trend/context: 12px — emerald text + TrendingUp icon (↑) if positive, red + TrendingDown (↓) if negative, gray if neutral
- Revenue: "$12,400" with "↑ 18% vs last month" in emerald
- New Leads: "23" with "12 today" in emerald (today's count highlighted — creates a "checking the score" habit)
- Calls Booked: "4" with "this week" in gray
- Dividers: thin 1px #E5E7EB vertical lines between columns
- Bottom border: 1px #E5E7EB to separate from next section
- Padding: 16px top, 20px bottom
- These numbers pull from integrations (GHL, Stripe, Calendly, etc.). If not connected: show "--" with "Connect in Services →" link (12px, emerald)

---

### SECTION 2: IQ SCORE (Health gauge — with milestone gamification)

The expert's overall platform health score — a composite of all category scores. Now with a milestone to chase.

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│     ┌─────────┐                                     │
│     │         │    IQ Score                         │
│     │   71    │    +3 from last week                │
│     │  /100   │                                     │
│     │         │    🎯 4 points to 75 —              │
│     └─────────┘       unlock Audience Insights      │
│     (circular gauge)                                │
│                                                     │
│   Ad 64  ·  Funnel 78  ·  Social 82  ·  Email 58  │
│   (🔴)      (🟢)         (🟢)          (🟡)        │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Circular gauge: 64px diameter (slightly smaller than before to save vertical space), thick stroke (6px). Color matches score: emerald (80+), amber (60–79), red (<60). This one shows amber at 71.
- Score number: 28px, bold, #1F2937, centered inside the gauge
- "/100" below number: 12px, #6B7280
- Right of gauge (vertically stacked):
  - "IQ Score" — 16px, bold, #1F2937
  - "+3 from last week" — 12px, emerald text with TrendingUp icon (if positive), red with TrendingDown (if negative)
  - Milestone: "🎯 4 points to 75 — unlock Audience Insights" — 12px, #6B7280. The 🎯 is the target emoji. The milestone text shows the next threshold and what it unlocks.
- **Milestones** (the gamification layer):
  - 50: "Foundation Set" — basic profile and content running
  - 75: "Audience Insights" — advanced analytics unlock
  - 85: "Growth Mode" — scaling recommendations activate
  - 95: "Elite Operator" — badge + priority support + advanced features
  - The dashboard always shows the next milestone the expert hasn't reached yet. Once hit, it celebrates briefly (confetti? emerald glow?) then shows the next one.
- Category scores below: horizontal row, 12px each, #6B7280 text. Colored dot (6px) next to each: emerald (75+), amber (50–74), red (<50). Lowest score gets a subtle amber/red background tint to draw the eye.
- Clicking any category score → navigates to a deeper view (future: Analytics page. For now: no-op or scroll to a relevant section).
- Card: no card border — bleeds to panel edges. White bg, 16px padding top/bottom. 1px #E5E7EB bottom border.

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

### SECTION 5: WINNING & LOSING (The contrast that creates action)

Not just what's working — the one thing that's crushing it next to the one thing that's dying. The contrast creates urgency. The expert immediately knows what to double down on and what to fix.

```
┌─────────────────────────────────────────────────────┐
│  📊 PERFORMANCE SPOTLIGHT                            │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  🟢 WINNING                                        │
│  📝 Cortisol carousel                  4.2% eng    │
│     ↑ 2.3x your average                            │
│     ▁▂▃▅▇█▇▅ (sparkline)                          │
│                                                     │
│  🔴 FIX THIS                                       │
│  📝 Thursday posts                     0.8% eng    │
│     ↓ 60% below average                            │
│     █▇▅▃▂▁▁▁ (sparkline, declining)               │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Header: "PERFORMANCE SPOTLIGHT" (11px, uppercase, #6B7280) + BarChart3 icon
- **Winner row:**
  - Sub-header: "WINNING" (10px, uppercase, #065F46, letter-spacing 0.05em)
  - Card: #F0FDF4 background (light emerald tint), rounded-lg, padding 10px 14px, 2px left border emerald
  - Left: builder emoji + content name (13px, bold, #065F46)
  - Right: metric value (13px, bold, #065F46)
  - Below: trend context (12px, #065F46) + sparkline (32px, emerald stroke, trending up)
- **Loser row:**
  - Sub-header: "FIX THIS" (10px, uppercase, #991B1B, letter-spacing 0.05em)
  - Card: #FEF2F2 background (light red tint), rounded-lg, padding 10px 14px, 2px left border red
  - Left: builder emoji + content name (13px, bold, #991B1B)
  - Right: metric value (13px, bold, #991B1B)
  - Below: trend context (12px, #991B1B) + sparkline (32px, red stroke, trending down)
- 8px gap between winner and loser cards.
- One winner. One loser. That's it. Maximum contrast, maximum action.

---

### SECTION 6: IQ RECOMMENDS (Smart suggestions — 2 max, plus proof bank nudge)

AI-powered actions the expert can take with one click. The top 2 highest-impact moves. Plus a persistent nudge when the proof bank is thin — because proof directly impacts conversion rates and most experts don't realize it.

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
│  ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─   │
│                                                     │
│  🛡️ Proof Bank: 42/100                              │
│  Ask your next 3 patients who got results           │
│  for a video testimonial — this directly            │
│  improves your ad and webinar conversion.           │
│                            [Strengthen Proof →]     │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Header: "IQ RECOMMENDS" (11px, uppercase, #6B7280) + Lightbulb icon
- Each recommendation: number circle (20px, #1F2937 bg, white text, bold) + text (13px, #374151) + [Apply →] link (emerald, 12px, bold)
- Exactly 2 recommendations. The two highest-leverage actions right now.
- Clicking [Apply →] → tells IQ Claw to execute the recommendation (pre-fills chat)
- Rows: 48px height, 6px gap, no background (just text rows with subtle bottom border #F3F4F6)

**Proof Bank Nudge (conditional):**
- Only shown when `proof_bank_depth_score` is below 60
- Appears below the 2 recommendations, separated by a dashed divider (1px dashed #E5E7EB)
- Shield icon (🛡️) + "Proof Bank: [score]/100" (13px, bold, #374151) + progress bar (full-width, 4px height, amber fill if 40–59, red fill if <40)
- Nudge text: one specific, actionable sentence connecting a real-world action to a platform outcome (13px, #6B7280)
- [Strengthen Proof →] emerald text link → navigates to Brand tab, scrolls to Proof Bank section
- When proof bank hits 60+, this nudge disappears and the space is reclaimed
- The nudge text rotates between different specific asks:
  - "Ask your next 3 patients who got results for a video testimonial — this directly improves your ad conversion."
  - "Upload the before/after labs from your last success story — data-backed proof converts 3x better than text testimonials."
  - "Record a 60-second clip of your next patient win — video testimonials are your highest-converting ad format."

---

## WHAT WAS REMOVED AND WHY

| Removed | Why |
|---------|-----|
| Greeting + date header | Redundant with IQ's chat greeting. Wastes top real estate. Replaced by The Pulse — real numbers. |
| Four score cards across the top | Replaced by single IQ Score gauge with inline category scores below. One number to rule them all. |
| "Overall Health Score" donut in row 2 | Promoted to Section 2 (after The Pulse) — still prominent but money comes first. |
| "Performance by Category" with tabs and detail metrics | Too deep for the right panel. That depth lives on the Home page (/home). The right panel gives you the score; Home gives you the breakdown. |
| "Activity Feed" timeline | Redundant. IQ Claw narrates activity in the center chat. The right panel doesn't need to repeat it. |
| Third recommendation | Two is enough for the right panel. Keep it tight. |
| "What's Working" showing only winners | Replaced by "Performance Spotlight" — one winner AND one loser. The contrast creates action. |

---

## FULL SECTION ORDER

1. **The Pulse** — revenue, leads, calls booked (the money — above everything)
2. **IQ Score** — the health gauge with milestone gamification
3. **Needs Attention** — what's broken / what needs action
4. **Active Engines** — what systems are running
5. **This Week** — what's publishing
6. **Performance Spotlight** — best performer vs. worst performer
7. **IQ Recommends** — top 2 smart moves + proof bank nudge

**Total scroll depth:** The expert should see Sections 1–3 without scrolling (above the fold on a standard right panel). Sections 4–7 are one scroll down. Nothing should feel buried or endless.

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

This dashboard is the **executive briefing** — not the full report. The expert glances right, sees the money flowing, gets the health score, sees what needs attention, knows what's running, knows what's publishing, sees what's winning AND what's dying, and gets two smart moves to make. Then they turn back to IQ in the center chat and act on it.

**Every pixel earns its space. If it doesn't make the expert smarter or faster in 2 seconds, it doesn't belong.**

The three things that make an expert check this dashboard every morning:
1. **The Pulse** — "Am I making money?" ($12,400 revenue, 23 leads, 4 calls booked)
2. **The Milestone** — "How close am I to 75?" (gamification creates pull)
3. **The Contrast** — winner vs. loser side by side ("Double down on cortisol carousels. Fix Thursday posts.")
