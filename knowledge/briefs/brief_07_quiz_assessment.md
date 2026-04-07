# AGENT BRIEF #7 — quiz_assessment_best_practice.md
**clinicIQ Knowledge Base | Frameworks Layer**
**Version 1.0 — April 2026**

---

## Overview

This brief instructs the agent writing:
`/home/work/.openclaw/workspace/cliniciq/knowledge/frameworks/quiz_assessment_best_practice.md`

---

## What the Output File Is

The complete intelligence document for building quizzes, assessments, and scored lead magnets for health experts. The Quiz & Assessment Builder sub-agent reads this as its primary operating manual. This is the complete system — not an overview — for building health-specific quizzes that capture leads at high opt-in rates, segment the audience precisely, and route them to the right offer with maximum conversion.

---

## Source Files the Agent Reads

Before writing, read all three completely:

1. `/home/work/.openclaw/workspace/cliniciq/knowledge/avatars/health_patient_avatar_system.md`
   Read specifically: Section 5 (Awareness Levels with full conversion journey) and Section 3 (DISC profiles and decision-making). Quiz routes patients by both systems — the agent must understand them deeply to build scoring and routing logic that works.

2. `/home/work/.openclaw/workspace/cliniciq/knowledge/frameworks/complete_offer_system.md`
   Read completely. The quiz results page bridges awareness to offer — the agent must understand the full offer architecture to know what it's routing toward and how to frame it.

3. `/home/work/.openclaw/workspace/cliniciq/knowledge/frameworks/grand_slam_offer_value_equation.md`
   Read specifically: The Value Equation section and the Dream Outcome section. Quiz result pages speak to dream outcome and perceived likelihood of achievement — the two numerator variables that drive conversion.

---

## Output Path

`/home/work/.openclaw/workspace/cliniciq/knowledge/frameworks/quiz_assessment_best_practice.md`

---

## Format Standard

Match `cross_industry_hook_patterns.md`: section headers, subsections, worked examples throughout, tables for decision trees and scoring structures, the complete template in Section 10 fully written.

---

## Sections to Produce

### Section 1 — Quiz vs. Assessment vs. Scored Assessment: When to Use Each

**Quiz (7–12 questions):**
Psychological profile: fast, game-like, curiosity-driven. The person feels like they're playing, not being evaluated. Emotional register: "I'm curious what I'll find out." Low commitment barrier, high completion rate for cold audiences. Best for: cold traffic lead generation, top-of-funnel first contact. Health naming convention: "discover" or "find out" not "test" or "evaluate" (too clinical). Benchmark opt-in rate for a well-built health quiz: 40–65%.

**Assessment (15–25 questions):**
Psychological profile: diagnostic, serious, valuable. Feels like a professional evaluation. Higher commitment barrier but higher perceived value. Best for: warm traffic, post-webinar, pre-purchase for complex programs. Health naming: "The Comprehensive [X] Assessment" — framed as a professional diagnostic tool. Benchmark opt-in rate: 30–50% with higher lead quality.

**Scored Multi-Dimensional Assessment (25+ questions):**
Psychological profile: thorough, authoritative, genuinely diagnostic. The person feels they just received a real clinical evaluation. Highest commitment, highest perceived value, highest quality leads. Best for: pre-purchase for high-ticket programs ($3K+), post-consultation intake, deep segmentation. Completion creates psychological ownership — the person has invested significant time and is committed to seeing what it produces. Opt-in rates 20–35% but lead quality is highest and close rates are significantly above benchmark.

**Format selection decision tree** — produce as a table:

| Traffic Temperature | Offer Price Point | Avatar Awareness | Recommended Format |
|---|---|---|---|
| Cold | Under $500 | L1–L2 | Quiz (7–12 questions) |
| Cold | $500–$2,997 | L2–L3 | Quiz or Assessment |
| Warm | $500–$2,997 | L3–L4 | Assessment (15–25 questions) |
| Warm/Hot | $3,000+ | L3–L5 | Scored Multi-Dimensional |
| Post-webinar (no purchase) | Any | L4 | Short Assessment (10–15 questions) |

