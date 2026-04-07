# clinicIQ — Layer 1: Onboarding Agent — Step 2: Expert Dossier Data Schema
**Version 1.0 — Draft**
*Step 2 of 22 | Depends on: Step 1 (Agent Description)*

---

## Purpose

The Expert Dossier is the single most important data structure in the entire clinicIQ platform. Every agent in every layer reads from it. Every word the platform writes for an expert is calibrated against it. Every strategy it builds is grounded in it. Every output it produces is only as good as the data here.

This document defines the complete 164-field schema — 14 sections, every field named, typed, described, and mapped to the downstream agents that consume it. This is the specification the Onboarding Lead Agent (Step 1) is built to populate, the schema the Dossier Assembler sub-agent assembles into the two payload formats (Step 7), and the data contract every Layer 2, Layer 3, and Layer 4 agent reads from.

Developers building against this schema should treat it as the canonical reference. When a field is added, the schema version increments. Downstream agents always declare which schema version they read from — this prevents silent breaking changes as the platform evolves.

---

## Schema Version and Versioning Protocol

**Current version:** 1.0
**Versioning rule:** Any addition of a new field increments the minor version (1.0 → 1.1). Any removal or rename of an existing field increments the major version (1.0 → 2.0). Downstream agents declare their minimum schema version in their own configuration. The platform enforces compatibility at handoff.

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
| `agent-generated` | Agent built this value based on available context; expert has not yet seen or responded to it | No indicator — value is in use but not surfaced to expert yet |
| `pending-approval` | Agent-generated value has been surfaced to expert; awaiting thumbs up, edit, or regenerate | Yellow indicator — "Review & confirm" prompt shown |
| `pending-upload` | Field requires a file asset; conversation-derived placeholder is in use until upload arrives | Grey indicator with paperclip icon — "Upload when ready" prompt shown |

No status flag blocks downstream output generation. The platform always moves forward using the best available value, flagged appropriately.

---

## Section 1 — Identity & Practice

**Schema key:** `identity`
**Field count:** 12
**Purpose:** The foundational context for everything else in the dossier. Who the expert is, what they do, how their practice is structured, and where they operate. Every downstream agent reads this section as baseline context — it is the "who is this person" that all strategy and content is built around.
**Primary consumers:** All agents (universal context layer)

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `identity.full_name` | Full Name | String | Expert's legal or professional full name | "Dr. Sarah Mitchell, ND" | All agents |
| `identity.credential_title` | Credential Title | String | The credential or title they lead with professionally | "Naturopathic Doctor" | All agents, Website Builder, Ad Builder |
| `identity.practice_name` | Practice Name | String | The name of their practice or brand | "Mitchell Functional Health" | All agents |
| `identity.specialty_primary` | Primary Specialty | Enum | Their main clinical focus area | "Functional Medicine" | All agents, Strategy agents |
| `identity.specialty_secondary` | Secondary Specialty | Array[String] | Additional specialty areas they work within | ["Autoimmune", "Hormones"] | Brand Strategy, Content Builder |
| `identity.practice_model` | Practice Model | Enum | How they deliver care: telehealth / brick-and-mortar / hybrid / group / solo / course-creator | "Hybrid" | Growth Strategy, Funnel Builder |
| `identity.years_in_practice` | Years in Practice | Integer | Total years practicing in their specialty | 11 | Ad Builder, Sales Script (credibility signals) |
| `identity.geographic_scope` | Geographic Scope | Enum | Local / Regional / National / International | "National" | Growth Strategy, Campaign Planner |
| `identity.state_or_country` | State or Country | String | Primary operating jurisdiction — relevant for compliance | "Tennessee" | Compliance filter, all ad copy |
| `identity.team_size` | Team Size | Integer | Number of staff including the expert | 4 | Growth Strategy (scaling assessment) |
| `identity.current_monthly_revenue` | Current Monthly Revenue | Enum | Revenue bracket for internal strategy calibration | "$30K–$60K" | Growth Strategy (gap analysis) |
| `identity.website_url` | Website URL | URL | Primary practice or brand website | "https://mitchellfunctionalhealth.com" | Web Scraper, Content Audit, Brand Strategy |

---

## Section 2 — Voice DNA

**Schema key:** `voice_dna`
**Field count:** 15
**Purpose:** The fingerprint of how this expert communicates — the data structure that every Builder Layer agent reads before writing a single word. A weak Voice DNA profile produces generic outputs. A strong one produces outputs the expert reads and says "that sounds exactly like me." This section is populated passively throughout the entire onboarding session by the Voice DNA Analyst sub-agent and confirmed actively in Section 2 of the conversation flow. Full extraction methodology in Step 4.
**Primary consumers:** All Layer 3 Builder agents — every content output reads this section first

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `voice_dna.tone_primary` | Primary Tone | Enum | The dominant tonal quality of their communication: authoritative / empathetic / urgent / educational / conversational / inspirational | "Authoritative" | All Builder agents |
| `voice_dna.tone_secondary` | Secondary Tone | Enum | The secondary tonal layer that adds texture to the primary | "Empathetic" | All Builder agents |
| `voice_dna.formality_level` | Formality Level | Enum | High / Medium / Low — how formally they relate to their audience | "Medium" | All Builder agents |
| `voice_dna.sentence_rhythm` | Sentence Rhythm | Enum | Short-punchy / Long-flowing / Mixed-dynamic — their natural sentence construction pattern | "Mixed-dynamic" | All Builder agents |
| `voice_dna.vocabulary_register` | Vocabulary Register | Enum | Clinical-technical / Plain-language-translator / Street-level-casual / Mixed-professional | "Plain-language-translator" | All Builder agents |
| `voice_dna.emotional_register` | Emotional Register | String | Full description of how much feeling they bring and in what form — specific and grounded vs. measured and analytical vs. mission-driven | "High emotional — visible frustration with conventional medicine, genuine excitement about patient results, deep empathy expressed through specific stories rather than general statements" | All Builder agents |
| `voice_dna.humor_level` | Humor Level | Enum | None / Dry / Warm | "Dry" | All Builder agents |
| `voice_dna.conviction_level` | Conviction Level | Enum | High-conviction / Balanced / Tends-to-hedge — their natural ratio of declarative statements to qualified ones | "High-conviction" | All Builder agents |
| `voice_dna.authority_style` | Authority Style | Enum | Credential-first / Results-first / Story-first / Teaching-first — how they establish credibility | "Results-first" | Ad Builder, Content Builder, Webinar Builder |
| `voice_dna.signature_phrases` | Signature Phrases | Array[String] | Phrases the expert used more than once in the session — confirmed as authentically theirs | ["root cause", "nobody's asking the right questions", "the body knows how to heal"] | All Builder agents |
| `voice_dna.words_they_use` | Words They Use | Array[String] | Vocabulary preferences — words and constructions they favor | ["upstream", "driver", "healing", "restore"] | All Builder agents |
| `voice_dna.words_they_avoid` | Words They Avoid | Array[String] | Hard vocabulary avoidances — confirmed by expert | ["holistic", "wellness", "fix", "patients" (prefers "people")] | All Builder agents |
| `voice_dna.sample_extracts` | Sample Extracts | Array[String] | 3–5 verbatim quotes from the session — the highest-signal samples of their authentic voice; the calibration standard the Builder Layer uses to match their voice | ["The body already knows how to heal. Our job is to stop getting in the way.", "Nobody's asking why the immune system is attacking itself. They're just trying to quiet it down."] | All Builder agents — highest-weight field in Voice DNA |
| `voice_dna.high_passion_topics` | High-Passion Topics | Array[String] | Topics where the expert's language accelerated, sentences shortened, or expression intensified — where their authentic brand energy lives | ["Autoimmune root cause", "What conventional medicine gets wrong", "Patient transformations"] | Content Builder, Ad Builder |
| `voice_dna.voice_confidence_score` | Voice Confidence Score | Integer | Internal quality score 0–100 reflecting how rich and confirmed the Voice DNA profile is; used by Builder Layer to calibrate output confidence and flag enrichment need | 72 | All Builder agents (internal calibration) |

