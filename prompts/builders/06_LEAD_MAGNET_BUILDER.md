# ClinicIQ — Lead Magnet Builder: Complete Build Spec
## Pattern C: Type Selection → Wizard Build → Live Preview
## Modeled after: ScoreApp quiz builder + Typeform flow builder + Interact quiz maker

---

## WHAT THIS BUILDER DOES

The Lead Magnet Builder produces the expert's primary opt-in offer: quizzes, assessments, PDF guides, calculators, or vibe-coded mini-apps. The lead magnet is the entry point of the funnel — what gets the first email address. Type is selected based on avatar awareness level.

---

## THE FLOW

### Phase 1: Brief (IQ Chat)

IQ recommends a type based on the avatar's awareness level:

> "Your primary avatar Stressed Mom Sarah is at Level 2 (Problem-Aware). For that awareness level, I'd recommend a **quiz or assessment** — it creates self-identification and makes the results feel personal. Here are your options:"

**Type selection** (shown as cards in the chat or right panel):

```
┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│  📊 Quiz       │ │  📋 Assessment │ │  📖 PDF Guide  │
│  "What's really│ │  "Root Cause   │ │  "The 5 Hidden │
│  driving your  │ │  Risk Profile" │ │  Causes of     │
│  fatigue?"     │ │  Score + report │ │  Fatigue"      │
│  Best for L1-2 │ │  Best for L2-3 │ │  Best for L2   │
│  [Select]      │ │  [Select]      │ │  [Select]      │
├────────────────┤ ├────────────────┤ ├────────────────┤
│  🧮 Calculator │ │  🔬 Mini App   │ │  💰 Paid       │
│  "Hormone      │ │  Vibe-coded    │ │  Assessment    │
│  Health Score" │ │  interactive   │ │  $47–$97       │
│  Best for all  │ │  tool          │ │  Best for L2-3 │
│  [Select]      │ │  [Select]      │ │  [Select]      │
└────────────────┘ └────────────────┘ └────────────────┘
```

IQ then asks:
1. **"What topic?"** — "Based on your mechanism (Signal Reset Protocol), I'd suggest a cortisol or hormone assessment. Or pick your own."
2. **"What's the bridge to the next step?"** — "After they see their results, what should the CTA be?" → [Watch the webinar] [Book an assessment] [Download the guide]

### Phase 2: Structure Builder (Right Panel)

The right panel shows the **lead magnet structure** being built — different view depending on type.

#### FOR QUIZ / ASSESSMENT:

**Flow builder view** (modeled after Typeform/ScoreApp):

```
┌─────────────────────────────────────────────┐
│  🧲 Lead Magnet Builder                     │
│  Cortisol Assessment Quiz · 8 questions     │
│  ████████████████░░░░ 75%                   │
│  ─────────────────────────────────────────  │
│                                             │
│  FLOW:                                      │
│                                             │
│  ┌─ 📝 Welcome Screen ──────────── ✅ ─┐   │
│  │  "Discover what's really driving     │   │
│  │   your fatigue in 3 minutes"         │   │
│  └──────────────────────────────────────┘   │
│           ↓                                 │
│  ┌─ Q1: How often do you crash? ── ✅ ─┐   │
│  │  ○ Daily  ○ 3-4x/week  ○ Weekly     │   │
│  │  ○ Rarely                            │   │
│  └──────────────────────────────────────┘   │
│           ↓                                 │
│  ┌─ Q2: When is your worst time? ─ ✅ ─┐   │
│  │  ○ Morning  ○ Afternoon (2-4pm)      │   │
│  │  ○ Evening  ○ All day                │   │
│  └──────────────────────────────────────┘   │
│           ↓                                 │
│  ┌─ Q3: Sleep quality? ────────── 🔄 ─┐   │
│  │  Building...                  ████░  │   │
│  └──────────────────────────────────────┘   │
│           ↓                                 │
│  ○  Q4–Q8 (queued)                          │
│           ↓                                 │
│  ┌─ 📊 Results Screen ──────────── ○ ──┐   │
│  │  Personalized score + category       │   │
│  │  + mechanism bridge + CTA            │   │
│  └──────────────────────────────────────┘   │
│           ↓                                 │
│  ┌─ 📧 Lead Capture Gate ────────── ○ ─┐   │
│  │  Name + Email → then show results    │   │
│  └──────────────────────────────────────┘   │
│                                             │
│  [+ Add Question]  [Reorder]  [Preview]     │
└─────────────────────────────────────────────┘
```

**Question card styling:**
- Each question: white card, 1px border, rounded-lg, full-width
- Question text (13px, bold), answer options below (12px, radio/checkbox style)
- Status: ✅ complete, 🔄 building, ○ queued
- Click → opens question editor (edit text, answer options, scoring weight, branching logic)
- Connected by ↓ arrows with subtle lines

**Question editor (inline expand or detail view):**
- Question text: editable input
- Answer options: list of inputs, each with a score weight (1–5). [+ Add option] [Remove]
- Question type: [Multiple choice] [Scale (1–10)] [Text input] [Yes/No]
- Branching (optional): "If answer is X → skip to Q6" — dropdown logic builder
- Image (optional): attach an image to the question
- [Save] [Delete Question]

