# clinicIQ — Layer 1: Onboarding Agent — Step 7: Onboarding Output Payload — Handoff to Layer 2
**Version 1.0 — Final**
*Step 7 of 22 | Depends on: Steps 1–6 (All Layer 1 steps)*

---

## Purpose

This document defines the exact output the Onboarding Agent produces at the end of every session — what it looks like, how it is structured, what format it takes, what status flags are applied, and how it is passed to the Layer 2 Strategy Agents.

The payload is the bridge between everything the Onboarding Agent captures and everything the Strategy and Builder Agents produce. If the payload is clean, complete, and well-structured, every downstream agent runs at full power. If it is incomplete or poorly organized, every downstream output degrades.

This step also defines the minimum viable payload (Fast-Start) vs. the full payload (Deep-Dive), the pending flags protocol, and the re-entry logic for experts who return to deepen their dossier over time.

---

## The Two Payload States

### State 1 — Fast-Start Payload (Minimum Viable Dossier)
Produced at the end of a Fast-Start Mode session (20–30 minutes).
Unlocks: Layer 2 strategy agents. Brand Agent and Growth Agent can produce their first outputs.
Coverage: ~60 P1 priority fields confirmed or agent-generated with approval. Full P1 field list defined in Step 2 schema.
Pending flags: Remaining fields auto-populated with agent-generated best-guess values marked `pending-approval`.

### State 2 — Full Payload (Complete Dossier)
Produced at the end of a Full Deep-Dive session or after multiple sessions that collectively cover all sections.
Unlocks: Full platform capability — all Builder Layer agents run at maximum intelligence.
Coverage: All 198 fields populated (confirmed, agent-generated+approved, or pending-upload for file assets).
Pending flags: Only file-based visual assets (logo, brand guide, photos) remain as `pending-upload`.

---

## Payload Structure

The Expert Dossier payload is delivered in two parallel formats:

### Format 1 — Structured Data Object (Machine-Readable)
A clean JSON/structured data object that every downstream agent reads programmatically. Every field from the 198-field schema is present, with its value, tier, status flag, and consuming agents noted.

This is what the platform's backend reads. It never changes shape — only the values and status flags update over time.

**Structure:**
```
{
  "dossier_id": "[unique expert ID]",
  "version": "[dossier version number — increments with every update]",
  "created": "[timestamp]",
  "last_updated": "[timestamp]",
  "session_mode": "fast-start | full-deep-dive",
  "completion_score": [0-100],
  "sections": {
    "identity": { [all Section 1 fields with values + status flags] },
    "voice_dna": { [all Section 2 fields] },
    "visual_dna": { [all Section 3 fields] },
    "avatar_psychology": { [all Section 4 fields] },
    "root_cause_map": { [all Section 5 fields] },
    "clinical_philosophy": { [all Section 6 fields] },
    "offer_architecture": { [all Section 7 fields] },
    "webinar_raw_material": { [all Section 8 fields] },
    "proof_bank": { [all Section 9 fields] },
    "competitive_landscape": { [all Section 10 fields] },
    "content_audit": { [all Section 11 fields] },
    "dream_vision_traffic": { [all Section 12 fields] },
    "business_context": { [all Section 13 fields] },
    "expert_personal_story": { [all Section 14 fields] }
  },
  "pending_flags": {
    "pending_approval": [ [list of field IDs awaiting expert validation] ],
    "pending_upload": [ [list of visual asset fields awaiting file upload] ]
  },
  "silent_diagnosis": { [gap flags and priority items for Strategy Layer] },
  "achievements_unlocked": [ [list of achievement IDs earned in this session] ],
  "handoff_ready": true | false
}
```

**`handoff_ready` flag:** Set to `true` only when the Fast-Start minimum fields are confirmed. The Strategy Layer agents will not run until this flag is `true`. This prevents half-baked strategy outputs from reaching the expert.

---

### Format 2 — Expert Dossier Brief (Human-Readable)
A clean, narrative-formatted markdown document that reads like an expert intelligence brief. This is what the expert sees in their dashboard, what the expert can download and share with their team, and what any human reviewer (coach, strategist, copywriter) reads to understand the expert's business instantly.