---

## Section 3 — Visual DNA

**Schema key:** `visual_dna`
**Field count:** 10
**Purpose:** The aesthetic identity of the expert's brand — colors, photography style, typography direction, and visual tone. Collected last in the conversation flow because it is often the least defined section and asset uploads happen asynchronously. The Voice DNA Analyst sub-agent infers Visual DNA signals throughout the session (a short-punchy, high-conviction voice almost always maps to a clean, high-contrast visual brand) so the section has agent-generated starting values from day one.
**Primary consumers:** Ad Creative Builder, Website Builder, Content Builder (visual assets and design direction)

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `visual_dna.aesthetic_keywords` | Aesthetic Keywords | Array[String] | 3–6 words describing the visual feel of the brand — or the feel they want | ["Clean", "Clinical", "High-contrast", "Trustworthy", "Modern"] | Ad Builder, Website Builder, Content Builder |
| `visual_dna.color_palette_description` | Color Palette Description | String | Description of primary and secondary brand colors — conversational or hex codes | "Deep navy and white with a warm gold accent" | Ad Builder, Website Builder |
| `visual_dna.color_palette_hex` | Color Palette (Hex) | Array[String] | Confirmed hex codes if available | ["#1A2B5F", "#FFFFFF", "#C9A84C"] | Ad Builder, Website Builder |
| `visual_dna.typography_direction` | Typography Direction | String | Description of font style direction — serif / sans-serif / modern / classic / editorial | "Clean sans-serif — modern and clinical, not ornate" | Website Builder, Content Builder |
| `visual_dna.photography_style` | Photography Style | String | Description of the photography tone the brand uses or should use | "Professional documentary — real clinical settings, no stock lifestyle imagery" | Ad Builder, Content Builder |
| `visual_dna.logo_status` | Logo Status | Enum | Exists-uploaded / Exists-not-uploaded / Does-not-exist | "Exists-not-uploaded" | Ad Builder, Website Builder |
| `visual_dna.logo_file` | Logo File | File | Uploaded logo asset | [file reference] | Ad Builder, Website Builder, Content Builder |
| `visual_dna.brand_guide_status` | Brand Guide Status | Enum | Exists-uploaded / Exists-not-uploaded / Does-not-exist | "Does-not-exist" | Brand Strategy |
| `visual_dna.brand_guide_file` | Brand Guide File | File | Uploaded brand style guide | [file reference] | All Builder agents |
| `visual_dna.expert_photo_status` | Expert Photo Status | Enum | Uploaded / Not-yet-uploaded | "Not-yet-uploaded" | Ad Builder, Website Builder, Content Builder |

---

## Section 4 — Avatar Psychology

**Schema key:** `avatar_psychology`
**Field count:** 20
**Purpose:** The psychological profile of the expert's ideal patient — the most consumed data section across the entire platform. Every ad hook, every email subject line, every webinar opener, every funnel headline starts with who this avatar is, what they feel, what they've tried, and where they are in their awareness. Full extraction methodology in Step 5.
**Primary consumers:** All Builder agents, Brand Strategy Agent, Growth Strategy Agent

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `avatar_psychology.avatar_name` | Avatar Name | String | The alliterative avatar name — makes the psychology specific and memorable across the team | "Dismissed Denise" | All agents |
| `avatar_psychology.age_range` | Age Range | String | The primary demographic age range | "42–55" | Ad Builder, Content Builder |
| `avatar_psychology.gender_skew` | Gender Skew | Enum | Female-skewed / Male-skewed / Even | "Female-skewed" | Ad Builder, Content Builder |
| `avatar_psychology.income_level` | Income Level | Enum | The household income bracket relevant for offer accessibility | "$80K–$150K household" | Growth Strategy, Offer Architecture |
| `avatar_psychology.primary_symptom` | Primary Symptom | String | The single dominant symptom or experience — the one they lead with in their own words, not the clinical name | "Can't get out of bed in the morning, brain fog that makes it impossible to think clearly at work" | Ad Builder, Webinar Builder, Email Builder |
| `avatar_psychology.symptoms_list` | Symptoms List | Array[String] | The full stack of secondary symptoms and life impacts — in the avatar's own words | ["Exhausted by 2pm", "Weight that won't move", "Mood swings", "Can't focus", "Missing my kids' activities"] | All Builder agents |
| `avatar_psychology.daily_frustrations` | Daily Frustrations | Array[String] | The specific moments and situations the symptoms create in daily life | ["Having to cancel plans with her kids", "Falling asleep at her desk", "Feeling like a failure at work"] | Ad Builder, Webinar Builder |
| `avatar_psychology.core_fear` | Core Fear | String | The deepest fear — what they're afraid this means about their future | "I'm never going to get better. This is the rest of my life." | Webinar Builder, Email Builder, Ad Builder |
| `avatar_psychology.secondary_fears` | Secondary Fears | Array[String] | The fears orbiting the core fear | ["Being dismissed by another doctor", "Wasting money on something that won't work", "Making things worse"] | Webinar Builder, Sales Script |
| `avatar_psychology.deepest_desire` | Deepest Desire | String | What they actually want — specific, not generic | "To have energy when I wake up and still have it at dinner with my family. To feel like myself again for the first time in ten years." | All Builder agents — close language |
| `avatar_psychology.transformation_identity` | Transformation Identity | String | Who they want to BECOME — the new identity, not just the improved health | "The mom who shows up fully. Who has energy for her kids and doesn't have to apologize for disappearing." | Webinar Builder, Funnel Builder, Sales Script |
| `avatar_psychology.awareness_level` | Awareness Level | Enum | 1-Unaware / 2-Problem-Aware / 3-Solution-Aware / 4-Product-Aware / 5-Most-Aware — the Eugene Schwartz awareness level that sets the entry angle for all cold traffic | "Level 2-3" | Strategy agents, all Builder agents — master entry angle variable |
| `avatar_psychology.false_belief_vehicle` | False Belief — Vehicle | String | Why the avatar doesn't believe the expert's approach will work — the vehicle doubt. Maps to Brunson's Secret #1. | "I've tried supplements and diet changes before and nothing worked. Functional medicine is probably just another expensive experiment." | Webinar Builder, Ad Builder, Strategy |
| `avatar_psychology.false_belief_internal` | False Belief — Internal | String | Why the avatar doesn't believe they personally can achieve the result. Maps to Brunson's Secret #2. | "I don't have the willpower to stick to a protocol. I've failed at health programs before. My body is probably too far gone." | Webinar Builder, Sales Script |
| `avatar_psychology.false_belief_external` | False Belief — External | String | Why external circumstances will prevent success even if they try. Maps to Brunson's Secret #3. | "I can't afford it. My family won't support major dietary changes. I work too much to be consistent." | Webinar Builder, Sales Script, Funnel Builder |
| `avatar_psychology.language_patterns` | Language Patterns | Array[String] | The exact phrases the avatar uses to describe their experience — verbatim from the expert's description of what patients say. Used directly in copy — never paraphrased. | ["I just feel off", "I'm running on empty", "My doctor says everything is normal but I know something is wrong", "I've lost myself"] | All Builder agents — never paraphrase these |
| `avatar_psychology.previous_solutions_tried` | Previous Solutions Tried | Array[Object] | Each object: {solution, promise_made, what_happened, conclusion_drawn}. The failure stack. | [{solution: "Thyroid medication", promise_made: "Will fix your numbers", what_happened: "Numbers improved but still felt terrible", conclusion_drawn: "Nothing will ever really work"}] | Webinar Builder, Ad Builder |
| `avatar_psychology.buying_triggers` | Buying Triggers | Array[String] | The specific life events or moments that tip this avatar into action | ["New diagnosis or worsening labs", "Health scare", "Milestone birthday", "Stopped being able to participate in family life"] | Strategy agents, Campaign Planner |
| `avatar_psychology.objections_primary` | Primary Objections | Array[String] | The last-mile objections that stop the sale after interest is established | ["Price — can't justify the investment right now", "Need to talk to my spouse", "Not sure this will work for me specifically"] | Sales Script, Webinar Builder, Funnel Builder |
| `avatar_psychology.secondary_avatars` | Secondary Avatars | Array[Object] | Array of secondary avatar objects — each with name, awareness_level, primary_symptom, core_fear, and key false beliefs | [{name: "Optimization Oliver", awareness_level: "1-2", primary_symptom: "Performing at 70% of potential", core_fear: "Declining as I age"}] | Content Builder (content variation briefs) |

