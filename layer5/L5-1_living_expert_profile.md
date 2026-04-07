# ClinicIQ — Layer 5: The IQ Intelligence Platform
# L5-1: Living Expert Profile
**Version 1.0**
*Layer 5, Spec 1 of 5 | Depends on: All 22 Steps (especially Layer 1 Onboarding, Layer 4 Analytics)*

---

## Purpose

Every agent in the ClinicIQ platform — all 168 of them — reads from a single source of truth before they produce a single word of output. That source of truth is the **Living Expert Profile (LEP).**

The Expert Dossier built in Layer 1 is the foundation. The Living Expert Profile is what it becomes over time — not a static intake document, but a **continuously updating intelligence model** of the expert's identity, voice, market position, performance patterns, and audience psychology.

The LEP is what separates ClinicIQ from every tool that exists today. Every other platform asks you to configure it once and live with the result. The LEP means the platform **gets smarter the longer you use it** — automatically, without the expert doing any extra work.

This spec defines: what the LEP is, what it contains, how it's built, how it updates, how it's used by every layer of the platform, and how it compounds over time into an unfair competitive advantage for every expert on the platform.

---

## The Core Concept: From Static Dossier to Living Intelligence Model

### What the Dossier Was (Layer 1)
The Layer 1 Expert Dossier is a structured intake — 198 fields across 14 sections, captured via the Onboarding Agent. It is the best possible starting point: rich, deep, expert-specific. But it is a snapshot. It represents the expert as they were when they joined.

### What the Living Expert Profile Is (Layer 5)
The Living Expert Profile is the same 198-field architecture — plus 46 additional performance-derived fields — continuously updated by every interaction the expert has with the platform, every piece of content the platform produces, every performance data point the analytics layer captures, and every market signal the platform monitors.

It is never done. It is never "current." It is always becoming more accurate.

**The distinction that matters:**
- Dossier: *This is who you told us you are.*
- Living Expert Profile: *This is who you demonstrably are — confirmed by everything you've done on the platform and everything your audience has responded to.*

---

## The LEP Architecture: 3 Layers of Intelligence

The Living Expert Profile is organized into three layers of intelligence, each building on the last.

---

### Layer A — Identity Core (Static Foundation)
*Source: Layer 1 Onboarding | Updates: Expert-initiated only*

These are the fields that define who the expert fundamentally is. They don't change often. When they do change, it's a significant event (rebrand, new specialty, major offer change) and requires intentional expert action.

**Sections:**
1. **Expert Identity** — Name, credentials, specialty, practice model, location, years in practice, license type, compliance jurisdiction
2. **Voice DNA** — Sentence rhythm, vocabulary register, tone spectrum, humor style, signature phrases, forbidden phrases, formality level, pace profile
3. **Visual DNA** — Brand color palette, typography family, photography style, aesthetic keywords, logo/asset files
4. **Clinical Philosophy** — Core belief system, methodology name and description, what they reject, credibility anchors, origin story
5. **Expert Personal Story** — Full epiphany bridge narrative, before/after arc, mission statement
6. **Offer Architecture** — Complete 4-tier offer stack (attraction → entry → core → continuity) with pricing, value stacks, mechanism name, guarantee concept
7. **Proof Bank** — All patient transformation stories, testimonials, before/afters, clinical outcomes, expert credentials proof

**Update protocol for Identity Core:**
- Expert can edit any field at any time via the Dashboard → IQ Profile → Edit
- All edits require explicit confirmation ("Update this across the platform?")
- Downstream agents are notified of changes to fields they depend on
- Version history is retained — expert can roll back any field to a prior value
- Major changes (voice, offer, philosophy) trigger a re-run of Brand Strategy Agent to update Brand North Star

---

### Layer B — Market Intelligence (Dynamic, Platform-Updated)
*Source: Layer 4 Analytics + External Monitoring | Updates: Continuous, automated*

