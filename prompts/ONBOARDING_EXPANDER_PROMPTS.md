# IQ Onboarding — Section Expander Prompts
## The actual instructions IQ follows to expand raw answers into complete strategic documents.
## These go into the new `_onboarding_guidelines.md` that replaces the 1,199-line version.

---

## HOW THESE WORK

After IQ finishes a section's questions and has the raw answers in context, it expands them into a complete strategic card. These prompts tell IQ exactly how to do that expansion for each section. IQ doesn't need a separate expander service — it has the raw answers, it has these instructions, and it has the framework knowledge. It does the expansion in its own reasoning, then calls `capture_dossier` with the full payload and `append_profile_section` with the narrative.

**The rule for every expander: generate EVERYTHING the downstream builders will need. If you don't generate it now, a builder will have to invent it later — and invented material is always weaker than extracted + expanded material.**

---

## SECTION 1 EXPANDER: You & Your Method

**From the raw answers to Q1-Q5, generate ALL of the following:**

**Mechanism:**
- `mechanism_name`: If the expert gave a name, use it. If not, generate 1 strong candidate based on their approach — something specific and ownable, not generic ("The Signal Reset Protocol" not "Root Cause Method"). Note it as AI-suggested so the expert can rename.
- `mechanism_description`: 2-3 sentences explaining what the expert does differently, written in plain language a patient would understand. Pull from Q2.
- `mechanism_simple`: The fifth-grade version. One sentence. If the expert's Q2 answer was already simple, this might match. If it was clinical, translate it.
- `mechanism_why_it_works`: Why this approach succeeds when diets, drugs, conventional care, and other approaches fail. Infer from Q2 + Q3. Frame as: "Other approaches do X. This works because it does Y instead."
- `mechanism_vs_conventional`: The explicit contrast. "Conventional care does [X]. This approach does [Y]." Must be specific enough that a funnel page headline could be written from it.

**Positioning:**
- `contrarian_position`: The expert's core belief that goes against their field. From Q3. Sharpen it into a single declarative statement that could be a social media post hook. Not "I believe in a more thorough approach" — that's improvement positioning. Must be a NEW VEHICLE claim: "The thing everyone else is treating isn't actually the problem."
- `category_villain`: From Q5 — what they're angry about, turned into a clear enemy. Not a person. A practice, a system, a dogma. "The 15-minute specialist visit that checks three markers and calls it complete."
- `why_now`: Why this expert's approach is especially urgent right now. AI-generated from their specialty + current health landscape. E.g., for a functional medicine practitioner: "GLP-1 drugs are masking symptoms at scale while the root causes compound untreated."

**Origin Story (Epiphany Bridge):**
- `before_state`: What the expert believed or did before their turning point. From Q4.
- `trigger_event`: The specific moment — a patient, a personal crisis, a discovery. From Q4.
- `realization`: What they now understand. From Q4.
- `emotional_truth`: How it felt. From Q4 — if the expert was matter-of-fact, infer the emotion from the content.
- `bridge_to_patients`: Why this moment made them committed to every patient after. If not explicit in Q4, infer from Q5 (anger often connects to mission).
- `character_type`: Infer from the full conversation — Reluctant Hero ("I didn't plan this"), Cause-Driven ("I can't NOT do this"), Reporter ("I documented everything and became obsessed").

**Personal details to preserve verbatim:**
- Any specific names, places, moments from their origin story — these make webinar openings and about pages feel real, not templated
- The exact language they used when describing their anger (Q5) — this becomes the most quotable material in their entire brand
- Any phrases they repeated or emphasized — early Voice DNA signal

