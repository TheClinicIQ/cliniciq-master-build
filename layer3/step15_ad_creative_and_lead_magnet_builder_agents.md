# clinicIQ — Layer 3: Builder Agents — Step 15: Ad Creative Builder + Lead Magnet / Tool Builder
**Version 3.0 — Final**
*Step 15 of 22 | Depends on: Steps 1–14 + Platform Architecture*

---

## The Knowledge Folder System

Before speccing the agents, the architecture decision that makes every agent in clinicIQ cleaner needs to be documented.

**The principle:** Agent specs define what an agent *does*. A shared knowledge folder defines what agents *know*. These are separate. Agents read from the knowledge base. When the knowledge base is updated, every agent that reads from it is immediately smarter — with no changes to the agent architecture.

```
/cliniciq/knowledge/
├── hooks/
│   ├── cross_industry_hook_patterns.md       ← viral hook swipe bank, all industries
│   ├── health_niche_adaptations.md           ← patterns adapted to health niche
│   └── hook_performance_data.md              ← what's working, updated monthly from ad data
├── copy_frameworks/
│   ├── direct_response_frameworks.md         ← DIC, PAS, AIDA, Before-After-Bridge
│   ├── meta_ad_copy_standards.md             ← 5 elements, character limits, policy rules
│   ├── email_copy_standards.md               ← subject lines, body structure, PS
│   └── image_copy_standards.md              ← headline hierarchy, CTA placement rules
├── compliance/
│   ├── meta_health_ad_policy.md             ← what Meta allows/prohibits for health
│   ├── health_claim_rules.md                ← FTC, FDA, general health claim standards
│   └── specialty_compliance/               ← one file per specialty (hormone, gut, auto-immune, etc.)
├── production/
│   ├── html_css_render_standard.md          ← how all visual assets are built in code
│   ├── platform_dimensions.md              ← every spec for every platform format
│   ├── video_production_standards.md       ← b-roll, UGC, timing, text overlay specs
│   └── design_principles.md               ← hierarchy, typography, color, premium standard
├── frameworks/
│   ├── perfect_webinar_framework.md         ← Brunson full spec
│   ├── fladlein_framework.md               ← Fladlein full spec
│   ├── funnel_page_copy_standards.md       ← per page type copy frameworks
│   ├── quiz_assessment_best_practice.md    ← question design, results pages, lead gates
│   ├── email_sequence_architecture.md      ← all sequence types and structures
│   └── soap_opera_epiphany_frameworks.md  ← Chaperon + Brunson email systems
└── avatars/
    ├── health_avatar_psychology.md          ← false beliefs, emotional states, objections
    └── awareness_level_frameworks.md        ← 5 levels applied to health niche
```

This is the knowledge base that gets built during the knowledge base phase (after Steps 1–22 architecture is complete). Every agent spec below references the relevant knowledge files it reads from. When performance data updates `hook_performance_data.md`, every agent that reads hooks immediately benefits.

---

## The Traffic Architecture — Non-Negotiable

**Cold traffic destinations (paid ads drive to one of these only):**
1. Webinar registration page — primary, always built first
2. Quiz → Webinar funnel — tested against straight webinar to optimize CPR
3. Assessment → Webinar funnel — tested as third variant when data supports it

**Retargeting destinations:**
1. Order page — for webinar viewers who didn't buy
2. Order page — for order page visitors who didn't checkout

Never cold traffic to a PDF lead magnet. Never cold traffic to an order page.

---

## Part 1 — The Ad Creative Builder

### What It Builds

Purpose-built paid creative from scratch. The Advantage+ pool model — Meta's Andromeda system — means the agent produces pools of creative variations that Meta's algorithm tests and scales automatically. Not one hero ad. A pool.

| Pool Element | Volume per concept |
|---|---|
| Image variations | 5–10 (multiple visual treatments) |
| Video variations | 5–10 (multiple hook angles) |
| Primary text variants | 3–5 |
| Headline variants | 3–5 |

