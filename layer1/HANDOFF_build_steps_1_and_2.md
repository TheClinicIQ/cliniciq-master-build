# HANDOFF — Build Step 1 and Step 2 for clinicIQ Layer 1

> ⚠️ **HISTORICAL DOCUMENT** — Steps 1 and 2 have been built, audited, and revised (v1.1).
> This handoff brief was the original build instruction. Field count references to "164" in this file are superseded by the actual schema: **198 fields** across 14 sections.
> Canonical files: `step1_onboarding_lead_agent.md` (v1.1) and `step2_expert_dossier_data_schema.md` (v1.1).

**Written by:** Previous session (context limit reached)
**For:** Next fresh session
**Date:** 2026-04-07
**Priority:** HIGH — developer is waiting on these files

---

## The Situation

Steps 1 and 2 of Layer 1 were never written. Every other step (3–7) exists and is in the GitHub repo. The developer noticed the gap. We need to build both files now and push them to GitHub.

**GitHub remote:** `https://github.com/TheClinicIQ/cliniciq-master-build.git`
**Branch:** `main`

---

## What to Read First (Before Writing Anything)

Read these files completely before writing a single line:

1. `/home/work/.openclaw/workspace/cliniciq/layer1/step3_conversation_flow_architecture.md` — full read
2. `/home/work/.openclaw/workspace/cliniciq/layer1/step7_onboarding_output_payload_handoff.md` — full read
3. `/home/work/.openclaw/workspace/cliniciq/layer1/step4_voice_dna_extraction_methodology.md` — full read
4. `/home/work/.openclaw/workspace/cliniciq/layer1/step5_avatar_psychology_5_levels_awareness.md` — full read
5. `/home/work/.openclaw/workspace/cliniciq/layer1/step6_offer_architecture_extraction.md` — full read

This is non-negotiable. The format, depth, tone, and terminology of Steps 1 and 2 must match Steps 3–7 exactly. You are filling a gap in an existing document set — not starting from scratch.

---

## Output Files to Create

```
/home/work/.openclaw/workspace/cliniciq/layer1/step1_onboarding_lead_agent.md
/home/work/.openclaw/workspace/cliniciq/layer1/step2_expert_dossier_data_schema.md
```

---

## File 1: step1_onboarding_lead_agent.md

### What This File Is
The complete knowledge and skill description of the Onboarding Lead Agent — the first agent every new expert interacts with when they join the clinicIQ platform. Step 3 already references this file ("Depends on: Step 1 (Agent Description)") so this file is the definition that Steps 3–7 were built on top of.

### Header Format (match exactly)
```
# clinicIQ — Layer 1: Onboarding Agent — Step 1: Onboarding Lead Agent — Knowledge & Skill Description
**Version 1.0 — Draft**
*Step 1 of 22 | Layer 1: Onboarding Agent*
```

### Sections to Include (write all of these — full depth, no truncation)

**1. Purpose**
What the Onboarding Lead Agent is, what its single job is, and why it is the most important agent in the entire platform. The first interaction determines whether the expert trusts the system. Everything downstream — all 168 agents, all outputs, all intelligence — runs on the dossier this agent builds.

**2. Agent Identity and Role**
- Full name: Onboarding Lead Agent
- Layer: Layer 1
- Step: Step 1 of 22
- Role type: Lead Agent (orchestrates sub-agents; does not run sub-tasks itself)
- Activation trigger: New expert joins clinicIQ platform / first session begins
- Session types: Fast-Start Mode (20–30 min) and Full Deep-Dive Mode (60–90 min) — reference Step 3 for full session architecture
- Primary output: The Expert Dossier (164 fields across 14 sections) — reference Step 2 for full schema
- Handoff: Passes completed payload to Layer 2 Strategy Agents — reference Step 7 for full handoff protocol

**3. What the Onboarding Lead Agent Knows**
The complete knowledge base the agent arrives with before the first session. This is what makes the agent feel like an expert, not a form:

- Deep knowledge of health expert business models: telehealth, brick-and-mortar, hybrid, group practice, solo practitioner, course/program creator
- The full spectrum of health niches: functional medicine, integrative medicine, naturopathic, chiropractic, health coaching, nutrition, hormones, gut health, autoimmune, longevity, mental health, weight management, women's health, men's health
- The complete direct response and health marketing framework: Russell Brunson (Perfect Webinar, Hook-Story-Offer, New Vehicle), Alex Hormozi ($100M Offers — 4-tier stack, Grand Slam Offer), Eugene Schwartz (5 Levels of Awareness), Dan Kennedy, John Carlton (specificity principle), Gary Halbert, Gary Bencivenga
- Avatar psychology for health buyers: the shame cycle, the failed-treatment history, the "told it's normal" pattern, the loss of identity, the fear of never getting better
- Common offer structures, price points, and fulfillment models in health
- Compliance landscape: FTC health claims rules, FDA restrictions, state medical board advertising standards, testimonial disclaimers
- What good Voice DNA looks like vs. generic AI output
- The platform architecture: what Layer 2, Layer 3, and Layer 4 do with the dossier — so it can explain to the expert what their answers will be used for

