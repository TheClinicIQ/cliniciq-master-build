# ClinicIQ — Complete Onboarding Flow v2
## Every step, every message, every data capture, every edge case
**Purpose:** Complete specification for Claude Code to build the onboarding conversation system. Covers the exact flow, adaptive behavior, weak answer handling, save/resume, archetype detection, and all data capture points.

---

## SYSTEM BEHAVIORS (Active Throughout Entire Onboarding)

These behaviors run continuously from the first message to the close. They are not phase-specific — they apply everywhere.

### Auto-Save & Resume
- **Every phase completion triggers an auto-save.** The expert's progress is persisted to their dossier immediately. Nothing is ever lost.
- **If the expert leaves mid-session** (closes browser, loses connection, runs out of time), their progress is fully preserved.
- **When they return,** IQ Claw picks up exactly where they left off:
  > "Welcome back, Dr. [Name]. Last time we got through [last completed section]. Your [completed items] are locked in. Let's pick up where we left off — [next phase topic]."
- The right panel shows all previously completed sections as ✅ with the captured data visible in "What We Know So Far."
- **No progress is ever lost. No work is ever repeated.** The expert can complete onboarding across 1 session or 10 sessions.

### Expert Archetype Detection (First 2-3 Exchanges)
IQ Claw silently classifies the expert into one of three archetypes based on their first 2-3 responses. The archetype determines pacing and question style for the rest of the session.

**Detection signals:**

| Signal | Reluctant Expert | Confident Communicator | Overwhelmed Practitioner |
|--------|-----------------|----------------------|------------------------|
| Response length | <40 words avg | >100 words avg | <30 words, incomplete sentences |
| Qualifiers | 2+ per response ("I think," "maybe," "sort of") | Declarative ("The problem is..." "What I've found...") | High agreement ("Yeah sounds right") |
| Self-reference | Self-deprecating ("I'm not a marketer") | Opinionated ("Nobody else does this") | Time-stressed ("Can we do this quick?") |
| Latency | Normal | Fast, may redirect conversation | >60 seconds between messages |

**Adaptation rules:**

| Archetype | Pacing | Question Style | Key Behavior |
|-----------|--------|---------------|-------------|
| **Reluctant** | Normal. Don't rush. | Scenario-based ("Talk to me like you'd talk to a patient who..."). Avoid marketing terminology. | Reflect their words back in marketing terms to help them discover their voice. Push gently past short answers. |
| **Confident** | Match their speed but slow them on Voice DNA. | Ask for rules behind instincts ("You avoid 'holistic' — what is it about that word?"). Challenge constructively. | Document and precision-tune rather than extract. Watch for thin spots in offers and proof they gloss over. |
| **Overwhelmed** | Fast. 25 minutes max. | Confirmation-style ("Your main offer is X — right?"). Batch related questions. Lean on pre-scrape data. | Default to Fast-Start. Mark `enrichment_priority: high`. Schedule follow-up session. Don't force depth — accuracy over completeness. |

**Fallback:** If signals are mixed after 3 exchanges, default to Reluctant Expert approach (safest — draws out deeper answers).

### Three Response Handling Modes (Every Phase)
Every phase uses these three modes. The specific strong/weak/blank handling is detailed within each phase, but the principle is universal:

**Mode 1 — Strong Answer:** Expert gives a rich, specific response.
→ Confirm what you heard. Extract the data. Celebrate the asset. Move on.

**Mode 2 — Weak/Partial Answer:** Expert gives a vague or surface-level response.
→ Build on what they gave. Complete it with IQ Claw's knowledge of their specialty. Present the enhanced version for approval:
> "I heard you say [X]. Let me build on that — does this capture it better: [enhanced version]? Adjust anything that doesn't fit."

**Mode 3 — Blank/"I Don't Know":** Expert goes blank or says they don't know.
→ Do NOT re-ask. Generate immediately from specialty knowledge + scrape data. Present for approval:
> "No problem — based on what I know about [specialty] and what I've seen from your practice, here's what I'd put here: [generated answer]. Does that feel right, or want me to take it a different direction?"

### Story Mining (Continuous)
IQ Claw is always listening for patient stories regardless of which phase is active. Triggers:
- Expert mentions a patient by first name or condition
- Expert describes a result ("she got off her meds," "he lost 40 pounds")
- Expert references a dramatic before/after or a skeptic who came around

When a story surfaces mid-conversation in ANY phase:
> "I want to hold onto that — that's a powerful story. Let me make sure I captured it: [summary]. Is there a quote from them — something they actually said — that sticks with you?"

Story gets captured to `proof_bank.transformation_stories[]` immediately, regardless of current phase.

### Enrichment Flagging
After each phase, IQ Claw silently evaluates data quality against Tier 1 thresholds (from the Onboarding Intelligence Kit). If a phase completes with thin data:
- The field is accepted (never blocks progress)
- An `enrichment_needed` flag is set on the specific fields
- At the close, any enrichment flags are summarized and an enrichment session is scheduled for 5-7 days later
- The expert never feels like they failed a section

