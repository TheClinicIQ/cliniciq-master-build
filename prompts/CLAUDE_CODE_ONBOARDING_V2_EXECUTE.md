# ClinicIQ Onboarding v2 — Execution Prompt for Claude Code
## Read this. Then execute it against both codebases.

**Frontend repo:** `/tmp/ClinicIQFrontend`
**Backend repo:** `/tmp/cliniciq-backend`

---

## WHAT WE'RE DOING

Replacing the 11-phase / 97-question onboarding with a 6-section conversational flow. Each section: IQ asks 3-5 core questions + probes deeper as needed → LLM expands answers into a complete strategic document → expert reviews and approves in the right panel → next section. Section 6 picks a lead magnet and triggers an actual build.

**This is NOT a form.** IQ is a sharp growth strategist having a real conversation. The frameworks (Brunson, Hormozi, Robbins) run invisibly. The expert never hears those words.

---

## WHAT EXISTS NOW (READ THESE FILES FIRST)

### Backend — key files to understand before changing anything:
```
app/agents/orchestrator/prompts/_mode_onboarding.md        — 37 lines, mode routing
app/agents/orchestrator/prompts/_onboarding_agent.md        — 204 lines, agent rules + posture
app/agents/orchestrator/prompts/_onboarding_guidelines.md   — 1,199 lines, 97 Qs + coaching (REPLACE THIS)
app/agents/orchestrator/prompts/_profile_outline.md         — 320 lines, profile doc structure
app/agents/orchestrator/prompts/_strategy_outline.md        — 193 lines, 7 strategy deliverables
app/agents/orchestrator/modes/onboarding.py                 — mode config (Sonnet 4.6, 10 tools)
app/models/onboarding/dossier.py                            — ExpertDossier ORM (14 JSONB sections)
app/agents/_platform/agent_tools/onboarding/                — 10 tools (capture, read, reverse_pass, etc.)
app/services/onboarding/                                    — finalize, handoff, diagnostics, narrative, etc.
```

### Frontend — key files:
```
stores/onboarding-store.ts                                  — CapturedProfile + state
components/onboarding/onboarding-overlay.tsx                — main overlay component
components/onboarding/onboarding-chat.tsx                   — 673 lines, SSE streaming
components/onboarding/profile-panel.tsx                     — right panel (checklist + profile)
components/onboarding/onboarding-engine-picker.tsx           — end-of-onboarding engine pick
components/onboarding/inline-question-card.tsx               — renders option picks (chip picker)
components/onboarding/profile-document.tsx                   — live profile doc on right panel
hooks/use-onboarding.ts                                     — status hooks
```

### Tools that already exist and we KEEP:
- `capture_dossier` — writes to any of 14 JSONB sections. Supports `partial=True`. This is the workhorse.
- `append_profile_section` — writes voice-matched paragraphs to the live profile doc. Expert watches it build.
- `read_dossier` — self-orientation + resume.
- `update_capture` — corrections.
- `import_uploaded_context` — drag-drop intake.
- `generate_profile_narrative` — final canonical profile.
- `finalize` — triggers Layer 2 (brand_strategy_lead via ARQ).
- `ask_questions` — **THIS IS THE OPTION TREE / CHIP PICKER.** Already renders as clickable pills in chat via `inline-question-card.tsx`. We use this for the weak-response option trees.

### Tools to DELETE:
- `run_reverse_pass` — replaced by section-level approval as the quality gate.
- `list_missing_fields` — replaced by section state tracking.
- `list_captured_sections` — replaced by section state tracking.

### Dossier JSONB sections (all 14 — no schema changes needed):
`identity`, `expert_personal_story` (was `expert_story`), `clinical_philosophy`, `voice_dna`, `avatar_profile`, `root_cause_map`, `competitive_landscape`, `offer_architecture`, `proof_bank`, `content_audit`, `dream_vision_traffic` (was `dream_vision`), `business_context`, `visual_dna`, `webinar_raw_material`

### What stays 100% untouched:
- All 14+ builder agents in `app/agents/builders/`
- All strategy deliverable generators
- `_strategy_outline.md` and `_profile_outline.md`
- SSE streaming infrastructure
- Pipeline mode routing
- The handoff → ARQ → brand_strategy_lead chain
- All downstream consumers of the dossier

---

## THE 6 SECTIONS — What IQ Asks

### Section 1: You & Your Method

IQ's opening (personalized from web scrape — replaces the current LOCKED openers):

> "Hey [Name] — I'm IQ, your growth strategist. Before you got here, I took a look at your practice.
>
> [1-2 observations from scrape — specialty, positioning, something notable]
>
> Over the next 20-30 minutes, I'm going to learn everything I need to build your complete marketing engine. Not a form — a conversation. You'll watch it all come together on the right as we go.
>
> Let's start. Tell me about your practice — what do you do and who do you help?"

