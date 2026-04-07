# clinicIQ — Layer 1: Onboarding Agent — Step 2: Expert Dossier Data Schema
**Version 1.1 — Revised**
*Step 2 of 22 | Depends on: Step 1 (Agent Description)*

---

## Purpose

The Expert Dossier is the single most important data structure in the entire clinicIQ platform. Every agent in every layer reads from it. Every word the platform writes for an expert is calibrated against it. Every strategy it builds is grounded in it. Every output it produces is only as good as the data here.

This document defines the complete 198-field schema — 14 sections, every field named, typed, described, and mapped to the downstream agents that consume it. This is the specification the Onboarding Lead Agent (Step 1) is built to populate, the schema the Dossier Assembler sub-agent assembles into the two payload formats (Step 7), and the data contract every Layer 2, Layer 3, and Layer 4 agent reads from.

Developers building against this schema should treat it as the canonical reference. When a field is added, the schema version increments. Downstream agents always declare which schema version they read from — this prevents silent breaking changes as the platform evolves.

---

## Relationship to the Living Expert Profile (Layer 5)

The Expert Dossier is **Layer A (Identity Core)** of the Living Expert Profile (LEP) defined in `layer5/L5-1_living_expert_profile.md`. The LEP is the long-term intelligence model every agent in the platform ultimately reads from.

The relationship is:

```
Expert Dossier (Layer 1 — 198 fields)
    ↓  seeds  ↓
Living Expert Profile — Layer A: Identity Core     ← This document
Living Expert Profile — Layer B: Market Intelligence  ← Built by Layer 4 Analytics (performance-derived, automated)
Living Expert Profile — Layer C: Network Intelligence ← Built by L5-4 Network Intelligence (platform-wide aggregated data)
```

**What this means for the dev team:**
- The 198 fields defined in this document map 1:1 to LEP Layer A
- LEP Layer B adds ~30 performance-derived fields (audience response, competitive intelligence, offer performance) that are never captured at onboarding — they are built automatically from Layer 3 and Layer 4 output data
- LEP Layer C adds ~16 network-benchmarked fields drawn from anonymized cross-expert platform data
- Total LEP at full maturity: ~244 fields
- The schema keys used here (`voice_dna.*`, `avatar_psychology.*`, etc.) are the canonical field identifiers used in the LEP and in Step 7's machine-readable JSON payload

**Schema keys and shorthand aliases:** Steps 3–6 in this layer were written using shorthand field references for readability (`voice.*`, `avatar.*`, `offer.*`, `story.*`). These are documentation aliases only. The canonical schema keys — which are what the platform, all agents, and all integrations use — are the full keys defined in this document:

| Shorthand (Steps 3–6 docs) | Canonical Schema Key (this document + Step 7 + LEP) |
|----------------------------|------------------------------------------------------|
| `voice.*` | `voice_dna.*` |
| `avatar.*` | `avatar_psychology.*` |
| `avatar.primary_name` | `avatar_psychology.avatar_name` |
| `offer.*` | `offer_architecture.*` |
| `story.*` | `expert_personal_story.*` |
| `story.personal_story_summary` | `expert_personal_story.story_personal_story_summary` |
| `story.what_they_almost_gave_up_on` | `expert_personal_story.story_what_they_almost_gave_up_on` |
| `story.what_changed_everything` | `expert_personal_story.story_what_changed_everything` |
| `webinar.origin_story_*` | `webinar_raw_material.origin_story_*` |

All agent code, all API endpoints, all database columns use the canonical keys. The shorthand aliases are for human readability in documentation only.

---

## Schema Version and Versioning Protocol

**Current version:** 1.1
**Versioning rule:** Any addition of a new field increments the minor version (1.1 → 1.2). Any removal or rename of an existing field increments the major version (1.1 → 2.0). Downstream agents declare their minimum schema version in their own configuration. The platform enforces compatibility at handoff.

---

## Data Types Reference

| Type | Description |
|------|-------------|
| **String** | Free-text value of any length |
| **Enum** | A fixed set of allowed string values — listed in the field definition |
| **Array** | An ordered list of values — elements may be Strings, Objects, or other types |
| **Boolean** | True or false |
| **Integer** | Whole number |
| **Object** | A structured sub-record with its own named fields |
| **URL** | A valid HTTP/HTTPS URL |
| **File** | A reference to an uploaded binary asset (image, PDF, video, audio) |

---

## Status Flags

Every field in the dossier carries one of four status flags at all times. These flags govern how downstream agents treat the value and how the dashboard surfaces the field to the expert.

| Flag | Meaning | Dashboard Behavior |
|------|---------|--------------------|
| `confirmed` | Expert explicitly approved this value in a session | Green indicator — no action needed |
| `agent-generated` | Agent built this value from available context; expert has not yet seen it | No indicator — value is in use silently |
| `pending-approval` | Agent-generated value has been surfaced to expert; awaiting thumbs up, edit, or regenerate | Yellow indicator — "Review & confirm" prompt shown |
| `pending-upload` | Field requires a file asset; placeholder is in use until upload arrives | Grey indicator with paperclip icon — "Upload when ready" prompt shown |

No status flag blocks downstream output generation. The platform always moves forward using the best available value, flagged appropriately.

---

## Fast-Start Priority Flags

Every field is tagged with one of three Fast-Start priority levels. These determine what the Onboarding Lead Agent pursues in Fast-Start Mode (20–30 min) vs. defers to subsequent sessions.

| Priority | Meaning | Target |
|----------|---------|--------|
| `P1 — Required` | Must be populated (confirmed or agent-generated) before `handoff_ready = true` | ~60 fields |
| `P2 — Important` | Should be populated in first full session; unlocks additional Builder agent capabilities | ~80 fields |
| `P3 — Enrichment` | Deepens output quality over time; can be populated across multiple sessions | ~58 fields |

P1 fields are indicated with **[P1]** in the Field Name column of each table below. All others are P2 unless marked **[P3]**.

---

## Section 1 — Identity & Practice

**Schema key:** `identity`
**Field count:** 12
**LEP layer:** A — Identity Core
**Purpose:** The foundational context for everything else in the dossier. Who the expert is, what they do, how their practice is structured, and where they operate. Every downstream agent reads this section as baseline context. All 12 fields are P1 — the Web Scraper sub-agent pre-populates most of these before the first session begins.
**Primary consumers:** All agents (universal context layer)

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `identity.full_name` | **[P1]** Full Name | String | Expert's legal or professional full name | "Dr. Sarah Mitchell, ND" |
| `identity.credential_title` | **[P1]** Credential Title | String | The credential or title they lead with professionally | "Naturopathic Doctor" |
| `identity.practice_name` | **[P1]** Practice Name | String | The name of their practice or brand | "Mitchell Functional Health" |
| `identity.specialty_primary` | **[P1]** Primary Specialty | Enum | Their main clinical focus area: Functional-Medicine / Naturopathic / Chiropractic / Health-Coaching / Nutrition / Integrative / Hormones / Gut-Health / Autoimmune / Longevity / Mental-Health / Weight-Management / Womens-Health / Mens-Health / Pain / Pediatric / Other | "Functional-Medicine" |
| `identity.specialty_secondary` | Secondary Specialties | Array[String] | Additional specialty areas they work within | ["Autoimmune", "Hormones"] |
| `identity.practice_model` | **[P1]** Practice Model | Enum | Telehealth / Brick-and-mortar / Hybrid / Group / Solo / Course-creator | "Hybrid" |
| `identity.years_in_practice` | Years in Practice | Integer | Total years practicing in their specialty | 11 |
| `identity.geographic_scope` | **[P1]** Geographic Scope | Enum | Local / Regional / National / International | "National" |
| `identity.state_or_country` | **[P1]** State or Country | String | Primary operating jurisdiction — drives compliance filter | "Tennessee" |
| `identity.team_size` | Team Size | Integer | Number of staff including the expert | 4 |
| `identity.current_monthly_revenue` | **[P1]** Current Monthly Revenue | Enum | Under-$10K / $10K–$30K / $30K–$60K / $60K–$100K / $100K–$250K / $250K+ | "$30K–$60K" |
| `identity.website_url` | **[P1]** Website URL | URL | Primary practice or brand website | "https://mitchellfunctionalhealth.com" |

**Consuming agents:** All agents (universal context)

---

## Section 2 — Voice DNA

