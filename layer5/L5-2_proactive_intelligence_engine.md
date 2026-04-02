# ClinicIQ — Layer 5: The IQ Intelligence Platform
# L5-2: Proactive Intelligence Engine
**Version 1.0**
*Layer 5, Spec 2 of 5 | Depends on: L5-1 (Living Expert Profile), Layer 4 (Analytics & Intelligence)*

---

## Purpose

Every tool that exists today is reactive. It waits for you to log in. It waits for you to ask. It waits for you to notice a problem. You come to it.

The Proactive Intelligence Engine inverts this entirely.

**IQ comes to you.**

Before you open the platform, IQ has already analyzed your overnight performance data, scanned your competitive landscape, checked your content calendar against your conversion patterns, and identified the three things that matter most to your business today. It surfaces that intelligence in a Morning Brief — and it keeps surfacing relevant signals throughout the day, automatically, without you asking for any of it.

This is the spec for how that works. What gets monitored, how signals are detected, how they get prioritized, how they're delivered, and what happens when the expert acts on them.

The north star: **by the time the expert opens ClinicIQ each morning, IQ already knows what they should do today — and has already started doing it.**

---

## The Core Architecture: Signal → Intelligence → Action

The Proactive Intelligence Engine operates as a continuous pipeline:

```
SIGNAL SOURCES          INTELLIGENCE LAYER          DELIVERY & ACTION
─────────────────       ──────────────────          ─────────────────
Performance Data    →   Pattern Detection       →   Morning Brief
Competitor Feeds    →   Significance Scoring    →   IQ Claw Alert
Market Trends       →   Context Enrichment      →   In-App Notification
Calendar Events     →   Recommendation Build    →   Pre-Built Asset
Expert Behavior     →   Priority Ranking        →   One-Tap Approval
LEP Updates         →   Delivery Formatting     →   Auto-Execution
```

Every signal that enters the pipeline gets scored for significance, enriched with LEP context, converted into an actionable recommendation, and delivered in the most appropriate format for that type of insight. Nothing surfaces without being actionable. IQ never just tells you something is wrong — it tells you what to do about it, and usually has the fix ready.

---

## The Six Signal Categories

### Signal Category 1 — Performance Anomaly Detection
*Source: Layer 4 Analytics | Monitoring cadence: Continuous (hourly for paid, daily for organic)*

This is the early warning system. IQ watches every connected metric and detects when something moves meaningfully — up or down — outside of normal variance for this specific expert.

**What "meaningful" means:** Not every change triggers an alert. The engine applies statistical significance thresholds calibrated to the expert's own historical patterns (from the LEP Audience Response Profile). A 5% drop in email open rate might be noise for one expert and a crisis for another, depending on their baseline variance. IQ knows the difference.

**Performance anomaly types and trigger thresholds:**

| Metric | Alert Trigger | Priority Level |
|--------|--------------|----------------|
| Ad ROAS | Drops >20% vs. 7-day average | 🔴 Critical |
| Ad CPL | Increases >25% vs. 7-day average | 🔴 Critical |
| Funnel opt-in rate | Drops >15% vs. 30-day average | 🔴 Critical |
| Email open rate | Drops >10% vs. 30-day average | 🟡 Warning |
| Email click rate | Drops >20% vs. 30-day average | 🟡 Warning |
| Social reach | Drops >30% vs. 14-day average | 🟡 Warning |
| Podcast downloads | Drops >25% vs. 4-episode average | 🟡 Warning |
| Ad ROAS | Increases >30% vs. 7-day average | 🟢 Opportunity |
| Email open rate | Increases >15% vs. 30-day average | 🟢 Opportunity |
| Content engagement | Increases >50% vs. 14-day average | 🟢 Opportunity |
| Social post virality | Reaches 3x normal engagement within 4 hrs | 🟢 Opportunity |

**What IQ does with each alert type:**

🔴 **Critical:** IQ builds the diagnosis and a fix. The Morning Brief leads with it. If an automated fix is available (e.g., pause underperforming ad set, rotate in backup creative), IQ proposes it with a one-tap approval. Expert is notified immediately via in-app and optionally via email.

🟡 **Warning:** IQ includes in Morning Brief with diagnosis and recommendation. Not urgent enough for immediate notification unless it persists >48 hours.

