# clinicIQ — Platform Architecture
**Version 1.0**
*Cross-cutting platform decisions: Asset Library, IQ Claw, Patient-Facing AI*
*These are not steps in the build sequence — they are foundational platform layers that every step depends on*

---

## Three Platform Layers

| Layer | Name | Who uses it | What it does |
|---|---|---|---|
| **Storage** | The IQ Drive | Expert + platform agents | Stores and organizes every asset produced in clinicIQ |
| **Expert AI** | IQ Claw | Expert | Operates the entire platform via natural language; strategy partner + builder |
| **Patient AI** | Expert-named (see below) | Expert's patients/leads | Patient education and lead nurture AI, powered by the expert's content |

---

## Layer 1: The IQ Drive

### What It Is

The IQ Drive is clinicIQ's built-in asset storage and management system. It is the single repository for everything the platform produces — images, carousels, b-roll files, scripts, email sequences, webinar scripts, slide decks, funnel pages, lead magnets, and documents.

The UX is deliberately modeled on Genspark's AI Drive — clean, familiar, fast. Experts who have used Genspark will feel immediately at home. On top of that foundation, the IQ Drive adds a structured metadata layer that turns a generic file storage system into an intelligent content management system.

### What Makes It Different From a Generic Drive

Every asset in the IQ Drive carries metadata that a generic drive cannot understand:

| Metadata Field | Values | Why It Matters |
|---|---|---|
| Asset type | Image, Carousel, B-Roll, Script, Email, Webinar, Funnel Page, Lead Magnet, Slide Deck, Document | Filters and routing |
| Platform | IG, FB, Both, Email, SMS, Webinar, Web | Platform-specific organization |
| Status | Draft, Ready, Scheduled, Posted, Archived, Ad Candidate | Workflow management |
| Awareness level | 1–5 | Content funnel management |
| Hook angle | From the active hook bank | Performance tracking |
| CTA type | Engagement, Lead Magnet, Webinar, Purchase, Ascension | Conversion tracking |
| Performance score | Calculated from connected platform data | Quality ranking |
| Production date | Date created | Freshness tracking |
| Campaign tag | Monthly Master Plan campaign reference | Campaign organization |
| Email-deliverable | Yes/No | Flags for non-buyer engine |

This metadata is applied automatically at production — the Builder agents tag every asset on creation. The expert never manually tags anything.

### The Interface

**Folder structure (default):**
```
IQ Drive/
├── Content/
│   ├── Images/
│   ├── Carousels/
│   ├── B-Roll/
│   └── Scripts/
├── Webinars/
│   ├── [Webinar Name]/
│   │   ├── Script (Live)/
│   │   ├── Script (VSL)/
│   │   ├── Slide Deck/
│   │   └── Q&A Script/
├── Funnels/
│   ├── [Funnel Name]/
│   │   ├── Opt-in Page/
│   │   ├── Registration Page/
│   │   └── [All funnel pages]/
├── Emails/
│   ├── Sequences/
│   │   ├── Welcome/
│   │   ├── Post-Webinar/
│   │   ├── Nurture/
│   │   └── [All sequence types]/
│   └── One-Offs/
├── Lead Magnets/
├── Ads/
│   ├── Organic Versions/
│   └── Ad-Optimized Versions/
└── Documents/
    ├── Strategy Docs/
    ├── SOPs/
    └── Dossier/
```

**Smart filters (across all folders simultaneously):**
The filter bar at the top of the IQ Drive allows the expert to search and filter across the entire library by any metadata combination:
- "Show me all IG images at awareness Level 2 with a performance score above 7"
- "Show me all ad candidates I haven't run yet"
- "Show me all email sequences that haven't been updated in 90 days"
- "Show me all lead magnets tagged as email-deliverable"

**Views:** Grid (thumbnail), List (metadata), Calendar (by production date or scheduled date)

### In-Drive Editing

Every asset is editable from inside the IQ Drive without leaving clinicIQ:

- **AI chat edit:** Click any asset, open the IQ Claw panel, type what you want changed. The relevant Builder sub-agent rewrites the element and the asset is updated in under 60 seconds for copy edits, under 3 minutes for visual assets.
- **Visual editor:** For images, carousels, and funnel pages — GrapesJS-based visual editor embedded in the drive panel. Drag, drop, resize, recolor without touching code.
- **Version history:** Every edit creates a version. The expert can roll back to any previous version.
- **Duplicate and variant:** One-click to create a variant of any asset (for A/B testing or platform adaptation).

### Performance Data

