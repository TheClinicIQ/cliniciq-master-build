# clinicIQ — Layer 4: Measure, Adjust & Learn (Steps 17–20)
**Version 1.0**
*Steps 17–20 of 22 | Depends on: All prior layers + all Builder agents (Layers 1–3)*

---

## What Layer 4 Actually Is

Layer 4 is the intelligence layer that makes everything else compound. Every other layer produces outputs. Layer 4 measures those outputs, decides what's working, and either executes changes automatically or tells the expert exactly what to do next — then learns from every cycle to make the next one better.

It is not a reporting dashboard with some nice charts. It is a closed-loop system where data flows in, intelligence is applied, and the platform either acts or recommends — and it gets measurably better over time because every human decision and every data signal feeds back in.

The expert's experience: they open one dashboard, see red/yellow/green on everything that matters, understand exactly why each status is what it is, and either approve the platform's proposed fix or watch it execute automatically. They never need to log into Meta Ads Manager, GHL, or their social analytics to understand their business. It all lives here.

---

## The Four Steps

| Step | Agent | What It Does |
|------|-------|-------------|
| **Step 17** | Analytics Dashboard | Data ingestion, normalization, and the live red/yellow/green dashboard |
| **Step 18** | Performance Intelligence Agent | Interprets the data — diagnosis, root cause, opportunity identification |
| **Step 19** | Optimization Agent | Acts on the intelligence — executes automatable fixes, proposes human-required changes |
| **Step 20** | Learning & Feedback Engine | Closes the loop — updates all platform priors from performance data and human feedback |

These four run as a continuous cycle, not a one-time process. Every episode, every content batch, every funnel change, every ad rotation — Layer 4 sees it, measures it, interprets it, acts on it, and learns from it.

---

---

## Step 17 — Analytics Dashboard

### What It Is

The single source of truth for everything the expert's growth engine produces. Pulls data from every connected source into one normalized view. Displays it as a red/yellow/green status system so the expert knows at a glance what's working, what needs attention, and what's on fire.

The expert never logs into Meta Ads Manager, GHL, Spotify, Apple Podcasts Connect, Instagram Analytics, or any other platform to understand their business. Everything surfaces here.

### Data Sources — What Gets Connected

**Paid Advertising**
- Meta Ads Manager (Facebook + Instagram campaigns) — spend, reach, CPM, CTR, CPL, ROAS, frequency, ad set performance, creative performance
- TikTok Ads Manager (if active) — same metrics
- Google Ads (if active) — search and display performance
- Podcast ad platforms (Spotify Ads, Overcast — if Podcast Agent is active)

**CRM & Funnel (GHL / GoHighLevel)**
- Contact count by source, by stage, by date
- Pipeline stages — leads, applications, consultations booked, enrollments, revenue
- Funnel conversion rates at every step (opt-in → lead magnet download → webinar registration → webinar show rate → order page visit → purchase)
- Email list size + growth rate
- Automation trigger activity (what sequences are running, where contacts are dropping off)
- Revenue by product, by funnel, by source

**Social Media**
- Instagram: followers, reach, impressions, engagement rate, saves, shares, story views, link clicks, profile visits, best/worst posts by metric
- Facebook: page followers, post reach, engagement, group activity (if expert has a group)
- TikTok: followers, video views, profile visits, average watch time
- YouTube: subscribers, views, watch hours, CTR, average view duration, Shorts performance, channel revenue

**Email Platform** (Klaviyo, ActiveCampaign, ConvertKit — whichever the expert uses)
- List size, growth rate, unsubscribe rate
- Campaign open rate, click rate, revenue per email
- Sequence performance (which sequences are converting, which are dropping off)
- Deliverability metrics (bounce rate, spam rate)

**Podcast Platforms** (if Podcast Agent is active)
- Apple Podcasts Connect: downloads, followers, chart position, review count
- Spotify for Podcasters: streams, listeners, completion rate, new followers
- Cross-platform episode performance

**Program / Course Platform** (IQ Course Player)
- Enrollment count by program, by phase
- Active student count
- Phase completion rates
- Lesson completion rates (which lessons are getting skipped or dropped)
- Student question volume by phase (high volume = content gap)
- Graduation rate
- Testimonial capture rate

**Website / SEO**
- Google Search Console: impressions, clicks, average position, top queries
- Google Analytics: sessions, bounce rate, conversion rate, top landing pages
- Page-level funnel entry conversion rates

**IQ Platform Production Metrics**
- Asset production velocity (how many assets produced per week)
- Asset approval rate (what % of agent outputs are approved vs. sent back)
- Asset publish rate (approved assets that actually go live)
- Time from brief to published asset
- Content calendar fill rate (are all scheduled slots filled?)

