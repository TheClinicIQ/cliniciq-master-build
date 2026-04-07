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
| Gate Checker | Validates all 7 quality gates before any Builder agent is activated (see Step 11 for full gate list) |
| Brief Generator | Produces per-asset briefs from Monthly Master Plan + Monthly Messaging Brief |
| Router | Routes each Asset Brief to the correct Builder agent |
| Context Loader | Pre-loads the relevant dossier sections and strategy documents into Builder agent context |
| Output Tracker | Tracks asset status: in-brief → in-production → in-review → approved → deployed |
| **Output Quality Agent** | Runs Voice QA + Brand QA on every Builder output; pass → deliver to expert; fail → rewrite request back to Builder; 2 failures → "Needs Your Eye" flag |

**Agent count: 7** (Core Orchestrator Lead + 6 sub-agents)

**The 7 Quality Gates (must all be green before any Builder activates):**
1. Expert Dossier `handoff_ready: true`
2. Brand North Star Part 2 complete (Output Quality Agent checks)
3. Growth Blueprint unit economics pass (LTV:CAC ≥ 3:1 pessimistic)
4. **Strategic Integrity Check passed** — all 6 tests green: One Big Domino Specificity, Positioning Singularity, Avatar Specificity, Mechanism Demonstrability, Unit Economics Integrity, Proof Bank Minimum. Full spec: step10_full_strategy_output_stack.md
5. Monthly Master Plan produced
6. Monthly Messaging Brief produced
7. Asset Brief generated for this specific request

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
**Role:** Conducts a structured expert interview to build the 198-field Expert Dossier — the intelligence that powers every other agent on the platform.

### Confirmed Sub-Agent Team (12 agents)

| # | Sub-Agent | Role |
|---|-----------|------|
| Lead | Onboarding Lead Agent | Orchestrates the full interview; manages flow, pacing, and completion |
| 1 | Web Scraper | Pulls expert's existing web presence (website, social, Google Business) for pre-population — pre-populates up to 27 fields before session begins |
| 2 | Voice DNA Mass Ingestion | **Pre-session sub-agent.** Crawls all available public content (social posts, YouTube transcripts, podcast audio, blog posts) and builds a statistically grounded Voice DNA profile before the expert types a single word. Target: voice_confidence_score 70+ at session start. Full spec: step4_voice_dna_extraction_methodology.md |
| 3 | Voice DNA Analyst | Passive voice capture throughout live session; merges with Mass Ingestion base profile; confirms and locks Voice DNA in Section 2 |
| 4 | Avatar Psychology Builder | Extracts all 8 avatar layers + 5 Levels of Awareness determination + DISC buyer profile inference |
| 5 | Offer Architecture Builder | Extracts and scores full offer stack; Hormozi value equation; guarantee architecture; tier existence flags |
| 6 | Webinar Raw Material Extractor | Extracts One Big Domino, 3 Secrets, epiphany bridge, mechanism — webinar raw inputs |
| 7 | Proof Bank Miner | Extracts patient/client transformation stories; populates proof bank throughout session |
| 8 | Story Miner | Extracts expert's personal origin story and patient transformation arc |
| 9 | Silent Diagnostician | Gap analysis and priority flag generation — identifies what's missing without asking |
| 10 | Dossier Assembler | Compiles all sub-agent outputs into the final 198-field JSON payload + human-readable narrative |
| 11 | Progress Endowment Engine | Score calculation, achievement triggers, gamification, reflection moments |

**Agent count: 12** (Lead + 11 sub-agents)

**Primary Output:** Expert Dossier (JSON + narrative, 198 fields) with `handoff_ready: true` flag
**Feeds into:** Layer 2 (Brand Strategy Agent + Growth Strategy Agent), IQ Claw (IQ Profile base), all Layer 3 Builder agents (read-only), Layer 5 LEP Layer A (the Dossier IS LEP Layer A — same data object)

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

### In-Platform Editor Tool Map
*Two distinct editing tools are used across Layer 3. Developers must implement both — they serve different asset types and are not interchangeable.*