**Core questions (must ask all — can add follow-ups when answers are thin):**

1. "Tell me about your practice — what do you do, who do you help, and how are you set up?"
2. "What's the first thing you look at or test that most other practitioners skip? When someone comes to you after failing elsewhere — what do you find?"
3. "What do you believe about health that most people in your field get wrong?"
4. "Is there a story behind why you do this work? Something personal that put you on this path?"
5. "What makes you angry about your field — the thing you'd change if you could?"

**After these 5, IQ has enough to expand. IQ calls the expander (see below), which produces the Section 1 card. Right panel streams it live. Expert reviews.**

**→ Captures to dossier:** `identity` (specialty, practice model, team, years), `clinical_philosophy` (core belief, contrarian position), `root_cause_map` (mechanism name, description, simple version, why it works), `expert_personal_story` (origin: before/trigger/realization/mission, anger, enemy), `competitive_landscape.category_villain`, `webinar_raw_material.one_big_domino` (seeded — refined in Section 5)

---

### Section 2: Your Patient

1. "Describe the patient who gets the best results with you — not demographics, the actual person. What's she dealing with, what has she tried, how long has she been struggling?"
2. "Walk me through a bad day for her — what's the first thing she notices when she wakes up? What falls apart by mid-afternoon?"
3. "When she describes why she came to see you — in her own words, not clinical — what does she say?"
4. "What's she afraid will happen if nothing changes?"

**→ Captures to dossier:** `avatar_profile` (all fields — name, demographics, awareness level, symptom stack, emotional core, internal dialogue, false beliefs vehicle/internal/external, dream outcome, buying triggers, patient failure language)

**The LLM expander generates ALL of the avatar depth from these 4 answers.** The 4-layer model (daily reality, emotional core, belief system, internal dialogue), the 3 false beliefs, the patient failure language, buying triggers, awareness level — all AI-generated from the seed and presented for approval.

---

### Section 3: Your Offer

1. "What's the ONE offer we're building around right now — the main thing? What is it, what does the patient get, what does it cost?"
2. "What does a patient actually experience going through it? How long, and how soon do they feel the first shift?"
3. "What's the hardest part for patients — the friction, the thing that almost makes someone quit?"
4. "What happens if someone goes through it and doesn't see the results they expected?"
5. "After someone finishes — do they stay with you? Come back? Is there a maintenance phase or community?"

**→ Captures to dossier:** `offer_architecture` (core offer name, price, before/after transformation, timeline, effort, friction points, guarantee, continuity model). Only ONE offer — the rest of the value ladder gets built later in the platform's Offers section.

**Expander also generates:** Hormozi Value Equation assessment, 3 AI-generated bonus ideas (each addressing a specific friction point or false belief), retention/LTV strategy.

---

### Section 4: Your Proof

1. "Tell me about your best patient transformation — someone who came in struggling and left a different person. What was her life like before, and now?"
2. "What credentials and experience do you have? Degrees, certifications, years, media, books, podcasts, speaking — everything. Don't edit."
3. "Roughly how many patients have you helped with this approach? What percentage get meaningful results?"

**→ Captures to dossier:** `proof_bank` (flagship story structured as before/tried/turning point/result/life now, credentials sorted by impact, media inventory, aggregate outcomes, proof score, gaps flagged)

---

### Section 5: Your Voice & Brand

1. "What words or phrases do you find yourself saying all the time? The things that are uniquely you."
2. "What words do you NEVER want in your marketing?"
3. "Is there a brand or person on social media whose marketing you love? And anyone whose marketing makes you roll your eyes? Just names or descriptions."

**→ Captures to dossier:** `voice_dna` (tone, rhythm, authority style, emotional register, humor, signature phrases, banned words, voice confidence score — MOSTLY built from passive analysis of the entire conversation, these 3 Qs just confirm and add explicit bans/aspirations), `visual_dna` (brand feel direction)

---

### Section 6: Your Lead Magnet

IQ generates 5 creative lead magnet ideas based on the full profile. These are NOT from a fixed menu — IQ has full creative freedom. They must be interactive micro-apps (not PDFs) that deliver personalized results and capture leads.

1. "Which of these excites you most? Or does it spark a different idea?" (rendered via `ask_questions` tool as selectable cards)
2. "What should the opt-in page promise — speaking directly to [avatar name]'s biggest frustration?"
3. "After they get their results — what's the next step? Book a call, watch a training, or something else?"

The lead magnet is a lead capture tool. The expert calls and nurtures the leads. The value ladder gets built later in the Offers section.

**→ After approval:** Call `finalize` → triggers Layer 2 strategy generation via existing ARQ chain. Lead magnet builder agent (`app/agents/builders/lead_magnet_builder/`) receives the spec and starts building.