---

## Section 5 — Problems → Root Cause → New Vehicle Map

**Schema key:** `root_cause_map`
**Field count:** 12
**Purpose:** The intellectual architecture of the expert's approach — what their patients are experiencing, what is actually causing it (the root cause conventional medicine misses), and the unique mechanism and framework the expert uses to address it. This is the "new vehicle" — the proprietary angle that creates separation from every competitor and is the centerpiece of the Perfect Webinar structure.
**Primary consumers:** Brand Strategy Agent, Webinar Builder, Ad Creative Builder, Content Builder

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `root_cause_map.surface_problems` | Surface Problems | Array[String] | The symptoms and problems the avatar presents with — what they experience, in their language | ["Fatigue", "Brain fog", "Unexplained weight gain", "Hair loss", "Cold intolerance"] | Ad Builder, Content Builder, Webinar Builder |
| `root_cause_map.conventional_diagnosis` | Conventional Diagnosis | String | What conventional medicine typically tells these patients — the official label | "Hypothyroidism — managed with Levothyroxine" | Webinar Builder, Ad Builder |
| `root_cause_map.conventional_failure_reason` | Conventional Failure Reason | String | Why conventional medicine's approach does not fully resolve the problem — the gap the expert closes | "Conventional medicine treats the thyroid in isolation. It manages TSH numbers but never asks why the immune system is attacking the thyroid gland in the first place." | Webinar Builder, Ad Builder, Content Builder |
| `root_cause_map.true_root_causes` | True Root Causes | Array[String] | The actual upstream drivers the expert identifies and addresses | ["Autoimmune trigger — leaky gut", "Chronic stress dysregulating HPA axis", "Unaddressed nutrient deficiencies (selenium, iodine, zinc)", "Environmental toxin burden"] | Brand Strategy, Webinar Builder, Content Builder |
| `root_cause_map.new_vehicle_name` | New Vehicle Name | String | The proprietary name for the expert's approach — the mechanism name. One of the highest-leverage fields in the entire dossier. | "The Thyroid Root Cause Reset" | All agents — brand anchor |
| `root_cause_map.new_vehicle_description` | New Vehicle Description | String | A plain-language description of what the new vehicle is and why it works where other approaches fail | "A 5-phase protocol that identifies and addresses the specific autoimmune triggers driving the thyroid attack — rather than managing the downstream hormone numbers. When you remove the triggers, the immune system stops attacking, the thyroid heals, and the symptoms resolve." | All agents |
| `root_cause_map.mechanism_analogy` | Mechanism Analogy | String | A simple analogy or plain-language explanation that makes the mechanism immediately understandable to a non-clinical buyer | "It's like having a fire alarm going off and unplugging the alarm instead of putting out the fire. Conventional medicine unplugs the alarm. We find the fire." | Webinar Builder, Ad Builder, Content Builder |
| `root_cause_map.new_vehicle_phases` | New Vehicle Phases | Array[String] | The named phases or steps of the expert's protocol, if it has a defined structure | ["Phase 1: Root Cause Testing", "Phase 2: Gut Healing", "Phase 3: Immune Recalibration", "Phase 4: Hormone Optimization", "Phase 5: Maintenance Protocol"] | Webinar Builder, Funnel Builder, Website Builder |
| `root_cause_map.why_vehicle_is_new` | Why Vehicle Is New | String | The specific reason this approach is genuinely different from everything the avatar has already tried — the mechanism differentiation statement | "Most functional medicine protocols address the thyroid with generalized gut and hormone support. Ours runs advanced autoimmune-specific testing first to identify the exact immune dysregulation pattern — then builds the protocol around that specific pattern. Generic protocols get generic results. This is why ours works when others haven't." | Webinar Builder, Ad Builder, Brand Strategy |
| `root_cause_map.one_big_domino_draft` | One Big Domino Draft | String | The single belief that, if installed, makes everything else obvious. The thesis of the Perfect Webinar. Often a synthesis of the new vehicle and the conventional failure reason. | "If I can show you that your thyroid symptoms are actually driven by an autoimmune process that conventional medicine never tested for — and that we can identify and address that exact process — would that change everything you've been told about what's possible for you?" | Webinar Builder (primary input) |
| `root_cause_map.claim_restrictions` | Claim Restrictions | Array[String] | Specialty-specific and jurisdiction-specific compliance flags applied to all Builder agent outputs | ["Cannot claim to 'cure' or 'reverse' autoimmune disease in paid ads", "Must include 'results not typical' on testimonials", "Cannot make FDA disease treatment claims for supplements"] | Compliance filter — all Builder agents |
| `root_cause_map.mechanism_confidence` | Mechanism Confidence | Enum | Fully-named / Partially-named / Unnamed — whether the mechanism has been clearly identified and named | "Fully-named" | Brand Strategy, Strategy Layer routing |

---

## Section 6 — Clinical Philosophy

