# clinicIQ — Layer 1: Onboarding Agent — Step 4: Voice DNA Extraction Methodology
**Version 1.0 — Draft**
*Step 4 of 22 | Depends on: Step 1 (Agent Description), Step 2 (Data Schema), Step 3 (Conversation Flow)*

---

## Purpose

Voice DNA is the most important section in the entire clinicIQ dossier for one reason: every single word the platform ever writes for this expert runs through it. A weak Voice DNA profile produces generic outputs that sound like AI. A strong Voice DNA profile produces outputs the expert reads back and says "that sounds exactly like me."

This document defines how Voice DNA is extracted — passively throughout the session, actively confirmed in Section 2 of the flow, and continuously enriched over time as the platform builds more content and tests it in the wild.

---

## What Voice DNA Actually Is

Voice DNA is not a style guide. It is not a list of adjectives ("professional, warm, authoritative"). It is a living, precise fingerprint of how a specific human being communicates — the patterns so consistent and distinctive that they can be reproduced reliably by an AI across any content type, any platform, any format.

A complete Voice DNA profile answers three questions:
1. **How do they sound?** — rhythm, sentence structure, formality, pace
2. **What do they say?** — vocabulary, signature phrases, topics they return to, things they never say
3. **How do they make people feel?** — emotional register, warmth level, authority style, humor

When all three are captured accurately, every output the Builder Layer produces — ads, emails, webinar scripts, social posts, VSL copy, podcast scripts — reads like the expert wrote it on their best day.

---

## The Two Extraction Modes

### Mode 1 — Passive Real-Time Capture (runs throughout entire session)
The agent is analyzing voice from the first message. This is invisible to the expert — they're just having a conversation. The agent is simultaneously listening and building.

### Mode 2 — Active Confirmation (Section 2 of the conversation flow)
After enough conversation has happened (typically after the Expert Personal Story and Clinical Philosophy sections), the agent surfaces the Voice DNA profile it has built and asks the expert to confirm, adjust, or enrich it.

These two modes work together. Passive capture builds the raw profile. Active confirmation refines it into a locked, expert-approved fingerprint.

---

## Mode 1: Passive Real-Time Capture

### What the Agent Tracks from the First Message

#### 1. Sentence Rhythm
How does the expert naturally construct sentences? This is one of the most distinctive voice signals and one of the hardest to fake when it's missing.

**Patterns to detect:**
- **Short and punchy** — 5–10 word sentences. Declarative. No hedging. Often incomplete sentences used for emphasis. *("That's the problem. Nobody's looking at the root cause. They're just chasing symptoms.")*
- **Long and flowing** — Complex sentences with multiple clauses, building an argument or painting a picture. *("When I look at a patient who's been told they'll be on thyroid medication for life, the first thing I want to understand is whether anyone has ever looked at what's driving the autoimmune response in the first place.")*
- **Mixed / dynamic** — Alternates between short punchy statements and longer explanatory stretches. Often the most compelling voice style — short sentences land the point, long sentences build the case.

**Why it matters:** The Builder Layer needs to match this rhythm or every output will feel wrong to the expert. A naturally punchy communicator reading flowing, complex AI copy will immediately feel "that's not me."

#### 2. Vocabulary Register
What level of language does the expert default to?

**Signals to detect:**
- **Clinical/technical** — Uses medical terminology comfortably without translating it. Trusts the audience to follow or wants to signal expertise. *(mitochondrial dysfunction, dysbiosis, HPA axis dysregulation)*
- **Plain-language translator** — Consistently bridges clinical concepts into plain language. Shows high patient-communication intelligence. *("Your mitochondria — think of them as the battery in every cell...")*
- **Street-level casual** — Drops formality entirely. Contractions everywhere. Colloquialisms. Sometimes profanity. Energy feels like a smart friend, not a doctor. *("Look, the whole thing is basically rigged against you getting well.")*
- **Mixed professional** — Professional but accessible. Clinical credibility with warmth. The most common register for high-performing health experts.

#### 3. Formality Level
Separate from vocabulary — this is about how they relate to the person they're talking to.

