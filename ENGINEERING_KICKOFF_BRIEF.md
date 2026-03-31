# ClinicIQ — Engineering Kickoff Brief
**Version 1.0 | March 30, 2026**
*For: Engineering & Dev Team — Internal Kickoff*
*Prepared by: Ryan Cole / ClinicIQ Product*

---

## What We're Building

ClinicIQ is an **Agentic-as-a-Service platform** for health experts. It automates the entire growth engine of a health expert's business — brand, strategy, content, funnels, emails, ads, and webinars — using AI agents that know the expert deeply and produce finished, publish-ready work on demand.

The expert never writes a caption, builds a funnel page, or touches a prompt. They just talk to the platform and it builds.

**The master build is 22 steps across 4 layers.** Steps 1–11 are fully documented and locked. Steps 12–22 are partially documented. The job right now is to build what exists and finish speccing what doesn't.

---

## The Architecture At-a-Glance

```
EXPERT
    │
    ▼
┌─────────────────────────────────────┐
│         IQ CLAW (Layer 0)           │  ← Expert's AI operator. The front door to everything.
│  "Tell me what you need — I handle  │
│   the rest."                        │
└──────────────┬──────────────────────┘
               │ routes to
    ┌──────────┼──────────────────────────┐
    ▼          ▼                          ▼
LAYER 1    LAYER 2                    LAYER 3
Onboarding  Strategy                  Builders
(Who you    (How to grow)             (Make the stuff)
 are)
    │          │                          │
    └──────────┴──────────────────────────┘
                         │
                         ▼
                 IQ DRIVE (Storage)
              Every asset produced lives here
                         │
                         ▼
               ANALYTICS DASHBOARD (Layer 4)
              Performance data feeds back in
                         │
                         ▼
                PATIENT AI (V2 — deferred)
```

---

## Layer-by-Layer Breakdown

---

### LAYER 1 — Onboarding Agent (Steps 1–7) ✅ FULLY DOCUMENTED

**What it does:** Builds a deep expert profile — Voice DNA, avatar psychology, offer stack, proof bank, mechanism, visual brand — across 164 data fields. This "Expert Dossier" is the intelligence that powers every other agent on the platform.

**Two modes:**
- **Fast-Start (20–30 min):** Minimum viable dossier (~55–70 fields). Unlocks Layer 2.
- **Deep-Dive:** All 164 fields. Unlocks full platform.

