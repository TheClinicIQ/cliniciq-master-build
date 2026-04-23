# ClinicIQ Avatar Testing System
## 30 archetype avatars + an infinite-scale avatar factory. Each archetype is a full persona template that can be replicated across sub-niches, practice models, and quality tiers to generate thousands of unique test avatars.

---

## DESIGN PRINCIPLE

Don't build 100 avatars. Build 30 well-designed archetypes + a factory that expands them on demand. The system compounds. 30 archetypes × combinatorial variation = 3,000+ unique avatars when needed.

Each archetype is a FULL test template:
1. **Static persona spec** — who they are, their mechanism, their patient, their offer
2. **Pre-written answer set** — all 23 core onboarding questions answered in-character at their quality tier
3. **LLM runtime persona** — loaded when the avatar runs live so IQ's probing and follow-ups get in-character responses
4. **Testing metadata** — what specific failure modes this avatar is designed to stress-test
5. **Variation axes** — how this archetype can be multiplied (other sub-niches, other practice models, other personality flavors)

---

## THE 30 ARCHETYPES

### CELEBRITY TIER (5 archetypes — the "already crushing it" experts)

**AR01 — The Established Functional MD**
*(modeled archetype: Hyman-style)*
- Category: Functional Medicine
- Sub-niche: Metabolic/food-as-medicine
- Quality: A (Gold)
- Personality: P1 Confident + P2 Academic
- Model: M8 Digital + M9 High-Ticket
- Tests: Can platform handle expert who already has strong brand, books, audience? Does IQ add value or feel redundant?

**AR02 — The Brand-Driven Natural Health Expert**
*(modeled archetype: Axe-style)*
- Category: Functional Medicine / Natural Health
- Sub-niche: Cellular health, GLP-1 alternatives
- Quality: A (Gold)
- Personality: P1 Confident + P3 Healer
- Model: M1 Telehealth + M8 Digital + M9 High-Ticket
- Tests: The actual ClinicIQ client profile. Tests full webinar-to-offer funnel. High-volume lead-gen expert.

**AR03 — The Gentle-Voiced Women's Expert**
*(modeled archetype: Cole/Pelz-style blend)*
- Category: Functional Medicine / Women's Health
- Sub-niche: Inflammation, hormones, menopause
- Quality: A (Gold)
- Personality: P3 Healer
- Model: M1 Telehealth + M8 Digital
- Tests: Soft voice archetype. Does platform match gentle tone or default to aggressive DR copy?

**AR04 — The Clinical-Precision Longevity Expert**
*(modeled archetype: Attia/Huberman blend)*
- Category: Longevity / Performance Medicine
- Sub-niche: Data-driven longevity, biomarker optimization
- Quality: A (Gold)
- Personality: P2 Academic + P1 Confident
- Model: M8 Digital + M9 High-Ticket
- Tests: Hyper-clinical voice. Content must sound like long-form podcast, not Facebook ad.

**AR05 — The Contrarian-Positioned Expert**
*(modeled archetype: Gabrielle Lyon-style)*
- Category: Performance Medicine
- Sub-niche: Muscle-centric medicine, protein optimization
- Quality: A (Gold)
- Personality: P1 Confident
- Model: M8 Digital
- Tests: Contrarian positioning ("eat MORE, not less"). Does builder lean into contrarian or default to generic?

---

### ESTABLISHED LEADER TIER (8 archetypes — 100K-1M following, known in niche)

**AR06 — The Autoimmune Specialist**
- Category: Functional Medicine | Sub-niche: Autoimmune reversal | Quality: B Solid | Personality: P1 Confident + P3 Healer | Model: M1+M8
- Tests: Named methodology. Complex condition category.

**AR07 — The Gut-Focused Specialist**
- Category: Functional Medicine | Sub-niche: Gut health / SIBO / IBS | Quality: B Solid | Personality: P1 Confident | Model: M1 Telehealth
- Tests: Single-condition specialist. Deep niche expertise.

**AR08 — The Mold/CIRS Specialist**
- Category: Functional Medicine | Sub-niche: Mold illness, CIRS, Lyme | Quality: B Solid | Personality: P2 Academic | Model: M1 Telehealth
- Tests: Complex, controversial specialty. Proof requirements are high.

**AR09 — The Thyroid Specialist**
- Category: Functional Pharmacy | Sub-niche: Hashimoto's, thyroid | Quality: B Solid | Personality: P3 Healer | Model: M8 Digital
- Tests: Patient-as-avatar (expert has the condition). Authentic story leverage.