### The Red / Yellow / Green System

Every metric tracked in clinicIQ has three status zones. Thresholds are set in two ways:
1. **Benchmarks from Layer 2** — the Growth Strategy Agent sets initial red/yellow/green thresholds based on industry standards + the expert's specific funnel model when the platform is set up
2. **Expert-specific baselines** — after 60 days of data, the platform replaces industry benchmarks with the expert's own rolling 60-day average as the baseline for their green/yellow/red zones. A metric that would be red for a new expert might be green for an established one — the system self-calibrates.

**Status definitions:**
- 🟢 **Green** — performing at or above baseline. No action needed.
- 🟡 **Yellow** — 15–30% below baseline. Monitor. Optimization Agent is analyzing.
- 🔴 **Red** — >30% below baseline OR a critical threshold breached (e.g., ad account flagged, email deliverability below 85%, funnel conversion rate at half of baseline). Immediate attention.
- ⬆️ **Anomaly Up** — >20% above baseline. Platform identifies what caused it so it can be replicated.

**Dashboard sections:**

**1. The Command View (top of dashboard)**
One screen. Everything critical. Color-coded.

```
┌─────────────────────────────────────────────────────────────────┐
│  GROWTH ENGINE STATUS          Week of March 30, 2026           │
├──────────────┬──────────────┬──────────────┬────────────────────┤
│  PAID ADS    │  FUNNEL      │  CONTENT     │  EMAIL             │
│  🟡 CPL +18% │  🟢 Conv 3.2%│  🟢 Eng +12% │  🟢 Open 34%       │
│  ROAS $4.1   │  🔴 Show 41% │  Reach +8%   │  🟡 Click 2.1%     │
├──────────────┼──────────────┼──────────────┼────────────────────┤
│  PODCAST     │  PROGRAM     │  SOCIAL      │  SEO               │
│  🟢 +2.4K    │  🟡 Phase 2  │  🟢 IG +340  │  🟢 +28 positions  │
│  followers   │  drop 22%    │  followers   │  this month        │
└──────────────┴──────────────┴──────────────┴────────────────────┘

⚠ 2 RED ALERTS  |  3 RECOMMENDATIONS READY  |  1 AUTO-EXECUTING
```

**2. Paid Advertising View**
Per campaign: spend, reach, CPL, ROAS, frequency — with red/yellow/green per metric. Per ad set: same. Per creative: CTR, CPM, relevance score, frequency. Auto-flag: any creative with frequency >3.0 (stale — Performance Intelligence Agent triggered). Budget pacing vs. monthly cap.

**3. Funnel Performance View**
The full funnel waterfall — every step from traffic source to revenue:
```
Traffic → Opt-In Page    [visits → opt-ins]     🟢 38% CVR
Opt-in → Lead Magnet     [opt-ins → downloads]  🟢 91% delivery
Lead Magnet → Webinar    [leads → registrations] 🟡 24% (baseline: 31%)
Webinar Registration → Show [reg → attended]    🔴 41% (baseline: 62%)
Webinar → Order Page     [attended → clicked]   🟢 67%
Order Page → Purchase    [visited → purchased]  🟢 3.2%
```
Benchmarks from Layer 2 Strategy (the funnel performance standards set in Step 9 / Step 13) are the initial green thresholds. Expert-specific baselines replace them after 60 days.

**4. Content Performance View**
Per platform, per week: reach, engagement rate, saves, shares. Top 5 posts (overperforming). Bottom 5 posts (underperforming — flag for review). Content calendar fill rate. Awareness level distribution of published content vs. target. Hook type performance ranking.

**5. Email Performance View**
List size trend. Active sequence performance (which automation is running, open/click rates, revenue attributed). Broadcast performance (last 10 campaigns — open rate, clicks, revenue). Deliverability health.

**6. Program Performance View**
Active enrollments, phase completion rates, lesson completion rates, student question volume. High question volume on a phase = content gap flag. Phase 2 dropout rate spiked = Performance Intelligence Agent triggered. Graduation rate trend.

**7. Podcast Performance View** (if Podcast Agent active)
Cross-platform listener count trend, episode performance vs. rolling baseline, guest amplification results, clip performance, review count trend.

**8. Production Velocity View**
Asset production pipeline — what's in brief, in production, in review, approved, published. Time from brief to published. Bottleneck identification (where is work stacking up?).

---

### The Analytics Dashboard Sub-Agent Team