**4. The Sub-Agent Team**
The Onboarding Lead Agent does not do everything itself. It orchestrates a team of specialized sub-agents that run in the background during the session. List and describe each:

- **Web Scraper Sub-Agent** — Before the first session begins, scrapes the expert's website, social profiles, podcast listings, YouTube channel, and any existing lead magnets. Pre-populates ~20–40 fields in the dossier before the expert answers a single question. The expert arrives to a partially-built dossier — this is the "progress endowment" principle from Step 3.
- **Voice DNA Analyst Sub-Agent** — Runs in parallel throughout the entire conversation. Passively captures voice patterns from every message the expert sends — sentence rhythm, vocabulary register, emotional warmth, humor signals, signature phrases. Produces the Voice DNA profile surfaced in Section 2 of the conversation flow. Full methodology in Step 4.
- **Avatar Psychology Builder Sub-Agent** — Processes the expert's answers about their ideal patient and builds the full psychological avatar profile including awareness level determination. Full methodology in Step 5.
- **Offer Architecture Builder Sub-Agent** — Processes the expert's answers about their offers and builds the complete 4-tier offer stack, identifying gaps and generating proposed missing tiers. Full methodology in Step 6.
- **Proof Bank Miner Sub-Agent** — Detects patient transformation stories surfacing anywhere in the conversation (not just in the Proof Bank section) and captures them in structured format. Extracts: before state, interventions tried, turning point, result, timeline, any direct quotes.
- **Story Miner Sub-Agent** — Specific to the expert's own personal health journey and mission origin story. Extracts the full arc: before state, darkest moment, discovery, transformation, what they want others to know.
- **Silent Diagnostician Sub-Agent** — Runs throughout the session identifying gaps, risks, and opportunities that the expert doesn't explicitly raise. Produces the Silent Diagnosis payload delivered to Layer 2. Examples: missing offer tiers, thin proof bank, weak positioning, unnamed mechanism, compliance risks. Full Silent Diagnosis format in Step 7.
- **Dossier Assembler Sub-Agent** — Takes all outputs from all other sub-agents and assembles them into the two payload formats: the structured data object (machine-readable) and the Expert Dossier Brief (human-readable narrative). Full payload format in Step 7.
- **Progress Endowment Engine Sub-Agent** — Manages the gamification layer: dossier completion score calculation, achievement unlocks, real-time score updates. Full gamification architecture in Step 3.

**5. Operating Principles**
The core behavioral rules the Onboarding Lead Agent always follows — regardless of session type, expert personality, or content:

- Never asks more than one question at a time
- Never stalls on a blank or weak answer — generates immediately and presents for approval
- Never makes the expert feel like they're filling out a form — always conversational
- Never re-asks a question already answered, even partially
- Always has something ready — the expert's job is to approve or adjust, not to originate every answer
- Voice-mirrors from the first message — adapts formality, pace, and vocabulary to match the expert's register
- Always shows what it built, not just asks for input — demonstrates intelligence in real time
- Treats every answer as richer than it appears — mines for multiple field fills from single responses
- Celebrates high-value captures (stories, mechanism naming, One Big Domino) in the moment — makes the expert feel the value accruing

**6. Quality Standard for the Dossier**
What "done" looks like. The Onboarding Lead Agent is responsible for producing a dossier that:
- Is specific enough that a copywriter who has never met this expert can write in their voice
- Is deep enough that an ad creative team can produce an entire cold traffic campaign without asking another question
- Is accurate enough that the expert reads the Expert Dossier Brief and says "that's exactly me"
- Is complete enough (Fast-Start minimum: ~55 confirmed fields) that Layer 2 can produce first meaningful outputs immediately

**7. What Happens After the Session**
Brief description of what the dossier enables:
- Immediate: Layer 2 Brand Strategy and Growth Strategy Agents activate
- Short-term: Layer 3 Builder Agents have everything they need to produce ads, emails, funnels, webinar scripts, social content
- Ongoing: The dossier is a living document — every session adds to it, every output enriches it, every performance data point sharpens it
- Long-term: The platform's intelligence compounds over time — the more the expert uses clinicIQ, the more accurate every output becomes