**Schema key:** `clinical_philosophy`
**Field count:** 10
**Purpose:** The expert's belief system about healing, their methodology framework, what they reject about conventional medicine, and the professional credentials and credibility anchors they carry. This section provides the intellectual and ethical backbone that makes the brand feel substantive — not just persuasive.
**Primary consumers:** Brand Strategy Agent, Content Builder, Webinar Builder

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `clinical_philosophy.core_belief` | Core Belief | String | The single most fundamental thing they believe about healing that most doctors get wrong | "The body has an innate capacity to heal when you remove what is blocking it and provide what it needs. Most medicine is focused on suppressing symptoms, not creating conditions for healing." | Brand Strategy, Content Builder, Webinar Builder |
| `clinical_philosophy.methodology_name` | Methodology Name | String | What they call their clinical methodology, if it has a name | "Root Cause Functional Medicine" | All agents |
| `clinical_philosophy.what_they_reject` | What They Reject | Array[String] | The specific conventional medicine practices, frameworks, or assumptions they fundamentally disagree with | ["Symptom-only treatment", "Lab ranges built on sick populations", "Polypharmacy as a first resort", "The idea that chronic disease is inevitable"] | Content Builder, Webinar Builder, Brand Strategy |
| `clinical_philosophy.what_they_champion` | What They Champion | Array[String] | The practices, frameworks, and principles they actively advocate for | ["Root cause testing", "Personalized protocols", "The gut-immune connection", "Patient education and empowerment"] | Content Builder, Webinar Builder |
| `clinical_philosophy.credentials` | Credentials | Array[String] | All relevant credentials, certifications, and training programs | ["ND", "IFMCP", "Institute for Functional Medicine Certified Practitioner"] | Ad Builder, Website Builder, Sales Script |
| `clinical_philosophy.credibility_anchors` | Credibility Anchors | Array[String] | Non-credential credibility signals — media, publications, speaking, notable associations | ["Featured in Healthline", "500+ patients treated", "Trained under Dr. Mark Hyman", "11 years clinical experience"] | Ad Builder, Website Builder, Webinar Builder |
| `clinical_philosophy.years_treating_condition` | Years Treating Primary Condition | Integer | Years specifically treating the avatar's primary condition — more specific than general years in practice | 9 | Ad Builder, Sales Script |
| `clinical_philosophy.notable_results_summary` | Notable Results Summary | String | A summary statement of the most compelling collective results across the patient population | "Over 500 patients restored thyroid function without lifelong medication dependence. Average patient reduces or eliminates thyroid medication within 90 days." | Ad Builder, Webinar Builder, Website Builder |
| `clinical_philosophy.intellectual_influences` | Intellectual Influences | Array[String] | The practitioners, researchers, or authors who most shaped their clinical thinking | ["Dr. Alessio Fasano (leaky gut research)", "Dr. Tom O'Bryan (autoimmune)", "Dr. Izabella Wentz (Hashimoto's)"] | Brand Strategy (positioning context) |
| `clinical_philosophy.patient_relationship_style` | Patient Relationship Style | String | How they describe the ideal practitioner-patient relationship and their role in the healing process | "I am a guide, not a prescriber. My job is to educate, test, and build a protocol — and then support the patient in executing it. The healing is theirs." | Content Builder, Website Builder |

---

## Section 7 — Offer Architecture

**Schema key:** `offer_architecture`
**Field count:** 21
**Purpose:** The complete commercial offer stack — all four tiers, the mechanism and offer names, the value stack, the guarantee, urgency and scarcity levers, and pricing history. This section is the revenue engine specification. Every funnel, every webinar close, every sales script, every email sequence is built around the data here. Full extraction methodology in Step 6.
**Primary consumers:** Growth Strategy Agent, Funnel Builder, Sales Script Builder, Email Builder, Webinar Builder

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `offer_architecture.core_transformation` | Core Transformation | String | The specific, vivid outcome the core offer delivers — the dream result in the most concrete language possible | "Off thyroid medication, sustained energy from morning through evening, normal weight, clear thinking — in 90 days" | All agents — appears in virtually every output |
| `offer_architecture.high_ticket_name` | High-Ticket Offer Name | String | The name of the core Tier 2 offer | "The 90-Day Thyroid Restoration Program" | All Builder agents |
| `offer_architecture.high_ticket_price` | High-Ticket Price | Integer | The investment amount for the core Tier 2 offer in USD | 7500 | Webinar Builder, Funnel Builder, Sales Script |
| `offer_architecture.fulfillment_model` | Fulfillment Model | Enum | 1:1-with-expert / Hybrid-coach-led / Group / Self-paced / Hybrid-self-paced-with-coaching | "Hybrid-coach-led" | Growth Strategy, Sales Script, Website Builder |
| `offer_architecture.program_duration` | Program Duration | String | How long the core program runs | "90 days" | All Builder agents |
| `offer_architecture.value_stack` | Value Stack | Array[Object] | Each object: {element_name, description, assigned_value}. The full itemized value stack for the core offer. | [{element_name: "Personal Coach Access", description: "Dedicated coach, monthly Zoom, daily text support", assigned_value: 6000}] | Webinar Builder, Funnel Builder |
| `offer_architecture.value_stack_total` | Value Stack Total | Integer | Sum of all assigned values in the value stack — should be 10x the price | 74500 | Webinar Builder, Funnel Builder |
| `offer_architecture.mechanism_name` | Mechanism Name | String | The proprietary name for the expert's method — the brand anchor. Should match root_cause_map.new_vehicle_name. | "The Thyroid Root Cause Reset" | All agents |
| `offer_architecture.guarantee_concept` | Guarantee Concept | String | The risk reversal statement — what the expert promises and what happens if the result is not achieved | "90-Day Results Guarantee — achieve the defined outcome markers or we continue working with you at no additional cost until you do" | Webinar Builder, Funnel Builder, Sales Script |
| `offer_architecture.guarantee_type` | Guarantee Type | Enum | Results / Effort / Assessment / Satisfaction | "Results" | Webinar Builder, Funnel Builder |
| `offer_architecture.bonus_ideas` | Bonus Concepts | Array[Object] | Each object: {name, description, false_belief_addressed, assigned_value}. Bonus concepts that address specific false beliefs and implementation obstacles. | [{name: "The Quick-Start Lab Guide", description: "Which tests to order and what to say to your doctor", false_belief_addressed: "vehicle", assigned_value: 497}] | Webinar Builder, Funnel Builder, Email Builder |
| `offer_architecture.urgency_scarcity_levers` | Urgency & Scarcity Levers | Array[String] | Real urgency and scarcity elements — cohort enrollment dates, coaching capacity limits, price increases, health cost-of-inaction framing | ["New cohort starts first Monday of each month — 12 spots per cohort", "Each coach carries maximum 70 clients", "Cost of inaction: every 90 days without addressing root cause extends recovery timeline"] | Webinar Builder, Email Builder, Campaign Planner |
| `offer_architecture.lead_magnet_concept` | Lead Magnet Concept | String | The Tier 1 attraction offer — free or low-cost entry that generates the lead | "Paid Thyroid Root Cause Assessment ($67) — 45-minute diagnostic that identifies specific autoimmune drivers and shows the path forward" | Funnel Builder, Content Builder |
| `offer_architecture.lead_magnet_price` | Lead Magnet Price | Integer | Price of the Tier 1 offer — 0 if free | 67 | Funnel Builder, Ad Builder |
| `offer_architecture.downsell_name` | Downsell Name | String | The Tier 3 offer name — accessible entry for buyers who can't commit to the core offer | "The Thyroid Reset: Self-Paced Program" | Webinar Builder, Funnel Builder |
| `offer_architecture.downsell_price` | Downsell Price | Integer | Price of the Tier 3 downsell offer | 997 | Webinar Builder, Funnel Builder |
| `offer_architecture.continuity_name` | Continuity Name | String | The Tier 4 recurring offer name | "The Thyroid Maintenance Membership" | Email Builder, Sales Script |
| `offer_architecture.continuity_price_monthly` | Continuity Monthly Price | Integer | Monthly price of the Tier 4 continuity offer | 197 | Email Builder, Sales Script |
| `offer_architecture.payment_plan_structure` | Payment Plan Structure | String | How the core offer payment plan is structured | "3 payments of $2,750 — or single pay $7,500" | Sales Script, Funnel Builder |
| `offer_architecture.price_point_history` | Price Point History | Enum | Sold-successfully-at-this-level / Sold-unsuccessfully / New-price-untested | "Sold-successfully-at-this-level" | Growth Strategy (launch approach) |
| `offer_architecture.offer_gap_flags` | Offer Gap Flags | Array[String] | Silent Diagnosis flags from the Offer Architecture Builder sub-agent — missing tiers, underpricing, no guarantee, not-scalable model | ["Tier 4 continuity not yet built — MRR gap flagged for Growth Strategy"] | Growth Strategy Agent (priority brief) |