```
ANALYTICS DASHBOARD LEAD AGENT
├── Reads: All connected platform APIs (continuous polling)
├── Normalizes: All data into unified clinicIQ data schema
├── Calculates: Red/yellow/green status for every tracked metric
├── Orchestrates: 4 sub-agents below
└── Delivers: Live dashboard to expert + data feed to Performance Intelligence Agent

SUB-AGENTS:

1. Data Ingestion Agent
   Connects to and polls all external APIs on defined cadences:
   — Meta Ads Manager: every 4 hours (ad performance changes fast)
   — GHL / CRM: every 6 hours (pipeline + funnel conversion data)
   — Email platform: every 12 hours (campaign + sequence performance)
   — Social platforms (IG, TikTok, YouTube, Facebook): every 24 hours
   — Google Search Console + Analytics: every 24 hours
   — Apple Podcasts + Spotify: every 24 hours
   — IQ Platform (program, production): real-time
   Normalizes: All data into unified clinicIQ schema before storage
   Handles: API auth, rate limiting, error recovery, data gap detection
   Flags: Any API that stops responding or returns anomalous data

2. Benchmark & Threshold Manager
   Manages the red/yellow/green threshold system
   Initial state: loads industry benchmarks from knowledge base + thresholds from Layer 2 Strategy docs
   Calibration (Day 60): replaces initial benchmarks with expert's own 60-day rolling averages
   Ongoing: recalibrates thresholds every 90 days based on rolling performance
   Expert override: allows expert to manually set thresholds for any metric
   Seasonal adjustment: flags expected metric changes during known high/low periods
   (e.g., summer dip in webinar attendance is normal — adjust threshold, don't flag red)

3. Anomaly Detection Agent
   Continuously scans all metrics for patterns outside normal ranges
   Detects: both negative anomalies (metrics dropping) and positive ones (metrics spiking)
   For positive anomalies: logs what was different about that period for replication
   For negative anomalies: triggers Performance Intelligence Agent immediately
   Pattern types detected:
   — Sudden drop (>30% single-day change)
   — Gradual decline (consistent downward trend over 7+ days)
   — Plateau (no growth for 14+ days on a growth metric)
   — Correlation anomaly (metric A drops when metric B rises — signals a conflict)

4. Dashboard Renderer
   Builds the visual dashboard in the IQ Platform
   Updates in near-real-time as new data arrives from Data Ingestion Agent
   Manages: color status rendering, trend sparklines, comparison overlays
   Alert panel: surfaces all active red flags + pending recommendations
   Drill-down: every metric is clickable → full historical view + comparison + context
```

**Agent count: 5** (Analytics Dashboard Lead + 4 sub-agents)

---

---

## Step 18 — Performance Intelligence Agent

### What It Is

The analyst layer. Where the Analytics Dashboard shows *what* is happening, the Performance Intelligence Agent figures out *why* — and what to do about it.

Every red flag and yellow flag from the Analytics Dashboard triggers this agent. It goes beyond the metric to the root cause, surfaces a specific diagnosis, identifies what kind of fix is needed, and routes to the Optimization Agent with a clear brief.

### The Diagnosis Framework

The Performance Intelligence Agent doesn't just say "your webinar show rate is low." It says:

> *"Webinar show rate dropped from 62% to 41% over the last 14 days. The drop correlates with a change in traffic source — 67% of new registrants are coming from cold Instagram traffic (up from 31% two weeks ago after you boosted the registration post). Cold traffic show rates average 35–45% vs. 55–65% for warm traffic. This is a traffic quality issue, not a follow-up sequence issue. Recommendation: (1) Reduce cold boost budget on the registration post by 40% and redirect to the lead magnet. (2) Strengthen the Day-1 and Day-2 pre-webinar reminder sequence for cold leads — activate the '3 reasons to show up' email variant. The Optimization Agent can execute both automatically on your approval."*

That's the standard. Not "your show rate is low." Root cause + evidence + specific fix + who executes it.

### Diagnosis Categories

**Paid Advertising Diagnoses**
- CPL rising: audience fatigue vs. creative fatigue vs. landing page issue vs. offer position vs. bidding strategy
- ROAS dropping: front-end conversion issue vs. back-end offer issue vs. audience quality shift vs. funnel drop-off change
- Frequency too high: creative refresh needed vs. audience expansion needed
- Ad account flag risk: policy violation patterns in copy or creative

**Funnel Diagnoses**
- Opt-in rate dropping: headline issue vs. offer clarity vs. traffic quality mismatch vs. page speed
- Webinar show rate low: pre-webinar sequence weak vs. traffic quality vs. timing/timezone issue vs. topic relevance to traffic source
- Webinar conversion low: offer clarity vs. price resistance vs. trust gap vs. CTA timing vs. guarantee weakness
- Order page abandonment: price friction vs. missing social proof vs. guarantee position vs. mobile rendering issue