| Tool | Used For | Where Specced |
|------|---------|---------------|
| **Fabric.js** | Static image editor — editing finished PNG assets (text, colors, image swap, element repositioning). Reconstructs HTML/CSS source into a Fabric.js canvas. Re-renders via Puppeteer on save. | Step 12, Engineering Spec Appendix Section D |
| **GrapesJS** | Full page/funnel editor — editing live HTML funnel pages (opt-in, order, webinar, upsell, etc.). Drag-and-drop component architecture. Outputs GrapesJS JSON schema → converts to deployable HTML. | Step 13, Technical Architecture section |

Never use GrapesJS for image assets. Never use Fabric.js for full funnel pages. Both tools must be integrated and both will be actively used by experts.

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
| 9 | Patient AI Trainer | *(V2 — deferred. Do not build for V1.)* Builds Ask AI knowledge base; manages alert queue; monitors content gap patterns |
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
| **TOTAL** | | **20** | **~149** | **~169** |

*Layer 2 sub-agent counts pending final audit confirmation — estimated ~17 combined. Layer 5 agents (+15) bring platform total to ~184.*

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
- Format: JSON (198 fields across 14 sections) + human-readable Expert Dossier Brief narrative
- Gate: `handoff_ready: true` required before Layer 2 activates
- Schema: canonical reference in `layer1/step2_expert_dossier_data_schema.md` — 198 fields, P1/P2/P3 priority flags, status flags, LEP Layer A mapping
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
| `layer1/step1_onboarding_lead_agent.md` | Onboarding Lead Agent — full knowledge base, sub-agent team (12 agents), operating principles, Layer 5 seeding |
| `layer1/step2_expert_dossier_data_schema.md` | Expert Dossier schema — all 198 fields, 14 sections, P1/P2/P3 flags, status flags, LEP Layer A mapping |
| `layer1/step3_conversation_flow_architecture.md` | Onboarding conversation flow + gamification |
| `layer1/step4_voice_dna_extraction_methodology.md` | Voice DNA extraction — Mass Ingestion sub-agent + passive session capture + active confirmation + enrichment |
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
| `platform/cliniciq_platform_architecture.md` | IQ Drive + IQ Claw + Patient AI architecture (Patient AI = **V2 deferred** — do not scope for V1) |
| `platform/miro_fish_simulation_agent.md` | Miro Fish Simulation Agent — pre-launch synthetic audience validation system |
| `references/expert_secrets_full_synthesis.md` | Full synthesis of Expert Secrets framework — reference for Webinar Builder + Sales Script Builder |
| `step21_consistency_audit.md` | This audit |
| `step22_master_agent_document.md` | This document |
| `ENGINEERING_KICKOFF_BRIEF.md` | Executive summary for engineering kickoff |

---

*Step 22 of 22 — Final Master Agent Description Document — v1.0*
*clinicIQ Platform — Complete Agent Architecture*
*~169 agents across Platform Services, Layers 1–4 (184 including Layer 5)*
*All 22 steps documented. Build-ready.*

---

---

# LAYER 5 — THE IQ INTELLIGENCE PLATFORM
**Added: 2026-04-02 | Version 1.0**
*The compounding intelligence layer that transforms ClinicIQ from a great platform into an unbeatable one*

---

## Layer 5 Overview

Every layer below Layer 5 produces outputs. Layer 5 makes everything compound. It is the intelligence infrastructure that gets smarter with every expert who joins, every campaign that runs, every conversion that happens, and every market signal the platform monitors.

Layer 5 is the Apple play completed — the reason no competitor can catch up once ClinicIQ reaches scale.

```
LAYER 5 — IQ INTELLIGENCE PLATFORM
        │
        ├── L5-1: Living Expert Profile      — The platform's memory of every expert
        ├── L5-2: Proactive Intelligence     — IQ comes to the expert before they ask
        ├── L5-3: One-Tap Deployment         — Approve → live across every platform
        ├── L5-4: Network Intelligence       — Every expert makes every expert better
        ├── L5-5: IQ Score                   — One number for the entire business
        └── L5-6: IQ Growth Lab             — The platform playing its own game
```

