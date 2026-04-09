# ClinicIQ — Builders Tab Fix
## Remove workflow pills from Start New. Show all 12 builders.

---

## THE PROBLEM

The Builders tab on the right panel has a "Start New" section that currently shows:
1. Three workflow-type pills: "Content Batch", "Launch Campaign", "Monthly Refresh" — **these don't belong here.** Those are Growth Engines (multi-step workflows), not builders. They live on the /engines page. Remove them entirely.
2. Only 6 builder cards are showing (Content Builder, Funnel Builder, Email Builder, Ad Creative, Lead Magnet, Campaign Builder). **There are 12 builders.** All 12 must be visible.

---

## THE FIX

### Remove the workflow pills
Delete the "Content Batch", "Launch Campaign", and "Monthly Refresh" pill buttons from the Start New section entirely. Builders and Engines are separate concepts:
- **Builders** (this tab) = single-asset tools. "Make me a thing."
- **Engines** (/engines page) = multi-step coordinated systems. "Build me a machine."

The Builders tab should only show builders.

### Show all 12 builders
The "Start New" section should display all 12 builders in a 2-column grid. Each builder is a compact card.

**The 12 builders, in this exact order:**

Row 1:
📝 **Content Builder** — Posts, carousels, reels, stories
🔗 **Funnel Builder** — Opt-in pages, sales pages, landing pages

Row 2:
🎥 **Webinar Builder** — Script, slides, follow-up sequence
✉️ **Email Builder** — Sequences, nurtures, promos, launches

Row 3:
📢 **Ad Creative Builder** — Hooks, copy, creatives, variants
🧲 **Lead Magnet Builder** — PDF guides, quizzes, assessments

Row 4:
🎓 **Program Builder** — Course content, protocols, modules
🎙️ **Podcast Builder** — Episodes, scripts, show notes

Row 5:
📞 **Sales Script Builder** — Phone, DM, and close scripts
🌐 **Website Builder** — Landing pages, service pages

Row 6:
🚀 **Campaign Builder** — Full campaign: content + email + ads + funnels
🏆 **Challenge Builder** — 5, 7, 14, or 30-day challenge sequences

**Builder card styling:**
- White background (#FFFFFF), 1px border #E5E7EB, rounded-lg (8px)
- Padding: 10px 12px
- Left: colored emoji icon (20px)
- Right of icon: builder name (13px, bold, #1F2937) on first line, description (11px, #6B7280) on second line
- Hover: border #10B981 (emerald), subtle shadow, cursor pointer
- Clicking a builder card → pre-fills the IQ Claw chat input in the center panel with a prompt for that builder (e.g., clicking Content Builder types "Create a social post" in the chat input, or directly sends a message to IQ Claw saying the user wants to use that builder)
- 8px gap between cards in the grid

**Section header:**
"START NEW" — 11px, uppercase, #6B7280, letter-spacing 0.05em — same styling as other section headers in the right panel.

---

## FULL BUILDERS TAB LAYOUT (for reference)

The Builders tab content, top to bottom:

### Section 1: BUILD QUEUE
- Header: "BUILD QUEUE" + active count pill (e.g., "4 active")
- Shows currently running and queued builder tasks with progress bars
- This section is already correct — keep it as-is

### Section 2: JUST COMPLETED
- Header: "JUST COMPLETED"
- Shows recently finished builder outputs with timestamps and [View] buttons
- This section is already correct — keep it as-is

### Section 3: START NEW
- Header: "START NEW"
- 12 builder cards in a 2-column grid (as specified above)
- No workflow pills. No "Content Batch", "Launch Campaign", "Monthly Refresh."
- Just the 12 builders, clean and simple.

---

## THAT'S IT

Three changes:
1. Delete the three workflow pills (Content Batch, Launch Campaign, Monthly Refresh)
2. Add the 6 missing builders (Webinar, Program, Podcast, Sales Script, Website, Challenge)
3. Make sure all 12 are in a clean 2-column grid in the order specified above