🟢 **Opportunity:** IQ identifies the pattern behind the win and proposes scaling it. *"Your Thursday email subject lines are outperforming Monday by 34%. Want me to shift your next 3 broadcasts to Thursday?"* Pre-built action ready.

---

### Signal Category 2 — Competitive Intelligence Triggers
*Source: Competitor content monitoring, SEO monitoring | Monitoring cadence: Daily*

IQ monitors the expert's top 5 competitors (identified and ranked during onboarding + updated by the LEP) and surfaces signals when competitors do something that creates a threat or an opportunity.

**What gets monitored:**

| Signal | What IQ Detects |
|--------|----------------|
| Competitor content velocity change | Competitor starts publishing significantly more (or less) |
| High-performing competitor content | A competitor post/video/episode is gaining unusual traction |
| New competitor offer or price change | Competitor launches a new program, changes pricing, or runs a promotion |
| Competitor keyword ranking shift | Competitor gains or loses significant search ranking in shared keywords |
| Competitor ad activity | New competitor ad creative detected in niche (via public ad library monitoring) |
| Competitor negative sentiment | Complaints, negative reviews, or controversy emerging around a competitor |

**What IQ does with each:**

- **High-performing competitor content:** IQ drafts a response angle in the expert's voice. *"Dr. Mark Hyman just published a thyroid video that's at 380K views in 3 days. Your audience overlaps 60%. I've drafted a response piece from your root cause angle — want to review it?"* Draft ready in the right panel.

- **New competitor offer:** IQ flags it, compares it against the expert's current offer stack, and surfaces a differentiation brief: *"Competitor X just launched a $197 gut health program. Here's how your offer is differentiated — and one thing worth strengthening."*

- **Competitor negative sentiment:** IQ identifies the criticism and drafts a piece of content that positions the expert as the better alternative — tactfully, without naming the competitor. *"There's growing frustration in your niche about [topic]. Here's a content angle that addresses it from your perspective."*

- **Competitor ad creative:** IQ adds it to the expert's competitive ad swipe file and notes if it's using similar hooks to the expert's current ads. If hook overlap is high: *"A competitor is running a similar hook to your current VSL. Want me to draft fresh hook options to maintain differentiation?"*

---

### Signal Category 3 — Market Trend Triggers
*Source: Search trend APIs, social trend monitoring, health news feeds | Monitoring cadence: Daily*

IQ watches what's rising in the expert's niche before it peaks — giving them first-mover advantage on trending content, before competitors pile in.

**What gets monitored:**

| Signal Type | Source | Trigger |
|-------------|--------|---------|
| Rising search queries | Search trend API | Query volume up >40% week-over-week in niche keywords |
| Trending social topics | Social monitoring | Topic gaining engagement velocity across health creator accounts |
| News cycle relevance | Health news feeds | Mainstream media story directly relevant to expert's mechanism |
| Research publication | PubMed / research feeds | New study validating or challenging the expert's core mechanism |
| Cultural moment | General trend monitoring | Broad cultural event relevant to health/wellness (new year, seasonal) |
| Viral health claim | Social monitoring | Health claim going viral that the expert can address from authority |

**What IQ does with each:**

- **Rising search query:** *"'Histamine intolerance' search volume is up 67% this week. This is directly in your lane. I've drafted a YouTube script and a 3-part email series while this is still early — want to review?"*

- **Mainstream news story:** *"The New York Times just published a piece on long COVID fatigue that aligns with your mitochondrial protocol. I've drafted a 'here's what the research actually means' piece in your voice — this could be your highest-reach content this month."*

- **New research publication:** IQ pulls the abstract, cross-references it against the expert's clinical philosophy, and drafts a content piece that translates it for their audience — with appropriate compliance framing built in.

- **Viral health claim:** *"A claim about [topic] is going viral with 2M+ views. Some of it is accurate, some isn't. Here's a response piece from your authority position — builds trust and captures the traffic spike."*

**The early mover advantage:** IQ surfaces rising trends at +40% week-over-week. By the time something is trending (200%+ WoW), it's crowded. Being first — with content in the expert's authentic voice, ready to publish in one tap — is a significant competitive advantage.

---

### Signal Category 4 — Calendar & Seasonal Intelligence
*Source: LEP Seasonal Pattern Map, Monthly Master Plan, historical performance data | Monitoring cadence: Weekly look-ahead + daily check*

