# ClinicIQ — Workflows Page
## New component in MagicPath

---

Design the Workflows page for ClinicIQ — this is where the expert sees, launches, manages, and tracks all automated workflows and builder tasks. It's the operational engine room of the platform.

## LAYOUT

Same left sidebar rail (72px) as all other pages — same 8 items, same styling. "Workflows" is the ACTIVE item (white circle highlight behind the workflow icon).

The rest of the screen is a full-width content area. Light background (#F8F9FA). No chat panel, no right panel split — this is a full page.

## TOP SECTION — Page Header

Full-width white bar with subtle bottom border:

Left side:
- "Workflows" — large bold text (24px)
- "Launch, manage, and track your automated growth engine" — gray subtext

Right side:
- [+ New Workflow] button in teal — rounded, bold
- Next to it: a subtle gray pill showing "12 active · 2 running now" with a small green pulse dot

## TAB BAR — Below the header

Horizontal tabs across the full width:

**All Workflows | Running | Completed | Templates**

"All Workflows" is active by default (teal text + underline). Others in gray.

---

## MAIN CONTENT — "All Workflows" Tab (default)

### Section 1: 🔥 Currently Running (top, most prominent)

Header: "Running Now" with a green pulse dot animation.

2 active workflow cards displayed as wide horizontal cards with a subtle green left border (4px):

**Card 1:**
Left section:
- 📝 icon (teal circle)
- "Content Batch — April Week 2" — bold title
- "Started 12 min ago by IQ Claw (scheduled)" — gray text

Center section — progress bar:
- "Generating 7 posts..." — small text above
- Teal progress bar at 65% — animated subtle pulse
- "4 of 7 complete · ~3 min remaining" — gray text below

Right section:
- [View Progress →] teal link
- ••• menu

**Card 2:**
Left:
- ✉️ icon (blue circle)
- "Email Sequence — Post-Webinar Follow-Up" — bold
- "Started 4 min ago by you" — gray text

Center — progress:
- "Writing email 2 of 4..."
- Progress bar at 40%
- "1 of 4 complete · ~6 min remaining"

Right:
- [View Progress →]
- •••

### Section 2: ⚡ Builders — Quick Launch Grid

Header: "Builders" — bold, with subtitle "Start a builder workflow or let IQ Claw handle it"

A grid of builder cards — 4 columns, 3 rows. Each card: white background, subtle border (#E5E7EB), 12px rounded corners, hover state (subtle teal border + lift shadow).

Each card layout:
- Colored circular icon (40px) at top-left
- Bold title to the right of icon
- One-line gray description below
- Small gray text at bottom: "Last run: 2 days ago" or "Never used"
- Entire card is clickable — opens IQ Claw chat pre-seeded with that builder

Row 1:
📝 **Content Builder** — "Posts, carousels, reels, stories" — Last run: 2h ago
🔗 **Funnel Builder** — "Opt-in pages, sales pages, landing pages" — Last run: 5 days ago
🎥 **Webinar Builder** — "Script, slides, follow-up sequence" — Last run: 1 week ago
✉️ **Email Builder** — "Sequences, nurtures, promos, launches" — Last run: 4h ago

Row 2:
📢 **Ad Creative Builder** — "Hooks, copy, creatives, variants" — Last run: 3 days ago
🧲 **Lead Magnet Builder** — "PDF guides, quizzes, assessments" — Last run: 2 weeks ago
🎓 **Program Builder** — "Course content, protocols, modules" — Never used
🎙️ **Podcast Builder** — "Episodes, scripts, show notes" — Never used

Row 3:
📞 **Sales Script Builder** — "Phone, DM, and close scripts" — Last run: 1 week ago
🌐 **Website Builder** — "Landing pages, service pages" — Never used
🚀 **Campaign Builder** — "Full campaign: content + email + ads + funnels" — Last run: 3 weeks ago
🏆 **Challenge Builder** — "5, 7, 14, or 30-day challenge sequences" — Never used

### Section 3: 📋 Recent Workflow Runs

Header: "Recent" with a [View All →] teal link on the right and a search field: "Search workflows..."

A table/list view of recent completed and scheduled workflows:

| Status | Workflow | Type | Started | Duration | Items | Actions |
|--------|----------|------|---------|----------|-------|---------|
| ✅ Complete | Content Batch — April Week 1 | Content Builder | Apr 4, 8:00 AM | 18 min | 7 posts | [View] [Rerun] |
| ✅ Complete | Weekly Performance Summary | Analytics | Apr 4, 5:00 PM | 45 sec | 1 report | [View] |
| ✅ Complete | Webinar Pre-Promo Sequence | Email Builder | Apr 3, 10:15 AM | 8 min | 4 emails | [View] [Rerun] |
| ✅ Complete | Ad Hook Refresh — Set B | Ad Creative | Apr 3, 2:30 PM | 6 min | 3 variants | [View] [Rerun] |
| ✅ Complete | Monthly Strategy Refresh | Strategy | Apr 1, 8:00 AM | 22 min | 1 plan | [View] |
| ⚠️ Partial | Lead Magnet — Cortisol Guide | Lead Magnet | Mar 30, 11:00 AM | 12 min | Incomplete | [View] [Retry] |
| ✅ Complete | Welcome Email Sequence | Email Builder | Mar 28, 3:00 PM | 10 min | 5 emails | [View] [Rerun] |

Table styling:
- Status column: ✅ green for complete, ⚠️ amber for partial, 🔄 blue for running, 🕐 gray for scheduled
- Alternating row backgrounds: white / very light gray (#FAFBFC)
- [View] opens the workflow results. [Rerun] triggers the same workflow again. [Retry] retries a failed run.
- Rows have subtle hover state
- Compact row height (48px)

---

## "Running" Tab Content (when clicked)

Shows only the currently running workflows — same card format as Section 1 above. If nothing is running: "No workflows running right now. Start one from the Builders grid or ask IQ Claw."

## "Completed" Tab Content

Shows the full history table from Section 3 but with more rows, date range filters [Today | This Week | This Month | All Time], and filter by type dropdown [All Types | Content | Email | Ads | Funnel | Webinar | Strategy].

## "Templates" Tab Content

Header: "Workflow Templates" — "Pre-built multi-step workflows you can launch with one click"

A grid of template cards (3 columns). Each template card:
- Icon + bold title
- 2-3 line description of what the workflow does end to end
- "Steps: 5" or similar step count in gray
- [Launch →] teal button

Templates:

🚀 **Full Campaign Launch**
"Content batch + email launch sequence + ad creatives + funnel check — everything coordinated for a campaign launch in one workflow."
Steps: 6 | [Launch →]

📅 **Monthly Content Plan**
"Strategy refresh + content calendar + full month content batch + email sequences aligned to campaign themes."
Steps: 4 | [Launch →]

🎥 **Webinar Launch Package**
"Webinar script + slide deck + pre-webinar email sequence + post-webinar follow-up sequence + social promo content."
Steps: 5 | [Launch →]

🏆 **Challenge Launch**
"Challenge landing page + daily email sequence + daily social content + challenge completion sequence."
Steps: 4 | [Launch →]

📊 **Performance Deep Dive**
"Full analytics pull + content performance ranking + email audit + ad audit + recommendations report."
Steps: 3 | [Launch →]

🧲 **Lead Magnet Funnel**
"Lead magnet creation + opt-in page + delivery email + 5-email nurture sequence + webinar invitation."
Steps: 5 | [Launch →]

---

## DESIGN NOTES

- This page should feel like a mission control for marketing automation. The expert sees what's running, what's been done, and can launch anything with one click.
- The "Running Now" section at the top is the hero — if something is actively being built, they see it immediately with live progress.
- The Builder grid is the primary launch point — every builder is one click away.
- The table gives transparency into everything the platform has done. No black box. Every workflow is tracked with timing, status, and the ability to rerun.
- Templates are the "I don't know what to ask for" solution — pre-packaged multi-step workflows that handle complex coordinated tasks.
- The [+ New Workflow] button at the top opens IQ Claw chat with: "What would you like to build? Describe it and I'll set up the workflow."
- Clean, organized, professional. White cards on light gray. Teal accents for all interactive elements. Status colors: green (complete/running), amber (partial/warning), gray (scheduled/unused).