**Signals:**
- Do they use "you" or "one"?
- Do they use contractions? ("you're" vs. "you are")
- Do they use first names in examples?
- Do they talk about patients as "they" or "people like you"?
- Is the tone peer-to-peer or authority-to-student?

#### 4. Emotional Register
How much feeling do they bring to their communication?

**Signals:**
- **High emotional** — Expresses frustration with conventional medicine, genuine excitement about results, visible empathy for patients. The emotion is specific and grounded, not performed.
- **Measured/analytical** — Presents ideas and evidence with professional distance. Emotion is implied but not stated. The expertise is the warmth.
- **Mission-driven** — Language carries weight. They talk about what they do as if it matters beyond the transaction. Words like "broken system," "deserve," "fight," "change."

#### 5. Humor Level and Style
Most health experts don't lead with humor but many have a natural dry wit that makes them magnetic. Missing it in outputs makes them sound flatter than they are.

**Signals:**
- Self-deprecating references
- Irony about conventional medicine or the healthcare system
- Warmth-humor (laughing with patients rather than at situations)
- Zero humor (totally fine — do not insert it)

#### 6. Conviction vs. Hedging Ratio
This is a major differentiator between good and great health expert communication.

**High conviction:** *"This is the root cause. Full stop."*
**Hedging:** *"In my experience, it seems like it might potentially be related to..."*

**Why it matters:** Experts who communicate with conviction convert better. If an expert naturally hedges, the Builder Layer notes it — but outputs are calibrated toward the more convicted end of their range to maximize performance, flagged for their review.

#### 7. Signature Phrases
Words or phrases the expert uses more than once in the same session are almost always signature phrases. These are gold.

**Examples from the health space:**
- *"Root cause"* vs. *"upstream problem"* vs. *"the driver"*
- *"Get to the bottom of it"*
- *"The body knows how to heal"*
- *"Nobody's asking the right questions"*
- *"That's just not true"* (said about conventional medicine claims)
- *"Most doctors won't tell you this"*

The agent flags every repeated phrase. At confirmation, the expert is shown these and asked which feel most authentically theirs.

#### 8. What They Never Say
Equally important. Some experts have hard vocabulary preferences — words they find reductive, inaccurate, or beneath them. Missing these in outputs creates friction every time.

**Common avoidances in functional medicine:**
- *"Wellness"* (too vague/spa-adjacent for clinical practitioners)
- *"Holistic"* (overused, often meaningless)
- *"Fix"* (some prefer "heal" or "restore" — "fix" sounds mechanical)
- *"Patients"* vs. *"clients"* (strong preference either direction)
- Disease names used as permanent identity labels (*"a diabetic"* vs. *"someone with blood sugar dysregulation"*)

The agent listens for corrections — whenever the expert reframes a word or says "I don't love that term," that's a vocabulary avoidance signal.

#### 9. Authority Style
How does the expert establish credibility?

**Credential-first:** Leads with degrees, publications, clinical experience. Authority comes from proof.
**Results-first:** Leads with patient outcomes. Authority comes from what works.
**Story-first:** Leads with narrative — their own journey or a patient's. Authority comes from lived experience.
**Teaching-first:** Leads with explanation. Authority comes from the quality of the insight.

Most experts have a dominant style with a secondary. The Builder Layer uses this to determine how to open content — what comes first in an ad, an email subject line, a social post.

#### 10. Energy Markers
Where does the expert's language accelerate? Where do sentences get shorter? Where do they use emphasis or exclamation? This is where their passion lives — and passion is the most authentic brand content that exists.

**The agent tracks:** which topics caused a visible shift in response energy, length, or expressiveness. These topics are flagged as high-passion areas — Builder Layer defaults to pulling from these zones for content that needs to feel alive.

---

## Mode 2: Active Confirmation

After the Expert Personal Story and Clinical Philosophy sections are complete (typically 20–30 minutes into the session), the agent surfaces the Voice DNA profile it has built.

### The Confirmation Presentation

The agent presents the Voice DNA profile as a narrative, not a form. It should feel like being seen — not being processed.

**Example presentation:**