**Content Diagnoses**
- Engagement rate dropping: hook quality vs. posting time vs. content mix imbalance vs. algorithm change
- Reach declining: posting frequency vs. format mix vs. engagement velocity in first hour vs. caption length
- Saves/shares low: content not delivering standalone value vs. wrong awareness level for current audience growth stage
- Awareness distribution skewed: too many Level 4–5 posts (preaching to the choir) vs. too many Level 1 posts (building reach but not converting)

**Email Diagnoses**
- Open rate dropping: subject line quality vs. deliverability issue vs. list fatigue vs. send time vs. from name recognition
- Click rate low: CTA clarity vs. offer relevance vs. email length vs. link placement
- Unsubscribe spike: content relevance drop vs. too-frequent sending vs. sequence misfire vs. wrong segment receiving wrong message
- Deliverability warning: SPF/DKIM/DMARC issue vs. spam trigger language vs. list hygiene needed

**Program Diagnoses**
- Phase completion rate dropping: content clarity issue vs. content volume too high vs. missing accountability touchpoint vs. phase too long
- Lesson being skipped: lesson title not compelling vs. lesson positioned in wrong sequence vs. prerequisite knowledge gap
- Student question spike on Phase X: content gap — the question being asked isn't answered in existing lessons
- Graduation rate low: program too long vs. life interference vs. missing momentum touchpoints vs. final phase difficulty spike

**Podcast Diagnoses** (if active)
- Download curve flattening: launch-day execution issue vs. guest amplification failure vs. topic not resonating vs. title/packaging issue
- Completion rate dropping: episode too long vs. hook quality vs. segment structure losing momentum mid-episode
- Review growth stalled: review ask script weak vs. ask not placed at right moment vs. engaged audience not being targeted

### Opportunity Identification

The Performance Intelligence Agent doesn't only fire on problems. It also runs a weekly opportunity scan:

- **Replication opportunities:** What performed >20% above baseline this week, and what was different about it? Can it be systematically replicated?
- **Correlation opportunities:** Which content type is most predictive of webinar registrations? Which email subject line pattern drives the most clicks? Surfaces these patterns to inform future production decisions.
- **Timing opportunities:** What day/time produces the highest engagement for this expert's specific audience? Does it vary by content type?
- **Flywheel opportunities:** Which lead magnets are generating the highest-quality leads (highest-converting to high-ticket)? Which podcast episodes are driving the most funnel opt-ins? Surface these for amplification.

---

### The Performance Intelligence Sub-Agent Team

```
PERFORMANCE INTELLIGENCE AGENT LEAD
├── Reads: Analytics Dashboard data feed (continuous)
│         + All Layer 2 strategy docs (benchmarks, funnel specs, thresholds)
│         + All Layer 3 agent output history (what was built, when, what changed)
├── Triggers: On every red/yellow flag from Analytics Dashboard
│            + Weekly opportunity scan (every Monday)
├── Orchestrates: 4 sub-agents below
└── Delivers: Diagnosis reports → Optimization Agent
              Weekly opportunity brief → IQ Claw dashboard

SUB-AGENTS:

1. Root Cause Analyst
   Receives: Flag from Analytics Dashboard (metric, current value, baseline, deviation)
   Process: Cross-references all available data sources to isolate root cause
   Uses: Correlation analysis (what else changed when this metric changed?)
         Timeline analysis (when exactly did it start declining — what happened that day/week?)
         Segment analysis (is it all segments or one specific audience/sequence/campaign?)
   Output: Root cause hypothesis with confidence level + supporting evidence
   Standard: Never outputs "performance dropped" without a specific hypothesis for why

2. Diagnosis Writer
   Receives: Root cause hypothesis from Root Cause Analyst
   Writes: Full diagnosis in plain language — what's happening, why, evidence, severity
   Format: 3-part structure — Observation (what the data shows) / Root Cause (why it's happening) /
           Fix Type (what kind of solution is needed — automatic vs. human-required)
   Calibrates: Urgency level (fix within 24h vs. this week vs. next cycle)

3. Opportunity Scanner
   Runs: Weekly scan across all performance data
   Identifies: Positive anomalies, replication opportunities, correlation patterns, timing patterns
   Produces: Weekly opportunity brief (3–5 specific opportunities with supporting data)
   Routes: High-confidence opportunities to Optimization Agent for automatic implementation

4. Cross-Channel Correlation Agent
   Specialty: Finds relationships between data streams that the single-channel agents miss
   Examples: "Your best-performing podcast episodes are driving 34% higher webinar show rates
             among listeners who also follow your Instagram. Your non-podcast email subscribers
             show at 47%. Implication: grow podcast first, then monetize."
   Or: "Ad creative that emphasizes the mechanism (root cause angle) generates CPLs 31% lower
        than symptom-focused creative for your audience — but only for cold traffic. Warm
        retargeting performs better with symptom language."
   Runs: Weekly analysis of cross-channel patterns
   Output: Cross-channel insight report → Performance Intelligence Lead → Diagnosis Writer
```

