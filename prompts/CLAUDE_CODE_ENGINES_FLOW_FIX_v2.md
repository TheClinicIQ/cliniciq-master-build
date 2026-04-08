# ClinicIQ — Growth Engines Flow Fix v2
## Fix: Remove the custom split-panel build view. Use the standard Genspark 3-panel layout.

---

## THE PROBLEM

The current "Build with IQ" flow creates a custom two-panel layout on the `/engines` page with the blueprint on the left and IQ chat on the right. This breaks the platform's core layout pattern. ClinicIQ uses the standard Genspark 3-panel layout everywhere: **sidebar (left) → IQ Claw chat (center) → context panel (right).** The chat must always stay in the center panel. It should never move.

## THE FIX

**Delete the custom two-panel build view entirely.** When the user starts building an engine, navigate to the standard `/iq` workspace. The IQ Claw chat stays in its normal center position. The engine blueprint and progress tracker appear in the **right panel** as a dedicated view — same position where Dashboard, Brand, Strategy tabs normally live.

---

## CHANGE 1: Remove the Custom Build Layout

Delete the two-panel split view that currently renders when "Build with IQ" is clicked (the layout with blueprint on left, chat on right). This component should not exist. The build experience uses the existing `/iq` workspace layout — no new layout needed.

---

## CHANGE 2: "Build with IQ →" Button Behavior

When the user clicks **[Build with IQ →]** on a draft engine card on the `/engines` page:

1. Engine status changes from "Draft" to "Building"
2. Navigate to `/iq` (the standard IQ Claw workspace)
3. The **right panel** automatically switches to the **Engine Build view** (described below) — replacing whatever tab was previously active
4. IQ Claw sends the first message in the **center chat panel** (its normal position):
   > "Let's build your Challenge Funnel. I've got the blueprint ready — 5 steps, starting with the challenge architecture. Which avatar are we targeting? I see Stressed Mom Sarah as your primary. Want to build this for her?"
5. The conversation proceeds normally in the center chat — expert types responses, IQ responds, builders execute

---

## CHANGE 3: Right Panel — Engine Build View

When an engine is being built, the right panel shows a dedicated **Engine Build view**. This is not a new tab in the tab bar — it's a temporary overlay that replaces the tabbed dashboard while the engine is actively building. When the build completes (or the user dismisses it), the normal tabbed dashboard returns.

**Right panel layout during engine build:**