**AR10 — The Men's Health Expert**
- Category: Functional/Integrative | Sub-niche: Testosterone, men's longevity | Quality: B Solid | Personality: P1 Confident | Model: M5 Cash-Pay
- Tests: Different buyer psychology (men buy differently than women). Different copy rhythm.

**AR11 — The Women's Hormone Expert**
- Category: Naturopathic / Women's Health | Sub-niche: PCOS, post-birth-control | Quality: A Gold | Personality: P1 Confident | Model: M8+M1
- Tests: Women's health buyer. High emotional stakes.

**AR12 — The Nutrition-First Brand**
- Category: Nutritionist | Sub-niche: Functional nutrition, blood sugar | Quality: A Gold | Personality: P3 Healer + P4 Entrepreneur | Model: M8 Digital
- Tests: Product/methodology brand ("Fab Four"-style). Brand + content combo.

**AR13 — The Mechanism-Branded Expert**
- Category: Functional Medicine / Chiropractic | Sub-niche: Cellular detox, heavy metals | Quality: A Gold | Personality: P1 Confident | Model: M7+M8
- Tests: Existing proprietary methodology. Dual audience (practitioners + patients).

---

### GROWING EXPERT TIER (10 archetypes — the ClinicIQ ICP sweet spot)

**AR14 — The Mid-Career FM Doctor**
- Category: Functional Medicine | Sub-niche: Thyroid + hormones | Quality: B Solid | Personality: P3 Healer | Model: M1 Telehealth
- Tests: The classic ICP. Clinical competence, marketing gap.

**AR15 — The Growing Gut Specialist**
- Category: Functional Medicine | Sub-niche: Gut/SIBO | Quality: B Solid | Personality: P1 Confident | Model: M4 Hybrid
- Tests: Building from mid-size practice. Growth momentum but no system.

**AR16 — The Cash-Pay Men's Health Doc**
- Category: Naturopath | Sub-niche: Men's health, testosterone | Quality: B Solid | Personality: P1 Confident | Model: M5 Cash-Pay
- Tests: Premium cash-pay positioning. High-ticket pricing confidence.

**AR17 — The Somatic Therapist**
- Category: Mental Health | Sub-niche: Somatic therapy, chronic illness psychology | Quality: B Solid | Personality: P3 Healer | Model: M4 Hybrid
- Tests: Mental-health-meets-body-health. Softer close required.

**AR18 — The DPC Primary Care MD**
- Category: Direct Primary Care | Sub-niche: Concierge/membership primary care | Quality: C Surface | Personality: P4 Entrepreneur | Model: M6 Insurance Hybrid
- Tests: Membership model. Subscription offer. Not single-service selling.

**AR19 — The Plastic Surgeon**
- Category: Plastic Surgery | Sub-niche: Mommy makeover, body contouring | Quality: B Solid | Personality: P4 Entrepreneur | Model: M5 Cash-Pay
- Tests: Aesthetic/surgical category. Visual-heavy marketing needs. Different regulatory zone.

**AR20 — The Functional Dermatologist**
- Category: Dermatology | Sub-niche: Acne-gut connection, functional derm | Quality: B Solid | Personality: P1 Confident | Model: M5 Cash-Pay
- Tests: Medical specialty going functional. Bridge from insurance to cash-pay.

**AR21 — The Weight Loss MD (GLP-1 Era)**
- Category: Bariatric/Weight Loss | Sub-niche: GLP-1 alternatives, metabolic health | Quality: B Solid | Personality: P4 Entrepreneur | Model: M5 Cash-Pay
- Tests: Most competitive current category. Requires clear contrarian positioning.

**AR22 — The Acupuncturist / Fertility**
- Category: Acupuncture / TCM | Sub-niche: Fertility acupuncture | Quality: C Surface | Personality: P3 Healer | Model: M2 Solo Office
- Tests: Local practice. Emotional/high-stakes patient base. Non-Western modality.

**AR23 — The Biological Dentist**
- Category: Dentistry | Sub-niche: Biological/airway dentistry | Quality: C Surface | Personality: P2 Academic | Model: M2 Solo Office
- Tests: Novel dental positioning. Oral-systemic health angle. Service-based selling.

---

### EARLY-STAGE TIER (4 archetypes — the "I need help" users)