**Structure of the Expert Dossier Brief:**

---

#### CLINICIQ EXPERT DOSSIER
**[Expert Name] | [Credential Title] | [Practice Name]**
*Dossier Version [X] | Last Updated [Date] | Completion Score: [X]/100*

---

**WHO YOU ARE**
[2–3 sentence synthesis of identity, specialty, practice model, years in practice, and location/scope]

**YOUR VOICE**
[3–4 sentence description of Voice DNA — tone, rhythm, formality, signature phrases, what they avoid. Written in third person as a brief to a copywriter.]
*Sample extracts:*
- "[Verbatim quote 1]"
- "[Verbatim quote 2]"
- "[Verbatim quote 3]"

**YOUR BRAND AESTHETIC**
[2–3 sentences on visual DNA — aesthetic description, keywords, photography style, known assets / pending uploads noted]

**YOUR IDEAL PATIENT**
[The full avatar narrative brief — see Step 5 output format. Written as a vivid description of a real person, not a field list.]
*Awareness Level: [Level 1–5 with brief rationale]*

**YOUR ROOT CAUSE MAP**
*Surface problems the avatar experiences:* [list]
*The root cause(s) they've been missing:* [list]
*Why everything they've tried hasn't worked:* [narrative]
*Your new vehicle:* [New vehicle name + description]
*The mechanism explained simply:* [analogy or plain-language explanation]

**YOUR CLINICAL PHILOSOPHY**
[Core belief, methodology name, what they reject, credibility anchors — narrative format]

**YOUR OFFER STACK**
[Complete 4-tier offer stack in the visual format from Step 6 — Tier 1 through Tier 4 with names, prices, descriptions, and value stacks]
*Mechanism Name: [Name]*
*Guarantee: [Guarantee concept]*

**YOUR WEBINAR ARCHITECTURE**
*One Big Domino:* [Statement]
*Secret 1 (Vehicle Belief Shift):* [What and why]
*Secret 2 (Internal Belief Shift):* [What and why]
*Secret 3 (External Belief Shift):* [What and why]
*Your Origin Story Summary:* [Epiphany bridge — old world, discovery, new world]
*Hook Concepts:* [Top 3–5 webinar title and hook concepts]

**YOUR PROOF BANK**
[Top 3 patient transformation stories in narrative format — before, journey, result, timeline]
*Most dramatic transformation:* [Story]
*Fastest result:* [Story]
*Skeptic-to-believer:* [Story]

