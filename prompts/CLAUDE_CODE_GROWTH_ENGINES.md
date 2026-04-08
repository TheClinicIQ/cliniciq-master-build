# ClinicIQ Growth Engines Page — Complete Build Spec for Claude Code
## Build the `/engines` route: the expert's growth engine command center
## Where multi-step, coordinated marketing systems are built, tracked, and optimized

Build the `/engines` route for ClinicIQ. This is where a health practitioner builds, launches, tracks, and optimizes their complete marketing systems — not individual pieces of content, but coordinated multi-builder engines that produce entire business outcomes (webinar funnels, campaign launches, monthly content machines, challenge funnels, etc.).

Tech: React + Tailwind CSS + shadcn/ui. Lucide React icons. Inter font. Match all existing design patterns from the onboarding and IQ workspace screens.

---

## WHAT THIS PAGE IS

Growth Engines are multi-step, coordinated operations that chain multiple builders together toward a single business outcome. The expert either picks a pre-built engine template or describes what they want and IQ Claw architects a custom engine.

**The distinction (this drives every design decision):**
- **Builder** (right panel in /iq) = "Make me a thing" — single builder, single asset type
- **Growth Engine** (this page) = "Build me a system" — multiple builders, sequenced with dependencies, producing a complete marketing machine

---

## SCREEN LAYOUT

Same left sidebar rail (72px) as all other pages — same 8 items, same styling, same Lucide icons, same emerald active state. **"Engines"** is the ACTIVE item (white circle highlight behind the icon). Use the **Zap** icon from Lucide (lightning bolt — signals power/automation).

**Sidebar update:** Replace the "Workflows" item with "Engines":
- Old: GitBranch icon + "Workflows"
- New: Zap icon + "Engines"
- Same position in the sidebar (4th item, between IQ and Teams)