**Schema key:** `voice_dna`
**Field count:** 16
**LEP layer:** A — Identity Core
**Purpose:** The fingerprint of how this expert communicates — the data structure that every Builder Layer agent reads before writing a single word. A weak Voice DNA profile produces generic outputs. A strong one produces outputs the expert reads and says "that sounds exactly like me." Populated passively by the Voice DNA Analyst sub-agent throughout the entire session and confirmed actively in Section 2 of the conversation flow. Full extraction methodology in Step 4.
**Primary consumers:** All Layer 3 Builder agents — every content output reads this section first; LEP Layer B enriches this section over time with confirmed high-performing outputs

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `voice_dna.tone_primary` | **[P1]** Primary Tone | Enum | Authoritative / Empathetic / Urgent / Educational / Conversational / Inspirational | "Authoritative" |
| `voice_dna.tone_secondary` | Secondary Tone | Enum | Same enum as primary — the secondary tonal layer that adds texture | "Empathetic" |
| `voice_dna.formality_level` | **[P1]** Formality Level | Enum | High / Medium / Low | "Medium" |
| `voice_dna.sentence_rhythm` | **[P1]** Sentence Rhythm | Enum | Short-punchy / Long-flowing / Mixed-dynamic | "Mixed-dynamic" |
| `voice_dna.vocabulary_register` | **[P1]** Vocabulary Register | Enum | Clinical-technical / Plain-language-translator / Street-level-casual / Mixed-professional | "Plain-language-translator" |
| `voice_dna.emotional_register` | **[P1]** Emotional Register | String | Full description of how much feeling they bring and in what form — grounded and specific vs. measured and analytical vs. mission-driven | "High emotional — visible frustration with conventional medicine, genuine excitement about patient results, deep empathy expressed through specific stories rather than general statements" |
| `voice_dna.humor_level` | Humor Level | Enum | None / Dry / Warm | "Dry" |
| `voice_dna.conviction_level` | **[P1]** Conviction Level | Enum | High-conviction / Balanced / Tends-to-hedge | "High-conviction" |
| `voice_dna.authority_style` | Authority Style | Enum | Credential-first / Results-first / Story-first / Teaching-first — how they establish credibility | "Results-first" |
| `voice_dna.signature_phrases` | **[P1]** Signature Phrases | Array[String] | Phrases the expert used more than once in the session — confirmed as authentically theirs | ["root cause", "nobody's asking the right questions", "the body knows how to heal"] |
| `voice_dna.words_they_use` | Words They Use | Array[String] | Vocabulary preferences — words and constructions they favor | ["upstream", "driver", "healing", "restore"] |
| `voice_dna.words_they_avoid` | Words They Avoid | Array[String] | Hard vocabulary avoidances — confirmed by expert | ["holistic", "wellness", "fix"] |
| `voice_dna.sample_extracts` | **[P1]** Sample Extracts | Array[String] | 3–5 verbatim quotes from the session. The highest-signal samples of authentic voice. The calibration standard the Builder Layer uses to match tone. Minimum 3 extracts required for P1 status. | ["The body already knows how to heal. Our job is to stop getting in the way.", "Nobody's asking why the immune system is attacking itself. They're just trying to quiet it down."] |
| `voice_dna.high_passion_topics` | High-Passion Topics | Array[String] | Topics where the expert's language accelerated or intensified — authentic brand energy | ["Autoimmune root cause", "What conventional medicine gets wrong", "Patient transformations"] |
| `voice_dna.writing_vs_speaking_difference` | Writing vs. Speaking Difference | String | How their written communication style differs from how they quote themselves speaking — relevant for written copy vs. video scripts | "More clipped and direct in writing. More story-driven and emotional when speaking. Scripts should lean toward speaking register." |
| `voice_dna.voice_confidence_score` | Voice Confidence Score | Integer | Internal quality score 0–100 reflecting richness and confirmation of Voice DNA profile. Below 50: Builder agents flag outputs as needing expert review before use. | 72 |

**Consuming agents:** All Layer 3 Builder agents (every output reads this first); LEP updates `voice_dna.sample_extracts` automatically when high-performing content is approved

---

## Section 3 — Visual DNA

**Schema key:** `visual_dna`
**Field count:** 11
**LEP layer:** A — Identity Core
**Purpose:** The aesthetic identity of the expert's brand. Collected toward the end of the conversation flow because uploads happen asynchronously. The Voice DNA Analyst sub-agent infers visual DNA signals during the session and pre-populates `aesthetic_keywords` before this section is reached. File fields remain `pending-upload` until assets are submitted — they never block output generation.
**Primary consumers:** Ad Creative Builder, Website Builder, Content Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `visual_dna.aesthetic_keywords` | **[P1]** Aesthetic Keywords | Array[String] | 3–6 words describing the visual feel — inferred by Voice DNA Analyst if not stated | ["Clean", "Clinical", "High-contrast", "Trustworthy", "Modern"] |
| `visual_dna.color_palette_description` | Color Palette Description | String | Description of primary and secondary brand colors in plain language | "Deep navy and white with a warm gold accent" |
| `visual_dna.color_palette_hex` | Color Palette (Hex) | Array[String] | Confirmed hex codes if available | ["#1A2B5F", "#FFFFFF", "#C9A84C"] |
| `visual_dna.typography_direction` | Typography Direction | String | Font style direction — serif / sans-serif / modern / classic / editorial | "Clean sans-serif — modern and clinical, not ornate" |
| `visual_dna.photography_style` | Photography Style | String | Photography tone the brand uses or should use | "Professional documentary — real clinical settings, no stock lifestyle imagery" |
| `visual_dna.logo_status` | Logo Status | Enum | Exists-uploaded / Exists-not-uploaded / Does-not-exist | "Exists-not-uploaded" |
| `visual_dna.logo_file` | Logo File | File | Uploaded logo asset | [file reference] |
| `visual_dna.brand_guide_status` | **[P3]** Brand Guide Status | Enum | Exists-uploaded / Exists-not-uploaded / Does-not-exist | "Does-not-exist" |
| `visual_dna.brand_guide_file` | **[P3]** Brand Guide File | File | Uploaded brand style guide | [file reference] |
| `visual_dna.expert_photo_status` | Expert Photo Status | Enum | Uploaded / Not-yet-uploaded | "Not-yet-uploaded" |
| `visual_dna.expert_photo_file` | Expert Photo File | File | Uploaded headshot or brand photography asset — used in ads, website, email headers | [file reference] |

**Consuming agents:** Ad Creative Builder, Website Builder, Content Builder

---

## Section 4 — Avatar Psychology