---

## L5-1 — Living Expert Profile (LEP)

**Role:** The platform's continuously updating intelligence model of every expert — not a static intake document but a living system that gets more accurate every session, every approval, every data point.

**Three layers of intelligence:**

| Layer | Source | What It Contains |
|-------|--------|-----------------|
| **Layer A — Identity Core** | Expert-initiated | The 198-field onboarding dossier. Voice DNA, Visual DNA, Clinical Philosophy, Offer Stack, Proof Bank. Expert-controlled. Canonical schema: `layer1/step2_expert_dossier_data_schema.md`. |
| **Layer B — Market Intelligence** | Platform-automated | Audience response profile, competitive intelligence, market trend signals, offer performance data. Built by the platform from real data. |
| **Layer C — Behavioral Intelligence** | Learning loop | Output quality calibration, workflow preferences, expert evolution tracking. Learns what "good" looks like for this specific expert from every approval, edit, and rejection. |

**Key mechanic — LEP Context Bundle:**
Before any Builder agent generates a single word of output, it receives an auto-assembled LEP Context Bundle: Voice DNA snapshot, output quality calibration, audience response profile, brand north star, current offer context. Every output gets smarter because the context is always current.

**The compound moat:**

| | Day 1 | Month 12 |
|--|-------|----------|
| Voice DNA | Medium confidence | Exceptional — refined by 200+ approvals |
| Hook performance data | None | Full year of seasonal patterns |
| Output calibration | Baseline | Microscopically tuned |
| Competitive picture | Snapshot | Full evolution map |

**Agent count:** No new agents — LEP is a data architecture and update engine consumed by all existing agents
**Full spec:** `layer5/L5-1_living_expert_profile.md`

---

## L5-2 — Proactive Intelligence Engine

**Role:** IQ surfaces the right insight at the right time — before the expert asks. Every morning, by the time the expert opens ClinicIQ, IQ has already diagnosed the business, monitored competitors, caught the trend before it peaks, and built the fix.

**Six signal categories monitored 24/7:**

| Signal Category | Monitoring Cadence | What IQ Detects |
|----------------|-------------------|-----------------|
| **Performance Anomaly** | Hourly (paid) / Daily (organic) | Metric movements outside normal variance — drops flagged with fix, spikes flagged with scale opportunity |
| **Competitive Intelligence** | Daily | Competitor content gaining traction, new offers, ad creative changes, negative sentiment emerging |
| **Market Trend** | Daily | Rising search queries (+40% WoW threshold), trending social topics — surfaces before peak, when first-mover advantage exists |
| **Calendar & Seasonal** | Weekly look-ahead | 6 weeks before seasonal peak, IQ pre-builds the full campaign — content, emails, ads, all in draft |
| **Expert Behavior** | Continuous | Backlog building, approval rate dropping, ignored builders, repeated manual edits — all surface as calibration prompts |
| **Growth Milestones** | Daily | List milestones, revenue thresholds, performance records — celebrated and leveraged |

**The Morning Brief — delivered every morning at expert's natural login time:**
```
🔴 NEEDS YOUR ATTENTION     (max 2 critical, fix already built)
📊 OVERNIGHT PERFORMANCE    (3 metric movements, diagnosed)
🎯 TODAY'S RECOMMENDED ACTION (one thing, highest leverage, asset ready)
👀 WHAT IQ IS WATCHING      (2-3 market signals + "so what")
📅 COMING UP                (7-day calendar + pre-builds in progress)
✅ WHAT HAPPENED OVERNIGHT  (automations run, approvals waiting)
```

**Priority scoring model:** Every signal scored on Revenue Impact (40%) + Time Sensitivity (25%) + Effort-to-Impact (20%) + Expert Receptivity (10%) + IQ Score Impact (5%). Only signals scoring >60 surface in the Morning Brief. Maximum 5 items total. No alert fatigue.

