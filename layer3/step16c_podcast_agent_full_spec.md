# clinicIQ — Layer 3: Builder Agents — Step 16c: Podcast Agent (Full Specification)
**Version 1.0**
*Step 16 sub-section | Depends on: Steps 1–15 + Expert Dossier + Strategy Layer*
*Source docs: DrJoshAxe-RunsheetAgent.docx, DrJoshAxe-PodcastMarketingAgents.docx, DrJoshAxe-AgentPromptLibrary.docx*

---

## What the Podcast Agent Actually Is

The Podcast Agent is clinicIQ's full podcast operating system. It handles everything from show format design through episode production through marketing and growth — for any expert at any scale, from someone launching their first episode to a show doing 500K+ monthly plays.

It is not a clip tool or a show notes generator. It is the complete production and distribution machine that makes a health expert's podcast run at a professional level without a professional production team.

The architecture is built on the Dr. Josh Axe Show's 20-agent system — the most detailed podcast AI infrastructure spec in health media — abstracted into a platform that works for any expert, any scale, any show format.

---

## The Two Layers: Production + Marketing

Every podcast needs two things to succeed: great episodes and consistent distribution. Most health experts are decent at making content and terrible at the machine that gets it heard. The Podcast Agent runs both layers simultaneously.

```
LAYER 1 — PRODUCTION
    Show Format Design → Episode Planning → Runsheet → Recording → 
    Post-Production Assets (Show Notes, Slides, Transcript, SEO Article)

LAYER 2 — MARKETING & GROWTH
    Launch Execution → Clip Intelligence → Social Distribution → 
    Guest Amplification → Audience Growth → Analytics & Intelligence
```

Both layers run from a single trigger — the episode enters production — and every output feeds the next step automatically.

---

## Show Format Design — Before the First Episode

Before any episode is produced, the Podcast Agent runs a show format design session with the expert. This is the podcast equivalent of the Onboarding Dossier — it captures everything needed to run the show long-term.

### The Three Show Format Templates

The expert selects from three proven templates or customizes from scratch:

**Template 1 — The Authority Solo Show**
Expert speaks alone. Deep dives on mechanism, protocols, case studies, myth-busting. Best for experts who want to establish category authority. Every episode is a complete teaching.
- Structure: Hook → Why This Matters → Why Everything Else Fails → Root Cause / Mechanism → The Protocol → Action Step → CTA
- Ideal for: Functional medicine, hormone health, gut health, detox, longevity
- Model: Dr. Josh Axe solo episodes, Dr. Rhonda Patrick

**Template 2 — The Expert Interview Show**
Host interviews other practitioners, researchers, patient story guests. Best for experts who want to build authority through association and drive distribution through guest audiences.
- Structure: Guest intro → Guest origin story → Core conversation (7-question arc) → Mechanism moment (host steers to root cause framework) → Listener takeaway → CTA
- Ideal for: Experts with strong network, partnership growth focus, newer shows building credibility
- Model: Dr. Mark Hyman, Huberman Lab

**Template 3 — The Hybrid Show**
Mix of solo authority episodes and guest interviews, plus patient/client transformation story episodes. The highest-converting format for health experts because it combines authority (solo), social proof (patient stories), and distribution (guests).
- Episode mix default: 50% solo, 30% guest, 20% patient/transformation story
- Ideal for: Most health experts — this is the recommended default
- Model: Dr. Josh Axe show (full format)

### Show Format Customization

For any template, the expert customizes:
- Show name and positioning line
- Episode length target (20 min / 45 min / 60+ min)
- Release cadence (weekly / twice-weekly / biweekly)
- Segment names (the agent proposes; expert approves or renames)
- Signature CTA (what the expert wants every episode to drive — lead magnet, webinar, apply link)
- Signature review ask language
- Intro/outro style (scripted or conversational)
- Music and production style direction

The Show Format Document is stored in the expert's IQ Drive and used by every production agent for every episode.

---

## The Scale System — Universal Access, Scale-Activated Depth

Every expert gets access to every agent. What changes with scale is depth of operation, not availability.

The system reads the expert's podcast metrics and activates deeper functionality as thresholds are reached. A new podcaster doesn't get a watered-down version — they get the full system running at starter intensity. As their show grows, the agents go deeper automatically.

| Metric | Starter | Growing | Scaling | Elite |
|--------|---------|---------|---------|-------|
| Monthly plays | 0–10K | 10K–100K | 100K–500K | 500K+ |
| Clip volume | 3/episode | 5/episode | 8/episode | 10+/episode |
| Back-catalog revival | Top 5 episodes | Monthly 6-episode batch | Weekly | Continuous |
| Paid promotion | Guidance only | $1–5K/month managed | $5–15K/month | $15–30K+/month |
| Competitor intelligence | Basic (3 comps) | Standard (6 comps) | Full (9 comps) | Full + custom |
| Guest amplification | Standard tier only | Standard + Major tier | All tiers | All tiers + Whale outreach |
| Cross-promotion outreach | 10 active convos | 25 active | 50 active | 100+ active |
| Analytics reporting | Weekly summary | Weekly + Monthly | Weekly + Monthly + Quarterly | Full OKR reporting |

