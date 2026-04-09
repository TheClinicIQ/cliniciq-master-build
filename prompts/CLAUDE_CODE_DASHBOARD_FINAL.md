# ClinicIQ — Dashboard Tab: Final Version
## Revert to the original card-based dashboard. Then add Revenue Pulse, Engines, Calendar, Competitive Radar, and the winner/loser contrast.

**This prompt supersedes ALL previous dashboard prompts (v2, v3 grid). Revert the Dashboard tab to the original card-based design that Claude Code built initially, then layer these additions on top.**

---

## STEP 1: REVERT

Go back to the original Dashboard tab layout — the one with:
- Greeting + date + IQ Score pill + Open IQ button at the top
- 4 score cards in a row (Ad Metrics, Funnel Metrics, Social Media, Email/SMS)
- "Needs Your Attention" (3 alerts) + "Overall Health Score" (donut gauge)
- "Recommendations" (AI suggestions) + "What's Working" (top performers)
- "Performance by Category" (tabbed detail with metric tiles)
- Activity Feed at the bottom

**Restore all of this exactly as it was.** The card grid layout, the 2-column rows, the score cards, the tabs, all of it. That was the good foundation.

---

## STEP 2: ADD NEW SECTIONS

Now add the following sections INTO the existing dashboard, placed at the positions specified. The dashboard still scrolls vertically — that's fine. It should feel dense and information-rich, like a Bloomberg terminal for your practice.

---

### ADD: Revenue Pulse (INSERT at the very top — above the greeting)

This becomes the first thing the expert sees. Three revenue/pipeline metrics in a horizontal bar.

```
┌──────────────────┬──────────────────┬──────────────────┐
│    $12,400       │      23          │       4          │
│  REVENUE MTD     │  NEW LEADS       │  CALLS BOOKED    │
│  ↑ 18% vs last   │  12 today        │  this week       │
└──────────────────┴──────────────────┴──────────────────┘
```

- Full-width bar, no card border — sits flush at the top of the Dashboard tab
- 3 equal columns, divided by 1px #E5E7EB vertical lines
- Value: 22px, bold, #1F2937. Label: 10px, uppercase, #9CA3AF. Trend: 11px, emerald (positive) / red (negative) / #9CA3AF (neutral)
- Revenue: "$12,400" + "↑ 18% vs last month" emerald
- New Leads: "23" + "12 today" emerald
- Calls Booked: "4" + "this week" gray
- Bottom: 1px #E5E7EB divider
- If integrations not connected: "—" with "Connect in Services →" (11px, emerald)

---

### ADD: Milestone to the IQ Score pill in the greeting row

The existing "72 IQ Score" pill in the greeting row — add a milestone indicator next to it or below it:

"🎯 3 points to 75 — unlock Audience Insights"

- 11px, #6B7280, below the IQ Score pill or as a tooltip on hover
- Milestones: 50 (Foundation Set), 75 (Audience Insights), 85 (Growth Mode), 95 (Elite Operator)
- Shows the next unachieved milestone

---

### ADD: Active Engines (INSERT between "Needs Your Attention" row and "Recommendations" row)

A new 2-column section. Left card: Active Engines. Right card: This Week calendar.

#### Left Card: Active Engines

White card, same styling as other dashboard cards (border, rounded-xl, subtle shadow).

```
┌─────────────────────────────────────┐
│  ⚡ Active Engines            3 live │
│  ─────────────────────────────────  │
│                                     │
│  🎥 Evergreen Webinar Funnel  🟢   │
│     Opt-in 38% · Show 22% · CV 9%  │
│                                     │
│  📅 Monthly Content — April    🔵  │
│     Step 2 of 4 · ████████░░ 42%   │
│                                     │
│  🧲 Lead Magnet Funnel       🟡   │
│     30 assets ready for review      │
│                                     │
│              [View all engines →]    │
└─────────────────────────────────────┘
```

