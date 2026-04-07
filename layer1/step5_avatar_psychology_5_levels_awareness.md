# clinicIQ — Layer 1: Onboarding Agent — Step 5: Avatar Psychology & 5 Levels of Awareness Extraction
**Version 1.0 — Final**
*Step 5 of 22 | Depends on: Step 1 (Agent Description), Step 2 (Data Schema), Step 3 (Conversation Flow), Step 4 (Voice DNA)*

---

## Purpose

The avatar is the most consumed data in the entire clinicIQ platform. Every ad hook, every email subject line, every webinar opener, every funnel headline, every offer frame — all of it starts with who the avatar is, what they feel, what they've tried, what they believe, and where they are in their awareness of the problem and solution.

This document defines how the Onboarding Agent extracts deep, psychologically precise avatar profiles — including the critical awareness level determination that sets the entry angle for every cold traffic campaign — and how that data flows into every downstream output.

This is not demographics. Demographics are the least useful thing about a buyer. This is psychology. This is the voice inside their head at 2am. This is the story they've been telling themselves for years about why they can't get well. That's what this step captures.

---

## Why Health Buyers Are Different

Before the extraction methodology — a critical frame that must be baked into how the agent asks questions and interprets answers.

People buying health solutions are not buying something they want. They are buying something they desperately need — and they have usually been failed multiple times before they find this expert. That history shapes everything about how they think, what they believe, how skeptical they are, and what it takes to move them.

**The health buyer's psychological reality:**

1. **They have been told their problem is permanent.** Doctors, specialists, family members have confirmed the belief: "this is just how it is," "you'll be on this medication forever," "this is part of getting older." Years of reinforcement. The expert's job — and clinicIQ's job — is not to attack this belief head-on. It's to open a crack of possibility and let the avatar walk through it themselves.

2. **They have tried things that didn't work.** Diets. Supplements. Other doctors. Medications with side effects. Every failed attempt adds another layer to the belief that nothing will work — including this. Overcoming that accumulated skepticism requires specific strategic language, not just a stronger claim.

3. **They are not buying a product. They are buying a version of themselves.** What they really want is to feel like themselves again. To be present for their family. To get their life back. The product is only interesting because of the transformation it enables. All messaging must stay anchored to who they become — not what they take or what program they join.

4. **They are embarrassed.** Many chronic health conditions carry shame — weight, mental health, autoimmune conditions that don't show but ruin quality of life. The avatar has often stopped telling people how bad it is. They feel alone in it. The moment the messaging makes them feel seen and understood — that's when they lean in.

5. **They make buying decisions differently under health duress.** The pain of staying the same eventually becomes greater than the fear of trying something new. Great health marketing finds the moment that tipping point is near and makes the path forward obvious, safe, and urgent.

The agent extracts avatar psychology through this lens — not as a generic marketing exercise but as a deep act of empathy that translates directly into more effective messaging.

---

## The Primary Avatar — Extraction Framework

### Anchor Question (from Step 3)
> "Describe the patient who gets the absolute best results with you — not just who you work with, but who you light up for. What are they dealing with, what have they tried, and what does life look like for them before they find you?"

This question is designed to pull the expert into vivid, specific description — not demographics, not generalizations. The best answers are almost always about a specific type of person or a specific case they remember.

### Layer 1: Surface Demographics
The agent collects these quickly — they're the context, not the content.

- Age range
- Gender skew (if applicable)
- Income level (determines offer accessibility and payment sensitivity)
- Geographic context (local vs. national vs. global; urban vs. rural affects access and trust of alternative medicine)
- Family status (relevant to health motivation — many avatars are motivated by wanting to be present for kids or grandkids, not just themselves)

**Agent behavior:** These are fast-start fields. If the expert doesn't know, agent generates based on specialty norms. Don't dwell here — the real work is the psychology.

### Layer 2: The Symptom Stack
What does the avatar experience in daily life? Not diagnoses — lived experience.

**The critical distinction:** Avatars don't think in diagnoses. They think in symptoms and life impact. A person with Hashimoto's doesn't wake up thinking "my autoimmune thyroid condition is flaring." They wake up thinking "I can't get out of bed again. I'm going to let my kids down today. My brain won't work. I feel like a failure."

**Extraction questions:**
> "What does a bad day look like for your ideal patient — walk me through it, hour by hour if you can."

> "What symptoms are they describing when they first reach out to you?"

> "What are the things they've stopped doing because of how they feel?"

**Fields populated:**
- `avatar.primary_symptom` — the single dominant symptom or experience (the one they lead with)
- `avatar.symptoms_list` — the full stack of secondary symptoms and life impacts
- `avatar.daily_frustrations` — the specific moments and situations the symptom creates