> "I've been paying attention to the way you communicate throughout our conversation — not just what you said, but how you said it. Here's what I picked up. Tell me if this feels right.
>
> You communicate with a lot of conviction — you make declarative statements rather than hedging, which is going to make your content land hard. Your rhythm alternates between short punchy points and longer explanatory stretches — you make a claim, then build the case. That's a really strong natural style.
>
> Your vocabulary sits at the intersection of clinical credibility and plain-language translation — you use technical terms but you always bridge them. That's rare and it's powerful.
>
> I noticed you say 'root cause' and 'nobody's asking the right questions' more than once — those feel like signature phrases. And you've never used the word 'holistic' — which tells me you're not positioning yourself in that space.
>
> Does this feel like you? Anything I got wrong or missed?"

### What the Confirmation Step Produces

After the expert responds, the agent finalizes and locks the following Voice DNA fields from the schema:

| Field | What Gets Confirmed |
|-------|-------------------|
| `voice.tone_primary` | The dominant tonal quality (authoritative, empathetic, urgent, educational, conversational, inspirational) |
| `voice.tone_secondary` | The secondary tonal layer |
| `voice.formality_level` | High / Medium / Low |
| `voice.sentence_rhythm` | Short-punchy / Long-flowing / Mixed-dynamic |
| `voice.signature_phrases` | Array of confirmed recurring phrases |
| `voice.words_they_use` | Vocabulary preferences confirmed by expert |
| `voice.words_they_avoid` | Hard avoidances confirmed or surfaced |
| `voice.humor_level` | None / Dry / Warm |
| `voice.emotional_register` | Full description of emotional style |
| `voice.sample_extracts` | 3–5 verbatim quotes pulled from the session — the highest-signal samples of their authentic voice |

### The Sample Extracts Field
This is the most important field in the entire Voice DNA section. When the Builder Layer generates content, it reads these verbatim quotes from the expert and uses them as the calibration standard — the target to match.

The agent selects the 3–5 quotes from the session that are most:
- Distinctive (nobody else would say it that way)
- Emotionally alive (high energy, high conviction, or high empathy)
- Structurally representative (shows their natural sentence construction)

**Example extracts:**
- *"The body already knows how to heal. Our job is just to stop getting in the way."*
- *"Nobody's looking at why the immune system is attacking itself in the first place. They're just trying to quiet it down with drugs."*
- *"I've had patients come off 20-year-old prescriptions in 90 days. Not because I'm a miracle worker — because we finally addressed the actual problem."*

These three sentences tell the Builder Layer almost everything it needs to know about tone, rhythm, vocabulary, conviction level, and authority style — without any of the formal field labels.

---

## Voice DNA Enrichment Over Time

The initial Voice DNA profile is built from a 20–90 minute conversation. It is good. But it gets dramatically better over time as the platform builds more content and that content is tested and approved.

### Enrichment Sources

**1. Content approval patterns**
When an expert consistently approves certain types of outputs and consistently edits others, those patterns update the Voice DNA profile. If they always soften aggressive language, the profile adjusts. If they always sharpen passive constructions, the profile adjusts.

**2. Organic content performance**
When certain content pieces dramatically outperform — high engagement, high shares, high comments — the Voice DNA of those pieces gets extracted and added as high-weight samples. The market is telling us what version of this expert's voice resonates most. Layer 4 feeds this back.

**3. Direct voice uploads**
At any time, the expert can add to their Voice DNA by:
- Uploading existing content they love (blog posts, podcast transcripts, old emails)
- Recording a voice note that the agent transcribes and analyzes
- Pointing to specific social posts or videos they want the platform to sound more like

**4. Ongoing conversation sessions**
Every time the expert interacts with clinicIQ — answering update questions, requesting new content, refining strategy — the agent continues passively collecting voice data. The dossier deepens without the expert having to do anything intentional.

### The Compounding Advantage
After 6 months of use, the clinicIQ Voice DNA profile for an expert is more accurate than anything a human copywriter could build from interviews — because it has been calibrated against real performance data, real approvals, and real audience response. This is the moat. No new tool can replicate it without starting over.

---

## Voice DNA for Content Type Variations

One important nuance: most experts communicate differently across contexts. Their email voice is not identical to their ad voice. Their podcast voice is not their Instagram voice. Voice DNA captures a base profile — but the Builder Layer applies context-specific calibrations on top of it.