---

## Section 8 — Perfect Webinar Raw Material

**Schema key:** `webinar_raw_material`
**Field count:** 15
**Purpose:** The raw persuasion architecture that the Webinar Builder Agent assembles into a full Perfect Webinar script. Every field here maps directly to a component of the Brunson Perfect Webinar framework. This section is populated by synthesizing data from the avatar psychology, root cause map, clinical philosophy, and offer architecture sections — plus the expert's own answers to the webinar-specific anchor question.
**Primary consumers:** Webinar Builder Agent (primary), Ad Creative Builder

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `webinar_raw_material.one_big_domino` | One Big Domino | String | The single belief that, if the audience accepts it, makes the offer obvious and the objections dissolve. The thesis of the entire webinar. | "If your thyroid symptoms are being driven by an autoimmune process that nobody has ever tested for — and we can identify and address that exact process — then everything your doctor told you about what's possible for your thyroid is wrong." | Webinar Builder (primary), Ad Builder (hook source) |
| `webinar_raw_material.secret_1` | Secret 1 — Vehicle Belief Shift | String | The content block that dismantles the avatar's false belief about the vehicle (why the expert's approach won't work) and replaces it with belief. Maps to `avatar_psychology.false_belief_vehicle`. | "Why the standard thyroid protocol always fails — and the one test that changes everything" | Webinar Builder |
| `webinar_raw_material.secret_2` | Secret 2 — Internal Belief Shift | String | The content block that dismantles the avatar's false belief about their own capacity and replaces it with belief in themselves. Maps to `avatar_psychology.false_belief_internal`. | "Why it's not your willpower — and why people who 'can never stick to anything' get the fastest results with this approach" | Webinar Builder |
| `webinar_raw_material.secret_3` | Secret 3 — External Belief Shift | String | The content block that dismantles the avatar's false belief about external circumstances and replaces it with a path forward. Maps to `avatar_psychology.false_belief_external`. | "How to do this with a full schedule, a family, and a budget — the three things that stopped you before aren't what you think they are" | Webinar Builder |
| `webinar_raw_material.origin_story_before` | Origin Story — Before State | String | The before state of the expert's own story — or the patient story used as the Epiphany Bridge. Who they were, what they experienced, how they felt before the discovery. | "At 34, I had been told my labs were normal for three years. I was sleeping 10 hours and waking up exhausted. Gaining weight on 1,200 calories. Brain fog so bad I couldn't finish sentences." | Webinar Builder |
| `webinar_raw_material.origin_story_discovery` | Origin Story — Discovery | String | The turning point — what changed, what was found, what was the moment of insight that led to the new vehicle | "When I ran my own advanced autoimmune panel — the test my endocrinologist said I didn't need — I had the highest anti-TPO antibodies my colleague had ever seen. My immune system had been attacking my thyroid for years. Nobody had ever looked." | Webinar Builder |
| `webinar_raw_material.origin_story_after` | Origin Story — After State | String | The result — who they became on the other side of the discovery and the protocol | "Within 60 days of addressing the autoimmune drivers, my antibodies dropped by 70%. I was off Levothyroxine in 8 months. That was 7 years ago. I have been medication-free since." | Webinar Builder |
| `webinar_raw_material.hook_concepts` | Hook Concepts | Array[String] | 3–5 webinar title and hook concepts generated from the One Big Domino and avatar psychology | ["The Hidden Autoimmune Driver Behind Your Thyroid Symptoms (And Why Your Doctor Has Never Tested for It)", "Why Your Thyroid Medication Is Working — and Why You Still Feel Terrible"] | Ad Builder, Email Builder, Webinar Builder |
| `webinar_raw_material.mechanism_demonstration` | Mechanism Demonstration | String | How the mechanism is demonstrated during the webinar — the teaching moment that makes the audience believe it works before the offer is revealed | "Live walkthrough of the autoimmune testing panel — what it shows, what it means, and a real before/after case study showing antibody reduction and symptom resolution" | Webinar Builder |
| `webinar_raw_material.case_study_primary` | Primary Case Study | Object | {avatar_type, before_state, what_was_tried, turning_point, result, timeline, quote} — the main proof story used in the webinar. Should match the avatar as closely as possible. | {avatar_type: "42-year-old woman, Hashimoto's, 5-year history", result: "Off medication in 8 months, 22 lbs lost, full energy restored", timeline: "First results in 3 weeks"} | Webinar Builder (primary proof), Ad Builder |
| `webinar_raw_material.stack_close_structure` | Stack Close Structure | String | Description of how the offer reveal is sequenced — what gets introduced when, in what order | "Core program → coach access → community → Bonus 1 (quick-start testing guide) → Bonus 2 (family meal protocol) → Bonus 3 (travel and consistency toolkit) → Guarantee reveal → Price reveal" | Webinar Builder |
| `webinar_raw_material.faq_objections` | FAQ Objections | Array[Object] | Each object: {objection, answer}. The most common Q&A objections and the pre-scripted answers. Sourced from `avatar_psychology.objections_primary`. | [{objection: "Is this covered by insurance?", answer: "This program is not insurance-covered — here is why that is actually to your advantage..."}] | Webinar Builder, Sales Script |
| `webinar_raw_material.webinar_cta_language` | CTA Language | String | The specific language used for the call to action in the webinar close | "Click the button below to claim your spot in this month's cohort. You'll be taken to a short application — we want to make sure this is the right fit for you before we begin." | Webinar Builder, Funnel Builder |
| `webinar_raw_material.false_urgency_avoidance` | Real Urgency Notes | String | Notes on genuine urgency and scarcity to use — ensures the webinar never uses manufactured urgency | "12 spots per cohort — real. Coach capacity limit — real. Price increasing after beta phase — real. Use these only." | Webinar Builder |
| `webinar_raw_material.webinar_length_target` | Target Length | Enum | 45-min / 60-min / 75-min / 90-min | "60-min" | Webinar Builder |

---

## Section 9 — Proof Bank