---

### Section 2 — Question Architecture

**The inviolable rule:** Every question must serve one of three functions: (1) score or segment the respondent, (2) build emotional investment through recognition, or (3) personalize the result. If a question serves none — it doesn't belong. Each unnecessary question costs completion rate.

**Question types and their conversion value:**

Binary yes/no: fastest, lowest friction, maximum momentum. Use for: opening questions and commitment-building. The first 2–3 questions of any quiz should be binary — build the "yes" momentum that carries through the opt-in gate.

Multiple choice: primary segmentation vehicle. Each option maps to a result segment or scores a dimension. Critical writing rule: every option must feel like it could be "my answer." If one option is clearly "the good answer" and others are "bad answers," people pick the good answer and the segmentation fails. Options must be written from inside the avatar's perspective — validating, specific, honest.

Symptom checklist (select all that apply): the highest emotional resonance question type for health. The person is actively recognizing themselves. Use for: the peak emotional moment of the quiz — place at questions 4–6 of a 7–12 question quiz. After the checklist, emotional investment is highest. Opt-in conversion at the gate spikes.

Frequency/scale questions: maps to scoring weight. "How often do you experience [symptom]?" with options never/rarely/sometimes/often/daily. Used for: dimensional scoring and severity tier routing.

Identity/aspiration questions: the final question before the opt-in gate. "Which of these best describes where you are right now?" Options are identity statements written from inside the avatar's experience. This question primes the person to see themselves in their result — the optimal state for the opt-in gate.

**Question sequencing rules:**
- Questions 1–3: high-agreement binary or easy multiple choice. Build yes momentum. Never open with the hard emotional question.
- Questions 4–7: escalate to symptom checklist and deeper pain questions. The emotional peak. The person recognizes themselves completely. They are invested and want to know their result.
- Final question: identity/aspiration question. Emotional state of "I need to know my result" — optimal for the gate.

**Validating vs. clinical question tone:**
Validating: "How often do you find yourself needing to push through fatigue to get through a normal day?"
Clinical: "Rate the severity of your fatigue on a scale of 1–10."
Same information. Completely different emotional experience. Always validating.

---

### Section 3 — The Lead Capture Gate

Gate position: always after the final question. Never before the first question (reduces completion AND lead quality). Never mid-quiz.

**Gate page structure:**

Headline: personalized preview using information from the quiz. "Based on your answers, we've identified your primary hormonal pattern. Enter your name and email to see your results." Not: "Enter your email to see your results."

Value exchange statement: 2–3 lines about what specifically their results contain. Not a general promise — the specific insight they're about to receive. "Your results will show you the specific pattern your answers point to, the most likely root cause, and the one protocol change that addresses it directly."

Form fields: name + email only. Phone number optional and added as an optional field after submission — never required at the gate. Phone number in the gate reduces conversion by 20–40%.

Privacy statement: brief and genuine. "Your information is private. We'll never share it or spam you." Directly under the submit button.

CTA button text: "Show Me My Results" / "Reveal My [Assessment Name] Results" / "Get My Personalized Results." Never "Submit" or "Continue."

Mobile gate: name field + email field stacked vertically, full-width inputs, minimum 44px CTA touch target, no horizontal scrolling, no pinch-zoom required.

**Benchmark opt-in rates:**
- Quiz cold traffic, well-built: 40–65%
- Assessment warm traffic: 30–50%
- Scored Multi-Dimensional: 20–35%
Primary fix areas when below benchmark, in order: (1) gate page headline specificity, (2) symptom checklist placement and phrasing, (3) quiz title and frame.

---

### Section 4 — Scoring Logic Systems

**System 1 — Simple Scoring (1 score, 3–5 result tiers):**
Best for: short quizzes (7–10 questions), cold traffic, awareness building.
Structure: each answer option assigned point value. Total score determines result tier.
Example thresholds for 3 tiers across 10 questions: 0–15 = Tier 1, 16–30 = Tier 2, 31–45 = Tier 3.
Tier naming: empowering, specific — never clinical diagnoses, never names that shame the respondent. "The Burnout Pattern" / "The Imbalance Pattern" / "The Depletion Pattern" — not "Severe" / "Moderate" / "Mild."