### Context Calibrations

| Content Type | Calibration Applied |
|---|---|
| Organic social (Instagram, Facebook) | Base voice + personal/conversational register. First person, present tense, emotionally warm. |
| Paid ads | Base voice + elevated urgency and directness. Conviction dialed up. Hooks sharper than organic. |
| Email (nurture sequence) | Base voice + peer-to-peer intimacy. Feels like a letter, not a broadcast. |
| Webinar / VSL script | Base voice + teaching register. More structured, more evidence, more narrative arc. |
| Podcast | Base voice + conversational depth. Longer sentences acceptable. More tangents allowed. |
| Website copy | Base voice + authority register. Credentials and credibility signals more prominent. |
| SMS | Base voice compressed to its most essential. One idea. Maximum 3 sentences. |

The expert never has to configure these calibrations — they are built into the Builder Layer and applied automatically. But the base Voice DNA must be strong for all of them to work.

---

## Voice DNA Quality Scoring (Phase 2)

As part of the gamification and dossier scoring system, Voice DNA quality contributes to the overall Dossier Score. The Voice DNA sub-score is calculated as follows:

| Signal | Score Contribution |
|---|---|
| All 10 schema fields populated | 40% |
| 3+ sample extracts captured | 20% |
| Expert confirmed (not just agent-generated) | 20% |
| Signature phrases confirmed | 10% |
| Words-to-avoid list populated | 10% |

**Achievement trigger:** When `voice.sample_extracts` reaches 3+ confirmed extracts and all core fields are confirmed, the 🗣️ **Voice Locked** achievement fires.

---

## Voice DNA Failure Modes — What to Avoid

These are the most common ways Voice DNA goes wrong and what prevents each:

| Failure Mode | Cause | Prevention |
|---|---|---|
| Generic outputs that sound like AI | Sample extracts not captured or too generic | Always capture verbatim quotes from the session. Never use paraphrased summaries as sample extracts. |
| Voice that sounds like the expert on a bad day | Session captured a low-energy or defensive moment | Flag session energy in the dossier. Schedule enrichment session when expert is in high-energy mode. |
| Inconsistent voice across content types | Context calibrations not applied | Builder Layer must always apply context calibration on top of base Voice DNA — never output raw base voice directly. |
| Expert keeps editing the same things | Voice DNA profile has a systematic gap | Track edit patterns. Update the profile. Three consistent edits in the same direction = a Voice DNA update. |
| Outputs that are technically accurate but don't feel right | Emotional register not captured | Prioritize the sample extracts field. If the emotional register is in the extracts, the outputs will feel right even when other fields are approximate. |

---

## Relationship Between Voice DNA and Visual DNA

Voice DNA and Visual DNA are separate sections in the schema, but they are not independent. They are two expressions of the same underlying brand identity.

**The connection:** The same expert who communicates with short punchy conviction will almost certainly have a visual brand that is clean, direct, and high-contrast rather than soft, layered, and pastel. The agent uses Voice DNA signals as early input for Visual DNA aesthetic descriptions — before any brand assets are uploaded.

**Example inference chain:**
- Expert voice: short sentences, clinical vocabulary, high conviction, no humor
- → Visual DNA inference: clean and clinical aesthetic, likely dark or neutral palette, photography style likely professional/documentary, no warm lifestyle imagery
- → Builder Layer receives both Voice and Visual DNA as consistent signals

This inference is confirmed when assets are uploaded — but it means the Builder Layer can produce visually consistent outputs from day one, even before a single brand file arrives.

---

---

## Sub-Agent Architecture — Forward Reference

The Voice DNA extraction behaviors described in this document — passive real-time capture, active confirmation, and ongoing enrichment — are owned by the Voice DNA Analyst sub-agent operating under the Onboarding Lead Agent. The full sub-agent team structure is defined in Step 9 (Agent and Sub-Agent Architecture section) and formalized in Steps 21–22.

*Step 4 of 22 — Voice DNA Extraction Methodology — v1.0 Draft*
*Next: Step 5 — Avatar Psychology & 5 Levels of Awareness Extraction*