**Schema key:** `avatar_psychology`
**Field count:** 20
**LEP layer:** A — Identity Core (confirmed at onboarding); Layer B enriches `language_patterns` and `buying_triggers` with real audience response data over time
**Purpose:** The psychological profile of the expert's ideal patient — the most consumed section across the entire platform. Every ad hook, every email subject line, every webinar opener, every funnel headline starts here. Full extraction methodology in Step 5.
**Primary consumers:** All Builder agents, Brand Strategy Agent, Growth Strategy Agent

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `avatar_psychology.avatar_name` | **[P1]** Avatar Name | String | The alliterative avatar name — makes psychology specific and memorable. Also referenced as `avatar.primary_name` in Steps 4–6 documentation. | "Dismissed Denise" |
| `avatar_psychology.age_range` | **[P1]** Age Range | String | The primary demographic age range | "42–55" |
| `avatar_psychology.gender_skew` | **[P1]** Gender Skew | Enum | Female-skewed / Male-skewed / Even | "Female-skewed" |
| `avatar_psychology.income_level` | **[P1]** Income Level | Enum | Under-$50K / $50K–$80K / $80K–$150K / $150K–$300K / $300K+ | "$80K–$150K household" |
| `avatar_psychology.primary_symptom` | **[P1]** Primary Symptom | String | The dominant symptom — in the avatar's own words, not the clinical name | "Can't get out of bed in the morning, brain fog that makes it impossible to think clearly at work" |
| `avatar_psychology.symptoms_list` | **[P1]** Symptoms List | Array[String] | Full stack of secondary symptoms and life impacts — in the avatar's own words | ["Exhausted by 2pm", "Weight that won't move", "Mood swings", "Can't focus", "Missing my kids' activities"] |
| `avatar_psychology.daily_frustrations` | Daily Frustrations | Array[String] | The specific moments and situations the symptoms create in daily life | ["Having to cancel plans with her kids", "Falling asleep at her desk", "Feeling like a failure at work"] |
| `avatar_psychology.core_fear` | **[P1]** Core Fear | String | The deepest fear — what they're afraid this means about their future | "I'm never going to get better. This is the rest of my life." |
| `avatar_psychology.secondary_fears` | Secondary Fears | Array[String] | The fears orbiting the core fear | ["Being dismissed by another doctor", "Wasting money on something that won't work", "Making things worse"] |
| `avatar_psychology.deepest_desire` | **[P1]** Deepest Desire | String | What they actually want — specific, not generic | "To have energy when I wake up and still have it at dinner with my family. To feel like myself again for the first time in ten years." |
| `avatar_psychology.transformation_identity` | **[P1]** Transformation Identity | String | Who they want to BECOME — new identity, not just improved health | "The mom who shows up fully. Who has energy for her kids and doesn't have to apologize for disappearing." |
| `avatar_psychology.awareness_level` | **[P1]** Awareness Level | Enum | 1-Unaware / 2-Problem-Aware / 3-Solution-Aware / 4-Product-Aware / 5-Most-Aware — master entry angle variable for all cold traffic | "Level 2-3" |
| `avatar_psychology.false_belief_vehicle` | **[P1]** False Belief — Vehicle | String | Why the avatar doesn't believe the approach will work. Maps to Brunson's Secret #1. | "I've tried supplements and diet changes before and nothing worked. Functional medicine is probably just another expensive experiment." |
| `avatar_psychology.false_belief_internal` | **[P1]** False Belief — Internal | String | Why the avatar doesn't believe they personally can achieve the result. Maps to Brunson's Secret #2. | "I don't have the willpower to stick to a protocol. I've failed at health programs before. My body is probably too far gone." |
| `avatar_psychology.false_belief_external` | **[P1]** False Belief — External | String | Why external circumstances will prevent success. Maps to Brunson's Secret #3. | "I can't afford it. My family won't support major dietary changes. I work too much to be consistent." |
| `avatar_psychology.language_patterns` | **[P1]** Language Patterns | Array[String] | Exact phrases the avatar uses — verbatim, never paraphrased, used directly in copy. LEP Layer B enriches this with actual audience language from replies, reviews, and DMs over time. | ["I just feel off", "I'm running on empty", "My doctor says everything is normal but I know something is wrong", "I've lost myself"] |
| `avatar_psychology.previous_solutions_tried` | **[P1]** Previous Solutions Tried | Array[Object] | Each object: `{solution, promise_made, what_happened, conclusion_drawn}`. The failure stack. | [{solution: "Thyroid medication", promise_made: "Will fix your numbers", what_happened: "Numbers improved but still felt terrible", conclusion_drawn: "Nothing will ever really work"}] |
| `avatar_psychology.buying_triggers` | Buying Triggers | Array[String] | The specific life events or moments that tip this avatar into action | ["New diagnosis or worsening labs", "Health scare", "Milestone birthday", "Stopped being able to participate in family life"] |
| `avatar_psychology.objections_primary` | **[P1]** Primary Objections | Array[String] | The last-mile objections that stop the sale after interest is established | ["Price — can't justify the investment right now", "Need to talk to my spouse", "Not sure this will work for me specifically"] |
| `avatar_psychology.secondary_avatars` | **[P3]** Secondary Avatars | Array[Object] | Array of secondary avatar objects — each with name, awareness_level, primary_symptom, core_fear, and key false beliefs | [{name: "Optimization Oliver", awareness_level: "1-2", primary_symptom: "Performing at 70% of potential", core_fear: "Declining as I age"}] |

**Consuming agents:** All Builder agents (hook selection, entry angle, false belief architecture, close language); Brand Strategy (positioning); Growth Strategy (campaign targeting)

---

## Section 5 — Problems → Root Cause → New Vehicle Map

**Schema key:** `root_cause_map`
**Field count:** 12
**LEP layer:** A — Identity Core
**Purpose:** The intellectual architecture of the expert's approach — what their patients experience, what is actually causing it (the root cause conventional medicine misses), and the unique mechanism and framework the expert uses to address it. The "new vehicle" is the centerpiece of the Perfect Webinar and the platform's primary differentiation engine.
**Primary consumers:** Brand Strategy Agent, Webinar Builder, Ad Creative Builder, Content Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `root_cause_map.surface_problems` | **[P1]** Surface Problems | Array[String] | The symptoms the avatar presents with — in their language | ["Fatigue", "Brain fog", "Unexplained weight gain", "Hair loss", "Cold intolerance"] |
| `root_cause_map.conventional_diagnosis` | **[P1]** Conventional Diagnosis | String | What conventional medicine typically tells these patients — the official label | "Hypothyroidism — managed with Levothyroxine" |
| `root_cause_map.conventional_failure_reason` | **[P1]** Conventional Failure Reason | String | Why conventional medicine's approach does not fully resolve the problem | "Conventional medicine treats the thyroid in isolation. It manages TSH numbers but never asks why the immune system is attacking the thyroid gland in the first place." |
| `root_cause_map.true_root_causes` | **[P1]** True Root Causes | Array[String] | The actual upstream drivers the expert identifies and addresses | ["Autoimmune trigger — leaky gut", "Chronic stress dysregulating HPA axis", "Unaddressed nutrient deficiencies (selenium, iodine, zinc)", "Environmental toxin burden"] |
| `root_cause_map.new_vehicle_name` | **[P1]** New Vehicle Name | String | The proprietary name for the expert's mechanism. One of the highest-leverage fields in the entire dossier — this name appears in every downstream output. | "The Thyroid Root Cause Reset" |
| `root_cause_map.new_vehicle_description` | **[P1]** New Vehicle Description | String | Plain-language description of what the new vehicle is and why it works where other approaches fail | "A 5-phase protocol that identifies and addresses the specific autoimmune triggers driving the thyroid attack — rather than managing the downstream hormone numbers." |
| `root_cause_map.mechanism_analogy` | Mechanism Analogy | String | A simple analogy that makes the mechanism immediately understandable to a non-clinical buyer | "It's like having a fire alarm going off and unplugging the alarm instead of putting out the fire. Conventional medicine unplugs the alarm. We find the fire." |
| `root_cause_map.new_vehicle_phases` | New Vehicle Phases | Array[String] | The named phases or steps of the expert's protocol, if it has a defined structure | ["Phase 1: Root Cause Testing", "Phase 2: Gut Healing", "Phase 3: Immune Recalibration", "Phase 4: Hormone Optimization", "Phase 5: Maintenance Protocol"] |
| `root_cause_map.why_vehicle_is_new` | **[P1]** Why Vehicle Is New | String | The specific reason this approach is genuinely different from everything the avatar has already tried | "Most functional medicine protocols address the thyroid with generalized gut and hormone support. Ours runs advanced autoimmune-specific testing first to identify the exact immune dysregulation pattern." |
| `root_cause_map.one_big_domino_draft` | **[P1]** One Big Domino Draft | String | The single belief that, if installed, makes the offer obvious. The thesis of the Perfect Webinar. | "If I can show you that your thyroid symptoms are actually driven by an autoimmune process that conventional medicine never tested for — and that we can identify and address that exact process — would that change everything you've been told about what's possible for you?" |
| `root_cause_map.claim_restrictions` | **[P1]** Claim Restrictions | Array[String] | Specialty-specific and jurisdiction-specific compliance flags — read by every Builder agent before generating any output | ["Cannot claim to 'cure' or 'reverse' autoimmune disease in paid ads", "Must include 'results not typical' on testimonials", "Cannot make FDA disease treatment claims for supplements"] |
| `root_cause_map.mechanism_confidence` | **[P1]** Mechanism Confidence | Enum | Fully-named / Partially-named / Unnamed — routes Builder agents to appropriate naming workflow if not yet named | "Fully-named" |

**Consuming agents:** Brand Strategy, Webinar Builder, Ad Creative Builder, Content Builder (mechanism narrative, new vehicle reveal, differentiation messaging)

---

## Section 6 — Clinical Philosophy

