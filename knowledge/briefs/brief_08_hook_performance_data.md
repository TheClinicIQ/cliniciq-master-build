# AGENT BRIEF #8 — hook_performance_data.md
**clinicIQ Knowledge Base | Hooks Layer**
**Version 1.0 — April 2026**

---

## Overview

This brief instructs the agent writing:
`/home/work/.openclaw/workspace/cliniciq/knowledge/hooks/hook_performance_data.md`

---

## What the Output File Is

A living data file. The platform's accumulated performance intelligence on which hooks work, for which audiences, on which platforms, across which health niches. Initialized now with schema + seed data so the Ad Performance Analyst (Layer 4) can read from it and write to it correctly from the first day of operation. Two simultaneous functions: data store (structured, machine-readable performance records) and intelligence document (seed data and schema encode the known best-practice starting state).

---

## Source Files the Agent Reads

Before writing, read this file completely:
- `/home/work/.openclaw/workspace/cliniciq/knowledge/hooks/cross_industry_hook_patterns.md`

Read specifically: Section 3 (hook types taxonomy — naming conventions in this file must match exactly), Section 7 (NLP hook layer — NLP tags must match), and Section 11 (hook swipe bank — examples inform style and specificity of seed data).

---

## Output Path

`/home/work/.openclaw/workspace/cliniciq/knowledge/hooks/hook_performance_data.md`

---

## Format Standard

Hybrid: Sections 1–3 and Section 5 are prose/documentation. Section 4 is data entries formatted for both human reading and machine parsing. Consistent formatting for all data entries — same field order, same delimiter style, readable in a text editor. Optimized for machine parsing as much as human reading.

---

## Sections to Produce

### Section 1 — File Header and Update Protocol