**System 2 — Weighted Scoring:**
Best for: 10–20 question assessments where different questions have different diagnostic significance.
Structure: questions assigned multipliers. A question about a key symptom gets 2x or 3x weight. Total weighted score determines result tier.
When to use: when clinical knowledge indicates certain symptoms are more diagnostically significant than others. The expert's clinical insight about what is most predictive is encoded as the question weights.

**System 3 — Multi-Dimensional Scoring:**
Best for: 20+ question assessments, high-ticket pre-purchase, deep segmentation.
Structure: questions grouped into 3–5 dimensions, each scored independently. Result is a multi-dimensional profile, not a single tier.
Example dimensions for a hormonal assessment: Cortisol Pattern, Thyroid Pattern, Sex Hormone Pattern, Gut-Hormone Connection, Lifestyle Factors.
Why this converts highest: the person receives a multi-dimensional map of their situation. It feels like a real clinical evaluation, not a personality quiz.
Routing: the combination of dimension scores routes to the most relevant offer framing, email sequence, and webinar angle.

**Tier threshold calibration:** A well-calibrated quiz distributes respondents naturally across tiers. Target: 20–30% in each tier for a 3-tier system. If 80%+ land in one tier, recalibrate thresholds. Genuine segmentation, not everyone receiving the same result.

---

### Section 5 — Results Page Architecture

The highest-conversion page in the entire quiz funnel. Must produce the "this describes me exactly" moment of recognition — then immediately channel that recognition toward the offer.

**The "aha moment" standard:** The results page must make the person feel they received something of genuine value — an insight they couldn't have gotten anywhere else this quickly. Generic results feel like manipulation. Specific, accurate results feel like gratitude and openness.

**Five-element results page structure:**

Element 1 — Result Name and Score (above the fold):
The result tier name — empowering and specific. The score or profile (makes the result feel measured, not arbitrary). A brief emotionally resonant headline: "You're experiencing the most common hormonal pattern in women over 35 — and it's one of the most addressable."

Element 2 — The Recognition Section (the "this is you"):
3–5 specific statements about what this result pattern looks like in daily life. Written from inside the avatar's experience, not from a clinical perspective. The goal: make the person say "how did they know that?" Example: "People with this pattern often describe feeling like they're running on empty by 2pm regardless of how much sleep they got. They frequently wake up between 2–4am, often feel better later in the evening when they should be winding down, and notice their stress response feels out of proportion to the situation." This is the "aha" — not by explaining a diagnosis, but by describing the person's life back to them with accuracy.

Element 3 — The Mechanism Connection:
One paragraph connecting their result pattern to the specific root cause mechanism. Delivers genuine value AND begins building mechanism credibility for the offer. "This pattern is consistently associated with HPA axis dysregulation — the relationship between your brain, your adrenal glands, and your stress hormones. When this system is dysregulated, it creates a predictable cascade: disrupted energy rhythm, disrupted sleep architecture, heightened stress reactivity, and difficulty losing weight regardless of diet."

Element 4 — Case-Matched Social Proof:
One patient story of someone with their exact result pattern. Named (or aliased). Specific condition. Specific previous attempts that failed. Specific protocol. Specific result with timeframe. Not a generic testimonial — a case-matched story that makes the person think "this person had my exact situation." The conversion lift from case-matched vs. generic proof is significant.

Element 5 — The CTA:
One action. Not a hard offer — the next logical step. For most health quiz funnels: webinar registration ("Watch the free training that shows you how to address the [Result Pattern Name] — and exactly what Dr. [Expert Name] recommends for this pattern specifically") or consultation booking for high-ticket. Never a direct hard-sell on the results page — the person just received value, they are not in the buying emotional state yet.

**CTA positioning:** Visible without scrolling on mobile. All five elements designed so the CTA is at or above the fold on a 390px × 844px screen.