**Asset types produced:**
- Static image ads (all Meta placements)
- Carousel ads (5-card ad format)
- B-roll with text overlay (15-second + 30-second per concept)
- Direct-to-camera video scripts
- UGC-style scripts (expert and patient/character)
- All five ad copy elements per asset

---

### Cold vs. Retargeting Creative

**Cold creative always:**
- Sells the transformation promise, not the program
- Drives to a single action (register for webinar, take the quiz, or take the assessment)
- Never mentions price, never shows the paid offer, never explains the full mechanism
- Works for someone who has never heard of this expert

**Retargeting creative always:**
- Acknowledges where they are — warm audience already knows the expert
- Removes the specific friction blocking purchase
- Points directly to the order page — always a hard CTA

---

### Sub-Agent Team

```
AD CREATIVE BUILDER LEAD AGENT
├── Reads: Growth Blueprint + Monthly Master Plan + current performance data
│         + /knowledge/hooks/ + /knowledge/copy_frameworks/ + /knowledge/compliance/
├── Determines: Monthly creative brief — concepts, layers, Advantage+ pool targets
├── Orchestrates: 9 sub-agents
└── Delivers: Complete Advantage+ creative pools → IQ Drive/Ads/
              + weekly performance report + replacement queue

1. Ad Strategy Agent
   Reads: Growth Blueprint, Monthly Master Plan, current CPL/ROAS,
   funnel variant performance (webinar vs. quiz vs. assessment CPR)
   Produces: Monthly creative brief — which concepts, which audience layers
   (cold/warm/hot), which offers, creative volume targets per campaign
   Maps: which creative pools go into which Advantage+ campaigns

2. Hook Intelligence Agent
   Reads: /knowledge/hooks/cross_industry_hook_patterns.md
          /knowledge/hooks/hook_performance_data.md
   Monitors viral content across all industries — extracts structural patterns,
   not content (the underlying formula that made it viral)
   Adapts patterns for this expert's niche and avatar
   Updates /knowledge/hooks/ files weekly with new patterns
   Feeds winning patterns back from Ad Performance Analyst monthly
   Output: fresh hook adaptations routed to Creative Copy Specialist per batch

3. Creative Copy Specialist
   Reads: /knowledge/hooks/ (all files)
          /knowledge/copy_frameworks/ (all files)
          /knowledge/compliance/meta_health_ad_policy.md
          Expert Voice DNA + Avatar emotional trigger map from dossier
   The most important sub-agent in this team
   Writes ALL copy:
   — Text on images and carousel cards (hook headline, supporting line, CTA element)
   — Primary text × 3 variants (pain-led, curiosity-led, proof-led)
   — Headline × 3 variants (benefit, curiosity, pattern interrupt)
   — Description + CTA button recommendation
   Every element compliance-checked against Meta health policy before output

4. Visual Production Agent
   [Merged: Visual Direction Agent + Static Image Production Agent]
   Reads: /knowledge/production/design_principles.md
          /knowledge/production/platform_dimensions.md
          /knowledge/production/html_css_render_standard.md
          Expert Visual DNA from dossier
   Writes creative briefs for every visual:
   Images: scene concept, mood, subject, composition, text placement zones,
   3–5 treatment variants (dark/light, image-forward/copy-forward, bold/minimal)
   Video/b-roll: shot direction, storyboard, pacing, text overlay timing spec
   UGC: setting, energy, wardrobe, phone-aesthetic direction
   Then executes static image production directly from its own briefs:
   HTML/CSS per asset → Puppeteer renders all 3–5 visual treatments per concept
   All three platform dimensions in single pass (1080×1350, 1080×1080, 1080×1920)
   Ad layout rules enforced: hook dominant, hierarchy clear, CTA element always present
   Routes video/b-roll briefs to Video & B-Roll Production Agent
   Routes UGC briefs to UGC Script Writer
   Routes finished static images to Advantage+ Creative Packager
   Natural sequential flow: direction → production runs in single context, same Visual DNA knowledge base

5. Video & B-Roll Production Agent
   Reads: /knowledge/production/video_production_standards.md
   Executes Visual Production Agent video briefs
   B-roll: Kling v1.6 (cinematic) or Runway Gen-3 (stylized)
   Text overlay: composited programmatically, ad-specific timing
   — 0:00–0:03: Hook text (dominant, maximum contrast)
   — 0:03–0:08: Agitation line
   — 0:08–0:20: Intrigue/promise
   — 0:20–0:28: Proof/specificity
   — 0:28–0:30: CTA + URL
   Two lengths produced per concept in single pass:
   30-second (Feed) + 15-second (Reels/Stories) — same hook and CTA, middle compressed

6. UGC Script Writer
   Reads: /knowledge/copy_frameworks/direct_response_frameworks.md
          Expert Voice DNA from dossier
   Expert-as-UGC: casual, direct-to-camera, 15–60 seconds, phone aesthetic
   Script structure: hook (0–3s) → bridge (3–8s) → agitate (8–15s) → 
   promise (15–25s) → CTA (25–30s)
   Patient/character UGC: first-person story, specific result, AI avatar or real patient
   Authenticity test: every line passes "would a real person say this?"
   Produces cold and warm retargeting versions for both formats

7. Retargeting Creative Specialist
   Reads: /knowledge/copy_frameworks/ + current objection data from analytics
   Warm retargeting (webinar viewers, non-buyers → order page):
   Three angle templates: proof-focused, guarantee-focused, objection-specific
   Hot retargeting (order page visitors → order page):
   Ultra-direct: acknowledgment → final friction removal → urgency → CTA
   Each angle produced as image + short video + copy set

8. Advantage+ Creative Packager
   Reads: /knowledge/production/platform_dimensions.md
   Assembles all produced creative into Advantage+ compatible pools
   Images pool: 5–10 tagged variations
   Videos pool: 5–10 tagged variations (both lengths)
   Text pool: all primary text + headline variants
   Formats for direct import into Meta Ads Manager
   Produces campaign structure recommendation:
   which pools go in which ad sets, budget allocation,
   Advantage+ vs. manual campaign recommendation by budget level

9. Ad Performance Analyst
    Reads: Meta Ads Manager data via API integration
    Monitors: CTR, 3-sec retention, CPR, ROAS, creative frequency
    Identifies: winning hook patterns → routes back to Hook Intelligence Agent
    Triggers: creative refresh alert when frequency hits 3.0+ on any active asset
    Produces: weekly performance report → IQ Claw dashboard
    Updates: /knowledge/hooks/hook_performance_data.md monthly
```