**What downstream builders need from this section:**
- Webinar Builder: origin story (Epiphany Bridge), mechanism (3 Secrets build on this), contrarian position (Secret #1 typically breaks the "vehicle" false belief tied to this)
- Content Builder: contrarian position (myth-busting pillar), mechanism (mechanism education pillar), anger (authority/conviction content)
- Funnel Builder: mechanism name + description (hero section), why-now (urgency), villain (the "old way" section)
- Ad Creative Builder: contrarian position (villain hooks), mechanism (curiosity hooks), origin story (authority hooks)
- Email Builder: origin story (nurture sequence email #2-3), mechanism (belief-building emails)

---

## SECTION 2 EXPANDER: Your Patient

**From the raw answers to Q6-Q9, generate ALL of the following:**

**Avatar identity:**
- `avatar_name`: Generate a memorable persona name from their description. "[Adjective] [Name]" format — "Exhausted Emma," "Stressed Mom Sarah," "Foggy-Brain Fiona." Must feel real, not cartoonish.
- `demographics`: Age range, gender, life stage, occupation type — inferred from Q6.
- `awareness_level`: Classify from Q6 (how much she's tried, how long she's struggled): Unaware (doesn't know something's wrong), Problem-Aware (knows symptoms, hasn't found the solution), Solution-Aware (has tried things, comparing), Product-Aware (knows about experts like this one), Most-Aware (ready to buy, just needs the right one). Most health avatars are Level 2-3.

**Layer 1 — Daily Reality (from Q7):**
- `morning`: What her morning looks like. Specific, sensory — "wakes up already exhausted, hits snooze three times, drags herself to the coffee machine, snaps at her kids before school." Not "she's tired in the morning."
- `afternoon`: The crash, the fog, the moment the day falls apart. From Q7 mid-afternoon content.
- `evening`: What's left. Cancelled plans, couch by 7pm, guilt about not being present. From Q7 evening content.
- If Q7 only covered morning, GENERATE afternoon and evening from the pattern. A woman who "wakes up exhausted and can't think by 10am" predictably "crashes at 2pm, craves sugar, cancels the gym, and is asleep on the couch by 8." Generate this and let the expert approve.

**Layer 2 — Emotional Core:**
- `primary_frustration`: The thing that bothers her most. From Q6 + Q7.
- `primary_fear`: From Q9. What happens if nothing changes.
- `shame`: What she doesn't say out loud — infer from the pattern. If she's been struggling for years and "tried everything," the shame is usually "maybe this IS who I am now."
- `hope`: What she's still holding onto — infer from Q8 (why she came in). If she came in, she hasn't given up.

**Layer 3 — Belief System (THE 3 FALSE BELIEFS — critical):**
Generate these from the avatar profile + the mechanism from Section 1:

- `false_belief_vehicle`: What she believes about SOLUTIONS that blocks her. This is specific to her failed attempts from Q6. "Diets don't work for me" / "I've tried functional medicine and it didn't help" / "Nothing works for this." The vehicle belief is always about the METHOD — she doesn't believe the category of solution works.

- `false_belief_internal`: What she believes about HERSELF. "I'm not disciplined enough" / "I'm too far gone" / "I don't deserve to spend this on myself" / "My body is just broken." The internal belief is always about her own capacity or worthiness.

- `false_belief_external`: What she believes about OUTSIDE FORCES blocking her. "My husband won't support this" / "My doctor will judge me" / "I can't afford it" / "I don't have time." The external belief is always about something outside her control.

**Each false belief must be specific to THIS avatar.** Not generic. "I've tried everything" is generic. "I've been to 3 endocrinologists and they all said my thyroid is fine while I feel like I'm dying" is specific. Generate from the context.

**For each false belief, also generate:**
- The story or proof that breaks it (from proof bank if available, or flag as needed)
- The emotional weight: is it felt as shame, fear, skepticism, fatigue, or identity threat?

**Layer 4 — Internal Dialogue:**
- `two_am_thought`: What she says to herself at 2am. Generate from the fear (Q9) + the emotional core. "Is this just who I am now?" / "I used to be someone who could handle anything." / "What if it's something serious and nobody's catching it?"
- Generate 2-3 variants. Different emotional registers: permanence fear, identity grief, self-blame, isolation.

**Patient language (highest-converting copy material):**
- `failure_language`: Generate 3-5 phrases patients like her use to describe their failed journey. "I've been to 5 doctors and nobody found anything." / "My doctor told me it's just aging." / "Everything I try works for two weeks and then stops." These become ad hooks, email subject lines, and webinar opening lines. They must sound like HER, not like a marketer.
- `dream_language`: From Q8 — the exact words she uses to describe what she wants. Plus 2-3 AI-generated variants: "I just want to feel like myself again" / "I want to wake up and not dread the day" / "I want to be present for my kids."

**Buying triggers:**
- What finally makes her act. Infer from awareness level + fear + desire. Level 2 (problem-aware): a moment of crisis ("I couldn't get off the couch for my daughter's game"). Level 3 (solution-aware): seeing proof ("someone like me got results"). Level 4 (product-aware): urgency ("I can't keep doing this another year").

**What downstream builders need from this section:**
- EVERY builder uses the avatar. It's the targeting for everything.
- Ad Creative: failure_language (scroll-stopping hooks), two_am_thought (emotional hooks), false beliefs (angle structure — one per belief)
- Webinar Builder: 3 false beliefs become the 3 secrets. Each secret breaks one belief.
- Email Builder: Each false belief = one email in the nurture sequence. The sequence breaks beliefs in order: vehicle → internal → external.
- Content Builder: Daily reality = content themes. Failure language = hooks. Dream language = CTAs. False beliefs = myth-busting pillar.
- Funnel Builder: Dream outcome = hero section headline. Fear = urgency section. Proof that breaks each belief = testimonial placement.
- Sales Script Builder: Objections map to false beliefs. Each objection response = emotional acknowledgment → logical reframe → proof.

---

## SECTION 3 EXPANDER: Your Offer

**From the raw answers to Q10-Q14, generate ALL of the following:**

**Core offer:**
- `name`: What they called it. If they didn't name it, suggest one based on the mechanism.
- `price`: Exact number from Q10.
- `what_they_get`: Week-by-week from Q11. If they gave high-level, expand into a realistic program structure for their specialty.
- `before_state`: From the avatar (Section 2) — where the patient starts.
- `after_state`: Where the patient ends. From Q11 + inference. Must include practical (symptoms resolved), emotional (confidence, energy, presence), and identity (who she becomes) transformations.
- `time_to_first_shift`: From Q11. Specific — "week 2-3" not "quickly."
- `effort_required`: From Q11 — what the patient has to do. Be honest.
- `friction_points`: From Q12 — what almost makes them quit. SPECIFIC. "The elimination diet in week 2" not "it's hard."

**Guarantee:**
- From Q13 — structure as a named guarantee. "The [X] Guarantee: if you [criteria], and don't [result], we [action]." If the expert was vague, generate 2-3 guarantee options for them to pick from.

**Continuity / retention:**
- From Q14 — what happens after the core program. Maintenance phase, community, follow-up visits, next-level offering. If nothing exists, flag as an opportunity: "No continuity model yet — this is a major LTV opportunity. Recommend building a maintenance tier or community."

**Value Equation assessment (Hormozi — shown simply, not as a score):**
- Dream Outcome: Is it specific and compelling? If vague ("feel better"), flag for improvement.
- Perceived Likelihood: Is there proof? Cross-reference with Section 4 proof bank. If thin, flag.
- Time Delay: How fast to first result? Under 4 weeks = strong. Over 8 weeks = needs messaging to manage expectations.
- Effort/Sacrifice: How much work from the patient? High effort = needs friction reduction (bonuses, done-for-you elements).

**Bonus ideas (AI-generated — 3 options):**
Each bonus should do ONE of these:
- Reduce a specific friction point from Q12 (e.g., if the friction is "shopping for supplements," bonus = "pre-built supplement kit shipped to your door")
- Break a specific false belief from Section 2 (e.g., if the internal belief is "I'm not disciplined enough," bonus = "daily accountability check-in text from your care team")
- Reduce time delay (e.g., "Quick-start protocol — feel the first shift in 72 hours")

**What downstream builders need:**
- Funnel Builder: offer name, price, before/after, guarantee, bonus stack — this IS the order page
- Webinar Builder: offer name, price, before/after, guarantee — this IS the stack slide
- Sales Script Builder: price, friction points, guarantee — this IS the close section
- Email Builder: before/after, time to first shift — this IS email #5-7 in the post-webinar sequence

---

## SECTION 4 EXPANDER: Your Proof

**From the raw answers to Q15-Q17, generate ALL of the following:**

**Flagship transformation story:**
Structure from Q15 into: Before (her life, specific and sensory) → What she tried (failed attempts) → Turning point (the moment with this expert) → Result (specific outcomes) → Life now (the after-state, specific and sensory). Preserve any direct quotes verbatim. Preserve any emotional details — the expert's voice when telling this story IS the brand.

**Credential stack:**
From Q16 — sort by impact, most impressive first. Group into: Clinical credentials, Media/Authority, Teaching/Speaking, Institutional affiliations.

**Aggregate proof:**
From Q17 — structure as: "[X] patients across [Y] years, approximately [Z]% meaningful improvement." Even rough estimates are usable.

**Proof classification (AI-generated):**
For each piece of proof, classify:
- Which false belief it can break (vehicle / internal / external / general credibility)
- Best deployment context (webinar proof stack / ad creative / email / funnel page / sales script)

**Proof score and gap analysis:**
- Score 0-100 based on: number of stories, specificity, emotional weight, variety (transformation + data + credentials + media), direct quotes captured.
- Gaps flagged: "Need a faster-result story for ad proof" / "Need a skeptic-to-believer story for Solution-Aware audience" / "Need aggregate data for credibility" — with suggestions for how to capture later.

**What downstream builders need:**
- Webinar Builder: flagship story (proof stack section), aggregate (credibility slide), credentials (authority frame)
- Ad Creative Builder: transformation stories with patient language (proof hooks), credentials (authority hooks)
- Funnel Builder: testimonials with specific outcomes (order page), credentials (trust strip)
- Email Builder: proof stories broken into individual emails (one story per email in nurture)

---

## SECTION 5 EXPANDER: Your Voice & Brand

**From the raw answers to Q18-Q20 PLUS passive analysis of the entire conversation, generate ALL of the following:**

**Voice DNA (mostly from passive analysis):**
- `tone_primary`: The dominant tone across the conversation. "Direct and confident" / "Warm and reassuring" / "Blunt and no-nonsense" / "Clinical but accessible."
- `tone_secondary`: The undertone. "With dry humor" / "With grounded empathy" / "With quiet intensity."
- `sentence_rhythm`: How they build sentences. "Short declaratives when making a point. Longer, flowing sentences when explaining a concept."
- `vocabulary_register`: Clinical vs. plain. "Uses medical terms when precision matters, plain language everywhere else."
- `emotional_register`: How they express emotion. "Passionate but controlled" / "Understated — lets the data do the work" / "Openly emotional — tears when telling patient stories."
- `conviction_level`: Do they hedge or declare? "Declares. Says 'this is what's happening' not 'this might be related.'"
- `humor_level`: "Dry, occasional, never at the patient's expense" / "None — dead serious" / "Frequent — uses humor to disarm."
- `authority_style`: "Trusted guide" / "Bold challenger" / "Teacher" / "Peer."
- `signature_phrases`: From Q18 + phrases captured from the conversation. 3-5 minimum.
- `banned_words`: From Q19. Plus any words they conspicuously avoided throughout the conversation.
- `voice_confidence_score`: 0-100 based on how much conversation data IQ had to work with.

**Brand feel:**
- From Q20 + overall conversation energy. "Should feel like: [brand/person they admire]. Should never feel like: [brand/person they dislike]."
- AI-generated brand personality summary: 2-3 sentences capturing the overall feel.

**ALWAYS/NEVER rules (AI-generated from everything above):**
- ALWAYS: 5 rules. E.g., "Always lead with specifics, not generalities." "Always name the mechanism, not the category." "Always acknowledge the patient's effort before redirecting."
- NEVER: 5 rules. E.g., "Never use 'wellness journey.'" "Never hedge with 'might' or 'could' — declare." "Never open with a question — open with a statement."

**What downstream builders need:**
- EVERY builder runs every word through Voice DNA. This is the quality control layer.
- Content Builder: tone, rhythm, signature phrases — every post must match
- Email Builder: emotional register, conviction level — every email must match
- Webinar Builder: authority style, humor level — the script must sound like them presenting
- Ad Creative Builder: banned words are a hard filter — nothing with a banned word ships
- Funnel Builder: brand feel determines page design direction

---

## SECTION 6 EXPANDER: Lead Magnet Ideas

**From the complete profile (Sections 1-5), generate 5 creative, specific, personalized lead magnet ideas.**

**Each idea must:**
- Be a vibe-coded interactive micro-app (NOT a PDF)
- Be specific to this expert's mechanism and avatar (NOT generic "Health Quiz")
- Deliver personalized results to the user
- Capture email before showing results
- Bridge naturally to the expert's core offer or a booking page
- Have a name that sounds like a product, not a form

**Generation approach:**
Look at the avatar's awareness level, primary frustration, and the mechanism. Then ask: "What would make this avatar stop scrolling, give her email, spend 3 minutes, and feel like she just learned something about herself that nobody else has shown her?"

- If avatar is Level 2 (Problem-Aware) → Quiz or Assessment that DIAGNOSES ("Find out which of the 5 patterns is driving your fatigue")
- If avatar is Level 3 (Solution-Aware) → Calculator or Profiler that COMPARES ("See how your approach stacks up against what actually works")
- If avatar has strong fear → Risk Profile that QUANTIFIES the fear ("What's your [condition] risk score?")
- If the mechanism has clear steps → Tracker that DEMONSTRATES the mechanism ("Track your [markers] for 7 days and see the pattern")

**Each option presented with:**
- Emoji + specific name (tied to their mechanism)
- One-liner (what the user experiences)
- How it works (2-3 sentences)
- Why it fits THIS avatar (connects to their psychology from Section 2)

After selection, the lead magnet builder agent receives: `{type, name, headline, avatar, mechanism, next_step, dossier}` and builds it.

---

## THE NARRATIVE VOICE

When IQ calls `append_profile_section` to write the right-panel profile, it must:
- Write in the expert's voice (using the Voice DNA captured so far)
- Use specific names, numbers, and details (not "patients" — "women in their 40s with Hashimoto's who've been told their labs are normal")
- Include the expert's own phrases when possible (quoted from the conversation)
- Never use generic health marketing language ("wellness journey," "holistic approach," "empowered to heal")
- Be 3-6 sentences per section. Rich but not bloated.

This profile doc is what the expert watches build on the right side. It's the "wow" moment. If it reads like a template, the wow dies. If it reads like someone who actually listened to them, the wow is instant.