**Agent count: 5** (Performance Intelligence Lead + 4 sub-agents)

---

---

## Step 19 — Optimization Agent

### What It Is

The execution layer. Where Performance Intelligence identifies what needs to change, the Optimization Agent either changes it automatically or presents a specific, actionable proposal for the expert to approve.

The critical distinction:

**Computer-executable changes** (Optimization Agent executes automatically on a scheduled basis or on approval):
- Pause underperforming ad creative (frequency >3.5 or CTR below threshold)
- Rotate in next ad creative from the approved creative pool
- Adjust Meta ad budget allocation between ad sets (shift spend toward performing sets)
- Update email subject line for a re-send to non-openers
- Swap an underperforming webinar title (A/B variant from Title Optimization Agent)
- Update podcast episode title and description (SEO rewrite from Back-Catalog Revival Agent)
- Reorder lesson sequence in a phase (if data shows a specific lesson is consistently causing drop-off)
- Add a FAQ entry to the patient AI assistant when a new question has been approved

**Human-required changes** (Optimization Agent proposes with exact brief, expert approves, human executes or expert delegates to their team):
- Record a new webinar with a different angle or offer position
- Change the program's Phase 2 supplement protocol (clinical decision)
- Rewrite the webinar sales script (requires expert review of the new angle)
- Change the core offer price point or guarantee structure
- Approve a new ad creative batch for production
- Make a major funnel architecture change (add or remove a funnel step)

For every human-required change, the Optimization Agent produces a complete brief — not just "you should change this." It produces: what to change, exactly how to change it, what to say, the evidence justifying the change, and an expected impact estimate.

### Execution Modes

**Auto-Execute (expert has pre-approved this category):**
Expert can grant standing authorization for specific optimization categories. Examples:
- "Auto-pause any ad creative with frequency >3.5 — always"
- "Auto-shift budget toward the best-performing ad set, up to 60% of daily budget"
- "Auto-send re-open sequence to non-openers 48 hours after any broadcast email"

**Approve-and-Execute:**
Optimization Agent presents the proposed change with full brief. Expert reviews in IQ Claw dashboard and clicks Approve. Agent executes immediately.

**Propose-Only (human-required):**
Optimization Agent presents the full brief with all supporting data. Expert or their team implements manually. Agent tracks whether the change was implemented and whether it worked.

### The Optimization Briefing Format

Every optimization — whether auto, approve-execute, or propose-only — gets the same briefing format:

```
OPTIMIZATION BRIEF #[N]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STATUS: [🔴 RED — Immediate / 🟡 YELLOW — This Week / ⬆️ OPPORTUNITY]
TYPE: [Auto-Execute / Approve & Execute / Proposal — Human Required]
AREA: [Paid Ads / Funnel / Content / Email / Program / Podcast]

WHAT'S HAPPENING:
[2-3 sentences. The metric, the deviation, the impact.]

WHY IT'S HAPPENING:
[Root cause from Performance Intelligence Agent. Specific.]

WHAT NEEDS TO CHANGE:
[Exact change. Not vague. "Pause Ad Set ID #12847 and shift its
$85/day budget to Ad Set ID #12849" or "Update the Phase 2 module
intro script to address the supplement timing question before lesson 3."]

EXPECTED IMPACT:
[Specific estimate. "Based on prior creative rotations, expect CPL
to return to $22–26 range within 5–7 days."]

EXECUTION:
[Auto-executing in 2 hours / Awaiting your approval / Brief attached
— implement before next ad spend cycle]

[ APPROVE ] [ MODIFY ] [ DISMISS ]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

### The Optimization Agent Sub-Agent Team

```
OPTIMIZATION AGENT LEAD
├── Reads: Diagnosis reports from Performance Intelligence Agent
│         + Opportunity briefs from Performance Intelligence Agent
│         + Expert's pre-authorized execution categories
├── Determines: Execution mode (auto / approve-execute / propose-only)
├── Orchestrates: 5 sub-agents below
└── Delivers: Executed changes (auto) + Optimization Briefs (approve/propose)
              to expert dashboard via IQ Claw

SUB-AGENTS:

1. Ad Optimization Executor
   Scope: All Meta Ads Manager changes
   Auto-executes (with standing authorization): Creative pauses, budget shifts, audience
   bid adjustments, creative rotation from approved pool
   Produces briefs for: New creative batch requests, audience restructuring, offer changes,
   campaign architecture changes
   API integration: Meta Ads Manager API — reads and writes campaign data directly
   Guardrails: Never pauses an entire campaign automatically. Never increases total daily
   budget above expert's set cap. Never changes the offer or headline without approval.

2. Funnel Optimization Executor
   Scope: All funnel page changes, email sequence changes, GHL automation adjustments
   Auto-executes: Subject line swaps for re-opens, sequence timing adjustments,
   page title A/B test activation, GHL pipeline stage trigger updates
   Produces briefs for: Page copy rewrites, funnel architecture changes, offer repositioning,
   new sequence creation requests (routes to Email Builder)
   API integrations: GHL API, Email platform API, IQ Platform funnel hosting

3. Content Optimization Executor
   Scope: Content calendar adjustments, awareness level distribution corrections,
   hook bank updates, template performance score updates
   Auto-executes: Content calendar rebalancing (if awareness distribution is skewed),
   hook bank priority updates based on performance data,
   podcast episode title/description updates (SEO rewrites)
   Produces briefs for: New content batch requests, content strategy pivots,
   new hook angle tests (routes to Content Builder)

4. Program Optimization Executor
   Scope: Course player changes, lesson sequence adjustments, FAQ additions,
   phase pacing recommendations
   Auto-executes: FAQ entries (when expert approves patient AI answers),
   lesson completion nudge timing adjustments, phase reminder email timing
   Produces briefs for: New lesson creation (routes to Program Builder),
   protocol updates (clinical decisions — always human-required),
   phase structure changes

5. Impact Tracker
   Tracks: Every optimization that was executed — both auto and approved
   Measures: Did the change produce the expected result?
   Timeline: Checks impact at 48 hours, 7 days, and 30 days post-change
   Feeds back: Impact data to Learning & Feedback Engine (Step 20)
   Produces: Monthly optimization impact report (what we changed, what happened,
   what we learned — feeds directly into platform improvement)
```

**Agent count: 6** (Optimization Agent Lead + 5 sub-agents)

---

---

## Step 20 — Learning & Feedback Engine

### What It Is

The engine that makes the whole platform get smarter over time. Every human decision, every optimization outcome, every performance data point, every expert edit — it all feeds in here, and the platform updates accordingly.

This is not a passive data warehouse. It is an active system that continuously updates the priors — the default assumptions, templates, thresholds, and recommendations — that every other agent uses. Every expert's platform gets smarter for that expert. And where patterns are universal, every expert on the platform benefits.

### Two Types of Learning

**1. Expert-Specific Learning (individual)**
Everything learned about this specific expert's audience, voice, business, and performance patterns. Lives in the expert's own data layer. Never shared.

Examples of what updates:
- Voice DNA refinements (based on which copy the expert approves vs. edits or rejects)
- Hook angle performance rankings (which hooks convert for this specific audience)
- Best posting times (when this expert's audience engages most)
- Optimal ad creative styles (which visual approaches produce the lowest CPL for this expert)
- Email subject line patterns that work for this list
- Which lead magnets produce the highest-quality leads (highest downstream conversion to high-ticket)
- Phase dropout predictors (what combination of early signals predicts a patient dropping from Phase 2)

**2. Platform-Level Learning (universal)**
Anonymized patterns that are true across many experts. Used to improve default templates, benchmarks, and recommendations for all experts. Experts whose data contributes never see other experts' data.

Examples of what updates at platform level:
- Industry benchmark thresholds (as more real data comes in, "what is a good webinar show rate for a hormone expert" becomes a real-data benchmark instead of an industry guess)
- Hook formula performance (which hook types work best for which awareness levels in health niches)
- Email subject line patterns that work across health audiences
- Program phase length recommendations (what phase durations produce highest completion rates by specialty)
- Ad creative style performance by specialty (what visual style works best for gut health vs. hormone health)

### The Feedback Inputs

**Automatic data feedback (no human required):**
- Every performance metric (what worked, what didn't)
- Every optimization outcome (did the change produce the expected result?)
- A/B test results (which title, which creative, which subject line won)
- Content performance by type, hook, awareness level, posting time
- Email performance by subject line pattern, send time, sequence position
- Funnel conversion by traffic source, creative angle, offer framing

**Human feedback (captured systematically):**
- Expert approvals and rejections of agent outputs (every approval = positive signal; every rejection = negative signal + reason logged)
- Expert edits to agent outputs (what they changed = data on what the agent got wrong)
- Manual overrides (expert changes something the platform recommended against = logged as potential preference vs. platform error)
- Expert ratings (after each major output, option to rate — used sparingly, not required)
- IQ Claw conversation signals (when the expert says "this isn't quite right" or "this is exactly what I wanted" — those signals are captured)

### What Gets Updated

```
WHAT THE LEARNING ENGINE UPDATES:

Voice DNA
├── Updated when: Expert consistently edits copy in a specific direction
│                Expert rejects outputs that use certain patterns
│                Expert approves outputs with specific language characteristics
└── Result: Agent outputs get closer to the expert's natural voice over time

Hook Bank & Performance Rankings
├── Updated when: Performance data shows specific hook types outperforming
│                Clip Intelligence Agent tracks which clips went viral
└── Result: Runsheet Agent and Content Builder prioritize highest-performing hooks

Red/Yellow/Green Thresholds
├── Updated: Every 90 days with rolling performance data
│           Immediately when expert manually sets a threshold
└── Result: Benchmarks reflect this expert's actual performance range, not industry averages

Audience Intelligence Priors
├── Updated when: Content on specific topics consistently outperforms
│                Specific audience segments show higher conversion rates
└── Result: Audience Intelligence Agent surfaces more relevant content recommendations

Program Content Gaps
├── Updated when: New patient questions are asked and answered
│                Expert adds new content to phases
└── Result: Patient AI Assistant gets more accurate; fewer questions go unanswered

Production Defaults
├── Updated when: Expert consistently approves certain content approaches
│                Expert consistently modifies specific agent default choices
└── Result: Agents produce closer-to-final outputs faster over time

Ad Creative Learning
├── Updated when: New creative results come in
│                Cost-per-lead data by creative style accumulates
└── Result: Ad Optimization Executor makes better automatic decisions
```

---

### The Learning & Feedback Engine Sub-Agent Team

```
LEARNING & FEEDBACK ENGINE LEAD
├── Reads: All performance data (continuous feed from Analytics Dashboard)
│         All optimization outcomes (from Optimization Agent Impact Tracker)
│         All human feedback signals (approvals, rejections, edits, IQ Claw conversations)
│         All A/B test results
├── Determines: What to update, when to update it, what confidence level justifies an update
├── Orchestrates: 4 sub-agents below
└── Delivers: Updated priors to all agents + Monthly learning report to expert

SUB-AGENTS:

1. Human Feedback Processor
   Captures: All expert approvals, rejections, edits, and ratings across the entire platform
   Classifies: Each feedback signal by type (voice, structure, strategy, factual correction, preference)
   Extracts: What the agent got right vs. wrong in each case
   Confidence weighting: Single rejection = low signal; consistent pattern = high signal
   Routes: Classified feedback to the appropriate prior-update agent
   Principle: Never updates a prior based on a single data point. Looks for consistent patterns
               before making any change.

2. Performance Pattern Extractor
   Runs: Continuous analysis of all performance data
   Identifies: Statistically significant patterns (not noise)
   Separates: Expert-specific patterns vs. universal patterns
   Produces: Pattern reports with confidence scores
   Examples: "Hook type: 'contrarian claim' is producing 34% higher saves for this expert
              over last 90 days vs. other hook types — update hook bank priority score"
   Routes: Expert-specific patterns to Expert Prior Manager
           Universal patterns to Platform Prior Manager