**Agent count:** 1 Proactive Intelligence Agent (extension of existing IQ Claw sub-agent team)
**Full spec:** `layer5/L5-2_proactive_intelligence_engine.md`

---

## L5-3 — One-Tap Deployment

**Role:** Closes the gap between IQ's output and the real world. Expert approves — IQ does everything else. Asset routes to the correct platform, formatted correctly, placed in the right location, live — zero manual steps.

**Full integration stack (Tier 1 — Launch):**

| Platform | What Gets Deployed |
|----------|-------------------|
| **GoHighLevel (GHL)** | Email sequences, SMS sequences, automation workflows, funnel pages, landing pages |
| **Meta Ads Manager** | Ad creative, ad sets — added to existing campaigns (never modifies budgets without separate approval) |
| **Klaviyo / ActiveCampaign / ConvertKit** | Email sequences, broadcasts, automations, segments |
| **YouTube** | Video uploads, titles, descriptions, thumbnails, scheduled publish |
| **Buffer / Later / Publer** | Social posts across all platforms, reels, carousels, stories — batched weekly approval |
| **Apple / Spotify / RSS** | Podcast episodes — audio, metadata, show notes, scheduled publish |
| **Mux / IQ Course Player** | Video lessons, program phase content, patient access gates |
| **Webflow / WordPress** | Blog posts, landing pages, website copy updates |

**The approval flow:**
```
IQ builds → Expert reviews in right panel → "Approve & Deploy" tap
→ Confirmation modal (destination + ETA shown explicitly)
→ Deployment executes with live progress indicator
→ "Live" confirmation + Layer 4 tracking activated automatically
```

**Hard limits — never automatic without separate explicit approval:**
- Budget changes or ad spend increases
- Deleting existing campaigns, sequences, or pages
- Emails to full list >5,000 contacts
- New paid campaign launches (vs. adding creative to existing)
- Changes to funnel structure (vs. copy updates)

**Agent count:** 1 Deployment Agent (new — orchestrates API calls to all connected platforms)
**Full spec:** `layer5/L5-3_one_tap_deployment.md`

---

## L5-4 — Network Intelligence

**Role:** Every expert on the platform makes every other expert better. Aggregated, anonymized performance data from every campaign across every expert builds five intelligence databases that give every expert — from Day 1 — the accumulated wisdom of the entire network.

**The three laws:**
1. Individual data is noise. Collective data is signal.
2. Every expert's experience makes every other expert better.
3. Privacy is non-negotiable. Aggregation is everything.

**Five databases:**

| Database | What It Contains | How It's Used |
|----------|-----------------|---------------|
| **Niche Performance Atlas** | Top hook structures, subject line formulas, conversion benchmarks, content topics — by niche × avatar | Builder agents query before generating any output |
| **Hook & Copy Intelligence Library** | All copy element types ranked by emotional angle × platform × awareness level + saturation signals | Ad Creative and Content Builder foundation |
| **Conversion Benchmark Engine** | Real conversion rate distribution at every funnel stage by niche × offer type × traffic temp | Powers Layer 4 red/yellow/green context + IQ Score dimension scoring |
| **Avatar Language Corpus** | Exact words real health consumers use to describe their problems — from reviews, email replies, comments, forums | Injected into all copy generation — produces outputs that sound like the expert's audience wrote them |
| **Day-1 Advantage Engine** | Synthesized starting benchmark for new experts — matched to their niche × avatar × model profile | Eliminates cold start — new expert begins with validated intelligence from Day 1 |

**The saturation signal:** As a hook pattern is used by more experts and its performance declines across the board, the library flags it as saturating and stops recommending it as a primary structure. New experts never start with stale hooks.

**The flywheel:**
```
More experts → more campaigns → richer databases
→ better outputs for all experts → better results
→ attracts more experts → [compounds forever]
```

**At 50,000 experts:** The most comprehensive health marketing performance database in existence. Years and billions in ad spend to replicate from scratch.