The expert never configures this. The system detects scale from connected analytics and adjusts automatically. When a threshold is crossed, IQ Claw notifies: *"Your show hit 10K monthly plays — I've activated monthly back-catalog revival and expanded your clip volume to 5 per episode."*

---

## The Full Agent System — 20 Agents in 6 Categories

---

### CATEGORY 1 — SHOW PRODUCTION (4 agents)

These run before and during every episode recording. Their outputs are the pre-production package the expert uses to record a world-class episode.

---

**Agent P1 — Episode Runsheet Agent** *(Priority: P1)*

The most important production agent. Runs before every recording. Produces the complete pre-production package the expert uses to record — not an outline, a precision-engineered episode blueprint.

*What it produces:*
- **Pre-Show Strategy Brief** — audience psychology for this episode, search and growth angle, proof stack pre-matched to claims
- **5 Cold Open Options** — each a different psychological hook type (surprising stat, story-in-action, provocative question, contrarian claim, mechanism reveal). No slow intros, no generic welcomes.
- **Full Segment Map** — every segment with: title, duration target, core promise to listener, 3–5 key talking points, the ONE thing to remember, pattern interrupt moment, and bridge line to next segment
- **Guest Question Set** — for interview episodes: 16 questions specific to this guest (not generic podcast questions), pre-researched controversy moments, guest's most-shared clips from other appearances
- **5+ Pre-Flagged Clip Moments** — identified before recording, with hook rationale and platform recommendation per clip
- **CTA Architecture** — separate CTA scripts for audio podcast, YouTube video, and email/social. Review ask customized to this episode's topic.
- **Post-Production Notes** — editor guidance on retention engineering, where to use pattern interrupts, chapter marker placement

*Segment structure (adapts to show format template):*
```
SEGMENT 1 — THE PROBLEM (8–12 min)
SEGMENT 2 — WHY CONVENTIONAL APPROACHES FAIL (6–8 min)
SEGMENT 3 — ROOT CAUSE / MECHANISM (10–14 min)
SEGMENT 4 — THE PROTOCOL (12–16 min)
SEGMENT 5 — GUEST DEEP DIVE (12–18 min, if applicable)
SEGMENT 6 — RAPID FIRE / TOP QUESTIONS (6–8 min)
OUTRO — CTA + PREVIEW (2–3 min)
```

*Non-negotiables enforced in every runsheet:*
- Strong first 30 seconds and first 90 seconds
- Pattern interrupt every 5–8 minutes
- Promise → proof → payoff → bridge rule on every segment
- Minimum 3 clip moments (target: 5+)
- At least 1 contrarian or surprising insight
- At least 1 concrete action step the listener can implement today
- At least 1 strong research or stat moment
- At least 1 real story or patient case study
- Full narrative arc: problem → hope → solution → action

*Inputs:* Episode topic/guest, audience intelligence brief (from Agent P4), show format template, expert dossier (voice, mechanism, avatar)
*Tools:* Claude API, Airtable, Google Trends API

---

**Agent P2 — Show Notes & Research Agent** *(Priority: P1)*

Runs after recording. Generates research-backed, narrative-rich show notes — not a transcript summary. A standalone piece of content that delivers value, drives SEO, and converts readers into listeners.

*What it produces:*
- Hook headline (most surprising claim from the episode)
- Episode overview (150–200 words — why this episode matters *right now*)
- Pattern interrupt stat ("Did you know: [jaw-dropping number]?")
- The Science section (400–600 words — mechanistic explanation, 2 peer-reviewed studies, one analogy, "most doctors miss this because..." bridge)
- Real stories / case studies (1–2 patient or personal transformation stories)
- Key takeaways (5–7 numbered, shareable, actionable)
- Dr. [Expert]'s Action Protocol (structured: Morning / With Meals / Before Bed / Weekly)
- Surprising statistics (4–6 bullets with context)
- Listener questions this episode answers (3–5 written as someone would type them into Google)
- Resources mentioned
- Internal links (3 related episodes from catalog)
- Related products/programs from the expert's offer stack

*Research rules:* Verify all studies. Never fabricate statistics. Flag unverified claims for expert review.

*Inputs:* Episode transcript (AssemblyAI), episode metadata, producer notes, PubMed feed (top studies on episode topic)
*Tools:* Claude API, AssemblyAI, PubMed API, Google Scholar, Airtable

---

**Agent P3 — Episode Slide Deck Agent** *(Priority: P2)*

Produces the visual slide system for video recording — designed for YouTube chapter thumbnails, screenshot-worthy social sharing, and clip-friendly moments on screen.

*What it produces (12–18 slides per episode):*
- Title slide (episode title ≤5 words, guest name, one-line hook)
- Shocking stat slides (3–5) — big number + one-sentence context + source
- Mechanism diagram slides (1–2) — visual description of the biological process
- Protocol / checklist slides — numbered list (≤5 items), action verbs only
- Myth vs. Truth slides (1–2) — two columns: "What most doctors say" vs. "What the research shows"
- Quote pullout slides (2–3) — most tweetable, most surprising lines from transcript
- Chapter marker slides — segment title + minute mark for YouTube chapters

