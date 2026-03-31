# clinicIQ — Step 22: Final Master Agent Description Document
**Version 1.0 — Post-Audit**
*The single source of truth for every agent on the clinicIQ platform*
*Incorporates all Step 21 audit resolutions*

---

## How to Use This Document

This is the canonical reference for every agent on the clinicIQ platform. Engineers build from this. PMs scope from this. QA tests against this. If there is a conflict between this document and any step-level spec, this document takes precedence — it reflects all post-audit decisions.

Every agent entry includes: name, layer/category, role (one sentence), inputs, outputs, execution mode, and the downstream agents it feeds.

---

## Platform Overview

```
EXPERT
    │
    ▼
IQ CLAW (Expert AI Operator)
    │ routes to
    ├─────────────────────────────────────────────┐
    ▼                                             ▼
LAYER 1                                    PLATFORM SERVICES
Onboarding Agent                           Core Orchestrator
    │                                      Output Quality Agent
    ▼ Expert Dossier                       IQ Drive
LAYER 2                                    Block Library
Brand Strategy Agent                            │
Growth Strategy Agent                           │ (shared services)
Core Orchestrator                               │
    │                                           │
    ▼ Strategy Package (5 docs)                 │
LAYER 3 (Builder Agents)  ◄─────────────────────┘
Content Builder
Funnel Builder
Webinar Builder
Email & SMS Builder
Ad Creative Builder
Lead Magnet Builder
Sales Script Builder
Program Builder
Website Builder
Podcast Agent
    │
    ▼ All assets → IQ Drive
LAYER 4 (Intelligence Loop)
Analytics Dashboard
Performance Intelligence Agent
Optimization Agent
Learning & Feedback Engine
    │
    └── Updated priors → all agents (continuous)
    └── Monthly review → Layer 2 (monthly trigger)
```

---

## PLATFORM SERVICES

---

### IQ Claw — Expert AI Operator
**Layer:** Platform (cross-cutting)
**Role:** The expert's always-on AI operator — routes all requests, orchestrates multi-agent workflows, interprets analytics, surfaces alerts, and maintains the expert's living IQ Profile.

| Sub-Agent | Role |
|-----------|------|
| IQ Profile Manager | Owns the living IQ Profile; runs 10-phase interview on first launch; captures profile updates from every conversation |
| Request Router | Parses expert requests; routes to correct Builder agent with full context pre-loaded; monitors production |
| Performance Analyst | Reads Layer 4 analytics data; surfaces interpreted insights to expert in plain language |
| Proactive Intelligence Agent | Continuous monitoring; surfaces alerts (performance drops, content gaps, opportunities) proactively |
| Platform Navigator | Answers "how do I..." questions; navigates expert directly to relevant platform screen |
| Patient AI Manager | *(V2 — deferred)* Manages patient-facing AI system |

**Agent count: 7** (IQ Claw Lead + 6 sub-agents)
**Inputs:** Expert requests (natural language), Expert Dossier, IQ Profile, Layer 4 data feed
**Outputs:** Routed requests to all Builder agents; IQ Profile updates; expert-facing alerts and insights

---

### Core Orchestrator — Production Pipeline Manager
**Layer:** Platform (between Layer 2 and Layer 3)
**Role:** Validates that all quality gates are green before any Builder agent activates, generates Asset Briefs from the Strategy Package, routes briefs to Builder agents, and runs the Output Quality Agent on all completed outputs.

| Sub-Agent | Role |
|-----------|------|
| Gate Checker | Validates all 6 quality gates before any Builder agent is activated |
| Brief Generator | Produces per-asset briefs from Monthly Master Plan + Monthly Messaging Brief |
| Router | Routes each Asset Brief to the correct Builder agent |
| Context Loader | Pre-loads the relevant dossier sections and strategy documents into Builder agent context |
| Output Tracker | Tracks asset status: in-brief → in-production → in-review → approved → deployed |
| **Output Quality Agent** | Runs Voice QA + Brand QA on every Builder output; pass → deliver to expert; fail → rewrite request back to Builder; 2 failures → "Needs Your Eye" flag |

**Agent count: 7** (Core Orchestrator Lead + 6 sub-agents)

**The 6 Quality Gates (must all be green before any Builder activates):**
1. Expert Dossier `handoff_ready: true`
2. Brand North Star Part 2 complete (Output Quality Agent checks)
3. Growth Blueprint unit economics pass (LTV:CAC ≥ 3:1 pessimistic)
4. Monthly Master Plan produced
5. Monthly Messaging Brief produced
6. Asset Brief generated for this specific request