**Schema key:** `clinical_philosophy`
**Field count:** 10
**LEP layer:** A — Identity Core
**Purpose:** The expert's belief system about healing, their methodology framework, what they reject about conventional medicine, and the professional credentials and credibility anchors they carry. Provides the intellectual and ethical backbone that makes the brand feel substantive — not just persuasive.
**Primary consumers:** Brand Strategy Agent, Content Builder, Webinar Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `clinical_philosophy.core_belief` | **[P1]** Core Belief | String | The single most fundamental thing they believe about healing that most doctors get wrong | "The body has an innate capacity to heal when you remove what is blocking it and provide what it needs. Most medicine is focused on suppressing symptoms, not creating conditions for healing." |
| `clinical_philosophy.methodology_name` | Methodology Name | String | What they call their clinical methodology, if it has a name | "Root Cause Functional Medicine" |
| `clinical_philosophy.what_they_reject` | What They Reject | Array[String] | The specific conventional medicine practices or assumptions they fundamentally disagree with | ["Symptom-only treatment", "Lab ranges built on sick populations", "Polypharmacy as a first resort", "The idea that chronic disease is inevitable"] |
| `clinical_philosophy.what_they_champion` | What They Champion | Array[String] | The practices, frameworks, and principles they actively advocate for | ["Root cause testing", "Personalized protocols", "The gut-immune connection", "Patient education and empowerment"] |
| `clinical_philosophy.credentials` | **[P1]** Credentials | Array[String] | All relevant credentials, certifications, and training programs — pre-populated by Web Scraper | ["ND", "IFMCP", "Institute for Functional Medicine Certified Practitioner"] |
| `clinical_philosophy.credibility_anchors` | **[P1]** Credibility Anchors | Array[String] | Non-credential credibility signals — media, publications, speaking, notable associations — pre-populated by Web Scraper | ["Featured in Healthline", "500+ patients treated", "Trained under Dr. Mark Hyman", "11 years clinical experience"] |
| `clinical_philosophy.years_treating_condition` | Years Treating Primary Condition | Integer | Years specifically treating the avatar's primary condition — more specific than general years in practice | 9 |
| `clinical_philosophy.notable_results_summary` | **[P1]** Notable Results Summary | String | A summary statement of the most compelling collective results across the patient population | "Over 500 patients restored thyroid function without lifelong medication dependence. Average patient reduces or eliminates thyroid medication within 90 days." |
| `clinical_philosophy.intellectual_influences` | **[P3]** Intellectual Influences | Array[String] | The practitioners, researchers, or authors who most shaped their clinical thinking | ["Dr. Alessio Fasano (leaky gut research)", "Dr. Tom O'Bryan (autoimmune)", "Dr. Izabella Wentz (Hashimoto's)"] |
| `clinical_philosophy.patient_relationship_style` | Patient Relationship Style | String | How they describe the ideal practitioner-patient relationship | "I am a guide, not a prescriber. My job is to educate, test, and build a protocol — and then support the patient in executing it. The healing is theirs." |

**Consuming agents:** Brand Strategy, Content Builder, Webinar Builder

---

## Section 7 — Offer Architecture

**Schema key:** `offer_architecture`
**Field count:** 25
**LEP layer:** A — Identity Core (confirmed at onboarding); Layer B enriches with live performance data (conversion rates, LTV by tier, price sensitivity signals)
**Purpose:** The complete commercial offer stack — all four tiers, mechanism and offer names, value stack, guarantee, urgency and scarcity levers, paid traffic readiness, and pricing history. Every funnel, every webinar close, every sales script, every email sequence is built around the data here. Full extraction methodology in Step 6.
**Primary consumers:** Growth Strategy Agent, Funnel Builder, Sales Script Builder, Email Builder, Webinar Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `offer_architecture.core_transformation` | **[P1]** Core Transformation | String | The specific, vivid outcome the core offer delivers — the dream result in the most concrete language possible | "Off thyroid medication, sustained energy from morning through evening, normal weight, clear thinking — in 90 days" |
| `offer_architecture.high_ticket_name` | **[P1]** High-Ticket Offer Name | String | The name of the core Tier 2 offer | "The 90-Day Thyroid Restoration Program" |
| `offer_architecture.high_ticket_price` | **[P1]** High-Ticket Price | Integer | The investment amount for the core Tier 2 offer in USD | 7500 |
| `offer_architecture.fulfillment_model` | **[P1]** Fulfillment Model | Enum | 1:1-with-expert / Hybrid-coach-led / Group / Self-paced / Hybrid-self-paced-with-coaching | "Hybrid-coach-led" |
| `offer_architecture.program_duration` | **[P1]** Program Duration | String | How long the core program runs | "90 days" |
| `offer_architecture.value_stack` | Value Stack | Array[Object] | Each object: `{element_name, description, assigned_value}`. Full itemized value stack for the core offer. | [{element_name: "Personal Coach Access", description: "Dedicated coach, monthly Zoom, daily text support", assigned_value: 6000}] |
| `offer_architecture.value_stack_total` | Value Stack Total | Integer | Sum of all assigned values — should be 10x the price | 74500 |
| `offer_architecture.mechanism_name` | **[P1]** Mechanism Name | String | The proprietary name for the expert's method — the brand anchor. Must match `root_cause_map.new_vehicle_name`. | "The Thyroid Root Cause Reset" |
| `offer_architecture.guarantee_concept` | Guarantee Concept | String | The risk reversal statement — what the expert promises and what happens if result is not achieved | "90-Day Results Guarantee — achieve the defined outcome markers or we continue working with you at no additional cost until you do" |
| `offer_architecture.guarantee_type` | Guarantee Type | Enum | Results / Effort / Assessment / Satisfaction | "Results" |
| `offer_architecture.bonus_ideas` | Bonus Concepts | Array[Object] | Each object: `{name, description, false_belief_addressed, assigned_value}`. Bonuses map directly to the three false beliefs. | [{name: "The Quick-Start Lab Guide", description: "Which tests to order and what to say to your doctor", false_belief_addressed: "vehicle", assigned_value: 497}] |
| `offer_architecture.urgency_scarcity_levers` | Urgency & Scarcity Levers | Array[String] | Real urgency and scarcity only — cohort dates, coaching capacity limits, price increases, health cost-of-inaction framing | ["New cohort starts first Monday of each month — 12 spots per cohort", "Each coach carries maximum 70 clients"] |
| `offer_architecture.lead_magnet_concept` | **[P1]** Lead Magnet Concept | String | The Tier 1 attraction offer — free or low-cost entry that generates the lead | "Paid Thyroid Root Cause Assessment ($67) — 45-minute diagnostic that identifies specific autoimmune drivers and shows the path forward" |
| `offer_architecture.lead_magnet_price` | **[P1]** Lead Magnet Price | Integer | Price of the Tier 1 offer — 0 if free | 67 |
| `offer_architecture.tier1_exists` | **[P1]** Tier 1 Exists | Boolean | Whether a functioning Tier 1 attraction offer currently exists — routes offer gap flagging | true |
| `offer_architecture.downsell_name` | Downsell Name | String | The Tier 3 offer name — accessible entry for buyers who can't commit to the core offer | "The Thyroid Reset: Self-Paced Program" |
| `offer_architecture.downsell_price` | Downsell Price | Integer | Price of the Tier 3 downsell offer | 997 |
| `offer_architecture.tier3_exists` | **[P1]** Tier 3 Exists | Boolean | Whether a functioning Tier 3 downsell currently exists | false |
| `offer_architecture.continuity_name` | Continuity Name | String | The Tier 4 recurring offer name | "The Thyroid Maintenance Membership" |
| `offer_architecture.continuity_price_monthly` | Continuity Monthly Price | Integer | Monthly price of the Tier 4 continuity offer | 197 |
| `offer_architecture.tier4_exists` | **[P1]** Tier 4 Exists | Boolean | Whether a functioning Tier 4 continuity offer currently exists | false |
| `offer_architecture.payment_plan_structure` | Payment Plan Structure | String | How the core offer payment plan is structured | "3 payments of $2,750 — or single pay $7,500" |
| `offer_architecture.intake_form_url` | Intake Form URL | URL | URL of the expert's current intake/application form — used by Funnel Builder to link CTAs | "https://mitchellfunctionalhealth.com/apply" |
| `offer_architecture.price_point_history` | **[P1]** Price Point History | Enum | Sold-successfully-at-this-level / Sold-unsuccessfully / New-price-untested | "Sold-successfully-at-this-level" |
| `offer_architecture.offer_gap_flags` | **[P1]** Offer Gap Flags | Array[String] | Silent Diagnosis flags from the Offer Architecture Builder — missing tiers, underpricing, no guarantee, non-scalable model. Delivered to Layer 2 as a priority brief. | ["Tier 3 downsell not built — buyers without budget for core offer have no path", "Tier 4 continuity not yet built — MRR gap"] |

