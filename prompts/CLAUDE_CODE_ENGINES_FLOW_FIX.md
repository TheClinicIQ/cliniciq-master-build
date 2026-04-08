# ClinicIQ — Growth Engines Flow Fix
## Change: Engine creation stays on /engines. IQ conversation happens inline.

---

## THE PROBLEM

Currently, clicking [Launch →] on an engine template or [+ New Engine] navigates to `/iq`. This breaks the experience — the user leaves the Engines page, loses context, and has to navigate back to see their engine. 

## THE FIX

**All engine creation stays on `/engines`.** When the user launches a template or creates a new engine, it immediately appears on "My Engines" in Draft status. The user builds it out by opening an inline IQ conversation from the engine card — never leaving the page.

---

## CHANGE 1: [Launch →] on Engine Library Template

**Old behavior:** Navigate to `/iq` with pre-seeded message.

**New behavior:**

1. User clicks [Launch →] on a template (e.g., Challenge Funnel)
2. Engine is instantly created and added to "My Engines" as **Draft** status
3. Tab automatically switches from "Engine Library" to "My Engines"
4. The new engine card appears at the top with a subtle entrance animation (fade-in + slide-down, 300ms ease)
5. The card is in **Draft state** with a prominent CTA to start building (see Change 3 below)
6. A brief toast notification appears: "Challenge Funnel added to your engines" (emerald bg, white text, auto-dismiss after 3s)

## CHANGE 2: [+ New Engine] Button

**Old behavior:** Navigate to `/iq` with pre-seeded message.

**New behavior:**

1. User clicks [+ New Engine]
2. A **creation modal** appears (480px wide, white bg, rounded-2xl, shadow-xl):

```
┌─────────────────────────────────────────────┐
│  ⚡ New Growth Engine                    [×] │
│  ───────────────────────────────────────── │
│                                             │
│  Engine name:                               │
│  ┌────────────────────────────────────────┐ │
│  │  My Custom Engine                      │ │
│  └────────────────────────────────────────┘ │
│  (Input, border #E5E7EB, placeholder:       │
│   "e.g., Black Friday Campaign")            │
│                                             │
│  What's the goal?                           │
│  ┌────────────────────────────────────────┐ │
│  │  Describe the business outcome you     │ │
│  │  want — IQ will design the blueprint.  │ │
│  │                                        │ │
│  │                                        │ │
│  └────────────────────────────────────────┘ │
│  (Textarea, 4 rows, border #E5E7EB,        │
│   placeholder text in #9CA3AF)              │
│                                             │
│  ── or start from a template ──             │
│  (12px, #9CA3AF, centered, divider lines)   │
│                                             │
│  [Browse Engine Library →]                  │
│  (emerald text link — switches to           │
│   Engine Library tab and closes modal)      │
│                                             │
│  ─────────────────────────────────────────  │
│  [Cancel]                  [Create Engine]  │
│  (gray text)              (emerald button)  │
└─────────────────────────────────────────────┘
```

3. User fills in name + goal description → clicks [Create Engine]
4. Engine is created in Draft status on "My Engines" with the goal stored
5. Modal closes, card appears at top with entrance animation
6. Same toast: "Engine created — open it to start building with IQ"

## CHANGE 3: Draft Engine Card — The "Build with IQ" CTA

When an engine is in **Draft** status, the card looks different from active engines. It needs a clear, prominent, single-action CTA that opens the inline IQ conversation.

**Draft engine card layout:**