**Header (sticky top):**
- Engine icon + engine name (16px, bold, #1F2937)
- Status badge: "Building" (blue bg #EFF6FF, blue text #1E40AF, rounded-full pill)
- [× Close] button (top-right) — closes the build view, returns to normal right panel tabs. Engine continues building in the background.

**Overall progress:**
- Progress bar: full-width, 6px height, rounded-full. Gray track (#E5E7EB), emerald fill (#10B981). Animates smoothly.
- Below bar: "Step 2 of 5 · ~68 min remaining" (13px, #6B7280)

**Step list:**
Each step as a row, stacked vertically, 8px gap:

```
  ✅  Challenge Architecture      🏆  3 assets    [View →]
  🔄  Funnel Pages               🔗  Building...   ████░░ 40%
  ○   Email Sequence             ✉️  Waiting for step 2
  ○   Promo Content              📝  Waiting for step 2
  ○   Registration Ads           📢  Waiting for step 2
```

Step row styling (same as previously specced):
- ✅ Complete: emerald CheckCircle2 icon (16px) + name (#1F2937) + builder icon + asset count (emerald pill) + [View →] emerald text link
- 🔄 Active: blue Loader2 icon (16px, spinning) + name (#1F2937, bold) + builder icon + "Building..." + mini progress bar (48px, blue)
- ○ Queued: gray circle (16px) + name (#9CA3AF) + builder icon + "Waiting for step N"

Step rows: 40px height, padding 8px 16px, rounded-lg. Active step has light blue background (#EFF6FF).

**Divider** (1px, #E5E7EB, 16px margin top/bottom)

**"What We're Building" summary:**
Compact box, #F8F9FA background, rounded-lg, padding 12px 16px:
- Header: "DELIVERABLES" (11px, uppercase, #6B7280, letter-spacing 0.05em)
- Bulleted list (12px, #374151):
  - 🏆 1 challenge architecture
  - 🔗 3+ funnel pages
  - ✉️ 12–30 emails
  - 📝 15–22 social posts
  - 📢 6 ad creatives

**Bottom (sticky):**
- [Back to Engines →] gray text link (13px, #6B7280, ChevronRight icon) — navigates to `/engines` page. The engine card there shows "Building" status with a [Continue Build →] button.

---

## CHANGE 4: Viewing Completed Step Output

When the user clicks **[View →]** on a completed step in the right panel:

The right panel replaces the step list with the **step output view** — showing the assets that step produced. This is the same pattern the right panel already uses when showing content previews during a builder run.

**Step output view header:**
- [← Back to Blueprint] gray text link (returns to the step list)
- Step icon + step name (16px, bold)
- Asset count pill

**Step output body:**
- List or grid of assets produced by that step (same format as the Content tab or asset previews elsewhere in the right panel)

---

## CHANGE 5: Build Completion

When all steps are complete:

1. Right panel shows all steps as ✅ with asset counts
2. Progress bar at 100%, emerald fill
3. Status badge changes to "Ready for Review" (amber bg, amber text)
4. Two buttons appear at the bottom of the right panel:
   - [Review All Assets →] emerald button — opens the engine detail view at `/engines/[id]`
   - [Approve & Activate] emerald outlined button — marks engine as Active
5. IQ Claw sends a completion message in the center chat:
   > "Your Challenge Funnel is complete. 5 steps done — here's what's ready: [summary]. Everything is saved to IQ Drive. Want to review the assets or go straight to activating?"

---

## CHANGE 6: Returning to an In-Progress Build

If the user navigates away from `/iq` while an engine is building (e.g., clicks Home, Engines, or Drive in the sidebar):

**On the `/engines` page**, the engine card shows "Building" status with a **[Continue Build →]** button. Clicking it navigates back to `/iq` and restores the Engine Build view in the right panel + the IQ conversation resumes in the center chat.

**On the `/iq` page**, if the user closes the Engine Build view (clicks [× Close] on the right panel), the normal tabbed dashboard returns. A small **notification banner** appears at the top of the right panel:
- "🔄 Challenge Funnel is building (Step 3 of 5)" — 12px, #374151, #EFF6FF background, rounded-lg, padding 8px 12px
- [Open →] emerald text link — restores the Engine Build view in the right panel

---

## CHANGE 7: Right Panel Tab Bar Behavior

When the Engine Build view is active in the right panel:
- The normal tab bar (Dashboard, Brand, Strategy, etc.) is **hidden** — replaced by the engine build header
- This is the same pattern used during onboarding (where the right panel shows the progress card instead of tabs)
- When the build completes or the user closes the build view, the tab bar returns

---

## SUMMARY

The rule is simple: **the chat never moves.** IQ Claw always lives in the center panel. The right panel is the chameleon — it shows whatever context is relevant: dashboard tabs normally, onboarding progress during onboarding, engine blueprint during an engine build. This is the established Genspark pattern. No custom layouts.

```
STANDARD LAYOUT (always):
┌────────┬──────────────────────┬─────────────────────────┐
│        │                      │                         │
│ Side-  │    IQ Claw Chat      │   Right Panel           │
│ bar    │    (ALWAYS HERE)     │   (changes context)     │
│ Rail   │                      │                         │
│        │                      │   During normal use:    │
│ 72px   │    Center panel      │   Tabbed dashboard      │
│        │    Never moves       │                         │
│        │                      │   During engine build:  │
│        │                      │   Blueprint + progress  │
│        │                      │                         │
│        │                      │   During onboarding:    │
│        │                      │   Progress card         │
│        │                      │                         │
└────────┴──────────────────────┴─────────────────────────┘
```