For posted social assets: engagement data is pulled from connected social accounts (IG, FB) and displayed on the asset card — reach, saves, shares, comments, follows, link clicks. Updated daily.

For emails: open rate, CTR, CTOR, unsubscribe rate, conversion attribution displayed per sequence and per individual email.

For funnel pages: conversion rate, traffic, time on page, scroll depth displayed per page.

For ads: CPL, CTR, ROAS, conversion rate pulled from Meta Ads Manager.

The performance score (0–10) is a calculated composite metric — weighted by the asset type's primary success metric (saves for educational images, clicks for ad candidates, conversion rate for funnel pages).

---

## Layer 2: IQ Claw — The Expert's AI Operator

### What IQ Claw Is

IQ Claw is the expert's always-present AI operator inside clinicIQ. It is simultaneously:
- A strategic business partner that knows the expert's business deeply
- The natural language interface for every Builder agent on the platform
- A real-time performance analyst with access to all platform data
- A proactive system that surfaces problems and opportunities without being asked
- The central orchestrator that routes requests to the right agent and assembles multi-agent workflows

IQ Claw is always available. It lives as a persistent panel — accessible from any screen in the platform. The expert never has to navigate to it. It's always one click away, or triggered by typing.

**The core promise:** The expert never has to learn how the platform works to use it. They tell IQ Claw what they need and IQ Claw handles the rest.

### The IQ Profile — Deep Calibration System

IQ Claw knows the expert at two levels:

**Level 1 — The Dossier (from Onboarding Layer)**
Everything captured in the standard onboarding: Voice DNA, Avatar Psychology, Offer Architecture, Proof Bank, Mechanism, One Big Domino, Visual DNA, tech stack, and all strategy layer outputs. This is pre-populated automatically. IQ Claw has full read access.