---

## PRE-ONBOARDING (Before First Login)

When the expert submits the sign-up form, two processes fire:

1. **Web Scraper** — Analyzes website URL. Extracts: name, specialty, years in practice, existing offers, brand colors, logo, patient testimonials from testimonials page, "about" page content, practice model (telehealth/brick-and-mortar/hybrid), geographic scope.

2. **Voice DNA Mass Ingestion** — If Instagram handle was provided: analyzes last 90 days of captions, engagement patterns, top-performing content, sentence rhythm statistics, vocabulary register distribution, emotional intensity patterns, signature phrases (any phrase appearing 3+ times across posts), probable vocabulary avoidances, and the writing-vs-speaking voice split (comparing IG captions to any video/podcast transcripts found).

By the time they reach `/onboarding`, IQ Claw has a pre-populated partial dossier. Progress starts at 12%, not 0%.

---

## THE ONBOARDING SCREEN

Three panels:
- Left: Sidebar rail (72px) — all items visible but grayed/disabled except IQ (active). Communicates "there's a full platform waiting after this."
- Center: IQ Claw chat (~55% of remaining space)
- Right: Live progress panel (~45%)

### Right Panel — Live Progress Card (sticky, updates every phase)
- "Building Your Profile" header
- Progress bar (starts at 12%, emerald fill)
- Checklist sections: Identity ○ → 🔄 → ✅, Your Story ○, Voice DNA ○, Patient Avatar ○, Your Mechanism ○, Offer Stack ○, Proof Bank ○, Brand & Strategy ○
- "Est. ~22 min remaining" (updates as phases complete)
- Divider
- "WHAT WE KNOW SO FAR" — data populates live as captured (appears with subtle fade-in animation)
- Divider
- Info card: "💡 Every word of content, every ad, every email your platform produces runs through this profile. The better I know you, the less you'll ever need to edit."

---

## PHASE 1: THE OPENING (Identity & Practice)
**Progress: 12% → 22% | Time: ~2 minutes | Checklist: ✅ Identity**

### IQ Claw's First Message (visible on page load — never an empty screen)

> "Hi Dr. [Name]. I've been looking at your practice before you arrived.
>
> [PERSONALIZED FROM SCRAPE — 1-2 specific observations. Examples:]
> - "You've been practicing functional medicine in Austin for about 11 years. Your website leads with a hormone reset protocol."
> - "Your Instagram cortisol content outperforms everything else by about 3x on saves."
> - "That 'your body isn't broken' line on your About page — that's the kind of mechanism language that stops people mid-scroll."
>
> [ALWAYS end with a genuine, specific compliment about something in their positioning or content.]
>
> Before we build anything, I need to understand you, your patients, and your approach. This isn't a form — it's a conversation. Everything you tell me powers every output the platform produces.
>
> Let's start simple: tell me about your practice in your own words — what do you do, who do you help, and how are you set up right now?"

### Data Captured
- `identity.full_name` (confirmed from scrape)
- `identity.specialty_primary`
- `identity.specialty_secondary` (if mentioned)
- `identity.practice_model` (telehealth / brick-and-mortar / hybrid)
- `identity.geographic_scope` (local / regional / national / virtual)
- `identity.years_in_practice`
- `identity.practice_name`

### Weak Answer Handling
**If they give a one-liner** ("I'm a functional medicine doctor in Austin"):
> "Got it. Your website shows you focus on hormone health and thyroid — and you're running a hybrid model, telehealth plus in-office. Still accurate? Anything I should add?"

**If they go blank or seem unsure what to say:**
> "No worries — I already pulled some info from your site. You're [name], [specialty], based in [location], practicing since approximately [year]. Your website mentions [key service]. Does that sound right, and is there anything you'd add?"

### IQ Claw Confirms
> "Got it — [1-2 sentence summary]. [Any scrape data presented for confirmation.] Perfect. Now I want to go deeper."

### Right Panel Updates
- ✅ Identity & Practice
- Progress: 22%
- "What We Know So Far" adds: Name, Specialty, Practice Model, Location

### Archetype Detection Note
After this response, IQ Claw has the first signal for archetype classification. It uses response length, qualifier count, and energy to start the classification. Full classification locks after Phase 2.

---

## PHASE 2: THE ORIGIN STORY (Expert Personal Story)
**Progress: 22% → 32% | Time: ~3-5 minutes | Checklist: ✅ Your Story**

### IQ Claw

> "A lot of the best health experts got into this work because of something personal — either they went through it themselves, someone they loved did, or they saw something in the system that they couldn't walk away from.
>
> Is there a story behind why you do what you do?"

### Data Captured
- `story.origin.before_state` — what their life/career was like before
- `story.origin.trigger_event` — the specific moment
- `story.origin.realization` — what they understood that changed everything
- `story.origin.emotional_truth` — how it felt
- `story.origin.bridge_to_patient` — why it drives their work today
- `brand.character_type` — inferred: `reluctant_hero` | `cause_driven` | `reporter`