The rest of the screen is a full-width content area. Light background (#F8F9FA). No chat panel, no right panel split — this is a full page like Home and Teams.

---

## TOP BAR — Page Header

Full-width white bar (#FFFFFF), subtle bottom border (#E5E7EB), padding 24px horizontal, 16px vertical.

**Left side:**
- "Growth Engines" — bold, 24px, #1F2937
- "Build, run, and optimize your complete marketing systems" — 14px, #6B7280, 4px below heading

**Right side:**
- [+ New Engine] button — emerald (#10B981) background, white text, bold, 14px, rounded-lg (8px), padding 10px 20px, hover: darken 10%. Zap icon (16px, white) to the left of the text.
- To the left of the button (12px gap): a subtle gray (#F3F4F6) rounded-full pill with dark text — "3 active · 1 running" with a small green (#22C55E) pulse dot (6px, animated opacity 0.4→1→0.4 over 2s) next to "running." If nothing is running, pill shows "3 active" with no pulse dot. If no engines exist yet, no pill is shown.

---

## TAB BAR — Below the header

Horizontal tabs, full-width, 1px bottom border (#E5E7EB), padding 0 24px.

**4 tabs:**
**My Engines** | **Running** | **History** | **Engine Library**

- Active tab: #1F2937 text, bold, 2px emerald (#10B981) bottom border.
- Inactive tabs: #6B7280 text, regular weight, no border. Hover: #1F2937.
- Tab text: 14px. Tab padding: 12px 16px.
- "My Engines" is active by default.
- "Running" tab shows a small emerald badge (16px circle, white text, bold) with the count of currently running engines (e.g., "1"). Badge hidden when count is 0.

---

## "MY ENGINES" TAB — Default View

### Empty State (shown when expert has zero engines)

Centered on the page, max-width 520px:

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│                    [Zap icon, 48px, #9CA3AF]                    │
│                                                                 │
│              No growth engines yet                              │
│              (20px, bold, #1F2937, center)                      │
│                                                                 │
│     Your engines build complete marketing systems —             │
│     webinar funnels, content machines, campaign launches —      │
│     using multiple builders working together.                   │
│     (14px, #6B7280, center, max-width 400px)                   │
│                                                                 │
│            [Browse Engine Library →]                             │
│            (emerald text link, 14px, bold)                      │
│                                                                 │
│     or describe what you want to build:                         │
│     (12px, #9CA3AF, center)                                     │
│                                                                 │
│     ┌──────────────────────────────────────────────┐            │
│     │  "I want a funnel that turns cold traffic    │            │
│     │   into booked consults..."                   │            │
│     │                                  [→ Send]    │            │
│     └──────────────────────────────────────────────┘            │
│     (Rounded input, border #E5E7EB, placeholder text           │
│      in #9CA3AF italic. Send button: emerald circle, 32px,     │
│      ArrowUp icon 16px white. On submit: navigates to /iq      │
│      with the message pre-filled — IQ Claw handles it.)        │
│                                                                 │
│  ── or start with a popular engine ──                           │
│  (12px, #9CA3AF, center, with 1px #E5E7EB lines on sides)      │
│                                                                 │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                      │
│  │ 🎥       │  │ 📅       │  │ 🧲       │                      │
│  │ Webinar  │  │ Monthly  │  │ Lead     │                      │
│  │ Funnel   │  │ Content  │  │ Magnet   │                      │
│  │          │  │ Machine  │  │ Funnel   │                      │
│  │ 40+ items│  │ 30/mo    │  │ 30 items │                      │
│  │[Launch →]│  │[Launch →]│  │[Launch →]│                      │
│  └──────────┘  └──────────┘  └──────────┘                      │
│  (3 compact template cards in a row, 160px wide each,          │
│   white bg, border #E5E7EB, rounded-xl, hover: border          │
│   emerald + subtle shadow. Emoji top-left 24px, name           │
│   bold 13px, asset count 11px #6B7280, [Launch →]              │
│   emerald text 12px bold at bottom.)                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Populated State (one or more engines exist)

Engines displayed as full-width horizontal cards, stacked vertically, 12px gap between cards. Sorted by priority: Running → Needs Review → Scheduled → Active → Draft → Archived (collapsed section at bottom).

**Engine Card — Full Specification:**

White card (#FFFFFF), border 1px #E5E7EB, rounded-xl (12px), padding 20px 24px. Hover: border #D1D5DB, subtle shadow (0 1px 3px rgba(0,0,0,0.06)). Left border: 4px colored border indicating status (emerald for active, amber for needs review, blue for running, gray for draft/archived).

**Card structure (3 rows inside the card):**

**Row 1 — Header:**
- Left: Engine icon (emoji, 24px) + Engine name (bold, 16px, #1F2937) + 8px gap + Status badge (small rounded-full pill):
  - 🟢 "Active" — emerald bg (#ECFDF5), emerald text (#065F46)
  - 🔵 "Running" — blue bg (#EFF6FF), blue text (#1E40AF) + pulse dot
  - 🟡 "Needs Review" — amber bg (#FFFBEB), amber text (#92400E)
  - ⏰ "Scheduled" — gray bg (#F3F4F6), dark text (#374151) + next run date
  - ✏️ "Draft" — gray bg, gray text (#6B7280)
  - 📦 "Archived" — gray bg, gray text, italic
- Right: action buttons row (12px gap):
  - [View] — gray outlined button (border #E5E7EB, #374151 text, rounded-lg)
  - [Rerun] — gray outlined button
  - [Optimize] — emerald outlined button (border #10B981, #065F46 text) — only shown when IQ has a recommendation
  - [Clone] — gray outlined button
  - [···] — 3-dot menu (MoreHorizontal icon, 20px, #6B7280) → dropdown: Rename, Schedule, Export, Archive, Delete (red text)

**Row 2 — Metadata (only if card is not a Draft):**
- Left: step count + asset count + dates — "6 steps · 40 assets · Last run: Apr 1 · Next: May 1" — 13px, #6B7280
- Right (if engine has performance data): Compact metric chips, 4 in a row, 8px gap:
  - Each chip: metric label + value + status dot (6px circle: emerald/amber/red)
  - Example: "Opt-in 38% 🟢" | "Show 22% 🟡" | "Convert 9% 🟢" | "CAC $42 🟢"
  - Chip styling: #F3F4F6 background, rounded-md, padding 4px 8px, 12px text, #374151
  - Status dot color: emerald (#22C55E) if at or above benchmark, amber (#F59E0B) if within 80% of benchmark, red (#EF4444) if below 80% of benchmark

**Row 3 — IQ Recommendation (only shown when Layer 4 has flagged something):**
- Full-width, emerald-tinted background (#F0FDF4), rounded-lg, padding 10px 14px, 1px left border emerald
- Lightbulb icon (💡 or Lightbulb from Lucide, 16px, #10B981) + recommendation text (13px, #065F46):
  - Example: "Show rate is below 25% benchmark. Refresh pre-webinar emails to improve attendance."
- Right: [Apply Fix →] — emerald text button, bold, 13px. Hover: underline. Clicking this opens a confirmation: "Rebuild the pre-webinar email sequence (Step 4a)? This will use your current Voice DNA and latest performance data." [Rebuild →] [Cancel]

**Card states by engine status:**

| Status | Left Border | Row 2 | Row 3 | Actions Available |
|--------|-------------|-------|-------|-------------------|
| Running | Blue (#3B82F6) | Shows progress bar instead of metrics (overall % + "Building step 3 of 6...") | Hidden | View, Pause |
| Needs Review | Amber (#F59E0B) | Shows metadata | Hidden | View (primary CTA, emerald instead of gray), Approve All, Edit |
| Active | Emerald (#10B981) | Shows metadata + metrics | Shown if recommendation exists | View, Rerun, Optimize, Clone, ··· |
| Scheduled | Gray (#6B7280) | Shows metadata + next run date prominently | Hidden | View, Edit Schedule, Rerun Now, Clone, ··· |
| Draft | Gray dashed border | Shows "Blueprint ready — not yet built" | Hidden | View Blueprint, Start Building, Delete |
| Archived | No left border, gray background (#FAFBFC) | Shows metadata (no metrics) | Hidden | View, Unarchive, Delete |

**Running card — expanded detail:**
When an engine is Running, the card automatically expands to show each step:

```
┌──────────────────────────────────────────────────────────────────────────┐
│  🎥  Evergreen Webinar Funnel                         🔵 Running        │
│  ──────────────────────────────────────────────────────────────────────  │
│  Overall: ████████████░░░░░░░░ 58%  ·  Step 3 of 6  ·  ~28 min left   │
│                                                                          │
│  Steps:                                                                  │
│  ✅ 1. Lead Magnet        🧲  Quiz + results page           3 assets    │
│  ✅ 2. Funnel Pages       🔗  5 pages built                 5 assets    │
│  🔄 3. Webinar Script     🎥  Writing section 4 of 7...     ████░░ 57%  │
│  ⏳ 4. Email Sequences    ✉️  Waiting for step 3...         —           │
│  ⏳ 5. Ad Creatives       📢  Waiting for step 2... ✅ Ready —          │
│  ⏳ 6. Sales Script       📞  Waiting for step 3...         —           │
│                                                                          │
│  [View Step 1 Output] [View Step 2 Output] [Pause Engine]               │
└──────────────────────────────────────────────────────────────────────────┘
```

Step row styling:
- ✅ Complete steps: emerald checkmark (CheckCircle2 icon, 16px, #10B981) + step name (dark text) + builder icon + description (#6B7280) + asset count (emerald pill)
- 🔄 Active step: blue spinner (Loader2 icon, 16px, #3B82F6, spinning animation) + step name (dark text, bold) + progress description + mini progress bar (48px wide, blue fill)
- ⏳ Queued steps: gray clock (Clock icon, 16px, #9CA3AF) + step name (#9CA3AF text) + "Waiting for step N..." or "Ready" (if dependencies are met, waiting to start)
- Step rows: 8px vertical gap, 40px row height, left-aligned

---

## "RUNNING" TAB

Shows only engines currently executing. If no engines are running:

Centered, 400px max-width:
- Zap icon (40px, #9CA3AF) + "No engines running right now" (16px, bold, #1F2937) + "Start one from the Engine Library or ask IQ Claw." (13px, #6B7280) + [Browse Engine Library →] emerald text link

If engines are running: same expanded running card format as the "My Engines" tab but ONLY running engines are shown, each in full expanded view with per-step progress.

---

## "HISTORY" TAB

Shows all completed engine runs as a table.

**Filters row (above table):**
- Left: date range pills — [Today] [This Week] [This Month] [All Time] — pill-style toggle buttons. "All Time" active by default. Active: emerald bg, white text. Inactive: white bg, #E5E7EB border, #374151 text.
- Right: engine type dropdown — [All Engines ▾] — shadcn Select component, 200px wide. Options: All Engines, Webinar Funnel, Campaign Launch, Content Machine, Challenge, Lead Magnet, Conversion Stack, Email Machine, Paid Traffic, Podcast, Program, Custom.
- Right of dropdown: search input — "Search engines..." placeholder, Search icon, 240px wide.

**Table:**

| Column | Width | Content |
|--------|-------|---------|
| Status | 48px | Icon only: ✅ (emerald), ⚠️ (amber), 🔄 (blue), ❌ (red) |
| Engine | flex | Engine icon + name (bold) + step count subtitle ("6 steps") |
| Type | 140px | Template name or "Custom" in gray pill |
| Started | 160px | Date + time, 13px, #6B7280 |
| Duration | 100px | "1h 12m" or "18 min" |
| Assets | 80px | Count with emerald pill badge ("40") |
| Actions | 160px | [View] [Rerun] buttons, gray outlined, 12px text |

- Table styling: white bg, 1px border #E5E7EB on header row bottom. Alternating rows: white / #FAFBFC. Row height: 56px. Hover: #F3F4F6 background. 13px text throughout.
- Sort by Started (newest first) by default. Click any column header to sort.
- Pagination: 20 rows per page. [← Previous] [Page 1 of 3] [Next →] at bottom right.

**Expandable rows:** Click a row → expands to show per-step details (same format as the running card step list, but all steps show as ✅ complete with asset counts and [View Output] links).

---

## "ENGINE LIBRARY" TAB — Pre-Built Engine Templates

**Header section:**
- "Engine Library" — 20px, bold, #1F2937
- "Proven growth systems built from the frameworks that scaled nine-figure health brands. Pick one, customize it, and launch." — 14px, #6B7280
- Below: category filter pills — [All] [Funnels] [Content] [Conversion] [Ads] [Authority] — same pill toggle styling as History tab date filters.

**Template grid:** 3 columns on desktop (>1200px), 2 columns on tablet (768–1200px), 1 column on mobile. 16px gap between cards.

**Template card — exact spec:**

White card (#FFFFFF), border 1px #E5E7EB, rounded-xl (12px), padding 20px. Hover: border #10B981 (emerald), shadow (0 4px 12px rgba(0,0,0,0.08)), translateY(-2px) with 200ms ease transition.

```
┌─────────────────────────────────────────┐
│                                         │
│  🎥  Evergreen Webinar Funnel           │
│  (emoji 24px + name 16px bold #1F2937)  │
│                                         │
│  The flagship engine. Turns cold        │
│  traffic into booked consults through   │
│  an automated webinar that runs 24/7.   │
│  (13px, #6B7280, 3 lines max,          │
│   line-clamp-3)                         │
│                                         │
│  ┌─────────────────────────────────┐    │
│  │ 6 steps · 40+ assets · ~65 min │    │
│  └─────────────────────────────────┘    │
│  (12px, #6B7280, inside a #F8F9FA      │
│   rounded-md strip, padding 6px 10px)   │
│                                         │
│  Builders:                              │
│  🧲  🔗  🎥  ✉️  📢  📞              │
│  (Builder emojis in a row, 20px each,  │
│   8px gap. Each has a tooltip on hover  │
│   showing builder name.)                │
│                                         │
│  ──────────────────────────────────     │
│  (1px #E5E7EB divider)                  │
│                                         │
│  [Preview]              [Launch →]      │
│  (gray outlined,        (emerald bg,    │
│   left-aligned)          white text,    │
│                          right-aligned,  │
│                          bold)           │
│                                         │
└─────────────────────────────────────────┘
```

### The 10 Engine Templates (in display order):

**1. 🎥 Evergreen Webinar Funnel** — Category: Funnels
"The flagship engine. Turns cold traffic into booked consults through an automated webinar that runs 24/7."
6 steps · 40+ assets · ~65 min
Builders: 🧲 🔗 🎥 ✉️ 📢 📞

**2. 🚀 Full Campaign Launch** — Category: Content
"Coordinate a complete marketing push across all channels — content, email, ads, and funnel — all launching in sync."
6 steps · 35–60 assets · ~88 min
Builders: 📋 📝 ✉️ 📢 🔗

**3. 📅 Monthly Content Machine** — Category: Content
"Full month of strategic content across social, email, and ads. Auto-runs monthly. Never miss a beat."
4 steps · 27–39 assets · ~60 min
Builders: 📋 📝 ✉️ 📢

**4. 🏆 Challenge Funnel** — Category: Funnels
"5 to 21-day challenge that builds a warm audience and converts them into buyers at the finish line."
5 steps · 40–65 assets · ~83 min
Builders: 🏆 🔗 ✉️ 📝 📢

**5. 🧲 Lead Magnet Funnel** — Category: Funnels
"Complete lead capture system — valuable opt-in, nurture sequence, and bridge to your core offer."
5 steps · 28–32 assets · ~64 min
Builders: 🧲 🔗 ✉️ 📝 📢

**6. 📞 Sales Conversion Stack** — Category: Conversion
"Fix your conversion layer — webinar close, consult script, post-webinar emails, and order page optimization."
4 steps · 15+ assets · ~62 min
Builders: 🎥 📞 ✉️ 🔗

**7. ✉️ Email Machine** — Category: Conversion
"Build every automated email sequence your practice needs. Set it up once, it runs forever."
8 steps · 35–48 emails · ~73 min
Builders: ✉️

**8. 📢 Paid Traffic Engine** — Category: Ads
"Full paid advertising system — cold acquisition, 3-tier retargeting, scaling protocol, and media plan."
6 steps · 21 creatives + media plan · ~58 min
Builders: 📢 📋

**9. 🎙️ Podcast Launch** — Category: Authority
"Launch a podcast with episode scripts, promotion content, and a repurposing pipeline for multi-platform reach."
5 steps · 35+ assets · ~70 min
Builders: 🎙️ 📝 ✉️

**10. 🎓 Program & Course Builder** — Category: Authority
"Package your methodology into a digital program — curriculum, content, sales page, and launch webinar."
5 steps · 11+ major assets · ~82 min
Builders: 🎓 ✉️ 🔗 🎥

---

## ENGINE DETAIL VIEW — What Happens When You Click "View" or a Card

Clicking [View] on any engine card (or clicking the engine name) navigates to a detail page or expands a full-screen overlay.

**Route:** `/engines/[engine-id]`
**Layout:** Sidebar rail + full-width content

**Detail page structure:**

### Top bar:
- [← Back to Engines] gray text link with ChevronLeft icon, top-left
- Engine icon + name (24px, bold) + status badge + [Edit Name] pencil icon on hover
- Right: action buttons — [Rerun] [Optimize] [Clone] [Schedule] [···]

### Section 1 — Overview Card
White card, full-width, rounded-xl, padding 24px.

**Left column (60%):**
- "Business Objective" label (11px, uppercase, #6B7280, letter-spacing 0.05em) + objective text (16px, #1F2937)
- "Blueprint" label + visual step list (the blueprint the expert approved):

Each step as a compact row:
```
  ✅ │ 1 │ 🧲 Lead Magnet Builder │ Quiz + results page │ 3 assets │ [View →]
  ✅ │ 2 │ 🔗 Funnel Builder      │ 5 funnel pages      │ 5 assets │ [View →]
  ✅ │ 3 │ 🎥 Webinar Builder     │ Script + 47 slides  │ 2 assets │ [View →]
  ✅ │ 4 │ ✉️ Email Builder        │ 22 emails, 4 seqs   │22 assets │ [View →]
  ✅ │ 5 │ 📢 Ad Creative Builder  │ 9 creatives         │ 9 assets │ [View →]
  ✅ │ 6 │ 📞 Sales Script Builder │ Consult close script │ 1 asset  │ [View →]
```

Step row styling: 44px height, left-aligned, monospaced step number (16px, bold), builder icon, builder name (#374151), description (#6B7280), asset count (emerald pill), [View →] emerald text link.

Dependency lines: thin gray (#E5E7EB) vertical connector lines between sequential steps. Parallel steps shown at the same vertical level with a horizontal bracket connecting them.

**Right column (40%):**
- "Performance" label + the metric chips (same as card Row 2, but larger, stacked vertically):
  ```
  Opt-in rate        38%     🟢 Above benchmark (35%)
  Webinar show rate  22%     🟡 Below benchmark (25%)
  Conversion rate     9%     🟢 Above benchmark (8%)
  Cost per lead      $42     🟢 Below target ($50)
  ```
  Each row: metric name (13px, #6B7280), value (16px, bold, #1F2937), status dot + benchmark comparison (12px, colored text)
- If no performance data yet: "No performance data yet. Activate your engine assets to start tracking." in gray, centered.

### Section 2 — Assets Grid
White card, full-width, rounded-xl.

**Header:** "Assets" (18px, bold) + count pill ("40 assets") + view toggle [List | Grid] + filter dropdown [All Types | Pages | Emails | Ads | Scripts | Content]

**List view (default):** Table with columns: Type (icon), Name, Step, Status, Created, Actions ([Open] [Edit] [Delete])
**Grid view:** Thumbnail cards (4 columns) — each showing a preview (if renderable) or an icon + title. Click → opens the asset.

### Section 3 — Run History
White card, full-width, rounded-xl.

**Header:** "Run History" (18px, bold) + [Rerun Engine] emerald button

Table: Date, Trigger (Manual / Scheduled / Optimization), Duration, Steps Run, Status. Click to expand and see per-step details.

### Section 4 — Schedule (if engine has a schedule set)
White card, showing: cadence description ("Runs on the 25th of every month"), next run date, last run date, [Edit Schedule] [Pause Schedule] buttons.

---

## BLUEPRINT PREVIEW — Template Detail View

When the expert clicks [Preview] on a template card in the Engine Library, a **modal overlay** (not a page navigation) appears.

**Modal:** 680px wide, max-height 80vh, scrollable, white bg, rounded-2xl, shadow-xl. Backdrop: semi-transparent dark (#000 at 40% opacity).

**Modal content:**

**Header (sticky top):**
- Engine icon + name (20px, bold) + [×] close button top-right
- 1px #E5E7EB bottom border

**Body (scrollable):**

**Objective:** "Turns cold traffic into booked consults through an automated webinar that runs 24/7." (14px, #374151, in a #F8F9FA rounded-lg box with padding 12px)

**Steps preview:** Visual step list showing all steps with builder icons, names, descriptions, and dependency arrows. Same format as the engine detail blueprint section, but steps show ○ (empty circle, gray) status instead of ✅ since nothing has been built yet.

**What you'll get:** A summary box at the bottom:
- "This engine produces:" followed by a compact bulleted list:
  - 🧲 1 lead magnet (quiz, guide, or assessment)
  - 🔗 5 funnel pages (opt-in → thank you)
  - 🎥 1 webinar script + slide deck
  - ✉️ 22 emails across 4 sequences
  - 📢 9 ad creatives in 3 hook angles
  - 📞 1 consult close script
- "Estimated build time: ~65 minutes"
- "Everything is personalized to your voice, avatar, mechanism, and offers."

**Footer (sticky bottom):**
- 1px #E5E7EB top border, padding 16px 24px
- [Cancel] gray text button, left
- [Launch This Engine →] emerald button, right, bold. Clicking this navigates to `/iq` with a pre-seeded message: IQ Claw presents the personalized blueprint for this engine template.

---

## + NEW ENGINE FLOW

When the expert clicks [+ New Engine]:

**Option A (if on the /engines page):** Navigate to `/iq` with a pre-seeded IQ Claw message:
> "What do you want to build? Describe the business outcome you're after — not the pieces, the result. I'll design the engine and show you the blueprint before we build anything."

**Option B (if in the /iq workspace):** IQ Claw receives the routing and responds with the same message.

The blueprint that IQ creates appears as a **special chat message** — a structured card inside the chat (not plain text). The card shows the step list, dependencies, estimated time, and asset count. Below the card:
- [Start Building →] emerald button
- [Adjust Blueprint] gray outlined button → IQ says "What would you like to change?"
- [Save as Draft] gray text link → saves to My Engines as Draft status

---

## RELATIONSHIP TO OTHER SURFACES

### Builders tab (right panel in /iq):
Unchanged. Still shows 12 builder cards for single-asset work. Quick launch for "make me a post."

### + New flyout (sidebar):
Add a **"Growth Engines"** section at the TOP of the flyout (above the builders grid):
- Label: "Growth Engines" (11px, uppercase, #6B7280, letter-spacing 0.05em)
- 3 compact horizontal cards (the top 3 templates: Webinar Funnel, Monthly Content Machine, Lead Magnet Funnel):
  - Each: 64px tall, full flyout width, white bg, border, rounded-lg. Left: emoji (20px) + name (13px, bold). Right: "40+ assets" (11px, #6B7280) + [Launch →] emerald text (12px).
- Below: [View all engines →] emerald text link (13px)
- Then: 1px divider (#E5E7EB)
- Then: existing builders grid (unchanged)

### Home page (CEO dashboard):
Add an **"Active Engines"** widget card:
- White card, same style as other Home widgets
- Header: Zap icon + "Active Engines" + count
- List of active engines (max 3 shown): icon + name + status badge + top-level metric
- [View all →] link to /engines
- If an engine has an IQ recommendation: show a compact alert below the engine name

### Right panel in /iq — Engine Progress Tab:
When any engine is actively running, add a **temporary tab** to the right panel tab bar: ⚡ "Engine" — shows the same progress view as the Running card (step-by-step progress with percentage). This tab auto-appears when an engine starts and auto-disappears when it completes (replaced by a "Needs Review" notification in IQ Claw chat). This lets the expert monitor engine progress without leaving the IQ workspace.

---

## RESPONSIVE BEHAVIOR

### Desktop (>1200px):
Full layout as described.

### Tablet (768–1200px):
- Engine Library: 2-column grid
- Engine cards: same full-width layout but metric chips wrap to second line
- Blueprint modal: 90% viewport width

### Mobile (<768px):
- Engine Library: 1-column stack
- Engine cards: stack vertically, action buttons collapse into [···] menu
- Tabs: horizontally scrollable
- Blueprint modal: full-screen sheet (slides up from bottom)
- Empty state: stacked vertically, template mini-cards become full-width

---

## DATA STRUCTURES (for mock/demo data)

Use this mock data to populate the UI:

**Mock engines for "My Engines":**

```typescript
const mockEngines = [
  {
    id: "eng_1",
    name: "Evergreen Webinar Funnel",
    icon: "🎥",
    template: "webinar-funnel",
    status: "active", // active | running | needs-review | scheduled | draft | archived
    stepsTotal: 6,
    stepsComplete: 6,
    assetsTotal: 40,
    lastRun: "2026-04-01T08:00:00Z",
    nextRun: "2026-05-01T08:00:00Z",
    scheduled: true,
    performance: {
      optinRate: { value: 38, benchmark: 35, status: "green" },
      showRate: { value: 22, benchmark: 25, status: "amber" },
      conversionRate: { value: 9, benchmark: 8, status: "green" },
      cac: { value: 42, target: 50, status: "green" },
    },
    recommendation: {
      text: "Show rate is below 25% benchmark. Refresh pre-webinar emails to improve attendance.",
      action: "Rebuild Step 4a (pre-webinar email sequence)",
      stepId: "4a",
    },
    steps: [
      { id: "1", name: "Lead Magnet", builder: "Lead Magnet Builder", icon: "🧲", status: "complete", assets: 3, description: "Cortisol Assessment Quiz" },
      { id: "2", name: "Funnel Pages", builder: "Funnel Builder", icon: "🔗", status: "complete", assets: 5, description: "Opt-in → Thank You flow" },
      { id: "3", name: "Webinar Script", builder: "Webinar Builder", icon: "🎥", status: "complete", assets: 2, description: "Perfect Webinar + 47 slides" },
      { id: "4", name: "Email Sequences", builder: "Email Builder", icon: "✉️", status: "complete", assets: 22, description: "4 sequences, 22 emails" },
      { id: "5", name: "Ad Creatives", builder: "Ad Creative Builder", icon: "📢", status: "complete", assets: 9, description: "3 angles × 3 formats" },
      { id: "6", name: "Sales Script", builder: "Sales Script Builder", icon: "📞", status: "complete", assets: 1, description: "Consult close script" },
    ],
  },
  {
    id: "eng_2",
    name: "Monthly Content — April",
    icon: "📅",
    template: "monthly-content",
    status: "running",
    stepsTotal: 4,
    stepsComplete: 1,
    assetsTotal: null,
    lastRun: null,
    nextRun: null,
    scheduled: false,
    performance: null,
    recommendation: null,
    steps: [
      { id: "1", name: "Strategy Refresh", builder: "Strategy", icon: "📋", status: "complete", assets: 1, description: "Updated messaging brief" },
      { id: "2", name: "Content Batch", builder: "Content Builder", icon: "📝", status: "running", assets: null, description: "Generating 24 posts...", progress: 42 },
      { id: "3", name: "Email Broadcasts", builder: "Email Builder", icon: "✉️", status: "queued", assets: null, description: "Waiting for step 2" },
      { id: "4", name: "Ad Refresh", builder: "Ad Creative Builder", icon: "📢", status: "queued", assets: null, description: "Waiting for step 1 ✅ Ready" },
    ],
  },
  {
    id: "eng_3",
    name: "Lead Magnet Funnel",
    icon: "🧲",
    template: "lead-magnet",
    status: "needs-review",
    stepsTotal: 5,
    stepsComplete: 5,
    assetsTotal: 30,
    lastRun: "2026-04-06T14:30:00Z",
    nextRun: null,
    scheduled: false,
    performance: null,
    recommendation: null,
    steps: [
      { id: "1", name: "Lead Magnet", builder: "Lead Magnet Builder", icon: "🧲", status: "complete", assets: 1, description: "Hormone Health Score Calculator" },
      { id: "2", name: "Funnel Pages", builder: "Funnel Builder", icon: "🔗", status: "complete", assets: 3, description: "Opt-in + Thank You + Results" },
      { id: "3", name: "Email Sequence", builder: "Email Builder", icon: "✉️", status: "complete", assets: 8, description: "5 nurture + 3 SMS" },
      { id: "4", name: "Promo Content", builder: "Content Builder", icon: "📝", status: "complete", assets: 10, description: "10 social posts" },
      { id: "5", name: "Ad Creatives", builder: "Ad Creative Builder", icon: "📢", status: "complete", assets: 6, description: "3 angles × 2 formats" },
    ],
  },
];
```

**Mock history:**

```typescript
const mockHistory = [
  { id: "run_1", engineName: "Evergreen Webinar Funnel", icon: "🎥", type: "Webinar Funnel", started: "2026-04-01T08:00:00Z", duration: "1h 12m", assets: 40, status: "complete", trigger: "Scheduled" },
  { id: "run_2", engineName: "Monthly Content — March", icon: "📅", type: "Content Machine", started: "2026-03-25T08:00:00Z", duration: "58 min", assets: 33, status: "complete", trigger: "Scheduled" },
  { id: "run_3", engineName: "Email Machine", icon: "✉️", type: "Email Machine", started: "2026-03-15T10:00:00Z", duration: "1h 22m", assets: 42, status: "complete", trigger: "Manual" },
  { id: "run_4", engineName: "Ad Refresh — Q1", icon: "📢", type: "Custom", started: "2026-03-10T14:00:00Z", duration: "32 min", assets: 12, status: "complete", trigger: "Manual" },
  { id: "run_5", engineName: "Lead Magnet Funnel v1", icon: "🧲", type: "Lead Magnet", started: "2026-03-01T11:00:00Z", duration: "1h 04m", assets: 28, status: "partial", trigger: "Manual" },
];
```

---

## DESIGN SYSTEM REFERENCE (must match existing platform)

- **Theme:** Light mode only
- **Colors:** Black #1F2937, white #FFFFFF, grays (#F8F9FA bg, #E5E7EB borders, #6B7280 secondary, #9CA3AF disabled). Emerald #10B981 for primary CTAs, active states, positive. Red #EF4444 alerts. Amber #F59E0B warnings. Blue #3B82F6 for running/progress states. Green #22C55E for confirmed positive.
- **Typography:** Inter. Headings bold. Body regular. Small text 12–13px. Body 14px. Subheadings 16px. Headings 20–24px.
- **Cards:** White bg, 1px border #E5E7EB, rounded-xl (12px), padding 20–24px. Hover: darker border + subtle shadow.
- **Buttons:** Primary: emerald bg, white text, rounded-lg, bold. Secondary: white bg, #E5E7EB border, #374151 text. Danger: red text. Text buttons: colored text, no bg/border, hover underline.
- **Badges/Pills:** rounded-full, small text, colored bg + colored text per status.
- **Icons:** Lucide React, 16–24px, matching context color.
- **Transitions:** 200ms ease on hover/focus states. Progress bars: 500ms ease transition on width changes. Pulse dots: infinite opacity animation (0.4→1→0.4, 2s).
- **Spacing:** 8px base unit. 16px standard gap. 24px section padding.

---

## ACCESSIBILITY

- All interactive elements have focus-visible outlines (2px emerald, 2px offset)
- Status communicated via text labels + color (never color alone — the dot PLUS the text benchmark comparison)
- Tab navigation works across all tabs, cards, and buttons
- Modal traps focus and closes on Escape
- Screen reader: engine status announced, step progress announced

---

## BUILD ORDER (recommended implementation sequence)

1. **Page shell** — route, sidebar update (Zap icon + "Engines"), top bar, tab bar
2. **Engine Library tab** — template cards with all 10 engines, category filters, preview modal
3. **My Engines tab** — engine cards (active state), with mock data
4. **Running state** — expanded running card with per-step progress
5. **Empty state** — for new users
6. **History tab** — table with filters and expandable rows
7. **Engine detail page** — overview, assets grid, run history, schedule
8. **+ New Engine flow** — navigation to /iq with pre-seeded message
9. **+ New flyout update** — add Growth Engines section
10. **Right panel engine progress tab** — temporary ⚡ tab during running engines
11. **Home page widget** — Active Engines card
12. **Responsive** — tablet + mobile layouts

---

*This spec produces a complete, functional Growth Engines page matching the quality standard of the existing ClinicIQ onboarding and IQ workspace screens. Every component, color, spacing, and interaction is defined. No ambiguity.*