**Level 2 — The IQ Profile (from IQ Claw's own interview)**
A deeper, living document that captures everything the standard dossier doesn't: how the expert thinks and makes decisions, their business ecosystem beyond the primary program, their team structure, their bottlenecks, their goals at 1/3/5 years, their frustrations, their communication style, their AI readiness, their operational context.

**How the IQ Profile is built:**

IQ Claw runs a structured interview on first launch using a 10-phase framework covering:
1. Identity, role, and decision model
2. Business ecosystem map
3. Primary business deep-dive
4. Tools, tech stack, and data environment
5. People, roles, and human work mapping
6. Marketing, lead flow, and revenue engine
7. SOPs, systems, and training
8. AI opportunity mapping
9. Vision, scale, and future state
10. Communication and AI operating model

**The interview is not a form.** IQ Claw conducts it as a conversation — one question at a time, following threads, drilling down when answers are vague, surfacing contradictions, tracking open questions. It opens with:

*"I'm going to build a high-fidelity operating model of you and your business so I can support strategy, systems, and agent-building at a deep level. First question: what are the main businesses, projects, and major initiatives you are actively involved in right now — and which of them matter most over the next 12 months?"*

**Pre-fill from dossier:** Before asking anything, IQ Claw reviews the expert's dossier and pre-fills every answer it already knows. It presents these for confirmation, not re-entry. The expert is never asked something the platform already knows. *"Based on your onboarding, your primary program is [X] targeting [Y] avatar. Still accurate?"*

**The IQ Profile is a living document.** Every conversation adds to it. IQ Claw surfaces gaps proactively: *"You mentioned last week you're adding a group program — want me to add that to your offer architecture?"* When the expert answers a question in conversation that fills a profile gap, IQ Claw captures it automatically: *"Got it. I've added that to your IQ Profile."*

The expert never answers the same question twice. Ever.

**Deliverables from the completed IQ Profile interview:**
1. Founder Operating Profile (identity, decision style, communication preferences, standards)
2. Business Ecosystem Map (all businesses/projects with bottlenecks and opportunities)
3. Primary Business Blueprint (model, org map, patient journey, revenue engine, failure points)
4. Tool and Systems Map (every tool — keep/optimize/replace recommendation)
5. Role Automation Matrix (every role → automation potential → priority score)
6. AI Agent Opportunity Stack ranked by ROI
7. Top 10 Immediate Builds (concrete agent/automation recommendations)
8. Knowledge Gaps and Questions to Resolve
9. How to Use IQ Claw Effectively (personalized guide for this specific expert)

These deliverables live in the IQ Drive under Documents/Strategy Docs and are updated as the IQ Profile evolves.

### What IQ Claw Can Do

**1. Natural Language Platform Navigation**
*"How do I set up a new funnel?"*
*"Where are my ad candidate images?"*
*"Show me everything I've produced this month."*
IQ Claw answers any platform question instantly and can navigate the expert directly to the relevant screen.

**2. Content Production via Builder Agents**
Any content request is automatically routed to the correct Builder agent with full dossier and IQ Profile context pre-loaded. No setup, no configuration.

| Expert says | IQ Claw routes to |
|---|---|
| "Write me an email about cortisol and sleep" | Email Builder → Nurture Email Writer |
| "Create a carousel about thyroid symptoms" | Content Builder → Copy Writer + Layout Generator |
| "I need a promotional sequence for next week's sale" | Email Builder → Promotional Email Writer |
| "Build me a webinar about my new gut protocol" | Webinar Builder Lead |
| "I want 10 new image ideas for this month" | Content Builder → Content Ideation Engine |
| "Update my opt-in page headline" | Funnel Builder → Headline Generator |

IQ Claw confirms the request parameters, pulls from the relevant dossier fields, triggers the agent, monitors production, and delivers the output — all without the expert navigating anywhere.

**3. Multi-Agent Workflow Orchestration**
IQ Claw can trigger multiple agents in sequence for complex requests:

*"Plan my content for next month"*
→ Reads Monthly Master Plan → triggers Content Ideation Engine → assembles batch spec → routes to Content Builder → schedules outputs → updates Email Builder with new asset library → reports back with calendar

*"I want to launch my program next Tuesday"*
→ Reads offer architecture → triggers Funnel QA to verify pages are live → triggers Email Builder for launch sequence → triggers Content Builder for launch week social content → triggers Ad Creative Builder for paid amplification → assembles 7-day launch plan → reports status

**4. Strategy and Performance Analysis**
IQ Claw has live read access to all platform analytics. It doesn't just surface data — it interprets it.

*"Why is my webinar not converting?"*
→ Pulls webinar completion rate, drop-off timestamps, post-webinar sequence performance, order page conversion rate → identifies the most likely failure point → gives a specific diagnosis with recommended fix

*"What's working in my emails?"*
→ Pulls full email analytics → identifies top 3 performing emails by type, subject line pattern, and content angle → surfaces the pattern → recommends applying it to upcoming emails

*"What should I be doing this month?"*
→ Reads Monthly Master Plan + current performance metrics + IQ Profile goals → gives a prioritized 30-day action list specific to this expert's situation

**5. Proactive Alerts (without being asked)**
IQ Claw monitors the platform continuously and surfaces relevant alerts:
- Performance drops below threshold ("Your email open rate dropped 4% — here's what I think is happening")
- Assets aging out ("3 of your nurture emails have been in rotation 6+ months and are underperforming — want replacements?")
- Proof bank gaps ("You haven't added a new patient story in 45 days — this is limiting your content variety")
- Opportunity surfacing ("Your best-performing hook angle this month is [X] — you have no paid ads using this angle yet")
- Calendar gaps ("Your content calendar has no Level 1 posts scheduled next week — want me to add some?")

**6. IQ Profile Expansion**
IQ Claw continuously listens for information that expands the IQ Profile:
- New programs or offers mentioned → added to offer architecture
- New team members mentioned → added to role map
- New goals stated → added to vision document
- New frustrations surfaced → flagged as optimization opportunities

### IQ Claw's Persona

IQ Claw is not a chatbot. It is not a help desk. It is the expert's highest-performing operator — the person who knows the business better than anyone except the founder, and uses that knowledge to drive results.

**Voice:** Direct. Specific. High-agency. It doesn't ask if you want help — it tells you what it found, what it recommends, and what it needs from you to move. It doesn't flatter. It doesn't hedge unnecessarily. When it disagrees with a decision, it says so — once, clearly, with a specific reason — then executes the decision anyway if the expert confirms.

**The bar:** IQ Claw should make every expert feel like they have a world-class COO, growth strategist, and creative director working for them 24 hours a day who also happens to have perfect memory of every conversation they've ever had.

---

## Layer 3: The Patient-Facing AI — **V2 SCOPE**

> **Decision (March 26, 2026):** The patient-facing AI is deferred to V2. It requires a dedicated product conversation covering compliance scope (HIPAA, FDA, state medical board rules), monetization model, naming, content boundaries, EHR integration possibilities, and liability framing. These decisions should be made with real platform data from V1 users — not assumptions. Everything below is a placeholder for that conversation.

---

### The Product Decision

The expert wants their patients and leads to interact with an AI that represents their brand. The question is whether this lives inside clinicIQ or as a separate product.

**The answer: Inside clinicIQ, scoped as a patient education and lead nurture tool — not a clinical tool.**

Here is the reasoning:

A patient-facing diagnostic or treatment AI requires: HIPAA BAAs, FDA oversight risk, state medical board compliance, and per-session clinical liability management. That is a different product category entirely.

But a patient-facing **education and engagement AI** — one that answers questions based on the expert's published content, speaks in their voice, routes clinical questions to the expert's team, and functions as a lead nurture and patient education tool — lives squarely in the marketing and content layer. It is a smarter version of a website chatbot. It collects leads, warms prospects, answers common questions, and creates 24/7 brand presence. This is clinicIQ's lane, and it is a massive competitive advantage.

**What it is:** An AI assistant powered entirely by the expert's content library — their lead magnets, webinar educational content, blog posts, email sequences, and educational materials produced in clinicIQ. It speaks in their Voice DNA. It uses their mechanism language and positioning. It is their educational voice, available 24/7 to anyone who encounters their brand.

**What it is not:** A diagnostic tool. A treatment recommendation tool. A prescribing tool. A replacement for clinical care. Every response that approaches clinical territory routes with: *"That's a great question — and it's exactly the kind of thing [Expert Name] covers with patients directly. Here's how to connect with them: [link/form]."*

### Naming Convention

The patient AI belongs to the expert, not to clinicIQ. It is branded as the expert's AI, not clinicIQ's AI. clinicIQ provides the infrastructure; the expert provides the identity.

**How it's named:**
During platform setup, the expert is asked: *"What do you want to call your patient-facing AI assistant?"* They give it a name — ideally something that fits their brand. Dr. Sarah Chen might name it "Sarah's Health Guide." A hormone clinic might call it "HormonIQ." A gut health practice might call it "Gut Guide."

**Default if not named:** "[Expert First Name]'s Health AI"

This name appears:
- On the chat widget on their website/funnels
- In the first message of every conversation: *"Hi, I'm [Name], Dr. Sarah's AI health guide..."*
- On their branded URL: `ask.[expertdomain].com` or embedded in any funnel page

### What the Patient AI Does

**Content knowledge base:**
Everything produced in clinicIQ for educational purposes is fed into the patient AI's knowledge base: lead magnets, webinar educational content (not the close), blog posts, email nurture content, patient education materials. The AI answers from this library only — it never speculates beyond what the expert's content explicitly covers.

**Lead capture:**
When a visitor is engaging deeply, the patient AI offers natural transition points to opt-in:
- *"I actually have a free guide on this that goes much deeper — want me to send it to you?"*
- *"Dr. Sarah recently put together a training on exactly this — it's free, want the link?"*
These funnel directly into the expert's email sequences.

**Voice accuracy:**
The patient AI speaks in the expert's Voice DNA — same vocabulary, same rhythm, same warmth level, same mechanism language. A patient who interacts with the AI and then reads the expert's emails should feel like they're hearing from the same person.

**Clinical routing:**
Any question that approaches diagnosis, treatment, prescribing, or clinical recommendation is answered with a compassionate redirect:
- *"That's really important and it deserves a proper answer — not something I'm equipped to give. [Expert Name] works with patients on exactly this. Here's how to get on their schedule: [link]."*
- This routing is not a brush-off. It is a lead generation moment — the AI is routing warm, engaged prospects directly into the expert's funnel.

**Conversation insights (not PHI):**
The expert sees a dashboard of anonymized conversation trends: most common topics, most common questions, most common objections, most requested resources. This feeds directly back into the Content Builder's ideation — if 200 people this month asked about "hair loss and hormones," that becomes a content angle. No personally identifiable health information is stored or reported.

### Where It Lives

| Access Point | Description |
|---|---|
| **Website widget** | Embedded chat widget on the expert's website — bottom right corner, always visible |
| **Funnel pages** | Embedded on opt-in pages, thank you pages, and webinar registration pages |
| **Branded URL** | `ask.[expertdomain].com` — shareable, direct access |
| **Social bio link** | The expert can use the branded URL as their link-in-bio |
| **QR code** | Generated for print materials, event signage, business cards |

The patient AI is accessible to anyone — no login required. It is a public-facing tool. The expert manages it from within clinicIQ — updating the knowledge base, reviewing conversation insights, adjusting the routing behavior.

### Patient AI vs. IQ Claw — Clear Separation

| | IQ Claw | Patient AI |
|---|---|---|
| **User** | The expert | The expert's patients and leads |
| **Access** | Logged into clinicIQ | No login required |
| **Knowledge** | Full platform access — dossier, analytics, all agents | Expert's content library only |
| **Can trigger agents** | Yes | No |
| **Can access performance data** | Yes | No |
| **Persona** | High-agency operator | Warm, educational guide |
| **Clinical routing** | N/A | Always routes clinical questions to expert |
| **Lead capture** | N/A | Yes — routes to expert's funnel |
| **Branded as** | IQ Claw (clinicIQ brand) | Expert's chosen name (expert's brand) |