---

## THE EXPANDER — How Section Expansion Works

After each section's questions are answered, IQ needs to produce the full strategic expansion. **This is just the LLM with the right context.** No special "expander service" needed.

Here's how it works in the agent flow:

1. IQ finishes the section's questions and has the raw answers.
2. IQ composes an internal expansion by writing a rich, complete version of the section card. The LLM already has full context: it knows what the strategy deliverables need (`_strategy_outline.md`), what the profile doc looks like (`_profile_outline.md`), what the builders consume, and what the onboarding is FOR. It can do the expansion in its own reasoning.
3. IQ calls `capture_dossier` with the full section payload (using `partial=True` is fine if some fields need refinement).
4. IQ calls `append_profile_section` to write the voice-matched version to the profile doc.
5. IQ presents the expansion in the chat as a structured summary and asks the expert to review what appeared in the right panel.
6. Expert approves, or says "not quite" → IQ uses `ask_questions` tool to present alternative directions → expert picks → IQ adjusts and re-captures.

**The LLM IS the expander.** It has the dossier context, the strategy context, the builder context. It knows that a thin avatar means thin ads. It knows that missing false beliefs means the webinar builder can't produce 3 secrets. It knows what "enough" looks like because the strategy and builder specs are in its context. No separate service needed.

---

## THE RESPONSE + APPROVAL PROTOCOL

### During questions:

**Strong answer:** Confirm sharply. Capture immediately with `capture_dossier`. Call `append_profile_section`. Move to next question.

**Weak answer:** IQ expands using its knowledge of the specialty and the frameworks:
> "Based on what you said, here's how I'd frame that: [enhanced version]. Does that feel right?"
- YES → capture, append, move on
- NO → IQ fires `ask_questions` with 3-4 specific alternative directions + "Other" option
- Expert picks → IQ expands their pick → confirms → captures

**Blank / "I don't know":** IQ generates from specialty knowledge + any web scrape data:
> "No worries. Based on your specialty, here's what I'd put: [generated]. We can refine anytime."
- Capture with `source="agent_generated"` flag.

### During section approval:

After all questions in a section, IQ presents the full expansion and asks: "Take a look at what I've built on the right. Does this feel right?"

- **Approves** → section complete, move to next
- **Wants changes** → IQ fires `ask_questions` with alternative directions → expert picks → IQ re-expands → calls `update_capture` to overwrite → asks again
- **No hard cap on rounds.** IQ converges in 1-2. If stuck: "What specifically feels off? The tone? The positioning? The language?"

---

## BACKEND CHANGES

### Replace `_onboarding_guidelines.md` (1,199 lines → ~200 lines)

The new guidelines file has:
- The 6 sections with their core questions (from above)
- Per-section capture mappings (which `capture_dossier` sections each question feeds)
- The expansion instructions (how the LLM should build the full strategic card from raw answers)
- The section-level approval flow
- Section 6 lead magnet generation + `finalize` trigger

### Slim down `_onboarding_agent.md` (204 lines → ~80 lines)