### Strong Answer
If they share a vivid story with emotional specificity:
> "That's one of the most important things you'll tell me in this entire session. That story — [specific element] — that's your Epiphany Bridge. It's the moment that makes patients trust you before they ever walk through your door. I'm capturing every detail. 📖 Origin Story — locked."

### Weak Answer
If they give something surface ("I just always liked helping people" or "I went to school for this"):
> "Was there a specific patient, or a specific moment, where it became undeniably clear that you had to do this differently? A case that surprised you, or a moment where you saw something other providers missed?"

### Blank/IDK
> "That's totally fine — not everyone has a dramatic origin story. Some of the most effective practitioners I've worked with simply saw patterns in their patients that nobody else was connecting. Based on your specialty in [area], what I'd put here is: '[generated origin framing based on their specialty norms].' Does that feel close?"

### Archetype Lock
After Phase 2, IQ Claw has enough data to lock the archetype classification. From this point forward, pacing and question style adapt based on the detected archetype.

### Right Panel Updates
- ✅ Your Story
- Progress: 32%
- Adds: Origin summary (1-2 lines), Character type badge

---

## PHASE 3: CLINICAL PHILOSOPHY
**Progress: 32% → 40% | Time: ~2-3 minutes | Checklist: ✅ Philosophy**

### IQ Claw

> "Based on your story, it's clear you see things differently than most practitioners.
>
> What do you believe about healing that most doctors, specialists, or even other practitioners in your field get wrong?"

### Data Captured
- `clinical_philosophy.core_belief`
- `clinical_philosophy.what_conventional_gets_wrong`
- `clinical_philosophy.what_makes_them_different`
- Early signals for `mechanism.core_approach` (IQ begins detecting the mechanism here)

### Strong Answer
> "So if I'm hearing you right — [restate their philosophy in clear, sharp language]. That's not just a clinical philosophy. That's a positioning statement. That's what makes your approach different from every other [specialty] practitioner. I'm building from this."

### Weak Answer
If vague ("I just take a more thorough approach"):
> "Give me a specific example. A patient comes in with [common condition for their specialty] and they've already been to two other [specialists]. What's the first thing you look at that nobody else looked at?"

### Blank/IDK
> "Based on your specialty, most [specialty type] practitioners who get great results share a common belief: [generated philosophy based on specialty norms — e.g., 'that the body has an innate ability to heal when the right signals are identified and the interference is removed']. Does that resonate with how you think about it, or is your perspective different?"

### Right Panel Updates
- ✅ Clinical Philosophy
- Progress: 40%
- Adds: Core belief summary, early mechanism language

---

## PHASE 4: VOICE DNA CONFIRMATION
**Progress: 40% → 52% | Time: ~3 minutes | Checklist: ✅ Your Voice (🔒 Locked)**

By this point, IQ Claw has been passively analyzing the expert's communication for 10+ minutes across 3 phases. The Voice DNA Mass Ingestion (if it ran) provides statistical baseline data from their existing content. Now IQ Claw surfaces everything and asks the expert to confirm.

### Writing vs. Speaking Split Check
If mass ingestion detected a significant difference between written content voice and spoken/conversational voice:

> "Before I show you your voice profile — I noticed something interesting. Your written content (Instagram captions, website) sounds more [description — e.g., 'measured and clinical']. But in this conversation, you're more [description — e.g., 'direct, punchy, and emotionally expressive'].
>
> Which one feels more like the real you? That's the voice we want to build from."

Most experts point to their spoken voice. Lock `voice_dna.primary_voice_source` accordingly.

### IQ Claw Presents the Voice DNA Profile

