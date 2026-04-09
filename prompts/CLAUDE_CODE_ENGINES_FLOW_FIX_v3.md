# ClinicIQ — Growth Engines Flow Fix v3
## The right panel tab bar NEVER disappears. Engine build is a tab, not a replacement.

This prompt supersedes CLAUDE_CODE_ENGINES_FLOW_FIX_v2. That prompt incorrectly told you to hide the right panel tab bar and replace it with the engine build view. That was wrong.

---

## THE RULE

The three-panel layout is PERMANENT. Nothing ever removes, hides, or replaces any part of it:

```
┌────────┬──────────────────────┬─────────────────────────┐
│        │                      │  Tab bar (ALWAYS HERE)  │
│ Side-  │                      │  Dashboard | Brand |    │
│ bar    │    IQ Claw Chat      │  Strategy | Builders |  │
│ Rail   │    (ALWAYS HERE)     │  Content | Calendar |   │
│        │    (CENTER)          │  Channels | Services |  │
│ 72px   │                      │  Training | Settings   │
│        │    Never moves.      │                         │
│ALWAYS  │    Never changes.    │  Tab content below.     │
│HERE    │    Never hides.      │  TABS NEVER HIDE.       │
│        │                      │  TABS NEVER DISAPPEAR.  │
└────────┴──────────────────────┴─────────────────────────┘
```

- The **left sidebar** is always there with all navigation items
- The **center chat** is always IQ Claw — always in the center, never moves
- The **right panel** always has the tab bar at the top — Dashboard, Brand, Strategy, Builders, Content, Calendar, Channels, Services, Training, Settings — those tabs are ALWAYS visible, ALWAYS clickable, NEVER hidden

---

## HOW ENGINE BUILD WORKS WITH THE TABS

When the user clicks [Build with IQ →] from the engines page:

### Center Chat:
IQ Claw sends the first message — excited, specific, leading the user through what's about to happen:

> "Let's build your Challenge Funnel! Here's what we're going to create together:
>
> **Step 1** — Challenge Architecture — I'll design the full challenge: theme, daily topics, daily deliverables, and the transformation arc from Day 1 to the finish line
> **Step 2** — Funnel Pages — Registration page, daily challenge pages, and the graduation page that bridges to your offer
> **Step 3** — Email Sequence — Welcome email, daily challenge emails, post-challenge bridge to your core offer, and a re-engagement sequence for non-completers
> **Step 4** — Promo Content — 15–22 social posts for pre-launch, during the challenge, and post-challenge
> **Step 5** — Registration Ads — 6 ad creatives across 3 hook angles to drive signups
>
> First up: the challenge architecture. I'm targeting Stressed Mom Sarah as the avatar and your Signal Reset Protocol as the mechanism. Sound right, or do you want to adjust before we start?"

IQ then leads the conversation step by step. After each step completes, IQ tells the user what was built and what's next:

> "Step 1 is done — your challenge architecture is locked. 7-day Cortisol Reset Challenge, daily topics mapped, transformation arc built. You can review it in the Builders tab on the right.
>
> Moving to Step 2 — building your funnel pages now. I'll have the registration page, daily pages, and graduation page ready in about 18 minutes."

### Right Panel:
The tab bar stays exactly as it always is. **Add one new tab** to the tab bar:

**⚡ Engine** — this tab appears at the END of the tab row (after Settings) when an engine is actively being built. It auto-activates (becomes the selected tab) when the user arrives from "Build with IQ."

The ⚡ Engine tab content shows the engine build progress:

**Tab content layout:**

**Header:**
- Engine icon + name (16px, bold) — "🏆 Challenge Funnel"
- Status badge: "Building" (blue pill)

