# ClinicIQ — Layer 5: The IQ Intelligence Platform
# L5-5: IQ Score
**Version 1.0**
*Layer 5, Spec 5 of 5 | Depends on: All prior layers — L5-1 through L5-4, Layer 4 Analytics, Network Intelligence*

---

## Purpose

Every iPhone user knows their battery percentage. It's a single number. Everyone understands it immediately. It creates a behavior loop — you watch it, you react to it, you make decisions based on it, you feel a quiet anxiety when it drops too low and a quiet satisfaction when it's full. Apple didn't invent the battery. They invented the number that made the battery *meaningful* to every person who held the phone.

**The IQ Score is that number for the health expert's business.**

Not a dashboard with 47 metrics. Not a report that takes 20 minutes to interpret. One number, 0–100, that tells the expert — instantly, every single day — how healthy their entire growth engine is. Where it's strong. Where it's bleeding. What to do next. And exactly how far they are from their best.

This spec defines what the IQ Score is, how it's calculated, what every point represents, how it displays, how experts move it, and — most importantly — how it becomes the central behavioral and emotional engine of the entire ClinicIQ platform.

The IQ Score is not a reporting feature. **It is the product.**

---

## The Core Design Philosophy

### One Number, Total Clarity

The expert should be able to glance at their IQ Score and know in under three seconds whether their business is healthy, growing, struggling, or on fire — without reading a single chart.

That requires the score to be:
- **Honest** — it reflects reality, not a vanity metric
- **Specific** — when it drops, the expert knows exactly why
- **Actionable** — every point lost comes with a clear path to recovering it
- **Comparable** — the expert knows what a "good" score looks like in their niche (via Network Intelligence benchmarks)
- **Gameable in the right way** — every action that improves the IQ Score also genuinely improves the business

The last point is critical. A score that can be gamed by doing shallow work is worse than no score. The IQ Score is designed so the only way to improve it is to do the things that actually make the business stronger. There are no shortcuts.

### The Emotional Contract

The IQ Score creates a daily emotional relationship between the expert and their business health. It should feel:

- **Satisfying** when it rises — even by one point
- **Motivating** when it plateaus — "I know exactly what to do"
- **Urgent but not panicked** when it drops — "I understand why and I have a plan"
- **Pride-worthy** when it's high — worth sharing, worth talking about

The number becomes part of the expert's identity on the platform. A 91 score is something they're proud of. A 54 score is something they're actively working to fix. A sudden drop from 78 to 71 is something IQ Claw explains immediately and already has a plan for.

---

## The IQ Score Architecture: Eight Dimensions

The IQ Score is a weighted composite of eight business health dimensions. Each dimension is scored 0–100. The composite is calculated as a weighted average. The result is a single number, 0–100.

Every dimension is benchmarked against the Network Intelligence Conversion Benchmark Engine — so the score reflects real-world performance standards for this expert's specific niche and audience, not generic thresholds.

---

### Dimension 1 — Audience & Reach (Weight: 12%)
*"Are you in front of the right people, at the right scale, and growing?"*