**Key decisions locked:**
- Single onboarding flow with smart pre-fill (no re-asking what's already known)
- Two payload formats: JSON (machine-readable for agents) + human-readable narrative
- `handoff_ready` flag gates downstream agents — Layer 2 doesn't run until this is `true`
- Achievement/gamification system baked into UX

**Agents in this layer:**

| Agent | Role |
|-------|------|
| Onboarding Lead Agent | Orchestrates the full interview |
| Web Scraper | Pulls expert's existing web presence |
| Voice DNA Analyst | Extracts voice/tone from existing content |
| Avatar Psychology Builder | Builds the 8-layer avatar + 5 Levels of Awareness map |
| Offer Architecture Builder | Extracts and scores the full offer stack |
| Proof Bank Miner | Extracts transformation stories |
| Story Miner | Extracts the founder/expert's origin story |
| Silent Diagnostician | Identifies gaps and opportunities without asking |
| Dossier Assembler | Compiles the 164-field structured JSON payload |
| Progress Endowment Engine | Manages gamification, achievements, and momentum |

**Agent count: ~10** (Onboarding Lead + ~9 sub-agents — to be finalized in Step 21)

**Output:** Expert Dossier (JSON + narrative) → handed to Layer 2

---

### LAYER 2 — Strategy Agents (Steps 8–11) ✅ FULLY DOCUMENTED

**What it does:** Takes the Dossier and produces the strategic operating system for the expert's growth — brand rules, positioning, content framework, monthly messaging, campaign calendar, and asset briefs. This layer runs once to set up the platform, then monthly to update messaging.

**Steps in this layer:**
- **Step 8 — Brand Strategy Agent:** Produces the Brand North Star Document — the expert's positioning, One Big Domino, ALWAYS/NEVER rules, Avatar Quick Reference, mechanism framing, content pillars. This is the creative guardrail that every Builder agent uses.
- **Step 9 — Growth Strategy Agent:** Produces the Monthly Master Plan + Monthly Messaging Brief — hook bank, content calendar, campaign structure, creative briefs for every asset type. Also includes the Creative Production sub-agent team.
- **Step 10 — Full Strategy Output Stack:** The compiled package of all Layer 2 outputs.
- **Step 11 — Strategy Layer Handoff Payload:** The exact package handed to the Builder Layer (Layer 3). Includes: Expert Dossier Brief, Brand North Star, Monthly Messaging Brief, Monthly Master Plan, and Asset Brief per request.

**Agents in this layer:**

| Agent | Role |
|-------|------|
| Brand Strategy Lead | Runs the full brand strategy session |
| Growth Strategy Lead | Runs the full growth strategy session |
| Core Orchestrator | Assembles the handoff payload + routes asset briefs to builders |
| Brand North Star Writer | Writes the positioning doc |
| Competitive Research Agent | Pulls and analyzes competitor landscape |
| Hook Bank Builder | Generates the expert's hook library |
| Campaign Architect | Builds the Monthly Master Plan structure |
| Creative Brief Generator | Produces the specific per-asset brief for each Builder request |
| Creative Production sub-agents (×10) | Produce detailed creative briefs by asset type |

**Agent count: ~17** (across both strategy agents — to be finalized in Step 21)

**Output:** Strategy Package (5 documents) → handed to Layer 3

---

### LAYER 3 — Builder Agents (Steps 12–16) ⚠️ PARTIALLY DOCUMENTED

This is where everything gets made. Steps 12–15 are fully documented. Step 16 is partially documented. Steps 16b (Program Builder) and 16c (Podcast Agent) are in progress.

---

#### Step 12 — Content Builder Agent ✅ Documented

**What it builds:** Instagram/Facebook images, carousels, b-roll, video scripts, UGC character scripts, captions — fully composited, platform-sized, and ready to publish.

**Two modes:**
- **Batch Mode:** Full week/month of content in one session
- **Quick-Create:** Single asset from a natural language request (target: <90 seconds)

**Notable features:**
- Awareness Level Distributor ensures content hits all 5 levels of buyer awareness
- Every batch is also paid ad R&D — best-performing organic posts flagged as ad candidates
- Voice QA Agent reviews every piece of copy before it moves to visual production
- Image Production calls Flux Pro 1.1 via fal.ai API (most photorealistic for health content)
- HTML/CSS Layout Generator + Puppeteer renders final composited PNGs

**Agent count: 16** (Content Builder Lead + 15 sub-agents)

---

#### Step 13 — Funnel & Webinar Builder Agents ✅ Documented

**What it builds:**
- **Funnel Builder:** Opt-in pages, registration pages, sales pages, order bumps, upsell pages, thank you pages — full funnel architecture
- **Webinar Builder:** Complete webinar scripts (Russell Brunson Perfect Webinar + Jason Fladlein True/False frameworks), VSL scripts, slide decks, Q&A scripts, live + recorded variants

**Agent count: Funnel = 10, Webinar = 11**

---

#### Step 14 — Email & SMS Builder Agent ✅ Documented

**What it builds:** Every email and SMS sequence in the growth engine — welcome, post-webinar, promo, nurture, non-buyer, re-engagement, one-offs. Plus the Monthly Non-Buyer Engine (automated 30-email rotating library).

**Agent count: 12** (Email & SMS Builder Lead + 11 sub-agents)

---

#### Step 15 — Ad Creative & Lead Magnet Builder Agents ✅ Documented

**What it builds:**
- **Ad Creative Builder:** Full Meta campaign specs — primary ad creative (static, video, carousel), hooks, angle variants, audience targeting recommendations, split-test architecture
- **Lead Magnet & Tool Builder:** PDFs, guides, quizzes, calculators, and **vibe-coded mini SaaS tools** (interactive web apps used as lead magnets)

**Agent count: Ad Creative = 11, Lead Magnet = 5**

---

#### Step 16 — Sales Script Builder + Program Builder + Website Builder + Podcast Agent ✅ Documented

**Four agents in one step:**

- **Sales Script Builder:** Phone/video consultation scripts, front desk scripts, discovery session scripts, full objection library, referral ask script, re-enrollment script. Built on Brunson's 4-question framework + Hormozi offer framing + health-specific belief architecture. **Agent count: 6**

- **Program Builder:** Full program delivery system — phase architecture, prescription-level protocols (supplement/food/lifestyle), complete course curriculum, hosted native course player inside IQ, patient AI assistant, block library, custom-per-patient builds from lab/intake data, coach call agendas, community content generation. Built-in course player (white-labeled, patient never sees IQ). **Agent count: 11**

- **Website Builder:** Full expert website — home, about, work with me, resources, blog template, contact/apply. Awareness-calibrated copy, mechanism-consistent, mobile-first HTML/CSS production, deployed to expert's domain. **Agent count: 6**

- **Podcast Agent:** Full podcast operating system — 20 sub-agents across 6 categories: show production (runsheet, show notes, slides, audience intelligence), SEO/distribution (episode article, back-catalog revival), launch & distribution (launch orchestration, clip intelligence, content repurposing), optimization (title/packaging, YouTube), audience growth (guest amplification, cross-promotion, Instagram DM funnel, review campaigns, paid promotion), and intelligence (analytics reporting, competitor intelligence, quarterly growth opportunities). Scale-activation tiers — every expert gets every agent, depth increases automatically with show metrics. Built on the Dr. Josh Axe Show's 20-agent system. Josh Axe's team deploys this as a clinicIQ power user. **Agent count: 21**

**Step 16 total: 26 agents (4 Leads + 22 sub-agents)**

---

### LAYER 4 — Measure, Adjust & Learn (Steps 17–20) ✅ Documented

**Step 17 — Analytics Dashboard:** Single source of truth. Pulls from Meta Ads Manager, GHL/CRM, email platform, Instagram, Facebook, TikTok, YouTube, Google Search Console, Apple Podcasts, Spotify, IQ Platform (program + production), and more — 15+ data sources, normalized into one schema. Red/yellow/green status on every metric. Thresholds start from industry benchmarks (set in Layer 2), auto-calibrate to the expert's own 60-day rolling baseline after Day 60, recalibrate every 90 days. Command view shows everything critical on one screen. **Agent count: 5**

**Step 18 — Performance Intelligence Agent:** The analyst. Every red/yellow flag triggers root cause analysis — not "your show rate is low" but the specific diagnosis with evidence ("cold traffic mix increased 36%, cold traffic shows at 35–45% vs. 65% for warm — traffic quality issue, not sequence issue"). Weekly opportunity scan surfaces positive anomalies, correlation patterns, replication opportunities. Cross-channel correlation agent finds relationships across data streams. **Agent count: 5**

**Step 19 — Optimization Agent:** The executor. Three modes: Auto-Execute (standing authorization for defined categories), Approve-and-Execute (expert clicks approve, platform executes), and Propose-Only (human-required changes with a complete brief). Computer-executable changes (pause underperforming ads, shift budget, swap subject lines, update podcast titles, reorder lessons) execute automatically or on approval. Human-required changes (new webinar angle, protocol updates, offer changes) come with a full brief. Every change tracked for impact. **Agent count: 6**

**Step 20 — Learning & Feedback Engine:** Closes the loop. Captures all performance data, optimization outcomes, A/B test results, expert approvals/rejections/edits, and IQ Claw conversation signals. Updates expert-specific priors (Voice DNA, hook rankings, audience intelligence, ad creative performance, thresholds) and platform-level priors (anonymized universal benchmarks that improve defaults for all experts). Every agent in every layer gets smarter every cycle. **Agent count: 5**

**Layer 4 total: 21 agents (4 Leads + 17 sub-agents)**

---

### SYSTEM-WIDE (Steps 21–22) ✅ Documented

- **Step 21 — Cross-Agent Consistency Audit:** Full review of all 22 steps. 2 blocking issues, 10 important findings, 4 minor. Key resolutions: Voice QA + Brand QA consolidated into shared Output Quality Agent (Core Orchestrator); Performance Learning Agent removed from Content Builder (Layer 4 owns this); "Growth Blueprint" standardized to Monthly Master Plan + Expert Dossier; Core Orchestrator added to master count; Onboarding confirmed at 11 agents.
- **Step 22 — Final Master Agent Description Document:** Single source of truth for all ~168 agents. Complete sub-agent tables, corrected counts, universal data flow map, handoff payload standards, 8 open architecture decisions. File: `step22_master_agent_document.md`

---

### PLATFORM ARCHITECTURE — IQ Drive + IQ Claw (Cross-Cutting) ✅ FULLY DOCUMENTED

These are not steps — they're the foundational infrastructure every step depends on.

**IQ Drive (Asset Storage):**
- Every asset produced by any Builder agent is stored here with rich metadata (asset type, platform, status, awareness level, hook angle, CTA type, performance score, etc.)
- Smart filters, version history, in-drive editing
- Performance data overlay (reach, saves, CTR, conversion rates, etc.)

**IQ Claw (Expert AI Operator):**
- The expert's always-on operator — persistent panel accessible from every screen
- Knows the expert at two levels: Standard Dossier (from onboarding) + IQ Profile (deeper living document)
- Routes all expert requests to the correct Builder agent with full context pre-loaded
- Orchestrates multi-agent workflows for complex requests
- Proactive alerts (performance drops, content gaps, optimization opportunities)
- Runs a 10-phase IQ Profile interview on first launch

**IQ Claw sub-agents:**

| Sub-Agent | Role |
|-----------|------|
| IQ Profile Manager | Owns the living IQ Profile, runs the 10-phase interview |
| Request Router | Parses requests, routes to correct Builder, monitors production |
| Performance Analyst | Live analytics interpretation + diagnosis |
| Proactive Intelligence Agent | Continuous monitoring, alerts, opportunity surfacing |
| Platform Navigator | "How do I..." answers + direct screen navigation |
| Patient AI Manager | *(V2 — deferred)* |

**IQ Claw agent count: 7** (IQ Claw Lead + 6 sub-agents)

---

## Full Agent Count — Current State

| Layer | Agent Group | Lead Agents | Sub-Agents | Total |
|-------|------------|-------------|------------|-------|
| Platform | IQ Claw | 1 | 6 | **7** |
| Layer 1 | Onboarding Agent | 1 | ~9 | **~10** |
| Layer 2 | Brand Strategy | 1 | ~4 | ~5 |
| Layer 2 | Growth Strategy | 1 | ~11 | ~12 |
| Layer 2 | Core Orchestrator | 1 | 1 | ~2 |
| Layer 3 | Content Builder | 1 | 12 | **13** |
| Layer 3 | Funnel Builder | 1 | 9 | **10** |
| Layer 3 | Webinar Builder | 1 | 10 | **11** |
| Layer 3 | Email & SMS Builder | 1 | 11 | **12** |
| Layer 3 | Ad Creative Builder | 1 | 9 | **10** |
| Layer 3 | Lead Magnet Builder | 1 | 4 | **5** |
| Layer 3 | Sales Script Builder | 1 | 5 | **6** |
| Layer 3 | Program Builder | 1 | 10 | **11** |
| Layer 3 | Website Builder | 1 | 5 | **6** |
| Layer 3 | Podcast Agent | 1 | 20 | **21** |
| Layer 4 | Analytics Dashboard | 1 | 4 | **5** |
| Layer 4 | Performance Intelligence | 1 | 4 | **5** |
| Layer 4 | Optimization Agent | 1 | 5 | **6** |
| Layer 4 | Learning & Feedback Engine | 1 | 4 | **5** |
| **TOTAL (documented)** | | **~20** | **~143** | **~163+** |

---

## What's Done vs. What Still Needs Work

### ✅ Fully Documented & Locked
- Layer 1: All 7 steps — Onboarding Agent complete
- Layer 2: All 4 steps — Strategy Agents complete
- Layer 3: Steps 12–16 — All Builder Agents complete
- Layer 4: Steps 17–20 — Analytics, Intelligence, Optimization, Learning complete
- Platform Architecture: IQ Drive + IQ Claw complete

### ⚠️ In Progress / Partially Done
- Step 13b: Webinar Builder Deep Spec — supplemental detail doc exists, may need finalization

### ❌ Not Yet Documented
- System-Wide (Steps 21–22): ✅ Complete — Consistency Audit + Final Master Document

---

## Architecture Health Check — Best Practices Review

*This section was added specifically for the kickoff: an honest assessment of the current architecture against 2026 standards.*

### What We're Getting Right ✅

**1. Lead Agent + Sub-Agent Model**
Every major agent has a Lead Agent that orchestrates specialized sub-agents. This is exactly the pattern that's proven at production scale — it's what Anthropic calls "orchestrator-subagent" and what enterprise deployments run. The Lead Agent handles context and routing; sub-agents are narrow experts. Error isolation is clean.

**2. Single Responsibility Per Sub-Agent**
Each sub-agent owns one clearly defined output (Voice QA, Image Production, Copy Writer, etc.). This is correct. Sub-agents that try to do too much become unpredictable and hard to debug in production.

**3. Structured Handoff Payloads**
The Dossier → Layer 2 → Builder handoff chain uses defined payload structures (Step 7, Step 11). This is essential. Agents that share context through unstructured natural language break at scale. Structured payloads are version-controllable and testable.

**4. Quality Gates Between Layers**
`handoff_ready` flags between layers prevent partial data from reaching downstream agents. This is the right call.

**5. Tool Abstraction Layer (Content Builder)**
Every external API (Flux, fal.ai, etc.) is called through an abstraction layer. Best practice for longevity — swap models without touching the pipeline.

**6. Performance Feedback Loop (Layer 4)**
Designed into the architecture from the start. Most platforms skip this and bolt it on later. Having it as a first-class layer means agents improve over time instead of degrading.

### Questions to Resolve Before Build ⚠️

**1. Consolidation Opportunity — Layer 2 Creative Sub-Agents vs. Layer 3 Builders**
Layer 2 (Growth Strategy) has a "Creative Production" sub-agent team of 10 that writes creative *briefs* for every asset type. Layer 3 has the actual Builder agents that produce the assets. There's potential overlap that needs a clear dividing line in implementation:
- Layer 2 sub-agents produce *briefs* (strategy-level specs)
- Layer 3 agents do the *production* (actual asset generation)
This distinction is clean in the docs but must be enforced in implementation. If brief-writing logic bleeds into the builders, you get duplication and conflicting instructions.

**2. Voice QA Agent — Single or Shared?**
Currently, Voice QA lives inside the Content Builder as sub-agent #4. But every Builder agent needs voice quality control — Emails, Funnels, Webinar scripts all need the same Voice DNA check. Options:
- **Option A (Current):** Each Builder has its own Voice QA sub-agent (adds complexity, potential inconsistency)
- **Option B (Recommended):** Single shared Voice QA Agent called by any Builder via IQ Claw routing (consistent, single source of truth for Voice DNA enforcement)
**Recommendation: Shared Voice QA Agent as a platform service.**

**3. Brand QA — Same Question**
Same issue as Voice QA. The Content Builder has a Brand QA Agent for visual assets. The Ad Creative Builder will need it too. Should be a shared service.

**4. Performance Learning Agent — Single or Per-Builder?**
Currently scoped inside the Content Builder. But email performance, funnel conversion data, and ad ROAS all feed different builders. A single Performance Learning Agent at the platform level (Layer 4) that all builders query is cleaner than separate learning loops per builder.
**Recommendation: Elevate to Layer 4 as a platform-level agent.**

**5. Agent Count — Is ~100 the Right Number?**
Short answer: **Yes, if they're real sub-agents with scoped single jobs. No, if they're just labels on prompt variants.**
2026 best practice is clear: narrow agents that each own one output type, with a Lead Agent orchestrating. 100 agents across a platform of this complexity is not excessive — it's appropriate. The anti-pattern to avoid is "god agents" that try to produce 5 different outputs in one prompt. Those fail at quality and scale.
**The concern isn't count. It's clarity of responsibility. Every agent must have one job, one output format, and one clear hand-off.**

**6. Hybrid Model Architecture**
Current docs don't specify which LLM powers which agents. 2026 best practice is **hybrid SLM + LLM orchestration** — fast/cheap smaller models for structured extraction tasks, premium models (Claude, GPT-4o, Gemini) for quality-critical outputs (Voice QA, copy writing, strategy). This is a cost-at-scale decision the engineers need clarity on.
**Recommendation: Define model tiers per agent type before build starts.**

**7. Memory and State Architecture**
The IQ Profile and Expert Dossier are described as living documents. The platform needs a clear answer on: where does agent memory live, how is it accessed per-session, and how are updates persisted? This is the most common production failure point in multi-agent systems.
**Recommendation: Define the memory/state layer as a first-class architecture decision — parallel to the IQ Drive.**

---

## The Open Build Queue (Priority Order)

| Priority | Item | Status |
|----------|------|--------|
| 1 | IQ Claw Lead + sub-agents | ❌ Not built |
| 2 | IQ Drive data layer + metadata schema | ❌ Not built |
| 3 | Onboarding Agent (Layer 1) | ❌ Not built — fully specced |
| 4 | Brand Strategy Agent (Layer 2) | ❌ Not built — fully specced |
| 5 | Growth Strategy Agent (Layer 2) | ❌ Not built — fully specced |
| 6 | Core Orchestrator + handoff payload | ❌ Not built — fully specced |
| 7 | Content Builder Agent (Layer 3) | ❌ Not built — fully specced |
| 8 | Email & SMS Builder Agent (Layer 3) | ❌ Not built — fully specced |
| 9 | Funnel Builder Agent (Layer 3) | ❌ Not built — fully specced |
| 10 | Webinar Builder Agent (Layer 3) | ❌ Not built — fully specced |
| 11 | Ad Creative Builder (Layer 3) | ❌ Not built — fully specced |
| 12 | Lead Magnet Builder (Layer 3) | ❌ Not built — fully specced |
| 13 | Sales Script Builder (Layer 3) | ✅ Documented |
| 14 | Program Builder (Layer 3) | ✅ Documented |
| 15 | Website Builder (Layer 3) | ✅ Documented |
| 16 | Podcast Agent (Layer 3) | ✅ Documented |
| 15 | Analytics Dashboard (Layer 4) | ❌ Not specced |
| 16 | Performance Intelligence + Optimization (Layer 4) | ❌ Not specced |
| 17 | Monthly Review Agent (Layer 4) | ❌ Not specced |
| 18 | Step 21 Consistency Audit | ✅ Complete |
| 19 | Step 22 Master Agent Description | ✅ Complete |
| 20 | Patient AI (V2) | ❌ Deferred — decision pending |

---

## Key Engineering Decisions Needed

These are the things the engineering team needs explicit answers on before they can build:

1. **Framework choice:** LangGraph, CrewAI, OpenAI Agents SDK, or custom? (All are production-viable in 2026 — this is a team capability and cost decision)
2. **Model tier map:** Which LLM/SLM for which agent type?
3. **Memory/state backend:** How does the Dossier + IQ Profile persist and get accessed across sessions?
4. **Shared services:** Confirm Voice QA + Brand QA as platform-level shared agents (not per-builder)
5. **IQ Drive tech stack:** What's the underlying storage + metadata layer? (Object storage + vector DB is the most common pattern)
6. **Deployment model:** How are agents deployed — serverless functions, containers, hosted API endpoints?
7. **The interface layer:** What does IQ Claw's persistent panel actually run on? (Web app, embedded widget, native app?)

---

## One-Sentence Summary (for the engineers)

> We are building a multi-agent content and growth platform where a health expert talks to IQ Claw, which routes requests to ~12 specialized Builder agents, each coordinating ~5–15 sub-agents to produce finished assets stored in IQ Drive — the whole system calibrated to the expert's unique voice, brand, and offer from a deep onboarding interview.

---

*ClinicIQ Engineering Kickoff Brief — v1.0*
*All detailed specs: `/home/work/.openclaw/workspace/cliniciq/`*