These are the fields the platform builds and updates on its own — based on what the expert's audience actually responds to, what competitors are doing, what's trending in the niche, and what the market data shows.

The expert never fills these in. The platform builds them from behavior.

**Sections:**

#### B1 — Audience Response Profile
What the expert's audience demonstrably responds to — derived from email open rates, funnel conversion data, social engagement, content performance, and ad results.

| Field | What It Tracks | How It's Built |
|-------|---------------|----------------|
| Top Hook Patterns | Hook structures that outperform (question / statistic / bold claim / story open) | Analyzed from top 20% performing emails and ads |
| Winning Subject Line Formulas | Subject line structures with highest open rates | Extracted from email performance data |
| High-Convert Emotion Triggers | Emotional angles that drive the most clicks/conversions | Derived from A/B test results and ad performance |
| Avatar Language Patterns | Exact words and phrases the audience uses themselves | Extracted from reply emails, testimonials, DMs, reviews |
| Content Topic Affinity Map | Which topics drive the most engagement by content type | Built from social and email analytics |
| Objection Frequency Map | Most common objections raised at each funnel stage | Built from sales call recordings, email replies, chat logs |
| Awareness Level Distribution | % of current audience at each of the 5 Levels of Awareness | Derived from funnel entry points and behavior patterns |

#### B2 — Competitive Intelligence
A continuously updated picture of the expert's competitive landscape.

| Field | What It Tracks | How It's Built |
|-------|---------------|----------------|
| Competitor Content Calendar | Top competitors' publishing patterns and topics | External content monitoring (RSS, YouTube, social) |
| Competitor Hook Library | Hooks and angles competitors are using | Content analysis via monitoring agents |
| Market Saturation Map | Which angles/topics are overcrowded vs. underserved | Cross-expert platform data + external search trend data |
| Gap Opportunity Signals | Content angles competitors are not covering | Derived from search demand vs. available content analysis |
| New Vehicle Differentiation Score | How differentiated is this expert's mechanism vs. competitors | LLM-graded analysis on a 1–10 scale, updated monthly |

#### B3 — Market Trend Intelligence
What's moving in the expert's niche — before it peaks.

| Field | What It Tracks | How It's Built |
|-------|---------------|----------------|
| Rising Search Topics | Search queries gaining volume in niche | Search trend API monitoring |
| Trending Social Angles | Topics gaining engagement velocity on social | Social monitoring agents |
| Seasonal Pattern Map | Historical performance lift by month/season for this niche | Cross-platform data + expert's own historical data |
| Emerging Mechanism Angles | New mechanisms gaining credibility in functional medicine space | Research content monitoring |
| Platform Algorithm Signals | Changes in reach/distribution patterns by channel | Engagement rate trend analysis across channels |

#### B4 — Offer Performance Intelligence
Which offers, prices, and entry points are actually converting.

| Field | What It Tracks | How It's Built |
|-------|---------------|----------------|
| Funnel Conversion Rates by Stage | % converting at each funnel step | Funnel analytics integration |
| Best Performing Entry Offer | Which Tier 1/2 offer generates the most qualified leads | Revenue and LTV data |
| Price Sensitivity Signals | Where price resistance occurs in the buying journey | Checkout abandonment and sales call data |
| Upsell Conversion Map | Which upsell sequences perform best | Email + purchase data |
| LTV by Avatar Segment | Average lifetime value broken down by patient type | Patient database + revenue data |

---

### Layer C — Behavioral Intelligence (Learning Loop, Platform-Derived)
*Source: Layer 4 Learning & Feedback Engine | Updates: After every agent run + every approval action*

This is the most powerful layer and the one that creates the deepest lock-in over time. Layer C tracks how the expert *uses* the platform and what their behavior signals about their preferences, standards, and patterns.

**Sections:**

#### C1 — Output Quality Calibration
What does "good" look like for this specific expert? Built from every approval, edit, and rejection.