**File purpose:** One full paragraph explaining what this file is, who reads it (Ad Creative Builder reads to inform hook selection; Learning Loop Agent reads to identify patterns), who writes to it (Ad Performance Analyst is the sole writer after initialization), and what it is used for (accumulated hook performance intelligence that improves the platform's hook selection over time).

**Update authority:** Ad Performance Analyst (Layer 4) only. No other agent modifies this file.

**Update cadence:** Monthly. First business day of each month. Ad Performance Analyst pulls previous month's data from Meta Ads Manager and TikTok Ads Manager, updates this file.

**Version control convention:**
- Never delete entries — only update the Status field to "paused," "retired," or "seasonal"
- Date-stamp all new entries with the month/year first run
- When an entry is updated (status change, performance data update), add an "Updated" field with the update date
- The file grows monotonically — entries added, never removed

**Entry naming convention:**
Format: HOOK-[TYPE]-[NICHE]-[NUMBER]
Example: HOOK-CURIOSITY-GAP-HORMONES-001
- TYPE: hook type from `cross_industry_hook_patterns.md` taxonomy (use exact type names)
- NICHE: HORMONES / GUT / AUTOIMMUNE / LONGEVITY / FUNCTIONAL-MED / WEIGHT / MENTAL-HEALTH
- NUMBER: sequential 3-digit number within that type/niche combination

---

### Section 2 — The Performance Data Schema

Document every field as a table:

| Field | Type | Format / Allowed Values | Description |
|-------|------|------------------------|-------------|
| Hook ID | String | HOOK-[TYPE]-[NICHE]-[###] | Unique identifier, human-readable |
| Hook Type | Enum | From cross_industry_hook_patterns.md taxonomy | Hook category — must use exact taxonomy names |
| NLP Layer | Enum | From cross_industry_hook_patterns.md Section 7 | Primary NLP mechanic embedded in hook |
| Hook Text | String | Exact copy used | The complete hook as it appeared — no paraphrasing |
| Format | Enum | Video-Hook / Image-Text / Carousel-Slide-1 / Email-Subject / Ad-Headline | Asset format type |
| Platform | Enum | FB-Feed / IG-Feed / IG-Story / IG-Reel / TikTok / YouTube-Pre-Roll / Email | Delivery platform |
| Expert Niche | Enum | HORMONES / GUT / AUTOIMMUNE / LONGEVITY / FUNCTIONAL-MED / WEIGHT / MENTAL-HEALTH | Health specialty |
| Awareness Level | Enum | L1-Unaware / L2-Problem-Aware / L3-Solution-Aware / L4-Product-Aware / L5-Most-Aware | Target awareness level |
| Traffic Temp | Enum | Cold / Warm / Hot | Audience temperature |
| Launch Date | Date | YYYY-MM | Month and year first deployed |
| Impressions | Integer | Number | Total impressions accumulated |
| Thumb Stop Rate | Percentage | 0.0–100.0 | % who stopped scrolling (video and image formats) |
| Hook Hold Rate | Percentage | 0.0–100.0 | % who watched past 3 seconds (video formats only — null for image/text) |
| CTR | Percentage | 0.0–10.0 | Link click-through rate |
| CPL | Currency | $0.00 | Cost per lead |
| ROAS | Decimal | 0.00 (null if not tracked to purchase) | Return on ad spend |
| Status | Enum | Active / Paused / Retired / Seasonal | Current operational status |
| Season Notes | String | Free text or null | If Seasonal: which months/events it performs in |
| Performance Notes | String | Free text | What worked, what didn't, context, observations |
| Updated | Date | YYYY-MM-DD | Date of most recent field update |

**Performance benchmarks for the health niche (used by Ad Performance Analyst to classify performance):**

Thumb Stop Rate (health niche, cold traffic):
- Under 20%: poor — hook is not stopping the right people
- 20–35%: below average — some relevance but lacks pattern interrupt power
- 35–50%: good — hook working effectively
- 50%+: excellent — strong pattern interrupt for this audience

Hook Hold Rate (3-second retention, health niche):
- Under 30%: the hook stopped them but the bridge didn't hold — disconnect between frame 1 and frames 1–3
- 30–50%: average
- 50–70%: good
- 70%+: excellent — both hook and bridge are strong

CTR (health niche, Meta):
- Under 0.5%: poor
- 0.5–1.5%: average
- 1.5–3%: good
- 3%+: excellent

CPL (health niche, lead magnet / webinar registration, cold traffic):
- Over $35: investigate — likely audience, creative, or funnel issue
- $15–35: average
- $8–15: good
- Under $8: excellent — scale immediately

---

### Section 3 — Platform-Level Monthly Aggregates Schema

After the individual hook entries, the file contains a monthly summary block appended each month. Document the complete schema:

```
## Monthly Platform Summary — [MONTH YEAR]
Updated: [YYYY-MM-DD]

### Top 5 Hooks by Thumb Stop Rate (this month)
| Hook ID | Hook Text (truncated) | Platform | Thumb Stop Rate |
|---------|----------------------|----------|-----------------|

### Top 5 Hooks by CPL (this month)
| Hook ID | Hook Text (truncated) | Platform | CPL |
|---------|----------------------|----------|-----|

### Hook Types — Performance Trends (this month vs. prior month)
| Hook Type | Avg Thumb Stop | Avg CTR | Avg CPL | Trend |
|-----------|---------------|---------|---------|-------|
(Trend: ↑ improving / ↓ declining / → stable)

### Declining Patterns (flag for alternative testing)
[List: hook type/niche combinations where CPL has increased >20% month-over-month for 2+ consecutive months]

### New Patterns to Test Next Month
[List: hook type/niche combinations not yet tested or with under 500 impressions]

### Platform Notes
[Algorithm changes, policy updates, audience behavior shifts observed this month]
```

---

### Section 4 — Seed Data: 15 Starter Entries

15 complete entries using the full schema. Based on known top-performing hook patterns in health direct response advertising. Realistic benchmark metrics — not invented numbers. These represent the known best-practice starting state.

Write each entry as:
```
---
Hook ID: [ID]
Hook Type: [Type from taxonomy]
NLP Layer: [Layer from taxonomy]
Hook Text: "[Exact text]"
Format: [Format]
Platform: [Platform]
Expert Niche: [Niche]
Awareness Level: [Level]
Traffic Temp: [Temp]
Launch Date: 2026-01
Impressions: [Realistic seed number]
Thumb Stop Rate: [Realistic %]
Hook Hold Rate: [Realistic % or null]
CTR: [Realistic %]
CPL: $[Realistic amount]
ROAS: null
Status: Active
Season Notes: null
Performance Notes: [Genuine observation]
Updated: 2026-04-07
---
```

The 15 seed entries:

1. Hook: "The reason your thyroid medication isn't working has nothing to do with your thyroid."
   Type: Mechanism-Reveal | NLP: Paradigm-Shift | Format: Video-Hook | Platform: FB-Feed | Niche: HORMONES | Level: L3-Solution-Aware | Temp: Cold
   Realistic metrics: Thumb Stop ~48%, Hook Hold ~62%, CTR ~3.1%, CPL ~$11

2. Hook: "I did this one thing for 30 days. My doctor couldn't explain what happened to my labs."
   Type: Transformation-Proof | NLP: Curiosity-Gap | Format: Video-Hook | Platform: IG-Reel | Niche: FUNCTIONAL-MED | Level: L2-Problem-Aware | Temp: Cold
   Realistic metrics: Thumb Stop ~55%, Hook Hold ~67%, CTR ~3.8%, CPL ~$9

3. Hook: "Doctors told me my gut was fine. They were looking at the wrong thing."
   Type: Authority-Reversal | NLP: Presupposition | Format: Video-Hook | Platform: FB-Feed | Niche: GUT | Level: L3-Solution-Aware | Temp: Cold
   Realistic metrics: Thumb Stop ~44%, Hook Hold ~58%, CTR ~2.7%, CPL ~$13

4. Hook: "If you have any of these 5 symptoms, your cortisol pattern may be the missing piece."
   Type: Pattern-Interrupt-Symptom | NLP: Embedded-Command | Format: Image-Text | Platform: IG-Feed | Niche: HORMONES | Level: L2-Problem-Aware | Temp: Cold
   Realistic metrics: Thumb Stop ~41%, CTR ~2.3%, CPL ~$15

5. Hook: "What I wish I knew before spending 3 years and $12,000 trying to fix my thyroid."
   Type: Empathy-Mirror | NLP: Pacing-And-Leading | Format: Video-Hook | Platform: FB-Feed | Niche: HORMONES | Level: L2-Problem-Aware | Temp: Cold
   Realistic metrics: Thumb Stop ~46%, Hook Hold ~60%, CTR ~2.9%, CPL ~$12

6. Hook: "Nobody talks about this gut-hormone connection. And it's why nothing has worked."
   Type: Insider-Knowledge | NLP: Curiosity-Gap | Format: Video-Hook | Platform: TikTok | Niche: GUT | Level: L3-Solution-Aware | Temp: Cold
   Realistic metrics: Thumb Stop ~52%, Hook Hold ~64%, CTR ~3.4%, CPL ~$10

7. Hook: "847 patients. Same root cause. Most had been to 3 or more doctors before finding it."
   Type: Social-Proof-Mechanism | NLP: Specificity | Format: Image-Text | Platform: FB-Feed | Niche: FUNCTIONAL-MED | Level: L3-Solution-Aware | Temp: Cold
   Realistic metrics: Thumb Stop ~38%, CTR ~2.1%, CPL ~$17

8. Hook: "Your doctor may not know about this thyroid conversion problem. Most don't test for it."
   Type: Authority-Gap | NLP: Presupposition | Format: Video-Hook | Platform: IG-Feed | Niche: HORMONES | Level: L2-Problem-Aware | Temp: Cold
   Realistic metrics: Thumb Stop ~43%, Hook Hold ~55%, CTR ~2.5%, CPL ~$14

9. Hook: "FREE: Discover your gut health pattern in 60 seconds"
   Type: Lead-Magnet-Direct | NLP: Embedded-Command | Format: Image-Text | Platform: FB-Feed | Niche: GUT | Level: L1-Unaware | Temp: Cold
   Realistic metrics: Thumb Stop ~36%, CTR ~3.6%, CPL ~$8 (quiz lead magnet — lower CPL due to quiz format)

10. Hook: "Why everything you've been told about autoimmune disease is exactly backwards."
    Type: Paradigm-Shift | NLP: Curiosity-Gap | Format: Video-Hook | Platform: IG-Reel | Niche: AUTOIMMUNE | Level: L3-Solution-Aware | Temp: Cold
    Realistic metrics: Thumb Stop ~50%, Hook Hold ~63%, CTR ~3.2%, CPL ~$11

11. Hook: "Sarah came to me exhausted, 40 lbs overweight, and told there was nothing wrong. Here's what we actually found."
    Type: Story-Hook-Patient | NLP: Empathy-Mirror | Format: Video-Hook | Platform: FB-Feed | Niche: HORMONES | Level: L2-Problem-Aware | Temp: Cold
    Realistic metrics: Thumb Stop ~49%, Hook Hold ~65%, CTR ~3.0%, CPL ~$12

12. Hook: "Stop taking that supplement until you watch this."
    Type: Pattern-Interrupt-Urgent | NLP: Embedded-Command | Format: Video-Hook | Platform: TikTok | Niche: FUNCTIONAL-MED | Level: L3-Solution-Aware | Temp: Cold
    Realistic metrics: Thumb Stop ~58%, Hook Hold ~70%, CTR ~4.1%, CPL ~$9

13. Hook: "The cortisol-thyroid connection nobody's talking about — and why it explains everything."
    Type: Mechanism-Curiosity | NLP: Curiosity-Gap | Format: Image-Text | Platform: IG-Feed | Niche: HORMONES | Level: L3-Solution-Aware | Temp: Cold
    Realistic metrics: Thumb Stop ~39%, CTR ~2.2%, CPL ~$16

14. Hook: "I've helped 2,300 patients reverse autoimmune flares. The pattern is always the same."
    Type: Authority-Proof | NLP: Specificity | Format: Video-Hook | Platform: YouTube-Pre-Roll | Niche: AUTOIMMUNE | Level: L2-Problem-Aware | Temp: Cold
    Realistic metrics: Thumb Stop ~42%, Hook Hold ~54%, CTR ~2.4%, CPL ~$18

15. Hook: "Waking up at 3am every night? Your cortisol rhythm is backwards — and here's why."
    Type: Pattern-Interrupt-Symptom | NLP: Pacing-And-Leading | Format: Video-Hook | Platform: FB-Feed | Niche: HORMONES | Level: L2-Problem-Aware | Temp: Cold
    Realistic metrics: Thumb Stop ~47%, Hook Hold ~61%, CTR ~2.8%, CPL ~$13

---

### Section 5 — Update Instructions for the Ad Performance Analyst

Complete operational instructions for the monthly update cycle. Written as a direct operational guide.

**Step 1 — Data pull from Meta Ads Manager:**
Pull previous month's data for all active health ads.
Metrics to pull per ad: impressions, 3-second video views, link clicks, landing page views, leads, amount spent.
Calculations:
- Thumb Stop Rate = (3-second video views ÷ impressions) × 100
- Hook Hold Rate = (ThruPlay at 3 seconds ÷ impressions) × 100 — requires "Video Plays at 3 Seconds" metric in Meta reporting, not the general video view metric which counts at 2 seconds
- CTR = (link clicks ÷ impressions) × 100
- CPL = amount spent ÷ leads

**Step 2 — Hook identification:**
For each ad in the data pull, identify the Hook ID from the hook text. If the hook was not previously entered (new hook), create a new entry with all fields populated.

**Step 3 — Update existing entries:**
For each existing entry with new month data: update performance metrics using rolling 90-day average (not single-month data) to smooth out statistical noise. Rolling average formula: ((prior average × prior impressions) + (new month performance × new month impressions)) ÷ total impressions.

**Step 4 — Identify declining patterns:**
Scan all Active entries. Any hook type/niche combination where CPL has increased more than 20% month-over-month for 2 consecutive months: add to Declining Patterns section of monthly summary.

**Step 5 — Identify test opportunities:**
Review the decision matrix in `copy_frameworks/direct_response_frameworks.md`. Identify any framework/niche/platform combinations with under 500 impressions or not tested in the past 90 days. Add to New Patterns to Test section.

**Step 6 — Write the monthly summary block:**
Append the complete monthly summary block (schema from Section 3) to the end of the file.

**Step 7 — Flag for Learning Loop Agent:**
After monthly update, the Ad Performance Analyst creates a brief summary of key findings (top performers, declining patterns, test opportunities) and passes to the Learning Loop Agent for integration into platform optimization recommendations.

**Retirement thresholds:**
- Retired: CPL exceeds 2× platform benchmark for 3 consecutive months AND no seasonal or contextual explanation exists
- Seasonal: performance strongly correlated with a specific time of year or external event (New Year health resolutions, back-to-school, post-holiday detox, etc.)
- Paused: temporarily suspended for testing or policy review — not permanently retired

**The "Never Retire, Only Demote" principle in data management:**
Even when a hook is marked Retired, the entry remains in the file. The Status field changes but the data is preserved. Retired hooks are reviewed quarterly — some are seasonal (revive in the right period), some respond to new market conditions, some become relevant again after creative fatigue in competing hooks. The file is institutional memory. Nothing is deleted.

---

*clinicIQ Knowledge Base — Hooks Layer*
*brief_08_hook_performance_data.md — Version 1.0*
*April 2026*