**YOUR PERSONAL STORY**
[Expert's own health journey or mission origin — narrative format]

**YOUR COMPETITIVE LANDSCAPE**
[What the avatar tries first, why each alternative fails, how this expert is genuinely different]

**YOUR CURRENT ASSETS**
[Content audit summary — what exists, what performs best, email list status, tech stack]

**YOUR VISION AND REALITY**
*Where you're going:* [Dream practice vision]
*Where you are now:* [Traffic reality, current leads, audience temperature]
*The gap:* [What the Growth Agent will address]

**SILENT DIAGNOSIS — PRIORITY FLAGS**
[List of gaps identified during onboarding, each with a one-line description of what it means and what the Strategy Layer will do about it]

---

*This dossier was built by clinicIQ's Onboarding Agent on [date]. It deepens every time you add to it. Every output the platform creates reads from this document.*

---

## The Pending Flags Protocol

Not every expert arrives with a complete picture of their business. The pending flags system ensures nothing stalls while making it completely clear what remains to be confirmed or uploaded.

### pending-approval Fields
These are fields the agent generated on the expert's behalf and the expert has not yet explicitly confirmed. They are fully functional — downstream agents use them — but they are flagged so the expert knows to validate them.

**How they appear in the dashboard:**
- Yellow indicator on the relevant dossier section
- "Review & confirm" prompt that shows the agent-generated answer with a thumbs up / edit / regenerate option
- Never blocking — outputs still generate using these values
- Each confirmation increases the Dossier Completion Score

**Re-confirmation flow:**
The agent surfaces pending-approval fields at the start of every new session:
> "Before we dive in — there are [X] answers I built for you last time that you haven't confirmed yet. Want to take 5 minutes to look them over? It'll make everything I build for you sharper."

### pending-upload Fields
Visual asset fields (logo, brand guide, color palette, photos) that require a file upload. These never block any output — the platform works with conversation-derived aesthetic signals until assets arrive.

**How they appear in the dashboard:**
- Grey indicator with a paper clip icon
- "Upload when ready" prompt — no urgency, no blocking
- When uploaded, Visual DNA section updates and all future content outputs immediately apply the real brand assets

---

## The Silent Diagnosis Payload

This is the intelligence the Onboarding Agent collected while running the intake — the gaps, risks, and opportunities it identified without being asked. It is delivered to the Strategy Layer as a structured brief that shapes the first outputs.

**Silent Diagnosis categories:**

### Offer Gaps
Which tiers of the 4-tier offer stack are missing or underbuilt, with specific diagnosis and recommended fix.

### Positioning Gaps
Is the expert's differentiation clear? Is the new vehicle named and compelling? Is the mechanism demonstrable? Flags weak positioning for the Brand Strategy Agent to address.

### Audience Readiness
What is the gap between where the expert is (traffic reality) and where the strategy needs to go? Flags for the Growth Strategy Agent.

### Proof Bank Depth
Is there enough social proof to run a credible webinar and funnel? Flags thin proof banks with specific recommendations (case study capture, testimonial collection, before/after documentation).

### Voice DNA Confidence Level
How strong is the Voice DNA profile? Was it built from a rich, expressive session or a short, clipped one? Flags low-confidence Voice DNA so the Builder Layer applies conservative calibration and prompts for enrichment.

### Compliance Flags
Based on the expert's specialty, are there known claim restrictions (FDA, FTC, state medical board) that the Builder Layer needs to apply? Flagged here so every output is compliance-aware from the start.

**Example Silent Diagnosis output:**

```
SILENT DIAGNOSIS — PRIORITY FLAGS

1. OFFER GAP — No Tier 1 attraction offer exists.
   Impact: No lead generation mechanism. First asset to build.
   Growth Agent action: Lead magnet or paid assessment build is first priority.

2. OFFER GAP — Tier 4 continuity not built.
   Impact: Revenue resets every month. No recurring base.
   Growth Agent action: Membership or supplement subscription concept included in 90-day plan.

3. POSITIONING — New vehicle unnamed.
   Impact: Competing on price by default. No differentiation anchor.
   Brand Agent action: Mechanism naming is first brand deliverable.

4. PROOF BANK — Thin. Only 2 transformation stories captured.
   Impact: Webinar proof stack will be weak. Conversion risk.
   Growth Agent action: Case study capture included in first 30 days.
   Builder action: Use available stories fully — no fabrication.

5. VOICE DNA — Medium confidence. Session was short and clipped.
   Impact: Voice outputs will be accurate but not highly nuanced.
   Recommendation: Schedule a Voice DNA enrichment session after first content batch.

6. COMPLIANCE — Specialty: Functional medicine / autoimmune.
   Flags: Cannot claim to "cure," "reverse," or "treat" specific diseases in paid ads.
   Builder Layer: Auto-apply functional medicine compliance filter to all ad and funnel copy.
```

---

## The Handoff Trigger

The payload is handed off to Layer 2 the moment `handoff_ready` is set to `true`. This happens automatically when the Fast-Start minimum fields are populated.

**At handoff, Layer 2 agents receive:**
1. The full structured data object (all 198 fields, all status flags)
2. The Expert Dossier Brief (human-readable narrative)
3. The Silent Diagnosis payload (priority flags and recommended actions)
4. The session transcript (for additional Voice DNA enrichment and quality review)
5. The achievements list (for dashboard display)
6. The dossier completion score (for gamification display)

> **Note on sequencing:** Items 1–6 above are the Layer 1 *inputs* that Layer 2 receives at handoff. The following two documents are Layer 2 *outputs* — they do not exist at handoff time; Layer 2 agents produce them as their first deliverables. They are listed here so developers understand what Layer 2 is responsible for producing before the Builder Layer activates:
> - **Brand North Star Document** — produced by Brand Strategy Agent; all Builder agents read this before generating any output
> - **Monthly Messaging Brief** — produced by Growth Strategy Agent; campaign-level hook bank, angle map, objection library, emotional beat sequence, and social proof deployment map that Builder agents use as their monthly creative brief

**Layer 2 agents initialized at handoff:**
- Brand Strategy Agent (5b) — reads Voice DNA, Clinical Philosophy, Avatar Psychology, Competitive Landscape, Offer Architecture
- Growth Strategy Agent (5a) — reads Traffic Reality, Dream Vision, Offer Architecture, Avatar Psychology, Silent Diagnosis
- Core Orchestrator Agent (6) — reads the full dossier to initialize routing intelligence

---

## The Living Dossier — Update Protocol

The dossier is not a one-time document. Every session, every content approval, every performance data point, every new patient story can update it. The update protocol ensures changes are tracked, version-controlled, and immediately reflected in all downstream outputs.

### Update Triggers
- Expert returns for a follow-up session → Onboarding Agent resumes where gaps exist
- Expert uploads a new visual asset → Visual DNA section updates
- Expert approves a pending-approval field → Status flag updates, score increases
- Layer 4 performance data identifies a pattern → Relevant fields updated with performance signal
- Expert manually edits a field in the dashboard → Marked as confirmed, score updates
- New patient story captured → Proof bank section adds entry

### Version Control
Every update increments the dossier version number. Previous versions are retained. This creates a complete history of how the expert's positioning, voice, and offers have evolved over time — useful for the Learning Loop Agent (Step 19) and for the expert's own review.

### Update Notification to Downstream Agents
When a field that a specific downstream agent depends on is updated, that agent receives an automatic notification:
> "Dossier updated: [Field name] changed from [old value] to [new value]. Review outputs that depend on this field."

This prevents the Builder Layer from generating content based on stale data.

---

## Dossier Quality Score — Contribution Breakdown

The completion score (0–100) displayed in the dashboard is calculated as follows:

| Component | Weight | How Measured |
|---|---|---|
| Field population | 35% | % of 198 fields with any value (confirmed, agent-generated, or pending-approval) |
| Confirmation rate | 20% | % of populated fields marked "confirmed" vs. "agent-generated" |
| Story richness | 15% | Proof bank depth — number of transformation stories, quotes, before/afters |
| Voice DNA quality | 15% | Sample extracts count + confirmation rate on Voice DNA section |
| Offer stack completeness | 10% | Number of 4 tiers populated with confirmed data |
| Visual asset uploads | 5% | Number of pending-upload fields resolved |

**Score milestones and what they unlock:**

| Score | Status | Unlocks |
|---|---|---|
| 0–30 | 🟡 Getting Started | Nothing yet — Fast-Start minimum not reached |
| 31 | 🟢 Layer 2 Unlocked | Brand Strategy Agent + Growth Strategy Agent activate |
| 61 | 🔵 Full Build Mode | All Builder Layer agents activate at full capacity |
| 86 | ⚡ Elite Dossier | Maximum platform intelligence — all outputs at peak quality |

---

## Layer 1 Complete

With Step 7 complete, Layer 1 is fully documented. The Onboarding Agent has:

1. A complete knowledge and skill description (Step 1)
2. A 198-field data schema across 14 sections (Step 2)
3. A full conversation flow architecture with two modes, section sequencing, anchor questions, and recovery protocols (Step 3)
4. A Voice DNA extraction methodology — passive and active — with enrichment over time (Step 4)
5. A deep avatar psychology extraction framework with 5 Levels of Awareness determination (Step 5)
6. A complete offer architecture extraction methodology using Hormozi, Brunson, and Fladlein frameworks (Step 6)
7. A structured output payload — machine-readable and human-readable — with handoff protocol, pending flags, silent diagnosis, and living dossier update logic (Step 7)

**Layer 2 begins with Step 8 — Brand Strategy Agent Knowledge & Skill Description.**

---

*Step 7 of 22 — Onboarding Output Payload — Handoff to Layer 2 — v1.0 Draft*
*Next: Step 8 — Brand Strategy Agent — Knowledge & Skill Description*