IQ knows what time of year it is and what that means for this specific expert's business — not generic seasonal advice, but patterns derived from the expert's own historical performance data and cross-platform niche benchmarks.

**What gets monitored:**

| Trigger | Look-Ahead Window | What IQ Does |
|---------|------------------|--------------|
| Upcoming seasonal peak (e.g., New Year, Spring detox, post-holiday) | 6 weeks out | Drafts and queues the full seasonal campaign — content, emails, ads, offers |
| High-performing campaign anniversary | 4 weeks out | *"This campaign performed +34% last year. Should I rebuild it for this year?"* |
| Content calendar gap | 2 weeks out | Identifies days with no content planned, proposes fills |
| Offer launch timing | Per Monthly Master Plan schedule | Pre-build reminder + asset queue |
| Webinar or live event anniversary | 8 weeks out | *"Your last live webinar was 90 days ago. Audience engagement drops after 60 days without a live event. Want to schedule one?"* |
| Subscription renewal cycle | 30 days before patient cohort renewal | Retention sequence drafted and queued |

**The seasonal campaign pre-build:**

When a seasonal peak is 6 weeks out, IQ doesn't just remind the expert. It builds the campaign:
- Full content calendar for the campaign window
- Email sequence (typically 7–10 emails)
- Ad creative batch (5–8 variations)
- Social content batch (14–21 posts)
- VSL or webinar updates if the offer is being relaunched

All of this is built in draft state, waiting for review. The expert doesn't have to start from scratch — they just review what IQ built and approve with edits.

*"Your Spring Detox season starts in 6 weeks. Based on last year's data, your best window is March 25 – April 15. I've built the complete campaign. Want to review it?"*

---

### Signal Category 5 — Expert Behavior Triggers
*Source: LEP Layer C — Behavioral Intelligence | Monitoring cadence: Continuous*

IQ watches how the expert uses the platform and surfaces suggestions based on what it observes — not judgment, just intelligence.

**What gets monitored:**

| Behavioral Signal | IQ Response |
|------------------|-------------|
| Expert hasn't logged in for >5 days | Warm re-engagement: *"While you were out, here's what I've been working on..."* — summary of what ran automatically + what's waiting for review |
| Expert has >5 unapproved deliverables | Batched review prompt: *"You have 7 things ready for your review. Want to do a quick 10-minute approval run?"* |
| Approval rate dropping (expert is editing more than usual) | Quality recalibration prompt: *"I've noticed you've been editing more of my recent content — I want to make sure I'm hitting your standard. Want to do a quick voice calibration session?"* |
| Expert keeps approving same builder, ignoring others | *"You're crushing content and emails — but your funnel hasn't been updated in 47 days. That's where the conversions happen. Want to tackle it this week?"* |
| Expert makes the same manual edit repeatedly | Pattern learned + proactive offer: *"I've noticed you always shorten my email subject lines. I'll start shorter. And I've re-drafted the last 3 pending subjects with that in mind."* |
| Expert hasn't added to Proof Bank in 90 days | *"Your proof bank is 90 days old. Fresh patient wins make everything convert better. Got a recent transformation you can share in 2 minutes?"* |
| Expert's IQ Score plateauing for 30+ days | Full plateau diagnosis delivered in Morning Brief with specific action plan |

These triggers are never nagging. They're genuinely useful observations delivered the way a smart business partner would deliver them — specific, actionable, based on real data.

---

### Signal Category 6 — Growth Milestone Triggers
*Source: Analytics + LEP Expert Evolution Tracking | Monitoring cadence: Daily*

IQ celebrates wins and uses them strategically.

| Milestone | IQ Response |
|-----------|-------------|
| Email list crosses a round number (1K, 5K, 10K) | Celebrates in Morning Brief + proposes what to do with the new audience size |
| Funnel reaches a conversion rate threshold | *"Your opt-in page just crossed 40% conversion. That's elite. Let's run a VSL split test to push revenue per visitor."* |
| First $10K / $100K month detected | Celebration + retrospective: *"Here's exactly what drove it — and how to repeat it."* |
| Podcast episode crosses 1K downloads | *"Episode 23 just crossed 1K downloads — your best ever. Here's what was different about it."* |
| Patient program completion rate crosses 80% | *"Your program completion rate just hit 80%. That's exceptional. Let's capture testimonials from this cohort while the transformation is fresh."* |
| IQ Score improvement of >10 points in 30 days | Full performance summary delivered |