**8. Cross-References**
- Step 2 — Expert Dossier Data Schema (the 164-field schema this agent populates)
- Step 3 — Conversation Flow Architecture (how the session runs)
- Step 4 — Voice DNA Extraction Methodology (how Voice DNA is captured)
- Step 5 — Avatar Psychology Extraction (how the avatar is built)
- Step 6 — Offer Architecture Extraction (how the offer stack is built)
- Step 7 — Onboarding Output Payload & Handoff (what the agent produces and how it's passed to Layer 2)

### Footer Format (match exactly)
```
*Step 1 of 22 — Onboarding Lead Agent — Knowledge & Skill Description — v1.0 Draft*
*Next: Step 2 — Expert Dossier Data Schema*
```

### Length Target
~400–550 lines. Match the depth of Step 3 and Step 7. No section should be abbreviated. Every sub-agent needs a full description. Every operating principle needs a full sentence. This is an operational document, not a summary.

---

## File 2: step2_expert_dossier_data_schema.md

### What This File Is
The complete 164-field data schema for the Expert Dossier — the single most important data structure in the entire clinicIQ platform. Every agent in every layer reads from this schema. Every field defined here flows into at least one downstream output.

Step 3 references this as "Step 2 (Data Schema)" and says the dossier has "164 fields across 14 sections." Step 7 lists all 14 section names and the field counts. Step 7's structured data object shows the exact section keys. This file defines what goes inside each of those sections.

### Header Format (match exactly)
```
# clinicIQ — Layer 1: Onboarding Agent — Step 2: Expert Dossier Data Schema
**Version 1.0 — Draft**
*Step 2 of 22 | Depends on: Step 1 (Agent Description)*
```

### The 14 Sections and Their Field Counts

From Step 7 (structured data object) and Step 3 (Fast-Start vs. Full Deep-Dive coverage table):

| # | Section Name | Schema Key | Approx Fields |
|---|---|---|---|
| 1 | Identity & Practice | `identity` | ~12 fields |
| 2 | Voice DNA | `voice_dna` | ~15 fields |
| 3 | Visual DNA | `visual_dna` | ~10 fields |
| 4 | Avatar Psychology | `avatar_psychology` | ~20 fields |
| 5 | Problems → Root Cause → New Vehicle Map | `root_cause_map` | ~12 fields |
| 6 | Clinical Philosophy | `clinical_philosophy` | ~10 fields |
| 7 | Offer Architecture | `offer_architecture` | ~21 fields |
| 8 | Perfect Webinar Raw Material | `webinar_raw_material` | ~15 fields |
| 9 | Proof Bank | `proof_bank` | ~11 fields |
| 10 | Competitive Landscape | `competitive_landscape` | ~8 fields |
| 11 | Content Audit & Existing Assets | `content_audit` | ~13 fields |
| 12 | Dream Practice Vision & Traffic Reality | `dream_vision_traffic` | ~14 fields |
| 13 | Business Context & Growth Intelligence | `business_context` | ~11 fields |
| 14 | Expert Personal Story | `expert_personal_story` | ~7 fields |
| | **TOTAL** | | **~164 fields** |

Total must reach 164. Distribute fields across sections to hit the target. Add fields that make logical sense for each section if needed to reach 164.

### What Each Section Must Contain

For every section, the file must document:
1. **Section header** — section number, name, schema key, field count, and a 1–2 sentence description of what this section is for and what downstream agents consume it
2. **A table or structured list of every field** including:
   - Field ID (use dot notation: `identity.practice_name`, `voice_dna.tone_primary`, etc.)
   - Field name (human-readable)
   - Data type (String / Enum / Array / Boolean / Integer / Object / URL)
   - Description of what the field captures
   - Example value(s)
   - Status options: `confirmed` / `agent-generated` / `pending-approval` / `pending-upload`
   - Which downstream agents/layers consume this field

### Key Fields Already Named in Existing Steps

Pull these exact field names from the existing steps — they must appear in Step 2 exactly as referenced:

**From Step 3 (Fast-Start minimum fields):**
- `voice_dna.tone_primary`
- `voice_dna.formality_level`
- `voice_dna.sentence_rhythm`
- `avatar_psychology.avatar_name`
- `avatar_psychology.primary_symptom`
- `avatar_psychology.core_fear`
- `avatar_psychology.deepest_desire`
- `avatar_psychology.awareness_level`
- `avatar_psychology.false_beliefs` (all three)
- `root_cause_map.surface_problems`
- `root_cause_map.new_vehicle_name`
- `root_cause_map.new_vehicle_description`
- `offer_architecture.core_transformation`
- `offer_architecture.high_ticket_name`
- `offer_architecture.high_ticket_price`
- `offer_architecture.fulfillment_model`
- `webinar_raw_material.one_big_domino`
- `webinar_raw_material.secret_1`
- `webinar_raw_material.secret_2`
- `webinar_raw_material.secret_3`

**From Step 7 (Expert Dossier Brief structure):**
- `expert_personal_story.story_personal_story_summary`
- `expert_personal_story.story_what_they_almost_gave_up_on`
- `expert_personal_story.story_what_changed_everything`
- `webinar_raw_material.webinar_origin_story_*` fields (before, discovery, after)

**From Step 7 (Dossier Quality Score):**
- The schema must support: completion score calculation, confirmation rate tracking, story richness, Voice DNA quality, offer stack completeness, visual asset upload status

### Downstream Agent Consumption Map

Include a section at the end of the file that maps which dossier sections feed which platform layers/agents:

| Dossier Section | Primary Consumers |
|---|---|
| Identity & Practice | All agents (context) |
| Voice DNA | All Builder Layer agents (Layer 3) — every word they write |
| Visual DNA | Ad Creative Builder, Website Builder, Content Builder |
| Avatar Psychology | All Builder agents, Brand Strategy, Growth Strategy |
| Root Cause Map | Brand Strategy, Webinar Builder, Ad Creative Builder, Content Builder |
| Clinical Philosophy | Brand Strategy, Content Builder, Webinar Builder |
| Offer Architecture | Growth Strategy, Funnel Builder, Sales Script Builder, Email Builder |
| Perfect Webinar Raw Material | Webinar Builder Agent (primary), Ad Creative Builder |
| Proof Bank | Ad Creative Builder, Email Builder, Webinar Builder, Sales Script Builder |
| Competitive Landscape | Brand Strategy, Ad Creative Builder, Webinar Builder |
| Content Audit | Growth Strategy, Content Builder |
| Dream Vision & Traffic Reality | Growth Strategy Agent (primary) |
| Business Context | Growth Strategy, Email Builder, Compliance layer |
| Expert Personal Story | Content Builder, Ad Creative Builder, Webinar Builder |

### Additional Requirements for Step 2

**Status Flags Section:** Document the four status flag types and what each means:
- `confirmed` — Expert explicitly approved this value
- `agent-generated` — Agent built this value; expert has not yet confirmed it
- `pending-approval` — Agent-generated and surfaced to expert; awaiting thumbs up/edit/regenerate
- `pending-upload` — File asset field; conversation-derived placeholder in use until upload arrives

**Data Types Reference:** Brief glossary of data types used across the schema (String, Enum, Array, Boolean, Integer, Object, URL, File)

**Schema Version Note:** The schema is versioned. When a new field is added, the version increments. Downstream agents always declare which schema version they read from — this prevents silent breaking changes.

### Footer Format (match exactly)
```
*Step 2 of 22 — Expert Dossier Data Schema — v1.0 Draft*
*Next: Step 3 — Conversation Flow Architecture*
```

### Length Target
~600–800 lines. This is the longest file in Layer 1 because it defines every field. Do not truncate any section. Every field must have a full description and example. The schema is what the developer is building against — it must be complete.

---

## After Both Files Are Written

1. Verify both files exist at the correct paths
2. Run a quick check that all field names referenced in Steps 3–7 appear in Step 2
3. Commit both files to git:
   ```bash
   cd /home/work/.openclaw/workspace/cliniciq
   git add layer1/step1_onboarding_lead_agent.md layer1/step2_expert_dossier_data_schema.md
   git commit -m "Layer 1: Add Step 1 (Onboarding Lead Agent) and Step 2 (Expert Dossier Data Schema)"
   git push origin main
   ```
4. Confirm the push succeeded and report the commit hash back to Ryan

---

## Quality Check Before Pushing

- [ ] Step 1 header says "Step 1 of 22" and footer says "Next: Step 2"
- [ ] Step 2 header says "Step 2 of 22" and footer says "Next: Step 3"
- [ ] Step 2 total field count reaches 164
- [ ] All field names referenced in Steps 3–7 appear in Step 2 with matching dot-notation IDs
- [ ] Tone, depth, and format match Steps 3–7 exactly
- [ ] Both files pushed to GitHub main branch

---

*Handoff written: 2026-04-07*
*Context used when written: ~83% — new session required*