---

### Section 6 — Segmentation to Funnel Routing

**Tier 1 (most advanced/most symptomatic):**
Email sequence: urgency-framed. The person's situation is serious and delay is genuinely costly. The mechanism is urgent. The offer framing is direct.
Webinar variant: most direct mechanism and urgency angle.
Offer framing: most direct path to the expert's program. High-ticket consideration appropriate.
Cadence: faster — 3–4 emails in the first 5 days.

**Tier 2 (moderate — typically the largest segment):**
Email sequence: educational bridge — needs to understand the mechanism and why their current path is insufficient before they're ready for the offer. More story. More teaching.
Webinar variant: standard mechanism webinar.
Offer framing: full Value Equation framing — dream outcome, perceived likelihood, time reduction, effort reduction.
Cadence: standard — 2 emails in first 5 days, then 1 per week.

**Tier 3 (early stage/lower severity):**
Email sequence: awareness-building — may not fully understand the significance of their pattern yet. Builds that understanding before presenting the offer.
Webinar variant: "before it gets worse" angle or optimization angle.
Offer framing: long-term value and prevention — the offer protects against where Tier 1 currently is.
Cadence: slower — 1–2 emails in first 5 days, then 1–2 per week.

**DISC profile integration in routing:**
Result tier determines the offer path. DISC profile determines the communication style within that path. A Tier 2 D-profile receives efficient, result-forward email copy. A Tier 2 S-profile receives warm, relationship-oriented copy. Same offer path, different language. The system tags the respondent with both tier and inferred DISC weighting at opt-in.

---

### Section 7 — Health-Specific Question Bank Patterns

**Symptom frequency scale (works in any specialty):**
"How often do you experience [specific symptom]?"
Options: Never / Rarely (once a month or less) / Sometimes (1–2 times a week) / Often (3–4 times a week) / Daily or Almost Daily

Symptoms this pattern works for across specialties:
Afternoon energy crashes, morning stiffness, brain fog, bloating after meals, difficulty falling asleep, waking between 2–4am, mood fluctuations, food cravings (especially sugar/carbs), headaches, joint discomfort, skin reactions, hair thinning, temperature sensitivity, anxiety spikes, difficulty recovering from exercise, weight changes despite consistent diet, digestive irregularity, low motivation, PMS symptoms, heart palpitations.

**Energy and quality-of-life scale:**
"On a typical day, how would you rate your energy by mid-afternoon?"
Options: "I feel great — consistent energy all day" / "I have good energy most of the time with occasional dips" / "I hit a wall around mid-afternoon that's hard to push through" / "My energy is unpredictable — good some days, very low others" / "I struggle with low energy throughout most of the day"

**Duration questions:**
"How long have you been experiencing these symptoms?"
Options: Less than 6 months / 6 months–2 years / 2–5 years / More than 5 years
Why: duration is the strongest predictor of result tier and urgency framing. Also reveals the avatar's relationship with conventional medicine — longer duration = more failed attempts = higher Solution Aware positioning.

**Prior attempts questions:**
"Which of these approaches have you already tried for [condition]?" [select all that apply]
Options include: prescribed medications, dietary changes, supplements/vitamins, previous health programs, functional/integrative medicine practitioners, acupuncture/naturopathy, elimination diets, hormone therapy. 
Why: options selected directly reveal awareness level and inform email routing.

**Identity/aspiration questions:**
"Which of these best describes where you are right now on your health journey?"
Option sets for different specialties:
- Hormonal: "I'm doing everything right and something still isn't working" / "I've given up on conventional medicine and I'm looking for a different path" / "I've had some improvement but I still feel like something important is being missed" / "I'm just starting to realize this might be hormonal" / "I'm managing symptoms but I know I'm not addressing the root cause"
- Gut: "I've tried every diet and my gut still reacts unpredictably" / "I've been told my gut is 'fine' but it clearly isn't" / "I'm starting to connect my gut health to my energy and mood" / "I feel like food is the enemy and I don't know where to start"
- Autoimmune: "I've accepted this is something I'll manage forever — I just want to manage it better" / "I believe there's a root cause but I haven't found the right person to help me find it" / "I recently received a diagnosis and I'm trying to understand my options" / "I've been in remission and I want to keep it that way"