| Field | What It Tracks |
|-------|---------------|
| Approval Rate by Agent | % of outputs approved without edit, by builder type |
| Common Edit Patterns | What the expert consistently changes in AI-generated outputs |
| Rejection Reasons Bank | Categorized reasons why outputs are rejected |
| Quality Floor by Content Type | Minimum quality threshold the expert accepts, calibrated per content type |
| Voice Drift Detection | When platform outputs are drifting from true voice — detected by edit frequency |
| Preferred Output Length | How long the expert's approved content tends to be, by format |

**How it's used:** Every agent checks C1 before generating. If this expert consistently shortens headlines, the agent starts shorter. If they consistently add more clinical language, the agent starts more clinical. The calibration is invisible and continuous.

#### C2 — Workflow Preference Profile
How does this expert like to work with the platform?

| Field | What It Tracks |
|-------|---------------|
| Session Timing Patterns | When the expert is most active on the platform |
| Typical Session Length | Short bursts vs. deep work sessions |
| Approval Batching Preference | Does the expert prefer approving one at a time or batch reviewing? |
| Proactive Suggestion Receptivity | Does the expert act on IQ Claw's proactive suggestions? Which types? |
| Preferred Builder Activation Order | Which builders does this expert prioritize and activate most? |
| Communication Style with IQ Claw | Terse commands vs. detailed instructions vs. collaborative dialogue |

**How it's used:** IQ Claw adapts its interaction style to match. High-receptivity experts get more proactive suggestions. Low-receptivity experts get fewer interruptions and more confirmations. Session timing data informs when the Morning Brief is delivered.

#### C3 — Expert Evolution Tracking
How is the expert growing over time?

| Field | What It Tracks |
|-------|---------------|
| IQ Score Trajectory | IQ Score trend over time — accelerating, plateauing, declining |
| Offer Stack Evolution | How the offer stack has changed over time |
| Voice Evolution Signals | How the expert's voice is shifting as they mature on the platform |
| Niche Narrowing / Broadening | Is the expert's focus sharpening or expanding over time? |
| Revenue Growth Correlation | Connecting platform activity to business outcome trends |
| Milestone Achievements | Platform achievements earned over the expert's lifetime |

---

## The LEP Update Engine: How It Stays Current

The Living Expert Profile is updated by six distinct triggers. Each trigger has defined update logic, a defined scope of fields affected, and a downstream notification protocol.

### Trigger 1 — Expert Session
**When:** Any time the expert has a conversation with IQ Claw
**What updates:** Identity Core fields if new information is shared, Proof Bank if new stories emerge, Behavioral Intelligence — C1/C2 fields based on how the session went
**How:** IQ Claw's session summary agent extracts any new dossier-relevant information at session close and queues it for expert confirmation

### Trigger 2 — Performance Data Ingestion
**When:** Daily — Layer 4 Analytics agents push new performance data
**What updates:** All Layer B fields — Audience Response Profile, Offer Performance Intelligence
**How:** Automated. No expert action required. Fields update silently. IQ Score recalculates. If a significant shift is detected, the Morning Brief flags it.

### Trigger 3 — Content Approval
**When:** Every time the expert approves, edits, or rejects a builder output
**What updates:** Layer C — Output Quality Calibration fields
**How:** Output Quality Agent logs the approval action, edit delta, and any rejection reason. C1 fields update based on the pattern. Calibration effects propagate to all active builder agents.

### Trigger 4 — Market Intelligence Scan
**When:** Daily/weekly (cadence varies by field)
**What updates:** Layer B2/B3 fields — Competitive Intelligence, Market Trend Intelligence
**How:** Monitoring agents run scheduled scans. Significant findings surface in the Morning Brief and flag relevant IQ Claw suggestions.

### Trigger 5 — Expert-Initiated Edit
**When:** Expert manually updates any field via Dashboard → IQ Profile
**What updates:** Whichever Identity Core field was edited
**How:** Direct edit with confirmation + downstream agent notification