**Agent count: 10** (Ad Creative Builder Lead + 9 sub-agents — merged from 11; Visual Direction + Static Image Production → Visual Production Agent)

---

## Part 2 — The Lead Magnet & Tool Builder

### What It Actually Is

This agent builds three types of lead generation assets — and the third is what makes it unique on the market:

1. **Quizzes and assessments** — funnel entry points tested against the straight webinar
2. **PDF guides and checklists** — email non-buyer engine assets (secondary output)
3. **Micro vibe-coded SaaS tools** — interactive web tools built in code and hosted on clinicIQ

The micro SaaS tool is the differentiator. A PDF is downloaded and forgotten. A quiz is taken once. A tool gets used repeatedly, shared organically, and creates a brand association with the expert that no static asset can match. It also collects leads at a meaningfully higher rate because the avatar perceives it as genuinely valuable software — not a marketing freebie.

### What a Micro SaaS Lead Magnet Is

A small, fully functional interactive web tool that:
- Solves one specific problem for the avatar
- Is built in HTML/CSS/JS by the AI (vibe coding — the agent writes the full working code)
- Is deployed to clinicIQ infrastructure at a branded URL
- Collects an email before delivering results or full access
- Routes collected leads into the expert's email sequences
- Has the expert's branding — feels like their product, not clinicIQ's