**Schema key:** `proof_bank`
**Field count:** 11
**Purpose:** The social proof library — patient transformation stories, testimonials, before/after data, and collective outcome statistics. Every close sequence, every ad, every email nurture sequence, every webinar proof stack draws from here. The depth of the Proof Bank is one of the most important quality signals for the platform's conversion potential.
**Primary consumers:** Ad Creative Builder, Email Builder, Webinar Builder, Sales Script Builder

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `proof_bank.transformation_stories` | Transformation Stories | Array[Object] | Each object: {story_id, avatar_match, before_state, treatments_tried, turning_point, result, timeline, direct_quote, media_available}. Full structured case study library. | [{avatar_match: "Dismissed Denise", result: "Off medication, 18 lbs lost, full energy returned", timeline: "First result in 2 weeks, full result in 10 weeks", direct_quote: "I finally feel like the person my family deserves."}] | Webinar Builder, Ad Builder, Email Builder |
| `proof_bank.most_dramatic_transformation` | Most Dramatic Transformation | Object | The single most dramatic before/after story — identified for priority use in webinar proof stack and high-conversion ads | {result: "Off 20-year thyroid medication in 6 months", timeline: "Felt first change in week 3"} | Webinar Builder (primary), Ad Builder |
| `proof_bank.fastest_result` | Fastest Result Story | Object | The story with the shortest time-to-result — maximizes the Hormozi time-delay score in the value equation | {result: "Energy restored and brain fog gone", timeline: "First noticeable change in 9 days"} | Webinar Builder, Ad Builder |
| `proof_bank.skeptic_to_believer` | Skeptic-to-Believer Story | Object | The story of someone who was most skeptical and still got results — most powerful for Level 3 aware audiences | {background: "Had tried 4 other functional medicine practitioners. Said she would never try again.", result: "Complete symptom resolution in 12 weeks"} | Webinar Builder, Ad Builder |
| `proof_bank.collective_results_stats` | Collective Results Stats | Object | Aggregate outcome data across the patient population: {patients_treated, avg_time_to_first_result, medication_reduction_rate, completion_rate} | {patients_treated: 500, avg_time_to_first_result: "2-3 weeks", medication_reduction_rate: "73% reduce or eliminate within 6 months"} | Webinar Builder, Website Builder, Ad Builder |
| `proof_bank.testimonials_text` | Text Testimonials | Array[Object] | Each object: {name_or_initials, credential_or_context, testimonial_text, result_highlighted}. Written testimonials with permissions confirmed. | [{name_or_initials: "Jennifer M.", credential_or_context: "43, Hashimoto's, 7-year history", testimonial_text: "I was told I'd be on medication forever. I am off it."}] | Website Builder, Ad Builder, Email Builder |
| `proof_bank.video_testimonials` | Video Testimonials | Array[File] | Uploaded video testimonial files | [file references] | Ad Builder, Website Builder |
| `proof_bank.media_mentions` | Media Mentions | Array[Object] | Each object: {outlet, type, url, excerpt}. Third-party media coverage, podcast appearances, features. | [{outlet: "Healthline", type: "Feature article", excerpt: "Dr. Mitchell's approach challenges the standard thyroid protocol..."}] | Website Builder, Ad Builder (credibility) |
| `proof_bank.proof_bank_depth_score` | Proof Bank Depth Score | Integer | Internal quality score 0–100 reflecting the richness of the proof bank — number of stories, quality of stories, variety of avatar types. Used by Builder Layer to assess conversion readiness. | 45 | Strategy agents (conversion readiness assessment) |
| `proof_bank.missing_proof_flags` | Missing Proof Flags | Array[String] | Gaps in proof bank coverage identified by Silent Diagnostician — flagged for remediation in first 30 days | ["No skeptic-to-believer story captured yet", "No video testimonials uploaded"] | Growth Strategy (30-day proof plan) |
| `proof_bank.before_after_data` | Before/After Data Points | Array[Object] | Each object: {metric, before_value, after_value, timeframe}. Quantitative before/after data. | [{metric: "Anti-TPO antibodies", before_value: "1,200 IU/mL", after_value: "180 IU/mL", timeframe: "90 days"}] | Webinar Builder, Ad Builder |

---

## Section 10 — Competitive Landscape

**Schema key:** `competitive_landscape`
**Field count:** 8
**Purpose:** What the avatar has tried before finding this expert — from their perspective, not the expert's. The failed solutions, why each failed, and what makes this expert's approach genuinely different. This section is the raw material for vehicle doubt setup in the webinar and for differentiation messaging across all platforms.
**Primary consumers:** Brand Strategy Agent, Ad Creative Builder, Webinar Builder

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `competitive_landscape.alternatives_tried` | Alternatives Tried | Array[Object] | Each object: {alternative, promise_made, why_it_failed, avatar_conclusion}. The full sequence of what the avatar tried before this expert. | [{alternative: "Standard endocrinologist", promise_made: "Medication will normalize your levels", why_it_failed: "Numbers normalized but symptoms continued", avatar_conclusion: "Even when the labs look right, I still feel terrible"}] | Webinar Builder, Ad Builder |
| `competitive_landscape.direct_competitors` | Direct Competitors | Array[String] | Named practitioners, programs, or platforms competing directly for the same avatar | ["Dr. Izabella Wentz Hashimoto's Protocol", "Paloma Health"] | Brand Strategy (differentiation) |
| `competitive_landscape.competitor_differentiation` | Competitor Differentiation | String | What specifically makes this expert's approach different from the named competitors — concrete and demonstrable | "Paloma Health tests TSH only and provides medication management. We run 14 autoimmune markers, identify the specific triggers, and address root cause through protocol — not medication management." | Brand Strategy, Ad Builder |
| `competitive_landscape.category_villain` | Category Villain | String | The conventional approach or belief system that is framed as the villain in the expert's narrative — what the avatar has been told that has kept them sick | "The conventional medicine belief that thyroid disease is a hormone problem, not an autoimmune problem — and that the answer is replacing the hormone rather than addressing why the immune attack is happening" | Webinar Builder, Ad Builder, Content Builder |
| `competitive_landscape.why_others_fail_summary` | Why Others Fail Summary | String | The one-paragraph summary of why every alternative the avatar has tried has failed — the setup for the new vehicle reveal | "Every approach the avatar has tried — conventional medication, generic supplements, general diet changes — has failed for the same reason: none of them identified or addressed the autoimmune trigger. They managed downstream symptoms while the root cause continued unchecked." | Webinar Builder, Brand Strategy |
| `competitive_landscape.market_awareness_context` | Market Awareness Context | String | What the market currently believes about the expert's specialty — the water the avatar is swimming in | "Most avatars have heard of 'functional medicine' but have mixed or negative associations from expensive, unproductive experiences with generalist practitioners. The term needs to be reframed as 'autoimmune-specific root cause medicine' for this audience." | Brand Strategy, Ad Builder |
| `competitive_landscape.price_comparison_context` | Price Comparison Context | String | How the expert's price compares to what the avatar has already spent — often reveals that the investment is economical relative to years of failed alternatives | "Average avatar has spent $8,000–$15,000 on conventional care, medication, and failed alternatives over 5 years. The $7,500 program represents less than one year of what they've already been spending — and it actually addresses the cause." | Webinar Builder, Sales Script |
| `competitive_landscape.trust_barriers` | Trust Barriers | Array[String] | The specific reasons the avatar is skeptical of this category of solution — beyond the individual false beliefs | ["Has been burned by previous functional medicine practitioners", "Cannot tell the difference between qualified and unqualified practitioners in this space", "Worried it's just expensive supplements"] | Webinar Builder, Brand Strategy |

---

## Section 11 — Content Audit & Existing Assets