### Trigger 6 — Layer 4 Learning Loop
**When:** Monthly — Learning & Feedback Engine runs full dossier recalibration
**What updates:** Layer C — Expert Evolution Tracking, Behavioral Intelligence refinements
**How:** L4 Learning Engine reviews the past 30 days of platform activity, identifies drift or calibration opportunities, updates relevant fields, and surfaces a Monthly Profile Report to the expert: *"Here's how your IQ profile has evolved this month."*

---

## How Every Platform Layer Reads the LEP

The LEP is not just stored — it is actively consumed by every agent in the platform. Here is precisely how each layer uses it.

### Layer 1 — Onboarding Agent
Reads: Nothing (it's building the LEP)
Writes: The initial 198-field Identity Core

### Layer 2 — Strategy Agents
**Brand Strategy Agent** reads:
- Voice DNA (complete) → Brand North Star document
- Visual DNA → Style system definitions
- Clinical Philosophy → Positioning and differentiation framework
- Competitive Intelligence → Differentiation gap analysis
- Avatar Psychology → Messaging framework

**Growth Strategy Agent** reads:
- Offer Architecture → Revenue model and funnel strategy
- Traffic Reality + Dream Vision → Gap analysis and 90-day growth plan
- Audience Response Profile → Channel and angle selection
- Seasonal Pattern Map → Campaign calendar timing
- Objection Frequency Map → Core objection-handling strategy

### Layer 3 — Builder Agents
Every builder agent reads a LEP Context Bundle before generating any output:

```
LEP CONTEXT BUNDLE — [Builder Name] — [Date]
─────────────────────────────────────────────
VOICE DNA SNAPSHOT
  Rhythm: [current rhythm profile]
  Register: [vocabulary level]
  Tone: [tone spectrum position]
  Signature phrases: [top 5]
  Forbidden phrases: [top 5]
  Approved sample extracts: [3 verbatim examples]

OUTPUT QUALITY CALIBRATION
  Approval rate (this builder): [%]
  Common edits: [top 3 patterns]
  Preferred length (this format): [range]
  Voice drift status: [clean / flagged]

AUDIENCE RESPONSE PROFILE
  Top hooks (last 90 days): [top 3 patterns]
  High-convert emotion triggers: [top 3]
  Avatar language patterns: [key phrases]
  Awareness level distribution: [% by level]

BRAND NORTH STAR
  Mechanism name: [name]
  New vehicle statement: [statement]
  Core promise: [promise]
  Competitive differentiation: [statement]

CURRENT OFFER CONTEXT
  Active offer being built for: [tier + name]
  Funnel stage context: [where this asset lives]
─────────────────────────────────────────────
```

This bundle is assembled automatically and injected into every builder agent's prompt. The expert never configures it. The platform builds it fresh for each run.

### Layer 4 — Analytics & Intelligence Agents
Reads: Everything (Layer 4 is the LEP's primary data source)
Writes: All Layer B and Layer C fields

### Layer 5 — IQ Intelligence Platform
The LEP is the foundation all L5 specs operate on:
- L5-2 (Proactive Intelligence) reads Layer B to generate morning briefs and proactive alerts
- L5-3 (One-Tap Deployment) reads Layer C workflow preferences to optimize the approval flow
- L5-4 (Network Intelligence) anonymizes and aggregates LEP Layer B fields across all experts
- L5-5 (IQ Score) computes the score from all three LEP layers

---

## The Compound Effect: Why the LEP Creates an Unbreakable Moat

Here's what happens to the LEP over 12 months on the platform vs. Day 1:

| Dimension | Day 1 | Month 3 | Month 12 |
|-----------|-------|---------|----------|
| Voice DNA confidence | Medium (Onboarding session only) | High (enriched by 50+ approved outputs) | Exceptional (refined by 200+ approvals, patterns locked) |
| Hook performance data | None | 90 days of real results | Full year of seasonal patterns |
| Output quality calibration | Baseline | Tuned to this expert's preferences | Microscopically calibrated — almost no edits needed |
| Competitive intelligence | Snapshot | 3 months of competitor movement | Full competitive evolution map |
| Audience language patterns | Avatar hypothesis | Real language from real responses | Deep, verified audience vocabulary |
| Seasonal content patterns | Generic niche benchmarks | First-party data emerging | Fully expert-specific seasonal performance model |
| Offer performance intelligence | Hypothetical | First conversion data | Multi-funnel LTV model |

**The lock-in effect:** By Month 12, the platform knows this expert better than any VA, copywriter, strategist, or agency ever could. The idea of starting over somewhere else — and losing all of that accumulated intelligence — becomes unthinkable. That's the moat.

---

## Privacy and Expert Ownership

The LEP belongs to the expert. Always.

- **Full export:** Any expert can export their complete LEP in JSON and human-readable format at any time
- **Deletion:** Expert can delete any field, section, or the entire LEP at any time
- **Portability:** Exported LEP can be imported into future ClinicIQ accounts (if they leave and return) or used externally
- **Cross-expert aggregation:** Only anonymized, aggregated pattern data is used for Network Intelligence (L5-4). No individual expert's LEP is ever shared with another expert
- **Compliance:** All LEP data is stored encrypted at rest. HIPAA-adjacent best practices applied given the health expert context. No patient PHI is ever stored in the LEP — it captures the expert's business profile, not patient data.

---

## The LEP Dashboard: What the Expert Sees

The expert has a dedicated IQ Profile view in the platform where they can see and manage their Living Expert Profile.

### IQ Profile — View Layout
- **Header:** Expert name, photo, credential badge, IQ Score chip, Dossier Completion Score bar
- **Section tabs:** Identity Core / Market Intelligence / Behavioral Intelligence
- **Identity Core tab:** All 14 sections expandable, each field showing value + status (confirmed / agent-generated / pending-approval / pending-upload) + last-updated date
- **Market Intelligence tab:** Read-only panels for each Layer B section — live data visualizations where applicable (e.g., topic affinity heat map, hook performance bar chart)
- **Behavioral Intelligence tab:** Read-only panels showing output quality calibration charts, workflow preference summary, expert evolution timeline
- **Update feed:** Chronological list of LEP updates — "Voice DNA enriched from 50 content approvals (Mar 15)" / "Audience Response Profile updated — 3 new top hook patterns identified (Mar 12)"

### IQ Profile — Quick Actions
- **"Add to my story"** — opens IQ Claw in Voice DNA enrichment mode for expert to share more content samples
- **"Add a patient win"** — opens a structured form for adding a new transformation story to the Proof Bank
- **"Review pending confirmations"** — surfaces all pending-approval fields for expert review
- **"Export my profile"** — downloads complete LEP as structured JSON + readable PDF

---

## Integration with Layer 1: The Upgrade Path

The Layer 1 Expert Dossier doesn't get replaced by the LEP. It becomes the LEP's foundation.

On the day the expert completes onboarding:
- Their 198-field dossier becomes the seed of the LEP
- All Identity Core fields are imported at their current status (confirmed / agent-generated / pending-approval)
- Layer B fields are all initialized as empty (no data yet)
- Layer C fields are all initialized as baseline defaults
- The LEP update engine starts running immediately

From that point forward, the LEP grows on its own. The onboarding was the planting. The LEP is the tree.

---

## Summary

The Living Expert Profile is the central intelligence system of ClinicIQ. It is:

- **The memory** — everything the platform has ever learned about this expert, stored and organized
- **The calibration system** — ensuring every output gets better over time, automatically
- **The competitive moat** — accumulating expertise that makes leaving unthinkable
- **The foundation** — that every other Layer 5 spec (L5-2 through L5-5) builds on top of

Nothing the platform produces exists without reading the LEP first. Nothing the platform learns goes anywhere but the LEP. It is the brain of ClinicIQ.

---

*L5-1: Living Expert Profile — v1.0*
*Next: L5-2 — Proactive Intelligence Engine*