**Why it outperforms every other lead format:**

| Format | Perceived Value | Shareability | Return Visits | Lead Capture Rate |
|---|---|---|---|---|
| PDF guide | Low–Medium | Low | Rarely | 25–35% |
| Quiz | Medium | Medium | Rarely | 35–55% |
| Interactive tool | High | High | Often | 45–65% |

People share tools. "I found this hormone calculator — you need to try it." Nobody shares a PDF.

### Tool Concept Examples by Buyer Persona (Not Just Niche)

The Tool Concept Generator maps the full avatar life first — what this specific person wants to understand, track, or solve across every dimension of their daily experience — then identifies which of those the expert can credibly address. Clinical tools are one category. Lifestyle and personal tools are often higher-converting entry points because they meet the avatar where she already is.

**Hormone expert — avatar is a 40s woman, fatigued, frustrated, wants her life back:**

*Clinical tools (mechanism-direct):*
- The Hormone Pattern Identifier — symptoms in, dominant pattern out
- The Functional Lab Range Interpreter — paste labs, see the gaps mainstream medicine ignores
- The Cortisol Rhythm Mapper — rate energy/mood at 4 timepoints, get your adrenal pattern
- The Estrogen Dominance Risk Scorer — 12 inputs, risk score + what's driving it

*Lifestyle tools (buyer persona-first, mechanism bridge built into results):*
- The Energy Drain Finder — where is your energy going? identifies the top 3 energy leaks with mechanism explanation
- The Sleep Quality Analyzer — sleep inputs → score → "here's what's disrupting your sleep at the hormonal level"
- The Stress Burden Calculator — daily stressors scored → total load → cortisol/adrenal connection
- The Mood Pattern Tracker — log mood across a week → pattern identified → mechanism bridge
- The "Why Am I So Tired?" Diagnostic — 10 fast questions → 3 most likely root causes → webinar invite
- The Midlife Energy Blueprint — lifestyle audit → personalized recommendations → bridge to program

**Gut health expert — avatar is someone with chronic digestive issues, brain fog, low energy:**

*Clinical tools:*
- The Gut Imbalance Identifier — symptom clusters mapped to common imbalance patterns
- The Leaky Gut Risk Assessment — lifestyle + symptom inputs → risk score + mechanism
- The SIBO Probability Calculator — symptom + history → probability + what to do next

*Lifestyle tools:*
- The Brain Fog Root Cause Finder — cognitive symptom inputs → gut-brain axis connection
- The Food-Mood Tracker — food log + mood/energy ratings → pattern detection
- The Bloat Trigger Identifier — symptom + food + timing inputs → most likely triggers

**Autoimmune expert — avatar is managing an autoimmune condition, seeking control:**

*Clinical tools:*
- The Autoimmune Trigger Tracker — log exposures + flares → pattern over time
- The Inflammation Load Calculator — diet + lifestyle + symptoms → total burden score

*Lifestyle tools:*
- The Flare Predictor — stress + sleep + diet inputs → flare risk score for the week
- The "What's Draining My Immune System?" Audit — 15 lifestyle inputs → top 3 burden factors
- The Energy Reserve Calculator — activity vs. recovery ratio → sustainability score

**The pattern across all tools (clinical or lifestyle):**
Input (symptoms/lifestyle/behavior/labs) → Processing (scoring logic) → Personalized output (pattern + what it means) → Email gate → Full results + mechanism bridge + webinar CTA

The mechanism bridge is always built into the results page — but the tool earns the click by being something the avatar genuinely wanted *before* they were thinking about the expert's specialty.

### The Three Funnel Entry Variants

All three entry points drive to the webinar. Data determines which produces the best CPR:

```
VARIANT A: Straight Webinar Funnel
Cold Ad → Webinar Registration Page → Webinar → Order Page

VARIANT B: Quiz → Webinar
Cold Ad → Quiz → Results Page → Webinar Registration → Webinar → Order Page

VARIANT C: Micro SaaS Tool → Webinar
Cold Ad → Tool (e.g. "Hormone Calculator") → Results/Email Gate → 
Webinar Registration → Webinar → Order Page
```

Variant C often produces the highest lead quality because the avatar self-selected with specificity — they didn't just register for a webinar, they engaged with a tool about their exact situation. The webinar invitation is hyper-personalized to their tool output.

### Sub-Agent Team

```
LEAD MAGNET & TOOL BUILDER LEAD AGENT
├── Reads: Growth Blueprint funnel strategy + Email Builder architecture
│         + current funnel variant performance data
│         + /knowledge/frameworks/quiz_assessment_best_practice.md
├── Determines: Which assets to build (tool vs. quiz vs. PDF), production priority,
│              which funnel variants to A/B test against straight webinar
├── QA responsibility: The Lead Agent owns final quality check — no separate QA sub-agent
├── Orchestrates: 4 sub-agents
└── Delivers: Tools + quizzes hosted on clinicIQ + PDFs → IQ Drive/Lead Magnets/
              + email sequence trigger specs → Email Builder

1. Tool Concept Generator
   Reads: Expert niche + mechanism + avatar psychology from dossier
          /knowledge/avatars/health_avatar_psychology.md
   Critical frame: generates ideas based on what the BUYER PERSONA wants —
   not just what's clinically related to the expert's specialty.
   The avatar is a full human with many concerns. The best tools serve the person
   first, then bridge to the mechanism. A hormone expert's best-performing tool
   might be a Sleep Quality Analyzer, a Stress and Burnout Tracker, an Energy Audit,
   or a Mood Pattern Identifier — not just a hormone calculator. These reach the
   same avatar at entry points she cares about every day, not just when she's
   thinking about her diagnosis.
   
   Idea generation process:
   Step 1 — Map the full avatar life: What does this person worry about,
   track, want to measure, want to understand, want to improve — across
   ALL dimensions of their daily life (energy, sleep, stress, weight, mood,
   relationships, productivity, food, skin, aging, pain, clarity)?
   Step 2 — Identify which of those the expert can credibly address
   (directly or via mechanism bridge)
   Step 3 — Generate tool concepts across the full map — not just the
   clinical core. The bridge back to the mechanism is always built into
   the results page, but the tool earns attention by being genuinely useful
   to the person first.
   
   For each concept produces:
   — Tool name + concept (what it does for the user)
   — What the user inputs
   — What the tool calculates/produces
   — Lead capture moment
   — Webinar bridge logic (how results connect to the webinar promise)
   — Estimated lead capture rate potential
   — Technical buildability assessment
   Ranks all ideas and presents top 5 for expert selection via IQ Claw
   Expert selects 1–3 to build; rest stay in the concept library for future builds

2. Micro SaaS Tool Builder
   Reads: Approved concept from Tool Concept Generator
          /knowledge/production/html_css_render_standard.md
          Expert Visual DNA from dossier
   Writes full HTML/CSS/JS for the approved tool concept
   The complete working application — not a mockup, a functional tool
   Includes: scoring/calculation logic, results display, brand styling,
   email capture gate (before results delivery), webinar bridge CTA on results
   Deploys to clinicIQ infrastructure at branded URL
   (tool.[expertname].cliniciq.com or custom domain)
   Connects email capture to expert's email platform → routes to results-specific sequence
   Analytics: tracks tool starts, completions, email captures, webinar registrations
   from tool visitors (full funnel attribution)

3. Quiz & Assessment Builder
   Reads: /knowledge/frameworks/quiz_assessment_best_practice.md
   Quiz: 7–12 questions, fast, emotionally accurate avatar language
   Assessment: 15–25 questions, multi-dimensional scoring
   Scoring logic: routes to 3–5 result types
   Results page per result type: personalized, mechanism-confirming, webinar bridge CTA
   Lead capture gate: after final question, before results
   Email trigger per result type → Email Builder
   Hosted on clinicIQ infrastructure
   A/B variants: results page headline, CTA copy, video vs. no video

4. PDF & Content Builder
   Reads: /knowledge/production/html_css_render_standard.md
          Expert Voice DNA from dossier
   Premium HTML/CSS → Puppeteer PDF output
   Purpose: email non-buyer engine assets only (not cold traffic offers)
   Standard: mechanism-confirming, quick win structure, webinar bridge on final page
   Design: brand-accurate, indistinguishable from a $47 commercial product
```

