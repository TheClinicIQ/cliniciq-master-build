# ClinicIQ — Complete Onboarding Flow
## The exact conversation a new expert experiences from first screen to "you're ready"
**Purpose:** Feed this to Claude Code / Lovable so it knows every step, every message, every screen state, and every data capture point in the onboarding experience.

---

## PRE-ONBOARDING (happens before they log in)

When the expert submits the sign-up form, two things fire in the background:
1. **Web Scraper** analyzes their website URL — pulls: name, specialty, years in practice, existing offers, brand colors, logo, patient testimonials, "about" page content
2. **Voice DNA Mass Ingestion** analyzes their Instagram handle (if provided) — pulls: last 90 days of captions, engagement patterns, top-performing content, sentence rhythm, vocabulary, emotional register, signature phrases, words they never use

By the time they click into `/onboarding`, IQ Claw already knows something about them.

---

## THE ONBOARDING SCREEN

Three panels:
- Left: Sidebar rail (72px) — all items grayed/disabled except IQ (active)
- Center: IQ Claw chat (~55%)
- Right: Progress panel (~45%) showing their profile being built live

The right panel has a progress card that updates as the conversation progresses:
- "Building Your Profile" header
- Progress bar (starts at 12% because pre-scrape data already populated some fields)
- Checklist of sections (status updates from ○ → 🔄 → ✅ as each completes)
- "What We Know So Far" section that fills in live with captured data
- Estimated time remaining

---

## THE CONVERSATION — Step by Step

### PHASE 1: THE OPENING (Identity & Practice) — Progress: 12% → 22%
*Goal: Establish who they are. Fast, easy, builds rapport. IQ Claw leads with what it already knows.*

**IQ Claw's first message (pre-populated, visible on page load):**