**Questions to never ask:**
- Leading questions that make the person feel judged or inadequate
- Clinical diagnostic language in questions (save for results)
- Questions with one obvious "right" answer and several obvious "wrong" answers
- Questions that feel like sales qualification
- Questions whose answer doesn't affect the result

---

### Section 8 — A/B Test Protocol

**Test priority 1 (highest impact — test first):**
Results page headline — specifically Element 2, "the recognition section." Test: empathy-first framing vs. mechanism-first framing. This single element has the highest impact on results page conversion.
Results page CTA — specific action language and offer framing.

**Test priority 2:**
Quiz title and cold traffic frame — affects click-through and start rate. Test: curiosity-based title vs. direct benefit title.
Question 1 — opening question has the highest impact on completion rate. Test: binary vs. easy multiple choice.
Symptom checklist placement — test question 4 vs. question 6.

**What never to A/B test on launch:**
Gate position (always after final question — not a hypothesis, established conversion best practice).
The scoring model (changes invalidate all accumulating data — requires version replacement, not A/B test).
Number of questions (structural change — same issue).

**Statistical significance minimums:**
For a 5 percentage point conversion rate difference at 95% confidence: approximately 750 completions per variant. For a 3 percentage point difference: approximately 2,000 per variant. Calibrate test duration to typical quiz traffic before calling a winner.

**Learning Loop integration:** Quiz performance data tracked per version: completion rate per question (identify drop-off questions), gate opt-in rate, results page CTA conversion, downstream email open rates by result tier. Layer 4 Learning Loop Agent uses this data to flag optimization opportunities on a monthly review cycle.

---

### Section 9 — Technical Delivery Specification

**Hosting:** clinicIQ infrastructure. URL: [expertdomain.com]/quiz/[quiz-slug] — clean, no tracking parameters visible.

**Progress bar:** Required. Shows question X of Y. Updates instantly on answer. Increases completion rates significantly — gives the person a sense of investment and progress.

**Performance:** Question transitions under 200ms. Results page load under 1 second. Any delay at the opt-in gate kills conversion.

**Mobile first:** All interactions designed for touch. 44px minimum touch targets. No horizontal scrolling. No zoom required. Fully functional and visually correct at 320px width.

**Integration requirements:**
ESP integration: gate form connects directly to ESP, tags subscriber with result tier and DISC profile weight, triggers correct email sequence automatically.
CRM integration: name, email, result tier, and individual question answers pass to CRM for sales team use on high-ticket programs.
Analytics: each question, the gate, and the results page are individual tracked events. Full conversion funnel visible in analytics dashboard.

---

### Section 10 — Complete 10-Question Health Quiz Template

A fully worked example — not described, but written completely and usable as a starting point for any functional medicine general entry-point quiz.

**Quiz Title:** "Discover Your Root Cause Pattern: The 60-Second Quiz That Reveals Why You're Still Not Feeling Better"

**Question 1 (Binary — momentum opener):**
Have you ever had a doctor tell you your lab results look "normal" — even though you still feel far from it?
○ Yes, this has happened to me
○ No, my lab results have flagged something

**Question 2 (Binary — momentum and segmentation):**
Do you experience energy crashes, brain fog, or difficulty recovering from stress on a regular basis?
○ Yes, this is a consistent issue
○ Occasionally, but not regularly

**Question 3 (Multiple choice — awareness level reveal):**
How long have you been dealing with these health challenges?
○ Less than 6 months — this is relatively new for me
○ 6 months to 2 years
○ 2–5 years
○ More than 5 years — this has been going on a long time

**Question 4 (Multiple choice — prior attempts):**
Which of these have you already tried? (Pick the one that best applies)
○ I've mostly followed conventional medical advice — medications, standard testing
○ I've tried dietary changes and supplements on my own
○ I've worked with a functional or integrative medicine practitioner
○ I've tried multiple approaches and nothing has produced lasting results