---

## How These Three Layers Connect

```
EXPERT
    │
    ▼
IQ CLAW (Expert AI Operator)
    │
    ├── Reads / writes to → IQ DRIVE (Asset Library)
    │
    ├── Orchestrates → ALL BUILDER AGENTS (Steps 12–16+)
    │                  Content Builder, Funnel Builder, Webinar Builder,
    │                  Email Builder, Ad Creative Builder, etc.
    │
    ├── Reads from → Analytics Dashboard (Layer 4)
    │
    └── Manages → PATIENT AI configuration and knowledge base
                  ↓
              PATIENT AI (Expert-branded, patient-facing)
                  │
                  ├── Powered by → IQ Drive content library
                  ├── Routes leads → Expert's funnel (Email sequences)
                  └── Reports trends → IQ Drive / IQ Claw dashboard
```

The expert interacts with IQ Claw. IQ Claw interacts with everything else. The patient AI is a downstream product — configured by the expert via IQ Claw, powered by what clinicIQ produces, generating leads that flow back into the platform.

---

## IQ Claw Agent Specification

IQ Claw is itself an agent — the most important one in the platform. It is the orchestration layer that connects the expert to every other agent.

```
IQ CLAW LEAD AGENT
├── Always-on: persistent across all platform screens
├── Full read access: Expert Dossier, IQ Profile, all Builder outputs,
│   IQ Drive, Analytics Dashboard, Monthly Master Plan
├── Full trigger access: all Builder agents + all Layer 4 agents
├── Proactive monitoring: performance alerts, calendar gaps, 
│   profile gaps, opportunity surfacing
└── Persona: direct, specific, high-agency, non-flattering

IQ CLAW SUB-AGENTS:

1. IQ Profile Manager
   Owns the living IQ Profile document
   Runs the 10-phase onboarding interview on first launch
   Pre-fills from dossier before asking any question
   Captures new information from every conversation and updates the profile
   Surfaces profile gaps proactively
   Produces the 9 deliverables from the completed interview

2. Request Router
   Parses every expert request and routes to the correct Builder agent
   Auto-populates context from dossier + IQ Profile before routing
   Confirms parameters with expert when ambiguous
   Monitors production and reports completion

3. Performance Analyst
   Live read on all platform analytics
   Interprets data — not just surfaces it
   Diagnoses underperformance with specific failure point identification
   Recommends specific actions with priority ranking

4. Proactive Intelligence Agent
   Monitors platform state continuously
   Triggers alerts when thresholds are breached
   Surfaces opportunities the expert hasn't asked about
   Recommends Monthly Master Plan adjustments based on current performance

5. Platform Navigator
   Answers any "how do I..." question
   Navigates the expert directly to relevant screens
   Onboards experts to new features as they're released

6. Patient AI Manager *(V2 — deferred)*
   Placeholder for the patient-facing AI management sub-agent.
   Will be specced when the patient AI product decision is finalized.
```

**IQ Claw agent count: 7** (Lead + 6 sub-agents)

---

## Implementation Notes

**These three platform layers are foundational — they affect every step from 12 onward.** Every Builder agent's output goes to the IQ Drive. Every expert interaction is mediated by IQ Claw. Every content asset eventually feeds the Patient AI's knowledge base.

**IQ Claw is built before the Builder agents are deployed** — it is the expert's onramp to the entire platform. Without IQ Claw, the expert navigates a complex multi-agent system manually. With IQ Claw, they just talk to it.

**The Patient AI launches when the expert has sufficient content in the IQ Drive** — minimum viable: one lead magnet, the webinar educational content, and 30 days of nurture emails. IQ Claw tells the expert when the knowledge base is rich enough to launch.

---

*clinicIQ Platform Architecture — v1.0*
*IQ Drive + IQ Claw + Patient-Facing AI*
*Referenced by: Steps 12–22, all Builder Agents, Layer 4 Analytics*