**AR24 — The New FM Practitioner**
- Category: Functional Medicine | Sub-niche: Metabolic health | Quality: D Struggling | Personality: P7 Brand-New | Model: M1 Telehealth
- Tests: 1-2 years in, no proof stack, no offer yet. Building from zero.

**AR25 — The Transitioning Conventional MD**
- Category: Integrative | Sub-niche: Going functional from conventional | Quality: C Surface | Personality: P5 Reluctant | Model: M4 Hybrid
- Tests: Established clinician, new to marketing. Reluctant to "sell."

**AR26 — The Health Coach Starting Out**
- Category: Health Coach | Sub-niche: Hormone or weight coaching | Quality: D Struggling | Personality: P7 Brand-New | Model: M1 Telehealth
- Tests: Non-clinical credentialing. No medical authority. Coaching-only positioning.

**AR27 — The Career-Pivot Nutritionist**
- Category: Nutritionist | Sub-niche: Unclear — still niching | Quality: D Struggling | Personality: P6 Multi-Hyphenate | Model: M1 Telehealth
- Tests: Multi-hyphenate coaching moment. IQ must narrow the avatar.

---

### EDGE CASE TIER (3 archetypes — designed to stress the system)

**AR28 — The "I Help Everyone" Expert**
- Category: Functional Medicine | Sub-niche: 8 conditions, 4 avatars, 6 offers | Quality: E Resistant | Personality: P6 Multi-Hyphenate | Model: M3 Group Practice
- Tests: IQ's narrowing ability. Coaching moment at Q1. Does platform force focus without damaging expert's actual multi-specialty reality?

**AR29 — The Skeptical Veteran**
- Category: Integrative MD | Sub-niche: Chronic illness | Quality: E Resistant | Personality: P5 Reluctant + skeptical | Model: M5 Cash-Pay
- Tests: 20-year practitioner, hostile to marketing, doesn't trust AI. Every coaching moment fires. Trust-building is entire challenge.

**AR30 — The Brand-New-Nothing**
- Category: Naturopath | Sub-niche: General, new grad | Quality: D Struggling | Personality: P7 Brand-New | Model: M1 Telehealth
- Tests: Just graduated, no patients, no proof, no offer, no mechanism, no story. IQ must generate almost everything.

---

## AVATAR FILE STRUCTURE

Each archetype gets a directory at `cliniciq/testing/avatars/<AR##>_<shortname>/` containing:

```
AR01_established_functional_md/
├── persona.yaml            # Static identity, mechanism, avatar, offer
├── answers.yaml            # Pre-written answers for all 23 core questions
├── runtime_prompt.md       # LLM persona prompt for live session play
├── test_metadata.yaml      # What this avatar stress-tests
└── variations.yaml         # Axes this archetype can be multiplied along
```

### `persona.yaml`
```yaml
id: AR01
name: Dr. [Generated Name]
category: functional_medicine
sub_niche: metabolic_food_as_medicine
quality_tier: A
personality: [P1, P2]
practice_model: [M8, M9]

credentials:
  - MD (Harvard)
  - Functional Medicine certified (IFM)
  - 14x NYT bestselling author
  - Former Cleveland Clinic Center for Functional Medicine director

years_in_practice: 25
team_size: 50+
audience_size: 5M+ social
revenue_scale: $50M+

mechanism:
  name: "The Food Fix Method"
  description: "Food is the most powerful drug. Chronic disease is a dietary disease."
  simple: "Stop eating garbage. Start eating real food. Watch disease reverse."
  why_it_works: "Every chronic disease traces back to metabolic dysfunction. Fix the metabolism — fix the disease."
  vs_conventional: "Conventional care manages symptoms with drugs. This reverses the underlying metabolic disease through food."

primary_avatar:
  name: "Metabolically Broken Martha"
  demographics: "Women 45-65, college-educated, household income $100K+, health-conscious"
  awareness_level: 3  # Solution-Aware — has tried things
  primary_symptom: "Can't lose weight despite eating healthy, energy crashing, brain fog"
  daily_reality: "[Full description]"
  false_beliefs:
    vehicle: "Diets don't work for me"
    internal: "My metabolism is just broken — it's age"
    external: "My doctor says my bloodwork is fine, so I must just need to try harder"
  dream_outcome: "Feel like myself again. Fit in my clothes. Have energy for my kids."
  patient_failure_language:
    - "I've tried everything"
    - "My doctor says everything is normal"
    - "I thought I was eating healthy"

core_offer:
  name: "The 10-Day Metabolic Reset"
  price: 197  # entry
  flagship: "The UltraWellness Program — $15K/yr membership"
  experience: "[Full description]"
  guarantee: "[Specific guarantee]"
  continuity: "Annual membership renewal + quarterly retreats"

proof:
  flagship_story: "[Specific detailed transformation]"
  aggregate: "Tens of thousands of patients across 25 years"
  credentials_highlights: "[14 books, Cleveland Clinic, etc.]"

voice:
  tone: "Authoritative but warm. Science-heavy but accessible."
  signature_phrases:
    - "Food is medicine"
    - "Your body isn't broken"
    - "Chronic disease is a dietary disease"
  banned_words:
    - "holistic"
    - "wellness journey"
  authority_style: "Teaching doctor. Not selling — educating."
```

