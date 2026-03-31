# clinicIQ — Miro Fish: Pre-Launch Audience Simulation Agent
**Version 1.0**
*Cross-cutting platform service — runs after Output Quality Agent, before IQ Drive publish*
*Mandatory for: Ads, Webinars, Funnels | Optional for: High-stakes organic content*

---

## What It Is

Miro Fish is clinicIQ's pre-launch audience simulation system. Before any ad, webinar, or funnel asset goes live, it gets run through a synthetic crowd of the expert's specific avatar — across all relevant levels of awareness — and scored on how that crowd is predicted to react.

The output is a score, a verdict (roll / fix first), and specific recommendations for whatever isn't landing. The goal is not to be a gate that slows everything down. It is to catch the fixable problems before they cost money and time — and to give the expert and their team the confidence to launch fast when something is strong.

**The core principle:** If it passes, roll. If it doesn't, here's exactly what to fix. Then roll.

---

## Where It Sits in the Pipeline

```
BUILDER AGENT produces finished asset
        │
        ▼
OUTPUT QUALITY AGENT (Voice QA + Brand QA)
        │
        ▼ (if passed)
MIRO FISH SIMULATION AGENT  ◄── THIS IS HERE
        │
        ├── Score ≥ threshold → asset released to IQ Drive → expert publishes
        │
        └── Score < threshold → Recommendation Report → Builder agent refines
                                        │
                                        ▼
                              Refined asset → Miro Fish again
                                        │
                              Pass → IQ Drive → publish
                              (max 2 iterations — if still failing, expert decides)
```

**Hard rule on iteration:** Maximum 2 automated revision cycles. If the asset still doesn't pass after 2 rounds, it goes to the expert with the full simulation report and a clear note: "This is borderline — here's what the crowd is saying. Your call." The platform never holds an asset hostage indefinitely.

---

## When Miro Fish Runs

**Mandatory (always runs before publish):**
- All Meta ad creative (static, video, carousel, UGC)
- All webinar scripts (before recording)
- All funnel pages (opt-in, sales page, order page)
- All VSL scripts (before recording)
- All email launch sequences (welcome, post-webinar, promo campaigns)