*Each slide includes:* exact on-screen text, visual direction note for designer, social crop guidance (1:1 and 9:16)

*Inputs:* Episode transcript, key stats, segment map from Runsheet Agent
*Tools:* Claude API, Airtable; renders to HTML/CSS via Puppeteer (same system as rest of clinicIQ)

---

**Agent P4 — Audience Intelligence Agent** *(Priority: P2 → auto-elevates at Growing scale)*

The feed that makes everything else smarter. Runs continuously, delivers a weekly Monday brief to the expert's dashboard so every content decision is data-driven, not gut-feel.

*What it monitors:*
- YouTube comments on last 10 episodes (recurring questions, emotional responses, topic requests)
- Reddit communities in the expert's specialty (r/functionalmedicine, r/guthealth, r/hormones, r/longevity, etc.) — trending questions, the language the audience uses
- Spotify and Apple reviews — what listeners love, what they wish was covered
- Google Trends for the expert's top topic clusters — search spikes before they peak
- Quora and health forums — underserved questions no major health podcast has addressed
- Competitor episode performance — which episodes from competing shows are outperforming

*Weekly Monday morning output:*
- Top 5 questions your audience asked this week
- 3 trending topics in your space with supporting search data
- 2 underserved questions no major health podcast has answered well
- 1 suggested solo episode title (highest-signal finding, written in title formula format)
- 1 suggested guest booking based on audience questions and gap analysis

*Inputs:* YouTube Data API, Reddit API, Google Trends API, Brand24, Spotify API, competitor episode data
*Tools:* Claude API, multiple data source APIs, Airtable

---

### CATEGORY 2 — SEO & DISTRIBUTION ASSETS (2 agents)

These run after every episode and build the compounding catalog.

---

**Agent S1 — SEO + GEO Episode Article Agent** *(Priority: P1)*

Generates a fully optimized episode webpage for every episode — building a searchable health media library without the expert writing a word. Optimized for both Google ranking AND AI answer engines (ChatGPT, Perplexity, Gemini, Google AI Overviews).