**Results screen editor:**
- Score ranges: define 3–5 result categories (e.g., "Low risk 0–30", "Moderate 31–60", "High 61–100")
- Each category: custom title, description, and specific recommendation. "Your score suggests your HPA axis is in overdrive..."
- Mechanism bridge: text that connects results to the expert's approach
- CTA: button text + destination (webinar, booking page, etc.)

**Lead capture gate:**
- Fields: Name (required), Email (required), Phone (optional)
- Gate placement: [Before results] (recommended — higher conversion) or [After results]
- "Results are never shown before contact information is collected." — this is a hard rule

#### FOR PDF GUIDE:

**Document outline view** (simpler — like a table of contents being built):

```
┌─────────────────────────────────────────────┐
│  📖 PDF Guide: The 5 Hidden Causes of       │
│  Chronic Fatigue                             │
│  ─────────────────────────────────────────  │
│                                             │
│  ✅ Cover Page                              │
│  ✅ Introduction (who this is for)          │
│  ✅ Chapter 1: The Cortisol Connection      │
│  ✅ Chapter 2: The Thyroid Misconception    │
│  🔄 Chapter 3: The Gut-Brain Axis          │
│  ○  Chapter 4: The Toxin Burden            │
│  ○  Chapter 5: The Sleep Paradox           │
│  ○  Conclusion: The Root Cause Framework   │
│  ○  CTA Page: Your Next Step               │
│                                             │
│  [Preview PDF]  [Add Chapter]               │
└─────────────────────────────────────────────┘
```

- Click any chapter → detail view showing the full text, editable
- Final CTA page bridges to the webinar/offer
- [Preview PDF] opens a rendered PDF preview (branded with the expert's colors and logo)

#### FOR CALCULATOR / MINI APP:

**Spec view** showing the calculator/app flow:
- Input fields (what the user enters)
- Calculation logic (how the score is computed)
- Output display (what the result looks like)
- Lead capture gate position
- CTA on results page

This is a spec document that a developer would build — the Lead Magnet Builder produces the complete specification, content, and design direction for a vibe-coded tool, not the code itself. (Future: integrate with a code generation tool to auto-build it.)

### Phase 3: Preview

**[Preview] button** → opens a live preview of the lead magnet as the end user would experience it.

- Quiz: simulated walkthrough — click through questions, see results
- PDF: rendered document preview with branding
- Calculator: interactive preview with sample inputs

Preview opens in the right panel as a full-panel view (replacing the builder), or in a modal overlay. [← Back to editor] to return.

### Phase 4: Complete

IQ: "Your Cortisol Assessment Quiz is ready — 8 questions, 4 result categories, lead capture gate before results, CTA to your webinar. Want to preview the full flow?"

**Actions:**
- [Preview Full Flow] — walk through the entire quiz experience
- [Save to Drive]
- [Generate Opt-in Page] — shortcut to Funnel Builder, pre-configured with this lead magnet
- [Connect] — future: publish to a hosted URL. V1: "Connect your hosting platform in Services"

---

## MOCK DATA

```typescript
const mockQuiz = {
  name: "Cortisol Assessment Quiz",
  type: "quiz",
  topic: "What's really driving your fatigue?",
  questionCount: 8,
  resultCategories: [
    { range: "0-25", name: "Low Cortisol Impact", color: "#22C55E", description: "Your cortisol patterns look relatively stable..." },
    { range: "26-50", name: "Moderate Stress Response", color: "#F59E0B", description: "Your body is showing signs of a sustained stress pattern..." },
    { range: "51-75", name: "High Cortisol Disruption", color: "#F97316", description: "Your HPA axis is running in overdrive..." },
    { range: "76-100", name: "Critical — Signal Reset Needed", color: "#EF4444", description: "Your body is sending urgent signals that nobody has identified..." },
  ],
  questions: [
    { id: "q1", text: "How often do you experience an energy crash during the day?", type: "multiple-choice", options: ["Daily", "3-4 times a week", "1-2 times a week", "Rarely"], scores: [4, 3, 2, 1] },
    { id: "q2", text: "When is your worst time of day for fatigue?", type: "multiple-choice", options: ["Morning (hard to wake up)", "Afternoon (2-4pm crash)", "Evening (exhausted by 7pm)", "All day — no good time"], scores: [3, 4, 3, 5] },
    { id: "q3", text: "How would you rate your sleep quality?", type: "scale", min: 1, max: 10, labels: { 1: "Terrible", 5: "Average", 10: "Excellent" } },
    { id: "q4", text: "Have you been told your labs are 'normal' while you still feel unwell?", type: "yes-no", scores: { yes: 4, no: 0 } },
    // ... 4 more questions
  ],
  leadCapture: { position: "before-results", fields: ["name", "email"] },
  cta: { text: "Watch the Free Training →", destination: "/webinar" },
  mechanismBridge: "Your score suggests your body's stress signaling system — the HPA axis — may be running a pattern that nobody has identified. The Signal Reset Protocol was designed specifically for this pattern."
};
```

---

## THE PRINCIPLE

The lead magnet is the handshake — the first moment of trust. The Lead Magnet Builder must make it easy to create something that feels like a product, not a bribe. The quiz flow builder (modeled after ScoreApp and Typeform) makes the expert feel like they're designing an experience, not filling out a form. The results screen with mechanism bridge is where the lead magnet stops being "free content" and starts being "the first step in the funnel." The expert should look at the preview and think: "This is better than what agencies charge $5,000 to build."