**Inputs:** Expert Dossier, Brand North Star, Monthly Master Plan, Monthly Messaging Brief, Builder agent outputs
**Outputs:** Asset Briefs (to Builder agents), quality-passed outputs (to expert), quality-failed rewrites (back to Builder)

---

### IQ Drive — Asset Storage and Management
**Layer:** Platform (cross-cutting)
**Role:** The single repository for every asset produced in clinicIQ — with structured metadata that makes the library intelligent, searchable, and performance-aware.

**Not an agent team — a platform service.** All Builder agents write to IQ Drive on output. Layer 4 reads performance data from IQ Drive. Expert browses, filters, edits, and publishes from IQ Drive.

**Metadata schema per asset:** asset type, platform, status, awareness level, hook angle, CTA type, campaign month, phase (if program), performance score, version history.

---

---

## LAYER 1 — ONBOARDING AGENT

**Steps:** 1–7
**Role:** Conducts a structured expert interview to build the 164-field Expert Dossier — the intelligence that powers every other agent on the platform.

### Confirmed Sub-Agent Team (10 agents)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Onboarding Lead Agent | Orchestrates the full interview; manages flow, pacing, and completion |
| 1 | Web Scraper | Pulls expert's existing web presence (website, social, Google Business) for pre-population |
| 2 | Voice DNA Analyst | Passive voice capture throughout session; confirms and locks Voice DNA profile in Section 2 |
| 3 | Avatar Psychology Builder | Extracts all 8 avatar layers + 5 Levels of Awareness determination |
| 4 | Offer Architecture Builder | Extracts and scores full offer stack; Hormozi value equation; guarantee architecture |
| 5 | Webinar Raw Material Extractor | Extracts One Big Domino, 3 Secrets, epiphany bridge, mechanism — webinar raw inputs |
| 6 | Proof Bank Miner | Extracts patient/client transformation stories; populates proof bank |
| 7 | Story Miner | Extracts expert's personal origin story and patient transformation arc |
| 8 | Silent Diagnostician | Gap analysis and priority flag generation — identifies what's missing without asking |
| 9 | Dossier Assembler | Compiles all sub-agent outputs into the final 164-field JSON payload + human-readable narrative |
| 10 | Progress Endowment Engine | Score calculation, achievement triggers, gamification, reflection moments |

**Agent count: 11** (Lead + 10 sub-agents)

**Primary Output:** Expert Dossier (JSON + narrative) with `handoff_ready: true` flag
**Feeds into:** Layer 2 (Brand Strategy Agent + Growth Strategy Agent), IQ Claw (IQ Profile base), all Layer 3 Builder agents (read-only)

---

---

## LAYER 2 — STRATEGY AGENTS

**Steps:** 8–11
**Role:** Takes the Expert Dossier and produces the Strategic Operating System — brand rules, positioning, monthly messaging, campaign calendar, and asset briefs.

---

### Brand Strategy Agent (Step 8)
**Role:** Produces the Brand North Star Document — the expert's positioning, One Big Domino, ALWAYS/NEVER rules, and all creative guardrails that every Builder agent uses.

| Sub-Agent | Role |
|-----------|------|
| Brand Strategy Lead | Orchestrates the full brand strategy session |
| Brand North Star Writer | Produces the full Brand North Star Document (Parts 1 + 2) |
| Competitive Research Agent | Pulls and analyzes competitor landscape for positioning differentiation |
| Hook Bank Seeder | Generates the initial hook library aligned with mechanism and avatar |
| Brand QA Validator | Validates Brand North Star Part 2 completeness before marking it production-ready |

**Agent count: ~5** (to be finalized — sub-agent list confirmed in audit)
**Primary Output:** Brand North Star Document (Parts 1 + 2)
**Feeds into:** Core Orchestrator (required read), Output Quality Agent (standard for QA), all Layer 3 Builder agents

---

### Growth Strategy Agent (Step 9)
**Role:** Produces the Monthly Master Plan, Monthly Messaging Brief, and Growth Blueprint — the campaign-level operating documents that drive all Layer 3 production each month.