---

## The Morning Brief: Primary Delivery Vehicle

The Morning Brief is the centerpiece of the Proactive Intelligence Engine. It is delivered every morning at the expert's preferred time (learned from LEP Layer C session timing patterns), via IQ Claw in the center panel.

### Morning Brief Architecture

Every Morning Brief is structured identically — so the expert knows exactly what to expect and can move through it efficiently.

```
─────────────────────────────────────────────────────
IQ MORNING BRIEF — [Expert First Name]
[Day], [Date] | IQ Score: [X] [▲/▼ X pts vs. yesterday]
─────────────────────────────────────────────────────

🔴 NEEDS YOUR ATTENTION (if any)
  [Critical alerts only — max 2. Pre-built fix attached.]

📊 OVERNIGHT PERFORMANCE
  [3 most significant metric movements vs. prior period]
  [One-line diagnosis for each]

🎯 TODAY'S RECOMMENDED ACTION
  [Single highest-priority action for today]
  [Why this, why today, what IQ has already built]
  [→ Review now] button

👀 WHAT IQ IS WATCHING
  [2–3 market/competitor signals worth knowing]
  [Each with a one-line "so what" for this expert]

📅 COMING UP
  [What's on the calendar in the next 7 days]
  [What IQ is pre-building for upcoming campaigns]

✅ WHAT HAPPENED WHILE YOU WERE AWAY
  [Summary of automations that ran overnight]
  [Approvals still waiting]

─────────────────────────────────────────────────────
```

### Morning Brief Design Principles

**One action, not a list.** The brief surfaces one primary recommended action for today. Not five things the expert should probably do. One. The clearest, highest-leverage thing. This respects the expert's time and decision-making energy.

**Everything actionable.** Every item in the Morning Brief has an action attached. Not "your open rate dropped" — but *"your open rate dropped 12%. The last 3 subject lines were all questions. Your audience prefers statements. I've rewritten the next 3 — [review now]."*

**Pre-built, not pre-advised.** Wherever possible, IQ doesn't just recommend — it builds first. By the time the Morning Brief is delivered, the recommended action already has a draft asset waiting in the Builder workspace. The expert clicks "review now" and the work is already done.

**Delivery timing is personalized.** LEP Layer C tracks when the expert is most receptive to strategic thinking. If they log in every day at 7am, the brief is ready at 7am. If they're an afternoon user, it holds. The timing adapts over time.

**Delivery channel matches the expert.** Primary delivery: IQ Claw chat (center panel). Optional secondary: email digest (brief version), mobile push notification (critical alerts only).

---

## The Proactive Alert: Secondary Delivery Vehicle

Not everything waits for the Morning Brief. Time-sensitive signals get a real-time alert — a notification in IQ Claw's notification center (the 🔔 icon in the navigation rail) and, for critical items, a pop-up message from IQ Claw in the chat panel.

**What triggers an immediate alert (not waiting for morning):**

| Trigger | Alert Text Example |
|---------|------------------|
| Ad account spending >150% of daily budget | *"Your Facebook ad account spent $847 today vs. a $550 target. Something's off. Want me to pause and diagnose?"* |
| Funnel completely down (0 opt-ins for >4 hrs during active period) | *"Your opt-in page has had zero conversions in 4 hours during peak traffic time. This is unusual. Want me to check the funnel?"* |
| Competitor launches a direct offer attack | *"A competitor just launched a promotion that directly targets your core offer. Here's what I recommend."* |
| Viral content opportunity (trending in first 2 hours) | *"[Topic] is going viral right now. You have a 4-hour window for maximum impact. I've drafted a response — want it?"* |
| Significant positive performance spike | *"Your email just hit a 58% open rate — almost double your average. I know why. Want me to replicate the pattern?"* |

---

## Intelligence Prioritization: How IQ Decides What to Surface

Not every signal is worth the expert's attention. The Proactive Intelligence Engine scores every signal before surfacing it, using a five-factor priority model:

### The Five Factors

**1. Revenue Impact** (weight: 40%)
How directly does this signal connect to revenue? Funnel conversion drops score highest. Content engagement scores lower. The engine is always asking: *what does this actually mean for money?*