**Agent behavior:** The more specific and vivid this section is, the stronger every hook will be. Push for granularity. "Fatigue" is weak. "Can't make it to 2pm without needing to lie down, brain fog so bad she can't finish a sentence, has to cancel plans with her kids at least once a week" — that's an ad hook.

### Layer 3: The Emotional Core
What is this avatar really feeling underneath the symptoms? This is what creates connection — not the symptoms themselves but the emotional experience of living with them.

**The four emotional layers to extract:**

**1. Core Fear** — The deepest thing they're afraid this means.
- Common in health contexts: *"I'm never going to get better." "This is the rest of my life." "I'm going to miss my kids growing up." "My body is broken and I can't fix it." "I'm becoming a burden."*

**2. Secondary Fears** — The fears that orbit the core fear.
- Fear of being dismissed again ("another doctor who doesn't take me seriously")
- Fear of wasting money on something that won't work
- Fear of side effects or making things worse
- Fear of having to be the one who figures this out alone

**3. Deepest Desire** — What do they actually want more than anything?
- Not "to feel better" — that's too vague. What specifically?
- *"To have energy when I wake up and still have it at dinner with my family." "To lose the weight and keep it off without starving myself." "To get off these medications before they do permanent damage." "To feel like myself again for the first time in ten years."*

**4. Transformation Identity** — Who do they want to BECOME?
- This is the most powerful field in the entire avatar psychology section because it is the target of the close language in every webinar and every sales conversation.
- Not "someone who feels better" — a specific new identity. *"The mom who shows up fully." "The version of himself that can compete again." "The doctor who proves functional medicine right." "The woman her husband fell in love with."*

**Extraction question:**
> "If your perfect patient woke up one year from now and everything had worked exactly as you know it can — what does their life look like? Not their labs, not their symptoms — their actual life. What are they doing that they couldn't do before? Who are they being?"

This question reliably produces the transformation identity. It is the single most important answer in this section.

### Layer 4: The Belief System
What does this avatar currently believe — and what does that belief system make impossible to accept about the expert's approach?

This is where health marketing breaks down for most practitioners. They assume they just need to explain the science clearly enough and people will get it. They won't. The avatar has a belief system that filters everything they hear — built from years of doctor visits, failed treatments, medication side effects, family skepticism, and media messaging. Every new claim gets run through that filter.