**Question 5 (Symptom checklist — emotional peak):**
Which of these do you experience regularly? (Select all that apply)
☐ Afternoon energy crash (especially 2–4pm)
☐ Waking up between 2–4am
☐ Difficulty losing weight despite diet and exercise
☐ Brain fog or difficulty concentrating
☐ Feeling wired but tired — exhausted but can't sleep
☐ Mood fluctuations or anxiety spikes
☐ Digestive issues (bloating, irregularity, discomfort after meals)
☐ Hair thinning or slow nail growth
☐ Low motivation even for things you used to enjoy
☐ Temperature sensitivity — always cold or easily overheated

**Question 6 (Frequency scale):**
On a typical day, how would you describe your energy by mid-afternoon?
○ Great — I have consistent energy all day
○ Decent — I have some dips but I manage well
○ I hit a wall and really struggle to push through
○ My energy is unpredictable — sometimes okay, often very low
○ I'm exhausted most of the time regardless of how much I sleep

**Question 7 (Multiple choice — depth of impact):**
How much is this affecting your daily life?
○ Mild impact — I notice it but I'm functioning well
○ Moderate impact — it's affecting my productivity and how I feel most days
○ Significant impact — it's affecting my relationships, my work, and my quality of life
○ Severe impact — this has changed who I am and what I'm able to do

**Question 8 (Multiple choice — specificity of root cause understanding):**
What do you believe is the primary cause of how you're feeling?
○ I honestly don't know — that's what I'm trying to figure out
○ I think it's stress and lifestyle — I just need to manage better
○ I suspect a hormonal or thyroid issue that hasn't been properly identified
○ I believe there's a root cause that conventional testing isn't catching
○ I've been told a diagnosis but I'm not sure the treatment is addressing the real problem

**Question 9 (Multiple choice — goal specificity):**
What would "better health" look like for you — what's the one thing you most want back?
○ Consistent, reliable energy throughout the day
○ A clear head — no more brain fog or difficulty focusing
○ A healthy weight without constant restriction
○ Sleeping through the night and waking rested
○ Feeling like myself again — emotionally stable and motivated

**Question 10 (Identity/aspiration — final question):**
Which of these best describes where you are right now?
○ I'm just starting to realize something deeper might be going on
○ I know something is wrong but I haven't found the right answers yet
○ I've been trying to figure this out for years and I'm ready to get serious
○ I've given up on conventional medicine — I need a completely different approach
○ I know what I need to do but I can't seem to make it stick

---

**Scoring Logic (Simple 3-Tier):**

Score ranges are determined by responses to questions 2, 5, 6, 7, and 8 (the highest-diagnostic questions). Questions 1, 3, 4, 9, and 10 are used for segmentation and routing, not primary scoring.

Tier 1 — The Deep Depletion Pattern (highest severity): 5+ symptoms in Q5, energy at the two lowest options in Q6, significant or severe impact in Q7.
Tier 2 — The Hidden Imbalance Pattern (moderate): 3–4 symptoms in Q5, mid-range energy in Q6, moderate impact in Q7.
Tier 3 — The Early Signal Pattern (early stage): 1–2 symptoms in Q5, decent energy in Q6, mild impact in Q7.

---

**Results Pages:**

**Tier 1 — The Deep Depletion Pattern**

Result headline: "You're experiencing the Deep Depletion Pattern — and your body has been sending signals for a long time."

Recognition section: "People with this pattern often describe feeling like they've been running on reserves for months or years. The 2pm crash isn't occasional — it's predictable. Sleep doesn't feel restorative. The weight isn't moving despite doing everything 'right.' And the frustrating part is that your labs often come back 'normal' — leaving you feeling dismissed and alone with symptoms that are very real. What you're experiencing is real. And it has a root cause."

Mechanism connection: "This pattern consistently points to dysregulation in the HPA axis — the communication network between your brain, adrenal glands, and every other hormone system in your body. When this network is under sustained stress, it creates a downstream cascade that affects cortisol rhythm, thyroid conversion, sex hormones, blood sugar regulation, and immune function simultaneously. Standard labs don't catch it because they're looking at each system in isolation rather than the pattern connecting them."

