# ClinicIQ — Onboarding Rewrite for Claude Code
## Rebuild onboarding from 103 questions to 22 questions across 6 sections. AI expands between sections. Expert approves. First engine builds during onboarding.

---

## READ FIRST

Before making any changes, read these files to understand the current architecture:

- `stores/onboarding-store.ts` — the Zustand store (CapturedProfile type, state shape)
- `components/onboarding/onboarding-chat.tsx` — the main chat component (SSE streaming, message handling)
- `components/onboarding/profile-panel.tsx` — the right panel (checklist + profile card)
- `hooks/use-onboarding.ts` — onboarding status hooks
- `components/onboarding/onboarding-engine-picker.tsx` — the end-of-onboarding engine selection
- `lib/onboarding/api.ts` — backend API calls
- `CLAUDE.md` and `.claude/skills/cliniciq-design/SKILL.md` — design system rules

The onboarding system already works. The chat streams via SSE. The right panel tracks progress. Profile data lands in the store. What we're changing is the STRUCTURE — fewer questions, AI expansion between sections, section-by-section approval, and a lead magnet selection at the end that triggers engine production.

---

## WHAT CHANGES

### 1. The Checklist (profile-panel.tsx)

**Current:** 10 phases from the old 103-question model
**New:** 6 sections matching the streamlined flow

Update the `PHASES` constant in `profile-panel.tsx`:

```typescript
const PHASES = [
  {
    id: "section_1",
    label: "You & Your Method",
    isComplete: (p) => Boolean(p.specialty && p.mechanism),
  },
  {
    id: "section_2",
    label: "Your Patient",
    isComplete: (p) => Boolean(p.avatarName && p.avatarDescription),
  },
  {
    id: "section_3",
    label: "Your Offers",
    isComplete: (p) => Boolean(p.offersCore),
  },
  {
    id: "section_4",
    label: "Your Proof",
    isComplete: (p) => (p.proofStoryCount ?? 0) > 0,
  },
  {
    id: "section_5",
    label: "Your Voice & Brand",
    isComplete: (p) => Boolean(p.voiceTone || (p.signaturePhrases?.length ?? 0) > 0),
  },
  {
    id: "section_6",
    label: "Your First Engine",
    isComplete: (p) => Boolean(p.selectedEngine),
  },
] as const;
```

### 2. The Store (onboarding-store.ts)

Add fields to `CapturedProfile` for the new sections:

```typescript
export interface CapturedProfile {
  // Section 1: You & Your Method
  specialty?: string;
  practice?: string;
  practiceName?: string;
  mechanism?: string;
  mechanismName?: string;
  mechanismSimple?: string;         // fifth-grade version
  contrarianPosition?: string;
  origin?: string;
  character?: string;               // Reluctant Hero / Cause-Driven / Reporter
  anger?: string;
  enemy?: string;
  whyNow?: string;

  // Section 2: Your Patient
  avatarName?: string;
  avatarDescription?: string;
  avatarDailyReality?: string;
  avatarDreamOutcome?: string;
  avatarFears?: string;
  avatarInternalDialogue?: string;
  avatarAwarenessLevel?: string;
  falseBeliefVehicle?: string;
  falseBeliefInternal?: string;
  falseBeliefExternal?: string;
  patientFailureLanguage?: string[];  // exact phrases patients use

  // Section 3: Your Offers
  offersEntry?: string;
  offersCore?: string;
  offersPremium?: string;
  offersCorePrice?: string;
  offersCoreTimeline?: string;       // time to first shift
  offersCoreEffort?: string;         // what's required of patient
  offersFriction?: string;           // what makes them almost quit
  guarantee?: string;
  bonusIdeas?: string[];             // AI-generated, expert-selected

  // Section 4: Your Proof
  proofFlagshipStory?: string;
  proofStoryCount?: number;
  proofScore?: number;
  proofCredentials?: string;
  proofMedia?: string;
  proofAggregate?: string;           // "X patients, Y years, Z% improved"

  // Section 5: Your Voice & Brand
  voiceTone?: string;
  voiceRhythm?: string;
  voiceAuthority?: string;
  signaturePhrases?: string[];
  bannedWords?: string[];
  brandFeel?: string;
  brandLove?: string;                // marketing they love
  brandHate?: string;                // marketing they hate
  visualDirection?: string;

  // Section 6: First Engine
  selectedEngine?: string;           // lead magnet type selected
  selectedEngineHeadline?: string;
  selectedEngineNextStep?: string;   // what happens after lead magnet

  // Meta
  sectionApprovals?: {
    section1?: boolean;
    section2?: boolean;
    section3?: boolean;
    section4?: boolean;
    section5?: boolean;
    section6?: boolean;
  };
}
```