**Progress:**
- Progress bar (full-width, 6px, emerald fill, gray track)
- "Step 2 of 5 · ~68 min remaining" (13px, #6B7280)

**Step list:**
```
  ✅  Challenge Architecture      🏆  3 assets    [View →]
  🔄  Funnel Pages               🔗  Building...   ████░░ 40%
  ○   Email Sequence             ✉️  Waiting for step 2
  ○   Promo Content              📝  Waiting for step 2
  ○   Registration Ads           📢  Waiting for step 2
```

Same step styling as previously defined:
- ✅ Complete: emerald check + dark text + asset count pill + [View →] link
- 🔄 Active: blue spinner + bold text + mini progress bar
- ○ Queued: gray circle + gray text + "Waiting for step N"

**Deliverables summary:**
- "DELIVERABLES" label (11px, uppercase, #6B7280)
- Bulleted list of what the engine will produce

**Bottom:**
- [Back to Engines →] link — navigates to /engines page

**When no engine is building:**
The ⚡ Engine tab disappears from the tab bar entirely. It only exists while an engine is actively in Building state.

### The Expert Can Switch Tabs Freely

While an engine is building:
- The user can click **Dashboard** to check metrics
- Click **Brand** to review their Voice DNA
- Click **Strategy** to see their Monthly Master Plan
- Click **Content** to browse their content library
- Click **⚡ Engine** to check build progress
- The build continues in the background regardless of which tab is active
- IQ Claw continues narrating progress in the center chat no matter which tab is selected

**This is the key:** The engine build doesn't lock the user into anything. They use the platform normally. The ⚡ Engine tab is just one more tab they can check whenever they want. IQ keeps them updated in the chat.

---

## REMOVE THE OLD ENGINE BUILD VIEW

Delete the following from the previous implementation:
- Any layout that hides or replaces the right panel tab bar
- Any full-panel takeover of the right panel for engine building
- Any "overlay" or "temporary replacement" of the tabbed dashboard
- The notification banner that said "Challenge Funnel is building — [Open →]" — not needed because the ⚡ Engine tab is right there in the tab bar

---

## VIEWING COMPLETED STEP OUTPUT

When the user clicks [View →] on a completed step in the ⚡ Engine tab:

**Option A (preferred):** The relevant content appears in the appropriate existing tab. For example:
- Clicking [View →] on the funnel pages step → switches to the Content tab showing the funnel page assets
- Clicking [View →] on the email sequence step → switches to the Content tab filtered to emails

**Option B (simpler to implement):** The ⚡ Engine tab content scrolls down to show an expanded asset list for that step, inline below the step list. Clicking [← Back to steps] scrolls back up.

Either approach works. The key constraint: the tab bar never disappears.

---

## WHEN THE BUILD COMPLETES

1. ⚡ Engine tab shows all steps ✅, progress at 100%
2. Status changes to "Ready for Review" (amber badge)
3. IQ Claw sends completion message in chat:
   > "Your Challenge Funnel is complete! Here's what's ready: 1 challenge architecture, 3 funnel pages, 22 emails, 18 social posts, and 6 ad creatives. Everything is saved to Drive. Want to review anything or activate the engine?"
4. The ⚡ Engine tab stays until the user approves the engine (clicks [Approve & Activate] at the bottom of the tab), then it disappears and the engine moves to Active on the /engines page

---

## IQ CLAW FIRST MESSAGE — NO WELCOME SCREEN

Per CLAUDE_CODE_IQ_CHAT_FIX.md (which should already be applied): the center chat NEVER shows a welcome/splash screen. IQ always sends a real first message.

- **Normal visit to /iq:** Morning briefing / status update (the Dr. Chen message)
- **Arriving from Build with IQ:** Engine-specific first message (the "Let's build your Challenge Funnel!" message above)
- **Never:** "What can I help you build?" splash with suggestion cards

---

## SUMMARY

1. **Tab bar never hides.** Dashboard, Brand, Strategy, Builders, Content, Calendar, Channels, Services, Training, Settings — always visible, always clickable.
2. **⚡ Engine tab** is added to the end of the tab row when an engine is building. Auto-selected on arrival from Build with IQ.
3. **Tab disappears** when no engine is actively building.
4. **User can switch tabs freely** during a build — checking Dashboard, Brand, whatever. Build continues in background. IQ narrates in chat.
5. **IQ leads the conversation** — excited, step by step, tells the user what's happening and what's next.
6. **Delete any layout** that hides, replaces, or overlays the tab bar.