### `answers.yaml`
Pre-written in-character answers to all 23 core onboarding questions. Quality matches the archetype's tier. Example for AR01 Q2:

```yaml
Q2_different: |
  The first thing I do is run a comprehensive metabolic panel that most primary 
  care doctors don't run. Insulin (not just glucose), HgbA1c, HOMA-IR, fasting 
  insulin, apoB, Lp(a), homocysteine, vitamin D, omega index, inflammatory 
  markers, thyroid with free T3 and T4 and antibodies — not just TSH. A complete 
  picture of the metabolic system in under $400 of labs.
  
  Because here's what happens: a woman comes to me. She's 52. Her doctor ran 
  a TSH and a standard CMP and said everything's fine. I run the full panel 
  and her insulin is 22, her apoB is 140, her HgbA1c is 5.9. She's one step 
  from type 2 diabetes, she's got cardiovascular disease brewing, and nobody 
  told her because nobody looked. That's what I do that others don't. I look.
```

Full answer set covers all 6 sections × 3-5 questions = 23 answers minimum, plus probe responses.

### `runtime_prompt.md`
The LLM prompt that plays this avatar LIVE when IQ is asking questions not in the pre-written set (probes, follow-ups, edge cases). Example opening:

```
You are Dr. [Name]. You are a functional medicine MD with 25 years of 
experience, 14 NYT bestselling books, and a 5M+ social following. You are 
currently going through an onboarding interview with IQ, an AI strategist 
for ClinicIQ — a growth platform for health experts.

Your speaking voice: [tone description + signature phrases + banned words]
Your patient avatar: [full avatar description]
Your mechanism: [Food Fix Method]
Your offer: [UltraWellness Program]

IQ will ask you questions. Answer them IN CHARACTER. Your answers should:
- Match your tier (Gold Responder): long, detailed, specific, rich with stories
- Use your signature phrases naturally
- Avoid your banned words
- Reference specific patients, labs, case examples
- Push back if IQ asks something you find redundant or beneath your level
- Get visibly impatient if IQ is slow or generic (you're used to premium service)

When asked edge-case questions, respond AS THIS SPECIFIC PERSON WOULD — not 
as a generic health expert. [Name] would answer this way.

Your internal state is: [P1 Confident + P2 Academic — declarative, teaching-mode, 
slight impatience with surface-level questions, willingness to go long on 
anything science-related]
```

### `test_metadata.yaml`
```yaml
id: AR01
designed_to_test:
  - Platform handling of expert with established brand
  - Whether IQ adds value or feels redundant to sophisticated user
  - Can builders match Hyman-tier voice (warm + authoritative + science)
  - Does output flex Cleveland Clinic credential correctly
  - Mechanism name preservation (doesn't try to rename "Food Fix Method")

expected_failure_modes_to_watch:
  - IQ asking beginner questions to sophisticated user
  - Generic "wellness journey" language creeping into output
  - Under-leveraging authority assets
  - Voice drift toward corporate health brand tone

expected_success_criteria:
  - Voice match score >= 90 across all outputs
  - Mechanism used consistently
  - Content positions as teaching, not selling
  - Offer stacks reflect premium positioning
```

### `variations.yaml`
```yaml
id: AR01
base_archetype: established_functional_md

variation_axes:
  sub_niche:
    - metabolic_food_as_medicine  # base
    - autoimmune_reversal
    - longevity_optimization
    - brain_health_neurodegeneration
    - toxic_burden_detox
  
  gender:
    - male  # base (Hyman-style)
    - female  # produces Amy Myers / Sara Gottfried style variation
  
  practice_model:
    - digital_plus_high_ticket  # base
    - solo_telehealth
    - group_practice_flagship
  
  quality_tier_variation:
    - A  # base
    - B  # slightly less articulate but still established
  
  geography:
    - usa_major_market
    - usa_secondary_market
    - international_english
    - uk_australia_specific

total_possible_variations: 5 × 2 × 3 × 2 × 4 = 240 unique avatars from this one archetype
```