**Consuming agents:** Growth Strategy, Funnel Builder, Sales Script Builder, Email Builder, Webinar Builder

---

## Section 8 — Perfect Webinar Raw Material

**Schema key:** `webinar_raw_material`
**Field count:** 15
**LEP layer:** A — Identity Core
**Purpose:** The raw persuasion architecture that the Webinar Builder Agent assembles into a full Perfect Webinar script. Every field here maps directly to a component of the Brunson Perfect Webinar framework. Populated by synthesizing data from avatar psychology, root cause map, clinical philosophy, and offer architecture sections — plus the expert's own webinar-specific answers in the conversation flow.
**Note:** Fields in Steps 3–6 that reference `webinar.origin_story_*` map to `webinar_raw_material.origin_story_before`, `webinar_raw_material.origin_story_discovery`, and `webinar_raw_material.origin_story_after` in this schema.
**Primary consumers:** Webinar Builder Agent (primary), Ad Creative Builder (hook concepts feed ad creation)

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `webinar_raw_material.one_big_domino` | **[P1]** One Big Domino | String | The single belief that, if accepted, makes the offer obvious and objections dissolve. The thesis of the entire webinar. | "If your thyroid symptoms are being driven by an autoimmune process that nobody has ever tested for — and we can identify and address that exact process — then everything your doctor told you about what's possible for your thyroid is wrong." |
| `webinar_raw_material.secret_1` | **[P1]** Secret 1 — Vehicle Belief Shift | String | The content block that dismantles `avatar_psychology.false_belief_vehicle` and replaces it with belief in the vehicle. | "Why the standard thyroid protocol always fails — and the one test that changes everything" |
| `webinar_raw_material.secret_2` | **[P1]** Secret 2 — Internal Belief Shift | String | The content block that dismantles `avatar_psychology.false_belief_internal` and replaces it with belief in self. | "Why it's not your willpower — and why people who 'can never stick to anything' get the fastest results with this approach" |
| `webinar_raw_material.secret_3` | **[P1]** Secret 3 — External Belief Shift | String | The content block that dismantles `avatar_psychology.false_belief_external` and replaces it with a path forward. | "How to do this with a full schedule, a family, and a budget — the three things that stopped you before aren't what you think they are" |
| `webinar_raw_material.origin_story_before` | **[P1]** Origin Story — Before State | String | The before state of the expert's own story — or patient story used as the Epiphany Bridge. Also referenced as `webinar.origin_story_before` in Steps 3–6 documentation. | "At 34, I had been told my labs were normal for three years. I was sleeping 10 hours and waking up exhausted." |
| `webinar_raw_material.origin_story_discovery` | **[P1]** Origin Story — Discovery | String | The turning point — what changed, what was found, what led to the new vehicle. Also referenced as `webinar.origin_story_discovery`. | "When I ran my own advanced autoimmune panel — the test my endocrinologist said I didn't need — I had the highest anti-TPO antibodies my colleague had ever seen." |
| `webinar_raw_material.origin_story_after` | **[P1]** Origin Story — After State | String | The result — who they became on the other side. Also referenced as `webinar.origin_story_after`. | "Within 60 days of addressing the autoimmune drivers, my antibodies dropped by 70%. I was off Levothyroxine in 8 months. That was 7 years ago." |
| `webinar_raw_material.hook_concepts` | **[P1]** Hook Concepts | Array[String] | 3–5 webinar title and hook concepts generated from the One Big Domino and avatar psychology | ["The Hidden Autoimmune Driver Behind Your Thyroid Symptoms (And Why Your Doctor Has Never Tested for It)", "Why Your Thyroid Medication Is Working — and Why You Still Feel Terrible"] |
| `webinar_raw_material.mechanism_demonstration` | Mechanism Demonstration | String | How the mechanism is demonstrated during the webinar — the teaching moment that makes the audience believe before the offer is revealed | "Live walkthrough of the autoimmune testing panel — what it shows, what it means, and a real before/after case study showing antibody reduction and symptom resolution" |
| `webinar_raw_material.case_study_primary` | **[P1]** Primary Case Study | Object | `{avatar_type, before_state, what_was_tried, turning_point, result, timeline, quote}` — the main proof story used in the webinar. Should match the avatar as closely as possible. | {avatar_type: "42-year-old woman, Hashimoto's, 5-year history", result: "Off medication in 8 months, 22 lbs lost, full energy restored", timeline: "First results in 3 weeks"} |
| `webinar_raw_material.stack_close_structure` | Stack Close Structure | String | How the offer reveal is sequenced — what gets introduced when | "Core program → coach access → community → Bonus 1 → Bonus 2 → Bonus 3 → Guarantee reveal → Price reveal" |
| `webinar_raw_material.faq_objections` | **[P1]** FAQ Objections | Array[Object] | Each object: `{objection, answer}`. Sourced from `avatar_psychology.objections_primary`. Pre-scripted Q&A answers for the webinar close. | [{objection: "Is this covered by insurance?", answer: "This program is not insurance-covered — here is why that is actually to your advantage..."}] |
| `webinar_raw_material.webinar_cta_language` | CTA Language | String | The specific language used for the call to action in the webinar close | "Click the button below to claim your spot in this month's cohort. You'll be taken to a short application — we want to make sure this is the right fit for you before we begin." |
| `webinar_raw_material.false_urgency_avoidance` | Real Urgency Notes | String | Notes on genuine urgency and scarcity to use — ensures the webinar never uses manufactured urgency | "12 spots per cohort — real. Coach capacity limit — real. Price increasing after beta phase — real. Use these only." |
| `webinar_raw_material.webinar_length_target` | Target Length | Enum | 45-min / 60-min / 75-min / 90-min | "60-min" |

**Consuming agents:** Webinar Builder (primary); Ad Creative Builder (hook concepts)

---

## Section 9 — Proof Bank

**Schema key:** `proof_bank`
**Field count:** 11
**LEP layer:** A — Identity Core (base stories confirmed at onboarding); Layer A grows continuously as new stories are added in subsequent sessions
**Purpose:** The social proof library — patient transformation stories, testimonials, before/after data, and collective outcome statistics. Every close sequence, every ad, every email nurture sequence, every webinar proof stack draws from here. The depth of the Proof Bank is one of the most important conversion readiness signals in the platform.
**Primary consumers:** Ad Creative Builder, Email Builder, Webinar Builder, Sales Script Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `proof_bank.transformation_stories` | **[P1]** Transformation Stories | Array[Object] | Each object: `{story_id, avatar_match, before_state, treatments_tried, turning_point, result, timeline, direct_quote, media_available}`. Full structured case study library. | [{avatar_match: "Dismissed Denise", result: "Off medication, 18 lbs lost, full energy returned", timeline: "First result in 2 weeks, full result in 10 weeks", direct_quote: "I finally feel like the person my family deserves."}] |
| `proof_bank.most_dramatic_transformation` | **[P1]** Most Dramatic Transformation | Object | The single most dramatic before/after story — identified for priority use in webinar proof stack and high-conversion ads | {result: "Off 20-year thyroid medication in 6 months", timeline: "Felt first change in week 3"} |
| `proof_bank.fastest_result` | Fastest Result Story | Object | The story with the shortest time-to-result — maximizes the Hormozi time-delay score in the value equation | {result: "Energy restored and brain fog gone", timeline: "First noticeable change in 9 days"} |
| `proof_bank.skeptic_to_believer` | Skeptic-to-Believer Story | Object | The story of someone who was most skeptical and still got results — most powerful for Level 3 aware audiences | {background: "Had tried 4 other functional medicine practitioners. Said she would never try again.", result: "Complete symptom resolution in 12 weeks"} |
| `proof_bank.collective_results_stats` | **[P1]** Collective Results Stats | Object | `{patients_treated, avg_time_to_first_result, medication_reduction_rate, completion_rate}` — aggregate outcome data across the patient population | {patients_treated: 500, avg_time_to_first_result: "2-3 weeks", medication_reduction_rate: "73% reduce or eliminate within 6 months"} |
| `proof_bank.testimonials_text` | Text Testimonials | Array[Object] | Each object: `{name_or_initials, credential_or_context, testimonial_text, result_highlighted}`. Written testimonials with permissions confirmed. | [{name_or_initials: "Jennifer M.", credential_or_context: "43, Hashimoto's, 7-year history", testimonial_text: "I was told I'd be on medication forever. I am off it."}] |
| `proof_bank.video_testimonials` | **[P3]** Video Testimonials | Array[File] | Uploaded video testimonial files | [file references] |
| `proof_bank.media_mentions` | Media Mentions | Array[Object] | Each object: `{outlet, type, url, excerpt}`. Pre-populated by Web Scraper from publicly available coverage. | [{outlet: "Healthline", type: "Feature article", excerpt: "Dr. Mitchell's approach challenges the standard thyroid protocol..."}] |
| `proof_bank.before_after_data` | Before/After Data Points | Array[Object] | Each object: `{metric, before_value, after_value, timeframe}`. Quantitative before/after data. | [{metric: "Anti-TPO antibodies", before_value: "1,200 IU/mL", after_value: "180 IU/mL", timeframe: "90 days"}] |
| `proof_bank.proof_bank_depth_score` | Proof Bank Depth Score | Integer | Internal quality score 0–100 reflecting the richness of the proof bank — number and quality of stories, variety of avatar types. Below 40: Silent Diagnostician flags a proof-building sprint as a 30-day priority. | 45 |
| `proof_bank.missing_proof_flags` | Missing Proof Flags | Array[String] | Gaps identified by Silent Diagnostician — delivered to Growth Strategy as a 30-day proof plan | ["No skeptic-to-believer story captured yet", "No video testimonials uploaded"] |