**Agent count:** 4 Network Intelligence Agents (Data Aggregation, Pattern Extraction, Benchmark Calibration, Day-1 Package Assembly)
**Full spec:** `layer5/L5-4_network_intelligence.md`

---

## L5-5 — IQ Score

**Role:** One number, 0–100, that tells the expert exactly how healthy their entire growth engine is — every day, benchmarked against real niche data, with the highest-leverage action always identified and the fix always pre-built.

**Eight dimensions:**

| Dimension | Weight | What It Measures |
|-----------|--------|-----------------|
| **Conversion Engine** | 20% | Leads → buyers at a healthy rate across all funnel stages |
| **Revenue & Monetization** | 18% | Revenue growing, durable (continuity multiplier applied), multi-offer-tier |
| **Lead Generation** | 15% | Opt-in rate, volume, quality, source diversity — vs. niche benchmarks |
| **Audience & Reach** | 12% | Audience size, growth rate, engagement rate, cross-platform distribution |
| **Content Velocity** | 10% | Publishing consistency vs. own plan (consistency > volume), content-to-lead attribution |
| **Patient Outcomes** | 10% | Program completion rate, testimonial capture, proof bank growth — unique to ClinicIQ |
| **Platform Intelligence** | 8% | Dossier completion, pending approvals backlog, integration health, Voice DNA confidence |
| **Growth Trajectory** | 7% | 30-day trend across all dimensions — velocity and momentum, not just current state |

**All dimensions benchmarked against Network Intelligence Conversion Benchmark Engine — the score reflects where this expert sits in the real performance distribution for their niche, not against generic thresholds.**

**Score tiers:**

| Score | Tier | Status |
|-------|------|--------|
| 90–100 | 🏆 IQ Elite | Top 5% of platform — every engine firing |
| 80–89 | ⚡ IQ Pro | Strong — one or two dimensions to optimize |
| 70–79 | 🟢 IQ Active | Healthy — clear path to Pro |
| 55–69 | 🟡 IQ Building | Foundation in place, gaps in conversion |
| 40–54 | 🟠 IQ Early | Good starts, significant gaps |
| 0–39 | 🔴 IQ Starting | Just activated or major gaps |

**The Score Card always shows:** current score, trend vs. yesterday, niche percentile rank, all 8 dimensions with red/yellow/green, and — most importantly — the single highest-leverage action with the pre-built fix already waiting.

**The habit loop:** Morning Brief surfaces score → expert opens Score Card → clicks "Review it" on biggest opportunity → approves pre-built asset → deployed → score updates in 24 hours → did it move? Come back and check. Variable reward. Tight feedback cycle. The loop that builds the daily habit.

**The Monthly Master Plan is built around the IQ Score:** every month opens with two lowest dimensions identified, specific plan to close the gap, projected score improvement if executed.

**Agent count:** 1 IQ Score Engine (new — calculation, benchmarking, and Score Card generation)
**Full spec:** `layer5/L5-5_iq_score.md`

---

## L5-6 — IQ Growth Lab

**Role:** The platform playing its own game. ClinicIQ's internal R&D and market operations engine — running its own health brands, testing campaigns before a dollar is spent, using THI as the live $100M+ proving ground, and feeding every win back into the platform for every expert.

**Six engines:**

### Engine 1 — Intelligence Aggregator
Monitors everything 24/7 — internal platform data + external public sources:
- **Meta Ad Library:** Systematic daily scraping of health category — ads running 30+ days are validated by definition. Tags every ad by niche, hook type, emotional angle, format, offer type.
- **YouTube Intelligence:** Top 500 health channels — title structures, thumbnail patterns, hook analysis, view performance.
- **Search Intelligence:** Rising query detection across all health niches before they peak.
- **Review Mining:** Amazon, Google, Facebook, Trustpilot, Reddit — the rawest source of avatar language. Real health consumers describing their problems in their own words, at scale.
- **Competitor Intelligence Feed:** Top 100 health experts monitored — content frequency, new offers, ad spend signals, funnel reverse-engineering, price changes.
- **Internal Platform Intelligence:** Aggregated performance data from all experts, Miro Fish score patterns, IQ Score dimension trends.
Output: **Market Intelligence Master File** — continuously updated, feeds the Ideation Engine.