---

## THE AVATAR FACTORY

A programmatic generator that takes any archetype + variation axes and produces a fully-populated avatar ready to run through the platform.

### Factory logic
```
factory.generate(
  archetype_id="AR01",
  variations={
    "sub_niche": "autoimmune_reversal",
    "gender": "female", 
    "practice_model": "solo_telehealth",
  }
)
```

Produces:
1. New persona.yaml with sub-niche swapped (mechanism renamed, avatar renamed, answers rewritten to new niche's language)
2. New answers.yaml with all 23 responses rewritten for the new sub-niche but at the same quality tier
3. New runtime_prompt.md loaded with the variation
4. New test_metadata tagging what this specific variation stress-tests

### LLM-powered answer rewriting
The factory uses an LLM to rewrite pre-written answers for new sub-niches while preserving the archetype's quality tier, personality, and voice. Example:

**AR01 base answer to Q2:** Metabolic panel details (insulin, HgbA1c, apoB, etc.)

**AR01 + autoimmune_reversal variation Q2 (auto-rewritten):**
> "The first thing I do is run a comprehensive autoimmune panel most rheumatologists don't run. TPO, TG, ANA, dsDNA, RF, anti-CCP, transglutaminase, gliadin — plus the environmental triggers: mold, mycotoxins, tick-borne, EBV reactivation, heavy metals. A complete picture of what's driving the immune dysfunction..."

Same tier, same personality, different niche. Factory generates at volume.

---

## HOW THIS RUNS

### For onboarding testing:
1. Load avatar's `persona.yaml` and `runtime_prompt.md` into a testing LLM
2. Start an onboarding session. The avatar LLM receives IQ's messages and responds in character.
3. For questions matching the pre-written Q1-Q23, the avatar uses the prepared answer (ensures coverage)
4. For probes, follow-ups, edge cases, the avatar LLM responds dynamically in character
5. Full transcript + tool log + SSE stream logged for review

### For output testing:
1. Once onboarding completes, the dossier exists
2. Trigger engine runs against that dossier
3. Outputs are reviewed by the full synthetic panel (per `SYNTHETIC_REVIEW_SYSTEM_MASTER.md`)
4. All reviews aggregate into the avatar's test result file

### For scale:
1. Run the 30 base archetypes first — establish baseline
2. Generate 10-20 variations per archetype = 300-600 total avatars from the base set
3. Run batch testing — all avatars through onboarding + at least one engine each
4. Panel reviews produce aggregate quality data
5. Feedback loop (per master spec) improves IQ and builders based on patterns
6. Generate more variations as needed to stress-test specific improvements

---

## BUILD EXECUTION (FOR CLAUDE CODE)

### Deliverables:
1. **30 archetype directories** at `cliniciq/testing/avatars/AR01/` through `AR30/`, each with all 5 files populated
2. **Avatar factory** at `cliniciq/testing/avatar_factory/` — Python scripts that generate variations
3. **Test runner** at `cliniciq/testing/test_runner/` — orchestrates avatar → onboarding → engines → synthetic review
4. **Results dashboard** at `cliniciq/testing/results/` — aggregates test results per avatar

### Priority:
1. Build AR02 first (the archetype closest to actual ClinicIQ client reality)
2. Then AR14 and AR15 (the ICP sweet spot — most common real users)
3. Then AR24, AR26, AR30 (the struggling-user tier — hardest for the platform)
4. Then AR28 (the "I help everyone" edge case — key coaching moment test)
5. Then fill in the rest

### Quality bar per archetype:
- Persona is detailed enough to sound like a real person, not a stock character
- Answers are in the archetype's voice with tier-appropriate depth
- Runtime prompt produces in-character responses when tested with 10 sample edge-case questions
- Test metadata specifies what failure modes this avatar is DESIGNED to catch

### Not quality criteria:
- "Realistic revenue numbers" — these are testing avatars, not market research
- "Matches a specific real expert's exact positioning" — celebrity-tier archetypes are INSPIRED by public figures, not impersonations
- "Coverage of every possible niche" — that's the factory's job, not the archetypes'
