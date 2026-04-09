# ClinicIQ — Webinar Builder: Complete Build Spec
## Pattern A: Brief → Generate → Rich Document View → Section-by-Section Edit
## Modeled after: Gamma.app presentation builder + Beautiful.ai + Google Slides outline view

---

## WHAT THIS BUILDER DOES

The Webinar Builder produces a complete webinar: a full script built on the Perfect Webinar framework (hook → origin story → 3 secrets → stack → close), a slide deck (47+ slides), trial closes woven throughout, and all supporting elements (proof stack, value stack, guarantee, urgency). This is the most complex single-output builder — the script alone can be 5,000–8,000 words.

---

## THE FLOW

### Phase 1: Brief (IQ Chat)

IQ asks:

1. **"What's the webinar about?"** — IQ suggests based on the Monthly Master Plan: "Your plan calls for a webinar on cortisol and the Signal Reset Protocol. Want to build that, or something different?"
2. **"Live or evergreen?"** — [Live] [Evergreen/Automated] — affects pacing, interaction prompts, and urgency language
3. **"Which offer at the end?"** — shows offer stack: [Hormone Reset Protocol — $4,800] [VIP Intensive — $12,000]
4. **"How long?"** — [30 min] [45 min] [60 min] [90 min] — default 45–60 min based on offer price (higher ticket = longer)

IQ confirms and starts building. "Building your 60-minute webinar — Perfect Webinar framework, Signal Reset Protocol mechanism, pitching the Hormone Reset Protocol. This is the biggest build — give me about 30 minutes."

### Phase 2: Generation (Right Panel — Outline View)

The right panel shows the webinar being built as a **structured outline** — like a presentation builder's outline/sidebar. Each section of the webinar appears as it's generated.

**Right panel layout:**