**Schema key:** `content_audit`
**Field count:** 13
**Purpose:** An inventory of everything the expert already has in the world — digital footprint, content library, email list, existing funnels, and performance data. This section prevents the Builder Layer from building things that already exist and allows the Growth Strategy Agent to build on what is already working.
**Primary consumers:** Growth Strategy Agent, Content Builder

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `content_audit.website_status` | Website Status | Enum | Live-optimized / Live-needs-work / Under-construction / Does-not-exist | "Live-needs-work" | Growth Strategy, Website Builder |
| `content_audit.social_platforms_active` | Active Social Platforms | Array[String] | Platforms with meaningful active presence | ["Instagram", "Facebook", "YouTube"] | Content Builder, Growth Strategy |
| `content_audit.instagram_handle` | Instagram Handle | String | Instagram username | "@mitchellfunctionalhealth" | Content Builder |
| `content_audit.instagram_follower_count` | Instagram Followers | Integer | Current follower count | 4200 | Growth Strategy (audience temperature) |
| `content_audit.facebook_page_name` | Facebook Page Name | String | Facebook business page name | "Mitchell Functional Health" | Content Builder |
| `content_audit.facebook_follower_count` | Facebook Followers | Integer | Current page follower count | 2800 | Growth Strategy |
| `content_audit.youtube_channel_url` | YouTube Channel URL | URL | YouTube channel URL if active | "https://youtube.com/@mitchellfh" | Content Builder, Growth Strategy |
| `content_audit.podcast_name` | Podcast Name | String | Podcast name if exists | "Root Cause Health Podcast" | Content Builder, Brand Strategy |
| `content_audit.email_list_size` | Email List Size | Integer | Current email list subscriber count | 1850 | Growth Strategy (warm audience size) |
| `content_audit.email_platform` | Email Platform | String | Email service provider used | "ActiveCampaign" | Growth Strategy, Email Builder |
| `content_audit.best_performing_content` | Best Performing Content | Array[String] | URLs or titles of their highest-performing organic content pieces — by engagement, shares, or comments | ["The 5 thyroid tests your doctor isn't running — 47K views", "Why your medication is working but you still feel terrible — most shared post"] | Content Builder, Ad Builder (proven hooks) |
| `content_audit.existing_lead_magnets` | Existing Lead Magnets | Array[Object] | Each object: {name, url, lead_count, active}. Current opt-in offers. | [{name: "5 Thyroid Tests PDF", url: "...", lead_count: 340, active: true}] | Growth Strategy, Funnel Builder |
| `content_audit.existing_funnels` | Existing Funnels | Array[Object] | Each object: {name, type, platform, status, conversion_rate}. Active or dormant funnels. | [{name: "Webinar funnel", type: "Webinar opt-in", platform: "ClickFunnels", status: "Dormant", conversion_rate: null}] | Growth Strategy, Funnel Builder |

---

## Section 12 — Dream Practice Vision & Traffic Reality

**Schema key:** `dream_vision_traffic`
**Field count:** 14
**Purpose:** The north star the expert is building toward and the current reality they are starting from. The gap between these two data sets is the Growth Strategy Agent's primary operating brief — every strategic recommendation exists to close this gap.
**Primary consumers:** Growth Strategy Agent (primary)

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `dream_vision_traffic.revenue_goal_12mo` | 12-Month Revenue Goal | Integer | Target revenue in the next 12 months in USD | 2000000 | Growth Strategy |
| `dream_vision_traffic.revenue_goal_3yr` | 3-Year Revenue Goal | Integer | 3-year vision revenue target | 10000000 | Growth Strategy |
| `dream_vision_traffic.patient_volume_target` | Patient Volume Target | Integer | Target number of active clients at full operation | 200 | Growth Strategy (capacity planning) |
| `dream_vision_traffic.lifestyle_vision` | Lifestyle Vision | String | What the expert's ideal working life looks like — hours, travel, team, involvement level | "Working 3 days per week in a strategic and educational role, team fully handling delivery, speaking 6 times per year, able to take real vacations" | Growth Strategy |
| `dream_vision_traffic.impact_vision` | Impact Vision | String | The scope of impact they want to have — beyond revenue | "Prove to the world that autoimmune thyroid disease is reversible — change the standard of care" | Brand Strategy, Content Builder |
| `dream_vision_traffic.exit_or_build` | Exit or Build | Enum | Building-to-sell / Building-to-hold / Not-sure | "Building-to-hold" | Growth Strategy (long-term structure) |
| `dream_vision_traffic.current_lead_sources` | Current Lead Sources | Array[String] | Where new patients are currently coming from | ["Referrals from existing patients", "Organic Instagram", "Google search"] | Growth Strategy (traffic audit) |
| `dream_vision_traffic.paid_traffic_history` | Paid Traffic History | Enum | Currently-running / Has-run-in-past / Never-run | "Never-run" | Growth Strategy (ad readiness assessment) |
| `dream_vision_traffic.audience_temperature` | Audience Temperature | Enum | Cold-only / Warm-only / Mixed-cold-and-warm / Primarily-warm | "Primarily-warm" | Growth Strategy, Campaign Planner |
| `dream_vision_traffic.monthly_new_leads` | Monthly New Leads | Integer | Approximate current monthly lead volume across all sources | 45 | Growth Strategy (gap analysis) |
| `dream_vision_traffic.current_conversion_rate` | Current Conversion Rate | String | Approximate conversion rate from lead to paid client | "Roughly 1 in 5 who have a consultation" | Growth Strategy |
| `dream_vision_traffic.biggest_growth_obstacle` | Biggest Growth Obstacle | String | What the expert believes is the single biggest thing standing between them and growth | "I don't have a consistent way to bring in new leads outside of referrals. Everything depends on me and word of mouth." | Growth Strategy (primary brief input) |
| `dream_vision_traffic.tech_stack` | Tech Stack | Array[String] | CRM, funnel, email, booking, and payment tools currently in use | ["GoHighLevel", "ClickFunnels", "Stripe", "Acuity"] | Growth Strategy, Funnel Builder |
| `dream_vision_traffic.team_growth_readiness` | Team Growth Readiness | Enum | Ready-to-hire / Considering / Not-yet-ready | "Considering" | Growth Strategy (scaling plan) |

---

## Section 13 — Business Context & Growth Intelligence

**Schema key:** `business_context`
**Field count:** 11
**Purpose:** Operational details that shape strategy — business structure, compliance context, growth history, and the expert's personal capacity and constraints. The Growth Strategy Agent reads this section to ensure every recommendation is executable given the expert's actual situation.
**Primary consumers:** Growth Strategy Agent, Email Builder, Compliance layer

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `business_context.business_entity_type` | Business Entity Type | String | LLC, PLLC, S-Corp, sole proprietor, etc. | "PLLC" | Growth Strategy (structure context) |
| `business_context.licensing_states` | Licensing States | Array[String] | States where the expert is licensed to practice | ["Tennessee", "Texas", "Florida"] | Compliance filter, Growth Strategy |
| `business_context.compliance_context` | Compliance Context | String | Summary of the key compliance constraints for this expert's specialty and jurisdiction | "ND in Tennessee — cannot make disease treatment claims in advertising. FTC testimonial guidelines apply to all patient outcome claims. Cannot claim to cure or reverse named conditions in paid media." | Compliance filter — all Builder agents |
| `business_context.growth_history` | Growth History | String | A brief narrative of how the practice has grown to its current state | "Started as a solo ND in 2015. Added telehealth in 2020. Grew from $8K/month to $45K/month primarily through referrals and one webinar run in 2022." | Growth Strategy |
| `business_context.previous_marketing_attempts` | Previous Marketing Attempts | Array[Object] | Each object: {type, outcome, what_was_learned}. What they've tried in marketing before and what happened. | [{type: "Facebook ads", outcome: "Spent $3K, no conversions", what_was_learned: "Offer wasn't clear. Sent to homepage, no funnel."}] | Growth Strategy |
| `business_context.preferred_growth_channel` | Preferred Growth Channel | String | The traffic and growth channel the expert is most energized by or most comfortable with | "Long-form YouTube content — I like teaching and it builds real trust" | Growth Strategy, Content Builder |
| `business_context.founder_capacity_hours` | Founder Weekly Capacity | Integer | Hours per week the expert can realistically invest in growth activities (content, strategy, review) | 8 | Growth Strategy (realistic plan calibration) |
| `business_context.delivery_capacity_current` | Current Delivery Capacity | Integer | How many more clients the expert could take on right now without additional team | 15 | Growth Strategy (demand generation targeting) |
| `business_context.insurance_model` | Insurance Model | Enum | Insurance-only / Cash-pay-only / Hybrid / Not-applicable | "Cash-pay-only" | Growth Strategy, Offer Architecture |
| `business_context.referral_sources` | Referral Sources | Array[String] | Who refers patients to this expert — other practitioners, patients, platforms | ["Former patients", "Local OBGYNs who don't treat thyroid autoimmune", "Naturopathic college alumni network"] | Growth Strategy |
| `business_context.seasonality_patterns` | Seasonality Patterns | String | Known peaks and valleys in demand through the year | "January is highest demand — New Year resolution buyers. August slowdown. November-December uptick around health goals before year end." | Campaign Planner, Growth Strategy |