Keep:
- §1 Identity (IQ's personality)
- §2 Honest Partner Posture
- §3 Pushback Intensity Dial
- §4 Tool Discipline (updated for fewer tools)
- §5 CRITICAL FRAME ("expert doesn't know strategy — platform builds it")

Remove:
- All references to 97 questions, 11 phases, phase-by-phase coaching branches
- References to `run_reverse_pass`, `list_missing_fields`, `list_captured_sections`

### Update `_mode_onboarding.md` (37 lines)

Remove the 3 deleted tools from the toolbelt. Add `section_state` tracking instruction. Update the completion rules: instead of "list_missing_fields returns empty AND run_reverse_pass returns passed," completion is now "all 6 sections approved by expert."

### Update `app/agents/orchestrator/modes/onboarding.py`

Remove deleted tools from the tuple. Keep Sonnet 4.6. Toolbelt goes from 10 → 7:
```python
tools=(
    "capture_dossier",
    "append_profile_section",
    "read_dossier",
    "update_capture",
    "import_uploaded_context",
    "generate_profile_narrative",
    "finalize",
    "ask_questions",
)
```

### Add section state tracking

Add a `section_state` JSONB column to `expert_dossiers`:
```python
section_state: Mapped[dict | None] = mapped_column(
    JSONB, nullable=True, default=dict,
    comment="Tracks per-section approval: {method: approved, patient: chatting, ...}"
)
```

Migration: `ALTER TABLE expert_dossiers ADD COLUMN section_state JSONB DEFAULT '{}'::jsonb`

Six keys: `method`, `patient`, `offers`, `proof`, `voice`, `lead_magnet`
Five values: `pending`, `chatting`, `expanding`, `review`, `approved`

### Delete these tool directories:
```
app/agents/_platform/agent_tools/onboarding/run_reverse_pass/
app/agents/_platform/agent_tools/onboarding/list_missing_fields/
app/agents/_platform/agent_tools/onboarding/list_captured_sections/
app/services/onboarding/diagnostics.py
```

---

## FRONTEND CHANGES

### Update `stores/onboarding-store.ts`

Add to CapturedProfile:
```typescript
// Section tracking
currentSection?: number;  // 1-6
sectionApprovals?: Record<string, boolean>;
// Section 6
selectedLeadMagnet?: string;
leadMagnetHeadline?: string;
leadMagnetNextStep?: string;
```

### Update `components/onboarding/profile-panel.tsx`

Replace the 10-phase checklist with 6 sections:
```typescript
const PHASES = [
  { id: "method", label: "You & Your Method", ... },
  { id: "patient", label: "Your Patient", ... },
  { id: "offers", label: "Your Offer", ... },
  { id: "proof", label: "Your Proof", ... },
  { id: "voice", label: "Your Voice & Brand", ... },
  { id: "lead_magnet", label: "Your First Engine", ... },
];
```

Progress: each section = ~17%. 6 sections = 100%.

### Update `components/onboarding/onboarding-engine-picker.tsx`

Replace the organic/paid engine picker with a lead magnet picker:
- Receives 5 AI-generated lead magnet options from IQ (via `ask_questions` tool or a structured chat message)
- Each rendered as a selectable card: name, type, description, "why this fits your audience"
- After selection, 2 quick Qs (headline + next step)
- Then triggers build

### Keep the profile document building pattern

`append_profile_section` already writes to the profile doc that the expert sees on the right. The new flow just calls it less frequently (once per section instead of per-field) but with richer content.

### Keep `inline-question-card.tsx`

This is how `ask_questions` renders — as clickable chips in the chat. It already works. We use it for:
- Weak-response option trees
- Section 6 lead magnet selection
- Any decision point during the conversation

---

## COACHING MOMENTS (add to the new guidelines prompt)

When the expert says:
- **"I help everyone"** → "The experts who grow fastest start with ONE avatar. When content speaks to everyone, it converts no one. Let's start with who gets the best results — we expand from there."
- **"I don't have an offer yet"** → "That's actually great — we build it right. Tell me what you're best at clinically. I'll design the offer around that."
- **"I don't have proof yet"** → "We'll build it as we go. For now, give me your best story — even informal."
- **"I don't know my mechanism name"** → IQ fires `ask_questions` with 3-4 specialty-specific naming options + "Other."
- **"I tried marketing before and it didn't work"** → "What you tried before was probably disconnected tactics. What we're building is a system where everything connects. That's the difference."

---

## WHAT HAPPENS AFTER ONBOARDING

1. `finalize` fires → `handoff_ready=True` → Layer 2 ARQ job dispatches `brand_strategy_lead`
2. 7 strategy deliverables generate automatically (North Star, Growth Blueprint, DR Guide, Organic Strategy, Paid Strategy, Monthly Plan, Builder Handoff Pack)
3. Lead magnet builder agent starts building the selected lead magnet
4. Expert enters the platform. Their profile is complete. Their strategy exists. Their first engine is building.
5. They review and approve the lead magnet, opt-in page, email sequence, and first social posts
6. Assets deploy — lead magnet on a ClinicIQ-hosted URL, social posts queue for connected accounts
7. The lead magnet captures leads. Expert calls/emails leads to nurture them.
8. Later: expert builds out the full value ladder in the Offers section, adds more engines, grows.

---

## EXECUTION ORDER

1. **Backend first:** Write the new `_onboarding_guidelines.md` (~200 lines). Update `_onboarding_agent.md`. Update `_mode_onboarding.md`. Update `modes/onboarding.py` toolbelt. Add `section_state` migration. Delete the 3 tool directories + diagnostics.
2. **Frontend second:** Update the store, checklist, engine picker. The chat streaming and profile doc already work — minimal changes needed there.
3. **Test:** Run through the 6-section flow. Verify `capture_dossier` writes land in the right JSONB sections. Verify `finalize` triggers the ARQ chain. Verify the lead magnet builder receives the spec.

---

## THE NON-NEGOTIABLES

- IQ speaks first with personality. Never an empty screen.
- One question at a time. Never stack.
- Core questions MUST be asked. Follow-ups and probing are ADDITIONAL.
- The `ask_questions` tool is the option tree. Use it for every weak response and every decision point.
- No force-locking. Expert always has agency.
- No framework names spoken to the expert. Ever.
- The lead magnet is a lead capture tool. Expert calls/nurtures leads. Value ladder built later.
- The 6 sections and ~23 core questions are the MINIMUM. IQ probes deeper when it knows the builders need more depth.