> "I've been paying attention to how you communicate — not just what you've said, but how you say it. Here's what I've picked up. Tell me if this feels right.
>
> **Your tone:** [Detected — e.g., 'Direct and confident. You make declarative statements. You don't hedge. When you talk about patients, genuine warmth comes through — but you lead with clarity, not softness.']
>
> **Your rhythm:** [e.g., 'You mix short punchy statements with longer explanatory stretches. You make a claim, then you build the case. That's a really strong natural pattern.']
>
> **Phrases that are uniquely yours:** [3-5 signature phrases shown as pills/tags]
>
> **Words I noticed you never use:** [If mass ingestion found avoidances, show them. If not, skip this line.]
>
> Does this feel like you? Anything I got wrong or missed?"

### Then the Critical Ban Question

> "One more thing — what words do you absolutely NEVER want to see in your marketing? The ones that make you cringe when a competitor uses them."

### Data Captured
- `voice_dna.tone_primary` + `tone_secondary`
- `voice_dna.sentence_rhythm` (short-punchy / long-flowing / mixed-dynamic)
- `voice_dna.vocabulary_register` (clinical / plain-language / casual / mixed-professional)
- `voice_dna.formality_level` (high / medium / low)
- `voice_dna.emotional_register`
- `voice_dna.conviction_level` (high-conviction / moderate / hedging)
- `voice_dna.humor_level` (none / dry / warm)
- `voice_dna.authority_style` (credential-first / results-first / story-first / teaching-first)
- `voice_dna.signature_phrases[]` (confirmed array)
- `voice_dna.words_they_avoid[]` (confirmed array)
- `voice_dna.sample_extracts[]` (3-5 verbatim quotes from the conversation — the highest-signal, most distinctive things they said)
- `voice_dna.writing_vs_speaking_difference` (true/false)
- `voice_dna.primary_voice_source` (spoken / written / no_difference)
- `voice_dna.voice_confidence_score` (calculated from data density)

### Lock Celebration
> "Voice DNA — locked. 🗣️ Every piece of content the platform builds for you from this point forward will sound like you wrote it on your best day."

### Weak Answer to Ban Question
If they say "I don't know" or "nothing comes to mind":
> "Most [specialty] practitioners I work with have strong feelings about words like 'holistic,' 'wellness journey,' 'optimal,' or 'biohacking.' Any of those bother you? Or are there other terms that feel off for your brand?"

### Right Panel Updates
- ✅ Your Voice (🔒 Locked badge)
- Progress: 52%
- Adds: Tone description, Signature Phrases (emerald pills), Banned Words (red pills), Voice Confidence Score

---

## PHASE 5: PATIENT AVATAR (Deep Psychology)
**Progress: 52% → 62% | Time: ~4-5 minutes | Checklist: ✅ Patient Avatar**

### IQ Claw

> "Now that I know you deeply, let's talk about who you help. Not demographics — the human being.
>
> Describe the patient who gets the absolute best results with you — not just who you work with, but who you light up for. What are they dealing with, what have they tried, and what does life look like for them before they find you?"

### Follow-Up Probes (one at a time, based on what's missing from their response)

**If symptom stack is vague** ("fatigue, brain fog"):
> "Walk me through a bad day for this person — from the moment they wake up. What's the first thing they notice? What falls apart by lunch? What do they cancel in the evening?"

**If emotional core is missing:**
> "What's the thing they've stopped telling people about how they feel? And what are they afraid will happen if nothing changes?"

**If internal dialogue is missing:**
> "What do they say to themselves at 2am — the thing they think but won't say out loud to anyone?"

**If failed attempts aren't surfaced:**
> "When they come to you after trying other providers — what do they tell you about why nothing worked? What did their doctor tell them?"

**Explicitly extract the Three False Beliefs:**
> "People in this situation usually carry specific beliefs that keep them stuck. Things like 'this is just aging' or 'I've tried everything' or 'I can't afford another program.' What are the beliefs YOUR patients carry that you have to break through?"

This captures:
- `avatar.false_belief_vehicle` — why they don't believe the approach will work
- `avatar.false_belief_internal` — why they don't believe THEY can succeed
- `avatar.false_belief_external` — what external obstacles they see (cost, time, family, access)

### Data Captured (All 4 Psychological Layers)
- `avatar.name` — IQ Claw names the persona: "Let's call her Stressed Mom Sarah"
- `avatar.demographics` (age range, gender skew, income context, family status)
- `avatar.awareness_level` (inferred from their description of how patients find them)
- **Layer 1:** `avatar.symptom_stack` — daily reality, specific and vivid
- **Layer 2:** `avatar.emotional_core` — frustration, fear, shame, hope (each specifically captured)
- **Layer 3:** `avatar.belief_system` — including the three false beliefs explicitly
- **Layer 4:** `avatar.internal_dialogue[]` — exact phrases from their head
- `avatar.daily_frustrations` — specific moments and situations
- `avatar.deepest_desire` — specific identity-level transformation ("feel like myself again")
- `avatar.transformation_identity` — who they want to become

### Also Captured Here (feeds Competitive Landscape)
- `competitive_landscape.common_failure_modes[]` — what other approaches got wrong (from "what they tried before")
- `competitive_landscape.patient_language_about_failures[]` — the exact phrases patients use ("my labs were normal but I still feel awful")
- `competitive_landscape.conventional_path` — what the standard medical journey looks like for this patient

### IQ Claw Presents the Avatar Card

> "Here's your primary avatar:
>
> **Stressed Mom Sarah** — Women, 35-50, Problem-Aware
>
> **Her daily reality:** [specific symptom stack]
> **What she feels underneath:** [emotional core — frustration, fear, shame, hope]
> **What she believes:** [three false beliefs]
> **What she says to herself:** [internal dialogue quotes]
> **What she's tried:** [failed attempts]
> **What she really wants:** [deepest desire / transformation identity]
>
> Does she feel real? Anything to adjust?"

### Weak Answer Handling
If they describe demographics only ("Women in their 40s with thyroid issues"):
> "Got it — now make her real for me. Pick one specific patient you're thinking of. Not her name — just her life. What does her morning look like? What's her biggest frustration that has nothing to do with medical symptoms? What keeps her up at night?"

### Enrichment Flag
If after probing, the emotional core and internal dialogue layers are still thin: accept what's there, flag `avatar.emotional_depth: enrichment_needed`. Don't force it — the expert may need to warm up to this kind of thinking.

### Right Panel Updates
- ✅ Patient Avatar
- Progress: 62%
- Adds: Avatar card (name, age, core pain, core desire, awareness level)

---

## PHASE 6: THE MECHANISM & ONE BIG DOMINO
**Progress: 62% → 72% | Time: ~3-4 minutes | Checklist: ✅ Your Mechanism**

### IQ Claw

> "This is the most important question in the whole session.
>
> You've told me about your patients and what they're dealing with. You've told me what conventional medicine gets wrong.
>
> When a patient comes to you after failing with other providers — what's the first thing you look at that nobody else looked at?"

### Specialty-Adapted Follow-Up
Based on detected specialty, IQ Claw asks a tailored second question:

| Specialty | Follow-Up |
|-----------|----------|
| Functional medicine | "What test do you run that their regular doctor never ordered?" |
| Chiropractic | "What do you see in their spine or nervous system that the other chiropractors missed?" |
| Dentistry / TMJ | "What connection are you finding between their dental issue and their overall symptoms?" |
| Physical therapy | "What's the movement pattern or compensation you identify that everyone else treated around?" |
| Med spa / aesthetics | "What's the underlying cause of the skin/aging issue that topical treatments can't touch?" |
| Mental health | "What's the physiological driver behind the anxiety/depression that nobody's testing for?" |
| Nutrition | "What's the metabolic pattern you see that a standard diet approach will never fix?" |
| General / Other | "Why does your approach work when everything else they tried didn't?" |

### Then the Natural Language Question

> "If you had to explain your approach to a patient in one sentence — the way you'd say it across the desk, not how you'd write it on your website — what would you say?"

### Then the Naming Question

> "Does your method have a name? If you were going to name it, what would you call it?"

### Then the One Big Domino

> "Now here's the question that ties it all together: What's the one thing that, if your ideal patient truly believed it, would change everything for them? The belief that, once they accept it, all their other doubts fall away."

**If the answer is too broad** ("Health is about root cause"):
> "Make it specific to YOUR patients. Not 'health is about root cause' — every functional medicine doc says that. What's the specific belief that changes the game for the [avatar name] you just described?"

**If still generic:**
> "Think about the last patient who had a breakthrough moment in your office — the moment their face changed. What did you tell them that shifted everything?"

### The Dig-Deeper Protocol (If Mechanism Is Generic)
If after the above questions, the mechanism still sounds like an improvement rather than a new vehicle ("we take a more thorough approach," "we spend more time"):

1. "Tell me about the patient result you're most proud of — the one that surprised even you. What did you do differently?"
2. "What do most [practitioners in their specialty] get wrong? What frustrates you about how your field approaches this?"
3. "What's the thing you learned or discovered that changed how you practice — that you wish you'd known from day one?"
4. "What do your patients say about you that they wouldn't say about the last provider they saw?"

If all four still produce generic responses: flag `mechanism.differentiation_strength: low` and proceed. Don't manufacture false specificity. The Brand Strategy agent will work on this in Layer 2.

### New Vehicle vs. Improvement Litmus Test (Internal — Not Said to Expert)
IQ Claw evaluates internally:

❌ Improvement language: "more thorough," "more advanced," "better than," "comprehensive"
✅ New vehicle language: "nobody else tests for this," "the real driver is," "the thing they've been treating isn't the problem"

Flag: `mechanism.positioning_type: new_vehicle` or `improvement`

### Data Captured
- `mechanism.core_approach`
- `mechanism.why_it_works`
- `mechanism.natural_language` (their own words — the across-the-desk sentence)
- `mechanism.name` (or null, flagged for Brand Strategy)
- `mechanism.vs_conventional`
- `mechanism.positioning_type` (new_vehicle / improvement)
- `mechanism.differentiation_strength` (strong / moderate / low)
- `brand.one_big_domino`
- `brand.one_big_domino.supporting_beliefs[]`
- `brand.one_big_domino.opposing_beliefs[]` (the three false beliefs from Phase 5 become these)

### IQ Claw Lock

> "That's your One Big Domino: '[their belief statement].'
>
> Every ad, every email, every webinar, every piece of content — it all points back to this one belief. When your patient accepts this, every other objection falls away.
>
> 🎯 One Big Domino — locked."

### Right Panel Updates
- ✅ Your Mechanism
- Progress: 72%
- Adds: Mechanism name (or "Unnamed — will be developed"), One Big Domino statement

---

## PHASE 7: COMPETITIVE LANDSCAPE
**Progress: 72% → 76% | Time: ~2 minutes | Checklist: ✅ Competitive Landscape**

*Note: Some competitive data was already captured in Phase 5 (avatar's failed attempts). This phase fills the gaps and captures the full picture.*

### IQ Claw

> "You mentioned that [avatar name]'s been to [what they mentioned in Phase 5 — e.g., 'other doctors, tried supplements, got medication that didn't work']. Let me make sure I have the full picture of what your patients are up against before they find you.
>
> Walk me through the typical journey — what does their doctor tell them, what do they try on their own, and what are the other options they're considering?"

### Data Captured
- `competitive_landscape.conventional_path` (full description of the standard medical journey)
- `competitive_landscape.alternative_competitors` (other practitioners in their space)
- `competitive_landscape.diy_approaches` (Google protocols, supplement stacks, etc.)
- `competitive_landscape.common_failure_modes[]` (enriched from Phase 5)
- `competitive_landscape.patient_language_about_failures[]` (enriched — exact phrases)

### Strong Answer
> "That's the entire landscape your patient navigates before they find you. Every piece of content we build will speak to someone who's been through [specific parts of their journey]. That's what makes it land."

### Weak/Already Covered
If Phase 5 already captured most of this:
> "Based on what you told me about [avatar name]'s journey, I've captured: [summary]. Anything I'm missing about what else they typically try before finding you?"

Quick confirmation, move on. Don't belabor if the data is already there.

### Right Panel Updates
- ✅ Competitive Landscape
- Progress: 76%
- Adds: "What patients tried before" summary (if not already shown from Phase 5)

---

## PHASE 8: OFFER ARCHITECTURE
**Progress: 76% → 84% | Time: ~3-4 minutes | Checklist: ✅ Offer Stack**

*Note: Questions are asked ONE TIER AT A TIME — never stacked.*

### IQ Claw — Entry Offer

> "Let's map your offer stack. We'll go one tier at a time.
>
> First — the entry point. When someone discovers you, what's the first thing they can do or buy? A free assessment? A low-cost consult? A guide or quiz? What's the door they walk through?"

**For each tier, probe for transformation framing:**
> "And when someone goes through that — what shifts for them? What do they know or feel after that they didn't before?"

### IQ Claw — Core Offer

> "Now your core program — the main thing. What does it look like? How long? What does the patient experience? And most importantly — where do they start and where do they end up?"

**Price probe (direct, no awkwardness):**
> "What do you charge for this?"

**Timeline probe:**
> "How long until they feel the first shift — not full results, just the first moment where they think 'something is different'?"

### IQ Claw — Premium Offer (if applicable)

> "Do you have a highest-level offering? Something for patients who want the most direct, most intensive version of working with you?"

**If they don't have a premium tier:**
> "No problem — not everyone does yet. Something to think about for later. Let's move on."

### Grand Slam Offer Test (Internal — Not Said to Expert)
IQ Claw evaluates each offer against Hormozi's Value Equation:
- Dream Outcome: Is the After State specific and emotionally compelling?
- Perceived Likelihood: Does the offer include proof elements?
- Time Delay: Is time-to-first-result clearly communicated?
- Effort & Sacrifice: Is the patient's required effort reasonable?

If any dimension is weak: flag `offer.value_equation_flag: [dimension]_unclear` for the Brand Strategy agent. Don't lecture the expert.

### Data Captured (per tier)
- `offers.[tier].name`
- `offers.[tier].price`
- `offers.[tier].before_state` (transformation-framed)
- `offers.[tier].after_state` (transformation-framed)
- `offers.[tier].timeline_to_first_result`
- `offers.[tier].fulfillment_model`
- `offers.[tier].value_equation_flags[]`

### IQ Claw Presents

> "Here's your offer ladder:
>
> 🟢 Entry: [Name] — $[Price]
> '[Before State]' → '[After State]'
>
> 🔵 Core: [Name] — $[Price]
> '[Before State]' → '[After State]' in [timeline]
>
> 🟣 Premium: [Name] — $[Price]
> '[Description]'
>
> Does this capture it? 💰 Offer Stack — locked."

### Weak Answer Handling
If they describe features ("It's a 12-week program with weekly calls, lab testing, supplements"):
> "Got it — those are the components. Now help me see it through the patient's eyes: when [avatar name] starts this program, what is she feeling? And 12 weeks later, what's different about her life? Not her lab results — her actual life."

### Right Panel Updates
- ✅ Offer Stack
- Progress: 84%
- Adds: 3 tier cards with names and prices

---

## PHASE 9: PROOF BANK
**Progress: 84% → 90% | Time: ~3 minutes | Checklist: ✅ Proof Bank**

### IQ Claw

> "Tell me about a patient transformation that still gets you emotional — someone who came in struggling and left a different person. Give me the whole story."

### Follow-Up Probes (one at a time)

> "What was their life like before they found you?"
> "What had they already tried?"
> "What was the turning point — the moment things started shifting?"
> "How long did it take to see real results?"
> "What did they say — their actual words, if you remember?"

### Seek the Special Story Types

After the first story, if time allows:
> "That's powerful. Is there one that was even more dramatic — your biggest before-and-after? Or someone who was completely skeptical and still got results?"

This surfaces:
- `proof_bank.most_dramatic_transformation`
- `proof_bank.fastest_result`
- `proof_bank.skeptic_to_believer`

### Then Inventory

> "Beyond patient stories — what other proof do you have? Reviews on Google, video testimonials, before-and-after lab results, media features, published research, speaking appearances?"

### Data Captured
- `proof_bank.transformation_stories[]` (2-3 structured stories with: avatar_match, before_state, treatments_tried, turning_point, result, timeline, direct_quote, media_available)
- `proof_bank.most_dramatic_transformation`
- `proof_bank.fastest_result`
- `proof_bank.skeptic_to_believer`
- `proof_bank.testimonials_text[]`
- `proof_bank.video_testimonials[]` (references)
- `proof_bank.before_after_data[]`
- `proof_bank.media_mentions[]`
- `proof_bank.collective_results_stats` (patients treated, avg time to result, success rate)
- `proof_bank.credentials_and_certifications[]`
- `proof_bank.proof_bank_depth_score` (calculated)

### IQ Claw Celebrates

> "That story about [patient description] — that's a webinar slide. That's an ad. That's an email. You just gave me content that would take most marketers weeks to build. 🏆 I'm capturing every detail."

### Enrichment Flag
If proof bank depth score < 40:
> "Your stories are strong but I'd love more. The richer your proof bank, the stronger every ad and email becomes. We can do a quick 10-minute proof-building session next week if you're up for it."

Flag `proof_bank.enrichment_needed: true`

### Right Panel Updates
- ✅ Proof Bank
- Progress: 90%
- Adds: Story count, proof bank score

---

## PHASE 10: THE 90-SECOND DEMO
**Progress: 90% → 93% | The "Oh My God" moment**

### IQ Claw

> "I have enough to show you something. Give me 90 seconds."

### Loading Animation
3-5 second pulsing animation (emerald glow or progress ring). NOT generic loading dots — something that feels like generation is happening.

### IQ Claw Delivers

> "Here's a preview of what your content will look like. One Instagram post, written in YOUR voice, targeting [Avatar Name]:"

**Inline Instagram post preview card** — rendered as a mock IG post:
- Their handle as the username
- Image area with their brand aesthetic and a text overlay using one of their signature phrases
- Caption written in their exact voice, rhythm, and vocabulary — targeting the avatar's emotional core
- Hook that matches the avatar's internal dialogue
- Mechanism language woven naturally into the body
- CTA matching their entry offer

> "That's your voice, your mechanism, your patient's story, your offer. Every piece of content I build will sound like that. Does it feel like you?"

### If They Love It
> "Good. This is minute 25. Imagine what 174 agents can do with a full week."

### If They Want Changes
> "Tell me what's off — I'll adjust the whole voice profile right now."

Capture any corrections to Voice DNA fields. This is a live calibration moment.

### Right Panel Updates
- Progress: 93%
- ✨ "First Content Generated" celebration

---

## PHASE 11: QUICK CAPTURE (Content, Business, Vision, Visual DNA)
**Progress: 93% → 97% | Time: ~2-3 minutes | Checklist: ✅ Business & Brand**

### IQ Claw

> "Almost there. A few quick things to round out your profile.
>
> What do you already have out there — podcast, YouTube, social, email list, funnels, lead magnets? And roughly how big is your audience right now?"

### Data Captured
- `content_audit.social_platforms_active[]`
- `content_audit.instagram_follower_count`
- `content_audit.email_list_size`
- `content_audit.existing_lead_magnets[]`
- `content_audit.existing_funnels[]`
- `content_audit.podcast_name` (if applicable)
- `content_audit.youtube_channel_url` (if applicable)

### IQ Claw

> "How are new patients finding you right now — and what do you think is the single biggest thing standing between you and the growth you want?"

### Data Captured
- `business_context.current_traffic_sources[]`
- `business_context.biggest_growth_obstacle`

### IQ Claw

> "Paint the picture for me: if this works exactly the way you want it to in three years, what does the practice look like? Revenue, patients, lifestyle, impact — whatever matters most to you."

### Data Captured
- `dream_practice.revenue_target`
- `dream_practice.patient_volume_target`
- `dream_practice.lifestyle_vision`
- `dream_practice.impact_vision`

### Visual DNA (Quick Capture)

> "Last thing — your brand look and feel. I pulled your logo and colors from your website: [show scrape results — logo thumbnail, 2-3 colors]. Does this represent your brand, or is there a different direction you want to go?"

### Data Captured
- `visual_dna.brand_colors[]` (confirmed or updated)
- `visual_dna.logo` (confirmed from scrape or flagged for upload)
- `visual_dna.aesthetic_description` (if they elaborate)
- `visual_dna.font_preference` (if mentioned)

### Right Panel Updates
- ✅ Business & Brand
- Progress: 97%
- Adds: Audience size, traffic sources, dream vision (1-line)

---

## PHASE 12: THE CLOSE
**Progress: 97% → 100% | Time: ~1 minute**

### IQ Claw

> "Here's what I now know about you and your practice:
>
> You're [name], a [specialty] practitioner who believes [One Big Domino, in their natural language]. Your approach — [mechanism name or description] — works because [why it works, one sentence]. Your ideal patient is [avatar name]: [1-sentence avatar description, using internal dialogue language]. Your core offer takes them from '[Before State]' to '[After State]' in [timeline]. And your voice is [tone description] — '[one signature phrase example].'
>
> This is what every output the platform builds will be powered by.
>
> Your Brand Strategy and Growth Strategy agents are building your complete marketing blueprint right now. Your Brand North Star, your Monthly Master Plan, your content calendar, your messaging briefs — all of it, generated from everything you just told me.
>
> I'll have your first content batch ready within the hour."

### The Compounding Advantage (Always Said)

> "One more thing: the more you use ClinicIQ, the smarter it gets about you. Every output we build, every piece of content we test, every result we measure — it all comes back and makes this profile more precise. After 30 days, this system will know your audience better than any agency. After 90 days, it'll know things about what works for YOUR specific audience that no human brain can hold.
>
> That advantage compounds. It starts right now.
>
> Welcome to ClinicIQ."

### Enrichment Summary (If Flags Exist)
If any enrichment flags were set during the session:
> "A few areas where we can go deeper in a follow-up session: [list 2-3 items — e.g., 'more patient transformation stories,' 'refine your mechanism name,' 'add video testimonials']. I'll check in with you in a few days. None of this blocks anything — your first content batch will be ready before then."

### Right Panel
- Progress: 100% — celebration animation (subtle confetti burst or emerald glow)
- ✅ All sections complete
- Dossier Score displayed (e.g., 74/100 — with breakdown showing where enrichment can improve it)
- [Enter ClinicIQ →] large emerald button

### Platform Unlock
Clicking [Enter ClinicIQ →] navigates to `/` (main IQ workspace).
Sidebar items all unlock — no longer grayed out.
IQ Claw's first message on the workspace is the morning briefing (or an equivalent "here's what's being built for you" message if strategy generation is still in progress).

---

## TIMING SUMMARY

| Phase | Duration | Running Total |
|-------|----------|--------------|
| 1. Opening (Identity) | ~2 min | 2 min |
| 2. Origin Story | ~3-5 min | 5-7 min |
| 3. Clinical Philosophy | ~2-3 min | 7-10 min |
| 4. Voice DNA | ~3 min | 10-13 min |
| 5. Patient Avatar | ~4-5 min | 14-18 min |
| 6. Mechanism & One Big Domino | ~3-4 min | 17-22 min |
| 7. Competitive Landscape | ~2 min | 19-24 min |
| 8. Offer Architecture | ~3-4 min | 22-28 min |
| 9. Proof Bank | ~3 min | 25-31 min |
| 10. 90-Second Demo | ~2 min | 27-33 min |
| 11. Quick Capture | ~2-3 min | 29-36 min |
| 12. Close | ~1 min | 30-37 min |

**Fast-Start target: 25-30 minutes.** Overwhelmed archetype can finish in 20 with heavy pre-scrape reliance. Confident archetype may take 35-40 if they give rich, detailed answers (let them — mine the gold).

---

## RIGHT PANEL PROGRESS MAP

| Phase | Progress % | Checklist Update | "What We Know" Adds |
|-------|-----------|-----------------|-------------------|
| Pre-scrape | 12% | — | Name (from scrape) |
| 1. Opening | 22% | ✅ Identity | Specialty, Practice Model, Location |
| 2. Origin Story | 32% | ✅ Your Story | Origin summary, Character type |
| 3. Philosophy | 40% | ✅ Philosophy | Core belief |
| 4. Voice DNA | 52% | ✅ Voice (🔒) | Tone, Phrases (pills), Banned (pills) |
| 5. Avatar | 62% | ✅ Avatar | Avatar card (name, pain, desire) |
| 6. Mechanism | 72% | ✅ Mechanism | Mechanism name, One Big Domino |
| 7. Competitive | 76% | ✅ Landscape | (enriches existing data) |
| 8. Offers | 84% | ✅ Offers | 3 tier cards |
| 9. Proof Bank | 90% | ✅ Proof Bank | Story count, score |
| 10. Demo | 93% | ✨ First Content | — |
| 11. Quick Capture | 97% | ✅ Business & Brand | Audience, vision |
| 12. Close | 100% | 🎉 Complete | Full synthesis, Dossier Score |

---

## NON-NEGOTIABLE PRINCIPLES

1. **IQ Claw always speaks first.** Never an empty chat.
2. **One question at a time.** Never stack. Never list.
3. **Never feel like a form.** Conversation with someone who did their homework.
4. **Expert approves or adjusts — never originates from scratch.** IQ always has something ready.
5. **Every capture is celebrated as the asset it is.** "That's a webinar slide. That's your One Big Domino."
6. **Progress is always saved. Always resumable.** No work is ever lost.
7. **Adapt to the expert's energy and archetype.** Fast for overwhelmed. Deep for willing. Reflective for reluctant.
8. **The 90-second demo is the trust transaction.** Everything builds to it.
9. **Never stall, never repeat, never make them feel stuck.** Generate. Present. Confirm. Forward.
10. **Stories are mined continuously** — not just in the Proof Bank phase.
11. **Weak data is flagged, never blocked.** Enrichment sessions fill gaps later. Progress never stops.
12. **The right panel proves value in real-time.** They watch their profile build. That's what makes this different from every other tool.