### Engine 2 — Ideation Engine
Three agents converting intelligence into ranked concepts:
- **Concept Architect Agent:** Generates 20–50 raw concepts per session (lead magnet concepts, webinar angles, offer ideas, hook concepts) — volume first, no filtering.
- **Mechanism Naming Agent:** Turns raw concepts into ownable, differentiated vehicle names — tested for ownability, intuitiveness, aspiration, credibility.
- **Hook Bank Agent:** Generates 20–30 hook variations per validated concept across all emotional angles and awareness levels — raw material for head-to-head Miro Fish testing.

### Engine 3 — Miro Fish Focus Group (Enhanced)
Three upgrades beyond standard Miro Fish:

**Upgrade 1 — Broad Segment Simulation:** Test any health consumer segment on demand — not just a specific expert's avatar. Define parameters: niche, demographics, awareness level distribution, skepticism profile, past treatment history, emotional state. Instant synthetic crowd.

**Upgrade 2 — Head-to-Head Concept Testing:** Up to 5 concepts simultaneously against the same crowd. Ranked with statistical significance. The winner identified with a full report on exactly why it won. What focus groups charge $50K+ for — done in hours.

**Upgrade 3 — Campaign-Level Simulation:** Runs the synthetic crowd through the entire funnel end-to-end — ad → opt-in → lead magnet → email sequence → webinar → order page → upsell. Measures drop-off rate, belief progression, emotional arc, objection emergence, and conversion intent at every stage. Identifies the weak point before any production cost is sunk.

### The Organic-to-Paid Intelligence Loop
Two independent validation systems create launch confidence — together, nothing stronger exists in health marketing:

**Signal 1 — Organic Performance Intelligence (Real-world validated)**
Every organic post published by every expert on the platform is a live hook test against a real audience. That anonymized engagement data flows into the Hook & Copy Intelligence Library. When a new campaign launches — for any expert on the platform — the hooks it starts with have already been tested organically by dozens of other experts in the same niche against real humans. No guessing. Paid ads scale what organic has already proven.

Additionally: competitor ads scraped from the Meta Ad Library show what the market has already validated with real spend. Long-running competitor ads = proven hooks, proven angles, proven offers. The Growth Lab reverse-engineers them.

**Signal 2 — Miro Fish Simulation (Pre-launch synthetic validation)**
Catches the specific execution issues that organic data can't — funnel flow problems, belief arc gaps, weak transition points, objection timing.

**Together:** Organic intelligence says what real audiences respond to. Miro Fish says whether this execution will hold through a full funnel. Both cleared = strong launch position.

### Engine 4 — Campaign Assembly Pipeline
Validated concept → complete, ready-to-launch campaign in 5 days using the full Builder Layer:
- **Day 1:** Brand brief, avatar brief, offer stack, campaign architecture
- **Days 1–2:** VSL/webinar script + sales page + opt-in page (all Miro Fish Campaign-Level Simulation cleared)
- **Days 2–3:** Ad creative batch (8–12 variations → only top 3 Miro Fish winners go to production)
- **Days 3–4:** Lead magnet + 7–10 email nurture sequence + SMS sequence
- **Days 4–5:** 21-post organic content batch + podcast/YouTube support assets
- **Day 5:** Campaign Intelligence Package — predicted benchmarks, weak points, A/B test plan, optimization triggers

Compare: Agency equivalent = 6–12 weeks, $50–200K, no simulation, no data foundation.