---

## Section 14 — Expert Personal Story

**Schema key:** `expert_personal_story`
**Field count:** 7
**Purpose:** The expert's own health journey or mission origin story — often the most emotionally powerful brand content they have, and the most underused. A personal story creates trust faster than any credential. This section populates the Epiphany Bridge of the Perfect Webinar and is the source material for the expert's personal brand narrative across all platforms. Extracted by the Story Miner sub-agent and confirmed during the Expert Personal Story section of the conversation flow.
**Primary consumers:** Content Builder, Ad Creative Builder, Webinar Builder

| Field ID | Field Name | Type | Description | Example | Consuming Agents |
|----------|-----------|------|-------------|---------|-----------------|
| `expert_personal_story.story_personal_story_summary` | Personal Story Summary | String | A narrative summary of the expert's personal health journey or mission origin story — 2–4 sentences capturing the full arc | "Dr. Mitchell spent 3 years being told her thyroid labs were 'normal' while her life was shrinking from exhaustion and brain fog. After running her own advanced autoimmune panel, she discovered antibodies that had gone undetected — and built the protocol that healed her. She has spent the 9 years since doing for others what nobody did for her." | All Builder agents — brand narrative anchor |
| `expert_personal_story.story_what_they_almost_gave_up_on` | What They Almost Gave Up On | String | The darkest moment — what they were on the verge of accepting or surrendering — the emotional low point of the story | "I was two weeks from accepting that this was just what my life was going to be. I had stopped fighting with doctors and started researching disability accommodation." | Webinar Builder (Epiphany Bridge), Content Builder |
| `expert_personal_story.story_what_changed_everything` | What Changed Everything | String | The discovery — the insight, test, mentor, book, or moment that turned everything around and led to the creation of the new vehicle | "I found a paper on anti-TPO antibodies and autoimmune thyroiditis that described my exact symptom picture in patients with 'normal' TSH. I ordered the test myself. The results were the beginning of everything." | Webinar Builder (Epiphany Bridge), Content Builder |
| `expert_personal_story.story_before_state` | Before State | String | Detailed description of who they were and what life looked like before the discovery — physical, emotional, professional | "Sleeping 10 hours, waking up like I hadn't slept at all. Missing half my working hours to exhaustion. Watching my kids' activities from the couch because I couldn't stand up. Feeling like a fraud in my own practice because I couldn't fix myself." | Webinar Builder, Ad Builder, Content Builder |
| `expert_personal_story.story_after_state` | After State | String | Detailed description of who they became and what life looks like now — the transformation result | "Running a full clinical practice and seeing 500+ patients through the same protocol that healed me. Off all medication. Energy to run 5Ks with my daughter. Present in a way I hadn't been in years." | Webinar Builder, Content Builder, Website Builder |
| `expert_personal_story.story_mission_statement` | Mission Statement | String | What they want for others because of what they went through — the purpose statement that drives the work | "Nobody should spend years being told they're fine when they're not. I built this practice and this protocol so that what happened to me never happens to anyone who finds us." | Brand Strategy, Website Builder, Content Builder |
| `expert_personal_story.story_has_personal_health_journey` | Has Personal Health Journey | Boolean | Whether the expert has a personal health journey that is usable as brand content | true | Content Builder, Webinar Builder (routing flag) |

---

## Downstream Agent Consumption Map

The following table maps every dossier section to the agents and layers that consume it — providing a complete picture of how data flows from the Onboarding Agent through the entire platform.

| Dossier Section | Schema Key | Primary Consumers | How It's Used |
|----------------|-----------|-------------------|---------------|
| Identity & Practice | `identity` | All agents | Universal context — who this person is; appears in every agent's initialization context |
| Voice DNA | `voice_dna` | All Layer 3 Builder agents | Every word the Builder Layer writes is calibrated against this section first |
| Visual DNA | `visual_dna` | Ad Creative Builder, Website Builder, Content Builder | Visual direction for all designed assets; file assets applied when uploaded |
| Avatar Psychology | `avatar_psychology` | All Builder agents, Brand Strategy, Growth Strategy | Hook selection, entry angle, false belief architecture, close language |
| Root Cause Map | `root_cause_map` | Brand Strategy, Webinar Builder, Ad Creative Builder, Content Builder | Mechanism narrative, new vehicle reveal, differentiation messaging |
| Clinical Philosophy | `clinical_philosophy` | Brand Strategy, Content Builder, Webinar Builder | Brand credibility layer, content educational angle, webinar authority establishment |
| Offer Architecture | `offer_architecture` | Growth Strategy, Funnel Builder, Sales Script Builder, Email Builder, Webinar Builder | Stack construction, price reveal, guarantee, bonus sequence, close architecture |
| Perfect Webinar Raw Material | `webinar_raw_material` | Webinar Builder Agent (primary), Ad Creative Builder | Direct input to webinar script; hook concepts feed ad creation |
| Proof Bank | `proof_bank` | Ad Creative Builder, Email Builder, Webinar Builder, Sales Script Builder | Case studies for proof stack, testimonials for credibility, stats for collective authority |
| Competitive Landscape | `competitive_landscape` | Brand Strategy, Ad Creative Builder, Webinar Builder | Vehicle doubt setup, differentiation messaging, villain framing |
| Content Audit | `content_audit` | Growth Strategy, Content Builder | Build on what works; avoid rebuilding what exists; warm audience sizing |
| Dream Vision & Traffic Reality | `dream_vision_traffic` | Growth Strategy Agent (primary) | Gap analysis; 90-day plan construction; channel selection |
| Business Context | `business_context` | Growth Strategy, Email Builder, Compliance layer | Realistic plan calibration; compliance filter initialization; capacity planning |
| Expert Personal Story | `expert_personal_story` | Content Builder, Ad Creative Builder, Webinar Builder | Epiphany Bridge for webinar; personal brand content; trust-building ads |

---

## Dossier Completion Score — Field Contribution

The Dossier Completion Score (0–100) is calculated from five components, each drawing on specific fields across this schema:

| Component | Weight | Fields Contributing |
|-----------|--------|---------------------|
| Field population rate | 35% | % of all 164 fields with any value (confirmed, agent-generated, or pending-approval) |
| Confirmation rate | 20% | % of populated fields where status = `confirmed` vs. `agent-generated` |
| Story richness | 15% | `proof_bank.transformation_stories` count + `expert_personal_story.story_has_personal_health_journey` + `proof_bank.proof_bank_depth_score` |
| Voice DNA quality | 15% | `voice_dna.voice_confidence_score` + `voice_dna.sample_extracts` count + confirmation status of Voice DNA section |
| Offer stack completeness | 10% | Number of the 4 offer tiers populated with confirmed data across `offer_architecture` |
| Visual asset uploads | 5% | Number of `pending-upload` fields resolved: logo, brand guide, expert photo |

---

*Step 2 of 22 — Expert Dossier Data Schema — v1.0 Draft*
*Next: Step 3 — Conversation Flow Architecture*