```
┌──────────────────────────────────────────────────────────────────────────┐
│  🏆  Challenge Funnel                                    ✏️ Draft       │
│  ──────────────────────────────────────────────────────────────────────  │
│                                                                          │
│  5 steps · 40–65 assets · ~83 min                                       │
│  (13px, #6B7280 — pulled from the template metadata)                    │
│                                                                          │
│  Builders: 🏆 🔗 ✉️ 📝 📢                                              │
│  (20px emojis, 8px gap)                                                  │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────────────┐  │
│  │                                                                    │  │
│  │   Your engine blueprint is ready to customize.                     │  │
│  │   IQ will walk you through each step — your voice, avatar,         │  │
│  │   offers, and strategy — then build everything.                    │  │
│  │                                                                    │  │
│  │                    [Build with IQ →]                                │  │
│  │                    (emerald button, bold, centered,                 │  │
│  │                     16px text, padding 12px 32px,                  │  │
│  │                     rounded-lg, full-width max 280px)              │  │
│  │                                                                    │  │
│  └────────────────────────────────────────────────────────────────────┘  │
│  (Inner box: #F0FDF4 bg, 1px emerald border, rounded-xl,               │
│   padding 20px, text center-aligned, 14px #065F46)                      │
│                                                                          │
│  [Rename] [Delete]                                                       │
│  (small gray text links, bottom-right, 12px)                             │
└──────────────────────────────────────────────────────────────────────────┘
```