### Engine 5 — THI as the Live Proving Ground
The Health Institute ($120M/year telehealth clinic) runs entirely on the platform. Every major THI campaign is built in the Growth Lab, Miro Fish tested at Max tier, One-Tap Deployed, and tracked by Layer 4. This produces:
1. The platform's most powerful proof of concept — "We run THI. Here's the data."
2. The richest single-expert dataset in the Network Intelligence layer
3. The beta environment for every new platform feature before broader rollout
4. The acquisition engine for ClinicIQ — THI's results are ClinicIQ's sales argument

Dr. Josh Axe (largest natural health website in the world) and Dr. Will Cole (NYT bestselling celebrity doctor) serve as second and third proving ground archetypes — covering authority brand and premium clinical brand profiles.

### Engine 6 — The Feedback Loop
Every Growth Lab win flows back into the platform:
- New validated hooks → Hook & Copy Intelligence Library
- New conversion data → Conversion Benchmark Engine
- Miro Fish prediction vs. actual results → continuous simulation model recalibration
- New niche entries → seeds Day-1 Advantage Packages for every expert entering that niche
- Scraped competitor intelligence → Competitor swipe databases for all experts' Ad Creative Builders

**Agent count:** 8 Growth Lab agents (Intelligence Aggregator, Concept Architect, Mechanism Naming Agent, Hook Bank Agent, Miro Fish Focus Group Coordinator, Campaign Assembly Orchestrator, THI Integration Manager, Feedback Loop Agent)
**Full spec:** `layer5/L5-6_iq_growth_lab.md`

---

## Layer 5 — Updated Agent Count

| Layer 5 Component | New Agents |
|-------------------|-----------|
| L5-1 Living Expert Profile | 0 (data architecture consumed by existing agents) |
| L5-2 Proactive Intelligence Engine | 1 |
| L5-3 One-Tap Deployment | 1 |
| L5-4 Network Intelligence | 4 |
| L5-5 IQ Score | 1 |
| L5-6 IQ Growth Lab | 8 |
| **Layer 5 Total** | **15 new agents** |

**Revised platform total: ~184 agents** (169 original + 15 Layer 5)

---

## Updated Files Reference — Layer 5

| File | Contents |
|------|---------|
| `layer5/L5-1_living_expert_profile.md` | Living Expert Profile — full architecture, 3 intelligence layers, update engine, compound moat |
| `layer5/L5-2_proactive_intelligence_engine.md` | Proactive Intelligence — 6 signal categories, Morning Brief spec, priority scoring, noise filter |
| `layer5/L5-3_one_tap_deployment.md` | One-Tap Deployment — full integration stack, approval flow, deployment pathways, safeguards |
| `layer5/L5-4_network_intelligence.md` | Network Intelligence — 5 databases, flywheel, Day-1 Advantage Engine, privacy architecture |
| `layer5/L5-5_iq_score.md` | IQ Score — 8 dimensions, scoring model, Score Card, habit loop, tier system |
| `layer5/L5-6_iq_growth_lab.md` | IQ Growth Lab — 6 engines, organic-to-paid loop, Miro Fish Focus Group, THI proving ground |
| `layer5/README.md` | Layer 5 index and platform completion summary |
| `knowledge/briefs/copy_frameworks.md` | Direct response copy frameworks applied to health marketing |
| `knowledge/briefs/compliance_guidelines.md` | FTC, FDA, state medical board claim restriction reference |
| `knowledge/briefs/html_css_production.md` | HTML/CSS layout standards for Puppeteer-rendered assets |
| `knowledge/briefs/platform_dimensions.md` | All asset dimension specs by platform and format |
| `knowledge/briefs/design_principles.md` | Visual design standards for health expert brand assets |
| `knowledge/briefs/video_production.md` | B-roll, Reels, and video asset production guidelines |
| `knowledge/briefs/quiz_assessment.md` | Quiz and interactive tool build specifications |
| `knowledge/briefs/hook_performance.md` | Hook structure performance data and patterns |

---

*Step 22 — Updated with Layer 5 — v2.0*
*clinicIQ Platform — Complete Agent Architecture including IQ Intelligence Platform*
*~184 agents across Platform Services, Layers 1–5*
*Full platform specced. Build-ready.*