**Optional (expert-triggered):**
- Organic social content (available but not required — everyday posts don't need this)
- Podcast episode titles and hooks (recommended for new show topics)
- Lead magnet concepts before production

**Never runs on:**
- Internal documents (strategy docs, dossier, briefs)
- Program curriculum content (different evaluation standard — educational, not conversion)
- Operational assets (thank you pages, receipts, onboarding emails)

---

## The Synthetic Crowd — How It Works

### The Core Avatar

Every simulation is grounded in the expert's Core Avatar from the Expert Dossier — the 8-layer profile built during onboarding:

1. Demographics (age range, gender, income, location type)
2. Primary health concern (specific, not generic)
3. Emotional state (frustrated, hopeful, skeptical, exhausted — varies by awareness level)
4. False beliefs held (what they believe that's keeping them stuck)
5. Past failed attempts (what they've tried that didn't work)
6. Internal language (the exact words they use to describe their problem)
7. Aspirational identity (who they want to become)
8. Objection profile (what makes them hesitate)

### The Five Awareness Instances

The Core Avatar is instantiated at each Level of Awareness. Each instance has a distinct mindset, emotional posture, and set of reactions:

| Level | Name | Mindset | What They Need from the Asset |
|-------|------|---------|-------------------------------|
| L1 | Unaware | "I don't know why I feel this way" | Pattern interrupt — stop the scroll, create curiosity |
| L2 | Problem-Aware | "Something is wrong but I don't know what" | Validation — "yes, that's exactly what I have" |
| L3 | Solution-Aware | "I've tried things, nothing worked" | Differentiation — "this is different because..." |
| L4 | Product-Aware | "I've seen this expert before, not sure yet" | Trust + specificity — proof and clarity of mechanism |
| L5 | Most Aware | "I'm ready but I have one last hesitation" | Remove the final friction — guarantee, urgency, simplicity |

### The Synthetic Crowd

For each awareness level relevant to the asset type, the simulation spins up a crowd sampled across the variance ranges in the Core Avatar (age, income, concern severity, skepticism level). This produces a distribution of reactions rather than a single opinion — and makes the score statistically meaningful, not a coin flip.

Crowd size is **fully configurable** — the expert sets their preferred crowd size per asset type, and the system defaults to the tier matching their plan. More respondents = more statistical confidence = higher token cost = more reliable prediction. For high-stakes assets like webinars and flagship funnels, running a larger crowd is the right call and worth the cost.

### Crowd Size Tiers

| Tier | Respondents Per Awareness Level | Total (3 levels) | Best For |
|------|---------------------------------|-----------------|----------|
| **Quick** | 50 | ~150 | Everyday ads, organic content testing, fast iteration |
| **Standard** | 200 | ~600 | Regular ad campaigns, email sequences, opt-in pages |
| **Deep** | 500 | ~1,500 | Sales pages, lead magnets, promo campaigns |
| **Full** | 1,000 | ~3,000 | Webinar scripts, flagship funnels, VSLs, major launches |
| **Max** | 2,500 | ~7,500 | Once-a-year flagship launches, new offer rollouts, major pivots |

**Default crowd sizes by asset type (adjustable per expert):**
- Everyday ads (cold traffic test) → **Standard** (600 total)
- Ad campaign launch → **Deep** (1,500 total)
- Email sequences → **Standard** (600 total)
- Sales funnel pages → **Deep** (1,500 total)
- Webinar scripts → **Full** (3,000 total)
- VSL scripts → **Full** (3,000 total)
- Flagship funnel (new offer launch) → **Max** (7,500 total)

**Expert configuration:**
The expert sets their default tier per asset type in IQ Claw settings. They can override per-run — bump a routine ad up to Full if it's for a major campaign, or drop a webinar to Standard if they're doing a quick iteration test. IQ Claw always surfaces the estimated token cost before running so there are no surprises.

**The confidence curve:** Going from 150 to 600 respondents makes a meaningful difference. Going from 1,500 to 3,000 on a webinar is worth it — a webinar that underperforms costs orders of magnitude more than the simulation. Going from 3,000 to 7,500 is for when the stakes are high enough that you want near-certainty before you invest in a full launch. The cost scales with respondents; the confidence curve flattens above ~2,000 per level, so Max tier is reserved for genuinely high-stakes moments.

---

## What Gets Scored

### The Scoring Dimensions

Every asset is scored on dimensions relevant to its type. Not every dimension applies to every asset.

**Universal dimensions (all asset types):**

| Dimension | What It Measures | Weight |
|-----------|-----------------|--------|
| **Hook Strength** | Does the opening stop the scroll / command attention in first 3 seconds? | 25% |
| **Avatar Mirror** | Does the crowd recognize themselves in this immediately? | 20% |
| **Mechanism Clarity** | Is the root cause / unique approach clearly communicated? | 15% |
| **Believability** | Does this feel true and credible, not hype? | 20% |
| **Action Intent** | Does the crowd feel compelled to take the next step? | 20% |

**Ad-specific additional dimensions:**

| Dimension | What It Measures |
|-----------|-----------------|
| **Thumb-Stop Power** | Would this stop a fast scroll? |
| **Cold Traffic Readiness** | Does it work for someone who has never heard of this expert? |
| **Offer Clarity** | Is it immediately clear what's being offered and why it matters? |
| **Visual-Copy Harmony** | Do the image and copy reinforce each other or fight each other? |

**Webinar-specific additional dimensions:**

| Dimension | What It Measures |
|-----------|-----------------|
| **Hook Retention** | Does the opening create enough curiosity to hold attention for 90 minutes? |
| **False Belief Dismantling** | Are the 3 core false beliefs clearly identified and credibly challenged? |
| **Stack Believability** | Does the value stack feel real or inflated? |
| **Offer Timing** | Does the offer arrive at the right emotional moment? |
| **Objection Coverage** | Are the top 5 objections addressed before they arise? |

**Funnel page-specific additional dimensions:**

| Dimension | What It Measures |
|-----------|-----------------|
| **Above-Fold Clarity** | Is the core promise clear before any scrolling? |
| **Social Proof Weight** | Does the proof section create real belief shift? |
| **CTA Friction** | Is there any unnecessary friction at the action point? |
| **Mobile Experience** | Does the crowd engage differently on mobile vs. desktop? |

---

## The Scoring System

### Composite Score

Every asset receives a **composite score from 0–100** based on the weighted dimensions above.

**Verdict thresholds:**

| Score | Verdict | Action |
|-------|---------|--------|
| 85–100 | 🟢 **Roll** | Asset cleared. Release to IQ Drive. Launch. |
| 70–84 | 🟡 **Fix First** | 1–2 specific issues. Automated refinement cycle triggered. Re-score. |
| 50–69 | 🔴 **Significant Rework** | Multiple issues. Refinement cycle triggered twice. If still <70, escalate to expert. |
| <50 | ⛔ **Fundamental Problem** | Asset has a core issue (wrong awareness level, wrong angle, wrong mechanism). Expert review required. New brief recommended. |

### The Score Report

Every Miro Fish run produces a Score Report delivered to the expert's dashboard and to the originating Builder agent:

```
MIRO FISH SCORE REPORT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Asset: [Asset name / type]
Run: [Timestamp]
Crowd: [Awareness levels simulated] · [N respondents]

COMPOSITE SCORE: 78 / 100   🟡 FIX FIRST

DIMENSION BREAKDOWN:
  Hook Strength          ████████░░  81/100  ✓
  Avatar Mirror          ███████░░░  72/100  △ needs work
  Mechanism Clarity      ████████░░  82/100  ✓
  Believability          ███████░░░  74/100  △ needs work
  Action Intent          ███████░░░  71/100  △ needs work

WHERE THE CROWD IS LOSING INTEREST:
  L2 respondents (problem-aware): Hook works. Drops at mechanism reveal.
  "Feels like I've heard this before. Not sure why this is different."

  L3 respondents (solution-aware): Strong hook. Skepticism spike at
  the before/after claims. "These results seem too good to be specific."

TOP 3 FIXES (in order of impact):
  1. Mechanism reveal (lines 4–7): Add ONE specific clinical reason why
     this approach works differently. Currently says "root cause approach"
     without explaining the actual root cause. The L2 crowd needs
     the specific mechanism named — not just implied.

  2. Social proof (lines 14–18): The testimonial is general ("I feel
     so much better"). Replace with a specific, measurable result:
     "[Name] lost 14 lbs in Phase 2 after 3 years of trying everything."
     Specific results break L3 skepticism.

  3. CTA (final line): "Learn more" is too soft for this audience's
     awareness level. L3–L4 crowd needs a directional CTA:
     "Watch the free training →" outperforms "Learn more" by ~30%
     for this avatar profile.

AUTOMATED REFINEMENT: Triggered → Builder agent revising now.
Expected re-score: [timestamp]

[ VIEW FULL CROWD BREAKDOWN ]  [ OVERRIDE & LAUNCH ANYWAY ]  [ REQUEST MANUAL REVIEW ]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### The Expert Override

The expert can always override Miro Fish and launch anyway. The override is one click, it's logged, and it has one consequence: Layer 4's Performance Learning Engine marks this asset as "expert override — monitor closely" and watches its real-world performance with heightened attention. If it underperforms relative to the Miro Fish prediction, that data goes back into calibrating the model. If it overperforms, that also goes back in — Miro Fish learns it was wrong, and why.

---

## The Miro Fish Agent Team

```
MIRO FISH SIMULATION AGENT LEAD
├── Reads: Finished asset (from Output Quality Agent)
│         Expert Dossier (Core Avatar — all 8 layers)
│         Asset type → determines which awareness levels to simulate
│         Historical performance data (from Layer 4 — calibrates predictions)
├── Orchestrates: 4 sub-agents below
└── Delivers: Score Report to expert dashboard + pass/fail signal to pipeline

SUB-AGENTS:

1. Crowd Synthesis Agent
   Reads: Core Avatar from Expert Dossier (demographics, emotional profile,
          false beliefs, objection map, internal language)
   Builds: Synthetic crowd for this simulation run
   - Determines relevant awareness levels for asset type
   - Samples N respondents across Core Avatar variance ranges
   - Each respondent: awareness level, demographic variant, emotional state,
     top 2 false beliefs, primary objection, language register
   - Produces: Crowd manifest (the N personas used in this simulation)
   Principle: Every respondent is a plausible real person, not a statistical abstraction

2. Reaction Simulation Agent
   Reads: Asset (full text + visual direction or image) + Crowd manifest
   Simulates: How each awareness level responds to the asset at each stage
   - Reads the asset as the crowd would encounter it (in feed, in inbox, on page)
   - Identifies: where attention is captured, where interest drops, where skepticism spikes
   - Maps: emotional arc of the crowd through the full asset
   - Flags: specific lines, moments, or elements where a meaningful portion of the
     crowd disengages or objects
   Produces: Crowd reaction map (attention curve + drop-off points + objection moments)

3. Scorer & Diagnostician
   Reads: Crowd reaction map + scoring dimension weights for this asset type
   Calculates: Per-dimension scores + composite score
   Diagnoses: Root cause of any dimension scoring below threshold
   - Not just "believability is low" — why is believability low, which crowd segment,
     at which specific moment, and what is the crowd saying to themselves at that point
   Produces: Score breakdown + ranked fix list (ordered by impact on composite score)

4. Recommendation Writer
   Reads: Score breakdown + ranked fix list + Voice DNA + asset original
   Writes: The specific, actionable recommendations in the Score Report
   Standard: Every recommendation must be specific enough that the Builder agent
             can execute it without asking a clarifying question
   - Bad: "Improve the hook"
   - Good: "Line 1 ('Are you tired of feeling exhausted?') reads as generic to L2 
            crowd. Replace with a specific symptom pattern: 'If you wake up tired 
            no matter how much you sleep, your cortisol rhythm is broken — not 
            your willpower.' Specificity increases avatar mirror score by ~15 points."
   Also writes: The override warning if expert chooses to launch despite failing score
```

**Agent count: 5** (Miro Fish Lead + 4 sub-agents)

---

## How Miro Fish Gets Smarter Over Time

This is where the Layer 4 Learning Engine connection matters.

Every asset that goes through Miro Fish gets a prediction. Every asset that then gets published has real performance data attached to it (from Layer 4's Analytics Dashboard). The Learning Engine continuously compares:

**Predicted score** (what Miro Fish said) vs. **Actual performance** (what Layer 4 measured)

Where predictions were accurate → Miro Fish's model is reinforced.
Where predictions were wrong → Miro Fish's model is updated.

Specifically:
- **Miro Fish said 🟢 Roll, asset underperformed** → scoring model for this asset type recalibrated upward (threshold was too low)
- **Miro Fish said 🟡 Fix First, expert overrode and launched, asset overperformed** → Miro Fish was too conservative on this dimension — recalibrate
- **Fix recommendation was applied, score improved, real-world performance improved** → recommendation pattern reinforced, used more frequently for similar assets

Over 6–12 months of production data, Miro Fish's predictions become significantly more accurate for this expert's specific audience. It is not a static simulation — it is a calibrated model that compounds.

At the platform level (anonymized): patterns observed across many experts in the same specialty (e.g., functional medicine hormone experts) feed into improved default simulation parameters for all new experts in that specialty. A new hormone health expert starting on clinicIQ benefits from the simulation accuracy built up across all the hormone experts before them.

---

## Integration Points

**Reads from:**
- Expert Dossier (Core Avatar — all 8 layers, awareness level map)
- Output Quality Agent (receives assets that have passed Voice + Brand QA)
- Layer 4 Analytics Dashboard (historical performance data for calibration)
- Layer 4 Learning Engine (updated simulation priors)

**Writes to:**
- Score Report → Expert dashboard (via IQ Claw)
- Pass signal → IQ Drive (asset released for publish)
- Fail signal + recommendations → originating Builder agent (refinement cycle)
- Override log → Layer 4 (if expert overrides, performance monitored closely)
- Simulation results → Layer 4 Learning Engine (feeds calibration loop)

**Position in pipeline:**
```
Builder Agent
    → Output Quality Agent (Voice QA + Brand QA)
        → Miro Fish Simulation Agent
            → IQ Drive (on pass)
            → Builder Agent refinement (on fail, max 2 cycles)
            → Expert dashboard (score report always delivered)
```

---

## IQ Claw Integration

| Expert Says | IQ Claw Routes To |
|-------------|------------------|
| "Run the focus group on this ad" | Miro Fish Lead → full simulation |
| "How is this ad going to perform?" | Miro Fish Lead → simulation + score |
| "Why did this asset fail Miro Fish?" | Miro Fish → Score Report detail view |
| "Launch it anyway" | Override logged → IQ Drive release → Layer 4 monitor flag |
| "Fix what Miro Fish flagged" | Recommendation Writer output → Builder agent refinement |
| "How accurate is Miro Fish for my audience?" | Layer 4 → Miro Fish calibration history |

---

*Miro Fish — Pre-Launch Audience Simulation Agent — v1.0*
*File: `/home/work/.openclaw/workspace/cliniciq/platform/miro_fish_simulation_agent.md`*