*What it produces (700–950 words):*
- H1 with primary keyword phrase + benefit hook
- Meta description (155 chars, keyword + benefit + curiosity gap)
- Introduction (80–100 words — leads with startling stat, identifies pain, states what article delivers)
- The Science section (200–250 words — mechanistic explanation + 2 research citations + analogy)
- Why Conventional Approaches Miss section (100–150 words — positions expert's differentiation)
- The [Expert] Protocol section (200–250 words — numbered, action verb, specific instruction, rationale)
- FAQ block (150–200 words, 3–4 questions written as Google autocomplete language)
- Key Takeaways (50–80 words, bullet-pointed citable facts)
- Closing CTA (listen on Apple/Spotify/YouTube)
- 3–4 internal links to related episodes
- Schema flags (FAQ, HowTo, Article)
- Related products/programs section (direct monetization layer)

*GEO principle:* FAQ schema is the #1 format AI answer engines pull from. Structured protocols are frequently cited. Bullet-pointed factual summaries are cited verbatim. Write for both Google and AI.

*The compounding math:* At 4 episodes/month, 48 new SEO pages per year. At year 3, ~150 optimized health pages. Each ranking for one moderate-traffic query = 75K+ additional monthly organic visitors.

*Inputs:* Episode transcript, primary keyword, topic cluster, Ahrefs keyword data, related episodes list
*Tools:* Claude API, Ahrefs API, Google Search Console API, Airtable

---

**Agent S2 — Back-Catalog Revival Agent** *(Priority: P2 → activates at Growing scale, continuous at Elite)*

Audits the expert's full episode catalog monthly, identifies revival candidates, rewrites their packaging for current SEO, and produces a ready-to-deploy re-promotion calendar.

*How it works:* Runs on the 1st of every month. Ingests full episode list with performance data. Cross-references expert's top topic clusters and current Google Trends signals. Identifies episodes covering high-demand topics with underperforming packaging.

*Per revival episode it produces:*
- Rewritten title (formula bank applied, current keyword structure)
- Rewritten description (modern keyword structure, updated language)
- "Worth revisiting" email draft
- Social post (timely recommendation framing)
- Clip brief (strongest moment for re-edited short)

*Monthly output:* Prioritized list of 6 revival episodes with all assets ready for one-click review.

*Also builds:* A "Start Here" playlist for new listeners — 10 best evergreen episodes organized by health topic, formatted as a pinned YouTube playlist and landing page.

*The compounding math:* 50 back-catalog episodes restored to meaningful traffic at 2K additional plays each = 100K additional monthly plays from content already created.

*Inputs:* Full episode catalog with performance data, Google Trends, Ahrefs keyword data, topic cluster map
*Tools:* Claude API, YouTube Analytics API, Ahrefs API, Google Trends API, Airtable

---

### CATEGORY 3 — LAUNCH & DISTRIBUTION (3 agents)

These run on every episode launch day. The first 24–48 hours are disproportionately important for Apple chart ranking. These three agents engineer that spike precisely.

---

**Agent L1 — Episode Launch Orchestration Agent** *(Priority: P1)*

Fully automates launch-day execution so every episode launches with perfect timing across every channel — simultaneously, without human error.

*Trigger:* Episode published in RSS feed.

*Launch timeline it executes:*
```
HOUR 0:   Launch email sent, IG story posted, YouTube community post live,
          Apple/Spotify links confirmed, guest promo kit delivered
HOUR 2:   X/Twitter post, LinkedIn post, first short clip published
HOUR 6:   Reel posted, TikTok posted
HOUR 12:  IG reminder story, guest reminder triggered if no repost detected
HOUR 24:  Second clip posted, performance check logged,
          underperformance flag triggered if applicable
```

*What it generates per launch:*
- Launch email (sent within 30 minutes of release — Josh's/expert's voice, single CTA)
- YouTube community update
- Platform-specific social captions (Instagram, X, LinkedIn, TikTok) with correct links
- Guest promotional kit (their specific clip, 3 caption options per platform, personalized note)
- IG story sequence (launch + 12-hour reminder)
- All actions logged with timestamps; anything requiring human review flagged

*Time saved:* 3–5 hours of manual launch work → 15 minutes of human review.

*Inputs:* Episode metadata, transcript, guest info, social account connections, email platform API
*Tools:* n8n orchestration, Claude API, Buffer/Later API, Klaviyo/ESP API, YouTube API, Monday.com API

---

**Agent L2 — Clip Intelligence Agent** *(Priority: P1)*

Identifies the highest-potential clip moments in every episode before the editing team touches it. Editors cut from a prioritized list — not from watching full episodes.

*Scoring model — 5 dimensions:*
1. Emotional intensity — does this provoke a strong reaction?
2. Shareability — would someone send this to a friend?
3. Standalone comprehensibility — does it make sense out of context?
4. Alignment with the expert's top viral topic areas
5. Hook strength — does the first sentence demand attention?

*Clip types it identifies:*
- Authority clips: "3 Signs Your [Problem] Won't Heal"
- Myth-busting clips: "Why Most Doctors Miss This About [Topic]"
- Protocol clips: "The Morning Routine That Fixes [Condition]"
- Curiosity clips: "The One Lab Test Your Doctor Never Runs"
- Story clips: patient transformation moments or personal expert stories

*Output per clip:* exact timestamps, suggested clip title per platform, hook sentence for caption, recommended CTA, all platform-specific copy variants (IG caption, TikTok caption, YouTube Shorts title, X post)

*Clip volume targets by scale:*
- Starter: 3 clips/episode
- Growing: 5 clips/episode
- Scaling: 8 clips/episode
- Elite: 10+ clips/episode

*Compounding benefit:* Agent is fed performance data over time and learns which clip types and angles drive the most podcast follows for this specific expert. Within 6 months it's a proprietary content intelligence model trained on their audience.

*Inputs:* Episode transcript (with timestamps), performance data from prior clips, expert's viral topic list
*Tools:* Claude API, AssemblyAI, Airtable

---

**Agent L3 — Content Repurposing Agent** *(Priority: P2)*

Turns every episode into 15+ social assets distributed across 30 days. One recording session → a month of content.

*What it produces per episode:*
- 5–8 social image posts with captions (routed to Content Builder for visual production)
- 3–5 carousel concepts (slide-by-slide spec, routed to Content Builder)
- 3–5 short-form video clip specs (timestamps + text overlay + caption per platform)
- 1–2 LinkedIn long-form article adaptations
- 1 email newsletter adaptation (standalone value piece from episode content)
- YouTube description optimized for search + chapter markers
- YouTube Shorts titles and descriptions for all clip specs

*30-day distribution calendar:* Maps all assets to a post schedule so the episode drives traffic for a full month, not just 48 hours.

*Inputs:* Episode transcript, Clip Intelligence Agent output, show notes, episode article
*Tools:* Claude API, Airtable, Buffer API; visual assets routed to Content Builder

---

### CATEGORY 4 — TITLE, PACKAGING & OPTIMIZATION (2 agents)

---

**Agent O1 — Title & Packaging Optimization Agent** *(Priority: P1)*

Continuously tests and improves episode titles and thumbnails using real performance data. Catches underperforming episodes fast and triggers intervention.

*Pre-launch mode:*
Generates 5 title variants for every new episode using the formula bank. Scores each on: outcome-first language, keyword strength, emotional trigger, search intent alignment. Presents top 3 to producer with recommended winner and one-line rationale each.

*Title formula bank:*
- How to [Specific Outcome] Naturally / Without X / In X Days
- The #1 Cause of [Problem] (Most Doctors Miss This)
- The [Protocol/Reset/Blueprint] for [Condition or Goal]
- [N] Signs/Mistakes/Things That Are [Causing/Destroying/Blocking] Your [Health Outcome]
- Why [Mainstream Belief] Is Wrong About [Topic] — And What the Research Actually Shows
- The Hidden Cause of [Problem] Your Doctor Has Never Tested For
- What [N]% of People Get Wrong About [Topic]
- Do This, Not That for [Condition]

*Post-launch mode:*
At 24 hours, 72 hours, and 7 days — checks YouTube CTR, podcast download curve slope, and social clip engagement against the expert's rolling baseline. If underperforming: automatically drafts revised title, revised thumbnail brief, and revised hook for a re-promoted clip. Flags for team to implement within the same week.

*Inputs:* YouTube Analytics API, Apple Podcasts Analytics, rolling performance baseline in Airtable
*Tools:* Claude API, YouTube Data API, Apple Podcasts Connect API, Airtable

---

**Agent O2 — YouTube Optimization Agent** *(Priority: P1)*

Treats the expert's YouTube channel as a discovery engine — not just a video host. Drives search and browse discovery from the expert's existing subscriber base.

*What it produces per episode:*
- YouTube title (A/B variant with different emotional and keyword angles)
- YouTube description (full, keyword-rich, timestamp chapters embedded)
- Tags and hashtag set
- Thumbnail brief (visual direction for designer — specific direction, not "make it good")
- End screen and card placement recommendations
- Chapter markers (from segment map)
- Pinned comment (first comment the expert should pin — value-first, drives engagement)
- Community post draft (posted on launch day)

*Ongoing optimization:* Monthly audit of the channel's top 20 videos — identifies which topics/formats drive the most subscribers and watch time, surfaces the pattern, recommends upcoming episodes lean into it.

*Inputs:* Episode metadata, transcript, segment map from Runsheet Agent, YouTube channel performance data
*Tools:* Claude API, YouTube Data API, VidIQ or TubeBuddy API, Airtable

---

### CATEGORY 5 — AUDIENCE GROWTH (4 agents)

These run continuously — not just per episode. They build the distribution machine that makes each episode more powerful than the last.

---

**Agent G1 — Guest Amplification Agent** *(Priority: P1)*

Manages every guest from booking confirmation through 90-day post-launch — converting each from a content provider into an active distribution partner.

*Guest tiers:*
- **Tier 1 (Whale):** 2M+ combined reach — agent-assisted, producer-reviewed, personal relationship maintained
- **Tier 2 (Major):** 500K–2M — agent-managed with producer review on outgoing communications
- **Tier 3 (Standard):** Under 500K — fully agent-managed

*Full sequence per guest:*
- **Booking confirmed:** Welcome email (show context, audience demographics, promo expectations, ask for social handles)
- **48 hours pre-recording:** Custom prep brief (5 pre-researched questions, controversy moments from guest's public work, promo expectations restated)
- **Launch day:** Full promotional kit — their specific clip (60s), 3 caption options per platform, newsletter template, stories template, direct Apple + Spotify links. Delivered as PDF or Notion page.
- **Hour 12:** Brand24 check. No repost → gentle automated reminder (Tier 2/3 only; Tier 1 → flag for personal outreach)
- **Day 30:** "Your episode stats" email with cumulative performance data — highest-leverage relationship touchpoint
- **Day 90:** Check for re-shares, update relationship score

*Whale Guest Outreach Sub-Agent (activates at Scaling/Elite):*
Targets guests with 2M+ audiences — identifies current content focus, finds intersection with expert's audience, drafts 150-word warm pitch, identifies introduction pathway, tracks in pipeline.

*Guest Performance Score (logged to Airtable):*
Downloads driven vs. show average (40%) + social shares (30%) + newsletter mention (20%) + audience overlap quality (10%) = composite score. Directly informs future booking priority.

*Inputs:* Guest profile, Brand24 monitoring, episode performance data, booking calendar
*Tools:* Claude API, Brand24, Airtable, Klaviyo API

---

**Agent G2 — Cross-Promotion Outreach Agent** *(Priority: P2)*

Runs a systematic, always-on outreach program to identify podcast cross-promotion partners and manage the pipeline. Legitimate version of the concentrated-spike growth tactic.

*Qualification criteria:*
- Monthly downloads: 100K–800K
- Audience overlap with expert's listeners: <50%
- Topic alignment: Health, wellness, specialty-adjacent, faith, mindset, longevity
- Format: Long-form interview or solo
- No brand-safety concerns

*Scoring (composite):* Net new listener potential × topic fit × host openness = priority score

*Pipeline stages:* Identified → Outreach Sent → Warm → Negotiating → Confirmed → Live → Completed

*Per prospect it produces:* Personalized 120-word outreach email (show credentials + specific audience match reason + 2–3 format options + low-friction ask), 7-day follow-up sequence

*Active pipeline volume by scale:* 10 (Starter) → 25 (Growing) → 50 (Scaling) → 100+ (Elite)

*Target:* 1 confirmed partnership/month (Starter) → 3/month (Elite). Each partnership averaging 50K listeners sending 2% = 1K–3K new listeners per month, compounding.

*Inputs:* Chartable/Podscribe audience overlap data, podcast directory data, Airtable pipeline
*Tools:* Claude API, Chartable, Podscribe, Airtable

---

**Agent G3 — Instagram DM Funnel Agent** *(Priority: P1)*

Converts the expert's existing Instagram engagement into podcast follows. Fastest, cheapest podcast follow growth mechanism available.

*How it works:* Uses ManyChat (Instagram-compliant API). Triggers when someone comments on or reacts to a health-related post. Sends a personalized DM with a direct link to the most relevant podcast episode for that exact topic.

*Trigger conditions:*
1. Comment on Instagram post about a health topic
2. Reaction to an Instagram Story
3. DM to the account with a health question
4. Story link click without following

*Core principle:* Never generic. Every DM references the specific content and routes to the best episode for that topic. Topic-to-episode routing queries Airtable for the highest-completion + most-follows-driven episode per topic cluster.

*DM templates:*
- **Comment response:** "Hey [name]! So glad this resonated. If you want to go deeper on [specific topic], [expert] just released a full episode that covers [ONE specific concrete thing]. Direct link to Apple/Spotify: [LINK]. Would mean a lot if you followed while you're there 🙏"
- **Question response:** "Great question! [Expert] covered this in depth recently — [1 sentence direct answer]. Goes much deeper in [Episode Title]: [LINK]. Follow the show on Apple or Spotify to get full episodes like this every week."
- **Story reaction:** "Glad this was helpful! Full episode going way deeper on [topic]: [ONE surprising thing]. Here's the link: [LINK]"

*Rules:* First name always used. Reference exact post/story. ONE specific value statement. Under 100 words. 1 emoji max.

*Inputs:* ManyChat trigger data, Airtable episode routing table (best episode per topic cluster + direct links)
*Tools:* ManyChat, Claude API, Airtable

---

**Agent G4 — Review & Follow Campaign Agent** *(Priority: P2)*

Systematic, always-on campaign to grow Apple reviews and Spotify follows — the two most important algorithmic signals most shows chronically under-optimize.

*Three parallel tracks:*

**Email track:** Identifies the expert's most engaged email subscribers (opened last 5+ episode emails). Sends personalized, low-pressure review request sequence — targeted ask to most loyal listeners, timed to follow an episode they demonstrably opened.

**In-episode track:** Generates a custom review ask script for each episode written to feel natural within that specific episode's context — not a generic boilerplate outro. Placement: 70% completion mark (optimal per listening behavior research).

**Performance tracking track:** Monitors Apple review count and Spotify follower gain weekly. Flags if 30+ days pass without a review campaign. Identifies which episode types drive the most new follows.

*Target:* From baseline to 1,000 recent reviews within 12 months (Starter) → 5,000+ (Elite). At that volume, Apple's algorithm treats the show as actively growing and increases browse/recommendation placement.

*Inputs:* Email platform engagement data, Apple Podcasts Connect API, Spotify API, episode performance history
*Tools:* Claude API, Klaviyo API, Apple Podcasts Connect, Airtable

---

### CATEGORY 6 — INTELLIGENCE & ANALYTICS (3 agents)

These run continuously and make the whole system smarter over time.

---

**Agent I1 — Analytics Reporting Agent** *(Priority: P2)*

Pulls all platform data and generates performance reports at three cadences: weekly for tactical adjustments, monthly for strategy, quarterly for OKR assessment.

*Weekly report includes:*
- Downloads: total this week vs. last week, rolling 30-day average, best/worst episode of week
- Apple: chart position + week-over-week change, new followers, review count
- Spotify: monthly listeners, streams, new followers, average completion %
- YouTube: views, watch hours, new subscribers, top CTR video, Shorts views
- Anomaly flags: any metric >20% above/below 4-week rolling average, with hypothesis and recommended action

*Monthly report adds:* Month-over-month growth rates, top 3 episodes across platforms, topic cluster performance breakdown, back-catalog revival results, one key strategic insight + one recommended adjustment

*Quarterly OKR report adds:* Progress vs. goals (monthly plays, chart position, subscriber count), trend projection ("At current rate, when do we hit [goal]?"), 3 evidence-backed strategic recommendations

*Inputs:* Apple Podcasts Connect API, Spotify for Podcasters API, YouTube Analytics, email platform, paid promotion data
*Tools:* Claude API, Supermetrics/Looker Studio, all platform APIs, Airtable

---

**Agent I2 — Competitor Intelligence Agent** *(Priority: P2 → activates at Growing scale)*

Monthly deep-dive on competing shows — what's driving their growth, what gaps exist, and what no one in the space is doing yet.

*Standard competitor roster (adapts to expert's specialty):* Tracks 3 competitors at Starter scale, up to 9 at Elite. Expert can configure who's tracked.

*Monthly tracking per competitor:* Podcast downloads/chart position/Spotify followers, YouTube growth + avg views, social clip strategy, SEO domain authority + top keywords

*Growth mechanism analysis (most important section):* For each competitor — what is the SINGLE THING driving their numbers most right now? Not surface metrics — the actual mechanism.

*Opportunity matrix:* Competitor coverage [Light/Medium/Heavy] × Expert's current coverage × Opportunity score → Recommended action [Double down / Match / Differentiate / Ignore]

*Tactical steal report:* What competitors are doing that's clearly working and the expert is NOT doing. For each: tactic + evidence it works + implementation plan + time/cost estimate.

*What nobody is doing (most valuable section):* 2–3 tactics no major health podcast executes well = leapfrog opportunities.

*Inputs:* Chartable/Podscribe, Ahrefs, Brand24, Social Blade, YouTube Data API
*Tools:* Claude API, multiple data source APIs, Airtable

---

**Agent I3 — New Growth Opportunity Agent** *(Priority: P3 — quarterly)*

Quarterly scan for unconventional growth tactics — needle movers the team hasn't considered, from adjacent industries.

*Tactic categories it hunts:*
- Adjacent industry tactics (what's working in newsletters, YouTube, online courses that podcasting hasn't adopted)
- Platform algorithm changes creating new optimization opportunities
- AI-native content formats (personalized episode recommendations, interactive companions)
- Community-driven growth (listener challenges, co-produced content)
- Distribution arbitrage (LinkedIn audio events, Alexa skills, podcast app promotion programs)
- Untested partnership models (network audience sharing, co-produced series, hospital distribution)

*Quarterly output:*
- 3–5 emerging tactics (evidence from adjacent industry, implementation plan, effort/impact rating)
- 1–2 unconventional bets (high-upside unusual ideas)
- ONE "just do this now" quick win (highest impact-to-effort, implementable in 2 weeks)

*Inputs:* Current tactics list, platform change log, adjacent industry growth examples
*Tools:* Claude API, web search, Airtable

---

### PAID PROMOTION — Managed Within IQ (activates at Growing scale)

**Agent G5 — Paid Promotion Optimization Agent** *(Priority: P2 → activates at Growing scale)*

Manages podcast promotion spend across three channels, optimizing for cost-per-follower continuously. Self-funding when the expert has a funnel generating revenue.

*Channels managed:*
- **Spotify Podcast Ads:** 30-second pre-roll targeting listeners of competing shows. Pause if CPF >$3.00. Scale if CPF <$1.50.
- **Overcast/Podcast Addict:** Dedicated podcast listener audience at 40–60% lower CPM than social. Rotate creative every 14 days.
- **Meta (Instagram + Facebook):** Lookalike of email subscribers + health interests. 60% cold prospecting / 40% retargeting. 15-second clip reel → episode page.

*Budget guidance by scale:*
- Growing: $1–5K/month
- Scaling: $5–15K/month
- Elite: $15–30K+/month

*Per-episode launch brief:* Recommended budget, best audience segment for this topic, 3 ad copy concepts, 15-second clip creative brief.

*Weekly optimization:* Spend by platform, new followers attributed, blended CPF, pause/scale recommendations, budget reallocation instructions.

*Inputs:* Spotify Ad Analytics, Meta Ads API, Overcast data, monthly budget cap, episode performance
*Tools:* Claude API, Spotify Ad Analytics API, Meta Ads API, Airtable

---

## The Complete Sub-Agent Architecture

```
PODCAST AGENT LEAD
├── Reads: Expert Dossier + Show Format Document + Monthly Master Plan
│         + Audience Intelligence brief (weekly, from Agent P4)
├── Determines: Episode mix, season theme, guest strategy, scale tier
├── Orchestrates: All 20 agents below
└── Delivers: Complete episode packages + continuous growth operations

SHOW PRODUCTION (4)
├── P1: Episode Runsheet Agent
├── P2: Show Notes & Research Agent
├── P3: Episode Slide Deck Agent
└── P4: Audience Intelligence Agent

SEO & DISTRIBUTION ASSETS (2)
├── S1: SEO + GEO Episode Article Agent
└── S2: Back-Catalog Revival Agent

LAUNCH & DISTRIBUTION (3)
├── L1: Episode Launch Orchestration Agent
├── L2: Clip Intelligence Agent
└── L3: Content Repurposing Agent

TITLE, PACKAGING & OPTIMIZATION (2)
├── O1: Title & Packaging Optimization Agent
└── O2: YouTube Optimization Agent

AUDIENCE GROWTH (5)
├── G1: Guest Amplification Agent
├── G2: Cross-Promotion Outreach Agent
├── G3: Instagram DM Funnel Agent
├── G4: Review & Follow Campaign Agent
└── G5: Paid Promotion Optimization Agent

INTELLIGENCE & ANALYTICS (3)
├── I1: Analytics Reporting Agent
├── I2: Competitor Intelligence Agent
└── I3: New Growth Opportunity Agent (quarterly)
```

**Agent count: 21** (Podcast Agent Lead + 20 sub-agents)

---

## The Infrastructure Stack

| Layer | Technology | Why |
|-------|-----------|-----|
| **Orchestration** | n8n (self-hosted) + Make (backup) | n8n flat-rate pricing saves $2–3K/month vs. Make at scale. Self-hosted = full control, no per-task fees |
| **AI Brain** | Claude API (primary) | Measurably better at maintaining consistent voice across thousands of outputs than alternatives — essential for brand voice |
| **Transcription** | AssemblyAI | Speaker-labeled transcripts, every downstream agent depends on transcript quality |
| **Analytics Hub** | Supermetrics / Looker Studio | All platform data (YouTube, Spotify, Apple, email) in single dashboard every agent can query |
| **Central Database** | Airtable | Episode data, guest scores, clip performance, content calendar, outreach pipeline — agents read/write constantly |
| **Social Scheduling** | Buffer (API-connected) | Agent outputs auto-post |
| **DM Automation** | ManyChat ($299/month Pro) | Instagram-compliant API for DM sequences |
| **Guest/Brand Monitoring** | Brand24 | Guest promotional activity detection, brand mention monitoring |
| **Email** | Expert's ESP (Klaviyo or equivalent) via API | Programmatic launch-day sends |
| **Competitive Intelligence** | Chartable + Podscribe + Ahrefs | Download estimates, audience overlap, SEO data |

**Total monthly infrastructure cost:** $800–2,500/month at full build-out (scales with expert's plan tier — Starter pays less, Elite pays more). Against any meaningful funnel revenue, this is under 1% of podcast-driven income.

---

## The Compounding Loop — Why This Compounds Instead of Just Adding

```
AUDIENCE INTELLIGENCE AGENT
    Identifies surging topic → informs content calendar
         ↓
RUNSHEET AGENT
    Engineers episode for max retention + clipability
         ↓
LAUNCH ORCHESTRATION AGENT
    Executes all channels at Hour 0 → concentrated 24h spike
         ↓
CLIP INTELLIGENCE AGENT
    Identified 5–10 clips before recording → team cuts from prioritized list
         ↓
CONTENT REPURPOSING AGENT
    Turns episode into 15+ assets → extends reach for 30 days
         ↓
SEO ARTICLE AGENT
    Drives search discovery for 3+ years
         ↓
BACK-CATALOG REVIVAL AGENT
    Resurfaces related episodes → multiplies total topic plays
         ↓
GUEST AMPLIFICATION AGENT
    Guest shares to their audience by Hour 12 → logged for future booking decisions
         ↓
CROSS-PROMOTION AGENT
    Identifies 3 shows with matching audience → initiates partnership outreach
         ↓
PAID PROMOTION AGENT
    Puts $500–2K behind best-performing episode on Spotify → drives qualified new followers
         ↓
REVIEW CAMPAIGN AGENT
    Identifies engaged subscribers → targeted review request → Apple algorithm ranking improves
         ↓
ALL RESULTS → Airtable → Analytics Agent → system improves for next episode
```

Every output feeds back in. The 12th episode launches more powerfully than the 1st. The 52nd launches more powerfully than the 12th. The system compounds.

---

## IQ Claw Integration — Podcast Agent Requests

| Expert Says | IQ Claw Routes To |
|-------------|------------------|
| "Build my show format" | Podcast Lead → Show Format Design session |
| "Plan next month's podcast calendar" | Podcast Lead → Editorial Planner (from season/episode architecture) |
| "Build the runsheet for Thursday's episode" | P1: Runsheet Agent |
| "Write show notes for this week's episode" | P2: Show Notes & Research Agent |
| "What clips should we cut from this episode?" | L2: Clip Intelligence Agent |
| "Get all the social posts for this episode" | L3: Content Repurposing Agent |
| "Check if this episode title is strong" | O1: Title & Packaging Optimization Agent |
| "What are my listeners asking about this week?" | P4: Audience Intelligence Agent |
| "Send the promo kit to my guest" | G1: Guest Amplification Agent |
| "Find me 10 cross-promotion partner shows" | G2: Cross-Promotion Outreach Agent |
| "What's my podcast performance this month?" | I1: Analytics Reporting Agent |
| "What is Huberman doing that we aren't?" | I2: Competitor Intelligence Agent |
| "What growth tactics are we missing?" | I3: New Growth Opportunity Agent |
| "Set up the Instagram DM funnel" | G3: Instagram DM Funnel Agent |

---

## How the Podcast Agent Connects to the Rest of clinicIQ

```
PODCAST AGENT
    │
    ├── Reads from: Expert Dossier (voice, mechanism, avatar, offer stack)
    │              Brand North Star (positioning, ALWAYS/NEVER rules)
    │              Monthly Master Plan (campaign alignment)
    │
    ├── Feeds into: Content Builder (clip specs + social post briefs per episode)
    │              Email Builder (episode announcement brief + launch email)
    │              Website Builder (show notes → blog posts)
    │              Ad Creative Builder (best-performing clips → ad creative candidates)
    │              IQ Drive/Podcast/[Show Name]/[Season]/[Episode]/
    │
    └── Shares with: Analytics Dashboard (Layer 4) — podcast performance data
                     feeds back into monthly strategy alongside content + funnel metrics
```

One podcast episode, fully processed by the Podcast Agent, automatically generates work queues for Content Builder, Email Builder, and Website Builder. The expert records. The machine handles the rest.

---

*Step 16c — Podcast Agent — Full Specification — v1.0*
*Source: DrJoshAxe-RunsheetAgent.docx + DrJoshAxe-PodcastMarketingAgents.docx + DrJoshAxe-AgentPromptLibrary.docx*
*This is the generalized platform version. Josh Axe's team deploys this system as a clinicIQ power user.*
*Next: Step 17 — Analytics Dashboard (Layer 4)*