- Header: "Active Engines" (14px, bold) + Zap icon + count badge ("3 live")
- Each engine: emoji + name (13px, bold) + status pill (emerald/blue/amber) right-aligned
- Below name: compact metrics or progress bar (12px, #6B7280)
- 44px per engine row. Max 3 shown.
- [View all engines →] emerald link → /engines
- Zero state: "No engines yet. [Browse Engine Library →]"

#### Right Card: This Week

White card, matching height to Active Engines.

```
┌─────────────────────────────────────┐
│  📅 This Week              Apr 7–13│
│  ─────────────────────────────────  │
│                                     │
│  Today                              │
│  · 📝 Instagram Reel — Cortisol 9am│
│  · ✉️ Weekly broadcast email  11am │
│                                     │
│  Tomorrow                           │
│  · 📝 Carousel — Sleep       9am   │
│  · 📢 Ad Set A refresh      Auto   │
│                                     │
│  Thursday                           │
│  · 📝 Story — Client win    10am   │
│  · 🎥 Webinar replay email   2pm   │
│                                     │
│            [View full calendar →]    │
└─────────────────────────────────────┘
```

- Header: "This Week" (14px, bold) + Calendar icon + date range (12px, #9CA3AF)
- Day labels: 13px, bold. Items: 12px, #374151 + time right-aligned #9CA3AF
- Today items: emerald left border (2px)
- Max 3 days, max 2 items per day. [View full calendar →] → Calendar tab.

---

### MODIFY: "What's Working" → "Performance Spotlight" (winner vs. loser)

The existing "What's Working" card only shows winners (green). Change it to show **one winner AND one loser** side by side. The contrast creates urgency.

**Rename** from "What's Working" to "Performance Spotlight"

```
┌─────────────────────────────────────┐
│  📊 Performance Spotlight           │
│  ─────────────────────────────────  │
│                                     │
│  WINNING                            │
│  ┌────────────────────────────────┐ │
│  │ 📝 Cortisol carousel   4.2% 🟢│ │
│  │ ↑ 2.3x your average  ▁▃▅▇█   │ │
│  └────────────────────────────────┘ │
│                                     │
│  FIX THIS                           │
│  ┌────────────────────────────────┐ │
│  │ 📝 Thursday posts      0.8% 🔴│ │
│  │ ↓ 60% below average  █▅▃▂▁   │ │
│  └────────────────────────────────┘ │
│                                     │
└─────────────────────────────────────┘
```

- "WINNING" label: 9px, uppercase, #065F46. Green card: #F0FDF4 bg, emerald left border, emerald sparkline trending up.
- "FIX THIS" label: 9px, uppercase, #991B1B. Red card: #FEF2F2 bg, red left border, red sparkline trending down.
- Each: name (13px, bold) + metric (13px, bold, right) + trend context (11px) + sparkline (28px)

---

### ADD: Competitive Radar (INSERT into the "Recommendations" row — either below recommendations or as a paired card)

A compact competitive intelligence card. IQ monitors the expert's market and surfaces what competitors are doing.

```
┌─────────────────────────────────────┐
│  🔍 Competitive Radar               │
│  ─────────────────────────────────  │
│                                     │
│  2 competitor moves this week       │
│                                     │
│  📢 Dr. Martinez launched a new     │
│     "hormone quiz" ad campaign      │
│     Hook: "Is your thyroid really   │
│     the problem?"        [See more] │
│                                     │
│  🔗 Wellness Co. updated their      │
│     opt-in page — new social proof  │
│     layout with video testimonials  │
│                          [See more] │
│                                     │
│        [View full radar →]          │
└─────────────────────────────────────┘
```

- Header: "Competitive Radar" (14px, bold) + Search icon + move count
- Each intel item: emoji + competitor name/description (12px, #374151) + [See more] emerald link
- Max 2 items. [View full radar →] links to a future competitive intelligence page (for now: opens IQ chat with "Show me competitive intel")
- If no intel available: "IQ is monitoring your market. Intel will appear here as competitors make moves." (12px, #6B7280, italic)
- This card can sit below the Recommendations card in the same column, creating a Recommendations + Competitive Radar stack on the left, paired with Performance Spotlight on the right.

---

### ADD: Brand Growth Bar (INSERT between the 4 score cards and "Needs Your Attention")

A compact horizontal bar showing total audience reach across all connected platforms. One number, one trend.

```
┌─────────────────────────────────────────────────────────────┐
│  📈 Total Reach: 14,200  (+340 this week)                   │
│  IG 8.2K · FB 3.1K · YT 1.2K · Email 4.8K · TikTok —      │
└─────────────────────────────────────────────────────────────┘
```

- Full-width, compact bar (40px height), #F8F9FA bg, no card border
- "Total Reach" (13px, bold, #1F2937) + number (13px, bold) + trend in emerald/red (12px)
- Per-platform breakdown: 11px, #6B7280, separated by · dots. Platforms with no connection show "—"
- This is the vanity metric practitioners obsess over. Put it right where they'll see it every time.

---

### ADD: Proof Bank Nudge (INSERT at the bottom of the Recommendations card — conditional)

When `proof_bank_depth_score` is below 60, add a nudge inside the Recommendations card:

```
─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
🛡️ Proof Bank: 42/100
████████░░░░░░░░░░
Ask your next 3 patients who got results for a video
testimonial — this directly improves ad conversion.
                          [Strengthen Proof →]
```

- Dashed divider above
- Shield emoji + score (13px, bold) + progress bar (3px, amber fill)
- Nudge text (12px, #6B7280) + [Strengthen Proof →] emerald link → Brand tab → Proof Bank section
- Disappears when proof bank hits 60+

---

## FINAL SECTION ORDER (top to bottom)

1. **💰 Revenue Pulse** — $12,400 / 23 leads / 4 calls (NEW — full-width bar)
2. **👋 Greeting** — "Good evening, Dr. Sarah" + date + IQ Score pill with milestone (EXISTING + milestone added)
3. **📊 4 Score Cards** — Ad 64, Funnel 78, Social 82, Email 58 (EXISTING — unchanged)
4. **📈 Brand Growth Bar** — 14,200 total reach, per-platform breakdown (NEW — compact bar)
5. **⚠️ Needs Your Attention + 🩺 Overall Health Score** — 2-column row (EXISTING — unchanged)
6. **⚡ Active Engines + 📅 This Week** — 2-column row (NEW)
7. **💡 Recommendations + 🔍 Competitive Radar** — stacked in left column (EXISTING recommendations + NEW radar below)
8. **📊 Performance Spotlight** — winner vs. loser contrast (MODIFIED from "What's Working")
9. **📈 Performance by Category** — tabbed detail with metric tiles (EXISTING — unchanged)
10. **📋 Activity Feed** — recent events timeline (EXISTING — unchanged)

---

## WHAT CHANGED FROM THE ORIGINAL

| Change | Type | Why |
|--------|------|-----|
| Revenue Pulse at top | ADDED | Money is what practitioners check first. Makes the platform feel indispensable. |
| IQ Score milestone | ADDED | "🎯 3 points to 75" creates gamification pull. |
| Brand Growth Bar | ADDED | Vanity metric that keeps them engaged. Watching followers grow = posting more. |
| Active Engines section | ADDED | Shows the growth systems running — the platform is working 24/7. |
| This Week calendar | ADDED | Shows what's publishing — momentum even when they're not working. |
| Competitive Radar | ADDED | Nobody else shows this. Makes IQ feel omniscient. |
| "What's Working" → Performance Spotlight | MODIFIED | Added loser alongside winner. Contrast creates action. |
| Proof Bank nudge | ADDED | Connects real-world action to platform performance. |
| Greeting + date | KEPT | Premium touch — personal. |
| 4 score cards | KEPT | Strong visual anchor. |
| Needs Your Attention | KEPT | Critical operational alerts. |
| Overall Health Score donut | KEPT | Satisfying visual. |
| Recommendations | KEPT | High-leverage AI suggestions. |
| Performance by Category | KEPT | Deep metrics when they want to dig in. |
| Activity Feed | KEPT | Recent events for context. |

**Nothing from the original was removed.** Everything was kept. 6 new sections were added, 1 was modified. The dashboard got richer, not thinner.

---

## THE PRINCIPLE

This is the dashboard that makes a practitioner check ClinicIQ before they check their email in the morning. Revenue flowing, audience growing, competitors monitored, engines running, content publishing, winners celebrated, losers flagged, and two smart moves to make. It answers every question a health business owner has — in one scroll.