**The Three False Beliefs (maps directly to Brunson's Three Secrets / Webinar Structure):**

**False Belief #1 — Vehicle Belief** *(maps to `avatar.false_belief_vehicle`)*
Why they don't believe the expert's approach will work — the thing they've been told or concluded that makes the new vehicle seem unlikely or impossible.

Common examples:
- *"I've tried supplements before and they don't work for me."*
- *"My doctor says there's no evidence for functional medicine."*
- *"If this worked, insurance would cover it."*
- *"I've already tried diet changes and nothing happened."*
- *"Things like this only work for people who aren't as sick as I am."*

**False Belief #2 — Internal Belief** *(maps to `avatar.false_belief_internal`)*
Why they don't believe they personally can achieve the result — the self-limiting belief about their own capacity.

Common examples:
- *"I don't have the willpower to stick to a protocol."*
- *"I've failed at health programs before."*
- *"My body is too far gone."*
- *"I'm too busy/tired/old to do what it takes."*
- *"I've never been able to sustain anything."*

**False Belief #3 — External Belief** *(maps to `avatar.false_belief_external`)*
Why they believe external circumstances will prevent them from succeeding, even if the approach and their willpower are both there.

Common examples:
- *"I can't afford it."*
- *"My family won't support a change like this."*
- *"I travel too much / work too much to be consistent."*
- *"I can't find a practitioner near me."*
- *"I don't have time to cook differently or exercise."*

**Extraction question:**
> "When someone first hears about what you do and how you do it — what are the most common reasons they give for why it won't work for them? The excuses, the doubts, the things they say before they've really committed?"

**Why this matters:** These three false beliefs are not obstacles to work around. They are the architecture of the webinar. Every piece of the persuasion sequence — the stories, the mechanism, the case studies, the close — exists to systematically dissolve these three beliefs. The agent captures them here so the Builder Layer can construct that architecture precisely.

### Layer 5: Language Patterns
What exact words does the avatar use when they talk to themselves about their problem?

This is one of the most underutilized levers in health marketing. When messaging uses the exact words the avatar uses internally — not paraphrases, not clinical translations, not marketing language — the avatar's brain recognizes it as their own thought and trust is established instantly.

**Extraction question:**
> "What do your patients say when they first reach out — not the formal intake answers but the first message, the first call? What words do they use? What are they describing?"

**What to capture:**
- The exact phrases they use to describe their symptoms (not the clinical name — their words)
- The emotional shorthand they use (*"I just feel off," "I'm running on empty," "I've lost myself"*)
- What they've been told by doctors (this becomes the villain language — what the avatar currently believes that the messaging needs to gently challenge)
- What they've Googled or searched for (tells you exactly how problem-aware they are and what search terms resonate)

**Field populated:** `avatar.language_patterns` — an array of exact phrases, stored verbatim, used directly in ad copy, email subject lines, and webinar hooks.

**The rule:** The best hooks are not invented by copywriters. They are stolen directly from the avatar's mouth.

### Layer 6: Previous Solutions — The Failure Stack
What has this avatar already tried, in what order, and why did each thing fail?

This is the competitive landscape from the avatar's perspective — not what the expert knows about competitors, but what the patient experienced firsthand.

**Extraction question:**
> "Walk me through the typical journey your patient takes before they find you — year by year if you can. What do they try? What happens? Where do they end up?"

**What to capture for each failed solution:**
- What it was (medication, diet, another practitioner, supplement, surgery)
- Why they tried it (what promise it made)
- What happened (why it failed — side effects, stopped working, never worked, temporary fix)
- What they concluded from the failure (this becomes a false belief — see above)

**Field populated:** `avatar.previous_solutions_tried`

**Why this matters for copy:** Every previous failed solution is a vehicle doubt that must be acknowledged and dissolved before the new vehicle can be accepted. A webinar that ignores what the avatar has already tried will feel tone-deaf. A webinar that names exactly what they tried, exactly why it didn't work, and exactly why the new vehicle is fundamentally different — that's a webinar that converts.

### Layer 7: Buying Triggers
What finally makes this avatar take action? After all the failed attempts and accumulated skepticism — what tips them over?

**Common health buying triggers to probe for:**
- A new or worsening diagnosis ("my doctor said if I don't change something I'll be on insulin within a year")
- A major life event (wedding, grandchild born, milestone birthday, health scare)
- Hitting a personal bottom ("I couldn't make it through my daughter's graduation without sitting down")
- Finding proof that it works for someone like them (testimonial from a similar case)
- Running out of conventional options ("my doctor said there's nothing more they can do")
- A specific piece of content that described their experience exactly

**Extraction question:**
> "Think about the patients who committed most quickly when they found you — what was going on in their life right then? What had just happened, or what were they terrified was about to happen?"

**Field populated:** `avatar.buying_triggers`

**Why this matters:** Buying triggers inform the urgency architecture of every funnel. When the expert knows that a diagnosis conversation with a conventional doctor is a common trigger, they can build content that intercepts the avatar right at that moment. When they know a milestone birthday is a common trigger, seasonal campaigns get timed accordingly.

### Layer 8: Primary Objections
What are the last-mile objections that prevent the sale even after interest is established?

**The four most common in health high-ticket:**
1. **Price** — "I can't afford $6,000 / $8,000 right now." (Almost always a value problem, not a money problem)
2. **Spouse/partner** — "I need to talk to my husband/wife." (Trust issue or missing social proof with the partner)
3. **Time** — "I don't have time to commit to a program right now." (Usually fear of another failed attempt disguised as a logistics objection)
4. **Skepticism** — "I don't know if this will work for me specifically." (Internal false belief — not dissolved sufficiently in the webinar)

**Extraction question:**
> "When someone gets to the point of making a decision and they don't buy — what do they say? What's the reason they give?"

**Field populated:** `avatar.objections_primary`

**Why this matters:** These objections must be addressed in the webinar close, in the sales script, in the FAQ section of the order page, and in email follow-up sequences. The Builder Layer uses this field to ensure every close sequence is pre-objection-handling — the objection is dissolved before the prospect even raises it.

---

## The 5 Levels of Awareness — Determination Framework

Eugene Schwartz's 5 Levels of Awareness is the most important framework in direct response marketing for determining how to enter a cold traffic conversation. Get it wrong and every ad, every hook, every webinar opener is aimed at the wrong person at the wrong stage. Get it right and the entry angle cuts through instantly.

### The Five Levels — Defined for Health Markets

**Level 1 — Unaware**
The avatar does not know they have a problem, or does not connect their symptoms to a treatable condition. They are not searching for solutions. They cannot be reached with problem-focused messaging.

*Health context:* Someone experiencing early fatigue or brain fog but attributing it to stress, aging, or just "how life is." Has not yet connected symptoms to a root cause or considered that there might be a solution.

*Entry angle:* Pattern interrupt. Content that makes them identify themselves as having a problem they didn't know had a name. Education-first. Never sells in the first touch.

*Headline style:* "The real reason you're exhausted all the time (and why your doctor probably missed it)"

**Level 2 — Problem Aware**
The avatar knows they have a problem. They experience it daily. But they do not know solutions exist — or they've given up believing solutions exist.

*Health context:* Has been suffering for years. Has been told by multiple doctors that this is normal, unfixable, or managed-only. Has accepted the problem as permanent. The most emotionally raw avatar — and often the most motivated buyer once the crack of possibility opens.

*Entry angle:* Identify the problem with extreme precision (makes them feel seen). Introduce the possibility that the cause has been misidentified. Do not pitch a solution yet — just open the door.

*Headline style:* "If you've been told your thyroid is 'fine' but you still feel terrible — read this"

**Level 3 — Solution Aware**
The avatar knows solutions exist. They've tried some. They're actively looking for the right one. They are comparing and evaluating.

*Health context:* Has tried functional medicine before, or has researched it, or has tried other alternative approaches. Is not new to the idea but hasn't found one that worked or worked completely.

*Entry angle:* Lead with differentiation. Not "here's what functional medicine can do" — they know that. Lead with what makes this specific expert's approach different from everything else they've tried. The new vehicle must be front and center.

*Headline style:* "Why most functional medicine protocols fail at the root cause level — and what ours does differently"

**Level 4 — Product Aware**
The avatar knows this specific expert or solution exists. They've seen content, maybe been on the email list, maybe watched a webinar before. They need to be convinced this is the right move right now.

*Entry angle:* Proof, urgency, risk reversal. Case studies. Guarantees. Scarcity. Address the objections directly. The question is not whether they're interested — it's why haven't they bought yet.

*Headline style:* "Here's what happened to 47 people who did what you're thinking about doing"

**Level 5 — Most Aware**
The avatar is ready to buy. They know what they want. They just need the right offer presented at the right moment with the right CTA.

*Entry angle:* Direct offer. Make it easy. Clear CTA. No lengthy education needed.

*Headline style:* "Book your assessment — spots this week"

---

### Determining the Primary Awareness Level

The vast majority of health expert cold traffic audiences operate at **Level 2 (Problem Aware)** or **Level 3 (Solution Aware)**. The determination depends on:

**1. The condition or problem being addressed**
- Mainstream conditions (thyroid, diabetes, weight loss, anxiety) → often Level 3 — the avatar has already tried things
- Emerging or less-recognized conditions (mold toxicity, leaky gut, subclinical hormone issues) → often Level 2 — the avatar doesn't know these are real or treatable
- Longevity and optimization → often Level 1-2 — they don't see themselves as having a problem

**2. The expert's marketing history**
- If the expert has been building a warm audience, their retargeting pool is Level 4
- Cold traffic is almost always Level 2-3

**3. What the avatar has already tried**
- If `avatar.previous_solutions_tried` is long and specific → Level 3 or higher
- If it's short or mostly conventional medicine → Level 2

**Extraction question:**
> "When your best patients first find you — do they usually know that something like what you offer exists? Or are they completely new to this approach?"

**Field populated:** `avatar.awareness_level`

**How this flows downstream:** The awareness level is a master variable that the Strategy Layer reads to determine the entry angle for every cold traffic campaign. It sets the tone for the webinar opener, the first line of every ad, and the subject line of the first email in the nurture sequence.

---

## Secondary Avatars

Most health experts have a primary avatar and 1–3 meaningful secondary avatars. These are often:
- A different demographic with the same core problem (men vs. women with the same condition)
- A different stage of the same problem (early vs. advanced)
- A different entry point (referred by a doctor vs. self-diagnosed via Google vs. influenced by social)

**Extraction question:**
> "Is there another type of patient you work with who's meaningfully different from the one you just described — a different age, different condition, different story?"

**Field populated:** `avatar.secondary_avatars` — an array of secondary avatar objects, each with their own name, awareness level, primary symptom, and key false beliefs.

**Builder Layer use:** Secondary avatars don't get their own full dossier at onboarding — but they are flagged so the Content Builder knows to create avatar-specific content variations once the primary avatar engine is running.

---

## Avatar Naming

Every avatar gets a name. Not a segment label — a name. This is not a luxury detail. It is a functional requirement.

When the Builder Layer generates a headline, it is not thinking "write a headline for a middle-aged woman with thyroid problems." It is thinking "write a headline for Exhausted Executive Emily — 45, knows something is wrong, has been told her labs are normal, can't make it through the afternoon without crashing, terrified this is just aging."

The name makes the psychology real and specific. Generic avatar labels produce generic outputs.

**How to name:**
- The name is alliterative (easy to remember and reference across the team)
- The adjective captures the dominant emotional state or primary symptom
- The noun captures either the life role they're motivated by or the context they're in

**Examples:**
- *Exhausted Executive Emily* — professional woman, energy and brain fog
- *Dismissed Denise* — woman who's been told her labs are normal despite clear symptoms
- *Desperate Dad David* — man watching his health deteriorate and motivated by wanting to be present for his family
- *Skeptical Susan* — has tried everything, highest objection level, most valuable to convert
- *Optimization Oliver* — not sick, wants to perform at the highest level, longevity mindset

**Field populated:** `avatar.primary_name`

---

## The Avatar Psychology Output

At the end of Section 4 of the conversation flow, the agent presents the completed avatar profile to the expert. Not as a list of fields — as a narrative brief that feels like a real person.

**Example output:**

> **Primary Avatar: Dismissed Denise**
>
> Denise is 42–55, college-educated, household income $80K+. She's been experiencing fatigue, brain fog, weight gain, and mood instability for 3–7 years. She's been to her GP, probably an endocrinologist, maybe a rheumatologist. Every time, she's told her labs are "in the normal range" or that what she's experiencing is "just stress" or "perimenopause." She's started to believe them — or at least to stop fighting.
>
> She's tried clean eating. She may have tried thyroid supplements or adrenal support she found on Instagram. Nothing moved the needle. Each failed attempt added a layer of "maybe it really is just me."
>
> What she really wants isn't to feel better. She wants to feel like herself again — the version of her that had energy for her kids at dinner, could think clearly at work, felt good in her body. She wants her life back.
>
> She's not going to believe the first thing she hears. She needs to feel completely understood before she'll consider trusting anything new. The moment your messaging names exactly what she's experiencing and names why the things she's tried haven't worked — she'll lean in hard.
>
> She's at Level 2–3 awareness. She knows something is wrong. She's less sure that what you do is different from what she's already tried. Your entire entry sequence is designed to open that gap.

This brief — stored in the dossier, readable by every downstream agent — is more powerful than any field list. When the Content Builder needs to write an ad, it reads this. When the Webinar Builder needs to write the opener, it reads this. When the Email Builder needs to write the subject line of the first email in the nurture sequence, it reads this.

---

## Avatar Data — Flow to Downstream Agents

| Avatar Field | Consuming Agents | How It's Used |
|---|---|---|
| `avatar.awareness_level` | Strategy, All Builders | Determines entry angle for every cold traffic asset |
| `avatar.primary_symptom` | Content Builder, Ad Builder | Primary hook material |
| `avatar.symptoms_list` | Content Builder, Webinar Builder | Secondary hook angles, webinar opener |
| `avatar.language_patterns` | All Builders | Exact phrasing in copy — never paraphrased |
| `avatar.core_fear` | Webinar Builder, Email Builder | Emotional resonance in openers and subject lines |
| `avatar.deepest_desire` | All Builders | The transformation promise — appears in every close |
| `avatar.transformation_identity` | Webinar Builder, Funnel Builder | Close language — who they become |
| `avatar.false_belief_vehicle` | Webinar Builder, Strategy | Secret #1 structure in webinar |
| `avatar.false_belief_internal` | Webinar Builder, Sales Script | Secret #2 + close objection handling |
| `avatar.false_belief_external` | Webinar Builder, Sales Script | Secret #3 + close objection handling |
| `avatar.previous_solutions_tried` | Webinar Builder, Ad Builder | Vehicle doubt setup — what they've tried and why it failed |
| `avatar.buying_triggers` | Strategy, Campaign Planner | Timing and urgency architecture |
| `avatar.objections_primary` | Sales Script, Funnel Builder | Pre-objection handling in close + FAQ |
| `avatar.secondary_avatars` | Content Builder | Content variation briefs |

---

---

## Sub-Agent Architecture — Forward Reference

The avatar psychology extraction behaviors described in this document — all 8 extraction layers plus the 5 Levels of Awareness determination — are owned by the Avatar Psychology Builder sub-agent operating under the Onboarding Lead Agent. The full sub-agent team structure is defined in Step 9 (Agent and Sub-Agent Architecture section) and formalized in Steps 21–22.

*Step 5 of 22 — Avatar Psychology & 5 Levels of Awareness Extraction — v1.0 Draft*
*Next: Step 6 — Offer Architecture Extraction Methodology*
