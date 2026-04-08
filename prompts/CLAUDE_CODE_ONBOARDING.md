# ClinicIQ Onboarding — Complete Build Spec for Claude Code
## Build the entire onboarding experience: UI + conversation flow + data capture + all edge cases

Build the `/onboarding` route for ClinicIQ. This is the first screen a new health practitioner sees after signing up. It's a conversational AI onboarding that extracts everything the platform needs to build their growth engine — voice, brand, patients, offers, mechanism, proof — through a natural conversation, not a form.

Tech: React + Tailwind CSS + shadcn/ui. Lucide React icons. Inter font.

---

## SCREEN LAYOUT

Three panels side by side:

### Left Panel — Sidebar Rail (72px wide)
- White background (#F8F9FA), subtle right border (#E5E7EB)
- Items center-aligned, each: 20px Lucide icon + 10px gray (#9CA3AF) label beneath
- Top: Dark rounded square (32px) with Sparkles icon (the logo). No label.
- Below logo: Plus icon + "New", House icon + "Home", BrainCircuit icon + "IQ" (ACTIVE — white circle background, dark icon), GitBranch icon + "Workflows", Users icon + "Teams", FolderOpen icon + "Drive", MoreHorizontal icon + "More"
- Bottom pinned: Settings gear + 28px emerald (#10B981) circle with "SC" initials + tiny "Dr. Sarah Chen"
- **ALL items except IQ are visually disabled** — gray icons, not clickable, cursor-not-allowed. They preview the full platform without letting the expert navigate away during onboarding.

### Center Panel — IQ Claw Chat (~55% of remaining space)
- White background
- **Top bar:** Emerald circular avatar (with brain icon inside) + "IQ Claw" bold (#1F2937) + green dot + "Online" in small green text. Right side: three-dot menu button. Subtle bottom border #E5E7EB.
- **Chat area:** Scrollable. Messages flow top to bottom. IQ Claw messages left-aligned with avatar, in light gray bubbles (#F3F4F6) with dark text. Expert messages right-aligned in light emerald-tinted bubbles (#ECFDF5) with dark text. Proper spacing between turns. Timestamps optional (small gray, right-aligned within bubble).
- **Input bar (fixed bottom):** Rounded-full white input with border (#E5E7EB), 48px height. Placeholder: "Type your answer..." in gray. Right side: Mic icon (gray) + emerald circular send button with ArrowUp icon. Below the input: tiny gray text "IQ Claw can analyze patterns across all your active channels in real-time."

### Right Panel — Progress Card (~45% of remaining space)
- Light gray background (#F8F9FA), subtle left border (#E5E7EB)
- **Sticky** — does not scroll with the chat. Content is fixed in view.
- Everything below is inside a white card with subtle border, 12px radius, padding 24px.

**Progress card contents (top to bottom):**

**Header:** "Building Your Profile" — bold, 18px, #1F2937

**Progress bar:** Full-width bar, 8px height, rounded-full. Gray track (#E5E7EB), emerald fill (#10B981). Starts at 12%. Animates smoothly when percentage increases. Percentage shown to the right: "12%"

**Checklist (vertical, 8px gap between items):**
Each item: status icon + label. Three states:
- ○ Not started — gray empty circle + gray text
- 🔄 In progress — amber (#F59E0B) spinner/loading icon + slightly muted text
- ✅ Complete — emerald (#10B981) checkmark + dark text

Initial state:
- 🔄 Identity & Practice
- ○ Your Story
- ○ Your Voice
- ○ Patient Avatar
- ○ Your Mechanism
- ○ Competitive Landscape
- ○ Offer Stack
- ○ Proof Bank
- ○ Business & Brand

**Estimated time:** "Est. ~25 min remaining" — small gray text. Updates as phases complete.

**Divider** — 1px #E5E7EB, 16px margin top/bottom.

**"WHAT WE KNOW SO FAR"** — uppercase, 11px, #6B7280, letter-spacing 0.05em

This section populates progressively as the conversation captures data. Each item appears with a subtle fade-in animation. Format: bold label in gray (#6B7280) + value in dark text (#1F2937).

Items appear in this order as captured:
- **Specialty:** Functional Medicine
- **Practice:** Telehealth + Austin, TX
- **Origin:** [1-line summary of their story]
- **Character:** Cause-Driven (emerald badge)
- **Voice:** Direct, systems-thinker, reassuring but not soft
- **Signature Phrases:** (shown as small emerald-outlined pills) "your body is sending you signals" · "the whole picture"
- **Banned Words:** (shown as small red-outlined pills) wellness journey · holistic · bio-hacking · optimal
- **Avatar:** Stressed Mom Sarah — Women, 35-50, dismissed by doctors
- **Mechanism:** The Signal Reset Protocol
- **One Big Domino:** "Your body isn't broken — it's stuck in a stress loop nobody identified"
- **Offers:** Entry: Free Assessment · Core: $4,800 · Premium: $12,000
- **Proof Bank:** 3 stories · Score: 62/100

Each new data point fades in when captured. The section grows as the conversation progresses — the expert watches their profile being built in real-time.

**Divider**

**Info card** — light emerald background (#ECFDF5), 8px radius, padding 12px. Lightbulb icon (💡) + text: "Every word of content, every ad, every email your platform produces runs through this profile. The better I know you, the less you'll ever need to edit." Small text, #065F46.

---

## SYSTEM BEHAVIORS (Active Throughout)

### Auto-Save & Resume
- Auto-save triggers after every phase completes. All progress persists to the expert's dossier.
- If they leave and return, IQ Claw picks up where they left off:
  > "Welcome back, Dr. [Name]. We got through [last section] last time. [Previous items] are locked in. Let's pick up with [next phase]."
- Right panel shows all completed sections as ✅ with captured data visible.
- No progress is ever lost. Expert can complete across 1 session or 10.

### Expert Archetype Detection
IQ silently classifies the expert from their first 2-3 responses:

**Reluctant Expert** (short answers, qualifiers, self-deprecating):
→ Use scenario-based questions. Avoid marketing terms. Reflect their words back.

**Confident Communicator** (long answers, declarative, opinionated):
→ Document and precision-tune. Challenge constructively. Slow them on Voice DNA.

**Overwhelmed Practitioner** (slow responses, time-stressed, high agreement):
→ Fast-Start mode. Confirmation questions. Lean on pre-scrape data. 25 min max.

### Three Response Modes (Every Phase)
**Strong answer:** Confirm. Celebrate as asset. Move on.
**Weak/partial:** Build on what they gave + present enhanced version for approval.
**Blank/IDK:** Generate from specialty knowledge + scrape data. Present for approval. Never re-ask.

### Story Mining (Continuous)
Always listening for patient stories in ANY phase. When a story surfaces:
> "I want to hold onto that — that's a powerful story. [summary]. Is there a quote from them that sticks with you?"
Capture to `proof_bank.transformation_stories[]` immediately.

### Enrichment Flagging
After each phase, silently evaluate data quality. If thin: accept it (never block), set `enrichment_needed` flag, summarize at close.

---

## THE CONVERSATION — Phase by Phase

### PHASE 1: OPENING (Identity)
**Progress: 12% → 22% | ~2 min | ✅ Identity**

IQ Claw's first message (visible on page load — NEVER an empty chat):

> "Hi Dr. [Name]. I've been looking at your practice before you arrived.
>
> [1-2 personalized observations from web scrape — specialty, years, what stood out from their site/IG]
>
> [One specific compliment about their content or positioning]
>
> Before we build anything, I need to understand you, your patients, and your approach. This isn't a form — it's a conversation.
>
> Tell me about your practice in your own words — what do you do, who do you help, and how are you set up right now?"

**Captures:** `identity.specialty_primary`, `identity.practice_model`, `identity.geographic_scope`, `identity.years_in_practice`

**Weak:** "I'm a functional medicine doctor in Austin." → IQ fills from scrape: "Your website shows you focus on hormone health, telehealth plus in-office, since about 2015 — still accurate?"

**Blank:** Generate from scrape data, present for confirmation.

**Confirm + transition:** "Got it — [summary]. Now I want to go deeper."

---

### PHASE 2: ORIGIN STORY
**Progress: 22% → 32% | ~3-5 min | ✅ Your Story**

> "A lot of the best health experts got into this work because of something personal — either they went through it themselves, someone they loved did, or they saw something in the system they couldn't walk away from.
>
> Is there a story behind why you do what you do?"

**Captures:** `story.origin.before_state`, `story.origin.trigger_event`, `story.origin.realization`, `story.origin.emotional_truth`, `story.origin.bridge_to_patient`, `brand.character_type` (inferred)

**Strong:** "That story — [specific element] — that's your Epiphany Bridge. Patients will trust you before they walk through the door because of this. 📖 Origin Story — locked."

**Weak:** "Was there a specific patient, or a specific moment, where it became undeniably clear you had to do this differently?"

**Blank:** "That's fine — not everyone has a dramatic origin. Based on [specialty], what I'd put here is: '[generated framing].' Feel close?"

Archetype classification locks after this phase.

---

### PHASE 3: CLINICAL PHILOSOPHY
**Progress: 32% → 40% | ~2-3 min | ✅ Philosophy**

> "What do you believe about healing that most doctors, specialists, or even other practitioners in your field get wrong?"

**Captures:** `clinical_philosophy.core_belief`, `clinical_philosophy.what_conventional_gets_wrong`, `clinical_philosophy.what_makes_them_different`

**Strong:** "So if I'm hearing you right — [restate sharply]. That's not just a philosophy. That's a positioning statement."

**Weak** ("I take a more thorough approach"): "Give me a specific example. A patient comes in with [condition common to their specialty] after seeing two other [specialists]. What's the first thing you look at that nobody else did?"

**Blank:** Generate from specialty norms, present for confirmation.

---

### PHASE 4: VOICE DNA CONFIRMATION
**Progress: 40% → 52% | ~3 min | ✅ Your Voice (🔒 Locked)**

If writing-vs-speaking split detected from mass ingestion:
> "Your written content sounds more [measured/clinical]. But in this conversation you're more [direct/punchy]. Which one is the real you?"

Then present the full voice profile:
> "I've been paying attention to how you communicate. Tell me if this feels right.
>
> **Your tone:** [detected]
> **Your rhythm:** [detected]
> **Phrases that are uniquely yours:** [3-5 as pills]
> **Words you never use:** [detected avoidances if mass ingestion ran]
>
> Does this feel like you?"

Then the critical question:
> "What words do you absolutely NEVER want in your marketing? The ones that make you cringe."

**Captures:** `voice_dna.tone_primary`, `tone_secondary`, `sentence_rhythm`, `vocabulary_register`, `formality_level`, `emotional_register`, `conviction_level`, `humor_level`, `authority_style`, `signature_phrases[]`, `words_they_avoid[]`, `sample_extracts[]` (3-5 verbatim quotes from conversation), `writing_vs_speaking_difference`, `primary_voice_source`, `voice_confidence_score`

**Lock:** "Voice DNA — locked. 🗣️ Every piece of content will sound like you on your best day."

**Weak on bans:** "Most [specialty] practitioners hate words like 'holistic,' 'wellness journey,' 'optimal.' Any of those bother you?"

---

### PHASE 5: PATIENT AVATAR
**Progress: 52% → 62% | ~4-5 min | ✅ Patient Avatar**

> "Describe the patient who gets the absolute best results with you — not demographics, the human being. What are they dealing with, what have they tried, and what does life look like before they find you?"

Follow-up probes (one at a time, based on gaps):
- Vague symptoms: "Walk me through a bad day for this person — from the moment they wake up."
- Missing emotions: "What have they stopped telling people about how they feel? What are they afraid will happen?"
- Missing internal dialogue: "What do they say to themselves at 2am?"
- Missing failed attempts: "When they come to you after other providers — what do they tell you about why nothing worked?"
- **Explicitly extract Three False Beliefs:** "What beliefs do YOUR patients carry that keep them stuck? Things like 'this is just aging' or 'I've tried everything' or 'I can't afford it.'"

**Captures (all 4 layers):**
- `avatar.name` (IQ names the persona)
- `avatar.demographics`, `avatar.awareness_level`
- Layer 1: `avatar.symptom_stack` (specific daily reality)
- Layer 2: `avatar.emotional_core` (frustration, fear, shame, hope)
- Layer 3: `avatar.belief_system` including `false_belief_vehicle`, `false_belief_internal`, `false_belief_external`
- Layer 4: `avatar.internal_dialogue[]`
- `avatar.deepest_desire`, `avatar.transformation_identity`
- Also captures: `competitive_landscape.common_failure_modes[]`, `competitive_landscape.patient_language_about_failures[]`

**Present:** "Here's your primary avatar — **Stressed Mom Sarah**: [formatted card with all 4 layers]. Does she feel real?"

**Weak** (demographics only): "Pick one specific patient you're thinking of. What does her morning look like? What's her biggest frustration beyond symptoms?"

---

### PHASE 6: MECHANISM & ONE BIG DOMINO
**Progress: 62% → 72% | ~3-4 min | ✅ Your Mechanism**

> "When a patient comes to you after failing with other providers — what's the first thing you look at that nobody else looked at?"

**Specialty-adapted follow-up:**
- Functional medicine: "What test do you run that their regular doctor never ordered?"
- Chiropractic: "What do you see in their spine or nervous system that others missed?"
- Dentistry/TMJ: "What connection do you find between their dental issue and overall symptoms?"
- Physical therapy: "What movement pattern do you identify that everyone else treated around?"
- Med spa: "What underlying cause of the skin/aging issue can't topical treatments touch?"
- Mental health: "What physiological driver behind the anxiety/depression is nobody testing for?"
- Nutrition: "What metabolic pattern do you see that standard diets never fix?"

Then: "If you had to explain your approach in one sentence — across the desk, not on your website — what would you say?"

Then: "Does your method have a name?"

Then the One Big Domino: "What's the one thing that, if your ideal patient truly believed it, would change everything? The belief that makes all other doubts fall away."

**If broad:** "Make it specific to YOUR patients. Not 'root cause medicine.' What specific belief changes the game for [avatar name]?"

**If still generic:** "Think about the last patient who had a breakthrough moment — their face changed. What did you tell them?"

**Dig-deeper protocol (if mechanism is generic after above):**
1. "Tell me about the result you're most proud of — what did you do differently?"
2. "What do most [practitioners] get wrong?"
3. "What's the thing you learned that changed how you practice?"
4. "What do patients say about you that they wouldn't say about their last provider?"

If still generic after all four: flag `mechanism.differentiation_strength: low`, proceed honestly.

**Captures:** `mechanism.core_approach`, `mechanism.why_it_works`, `mechanism.natural_language`, `mechanism.name`, `mechanism.vs_conventional`, `mechanism.positioning_type`, `mechanism.differentiation_strength`, `brand.one_big_domino`, `brand.one_big_domino.supporting_beliefs[]`, `brand.one_big_domino.opposing_beliefs[]`

**Lock:** "That's your One Big Domino: '[belief].' Every ad, email, webinar, content piece points back to this. 🎯 Locked."

---

### PHASE 7: COMPETITIVE LANDSCAPE
**Progress: 72% → 76% | ~2 min | ✅ Competitive Landscape**

> "You mentioned [avatar name] tried [what came up in Phase 5]. Let me get the full picture — what does the typical journey look like before they find you? What does their doctor tell them, what do they try on their own, what other options do they consider?"

**Captures:** `competitive_landscape.conventional_path`, `competitive_landscape.alternative_competitors`, `competitive_landscape.diy_approaches`, enriches `common_failure_modes[]` and `patient_language_about_failures[]`

If Phase 5 already covered most of this: "Based on what you told me, I've captured: [summary]. Anything I'm missing?" Quick confirm, move on.

---

### PHASE 8: OFFER ARCHITECTURE
**Progress: 76% → 84% | ~3-4 min | ✅ Offer Stack**

One tier at a time. Never stacked.

**Entry:** "When someone discovers you, what's the first thing they can do? A free assessment? Low-cost consult? A guide?"
→ "When someone goes through that — what shifts for them?"

**Core:** "Your core program — what does it look like? How long? What does the patient experience?"
→ "What do you charge?" → "How long until they feel the first shift?"

**Premium:** "Do you have a highest-level offering?"
→ If not: "No problem. Something for later."

For each tier: capture `name`, `price`, `before_state`, `after_state`, `timeline_to_first_result`, `fulfillment_model`

**Weak** (features only): "Those are the components. Now through the patient's eyes: when [avatar name] starts, what is she feeling? 12 weeks later, what's different about her LIFE?"

**Present:** "Here's your offer ladder: 🟢 Entry: [name] $[price] · 🔵 Core: [name] $[price] · 🟣 Premium: [name] $[price]. Capture it? 💰 Locked."

---

### PHASE 9: PROOF BANK
**Progress: 84% → 90% | ~3 min | ✅ Proof Bank**

> "Tell me about a patient transformation that still gets you emotional — someone who came in struggling and left a different person."

Probes (one at a time): "What was their life like before?" → "What had they tried?" → "What was the turning point?" → "How long?" → "Their actual words?"

After first story: "Is there one even more dramatic — your biggest before/after? Or a total skeptic who got results?"

Then inventory: "What other proof? Reviews, video testimonials, before-after documentation, research, media?"

**Captures:** `proof_bank.transformation_stories[]` (structured: avatar_match, before_state, treatments_tried, turning_point, result, timeline, direct_quote), `most_dramatic_transformation`, `fastest_result`, `skeptic_to_believer`, `testimonials_text[]`, `video_testimonials[]`, `media_mentions[]`, `collective_results_stats`, `proof_bank_depth_score`

**Celebrate:** "That story — that's a webinar slide. That's an ad. That's an email. 🏆"

**If thin (<40 score):** Flag `enrichment_needed`, mention at close.

---

### PHASE 10: THE 90-SECOND DEMO
**Progress: 90% → 93% | The trust transaction**

> "I have enough to show you something. Give me 90 seconds."

Loading animation (3-5 sec — pulsing emerald glow, not generic dots).

IQ delivers one Instagram post in their voice, targeting their avatar, using their mechanism:

**Inline Instagram preview card** (white card, border, rounded-xl):
- Header: emerald "SC" avatar + "dr.sarahchen" + "Scheduled — Tomorrow 9am"
- Image: emerald gradient with large white italic text using one of their signature phrases
- Caption: written in their exact voice/rhythm/vocabulary, targeting avatar's emotional core, mechanism language woven in, CTA matching entry offer
- Below: "That's your voice, your mechanism, your patient. Does it feel like you?"

If they love it: "Good. This is minute 25. Imagine what 174 agents do with a full week."
If they want changes: capture corrections, update Voice DNA live.

---

### PHASE 11: QUICK CAPTURE
**Progress: 93% → 97% | ~2-3 min | ✅ Business & Brand**

> "Almost there. What do you already have out there — podcast, YouTube, social, email list, funnels, lead magnets?"

> "How are new patients finding you right now — and what's the biggest thing between you and the growth you want?"

> "Paint the picture: three years, this works perfectly — what does the practice look like?"

> "Your brand visuals — I pulled your logo and colors from your site: [show]. Does this represent you, or different direction?"

**Captures:** `content_audit.*`, `business_context.current_traffic_sources`, `business_context.biggest_growth_obstacle`, `dream_practice.*`, `visual_dna.brand_colors[]`, `visual_dna.logo`, `visual_dna.aesthetic_description`

---

### PHASE 12: THE CLOSE
**Progress: 97% → 100%**

> "Here's what I now know about you:
>
> You're [name], a [specialty] practitioner who believes [One Big Domino]. Your approach — [mechanism] — works because [why]. Your ideal patient is [avatar name]: [1-sentence description]. Your core offer takes them from '[Before]' to '[After]' in [timeline]. Your voice is [tone] — '[signature phrase].'
>
> This powers every output the platform builds.
>
> Your Brand Strategy and Growth Strategy agents are generating your complete marketing blueprint right now. Brand North Star, Monthly Master Plan, content calendar, messaging briefs — all from what you just told me. First content batch ready within the hour.
>
> The more you use ClinicIQ, the smarter it gets. After 30 days it knows your audience better than any agency. After 90 days it knows things no human brain can hold. That compounds. Starting now.
>
> Welcome to ClinicIQ."

If enrichment flags exist:
> "A few areas we can deepen in a follow-up: [2-3 items]. I'll check in next week. Nothing's blocked — your content is already being built."

**Right panel:** Progress 100%, celebration animation (confetti or emerald glow), Dossier Score (e.g., 74/100), [Enter ClinicIQ →] large emerald button.

Clicking it → navigates to `/` (main workspace). All sidebar items unlock.

---

## TIMING

| Phase | Duration | Running Total |
|-------|----------|--------------|
| 1. Opening | ~2 min | 2 min |
| 2. Origin Story | ~3-5 min | 5-7 min |
| 3. Philosophy | ~2-3 min | 7-10 min |
| 4. Voice DNA | ~3 min | 10-13 min |
| 5. Avatar | ~4-5 min | 14-18 min |
| 6. Mechanism | ~3-4 min | 17-22 min |
| 7. Competitive | ~2 min | 19-24 min |
| 8. Offers | ~3-4 min | 22-28 min |
| 9. Proof Bank | ~3 min | 25-31 min |
| 10. Demo | ~2 min | 27-33 min |
| 11. Quick Capture | ~2-3 min | 29-36 min |
| 12. Close | ~1 min | 30-37 min |

---

## PROGRESS MAP

| Phase | % | Checklist | "What We Know" Adds |
|-------|---|-----------|-------------------|
| Pre-scrape | 12% | — | Name |
| 1. Opening | 22% | ✅ Identity | Specialty, Practice, Location |
| 2. Story | 32% | ✅ Story | Origin, Character type |
| 3. Philosophy | 40% | ✅ Philosophy | Core belief |
| 4. Voice | 52% | ✅ Voice 🔒 | Tone, Phrases, Bans |
| 5. Avatar | 62% | ✅ Avatar | Avatar card |
| 6. Mechanism | 72% | ✅ Mechanism | Name, One Big Domino |
| 7. Competitive | 76% | ✅ Landscape | (enriches existing) |
| 8. Offers | 84% | ✅ Offers | 3 tiers |
| 9. Proof | 90% | ✅ Proof | Stories, score |
| 10. Demo | 93% | ✨ Content | — |
| 11. Capture | 97% | ✅ Business | Audience, vision |
| 12. Close | 100% | 🎉 Done | Synthesis, score |

---

## PRINCIPLES

1. IQ Claw always speaks first. Never empty chat.
2. One question at a time. Never stack.
3. Never feel like a form.
4. Expert approves or adjusts — never originates from scratch.
5. Every capture celebrated as the asset it is.
6. Progress always saved. Always resumable.
7. Adapt to archetype. Fast for overwhelmed. Deep for willing.
8. 90-second demo is the trust transaction.
9. Never stall, never repeat, never make them stuck.
10. Stories mined continuously across all phases.
11. Weak data flagged, never blocked. Enrichment fills gaps later.
12. Right panel proves value in real-time.