> "Hi Dr. [Name]. I've been looking at your practice before you arrived.
>
> [1-2 sentences of personalized intel from the web scrape — what they specialize in, how long they've been practicing, what stood out from their website or Instagram. Be specific, not generic.]
>
> [One specific compliment about something in their content or positioning — a hook that worked, a mechanism phrase that's powerful, a transformation story that stood out.]
>
> Before we build anything, I need to understand a few things about you, your patients, and your approach. This isn't a form — it's a conversation. Everything you tell me makes every output the platform produces more accurate and more YOU.
>
> Let's start simple: tell me about your practice in your own words — what do you do, who do you help, and how are you set up right now?"

**What gets captured from their response:**
- `identity.specialty_primary`
- `identity.practice_model` (telehealth, brick-and-mortar, hybrid)
- `identity.geographic_scope`
- `identity.years_in_practice` (confirmed or corrected from scrape)

**IQ Claw confirms what it heard + fills any gaps from scrape data:**

> "Got it — [1-2 sentence summary of what they said]. [Any pre-fill from scrape data presented for confirmation: 'Your website shows you're based in Austin and you've been in practice since 2015 — still accurate?']
>
> Now I want to go deeper."

**Right panel updates:**
- ✅ Identity & Practice (complete)
- Progress bar: 22%
- "What We Know So Far" shows: Name, Specialty, Practice Model, Location

---

### PHASE 2: THE ORIGIN STORY (Expert Personal Story) — Progress: 22% → 32%
*Goal: Get them talking in their real voice. Surface emotional hooks and brand DNA. This is where the conversation opens up.*

**IQ Claw:**

> "A lot of the best health experts got into this work because of something personal — either they went through it themselves, or someone they loved did, or they saw something in the system that they couldn't walk away from.
>
> Is there a story behind why you do what you do?"

**What gets captured:**
- `story.origin.before_state` — What their life/practice was like before
- `story.origin.trigger_event` — The specific moment that changed everything
- `story.origin.realization` — What they understood that they didn't before
- `story.origin.emotional_truth` — How it felt
- `story.origin.bridge_to_patient` — Why this drives their work today
- `brand.character_type` — Inferred (reluctant_hero / cause_driven / reporter)

**If they share a powerful story, IQ Claw celebrates it as the asset it is:**

> "That's one of the most important things you'll tell me in this entire session. That story — [specific element they shared] — that's your Epiphany Bridge. It's the moment that makes patients trust you before they ever walk through your door. I'm capturing every detail."

**If they give a short or surface answer, IQ Claw probes gently:**

> "Was there a specific patient, or a specific moment, where it became undeniably clear that you had to do this differently?"

**Right panel updates:**
- ✅ Your Story (complete)
- Progress: 32%
- "What We Know So Far" adds: Origin story summary (1-2 lines), Character type

---

### PHASE 3: CLINICAL PHILOSOPHY — Progress: 32% → 40%
*Goal: Surface what they believe that's different. This feeds the mechanism and the One Big Domino.*

**IQ Claw:**

> "Based on your story, it's clear you see things differently than most practitioners in your space. Let me ask you this:
>
> What do you believe about healing that most doctors, specialists, or even other practitioners in your field get wrong?"

**What gets captured:**
- `clinical_philosophy.core_belief` — Their fundamental clinical worldview
- `clinical_philosophy.what_conventional_gets_wrong` — Their critique of the standard approach
- `clinical_philosophy.what_makes_them_different` — Their differentiator in their own words

**IQ Claw reflects back the mechanism it's detecting:**

> "So if I'm hearing you right — [restate their philosophy in clear, sharp language]. That's not just a clinical philosophy. That's a positioning statement. That's the thing that makes your marketing different from every other [specialty] out there."

**Right panel updates:**
- ✅ Clinical Philosophy (complete)
- Progress: 40%
- Adds: Philosophy summary, early mechanism language

---

### PHASE 4: VOICE DNA CONFIRMATION — Progress: 40% → 52%
*Goal: By now, IQ Claw has been passively analyzing their communication for 10+ minutes. Time to surface and confirm.*

**IQ Claw:**

> "I've been paying attention to how you communicate — not just what you've said, but how you say it. Let me show you what I've picked up. Tell me if this feels right.
>
> **Your tone:** [Detected tone — e.g., 'Direct and confident. You make declarative statements. You don't hedge. When you talk about patients, genuine warmth comes through — but you lead with clarity, not softness.']
>
> **Your rhythm:** [e.g., 'You mix short punchy statements with longer explanatory stretches. You make a claim, then build the case.']
>
> **Phrases that are uniquely yours:** [List 3-5 detected signature phrases as tags]
>
> **Words you never use:** [List detected avoidances — if mass ingestion ran, this is statistically validated]
>
> Does this feel like you? Anything I got wrong or missed?"

**The expert confirms, adjusts, or adds.**

**Then IQ Claw asks the critical question:**

> "One more thing on voice — what words do you absolutely NEVER want to see in your marketing? The ones that make you cringe when a competitor uses them."

**What gets captured:**
- `voice_dna.tone_primary` + `tone_secondary`
- `voice_dna.sentence_rhythm`
- `voice_dna.vocabulary_register`
- `voice_dna.formality_level`
- `voice_dna.emotional_register`
- `voice_dna.conviction_level`
- `voice_dna.signature_phrases` (confirmed array)
- `voice_dna.words_they_avoid` (confirmed array)
- `voice_dna.humor_level`
- `voice_dna.authority_style`
- `voice_dna.sample_extracts` (3-5 verbatim quotes from the conversation so far)

**IQ Claw locks it:**

> "Voice DNA — locked. 🗣️ Every piece of content the platform builds for you from this point forward will sound like you wrote it on your best day."

**Right panel updates:**
- ✅ Your Voice (complete, shows emerald "Locked" badge)
- Progress: 52%
- Adds: Tone, Signature Phrases (as pills), Banned Words (as pills)

---

### PHASE 5: PATIENT AVATAR — Progress: 52% → 62%
*Goal: Build the primary patient persona with deep psychology — not demographics.*

**IQ Claw:**

> "Now that I know you deeply, let's talk about who you help. I don't mean demographics — I mean the human being.
>
> Describe the patient who gets the absolute best results with you — not just who you work with, but who you light up for. What are they dealing with, what have they tried, and what does life look like for them before they find you?"

**Follow-up probes (one at a time, based on what they give):**

> "Walk me through a bad day for this person — from the moment they wake up."

> "What's the thing they've stopped telling people about how they feel?"

> "What are they afraid will happen if nothing changes?"

> "What do they say to themselves at 2am — the thing they think but don't say out loud?"

> "When they come to you after trying other providers — what do they tell you about why nothing worked?"

**What gets captured (all 4 psychological layers):**
- `avatar.name` (IQ Claw names the persona: "Let's call her Stressed Mom Sarah")
- `avatar.demographics` (age range, gender, context)
- `avatar.awareness_level` (inferred from their answers)
- Layer 1: `avatar.symptom_stack` — daily reality, specific
- Layer 2: `avatar.emotional_core` — frustration, fear, shame, hope
- Layer 3: `avatar.belief_system` — false beliefs about vehicle, internal, external
- Layer 4: `avatar.internal_dialogue` — exact phrases from their head
- `competitive_landscape.common_failure_modes` (captured from "what they tried")
- `competitive_landscape.patient_language_about_failures`

**IQ Claw presents the avatar card:**

> "Here's your primary avatar — Stressed Mom Sarah:
>
> [Formatted avatar summary with all 4 layers — presented as a clean card, not a data dump]
>
> Does she feel real? Anything to adjust?"

**Right panel updates:**
- ✅ Your Patient Avatar (complete)
- Progress: 62%
- Adds: Avatar card in "What We Know So Far" — name, age, key pain, key desire

---

### PHASE 6: THE MECHANISM & ONE BIG DOMINO — Progress: 62% → 72%
*Goal: Extract the New Vehicle and the belief that makes everything click.*

**IQ Claw:**

> "Now the most important question. You've told me about your patients and what they're dealing with. You've told me what conventional medicine gets wrong.
>
> When a patient comes to you after failing with other providers — what's the first thing you look at that nobody else looked at? And why does your approach work when everything else they tried didn't?"

**Follow-up:**

> "If you had to explain your approach to a patient in one sentence — the way you'd say it across the desk — what would you say?"

**Follow-up:**

> "Does your method have a name? If you were going to name it, what would you call it?"

**Then the One Big Domino:**

> "Now here's the question that ties it all together: What's the one thing that, if your ideal patient truly believed it, would change everything for them? The one belief that, once they accept it, all their other doubts start to fall away?"

**What gets captured:**
- `mechanism.core_approach`
- `mechanism.why_it_works`
- `mechanism.natural_language`
- `mechanism.name` (or null, flagged for Brand Strategy)
- `mechanism.vs_conventional`
- `mechanism.positioning_type` (new_vehicle or improvement — IQ flags internally)
- `brand.one_big_domino`
- `brand.one_big_domino.supporting_beliefs`
- `brand.one_big_domino.opposing_beliefs`

**IQ Claw names it:**

> "That's your One Big Domino: '[their belief statement].' Every ad, every email, every webinar, every piece of content — it all points back to this belief. 🎯 One Big Domino — locked."

**Right panel updates:**
- ✅ Mechanism & Beliefs (complete)
- Progress: 72%
- Adds: Mechanism name (or "Unnamed — will develop"), One Big Domino statement

---

### PHASE 7: OFFER ARCHITECTURE — Progress: 72% → 80%
*Goal: Map their offer stack as transformations, not features.*

**IQ Claw:**

> "Let's map your offer. Not features — transformations.
>
> Walk me through what happens when someone finds you. What's the first thing they can do — the entry point? What does your core program look like? And if someone wanted the highest level of working with you, what does that look like?"

**For each offer tier, IQ Claw probes for:**
- Before State → After State
- Price
- Timeline to first result
- Fulfillment model
- What makes it different from alternatives

**IQ Claw presents the offer stack:**

> "Here's your offer ladder:
>
> 🟢 Entry: [Name] — $[Price] — '[Before State]' → '[After State]'
> 🔵 Core: [Name] — $[Price] — '[Before State]' → '[After State]' in [timeline]
> 🟣 Premium: [Name] — $[Price] — '[Description]'
>
> Does this capture it?"

**Right panel updates:**
- ✅ Your Offer Stack (complete)
- Progress: 80%
- Adds: 3 offer tiers with names and prices

---

### PHASE 8: PROOF BANK — Progress: 80% → 88%
*Goal: Capture transformation stories and inventory existing proof assets.*

**IQ Claw:**

> "Tell me about a patient transformation that still gets you emotional — someone who came in struggling and left a different person. Give me the whole story."

**Follow-up probes for each story:**

> "What was their life like before?"
> "What had they already tried?"
> "What was the turning point?"
> "How long did it take?"
> "What did they say — their actual words?"

**Then inventory:**

> "What other proof do you have? Think reviews, video testimonials, before-and-after documentation, published research, media features, speaking appearances."

**What gets captured:**
- `proof_bank.transformation_stories[]` (2-3 structured stories with full arc)
- `proof_bank.most_dramatic_transformation`
- `proof_bank.fastest_result`
- `proof_bank.testimonials_text`
- `proof_bank.video_testimonials` (references)
- `proof_bank.media_mentions`
- `proof_bank.collective_results_stats`
- `proof_bank.proof_bank_depth_score`

**IQ Claw celebrates:**

> "That story about [patient name/description] — that's a webinar slide. That's an ad. That's an email. You just gave me content that would take most marketers weeks to build. 🏆"

**Right panel updates:**
- ✅ Your Proof Bank (complete or flagged for enrichment)
- Progress: 88%
- Adds: Story count, testimonial count, proof bank score

---

### PHASE 9: THE 90-SECOND DEMO — Progress: 88% → 92%
*Goal: The "oh my god" moment. Show them what the platform can do with what it now knows.*

**IQ Claw:**

> "I have enough to show you something. Give me 90 seconds."

**[Loading animation — pulsing emerald glow or progress ring, 3-5 seconds in the demo]**

**IQ Claw delivers one Instagram post — written in their voice, targeting their avatar, using their mechanism language:**

> "Here's a preview of what your content will look like. This is one Instagram post, written in YOUR voice, targeting [Avatar Name]:"
>
> **[Inline Instagram post preview card — rendered as a mock IG post with:**
> - Their handle
> - Image concept with their brand feel
> - Caption in their voice, their rhythm, their phrases
> - Their mechanism language woven in
> - A hook that matches their avatar's internal dialogue
> - A CTA that matches their entry offer**]**
>
> "That's your voice, your mechanism, your patient's story. Every piece of content I build will sound like that. Does it feel like you?"

**This is the trust transaction.** If they say yes — or even hesitate with impressed energy — the relationship shifts.

**Right panel updates:**
- Progress: 92%
- A small "✨ First Content Generated" celebration moment

---

### PHASE 10: BRAND & STRATEGY GENERATION — Progress: 92% → 95%
*Goal: Quick capture of remaining items + launch Layer 2.*

**IQ Claw:**

> "Almost there. A few quick things to round out your profile:
>
> What do you already have out there — podcast, YouTube, social, email list, funnels, lead magnets?"

**Quick capture of:**
- `content_audit` fields
- `business_context.current_traffic_sources`
- `business_context.biggest_growth_obstacle`

**IQ Claw:**

> "Last question — and paint the picture: if this works exactly the way you want it to in three years, what does the practice look like? Revenue, patients, lifestyle, impact."

**Captures:**
- `dream_practice.revenue_target`
- `dream_practice.lifestyle_vision`
- `dream_practice.impact_vision`

**Right panel updates:**
- Progress: 95%

---

### PHASE 11: THE CLOSE — Progress: 95% → 100%
*Goal: Show what was built, unlock the platform, plant the compounding advantage.*

**IQ Claw:**

> "Here's what I now know about you and your practice:
>
> You're [name], a [specialty] practitioner who believes [One Big Domino]. Your approach — [mechanism name or description] — works because [why it works]. Your ideal patient is [avatar name]: [1-sentence avatar description]. Your core offer takes them from '[Before State]' to '[After State]' in [timeline]. And your voice is [tone description] — [signature phrase example].
>
> This is what every output the platform builds will be powered by.
>
> Your Brand Strategy and Growth Strategy agents are now building your complete marketing blueprint. Your Brand North Star, your Monthly Master Plan, your content calendar, your messaging briefs — all of it is being generated right now based on everything you just told me.
>
> I'll have your first content batch ready within the hour.
>
> One more thing: the more you use ClinicIQ, the smarter it gets about you. Every output we build, every piece of content we test, every result we measure — it all comes back and makes your dossier more precise. After 30 days, this system will know your audience better than any agency you've ever hired. After 90 days, it'll know things about what works for YOUR specific audience that no human brain could hold simultaneously.
>
> That advantage compounds. And it starts right now.
>
> Welcome to ClinicIQ."

**Right panel:**
- Progress: 100% — celebration animation (confetti or emerald glow)
- ✅ All sections complete
- Dossier Score shown (e.g., 74/100 with room to grow through enrichment)
- [Enter ClinicIQ →] emerald button appears

**Clicking [Enter ClinicIQ →] navigates to `/` — the main IQ workspace with the morning briefing.**

**Sidebar items unlock** — all navigation items become active and clickable.

---

## TIMING

The Fast-Start version of this flow should take **20-30 minutes** for an engaged expert. The conversation is brisk but never rushed. If the expert is giving rich answers, let them talk — mine the gold. If they're short and fast, match their pace and lean on pre-scrape data and agent-generated fills.

**The pacing rule:** Every 3-4 questions, IQ Claw reflects something back that demonstrates intelligence — not just data capture. The expert should feel the system getting smarter about them in real-time.

---

## WHAT THE RIGHT PANEL SHOWS THROUGHOUT

The right panel is a **live progress dashboard** that updates as the conversation progresses:

| Phase | Progress | Checklist Update | "What We Know" Adds |
|-------|----------|-----------------|-------------------|
| Opening | 12%→22% | ✅ Identity | Name, Specialty, Location, Practice Model |
| Origin Story | 22%→32% | ✅ Your Story | Origin summary, Character type |
| Philosophy | 32%→40% | ✅ Philosophy | Core belief, What others get wrong |
| Voice DNA | 40%→52% | ✅ Your Voice (🔒 Locked) | Tone, Signature Phrases (pills), Banned Words (pills) |
| Avatar | 52%→62% | ✅ Patient Avatar | Avatar card (name, age, pain, desire) |
| Mechanism | 62%→72% | ✅ Mechanism | Mechanism name, One Big Domino |
| Offers | 72%→80% | ✅ Offer Stack | 3 tiers with names and prices |
| Proof Bank | 80%→88% | ✅ Proof Bank | Story count, Score |
| 90-Sec Demo | 88%→92% | ✨ First Content | — |
| Quick Capture | 92%→95% | ✅ Business Context | Traffic sources, Dream vision |
| Close | 95%→100% | 🎉 Complete | Full synthesis, Dossier Score |

---

## KEY PRINCIPLES (non-negotiable)

1. **IQ Claw always speaks first.** Never an empty chat. Never "How can I help you?"
2. **One question at a time.** Never stack questions. Never present a list.
3. **Never feel like a form.** This is a conversation with someone who already did their homework.
4. **The expert's job is to approve or adjust — not originate.** IQ always has something ready. If they go blank, generate and present.
5. **Celebrate every capture as the asset it is.** Not "Great answer!" — "That's a webinar slide. That's an ad hook. That's your One Big Domino."
6. **The right panel proves value in real-time.** Watching their profile build live creates the feeling that something real is happening — not just data entry.
7. **The 90-second demo is the trust transaction.** Everything before it builds to this moment. Everything after it is momentum.
8. **Never stall, never repeat, never make them feel stuck.** If they don't know, generate. If they give a weak answer, build on it. Forward always.