Bump `STORE_VERSION` to trigger a clean migration for existing users.

### 3. Section Approval Flow (new component)

Create `components/onboarding/section-approval.tsx`:

After each section's questions are answered, IQ generates an AI expansion and presents it as a **structured card in the chat**. This is NOT plain text — it's a rich card with formatted sections and an approval action.

```typescript
// section-approval.tsx
interface SectionApprovalProps {
  sectionId: string;
  sectionTitle: string;
  content: Record<string, string>;  // key-value pairs to display
  onApprove: () => void;
  onEdit: (field: string) => void;
}
```

The card renders as:
- White card with emerald left border (4px)
- Section title at top (bold, 14px)
- Content as labeled rows (label: value) — each row editable on click
- Bottom: [✅ Approve & Continue] emerald button + [✏️ Edit] gray text link
- When approved: card gets a green checkmark overlay, becomes non-editable, and IQ moves to the next section

**How it works in the chat flow:**
1. IQ asks the section's questions (3-5 questions, one at a time)
2. After the last question in the section, IQ sends a special message type: `section_expansion`
3. The `section_expansion` message renders as the SectionApproval card
4. Expert clicks Approve → profile store updates → IQ says "Section locked ✅" → moves to next section
5. Expert clicks Edit → specific field opens for inline editing in the card → re-approve

### 4. Profile Panel Updates (profile-panel.tsx)

The right panel should show each section's data AFTER approval, building up as sections complete:

```
Section 1 ✅ → Shows: specialty, mechanism name, contrarian position, origin (1-liner)
Section 2 ✅ → Shows: avatar name + description card
Section 3 ✅ → Shows: offer stack (entry/core/premium with prices)
Section 4 ✅ → Shows: proof score + flagship story preview
Section 5 ✅ → Shows: voice tone + signature phrases + banned words
Section 6 ✅ → Shows: engine type + "Building..." with progress
```

Each section's data appears as a **compact card** in the right panel when that section is approved. Before approval, the section shows as a pending item in the checklist. The expert watches their profile materialize section by section.

### 5. Section 6: Lead Magnet Engine Picker (update onboarding-engine-picker.tsx)

**Current:** Picks between "Organic" and "Paid" engine paths
**New:** IQ generates 5 vibe-coded micro-SaaS lead magnet ideas tailored to the expert's profile, and the expert picks one

Replace the current engine picker with a **Lead Magnet Selector** that:
1. Takes the expert's profile (mechanism, avatar, offers) as input
2. Generates 5 lead magnet options (IQ sends these as a structured message)
3. Each option is a card: icon + name + description + "Why this works" + [Select] button
4. Types: Score Calculator, Assessment, Quiz, Tracker, Risk Profile
5. After selection: 2 more quick questions (headline + next step)
6. Then: engine starts building — lead magnet + opt-in page + email sequence + first week of social posts

The lead magnet options should be SPECIFIC to their profile. Not generic templates. If their mechanism is "The Signal Reset Protocol" and their avatar is "Stressed Mom Sarah" with thyroid issues, the options should be things like:
- "Thyroid Signal Score Calculator"
- "Root Cause Fatigue Assessment"
- "Is Your Thyroid Really Fine? Quiz"
- "7-Day Energy Pattern Tracker"
- "Hormone Health Risk Profile"

Each rendered as a selectable card in the chat.

### 6. The Conversation Logic