| Sub-Agent | Role |
|-----------|------|
| Growth Strategy Lead | Orchestrates the full growth strategy session |
| Monthly Planner Sub-Agent | Builds the Monthly Master Plan (campaign calendar, hook bank, creative briefs) |
| Messaging Brief Writer | Produces the Monthly Messaging Brief (angle map, hook bank, objection library) |
| Campaign Architect | Structures campaign sequencing and multi-channel coordination |
| Competitive Research Agent | Growth-specific competitive analysis (adjacent to Brand Strategy's version — different angle) |
| Unit Economics Validator | Runs the LTV:CAC model; validates Gate 3 before Layer 3 activates |
| Creative Brief Generator | Produces the per-asset brief for each Builder request — handed to Core Orchestrator |
| Creative Production Sub-Agents (×7) | Produce detailed creative briefs by asset type (content, email, funnel, webinar, ads, lead magnet, video) |

**Agent count: ~12** (to be finalized)
**Primary Outputs:** Monthly Master Plan, Monthly Messaging Brief, Growth Blueprint (unit economics + traffic strategy section)
**Feeds into:** Core Orchestrator, all Layer 3 Builder agents, Layer 4 Learning Engine (monthly feedback loop)

---

### Core Orchestrator (Step 11)
*(Defined above under Platform Services — classified as platform-level, not Layer 2-specific)*

---

---

## LAYER 3 — BUILDER AGENTS

**Steps:** 12–16
**Role:** Produce every finished, publish-ready asset in the expert's growth engine.

**Universal inputs for all Builder agents:**
- Expert Dossier Brief (voice, avatar, offer, mechanism)
- Brand North Star Part 2 (operational rules, ALWAYS/NEVER, positioning)
- Monthly Messaging Brief (hook bank, angle map, current campaign focus)
- Monthly Master Plan Brief (what's being built this month, primary CTA)
- Asset Brief from Core Orchestrator (specific instructions for this asset)

**Universal output routing:**
- All finished assets → IQ Drive
- All finished assets → Output Quality Agent (Voice QA + Brand QA) before delivery to expert
- All performance data → Layer 4 Analytics Dashboard

---

### Content Builder Agent (Step 12) — UPDATED POST-AUDIT
*Note: Voice QA Agent (was #4), Brand QA Agent (was #12), and Performance Learning Agent (was #13) removed — functions transferred to Output Quality Agent (platform service) and Layer 4 Learning Engine.*

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Content Builder Lead | Orchestrates full content production for the month (batch and quick-create modes) |
| 1 | Ideation Engine | Generates 30+ content concepts per month from Monthly Messaging Brief hook bank |
| 2 | Awareness Level Distributor | Allocates concepts across 5 Levels of Awareness to target distribution |
| 3 | Copy & Script Writer | *[Merged: Copy Writer + Script Formatter]* Writes all copy + formats video/UGC scripts |
| 4 | Template Manager | Selects and configures the correct visual template per asset type |
| 5 | Visual Production Agent | *[Merged: Visual Direction + Image Production]* Writes image prompts + executes Flux/Kling/Runway generation |
| 6 | HTML/CSS Layout Generator + Renderer | Writes layout code + renders final composited PNGs via Puppeteer |
| 7 | UGC Character Script Writer | Writes patient/character UGC scripts (first-person transformation story format) |
| 8 | B-Roll Direction Agent | Writes cinematic b-roll direction and shot sequences |
| 9 | Carousel Builder | Assembles multi-slide carousels from individual slide outputs |
| 10 | Publishing Prep Agent | *[Merged: Ad Candidate Tagger + Content Scheduler]* Evaluates ad candidates + maps to content calendar |
| 11 | Asset Library Manager | Organizes all finished assets in IQ Drive with full metadata tagging |

**Agent count: 12** (Content Builder Lead + 11 sub-agents)

---

### Funnel Builder Agent (Step 13)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Funnel Builder Lead | Orchestrates full funnel architecture and page production |
| 1 | Page Strategy Agent | Determines build sequence from Monthly Master Plan funnel variant |
| 2 | Page Copy Writer | Writes all copy for every funnel page (awareness-calibrated) |
| 3 | Social Proof Block Builder | Formats testimonials, case studies, and proof elements per page |
| 4 | Offer Stack Presenter | Structures and writes the value stack and offer presentation sections |
| 5 | Page Layout Generator | Writes HTML/CSS/JS for every page (conversion-optimized, mobile-first) |
| 6 | Integration Configurator | Injects email platform, payment, pixel, and calendar integrations from tech stack |
| 7 | Mobile QA Agent | Validates all pages at 375px, 414px, 768px — flags layout breaks |
| 8 | CTA Architecture Agent | Places and writes CTAs per page with correct funnel routing |
| 9 | Funnel Flow Validator | Confirms every page connects correctly to the next; no broken routing |

**Agent count: 10** (Funnel Builder Lead + 9 sub-agents)

---

### Webinar Builder Agent (Step 13b)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Webinar Builder Lead | Orchestrates full webinar script production |
| 1 | Story Architect | Writes the epiphany bridge and origin story for the webinar narrative |
| 2 | Three Secrets Writer | Writes the 3 false-belief-breaking secret reveals with mechanism bridges |
| 3 | Stack Builder | Constructs the offer stack presentation with value assignments |
| 4 | Close Writer | Writes the sales close sequence (trial close, hard close, guarantee reveal) |
| 5 | Q&A Script Writer | Produces live Q&A response scripts for top predicted objections |
| 6 | Slide Direction Agent | Produces full slide deck brief (visual direction + content per slide) |
| 7 | VSL Adaptation Agent | Adapts webinar script to VSL format (shorter, tighter, no live sections) |
| 8 | Evergreen Conversion Agent | Adapts webinar for evergreen auto-webinar delivery |
| 9 | Pattern Interrupt Designer | Inserts retention engineering (stories, demonstrations, polls, re-hooks) at 10-min intervals |
| 10 | Webinar QA Agent | Validates full script against Perfect Webinar framework completion standards |

**Agent count: 11** (Webinar Builder Lead + 10 sub-agents)

---

### Email & SMS Builder Agent (Step 14)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Email & SMS Builder Lead | Orchestrates all email and SMS sequence production |
| 1 | Sequence Architect | Designs the full sequence map: trigger, cadence, branch logic |
| 2 | Subject Line Specialist | Writes and tests subject lines for every email (3 variants per email) |
| 3 | Welcome Sequence Writer | Writes the new subscriber welcome series |
| 4 | Post-Webinar Sequence Writer | Writes the non-buyer and buyer post-webinar follow-up sequences |
| 5 | Promo Campaign Writer | Writes time-sensitive promotional email sequences |
| 6 | Nurture Sequence Writer | Writes long-form evergreen nurture content sequences |
| 7 | Re-Engagement Writer | Writes the inactive subscriber re-engagement sequence |
| 8 | SMS Copy Writer | Writes all SMS touchpoints (brief, high-urgency, link-driven) |
| 9 | Non-Buyer Engine Builder | Builds the Monthly Non-Buyer Engine (30-email rotating library) |
| 10 | Personalization Agent | Inserts conditional content blocks based on subscriber segment data |
| 11 | Email QA Agent | Validates all sequences for deliverability triggers, link accuracy, and voice consistency |

**Agent count: 12** (Email & SMS Builder Lead + 11 sub-agents)

---

### Ad Creative Builder Agent (Step 15) — UPDATED POST-AUDIT
*Note: Brand QA Agent removed — function transferred to Output Quality Agent (platform service).*

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Ad Creative Builder Lead | Orchestrates full Meta ad creative production |
| 1 | Hook Intelligence Agent | Builds the expert's hook library; ranks hooks by performance data from Layer 4 |
| 2 | Angle Architect | Generates 5–7 creative angles per campaign from the hook bank |
| 3 | Ad Copy Writer | Writes primary text, headlines, and descriptions for all ad variants |
| 4 | Visual Production Agent | *[Merged: Visual Direction + Static Image Production]* Writes prompts + renders all static ad creatives |
| 5 | Video & B-Roll Production Agent | Executes video briefs (Kling v1.6 / Runway Gen-3) + ad-specific text overlay timing |
| 6 | UGC Script Writer | Writes expert-as-UGC and patient/character UGC scripts |
| 7 | Retargeting Creative Specialist | Produces warm and hot retargeting variants (proof-focused, objection-specific, urgency) |
| 8 | Advantage+ Creative Packager | Assembles all creative into Advantage+ compatible pools; formats for Meta Ads Manager import |
| 9 | Ad Performance Analyst | Monitors live ad performance; flags refresh needs; updates hook performance data |

**Agent count: 10** (Ad Creative Builder Lead + 9 sub-agents)

---

### Lead Magnet & Tool Builder Agent (Step 15b)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Lead Magnet Builder Lead | Orchestrates lead magnet and interactive tool production |
| 1 | Lead Magnet Strategist | Selects format (PDF, quiz, calculator, mini-SaaS) based on funnel position and avatar stage |
| 2 | Content Writer | Writes all lead magnet copy (guides, checklists, reports) in expert's voice |
| 3 | Quiz & Calculator Builder | Builds interactive logic for quizzes and calculators |
| 4 | Vibe-Code Mini SaaS Builder | Builds interactive web tools (HTML/CSS/JS) used as high-value lead magnets |

**Agent count: 5** (Lead Magnet Builder Lead + 4 sub-agents)

---

### Sales Script Builder Agent (Step 16a)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Sales Script Builder Lead | Orchestrates production of all sales call and consultation scripts |
| 1 | Discovery Architect | Builds the core discovery question sequence (4 Brunson phases, avatar-specific) |
| 2 | Script Writer | Writes full word-for-word scripts for all 6 script types with branching logic |
| 3 | Objection Library Builder | Writes full objection responses (acknowledge → validate → reframe → bridge → re-offer) |
| 4 | Roleplay Scenario Generator | Produces 5–8 training roleplay scenarios with ideal script walkthroughs |
| 5 | Script Performance Analyst | *(Layer 4 trigger)* Monitors call conversion data; recommends script revisions |

**Agent count: 6** (Sales Script Builder Lead + 5 sub-agents)

---

### Program Builder Agent (Step 16b)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Program Builder Lead | Orchestrates complete program creation — type selection, blueprint, build, delivery |
| 1 | Phase Architect | Builds phase sequence with clinical rationale + brand naming options |
| 2 | Protocol Prescription Agent | Generates prescription-level protocols (supplements, food, lifestyle) per phase |
| 3 | Curriculum Architect | Builds full curriculum map — modules, lessons, sequence, resource requirements |
| 4 | Lesson Script Writer | Writes word-for-word video scripts for every lesson; module intros/outros; orientation |
| 5 | Protocol Card & Resource Producer | Produces dose cards, food lists, trackers, quizzes, infographics, specialty guides |
| 6 | Coach Meeting Architect | Produces intake/phase/graduation call agendas + async messaging templates |
| 7 | Community Content Generator | Produces 7 Facebook posts/week per phase + weekly live session outlines |
| 8 | Patient Intake Processor | *(Custom-per-patient builds)* Reads labs/intake → Patient Protocol Profile → custom adjustments |
| 9 | Patient AI Trainer | Builds Ask AI knowledge base; manages alert queue; monitors content gap patterns |
| 10 | Block Library Manager | Tags and saves reusable blocks; surfaces relevant blocks during new builds |

**Agent count: 11** (Program Builder Lead + 10 sub-agents)
**Platform:** IQ Course Player (built inside clinicIQ — white-labeled at expert's domain)

---

### Website Builder Agent (Step 16d)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Website Builder Lead | Orchestrates full website architecture, copy, and production |
| 1 | Site Architecture Agent | Builds site map, page hierarchy, CTA hierarchy, internal linking structure |
| 2 | Page Copy Writer | Writes full copy for every page — awareness-calibrated per page type |
| 3 | Story Architect | Writes full About Page narrative + abbreviated Home Page story block |
| 4 | Visual Direction & Layout Agent | Produces HTML/CSS per page; GrapesJS component structure; Puppeteer preview renders; deploys via Caddy |
| 5 | Website QA Agent | Validates message consistency, CTA alignment, mobile rendering across all pages |

**Agent count: 6** (Website Builder Lead + 5 sub-agents)

---

### Podcast Agent (Step 16c)

**21 sub-agents across 6 categories — see `step16c_podcast_agent_full_spec.md` for full detail.**

| Category | Sub-Agents |
|----------|-----------|
| Show Production (4) | P1 Runsheet Agent, P2 Show Notes & Research, P3 Slide Deck, P4 Audience Intelligence |
| SEO & Distribution (2) | S1 SEO + GEO Article, S2 Back-Catalog Revival |
| Launch & Distribution (3) | L1 Launch Orchestration, L2 Clip Intelligence, L3 Content Repurposing |
| Optimization (2) | O1 Title & Packaging, O2 YouTube Optimization |
| Audience Growth (5) | G1 Guest Amplification, G2 Cross-Promotion, G3 Instagram DM Funnel, G4 Review & Follow Campaign, G5 Paid Promotion |
| Intelligence & Analytics (3) | I1 Analytics Reporting, I2 Competitor Intelligence, I3 New Growth Opportunity (quarterly) |

**Agent count: 21** (Podcast Agent Lead + 20 sub-agents)
**Infrastructure:** n8n orchestration, Claude API, AssemblyAI, Airtable, Buffer, ManyChat, Brand24

---

---

## LAYER 4 — MEASURE, ADJUST & LEARN

**Steps:** 17–20
**Role:** Pulls all performance data, interprets it, executes or proposes optimizations, and continuously updates all platform priors from data and human feedback.

---

### Analytics Dashboard (Step 17)

| Sub-Agent | Role |
|-----------|------|
| Data Ingestion Agent | Connects to and polls 15+ external APIs; normalizes all data into unified clinicIQ schema |
| Benchmark & Threshold Manager | Manages red/yellow/green thresholds; auto-calibrates to expert's 60-day baseline; recalibrates every 90 days |
| Anomaly Detection Agent | Detects sudden drops, gradual declines, plateaus, and positive spikes; triggers Performance Intelligence on flags |
| Dashboard Renderer | Builds and maintains the live expert-facing dashboard with real-time status, drill-downs, and alert panel |

**Agent count: 5** (Analytics Dashboard Lead + 4 sub-agents)
**Data sources:** Meta Ads, GHL, Email platform, Instagram, Facebook, TikTok, YouTube, Google Search Console, Google Analytics, Apple Podcasts, Spotify, IQ Platform (program + production), IQ Drive, TikTok Ads, Podcast ad platforms

---

### Performance Intelligence Agent (Step 18)

| Sub-Agent | Role |
|-----------|------|
| Root Cause Analyst | Isolates root cause of every flag using correlation, timeline, and segment analysis |
| Diagnosis Writer | Writes plain-language diagnosis (Observation / Root Cause / Fix Type) with urgency level |
| Opportunity Scanner | Weekly scan for positive anomalies, replication opportunities, and cross-channel patterns |
| Cross-Channel Correlation Agent | Finds relationships across data streams (e.g., podcast listeners showing at higher webinar rates than non-listeners) |

**Agent count: 5** (Performance Intelligence Lead + 4 sub-agents)
**Triggers:** Every red/yellow flag from Analytics Dashboard + weekly scheduled scan

---

### Optimization Agent (Step 19)

| Sub-Agent | Role |
|-----------|------|
| Ad Optimization Executor | Meta Ads API — pauses creative, shifts budget, rotates creative pool (auto/approve/propose) |
| Funnel Optimization Executor | GHL API + email platform — subject line swaps, sequence timing, page title A/B tests |
| Content Optimization Executor | Content calendar rebalancing, hook bank priority updates, podcast title/description updates |
| Program Optimization Executor | FAQ additions, lesson sequence adjustments, phase pacing, milestone email timing |
| Impact Tracker | Measures every change at 48h / 7d / 30d; feeds results to Learning Engine |

**Agent count: 6** (Optimization Agent Lead + 5 sub-agents)
**Three execution modes:** Auto-Execute (standing authorization) / Approve-and-Execute (one-click) / Propose-Only (brief for human-required changes)

---

### Learning & Feedback Engine (Step 20)

| Sub-Agent | Role |
|-----------|------|
| Human Feedback Processor | Captures all expert approvals, rejections, edits; classifies by type; extracts what agent got right/wrong |
| Performance Pattern Extractor | Identifies statistically significant patterns; separates expert-specific from universal |
| Expert Prior Manager | Owns this expert's personalized prior layer; updates Voice DNA, hook rankings, thresholds, audience priors; versioned |
| Platform Prior Manager | Owns anonymized universal learning; updates default templates and benchmarks for all experts (N≥10 threshold) |

**Agent count: 5** (Learning & Feedback Engine Lead + 4 sub-agents)
**Monthly trigger:** Routes Monthly Review Brief to Growth Strategy Agent's Monthly Planner Sub-Agent on last day of each month → closes the loop back to Layer 2

---

---

## COMPLETE PLATFORM AGENT COUNT

### By Layer

| Layer | Agent Group | Lead | Sub-Agents | Total |
|-------|------------|------|-----------|-------|
| **Platform** | IQ Claw | 1 | 6 | **7** |
| **Platform** | Core Orchestrator (incl. Output Quality Agent) | 1 | 6 | **7** |
| **Layer 1** | Onboarding Agent | 1 | 10 | **11** |
| **Layer 2** | Brand Strategy Agent | 1 | ~4 | **~5** |
| **Layer 2** | Growth Strategy Agent | 1 | ~11 | **~12** |
| **Layer 3** | Content Builder | 1 | 11 | **12** |
| **Layer 3** | Funnel Builder | 1 | 9 | **10** |
| **Layer 3** | Webinar Builder | 1 | 10 | **11** |
| **Layer 3** | Email & SMS Builder | 1 | 11 | **12** |
| **Layer 3** | Ad Creative Builder | 1 | 9 | **10** |
| **Layer 3** | Lead Magnet Builder | 1 | 4 | **5** |
| **Layer 3** | Sales Script Builder | 1 | 5 | **6** |
| **Layer 3** | Program Builder | 1 | 10 | **11** |
| **Layer 3** | Website Builder | 1 | 5 | **6** |
| **Layer 3** | Podcast Agent | 1 | 20 | **21** |
| **Layer 4** | Analytics Dashboard | 1 | 4 | **5** |
| **Layer 4** | Performance Intelligence | 1 | 4 | **5** |
| **Layer 4** | Optimization Agent | 1 | 5 | **6** |
| **Layer 4** | Learning & Feedback Engine | 1 | 4 | **5** |
| **TOTAL** | | **20** | **~148** | **~168** |

*Layer 2 sub-agent counts pending final audit confirmation — estimated ~17 combined.*

---

### By Function

| Function | Agent Count |
|----------|-------------|
| Expert interface and routing | 7 (IQ Claw) |
| Production orchestration and QA | 7 (Core Orchestrator) |
| Expert intelligence capture | 11 (Onboarding) |
| Strategic operating system | ~17 (Brand + Growth Strategy) |
| Content production | 12 (Content Builder) |
| Funnel production | 10 (Funnel Builder) |
| Webinar production | 11 (Webinar Builder) |
| Email & SMS production | 12 (Email Builder) |
| Ad creative production | 10 (Ad Creative Builder) |
| Lead magnet production | 5 (Lead Magnet Builder) |
| Sales enablement | 6 (Sales Script Builder) |
| Program delivery | 11 (Program Builder) |
| Website production | 6 (Website Builder) |
| Podcast production + growth | 21 (Podcast Agent) |
| Data and analytics | 5 (Analytics Dashboard) |
| Performance intelligence | 5 (Performance Intelligence) |
| Optimization execution | 6 (Optimization Agent) |
| Learning and improvement | 5 (Learning & Feedback Engine) |
| **TOTAL** | **~168** |

---

## Data Flow Map — What Feeds What

```
EXTERNAL WORLD
    Meta Ads, GHL, Email Platform, Social Platforms, Google,
    Apple/Spotify, IQ Platform, IQ Drive
                    │
                    ▼ (every 4–24 hours)
            ANALYTICS DASHBOARD (Layer 4)
                    │
          ┌─────────┴──────────┐
          ▼                    ▼
  PERFORMANCE               LEARNING ENGINE
  INTELLIGENCE              (Step 20)
  (Step 18)                     │
          │                     │ Updates priors
          ▼                     ▼
  OPTIMIZATION ─────────► ALL AGENTS (Layer 1–3)
  AGENT (Step 19)          Voice DNA, hooks, thresholds,
          │                templates, ad creative rankings
          │
  Auto-executes or
  Proposes to expert
  via IQ Claw
          │
          ▼
  Monthly Review Brief ──► Growth Strategy Agent
                           (Monthly Master Plan refresh)
                                    │
                                    ▼
                           Core Orchestrator
                                    │
                                    ▼
                           All Builder Agents (Layer 3)
                                    │
                                    ▼
                                IQ Drive
                                    │
                                    ▼
                         Analytics Dashboard (loop closes)
```

---

## Handoff Payload Standards

### Expert Dossier (Layer 1 → Layer 2 + All Builder Agents)
- Format: JSON (164 fields) + human-readable narrative
- Gate: `handoff_ready: true` required before Layer 2 activates
- Key sections consumed by Builder agents: Voice DNA, Avatar Psychology (false beliefs, desires, objection map), Offer Architecture, Proof Bank, Mechanism, Visual DNA, Tech Stack

### Strategy Package (Layer 2 → Core Orchestrator → Layer 3)
Five documents, all required before any Builder agent activates:
1. Expert Dossier Brief (from Layer 1)
2. Brand North Star Document — Part 2 (operational rules)
3. Monthly Messaging Brief (hook bank, angle map, objection library)
4. Monthly Master Plan Brief (campaign structure, CTA, webinar details)
5. Asset Brief (per-request, generated by Core Orchestrator)

### Asset Output (Layer 3 → Output Quality Agent → IQ Drive → Expert)
- Every Builder output → Output Quality Agent (Voice QA + Brand QA)
- Pass → IQ Drive → Expert-facing delivery
- Fail (1st) → rewrite request back to originating sub-agent
- Fail (2nd) → "Needs Your Eye" flag → expert dashboard hold

### Performance Data (IQ Drive + External APIs → Layer 4)
- All asset performance metadata tagged in IQ Drive
- External platform data polled by Data Ingestion Agent
- Normalized into unified clinicIQ schema before any Layer 4 agent reads it

---

## Open Architecture Decisions (From Step 21 Audit)

These must be resolved by the engineering team before build begins:

| # | Decision | Recommended Direction |
|---|----------|-----------------------|
| 1 | Agent framework | LangGraph (complex orchestration) or CrewAI (role-based teams) — team capability decides |
| 2 | Model tier map | Voice-critical: Claude 3.5+/GPT-4o. Extraction: smaller/faster. Classification: SLMs. Never premium for formatting. |
| 3 | Memory/state backend | Vector DB (semantic) + PostgreSQL (structured) + Redis (session state) |
| 4 | IQ Drive stack | S3-compatible object storage + vector DB + PostgreSQL + React/Next.js UI |
| 5 | IQ Course Player | React/Next.js + Mux + Puppeteer + PostgreSQL + vector DB — confirmed Step 16b |
| 6 | Agent deployment | Serverless for triggered agents; containers for always-on (IQ Claw, Data Ingestion) |
| 7 | IQ Claw interface | Persistent web panel overlay within clinicIQ web app; mobile responsive V1, native V2 |
| 8 | Monthly Master Plan refresh | Automatic: Layer 4 triggers Growth Strategy Agent on last day of month; expert approves before it takes effect |

---

## Files Reference

| File | Contents |
|------|---------|
| `layer1/step3_conversation_flow_architecture.md` | Onboarding conversation flow + gamification |
| `layer1/step4_voice_dna_extraction_methodology.md` | Voice DNA extraction, confirmation, enrichment |
| `layer1/step5_avatar_psychology_5_levels_awareness.md` | Avatar psychology + 5 Levels of Awareness |
| `layer1/step6_offer_architecture_extraction.md` | Offer stack extraction methodology |
| `layer1/step7_onboarding_output_payload_handoff.md` | Expert Dossier payload format + handoff spec |
| `layer2/step8_brand_strategy_agent.md` | Brand North Star production |
| `layer2/step9_growth_strategy_agent.md` | Monthly Master Plan + Messaging Brief + sub-agent team |
| `layer2/step10_full_strategy_output_stack.md` | Complete Layer 2 output stack |
| `layer2/step11_strategy_layer_handoff_payload.md` | Handoff to Layer 3 + quality gates |
| `layer3/step12_content_builder_agent.md` | Content Builder (post-audit: 12 agents) |
| `layer3/step13_funnel_and_webinar_builder_agents.md` | Funnel Builder overview |
| `layer3/step13b_webinar_builder_deep_spec.md` | Webinar Builder full spec |
| `layer3/step14_email_sms_builder_agent.md` | Email & SMS Builder |
| `layer3/step15_ad_creative_and_lead_magnet_builder_agents.md` | Ad Creative + Lead Magnet Builders |
| `layer3/step16_sales_script_program_website_podcast_agents.md` | Step 16 overview |
| `layer3/step16b_program_builder_full_spec.md` | Program Builder full spec |
| `layer3/step16c_podcast_agent_full_spec.md` | Podcast Agent full spec (20 sub-agents) |
| `layer4/steps17_20_analytics_intelligence_optimization_learning.md` | Full Layer 4 spec |
| `platform/cliniciq_platform_architecture.md` | IQ Drive + IQ Claw + Patient AI architecture |
| `step21_consistency_audit.md` | This audit |
| `step22_master_agent_document.md` | This document |
| `ENGINEERING_KICKOFF_BRIEF.md` | Executive summary for engineering kickoff |

---

*Step 22 of 22 — Final Master Agent Description Document — v1.0*
*clinicIQ Platform — Complete Agent Architecture*
*~168 agents across Platform Services, Layers 1–4*
*All 22 steps documented. Build-ready.*