**2. Time Sensitivity** (weight: 25%)
How quickly does the opportunity close or the problem compound? A viral content window has 4–6 hours. A seasonal campaign needs 6 weeks of lead time. Time-sensitive signals get boosted.

**3. Effort-to-Impact Ratio** (weight: 20%)
If IQ has already built the fix, the effective effort is near zero — so the recommendation gets boosted. If addressing the signal requires significant expert input, it's scored lower unless the impact is very high.

**4. Expert Receptivity** (weight: 10%)
Based on LEP Layer C — if this type of suggestion has historically been acted on by this expert, it scores higher. If they consistently ignore a certain category, frequency drops.

**5. IQ Score Impact** (weight: 5%)
Will acting on this signal move the IQ Score? Items that meaningfully improve the score get a small boost.

**The output:** Every signal gets a priority score 1–100. Score >80 = Morning Brief lead item or immediate alert. Score 60–79 = Morning Brief inclusion. Score 40–59 = available in IQ Claw if expert asks. Score <40 = logged but not surfaced.

---

## Avoiding Alert Fatigue: The IQ Noise Filter

The biggest failure mode for any proactive AI system is over-alerting — training the expert to ignore it because it surfaces too many things. IQ's noise filter prevents this.

**Hard limits:**
- Maximum 2 critical alerts per day (unless genuine emergency)
- Maximum 5 Morning Brief items total
- Maximum 1 proactive IQ Claw message per day outside the Morning Brief
- Suggestions the expert has dismissed >2 times are suppressed for 30 days, then re-evaluated

**The trust calibration loop:**
IQ tracks which suggestions get acted on and which get dismissed. Over time it learns this expert's signal-to-noise tolerance and adjusts the filter threshold accordingly. An expert who acts on 80% of suggestions gets more frequent signals. An expert who dismisses 60% gets fewer, higher-confidence signals only.

**The "quiet mode" override:**
The expert can tell IQ Claw "I'm heads down this week — only surface critical stuff." IQ activates quiet mode: Morning Brief only, no proactive alerts, only 🔴 critical items surface. Expert reactivates normal mode whenever they're ready.

---

## Integration with the Full Platform

The Proactive Intelligence Engine is not a standalone system — it reads from and writes to every other part of the platform.

**Reads from:**
- LEP (L5-1) — for context, calibration, and personalization of every signal
- Layer 4 Analytics — primary data source for performance anomaly detection
- External feeds — competitor monitoring, search trends, news feeds, research publications

**Writes to:**
- Layer 3 Builder agents — triggers pre-builds when a proactive recommendation includes a draft asset
- LEP Layer C — updates receptivity scores based on which suggestions are acted on
- IQ Score engine (L5-5) — certain ignored signals or missed opportunities affect the IQ Score trajectory
- Monthly Master Plan — seasonal and calendar triggers feed into the MMP update cycle

**The result:** The Proactive Intelligence Engine is the nervous system of ClinicIQ. It is always running, always watching, always connecting data to action — so the expert never has to be.

---

## What This Feels Like for the Expert

**Day 1:** Basic Morning Brief. Mostly performance summary + one recommended action. Sparse because there's no performance history yet.

**Week 2:** Patterns starting to emerge. First competitor signal surfaces. First content opportunity draft appears in the right panel.

**Month 1:** Morning Brief is genuinely useful every day. IQ has started pre-building content before the expert asks. Seasonal triggers are being prepared.

**Month 3:** The expert starts their day with the Morning Brief before they do anything else. It feels like having a strategic advisor who worked all night so they didn't have to.

**Month 12:** The expert cannot imagine running their business without it. Not because they're dependent — but because IQ's proactive intelligence is surfacing opportunities they would never have found on their own, at the speed that markets move. They are consistently 2–3 weeks ahead of their competitors.

---

## Summary

The Proactive Intelligence Engine is what turns ClinicIQ from a tool you use into a platform that works for you. It watches six categories of signals continuously, filters them through a five-factor priority model, delivers them in a structured Morning Brief every day, and wherever possible — has already built the solution before the expert even knows they need it.

The expert's job becomes approving and directing. IQ's job is everything else.

That is the iPhone shift: the technology disappears. The expert just runs their business — and wins.

---

*L5-2: Proactive Intelligence Engine — v1.0*
*Next: L5-3 — One-Tap Deployment*