**Consuming agents:** Ad Creative Builder, Email Builder, Webinar Builder, Sales Script Builder

---

## Section 10 — Competitive Landscape

**Schema key:** `competitive_landscape`
**Field count:** 8
**LEP layer:** A — Identity Core (confirmed at onboarding); Layer B continuously updates competitor intelligence automatically
**Purpose:** What the avatar has tried before finding this expert — from their perspective. The failed solutions, why each failed, and what makes this expert genuinely different. This section is the raw material for vehicle doubt setup in the webinar and for differentiation messaging across all platforms. LEP Layer B's Competitive Intelligence sub-layer adds continuous monitoring of named competitors defined here.
**Primary consumers:** Brand Strategy Agent, Ad Creative Builder, Webinar Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `competitive_landscape.alternatives_tried` | **[P1]** Alternatives Tried | Array[Object] | Each object: `{alternative, promise_made, why_it_failed, avatar_conclusion}`. The full sequence of what the avatar tried before this expert. | [{alternative: "Standard endocrinologist", promise_made: "Medication will normalize your levels", why_it_failed: "Numbers normalized but symptoms continued", avatar_conclusion: "Even when the labs look right, I still feel terrible"}] |
| `competitive_landscape.direct_competitors` | Direct Competitors | Array[String] | Named practitioners, programs, or platforms competing directly for the same avatar — seeded into LEP Layer B competitive monitoring | ["Dr. Izabella Wentz Hashimoto's Protocol", "Paloma Health"] |
| `competitive_landscape.competitor_differentiation` | **[P1]** Competitor Differentiation | String | What specifically makes this expert's approach different from named competitors — concrete and demonstrable | "Paloma Health tests TSH only and provides medication management. We run 14 autoimmune markers, identify the specific triggers, and address root cause through protocol — not medication management." |
| `competitive_landscape.category_villain` | **[P1]** Category Villain | String | The conventional approach or belief system that is framed as the villain in the expert's narrative | "The conventional medicine belief that thyroid disease is a hormone problem, not an autoimmune problem — and that the answer is replacing the hormone rather than addressing why the immune attack is happening" |
| `competitive_landscape.why_others_fail_summary` | **[P1]** Why Others Fail Summary | String | One-paragraph summary of why every alternative the avatar has tried has failed — the setup for the new vehicle reveal | "Every approach the avatar has tried has failed for the same reason: none of them identified or addressed the autoimmune trigger. They managed downstream symptoms while the root cause continued unchecked." |
| `competitive_landscape.market_awareness_context` | Market Awareness Context | String | What the market currently believes about the expert's specialty — the water the avatar is swimming in | "Most avatars have heard of 'functional medicine' but have mixed or negative associations from expensive, unproductive experiences with generalist practitioners." |
| `competitive_landscape.price_comparison_context` | Price Comparison Context | String | How the expert's price compares to what the avatar has already spent — often reveals that the investment is economical relative to years of failed alternatives | "Average avatar has spent $8,000–$15,000 on conventional care, medication, and failed alternatives over 5 years. The $7,500 program represents less than one year of what they've already been spending — and it actually addresses the cause." |
| `competitive_landscape.trust_barriers` | Trust Barriers | Array[String] | The specific reasons the avatar is skeptical of this category of solution — beyond individual false beliefs | ["Has been burned by previous functional medicine practitioners", "Cannot tell the difference between qualified and unqualified practitioners", "Worried it's just expensive supplements"] |

**Consuming agents:** Brand Strategy, Ad Creative Builder, Webinar Builder; LEP Layer B extends with live competitor monitoring

---

## Section 11 — Content Audit & Existing Assets

**Schema key:** `content_audit`
**Field count:** 19
**LEP layer:** A — Identity Core; pre-populated heavily by Web Scraper before first session
**Purpose:** An inventory of everything the expert already has in the world — digital footprint, content library, content strategy, email list, existing funnels, paid traffic readiness, and performance data. Prevents the Builder Layer from building things that already exist. Allows Growth Strategy Agent to build on what is already working.
**Primary consumers:** Growth Strategy Agent, Content Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `content_audit.website_status` | **[P1]** Website Status | Enum | Live-optimized / Live-needs-work / Under-construction / Does-not-exist | "Live-needs-work" |
| `content_audit.social_platforms_active` | **[P1]** Active Social Platforms | Array[String] | Platforms with meaningful active presence — pre-populated by Web Scraper | ["Instagram", "Facebook", "YouTube"] |
| `content_audit.instagram_handle` | Instagram Handle | String | Instagram username — pre-populated by Web Scraper | "@mitchellfunctionalhealth" |
| `content_audit.instagram_follower_count` | Instagram Followers | Integer | Current follower count — pre-populated by Web Scraper | 4200 |
| `content_audit.facebook_page_name` | Facebook Page Name | String | Facebook business page name — pre-populated by Web Scraper | "Mitchell Functional Health" |
| `content_audit.facebook_follower_count` | Facebook Followers | Integer | Current page follower count — pre-populated by Web Scraper | 2800 |
| `content_audit.youtube_channel_url` | YouTube Channel URL | URL | YouTube channel URL — pre-populated by Web Scraper | "https://youtube.com/@mitchellfh" |
| `content_audit.linkedin_url` | LinkedIn URL | URL | LinkedIn profile or company page URL — pre-populated by Web Scraper | "https://linkedin.com/in/drsarahmitchell" |
| `content_audit.tiktok_handle` | TikTok Handle | String | TikTok username — pre-populated by Web Scraper | "@mitchellfunctionalhealthnd" |
| `content_audit.podcast_name` | Podcast Name | String | Podcast name — pre-populated by Web Scraper | "Root Cause Health Podcast" |
| `content_audit.email_list_size` | **[P1]** Email List Size | Integer | Current email list subscriber count | 1850 |
| `content_audit.email_platform` | Email Platform | String | Email service provider used | "ActiveCampaign" |
| `content_audit.content_pillars` | **[P1]** Content Pillars | Array[String] | The 3–5 core topic territories the expert owns — the subjects they return to repeatedly and that define their content identity | ["Thyroid root cause", "Autoimmune healing", "Conventional medicine gaps", "Lab testing education", "Patient transformation stories"] |
| `content_audit.preferred_content_formats` | **[P1]** Preferred Content Formats | Array[String] | The formats the expert gravitates toward or performs best with — informed by existing content analysis | ["Long-form YouTube", "Instagram carousel", "Short-form video (Reels)", "Email newsletter"] |
| `content_audit.content_posting_frequency` | Content Posting Frequency | String | Current posting frequency across their primary platform(s) | "Instagram: 4x/week. YouTube: 1x/week. Email: 2x/month." |
| `content_audit.seo_keywords_primary` | **[P3]** SEO Keywords Primary | Array[String] | Top search terms the expert ranks for or is targeting — used by Content Builder and Website Builder | ["hashimoto's treatment without medication", "thyroid root cause", "functional medicine thyroid doctor"] |
| `content_audit.best_performing_content` | Best Performing Content | Array[String] | URLs or titles of their highest-performing organic content — by engagement, shares, or comments. Used by Ad Builder as proven hook signals. | ["The 5 thyroid tests your doctor isn't running — 47K views", "Why your medication is working but you still feel terrible — most shared post"] |
| `content_audit.existing_lead_magnets` | Existing Lead Magnets | Array[Object] | Each object: `{name, url, lead_count, active}`. Current opt-in offers. | [{name: "5 Thyroid Tests PDF", url: "...", lead_count: 340, active: true}] |
| `content_audit.existing_funnels` | Existing Funnels | Array[Object] | Each object: `{name, type, platform, status, conversion_rate}`. Active or dormant funnels. | [{name: "Webinar funnel", type: "Webinar opt-in", platform: "ClickFunnels", status: "Dormant", conversion_rate: null}] |