**Agent count: 5** (Lead Magnet & Tool Builder Lead + 4 sub-agents)

---

## Step 15 Final Agent Count

| Agent | Sub-Agents | Total |
|---|---|---|
| Ad Creative Builder Lead | 10 | 11 |
| Lead Magnet & Tool Builder Lead | 4 | 5 |
| **Step 15 Total** | | **16** |

---

## How It All Connects

```
COLD TRAFFIC
    │
    ├──► Webinar Registration Page (Funnel Builder, Step 13)
    │         └──► Webinar → Order Page
    │
    ├──► Quiz (Quiz & Assessment Builder)
    │         └──► Results Page → Webinar Registration → Webinar → Order Page
    │
    └──► Micro SaaS Tool (Tool Builder)
              └──► Email Gate + Results → Webinar Registration → Webinar → Order Page

RETARGETING
    ├──► Webinar viewer (didn't buy) → Order Page direct
    └──► Order page visitor → Order Page direct

ALL non-buyers → Email Builder non-buyer engine
    └── PDF assets from PDF & Content Builder as email value

PERFORMANCE DATA
    └──► Ad Performance Analyst
              └──► Hook Intelligence Agent (patterns updated)
              └──► /knowledge/hooks/hook_performance_data.md (updated monthly)
              └──► IQ Claw dashboard (weekly report)
```

---

## Inputs

| Source | What's Read | Used For |
|---|---|---|
| Expert Dossier | Voice DNA, Avatar emotional triggers, Mechanism, One Big Domino | Copy calibration, tool concept generation |
| /knowledge/hooks/ | Cross-industry patterns + performance data | Hook sourcing for all creative |
| /knowledge/copy_frameworks/ | DR frameworks, Meta ad standards | Copy structure |
| /knowledge/compliance/ | Meta health policy, health claim rules | Compliance filter |
| /knowledge/production/ | Render standards, dimensions, design principles | Production pipeline |
| Growth Blueprint | Ad strategy, funnel variant plan, budget | Creative priorities |
| Monthly Master Plan | Active offers, CTA rotation | Creative alignment |
| Current performance data | CPR by funnel variant, CTR by hook type | Performance-driven decisions |

---

## Outputs

**Ad Creative Builder:**
- Monthly Advantage+ creative pools (images, videos, text variants)
- UGC scripts for recording
- Retargeting creative sets (warm + hot)
- Meta Ads Manager import-ready campaign packages
- Weekly performance report → IQ Claw

**Lead Magnet & Tool Builder:**
- Micro SaaS tools deployed at branded URLs with full analytics
- Quizzes/assessments deployed on clinicIQ with A/B variants
- PDF lead magnets in IQ Drive tagged email-deliverable
- Email sequence trigger specs → Email Builder
- Tool concept library (approved + future builds)

---

*Step 15 of 22 — Ad Creative Builder + Lead Magnet & Tool Builder — v3.0 Final*
*Next: Step 16 — Sales Script Builder + Program Builder + Website Builder + Podcast Agent*