Social proof: "[Patient name], a 47-year-old functional medicine patient, had been dealing with this exact pattern for 6 years and been told repeatedly that her labs were normal. In 90 days of addressing the root HPA axis dysfunction, her energy stabilized, her sleep improved, and she lost 14 lbs without changing her diet. 'I finally feel like someone was actually listening to what my body was telling them.'"

CTA: "Watch Dr. [Expert Name]'s free training: The Deep Depletion Solution — exactly how to address the root pattern your symptoms have been pointing to." [Register for Free Training →]

---

**Tier 2 — The Hidden Imbalance Pattern**

Result headline: "You're experiencing the Hidden Imbalance Pattern — the pattern most conventional approaches completely miss."

Recognition section: "People with this pattern often feel like something is slightly off, but they can't put their finger on exactly what. Energy is inconsistent — good some days, surprisingly low on others. Sleep is okay but not great. The scale moves in the wrong direction despite reasonable effort. Your instinct that something deeper is going on is correct. The pattern you're experiencing typically has a specific root cause that standard evaluation isn't designed to find."

Mechanism connection: "This pattern commonly involves early-stage HPA axis dysregulation combined with sluggish thyroid conversion — a combination that can exist for years before showing up clearly on standard labs. The good news: at this stage, it responds very well to root cause intervention. Addressing it now is significantly easier than waiting until the pattern deepens."

Social proof: "[Patient name], 39, had been feeling 'off' for about two years — not sick enough to sound credible to her doctor, but not well enough to feel like herself. Six months of root cause work resolved the pattern entirely. 'I had no idea how much better I could feel until I actually felt it.'"

CTA: "Watch Dr. [Expert Name]'s free training: How to identify and address the Hidden Imbalance Pattern — before it deepens into something harder to reverse." [Register for Free Training →]

---

**Tier 3 — The Early Signal Pattern**

Result headline: "You're experiencing the Early Signal Pattern — your body is trying to tell you something before it becomes harder to hear."

Recognition section: "People with this pattern are functioning well most of the time — but there are signals that something is beginning to shift. The occasional energy dip. The sleep that's not quite as restorative as it used to be. The body that's a little less responsive than it was a few years ago. These signals are not random. They are early indicators of a root cause pattern that, addressed now, is very straightforward to resolve."

Mechanism connection: "Early signal patterns typically indicate the beginning of HPA axis stress response — often triggered by cumulative lifestyle stressors that haven't yet created obvious dysfunction but are beginning to shift the underlying physiology. The advantage of being here: you have a window to address this proactively, before it becomes the pattern the other result tiers describe."

Social proof: "[Patient name], 34, came in with mild but persistent symptoms — nothing dramatic, just 'not feeling quite right.' Identifying and addressing the early pattern took about 60 days. 'I'm so glad I didn't wait until it got worse. I feel better than I have in years.'"

CTA: "Watch Dr. [Expert Name]'s free training: Understanding the root cause pattern behind your early signals — and the proactive approach that prevents them from deepening." [Register for Free Training →]

---

**Email Routing Map:**

| Result Tier | ESP Tag | Sequence Name | First Email Subject Line |
|---|---|---|---|
| Tier 1 | deep-depletion | Deep Depletion Sequence | "Your quiz results — and what they mean for your health right now" |
| Tier 2 | hidden-imbalance | Hidden Imbalance Sequence | "What your quiz results are pointing to (and why most people miss this)" |
| Tier 3 | early-signal | Early Signal Sequence | "Your quiz results revealed something worth paying attention to" |

All three sequences lead to the same webinar. Tier 1 sequences receive urgency framing. Tier 2 sequences receive educational bridge framing. Tier 3 sequences receive proactive/prevention framing.

---

*clinicIQ Knowledge Base — Frameworks Layer*
*brief_07_quiz_assessment.md — Version 1.0*
*April 2026*