**Consuming agents:** Growth Strategy, Content Builder, Ad Builder (proven hooks from best_performing_content)

---

## Section 12 — Dream Practice Vision & Traffic Reality

**Schema key:** `dream_vision_traffic`
**Field count:** 14
**LEP layer:** A — Identity Core
**Purpose:** The north star the expert is building toward and the current reality they are starting from. The gap between these two data sets is the Growth Strategy Agent's primary operating brief — every strategic recommendation exists to close this gap.
**Primary consumers:** Growth Strategy Agent (primary)

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `dream_vision_traffic.revenue_goal_12mo` | **[P1]** 12-Month Revenue Goal | Integer | Target revenue in the next 12 months in USD | 2000000 |
| `dream_vision_traffic.revenue_goal_3yr` | 3-Year Revenue Goal | Integer | 3-year vision revenue target | 10000000 |
| `dream_vision_traffic.patient_volume_target` | **[P1]** Patient Volume Target | Integer | Target number of active clients at full operation | 200 |
| `dream_vision_traffic.lifestyle_vision` | Lifestyle Vision | String | What the expert's ideal working life looks like — hours, travel, team, involvement level | "Working 3 days per week in a strategic and educational role, team fully handling delivery, speaking 6 times per year, able to take real vacations" |
| `dream_vision_traffic.impact_vision` | Impact Vision | String | The scope of impact they want to have — beyond revenue | "Prove to the world that autoimmune thyroid disease is reversible — change the standard of care" |
| `dream_vision_traffic.exit_or_build` | **[P1]** Exit or Build | Enum | Building-to-sell / Building-to-hold / Not-sure | "Building-to-hold" |
| `dream_vision_traffic.current_lead_sources` | **[P1]** Current Lead Sources | Array[String] | Where new patients are currently coming from | ["Referrals from existing patients", "Organic Instagram", "Google search"] |
| `dream_vision_traffic.paid_traffic_history` | **[P1]** Paid Traffic History | Enum | Currently-running / Has-run-in-past / Never-run | "Never-run" |
| `dream_vision_traffic.audience_temperature` | **[P1]** Audience Temperature | Enum | Cold-only / Warm-only / Mixed-cold-and-warm / Primarily-warm | "Primarily-warm" |
| `dream_vision_traffic.monthly_new_leads` | **[P1]** Monthly New Leads | Integer | Approximate current monthly lead volume across all sources | 45 |
| `dream_vision_traffic.current_conversion_rate` | Current Conversion Rate | String | Approximate conversion rate from lead to paid client | "Roughly 1 in 5 who have a consultation" |
| `dream_vision_traffic.biggest_growth_obstacle` | **[P1]** Biggest Growth Obstacle | String | What the expert believes is the single biggest thing standing between them and growth | "I don't have a consistent way to bring in new leads outside of referrals. Everything depends on me and word of mouth." |
| `dream_vision_traffic.tech_stack` | **[P1]** Tech Stack | Array[String] | CRM, funnel, email, booking, and payment tools currently in use | ["GoHighLevel", "ClickFunnels", "Stripe", "Acuity"] |
| `dream_vision_traffic.team_growth_readiness` | Team Growth Readiness | Enum | Ready-to-hire / Considering / Not-yet-ready | "Considering" |

**Consuming agents:** Growth Strategy (primary — gap analysis, 90-day plan, channel selection); Campaign Planner

---

## Section 13 — Business Context & Growth Intelligence

**Schema key:** `business_context`
**Field count:** 18
**LEP layer:** A — Identity Core
**Purpose:** Operational details that shape strategy — business structure, compliance context, growth history, paid traffic readiness, IP assets, and the expert's personal capacity and constraints. The Growth Strategy Agent reads this section to ensure every recommendation is executable given the expert's actual situation.
**Primary consumers:** Growth Strategy Agent, Email Builder, Compliance layer, Ad Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `business_context.business_entity_type` | Business Entity Type | String | LLC, PLLC, S-Corp, sole proprietor, etc. | "PLLC" |
| `business_context.licensing_states` | **[P1]** Licensing States | Array[String] | States where the expert is licensed to practice — used to set geographic ad targeting limits | ["Tennessee", "Texas", "Florida"] |
| `business_context.compliance_context` | **[P1]** Compliance Context | String | Summary of key compliance constraints for this expert's specialty and jurisdiction. Read by every Builder agent before generating any claim-bearing output. | "ND in Tennessee — cannot make disease treatment claims in advertising. FTC testimonial guidelines apply to all patient outcome claims. Cannot claim to cure or reverse named conditions in paid media." |
| `business_context.growth_history` | Growth History | String | A brief narrative of how the practice has grown to its current state | "Started as a solo ND in 2015. Added telehealth in 2020. Grew from $8K/month to $45K/month primarily through referrals and one webinar run in 2022." |
| `business_context.previous_marketing_attempts` | Previous Marketing Attempts | Array[Object] | Each object: `{type, outcome, what_was_learned}`. What they've tried in marketing and what happened. | [{type: "Facebook ads", outcome: "Spent $3K, no conversions", what_was_learned: "Offer wasn't clear. Sent to homepage, no funnel."}] |
| `business_context.preferred_growth_channel` | **[P1]** Preferred Growth Channel | String | The traffic and growth channel the expert is most energized by or most comfortable with | "Long-form YouTube content — I like teaching and it builds real trust" |
| `business_context.founder_capacity_hours` | **[P1]** Founder Weekly Capacity | Integer | Hours per week the expert can realistically invest in growth activities | 8 |
| `business_context.delivery_capacity_current` | **[P1]** Current Delivery Capacity | Integer | How many more clients the expert could take on right now without additional team | 15 |
| `business_context.insurance_model` | **[P1]** Insurance Model | Enum | Insurance-only / Cash-pay-only / Hybrid / Not-applicable | "Cash-pay-only" |
| `business_context.referral_sources` | Referral Sources | Array[String] | Who refers patients to this expert — other practitioners, patients, platforms | ["Former patients", "Local OBGYNs who don't treat thyroid autoimmune", "Naturopathic college alumni network"] |
| `business_context.seasonality_patterns` | Seasonality Patterns | String | Known peaks and valleys in demand through the year — used by Campaign Planner for always-on calendar | "January is highest demand — New Year resolution buyers. August slowdown. November-December uptick around health goals before year end." |
| `business_context.monthly_ad_spend_willingness` | **[P1]** Monthly Ad Spend Willingness | Enum | Not-yet-ready / Under-$1K / $1K–$3K / $3K–$10K / $10K–$30K / $30K+ | "$3K–$10K" |
| `business_context.primary_ad_platform` | **[P1]** Primary Ad Platform | Enum | Facebook-Meta / Google / YouTube / TikTok / Multiple / Not-decided | "Facebook-Meta" |
| `business_context.ad_account_status` | **[P1]** Ad Account Status | Enum | Active-and-running / Exists-not-running / Needs-setup | "Needs-setup" |
| `business_context.pixel_installed` | **[P1]** Pixel Installed | Boolean | Whether a Meta Pixel (or equivalent) is installed on the expert's website — required before paid traffic can be run | false |
| `business_context.supplement_line_exists` | Supplement Line Exists | Boolean | Whether the expert has a proprietary supplement or product line — significant additional revenue tier if present | false |
| `business_context.book_or_ip_exists` | Book or IP Exists | Boolean | Whether the expert has published a book, course, or other formal IP product — pre-populated by Web Scraper | false |
| `business_context.speaking_engagement_status` | Speaking Engagement Status | Enum | Active-speaker / Occasional / Not-currently / Not-interested — pre-populated by Web Scraper | "Occasional" |

**Consuming agents:** Growth Strategy (primary); Email Builder; Compliance layer (reads compliance_context before every output); Ad Builder (reads ad_account_status, pixel_installed before building campaigns)

---

## Section 14 — Expert Personal Story