**For custom engines (created via + New Engine with a goal description):**
Same card, but instead of template metadata, show the goal the user typed:
- "Goal: Build a Black Friday flash sale campaign with countdown emails and social posts"
- (14px, #374151, in a #F8F9FA rounded-md box)

## CHANGE 4: "Build with IQ" → Inline Engine Builder

When the user clicks **[Build with IQ →]** on a draft engine card:

**The `/engines` page transforms into a two-panel layout:**

```
┌─────────────────────────────┬────────────────────────────────────────────┐
│                             │                                            │
│   ENGINE BLUEPRINT          │           IQ CLAW CHAT                     │
│   (left panel, 45%)         │           (right panel, 55%)               │
│                             │                                            │
│   🏆 Challenge Funnel       │   IQ: "Let's build your Challenge         │
│   Status: Building...       │   Funnel. I've got the blueprint           │
│                             │   ready — 5 steps, starting with           │
│   Steps:                    │   the challenge architecture.              │
│   🔄 1. Challenge Arch.    │                                            │
│   ○  2. Funnel Pages       │   First — which avatar are we              │
│   ○  3. Email Sequence     │   targeting? I see you have                 │
│   ○  4. Promo Content      │   Stressed Mom Sarah as your               │
│   ○  5. Ad Creatives       │   primary. Want to build this              │
│   ──────────────────        │   challenge for her?"                      │
│   Progress: ██░░░ 0%        │                                            │
│   Est. ~83 min              │   [Chat input bar at bottom]               │
│                             │                                            │
│   ┌──────────────────────┐  │                                            │
│   │ What we're building: │  │                                            │
│   │ • Challenge arch.    │  │                                            │
│   │ • 3+ funnel pages    │  │                                            │
│   │ • 12–30 emails       │  │                                            │
│   │ • 15–22 social posts │  │                                            │
│   │ • 6 ad creatives     │  │                                            │
│   └──────────────────────┘  │                                            │
│   (#F8F9FA bg, 12px text)   │                                            │
│                             │                                            │
│   [← Back to Engines]      │                                            │
│   (gray text link, bottom)  │                                            │
│                             │                                            │
└─────────────────────────────┴────────────────────────────────────────────┘
```

**Left Panel — Blueprint Tracker (45% width):**
- White background, right border 1px #E5E7EB
- Top: Engine icon + name (18px, bold) + status badge
- Step list (same format as the running engine card):
  - Status icons: ○ not started (gray), 🔄 building (blue spinner), ✅ complete (emerald check)
  - Each step: icon + name + builder name (12px, #6B7280)
  - Completed steps get a [View →] link
  - Active step highlighted with a light blue (#EFF6FF) background row
- Below steps: overall progress bar + estimated time
- Below that: "What we're building" summary box (#F8F9FA bg, rounded-lg, compact bulleted list of deliverables)
- Bottom: [← Back to Engines] gray text link with ChevronLeft icon — returns to My Engines (engine remains in whatever state it's in)

**Right Panel — IQ Claw Chat (55% width):**
- Same chat UI as the `/iq` workspace center panel — same emerald avatar, same "IQ Claw" header, same message bubbles, same input bar
- This is a full IQ Claw conversation scoped to this engine
- IQ Claw speaks first (never empty): personalizes the template to the expert's dossier, confirms avatar/offer/mechanism choices, then starts building step by step
- As IQ completes each step, the left panel updates in real-time (step status changes, progress bar advances, asset counts populate)
- Expert can review completed step outputs by clicking [View →] on the left panel — output appears as a card in the chat or replaces the left panel temporarily

**Route:** This view lives at `/engines/[engine-id]/build` — or use a state-based approach where the `/engines` page itself renders the two-panel layout when an engine is in active build mode. Either approach is fine — keep it consistent with existing routing patterns.

**Navigation:** The sidebar "Engines" item stays active. The page title in the top bar updates to show the engine name: "Growth Engines → Challenge Funnel" as a breadcrumb.

**When the build completes:**
- Left panel shows all steps ✅ with asset counts
- Progress bar at 100%
- IQ Claw delivers the completion message in chat
- Below the step list, two buttons appear:
  - [Review All Assets →] emerald button — opens the engine detail view
  - [Back to My Engines →] gray outlined button — returns to the list

**Engine status changes:** Draft → Building (while IQ conversation is active) → Needs Review (when all steps complete) → Active (when expert approves)

## CHANGE 5: [Preview Blueprint] on Engine Library

**Old behavior:** Opens a modal showing the template blueprint.

**New behavior:** Keep the modal exactly as specced — no change. The modal still has two buttons at the bottom:
- [Cancel] — closes modal
- [Add to My Engines →] — (renamed from "Launch This Engine →") creates the draft engine and switches to My Engines tab. Same behavior as Change 1.

## CHANGE 6: Update the + New Flyout

The compact engine cards in the + New flyout sidebar:

**Old behavior:** [Launch →] navigates to `/iq`

**New behavior:** [Launch →] navigates to `/engines` → creates the engine as Draft → shows on My Engines tab. Same behavior as Change 1, but from the flyout.

---

## SUMMARY OF FLOW

```
User clicks [Launch →] on template
  → Engine created as Draft on My Engines
  → Card appears with [Build with IQ →] CTA

User clicks [+ New Engine]
  → Modal: name + goal → [Create Engine]
  → Engine created as Draft on My Engines
  → Card appears with [Build with IQ →] CTA

User clicks [Build with IQ →] on draft card
  → Page transforms to two-panel: Blueprint (left) + IQ Chat (right)
  → IQ walks through the build step by step
  → Left panel updates in real-time as steps complete
  → On completion: engine moves to Needs Review
  → User reviews and approves → engine moves to Active

User clicks [← Back to Engines] during build
  → Returns to My Engines list
  → Engine stays in Building state
  → Can return to it anytime by clicking [Continue Build →] on the card
```

**The key insight:** The user never leaves `/engines`. The IQ conversation comes to them, embedded in the engine build experience. The engine is always visible, progress is always tracked, and the expert always knows where they are.

---

## ADDITIONAL CARD STATE: "Building" (in-progress but user navigated away)

When the user clicks [← Back to Engines] while a build is in progress, the card on My Engines shows:

```
┌──────────────────────────────────────────────────────────────────────────┐
│  🏆  Challenge Funnel                              🔵 Building          │
│  ──────────────────────────────────────────────────────────────────────  │
│  Step 2 of 5 · 1 step complete · ~68 min remaining                      │
│  ████████░░░░░░░░░░░░ 20%                                               │
│                                                                          │
│                     [Continue Build →]                                    │
│                     (emerald button, bold, centered,                     │
│                      same style as "Build with IQ →")                    │
│                                                                          │
│  [Pause] [Discard]                                                       │
│  (small gray text links, bottom-right, 12px)                             │
└──────────────────────────────────────────────────────────────────────────┘
```

[Continue Build →] takes them back to the two-panel build view, resuming the IQ conversation where they left off.