3. Expert Prior Manager
   Owns: This expert's personalized prior layer — the stored preferences, performance patterns,
         and learned behaviors that make this expert's platform unique to them
   Updates: Voice DNA, hook rankings, threshold calibrations, audience intelligence priors,
            production defaults, ad creative performance rankings
   Versioning: Every prior update is versioned — the platform can roll back to a prior state
               if an update made things worse
   Transparency: Expert can view their prior layer at any time ("here's what I know about
                 what works for your audience") and manually correct anything

4. Platform Prior Manager
   Owns: The anonymized universal learning layer — patterns that apply across experts
   Updates: Industry benchmarks, default templates, formula performance data
   Privacy: Operates only on anonymized, aggregated data — no individual expert data
   Governance: Changes to universal priors require a confidence threshold
               (observed in N≥10 experts before updating the platform default)
   Impact: When a universal prior updates, all experts benefit from the better default —
           even if they've never had the specific performance event that triggered the update
```

**Agent count: 5** (Learning & Feedback Engine Lead + 4 sub-agents)

---

---

## Layer 4 Complete Architecture

```
ANALYTICS DASHBOARD (Step 17)
├── Data Ingestion Agent ←── All external APIs
├── Benchmark & Threshold Manager
├── Anomaly Detection Agent
└── Dashboard Renderer → Expert Dashboard

        ↓ (every red/yellow flag + weekly scan)

PERFORMANCE INTELLIGENCE AGENT (Step 18)
├── Root Cause Analyst
├── Diagnosis Writer → Diagnosis Reports
├── Opportunity Scanner → Opportunity Briefs
└── Cross-Channel Correlation Agent

        ↓ (diagnosis reports + opportunity briefs)

OPTIMIZATION AGENT (Step 19)
├── Ad Optimization Executor → Meta Ads API (auto-execute)
├── Funnel Optimization Executor → GHL API (auto-execute)
├── Content Optimization Executor → Content Calendar (auto-execute)
├── Program Optimization Executor → IQ Platform (auto-execute)
└── Impact Tracker → feeds Step 20

        ↓ (all outcomes, all human feedback)

LEARNING & FEEDBACK ENGINE (Step 20)
├── Human Feedback Processor
├── Performance Pattern Extractor
├── Expert Prior Manager → updates all agent priors (expert-specific)
└── Platform Prior Manager → updates all default templates (universal)

        ↓ (updated priors flow back to ALL agents in all layers)
        
LAYERS 1–3 (all agents get smarter every cycle)
```

---

## All Data Sources Connected to Layer 4

| Source | Data | Connection | Cadence |
|--------|------|------------|---------|
| **Meta Ads Manager** | Spend, CPL, ROAS, CTR, frequency, creative performance | API | Every 4 hours |
| **GoHighLevel (GHL)** | Pipeline, contacts, funnel conversion, automation activity, revenue | API | Every 6 hours |
| **Klaviyo / Email Platform** | List size, open/click rates, sequence performance, deliverability | API | Every 12 hours |
| **Instagram** | Followers, reach, engagement, saves, shares, story views | API | Every 24 hours |
| **Facebook** | Page metrics, post performance, group activity | API | Every 24 hours |
| **TikTok** | Followers, video views, completion, profile visits | API | Every 24 hours |
| **YouTube** | Subscribers, views, watch time, CTR, Shorts | API | Every 24 hours |
| **Google Search Console** | Impressions, clicks, positions, queries | API | Every 24 hours |
| **Google Analytics** | Sessions, bounce, conversion, landing pages | API | Every 24 hours |
| **Apple Podcasts Connect** | Downloads, followers, reviews, chart position | API | Every 24 hours |
| **Spotify for Podcasters** | Streams, listeners, completion, followers | API | Every 24 hours |
| **IQ Platform (Program)** | Enrollments, completions, lesson data, student questions | Real-time | Real-time |
| **IQ Platform (Production)** | Asset pipeline, approval rates, publish rates | Real-time | Real-time |
| **IQ Drive** | Asset library, performance tags, block usage | Real-time | Real-time |
| **TikTok Ads / Google Ads** | Campaign performance (if active) | API | Every 4 hours |
| **Podcast Ad Platforms** | Spotify Ads, Overcast CPF, Podcast Addict | API | Every 24 hours |

---

## Layer 4 Agent Count Summary

| Step | Agent | Lead | Sub-Agents | Total |
|------|-------|------|-----------|-------|
| 17 | Analytics Dashboard | 1 | 4 | **5** |
| 18 | Performance Intelligence | 1 | 4 | **5** |
| 19 | Optimization Agent | 1 | 5 | **6** |
| 20 | Learning & Feedback Engine | 1 | 4 | **5** |
| **Layer 4 Total** | | **4** | **17** | **21** |

---

## IQ Claw Integration — Layer 4 Requests

| Expert Says | IQ Claw Routes To |
|-------------|------------------|
| "How is everything performing?" | Analytics Dashboard → Command View |
| "Why is my webinar show rate low?" | Performance Intelligence → Root Cause Analyst |
| "What should I fix first?" | Performance Intelligence → Diagnosis Writer (priority sort) |
| "What's working that I should do more of?" | Performance Intelligence → Opportunity Scanner |
| "Fix my underperforming ads" | Optimization Agent → Ad Optimization Executor |
| "What changes are pending my approval?" | Optimization Agent → brief queue |
| "Approve all ad pauses" | Optimization Agent → executes all queued ad pauses |
| "What has the platform learned about my audience?" | Learning Engine → Expert Prior Manager |
| "Show me my dashboard" | Analytics Dashboard → full dashboard view |
| "What does my funnel look like this week?" | Analytics Dashboard → Funnel Performance View |

---

*Layer 4 — Steps 17–20 — Analytics Dashboard + Performance Intelligence + Optimization Agent + Learning & Feedback Engine — v1.0*
*Next: Step 21 — Cross-Agent Consistency Audit | Step 22 — Final Master Agent Description Document*