**Header:**
- "🎥 Webinar Builder" (14px, bold) + "Building script..." (13px, #6B7280) + spinner
- "Section 3 of 7" + overall progress bar
- [Pause] gray text link

**Outline view:**
A scrollable outline showing the webinar's major sections. Each section is a collapsible card that fills in as it generates.

```
┌─────────────────────────────────────────────┐
│  🎥 Webinar: The Signal Reset Method        │
│  60 min · Evergreen · Hormone Reset Protocol│
│  ████████████████░░░░ 72%                   │
│  ─────────────────────────────────────────  │
│                                             │
│  ✅ 1. HOOK & INTRO (5–7 min)              │
│     "Two months ago, a guy with no medical  │
│     background launched a telehealth..."    │
│     4 slides · 847 words        [View →]    │
│                                             │
│  ✅ 2. ORIGIN STORY (7–10 min)             │
│     Epiphany Bridge — Dr. Chen's moment     │
│     of discovery...                         │
│     6 slides · 1,241 words      [View →]    │
│                                             │
│  ✅ 3. SECRET #1 (8–10 min)                │
│     "Agents + Teams = A Workforce"          │
│     Breaking the Vehicle false belief...    │
│     8 slides · 1,456 words      [View →]    │
│                                             │
│  🔄 4. SECRET #2 (8–10 min)                │
│     "It Sounds More Like You Than You Do"   │
│     Writing section 3 of 5...    ████░ 60%  │
│                                             │
│  ○  5. SECRET #3 (8–10 min)                │
│     Breaking the External false belief...   │
│                                             │
│  ○  6. THE STACK & CLOSE (10–15 min)       │
│     Value stack + If/All + Price reveal     │
│                                             │
│  ○  7. Q&A FRAMEWORK (5 min)               │
│     Pre-planted questions + live framework  │
│                                             │
└─────────────────────────────────────────────┘
```

**Section card styling:**
- ✅ Complete: emerald check + section title (13px, bold, #1F2937) + subtitle/preview (12px, #6B7280, 2 lines max) + metadata (11px, #9CA3AF: slide count, word count) + [View →] emerald link
- 🔄 Active: blue spinner + bold title + "Writing section X of Y..." + mini progress bar
- ○ Queued: gray circle + gray title + brief description of what will be built
- Card: 1px bottom border #E5E7EB, padding 12px 16px. Active section: light blue bg (#EFF6FF).

### Phase 3: Section Detail View (Right Panel — replaces outline)

Clicking [View →] on a completed section opens the **section detail view** — a rich document reader with slide thumbnails.

**Layout:**

**Header:**
- [← Back to outline] + "Section 1: Hook & Intro" (14px, bold)
- "4 slides · 847 words · ~6 minutes" (12px, #6B7280)
- [Edit in chat] [Edit inline] toggle

**Slide strip (top):**
Horizontal scrollable row of slide thumbnails (120px × 68px each, 16:9 ratio). Click any slide to jump to that part of the script. Active slide has emerald border.

```
┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐
│ S1   │ │ S2   │ │ S3   │ │ S4   │
│      │ │      │ │      │ │      │
└──────┘ └──────┘ └──────┘ └──────┘
```

Each thumbnail: #1F2937 bg (simulating a dark slide), white text showing the slide's main headline (8px, truncated). Badge in corner: "TC" (trial close) if the slide contains a trial close.

**Script content (below slides — scrollable):**

The script displayed as a rich document — like reading a presentation script with stage directions.

```
SLIDE 1 — OPENING HOOK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[SLIDE: Bold text — "What if everything you tried for
your fatigue was treating the wrong thing?"]

[ON CAMERA — Direct. No warmup.]

"Two months ago, I met a woman who had been to five
doctors in three years. She'd been told her labs were
normal. She'd been told it was stress. She'd been told
it was just aging.

She was 38.

In our first appointment, I ran a test nobody else had
run. And in 20 minutes, we found exactly what was wrong.

[PAUSE — let it land]

Over the next 60 minutes, I'm going to show you three
things..."

[TRIAL CLOSE #7 — "You probably":] 
"You've probably been told some version of 'your labs
are normal' while you still feel terrible."

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SLIDE 2 — THE THREE PROMISES
...
```

**Script formatting:**
- Slide headers: 14px, bold, #1F2937, with a horizontal rule below
- Slide descriptions: [bracketed, 12px, italic, #6B7280] — describes what's on the slide
- Stage directions: [bracketed, 12px, italic, #9CA3AF] — camera direction, pauses, transitions
- Script body: 14px, #374151, line-height 1.8 — comfortable reading
- Trial close callouts: highlighted block — #FEF3C7 bg (amber tint), amber left border (3px), "TRIAL CLOSE #7" label in bold 11px amber text
- Proof moments: highlighted block — #F0FDF4 bg, emerald left border, "PROOF MOMENT" label
- **Inline editing:** Click any text to edit directly. Changes save automatically. The script is a contenteditable rich text area with formatting preserved.

### Phase 4: Full Webinar View

From the outline, the expert can also click [View Full Script →] to see the **entire webinar as one continuous document** — all sections concatenated, all slides shown, formatted like a professional script/teleprompter. This is what they'd use to practice or deliver.

**Full script view header:**
- "The Signal Reset Method — Full Webinar Script"
- "60 minutes · 47 slides · 6,842 words · 14 trial closes"
- [Export PDF] [Export Google Slides] [Copy to clipboard] — action buttons
- [Print] — opens browser print dialog

**Navigation sidebar (left of script, narrow):**
Mini outline showing section names — click to jump. Sticky position so it stays visible while scrolling the script.

### Phase 5: Slide Deck View

Toggle between **Script View** and **Slide Deck View** with a tab at the top: [📝 Script] [📊 Slides]

**Slide Deck View:**
Grid of all slides (3 columns), each shown as a card with the slide content visible. Click any slide to see it full-size with the associated script text below.

Slides are generated as styled text-on-dark-background cards (not actual PowerPoint yet):
- Headline slides: large white text on #1F2937 bg
- Bullet slides: left-aligned bullets on dark bg
- Proof slides: testimonial quote with attribution
- Stack slides: value stack formatted with price strikethroughs
- Image slides: placeholder frames with image generation prompts

Future: [Export to Google Slides] and [Export to PowerPoint] generate actual downloadable slide files.

---

## WEBINAR SECTIONS (Perfect Webinar Framework)

| Section | Duration | What It Contains |
|---------|----------|-----------------|
| 1. Hook & Intro | 5–7 min | Opening hook, three promises, credibility establishment, origin story teaser |
| 2. Origin Story / Epiphany Bridge | 7–10 min | Expert's story, before state, trigger event, realization, bridge to patients |
| 3. Secret #1 | 8–10 min | Breaks the Vehicle false belief. Teaches the new vehicle (mechanism). Story + teaching. |
| 4. Secret #2 | 8–10 min | Breaks the Internal false belief. "AI can't sound like me" → Voice DNA proof. Story + teaching. |
| 5. Secret #3 | 8–10 min | Breaks the External false belief. "I should wait" → Compounding proof. Story + teaching. |
| 6. The Stack & Close | 10–15 min | Transition, value stack (element by element with running total), If/All statements, price reveal, I Had Two Choices, You've Got Two Choices, guarantee, CTA |
| 7. Q&A Framework | 5 min | Pre-planted questions that address top objections, framework for handling live Q&A |

**Trial closes** woven throughout (14 of 16 from the Brunson methodology). Each one is tagged in the script so the expert can see the pattern.

---

## IQ CHAT DURING BUILDING

IQ provides section-by-section updates:
- "Section 1 is done — the hook opens with a patient story that maps perfectly to Stressed Mom Sarah's internal dialogue."
- "Working on Secret #2 now. This one breaks the belief that AI can't capture their voice — I'm leading with your Voice DNA methodology."
- "Stack slide is built — 7 elements, running total of $820,000 in value."

Expert can request changes mid-build: "Make the origin story more emotional" → IQ regenerates Section 2.

---

## MOCK DATA

```typescript
const mockWebinar = {
  title: "The Signal Reset Method: Why Everything You've Tried for Fatigue Has Failed",
  duration: "60 min",
  format: "evergreen",
  offer: "Hormone Reset Protocol — $4,800",
  avatar: "Stressed Mom Sarah",
  sections: [
    { id: "s1", name: "Hook & Intro", status: "complete", slides: 4, words: 847, duration: "~6 min", trialCloses: 3 },
    { id: "s2", name: "Origin Story", status: "complete", slides: 6, words: 1241, duration: "~9 min", trialCloses: 2 },
    { id: "s3", name: "Secret #1: The Mechanism", status: "complete", slides: 8, words: 1456, duration: "~10 min", trialCloses: 3 },
    { id: "s4", name: "Secret #2: Voice DNA", status: "complete", slides: 7, words: 1312, duration: "~9 min", trialCloses: 2 },
    { id: "s5", name: "Secret #3: Compounding", status: "complete", slides: 6, words: 1089, duration: "~8 min", trialCloses: 2 },
    { id: "s6", name: "The Stack & Close", status: "complete", slides: 12, words: 1834, duration: "~14 min", trialCloses: 4 },
    { id: "s7", name: "Q&A Framework", status: "complete", slides: 4, words: 563, duration: "~4 min", trialCloses: 0 },
  ],
  totalSlides: 47, totalWords: 8342, totalTrialCloses: 16,
};
```

---

## THE PRINCIPLE

The Webinar Builder produces the single highest-revenue asset in the expert's arsenal. The Perfect Webinar framework has generated hundreds of millions in health revenue. The UX must make a 6,000+ word script feel manageable — the outline breaks it into digestible sections, the slide strip gives visual anchoring, the trial close highlights teach the framework while they read. The expert should finish reviewing their webinar and think: "This is better than anything I could have written myself."