**Schema key:** `expert_personal_story`
**Field count:** 7
**LEP layer:** A — Identity Core
**Purpose:** The expert's own health journey or mission origin story — often the most emotionally powerful brand content they have and the most underused. A personal story creates trust faster than any credential. This section populates the Epiphany Bridge of the Perfect Webinar and is the source material for the expert's personal brand narrative across all platforms. Extracted by the Story Miner sub-agent. Fields in Steps 3–6 that reference `story.*` map to the `expert_personal_story.*` keys below.
**Primary consumers:** Content Builder, Ad Creative Builder, Webinar Builder

| Field ID | Field Name | Type | Description | Example |
|----------|-----------|------|-------------|---------|
| `expert_personal_story.story_has_personal_health_journey` | **[P1]** Has Personal Health Journey | Boolean | Whether the expert has a personal health journey usable as brand content — routing flag for Webinar Builder and Content Builder | true |
| `expert_personal_story.story_personal_story_summary` | **[P1]** Personal Story Summary | String | 2–4 sentence narrative summary capturing the full arc. Also referenced as `story.personal_story_summary` in Steps 3–6 documentation. | "Dr. Mitchell spent 3 years being told her thyroid labs were 'normal' while her life was shrinking from exhaustion and brain fog. After running her own advanced autoimmune panel, she discovered antibodies that had gone undetected — and built the protocol that healed her. She has spent the 9 years since doing for others what nobody did for her." |
| `expert_personal_story.story_before_state` | **[P1]** Before State | String | Detailed description of who they were and what life looked like before the discovery — physical, emotional, professional | "Sleeping 10 hours, waking up like I hadn't slept at all. Missing half my working hours to exhaustion. Watching my kids' activities from the couch because I couldn't stand up. Feeling like a fraud in my own practice because I couldn't fix myself." |
| `expert_personal_story.story_what_they_almost_gave_up_on` | What They Almost Gave Up On | String | The darkest moment — the emotional low point of the story. Also referenced as `story.what_they_almost_gave_up_on` in Steps 3–6. | "I was two weeks from accepting that this was just what my life was going to be. I had stopped fighting with doctors and started researching disability accommodation." |
| `expert_personal_story.story_what_changed_everything` | **[P1]** What Changed Everything | String | The discovery — the insight, test, mentor, or moment that turned everything around and led to the new vehicle. Also referenced as `story.what_changed_everything` in Steps 3–6. | "I found a paper on anti-TPO antibodies and autoimmune thyroiditis that described my exact symptom picture in patients with 'normal' TSH. I ordered the test myself. The results were the beginning of everything." |
| `expert_personal_story.story_after_state` | After State | String | Detailed description of who they became on the other side of the discovery — the transformation result | "Running a full clinical practice and seeing 500+ patients through the same protocol that healed me. Off all medication. Energy to run 5Ks with my daughter. Present in a way I hadn't been in years." |
| `expert_personal_story.story_mission_statement` | **[P1]** Mission Statement | String | What they want for others because of what they went through — the purpose statement that drives the work | "Nobody should spend years being told they're fine when they're not. I built this practice and this protocol so that what happened to me never happens to anyone who finds us." |

**Consuming agents:** Content Builder, Ad Creative Builder, Webinar Builder (Epiphany Bridge); LEP Layer A — this section is the most permanent in the entire dossier; rarely changes once confirmed

---

## Downstream Agent Consumption Map

| Dossier Section | Schema Key | Primary Consumers | How It's Used |
|----------------|-----------|-------------------|---------------|
| Identity & Practice | `identity` | All agents | Universal context — appears in every agent's initialization |
| Voice DNA | `voice_dna` | All Layer 3 Builder agents | Every word the Builder Layer writes is calibrated against this first |
| Visual DNA | `visual_dna` | Ad Creative Builder, Website Builder, Content Builder | Visual direction for all designed assets |
| Avatar Psychology | `avatar_psychology` | All Builder agents, Brand Strategy, Growth Strategy | Hook selection, entry angle, false belief architecture, close language |
| Root Cause Map | `root_cause_map` | Brand Strategy, Webinar Builder, Ad Creative Builder, Content Builder | Mechanism narrative, new vehicle reveal, differentiation messaging |
| Clinical Philosophy | `clinical_philosophy` | Brand Strategy, Content Builder, Webinar Builder | Brand credibility layer, educational content angle, authority establishment |
| Offer Architecture | `offer_architecture` | Growth Strategy, Funnel Builder, Sales Script Builder, Email Builder, Webinar Builder | Stack construction, price reveal, guarantee, bonus sequence, close architecture |
| Perfect Webinar Raw Material | `webinar_raw_material` | Webinar Builder (primary), Ad Creative Builder | Direct input to webinar script; hook concepts feed ad creation |
| Proof Bank | `proof_bank` | Ad Creative Builder, Email Builder, Webinar Builder, Sales Script Builder | Case studies, testimonials, collective stats |
| Competitive Landscape | `competitive_landscape` | Brand Strategy, Ad Creative Builder, Webinar Builder | Vehicle doubt setup, differentiation messaging, villain framing; seeds LEP Layer B monitoring |
| Content Audit | `content_audit` | Growth Strategy, Content Builder, Ad Builder | Build on what works; avoid duplicating; proven hooks; ad readiness |
| Dream Vision & Traffic Reality | `dream_vision_traffic` | Growth Strategy (primary) | Gap analysis; 90-day plan construction; channel selection |
| Business Context | `business_context` | Growth Strategy, Email Builder, Compliance layer, Ad Builder | Realistic plan calibration; compliance filter; capacity planning; paid traffic readiness |
| Expert Personal Story | `expert_personal_story` | Content Builder, Ad Creative Builder, Webinar Builder | Epiphany Bridge; personal brand content; trust-building ads |

---

## Dossier Completion Score — Calculation

The Dossier Completion Score (0–100) is the primary health metric for the onboarding session. It powers the gamification layer (Step 3), gates Layer 2 activation (score 31+), and determines platform capability (Step 7 milestones).

**Score calculation — six weighted components:**

| Component | Weight | What It Measures |
|-----------|--------|-----------------|
| Field population rate | 35% | % of all 198 fields with any value (confirmed, agent-generated, or pending-approval) |
| Confirmation rate | 20% | % of populated fields where status = `confirmed` vs. `agent-generated` |
| Story richness | 15% | `proof_bank.transformation_stories` count × quality weight + `expert_personal_story.story_has_personal_health_journey` flag + `proof_bank.proof_bank_depth_score` |
| Voice DNA quality | 15% | `voice_dna.voice_confidence_score` normalized + `voice_dna.sample_extracts` count (min 3 for full credit) + confirmation rate of Voice DNA section |
| Offer stack completeness | 10% | Weighted count of confirmed tiers: Tier 1 (`tier1_exists`) + Tier 2 (price + name) + Tier 3 (`tier3_exists`) + Tier 4 (`tier4_exists`) |
| Visual asset uploads | 5% | Count of `pending-upload` fields resolved: logo, brand guide, expert photo |

**Score milestones (defined in Step 7):**

| Score | Milestone | What Unlocks |
|-------|-----------|-------------|
| 0–30 | Onboarding in progress | No Layer 2 activation |
| 31+ | **Fast-Start Complete** | `handoff_ready = true` — Layer 2 Brand Strategy + Growth Strategy activate |
| 61+ | **Full Build Mode** | All Layer 3 Builder agents run at full capability |
| 86+ | **Elite Dossier** | Maximum platform intelligence — LEP Layer B enrichment begins full cycle |

---

## Layer 5 — Living Expert Profile: Field Continuity

The 198 fields defined in this document are **Layer A (Identity Core)** of the Living Expert Profile (L5-1). They are the static foundation that the platform updates only when the expert makes intentional changes.

Layer B (~30 additional fields) and Layer C (~16 additional fields) of the LEP are populated entirely by the platform — built from Layer 3 output approvals, Layer 4 analytics, and Layer 5 Network Intelligence data. They are never captured at onboarding and do not appear in this schema. They are defined in `layer5/L5-1_living_expert_profile.md`.

**For developers:** The dossier schema defined here IS the LEP Layer A schema. They share the same field IDs, the same status flag system, and the same JSON structure. The LEP simply extends it. Build against this schema and you are building against the LEP Layer A spec.

---

*Step 2 of 22 — Expert Dossier Data Schema — v1.1 Revised*
*Next: Step 3 — Conversation Flow Architecture*