**What it measures:**
- Total addressable audience size (email list + social followings + podcast subscribers + YouTube subscribers) — weighted by platform conversion potential
- Audience growth rate (week-over-week, month-over-month)
- Audience quality signal (engagement rate vs. follower count — large audiences that don't engage score lower)
- Cross-platform reach distribution (over-reliance on one platform caps this score)

**Scoring logic:**
| Score Range | What It Means |
|-------------|--------------|
| 85–100 | Large, growing, engaged audience across multiple platforms |
| 70–84 | Good audience size and growth, some platform concentration |
| 50–69 | Moderate audience, slow growth or declining engagement |
| 30–49 | Small audience or stagnant — significant opportunity here |
| 0–29 | Minimal audience — top priority to address |

**How to move it:**
- Consistent content publishing (Content Builder)
- Podcast growth (Podcast Agent)
- Paid audience building (Ad Creative Builder)
- List growth via lead magnets (Lead Magnet Builder)

---

### Dimension 2 — Lead Generation (Weight: 15%)
*"Are you converting attention into identified, contactable leads at a healthy rate?"*

**What it measures:**
- Opt-in conversion rate (benchmarked against niche average via Network Intelligence)
- Weekly/monthly new lead volume
- Lead quality score (derived from downstream conversion — leads that buy score quality higher retroactively)
- Lead source diversity (relying on one source is fragile — diversity improves this score)
- Cost per lead (if paid traffic active)

**Scoring logic:**
- Opt-in rate in top quartile for niche → strong contribution
- Growing lead volume week-over-week → strong contribution
- Single lead source only → cap applied — cannot score above 72 regardless of volume
- CPL within niche benchmark range → full contribution; CPL >2x benchmark → score penalty

**How to move it:**
- Optimize opt-in page (Funnel Builder)
- Add a second lead source (organic + paid, or add a lead magnet)
- Improve ad creative (Ad Creative Builder)
- Add a quiz or interactive lead magnet (Lead Magnet Builder)

---

### Dimension 3 — Conversion Engine (Weight: 20%)
*"Are your leads becoming buyers at a healthy rate?"*

**This is the highest-weighted dimension because it is the most direct measure of revenue health.**

**What it measures:**
- Webinar show rate (if active)
- Webinar-to-order-page CTR
- Order page conversion rate
- Email sequence conversion rate (nurture → purchase)
- Sales call book rate and close rate (if sales call model is active)
- Overall lead-to-buyer conversion rate

**Scoring logic:**
Every funnel conversion rate is benchmarked against the Conversion Benchmark Engine for this expert's niche × offer type × traffic temperature. The score reflects where this expert sits in the performance distribution — not against a generic standard.

- Top quartile for niche → 85–100 range
- Median for niche → 55–70 range
- Bottom quartile → 30–50 range
- No active conversion mechanism → capped at 25

**How to move it:**
- VSL/webinar optimization (Webinar Builder)
- Funnel page copy refresh (Funnel Builder)
- Email sequence rebuild (Email & SMS Builder)
- Offer stack restructure (via IQ Claw strategy session)
- Miro Fish score improvement on conversion assets

---

### Dimension 4 — Revenue & Monetization (Weight: 18%)
*"Is the business generating real, growing revenue — and is it structured for durability?"*

**What it measures:**
- Monthly revenue (absolute and trend — growing scores higher than flat)
- Revenue per lead (most important efficiency metric)
- Revenue mix health: % from one-time sales vs. continuity/recurring
- Offer stack coverage: are all 4 tiers active and converting?
- Revenue concentration risk: is >80% of revenue from one product or funnel? (Concentrated = fragile)

**The continuity multiplier:**
Recurring revenue scores significantly higher than equivalent one-time revenue in this dimension — because it represents business durability. An expert doing $30K/month with 40% from continuity scores higher on this dimension than an expert doing $35K/month with 0% continuity. The platform actively encourages building recurring revenue because it's better for the expert's long-term business.

**Scoring logic:**
- Revenue growing month-over-month → contribution
- >30% continuity revenue → multiplier applied
- All 4 offer tiers active → full score available
- Revenue concentration >80% in one funnel → penalty applied

**How to move it:**
- Launch or optimize continuity offer (Program Builder + Email Builder)
- Activate a missing offer tier (IQ Claw strategy session)
- Build a second funnel to reduce concentration

---

### Dimension 5 — Content Velocity (Weight: 10%)
*"Are you showing up consistently and building authority with your audience?"*

**What it measures:**
- Publishing frequency vs. expert's own content plan (consistency against their standard, not a universal standard)
- Content engagement rate vs. niche benchmarks
- Content diversity: is the expert showing up on multiple formats/platforms or one only?
- Content-to-lead attribution: is organic content actually generating leads?

**The consistency principle:**
An expert who publishes 3x/week consistently scores higher than one who publishes 7x/week for two weeks then goes dark for three weeks. The score rewards consistency over volume. The platform cares about reliability — because the audience does too.

**Scoring logic:**
- Published within last 7 days → baseline maintained
- Consistent for 30 days straight → compounding score contribution
- Gap >14 days → score begins declining daily
- Content-to-lead attribution active → bonus points

**How to move it:**
- Approve and publish the pre-built content batches (Content Builder)
- Activate the seasonal campaign (Proactive Intelligence Engine)
- Add a second platform (Podcast Agent or YouTube Agent)

---

### Dimension 6 — Patient Outcomes (Weight: 10%)
*"Are the patients who buy actually getting results — and are those results being captured?"*

**This dimension is unique to ClinicIQ among all marketing platforms. No other platform asks this question. It's what makes ClinicIQ a health expert platform, not just a marketing platform.**

**What it measures:**
- Program completion rate (are enrolled patients finishing the program?)
- Phase progression rate (are patients advancing through phases at expected pace?)
- Testimonial capture rate (are wins being documented?)
- Proof bank growth (is new social proof being added?)
- Patient satisfaction signals (review volume, review sentiment, referral rate if tracked)

**Why this matters for marketing:**
Patient outcomes directly feed the Proof Bank, which feeds every conversion asset the platform produces. Better outcomes → richer stories → stronger proof → higher conversion. The circle is complete: platform helps convert, program delivers results, results become proof, proof improves conversion.

An expert with exceptional patient outcomes and a rich, growing proof bank scores at the top of this dimension — and the platform amplifies that advantage across every piece of content and every conversion asset it produces.

**Scoring logic:**
- Program completion rate ≥ 70% → strong contribution
- New testimonial/story added in last 30 days → maintained
- No new proof added in 90 days → score declining
- No program active → dimension scored from testimonial bank only

**How to move it:**
- Capture new patient wins (IQ Claw proof bank session)
- Improve program completion (Program Builder optimization)
- Add a testimonial capture step to program graduation flow

---

### Dimension 7 — Platform Intelligence (Weight: 8%)
*"Is the expert giving the platform what it needs to operate at full power?"*

**What it measures:**
- Dossier Completion Score (from the Living Expert Profile)
- Pending approvals backlog (how many assets are waiting — a large backlog signals the expert isn't moving at business speed)
- Integration completeness (are the key platforms connected?)
- Voice DNA confidence level (from the LEP)
- Data connection health (are the analytics integrations returning clean data?)

**The meta-dimension:**
This is the only dimension that measures the expert's relationship with the platform rather than the business's market performance. It exists because the platform can only be as good as the intelligence it has to work with. An expert who keeps their dossier updated, approves assets promptly, and has all integrations connected allows the platform to operate at full power — which flows directly into every other dimension.

**Scoring logic:**
- Dossier Completion Score ≥ 86 → maximum contribution
- 0 pending approvals → full contribution
- All Tier 1 integrations connected → full contribution
- Voice DNA confidence high → full contribution
- Integration errors or disconnections → score impact until resolved

**How to move it:**
- Complete pending dossier sections (IQ Claw dossier session)
- Clear the approvals queue (batched review session)
- Connect missing integrations

---

### Dimension 8 — Growth Trajectory (Weight: 7%)
*"Is the business moving in the right direction — and accelerating?"*

**The forward-looking dimension.**

**What it measures:**
- 30-day trend across all other seven dimensions (is the overall score rising, flat, or declining?)
- Velocity: how fast is the score moving?
- Momentum consistency: is growth happening in one dimension while others decline (unbalanced) or rising broadly (healthy)?
- Compared to 90-day trajectory: is the current rate of improvement accelerating or slowing?

**Why it's a separate dimension:**
A business can have a good current IQ Score but a declining trajectory — which is a problem that isn't visible from the current score alone. Growth Trajectory captures the momentum of the business, not just its current state. A lower score that's rapidly rising is often healthier than a higher score that's been flat for 6 months.

**Scoring logic:**
- All 7 other dimensions rising → maximum contribution
- Mixed: some rising, some flat → moderate contribution
- Any dimension in sustained decline (30+ days) → penalty applied
- Accelerating improvement (rate is increasing) → bonus applied

**How to move it:**
- Address the lowest-scoring dimension first (IQ Claw always surfaces this)
- Run the Morning Brief action item consistently for 30 days
- Clear the proactive suggestion backlog

---

## The Composite Calculation

```
IQ Score = 
  (Audience & Reach × 0.12) +
  (Lead Generation × 0.15) +
  (Conversion Engine × 0.20) +
  (Revenue & Monetization × 0.18) +
  (Content Velocity × 0.10) +
  (Patient Outcomes × 0.10) +
  (Platform Intelligence × 0.08) +
  (Growth Trajectory × 0.07)
```

**Update frequency:** The IQ Score recalculates every 24 hours, incorporating the latest performance data from all connected integrations. The expert sees the new score in their Morning Brief every morning.

**New expert bootstrapping:** For experts with insufficient data (first 30 days), dimensions are scored against Day-1 Advantage Package benchmarks and clearly labeled as "Estimated" until 30 days of real performance data is available.

---

## The IQ Score Display: What the Expert Sees

### The Primary Display
The IQ Score lives in three permanent locations:

1. **Top of Morning Brief** — first thing the expert sees every day
2. **Navigation rail** — small score chip visible at all times (updates daily)
3. **IQ Profile page header** — with full dimension breakdown below

### The Score Card
When the expert clicks their IQ Score, they see the full Score Card:

```
╔══════════════════════════════════════════════════════════╗
║  IQ SCORE                                    April 2     ║
║                                                          ║
║                      ◉ 74                               ║
║                   ▲ +3 this week                        ║
║                                                          ║
║  Niche rank: Top 34% of gut health experts              ║
╠══════════════════════════════════════════════════════════╣
║  DIMENSION BREAKDOWN                                     ║
║                                                          ║
║  Conversion Engine      ████████████░░░░  82  🟢        ║
║  Revenue & Monetization ███████████░░░░░  78  🟢        ║
║  Audience & Reach       ████████░░░░░░░░  61  🟡        ║
║  Lead Generation        ████████░░░░░░░░  59  🟡        ║
║  Patient Outcomes       ████████░░░░░░░░  57  🟡        ║
║  Content Velocity       ███████░░░░░░░░░  51  🟡        ║
║  Growth Trajectory      ███████████░░░░░  74  🟢        ║
║  Platform Intelligence  ██████████████░░  89  🟢        ║
║                                                          ║
╠══════════════════════════════════════════════════════════╣
║  BIGGEST OPPORTUNITY                                     ║
║                                                          ║
║  📌 Lead Generation (59) is your highest-leverage       ║
║  move right now. Your opt-in rate is 29% vs. the        ║
║  37% average for gut health experts at your             ║
║  traffic temperature. I've drafted a revised            ║
║  opt-in page — one change could move this 8–12          ║
║  points.  [Review it →]                                 ║
╚══════════════════════════════════════════════════════════╝
```

**Design principles for the Score Card:**
- The biggest opportunity is always called out — one action, not a list
- The revised asset is already built and waiting
- The expert knows their niche rank — real context, not abstract numbers
- Green/yellow/red gives instant visual comprehension before reading a word

---

## The Habit Loop: How the IQ Score Changes Expert Behavior

The IQ Score is designed around a specific behavioral loop that makes the expert check it, act on it, and see results — creating a habit that compounds over time.

### The Loop

```
CUE: Morning Brief arrives → IQ Score visible immediately
        ↓
ROUTINE: Expert opens Score Card → sees biggest opportunity → clicks "Review it"
        ↓
REWARD: Approves the pre-built asset → IQ Claw confirms it's deployed
        ↓
VARIABLE REWARD: Score updates tomorrow — did it move?
        ↓
[Loop repeats — expert comes back tomorrow to see the result]
```

The variable reward (will the score actually move?) is the behavioral engine. It's the same mechanism that makes fitness trackers compelling — you take the action today, you check the result tomorrow. ClinicIQ is engineered so that the score visibly moves in response to real actions — and the feedback cycle is tight enough (24 hours) that the expert can trace cause and effect.

### The Social Layer: IQ Score as Status
The IQ Score creates a natural social comparison dynamic among health experts:

- **On the platform:** Experts can see how their score compares to niche averages and percentile ranks (via Network Intelligence)
- **In the community:** "What's your IQ Score?" becomes a real conversation — a shorthand for business health that every ClinicIQ user understands
- **In marketing:** High-scoring experts have a badge to display — a third-party validation that their business is genuinely performing
- **As a floor:** No expert wants to be below 70. The score creates an implicit standard that raises the quality of how every expert runs their business

---

## IQ Score Tiers and What They Signal

| Score | Tier | Status | What It Means |
|-------|------|--------|--------------|
| 90–100 | 🏆 **IQ Elite** | Exceptional | Top 5% of platform. Every engine firing. Growing fast. |
| 80–89 | ⚡ **IQ Pro** | Strong | Strong business, one or two dimensions to optimize |
| 70–79 | 🟢 **IQ Active** | Healthy | Business is healthy and moving. Clear path to Pro. |
| 55–69 | 🟡 **IQ Building** | Developing | Foundation in place, gaps in key conversion areas |
| 40–54 | 🟠 **IQ Early** | Early stage | Good starts but significant gaps — focus needed |
| 0–39 | 🔴 **IQ Starting** | Starting | Platform just activated or major gaps across multiple dimensions |

**Tier transitions are celebrated.** Every time an expert moves up a tier, IQ Claw delivers a congratulatory message, a summary of what drove the improvement, and a specific challenge for the next tier. The transition feels earned — because it is.

---

## The IQ Score and the Monthly Master Plan

Every month, when the Monthly Master Plan refreshes (Layer 4 trigger), the IQ Score plays a central role in what the plan prioritizes.

The Monthly Master Plan always opens with the IQ Score diagnostic:

```
MONTHLY MASTER PLAN — APRIL 2026
IQ Score: 74 → Target: 80+ by April 30

This month's plan is optimized to close the gap on your two
lowest dimensions:

Priority 1: Lead Generation (59 → 70 target)
  → Revised opt-in page (ready for approval)
  → New lead magnet concept (ready to build)
  → Paid traffic test to new opt-in page (budget: $500/week)

Priority 2: Content Velocity (51 → 65 target)
  → 16-post content batch pre-built for April
  → Podcast episode 3 script ready
  → YouTube short series (4 videos) ready to review

These two moves, fully executed, are projected to move your
IQ Score from 74 to approximately 81. That puts you in the
top 22% of gut health experts on the platform.
```

The Monthly Master Plan is the strategic bridge between the IQ Score (what is) and the monthly build activity (what to do). The score gives the plan focus. The plan gives the score movement.

---

## IQ Score Over Time: The Long Game

The IQ Score isn't just about today. It's about the arc of the expert's business over time — and what that arc reveals.

**The trajectory view (available on the IQ Profile page):**
A 12-month chart showing IQ Score by day. The expert can see:
- When they launched campaigns (score spikes)
- When they went quiet (score gradual decline)
- Seasonal patterns (scores tend to dip in holiday periods for most health niches)
- The overall trend — is the business structurally getting stronger?

**What a healthy IQ Score trajectory looks like:**
- Gradual upward trend from Month 1 (score builds as platform learns and expert optimizes)
- Regular small dips when a campaign ends or content pauses (normal — shows the score is real)
- Score stabilizes in a higher range as the expert matures on the platform
- Occasional sharp rises when a new funnel or campaign launches and performs
- Long-term plateau-breaking moments when a new offer tier or channel is activated

**What a concerning trajectory looks like:**
- Flat score for 60+ days (plateau — expert needs a new initiative)
- Steady slow decline over 90 days (systematic underperformance in a key dimension)
- Volatile score with no upward trend (reactive rather than strategic — inconsistent execution)

IQ Claw proactively addresses all three concerning patterns before they become business-threatening. The Proactive Intelligence Engine monitors trajectory and surfaces the plateau/decline signal in the Morning Brief — with a specific plan already built.

---

## IQ Score as the North Star of the Entire Platform

Every other spec in every other layer of ClinicIQ ultimately points to the IQ Score:

- **Layer 1 (Onboarding)** → builds the Platform Intelligence dimension
- **Layer 2 (Brand & Growth Strategy)** → builds the strategic foundation that all conversion dimensions run on
- **Layer 3 (Builder Agents)** → produces the assets that move Conversion, Content Velocity, Lead Generation
- **Layer 4 (Analytics)** → provides the data that calculates every dimension
- **L5-1 (Living Expert Profile)** → the intelligence layer that makes all scoring context-aware
- **L5-2 (Proactive Intelligence)** → surfaces the actions that move the score
- **L5-3 (One-Tap Deployment)** → removes the friction between approved assets and score movement
- **L5-4 (Network Intelligence)** → provides the benchmarks that make the score meaningful
- **L5-6 (IQ Growth Lab)** → tests new plays before they're reflected in the score

The IQ Score is the synthesizing output of the entire platform. Every feature, every agent, every spec we have ever built — all of it exists to move this number upward for every health expert who uses ClinicIQ.

That is the product. One number. Total clarity. A business that gets better every day.

---

## Summary

The IQ Score is not a metric. It is the central experience of ClinicIQ.

It is what the expert checks every morning before they do anything else. It is what drives the Monthly Master Plan. It is what IQ Claw references in every strategic recommendation. It is what creates status, competition, and identity among experts on the platform. It is what proves to every expert — every day — that ClinicIQ is working.

Eight dimensions. One number. The entire health of their business — visible in a glance, actionable in a tap.

**That is the iPhone moment for the health expert. And it lives right here.**

---

*L5-5: IQ Score — v1.0*
*Layer 5 Complete: L5-1 through L5-5 fully specced.*
*Next: L5-6 — IQ Growth Lab (full spec)*