The conversation flow is driven by the backend (IQ's prompt), but the frontend needs to:

1. **Track which section we're in** — add `currentSection: number` to the onboarding store (1-6)
2. **Recognize section transitions** — when IQ sends a `section_expansion` event, the frontend renders the approval card
3. **Handle approval events** — when the expert approves a section, send an `onboarding_section_approved` event to the backend and advance `currentSection`
4. **Handle the lead magnet selection** — when IQ sends `engine_options`, render the lead magnet picker cards
5. **Trigger engine building** — after section 6 approval, fire the engine build (similar to current `onboarding_handoff_complete` flow)

Add to onboarding store:
```typescript
currentSection: number;  // 1-6
advanceSection: () => void;
```

### 7. Chat Message Types

The chat already handles text messages via SSE. Add support for structured message types that render as cards instead of text bubbles:

```typescript
type OnboardingMessageType = 
  | "text"                    // normal chat bubble
  | "section_expansion"       // AI expansion card with approve/edit
  | "engine_options"          // 5 lead magnet option cards
  | "engine_confirmed"        // engine building confirmation card
  | "profile_preview"         // inline profile snippet (avatar card, offer stack, etc.)
```

When `onboarding-chat.tsx` receives a `section_expansion` SSE event:
- Parse the expansion data (section title + key-value content)
- Render as `SectionApproval` component instead of a text bubble
- Wait for user interaction (approve or edit) before continuing

### 8. Timing & Progress

**Old progress:** 12% → 22% → 32% → ... → 100% across 12 phases
**New progress:** Each section = ~16.6%. 6 sections = 100%.

```
Section 1 approved → 17%
Section 2 approved → 33%
Section 3 approved → 50%
Section 4 approved → 67%
Section 5 approved → 83%
Section 6 approved → 100% + engine building
```

The progress bar should animate smoothly as each section locks.

---

## WHAT STAYS THE SAME

- **The SSE streaming architecture** — IQ's responses still stream via SSE. Don't change the streaming code.
- **The 3-panel layout** — sidebar (locked) + center chat + right panel. Don't change the layout.
- **The onboarding gate** — middleware redirects to /onboarding if not complete. Don't change this.
- **The profile panel position** — right panel, sticky. Don't move it.
- **The input bar** — same chat input. Don't change it.
- **The auto-save** — still persists to store. Still resumable.
- **The celebration at completion** — keep the celebration animation when 100% is reached.
- **The router** — still at `/onboarding`. Don't change the route.

---

## WHAT THE BACKEND PROMPT NEEDS TO KNOW

The backend IQ prompt (not this frontend prompt's concern, but documented for context) needs to:
1. Ask only the 22 questions across 6 sections
2. After each section's questions, generate the AI expansion and send it as a `section_expansion` SSE event
3. Wait for the `onboarding_section_approved` event before moving to the next section
4. In Section 6, generate 5 lead magnet options based on the profile and send as `engine_options` SSE event
5. After engine selection, confirm and trigger engine production

The frontend doesn't generate the expansions — the backend does. The frontend's job is to:
- Render the expansion cards
- Handle the approve/edit interaction
- Send approval events back to the backend
- Track progress
- Build the profile panel in real-time

---

## FILE CHANGES SUMMARY

| File | Change |
|------|--------|
| `stores/onboarding-store.ts` | Expand CapturedProfile, add currentSection + sectionApprovals, bump version |
| `components/onboarding/profile-panel.tsx` | Replace 10-phase checklist with 6-section checklist, update profile card rendering |
| `components/onboarding/section-approval.tsx` | **NEW** — section expansion card with approve/edit |
| `components/onboarding/lead-magnet-picker.tsx` | **NEW** — 5 lead magnet option cards for Section 6 |
| `components/onboarding/onboarding-chat.tsx` | Add structured message type handling (section_expansion, engine_options), section tracking |
| `components/onboarding/onboarding-engine-picker.tsx` | Replace organic/paid picker with lead magnet engine flow, or integrate into lead-magnet-picker |
| `components/onboarding/onboarding-checklist.tsx` | Update if separate from profile-panel |
| `hooks/use-onboarding.ts` | Update progress calculation for 6 sections |

---

## DESIGN SYSTEM

Follow the existing ClinicIQ design system (CLAUDE.md + design skill):

- **Section approval cards:** White bg, 4px emerald left border, rounded-xl, padding 20px. Labels in #6B7280 (11px, uppercase). Values in #1F2937 (13px). Approve button: emerald bg, white text.
- **Lead magnet option cards:** White bg, border #E5E7EB, rounded-xl, hover: emerald border + shadow. Icon (24px colored), name (14px bold), description (12px #6B7280), "Why this works" (11px #065F46 on #F0FDF4 bg), [Select →] emerald text.
- **Progress bar:** emerald fill, smooth animation (500ms transition on width).
- **Checkmarks:** emerald CheckCircle2 when section approved. Gray Circle when pending. Blue Loader2 (spinning) for current section.

---

## THE PRINCIPLE

**Old onboarding:** 103 questions → expert talks for an hour → platform builds strategy after
**New onboarding:** 22 questions in 6 sections → AI expands after each → expert approves in real-time → first engine starts building before they finish → done in 20-30 minutes

The expert should feel like they're watching their brand materialize in front of them — not filling out a form. Every section they approve, the right panel gets richer. By Section 3, they're already thinking "this thing gets me." By Section 6, they're watching their first lead magnet engine start building. That's the moment they become a retained user.
