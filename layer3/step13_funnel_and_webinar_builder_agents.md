# clinicIQ — Layer 3: Builder Agents — Step 13: Funnel Builder Agent + Webinar Builder Agent
**Version 1.0 — Draft**
*Step 13 of 22 | Depends on: Steps 1–12 (Layers 1 & 2 complete + Content Builder)*

---

## Purpose

Step 13 defines two agents that operate as a single conversion system: the **Funnel Builder Agent**, which constructs every page in the expert's funnel, and the **Webinar Builder Agent**, which produces the conversion event that sits at the center of it.

These two agents are architecturally distinct but strategically inseparable. The funnel pages exist to get people to the webinar and convert them after it. The webinar exists to establish the One Big Domino belief and present the offer. Neither works without the other. They are built together, read from the same dossier inputs, and deliver a unified conversion experience.

Every funnel page exits this agent as a live, hosted, mobile-optimized web page. Every webinar exits as a complete, production-ready script with an accompanying slide deck. Nothing requires a third-party page builder, a separate hosting subscription, or any tool outside of clinicIQ.

---

## Part 1 — The Funnel Builder Agent

### What It Builds

The Funnel Builder produces every page in the expert's conversion funnel — from the first opt-in to the post-purchase onboarding screen. Pages are live web pages: fully coded, hosted on the clinicIQ infrastructure, mobile-first, integrated with the expert's email platform, payment processor, and tracking pixels, and editable inside clinicIQ via a visual editor without leaving the platform.

**Complete page inventory:**

| Page | Position in Funnel | Primary Conversion Goal |
|---|---|---|
| **Opt-in / Lead capture page** | Entry — cold traffic lands here | Email capture in exchange for lead magnet |
| **Webinar registration page** | Entry — drives to conversion event | Registration for live or evergreen webinar |
| **Thank you / Bridge page** | Post opt-in, pre-webinar | Micro-commitment + expectation set + warm-up |
| **Webinar room page** | The conversion event | Attend the webinar, consume the offer |
| **VSL page** | Evergreen version of webinar room | Auto-play video sales letter, no live interaction |
| **Replay page** | Post-live webinar | Urgency-framed replay window for non-buyers |
| **Order page** | Post-webinar offer | Purchase the core offer |
| **Upsell page** | Immediately post-purchase | Upgrade to next offer tier |
| **Downsell page** | Non-buyer path | Alternative offer at lower commitment |
| **Thank you / Onboarding page** | Post-purchase | Welcome, next steps, continuity introduction |
| **Paid assessment page** | Tier 1 paid offer | Assessment booking + payment |
| **Application page** | High-ticket path ($15K+) | Application submission for strategy call |
| **Sales letter page** | Long-form text alternative | Long-form copy page for text-primary audiences |

Not every expert needs every page on day one. The Page Strategy sub-agent determines the build sequence based on the funnel variant specified in the Growth Blueprint, prioritizing the pages needed before traffic is sent.

---

### Technical Architecture — How Funnel Pages Are Built

Funnel pages are live, hosted web pages — not static images. The technical architecture is built for the following non-negotiable requirements:

- **Live URLs** — every page has a real URL (expertname.cliniciq.com or custom domain)
- **Mobile-first** — 60%+ of health funnel traffic arrives on mobile; mobile is the primary design target
- **Fast loading** — pages deploy as static HTML on Cloudflare CDN; sub-1-second load times are achievable and expected
- **Integrated** — email platform, payment processor, tracking pixels, and calendar tools connect automatically based on the expert's tech stack
- **Editable in-platform** — experts never leave clinicIQ to edit a page

**The build pipeline:**

**Step 1 — AI generates the complete page**
The Page Layout Generator sub-agent writes the full HTML/CSS/JS for each page. This includes all copy (pulled from the Page Copy Writer and Social Proof Block Builder sub-agents), all layout and design (conversion-optimized, brand-accurate, mobile-first), and all integration hooks (form IDs, pixel event names, payment widget placeholders).

**Step 2 — GrapesJS schema output**
The generated page is structured as a GrapesJS-compatible component tree — the open-source visual editor SDK that powers the in-platform editor. This means from the moment the page is generated, the expert can drag, drop, edit text, swap images, and change colors visually inside clinicIQ without touching code. It is Webflow-level editing without leaving the platform.

**Step 3 — Integration Configurator injects connections**
The Integration Configurator reads the expert's `business.tech_stack` dossier field and injects the correct integration code: the email platform form embed, Stripe payment widget (or PayPal secondary), Meta Pixel with correct event mapping, Google Tag Manager container, TikTok Pixel if applicable, Calendly or Cal.com embed for assessment pages.

**Step 4 — Deploy to CDN**
Pages are compiled to static HTML and pushed to Cloudflare CDN. The expert's subdomain is provisioned automatically. Custom domain support via CNAME — the expert points their own domain to clinicIQ's CDN in one step.

**Step 5 — QA pass**
The Funnel QA sub-agent verifies: all inter-page links are correct, forms submit to the right email list, pixel events fire on the correct actions, mobile rendering is clean, brand consistency passes.

**Step 6 — Live and editable**
The page is live at its URL and available in the expert's Funnel Dashboard inside clinicIQ for editing, duplication, A/B variant creation, and performance monitoring.

---

### Copy Frameworks — By Page Type

Every page follows a proven direct response architecture. These are not suggestions. They are the structural rules the Page Copy Writer sub-agent operates within.

**Opt-in Page / Lead Capture**
The simplest page in the funnel. One job: capture the email.
- **Headline:** Benefit + curiosity OR problem + solution promise. Specific, not clever.
- **Subheadline:** Who it's for + what they get + why it matters right now. One sentence.
- **Bullets:** 3–5 curiosity-gap bullets. Each one opens a loop the lead magnet closes. Never feature lists.
- **CTA button:** Action-specific ("Send Me The [Guide Name]" — never "Submit" or "Click Here")
- **Social proof line:** One line, above or below form ("Join 14,000+ practitioners who...")
- **Zero navigation.** Zero footer links. One exit: the opt-in form. Anything else is a conversion leak.
- **A/B variants:** Headline Generator produces 3 headline variants. Two full page variants (A/B) are produced for key pages — the Analytics Dashboard tracks conversion per variant and identifies the winner.

**Webinar Registration Page**
- **Headline:** What they will discover — framed as the One Big Domino in outcome language
- **Date/time block:** Prominent, specific, with timezone. Real urgency where applicable.
- **What you'll learn:** 3 bullet promises mapped directly to the Three Secrets from the webinar
- **Who this is for:** Avatar-specific qualifier (makes the right people lean in and the wrong people self-select out)
- **Host authority block:** Above the fold — top 2–3 authority signals only. Not a full bio.
- **CTA:** "Reserve My Spot" with date/time repeated in the button context
- **No navigation.** Same conversion hygiene as opt-in page.

**Thank You / Bridge Page**
Often underbuilt. This page does critical work: it confirms the action, sets expectations, and makes the first micro-commitment toward the next step (attending the webinar).
- Confirm what they just did ("You're registered — here's what happens next")
- Prime them for the webinar ("To get the most out of [training name], take 2 minutes to...")
- Optional: a short video from the expert with a personal invitation
- Add-to-calendar button (critical for show rate)
- Teaser of what they'll discover (open loops = motivation to show up)

**Order Page**
The most important page in the funnel. Everything upstream has been building to this.
- **Above the fold:** Offer name + transformation promise headline + price + primary CTA. This information must all be visible without scrolling on mobile.
- **Value stack:** Every program element listed with its individual value. Written by Offer Stack Builder sub-agent from the dossier offer architecture.
- **Total value vs. price:** The contrast between what it's worth and what they're paying is the core of the close.
- **Guarantee block:** Full, prominent, specific. Risk reversal is the primary conversion lever on the order page. Small or buried guarantees kill conversions.
- **Testimonials:** Minimum 3, positioned adjacent to the CTA. Use the proof that most directly matches the primary objection (cost, time, "will it work for me").
- **FAQ:** 5–7 questions — the most common objections. Written by Objection Handler, positioned below the CTA.
- **Payment options:** One-time price AND payment plan presented with equal visual weight. Payment plan reduces the psychological barrier without changing the conversion economics.
- **Urgency/scarcity:** Only if legitimate. Real enrollment deadlines, real bonus expiration, real price increases. Fake countdown timers are a compliance and trust risk and are never used in clinicIQ funnels.
- **No navigation.** The only action on this page is purchase or leave.

**Upsell Page**
Short, direct, one decision.
- Acknowledge what they just purchased with a congratulation
- "Before you access your program, take 30 seconds to look at this..."
- What this adds to what they just bought — specifically and briefly
- One CTA to add it, one CTA to skip
- No re-selling the original offer. No navigation.

**Downsell Page**
Not a consolation prize. A different path to a related result.
- Acknowledge they didn't take the main offer — without guilt or pressure
- Position the downsell as a different vehicle for a similar destination
- Brief value argument, clear price, single CTA
- Short. If it's longer than a scroll on mobile, it's too long.

**Replay Page**
Time-limited replay of a live webinar. Urgency is structural here because the replay window is real.
- Headline: "You registered for [webinar name] — here's your replay"
- Real deadline: specific date and time the replay comes down
- What they'll get if they watch and act before the deadline
- The webinar video embedded and auto-playing
- The offer presented below the video (same order page elements, condensed)

**Paid Assessment Page**
- What the assessment is, who it's for, and what they'll get from it
- Price ($47–$97) framed against the value of knowing their root cause
- Booking widget (Calendly or Cal.com) below the fold, Stripe payment collected on booking
- Brief expert bio/credibility block
- Testimonials from previous assessment participants

**Application Page**
For high-ticket programs ($15K–$50K+) where a strategy call precedes the purchase.
- What the program is and who it's for — specific qualifier criteria
- "This is not for everyone" framing (raises perceived exclusivity)
- Short application form: situation, goal, current revenue/reach, commitment level
- No price listed on the application page (the call is where the offer is made)
- What happens after they apply: timeline, what the call covers, next steps

---

### Mobile-First Design Standard

Every funnel page is designed mobile-first. The CSS uses `min-width` breakpoints — mobile is the base, desktop is the enhancement. This is not a preference. It is an architectural requirement.

**Mobile-specific rules the Page Layout Generator enforces:**

- **Above-the-fold content on mobile:** Headline, subheadline, and primary CTA must all be visible on a 375px viewport without scrolling
- **Button size:** All CTA buttons are minimum 44px tall on mobile (Apple/Google tap target standard)
- **Font sizes:** Body text minimum 16px on mobile (prevents iOS auto-zoom on form fields)
- **Form fields:** Stack vertically on mobile, full width, large tap targets
- **Video:** Embeds are 16:9 ratio, fluid width on mobile (never fixed pixel width)
- **Payment widgets:** Stripe elements are tested on mobile — touch-optimized card entry
- **Load speed:** No heavy background images above the fold on mobile (use CSS gradients or lightweight WebP)

The Mobile Optimizer sub-agent reviews every generated page at 375px, 414px, and 768px viewports before the page passes QA.

---

### Integration Architecture

Every funnel page connects to the expert's existing tech stack. The Integration Configurator reads the `business.tech_stack` field from the expert's dossier and injects the correct code automatically. The expert never manually configures integrations.

**Supported integrations:**

| Integration Type | Supported Platforms | How It's Injected |
|---|---|---|
| Email marketing | ActiveCampaign, Klaviyo, ConvertKit, GoHighLevel, Mailchimp | Form embed code, API webhook on opt-in |
| Payment processing | Stripe (primary), PayPal (secondary) | Stripe Elements widget on order/assessment pages |
| Tracking — Meta | Meta Pixel + Conversions API | GTM tag or direct pixel injection, event mapping per page action |
| Tracking — Google | Google Analytics 4 + Google Ads conversion | GTM container injection |
| Tracking — TikTok | TikTok Pixel | GTM tag injection |
| Calendar/Booking | Calendly, Cal.com | Embed widget on assessment and application pages |
| Webinar platform | Zoom Webinar, WebinarJam, Demio | Registration confirmation redirect + room page embed |
| CRM | GoHighLevel, HubSpot | Contact creation webhook on form submission |

**Integration failure protocol:** If an integration cannot be auto-configured (missing API key, unsupported platform), the Integration Configurator flags the specific gap in the expert's dashboard with a one-step instruction to resolve it. The page is built and live regardless — integrations are added when ready without rebuilding the page.

---

### Funnel Performance Benchmarks

These benchmarks are hardcoded into the Funnel QA sub-agent as the standard against which every page is measured. They feed directly into the Layer 4 red/yellow/green threshold system.

| Funnel Element | Green (On Target) | Yellow (Monitor) | Red (Fix Now) |
|---|---|---|---|
| Opt-in page conversion | ≥35% | 20–34% | <20% |
| Webinar registration conversion | ≥35% | 20–34% | <20% |
| Webinar show rate (live) | ≥25% | 15–24% | <15% |
| VSL completion rate to offer | ≥45% | 30–44% | <30% |
| Order page conversion (warm) | ≥12% | 6–11% | <6% |
| Order page conversion (cold) | ≥3% | 1.5–2.9% | <1.5% |
| Upsell take rate | ≥20% | 10–19% | <10% |
| Downsell take rate | ≥18% | 8–17% | <8% |
| Assessment booking conversion | ≥25% | 12–24% | <12% |

When a red threshold is hit, the Funnel QA sub-agent generates a specific diagnosis and a rebuild recommendation — not just a flag. It identifies the most likely failure point in the page (headline, CTA, proof, guarantee) based on where in the page scroll the conversion drops off.

---

### The Funnel Builder Sub-Agent Team

```
FUNNEL BUILDER LEAD AGENT
├── Reads: Expert Dossier Brief + Brand North Star Part 2 + Growth Blueprint funnel spec
├── Determines: Which pages to build, build priority order, funnel sequence map
├── Orchestrates: All 9 sub-agents below
└── Delivers: Live funnel pages + funnel map to expert dashboard

SUB-AGENTS:

1. Page Strategy Agent
   Maps the full funnel sequence from Growth Blueprint funnel variant
   Determines which pages need to be built for this expert's starting profile
   Sets build priority: opt-in and bridge page first, order page before traffic launch
   Produces the funnel flow diagram shown in the expert's dashboard

2. Headline Generator
   Writes 3–5 headline variants for every page
   Calibrates awareness level to funnel position (opt-in = Level 2; order page = Level 4)
   Applies direct response headline frameworks: benefit, curiosity, problem/solution, 
   who-it's-for qualifier
   Flags the recommended primary variant and reasons for the recommendation

3. Page Copy Writer
   Writes all body copy: subheadlines, bullets, proof narrative blocks, 
   guarantee language, FAQ answers, urgency language
   Reads from Brand North Star Part 2 ALWAYS/NEVER rules + Objection Library
   Applies compliance filter for this expert's specialty to all copy before output

4. Social Proof Block Builder
   Pulls transformation stories and testimonials from the Proof Bank
   Selects proof that matches the primary objection at each funnel position
   Formats for page position: brief social proof line above fold,
   full transformation story below fold or near CTA
   Flags thin proof banks and recommends what to capture

5. Offer Stack Builder
   Constructs the visual value stack for order pages
   Pulls all offer elements from the dossier offer architecture section
   Writes individual value justification for each stack element
   Calculates total stack value and formats the price contrast

6. Page Layout Generator
   Writes complete, production-ready HTML/CSS/JS for each page
   Mobile-first CSS architecture (min-width breakpoints)
   Conversion-optimized layout hierarchy: benefit → proof → offer → CTA
   Outputs GrapesJS-compatible component schema for in-platform visual editing
   Produces A/B variant for headline and above-fold section on key pages (opt-in, order)

7. Integration Configurator
   Reads business.tech_stack from the expert dossier
   Injects email platform integration (form embed or webhook)
   Injects payment processor (Stripe Elements on order and assessment pages)
   Injects tracking pixel suite (Meta, Google, TikTok) with correct event mapping
   Configures calendar embed on assessment and application pages
   Flags any integrations that require manual credential setup

8. Mobile Optimizer
   Tests every generated page at 375px, 414px, and 768px viewports
   Flags layout issues: content below fold on mobile, small tap targets, 
   fixed-width elements, font sizes below 16px
   Applies mobile-specific copy adjustments (headline shortened for mobile, 
   bullets tightened) where needed

9. Funnel QA Agent
   End-to-end funnel check before pages go live:
   All inter-page links correct and tested
   Form submissions route to the correct email list and sequence
   Pixel events fire on the correct actions (PageView, Lead, InitiateCheckout, Purchase)
   Mobile rendering clean on all test viewports
   Brand consistency: colors, fonts, voice register all match Brand North Star
   Produces a pre-launch checklist for the expert — every item checked off before traffic
```

**Agent count: 10** (Funnel Builder Lead + 9 sub-agents)

---

## Part 2 — The Webinar Builder Agent

### What It Builds

The Webinar Builder Agent produces the expert's complete conversion event — the single most high-leverage piece of content in the entire platform. A well-built webinar is worth more than all the content, ads, and email sequences combined. It is the moment the avatar's beliefs shift, the mechanism becomes undeniable, and the offer becomes the obvious next step.

The Webinar Builder produces:
1. **The full webinar script** — 7,000–15,000 words of precision-engineered persuasion, written to the expert's exact Voice DNA, calibrated to the avatar's specific false beliefs, and structured to establish the One Big Domino before the offer is ever made
2. **The slide deck** — a complete, designed presentation that accompanies the script slide by slide, built as HTML/CSS and rendered to a shareable, presentation-ready format
3. **A/B angle variants** — multiple webinar angles and titles to test before scaling traffic
4. **Two script formats** — a live webinar version (with energy markers, Q&A section, live interaction notes) and a VSL/evergreen version (word-for-word, tighter, no live elements)
5. **The Q&A script** — scripted responses to the 7–10 most likely objections for the live portion
6. **The follow-up trigger** — a structured handoff to the Email Builder Agent with the specific sequences needed post-webinar (show/no-show/purchased/didn't purchase)

---

### The Two Frameworks — And How They're Combined

The Webinar Builder operates on two primary frameworks simultaneously. They are not competing systems — they are complementary architectures that work best when layered.

#### Framework 1 — Russell Brunson's Perfect Webinar

The structural backbone. Every webinar built in clinicIQ follows this sequence as its skeleton.

**The Perfect Webinar Architecture:**

**1. The Opening (Minutes 0–5)**
The first five minutes do four jobs: establish credibility (briefly — not a CV recitation), tell the audience exactly what they're about to get, give them a compelling reason to stay (future pacing what's coming later), and deliver a pattern interrupt that signals this is not a typical webinar.

The pattern interrupt is critical. The avatar has been on webinars before. The first 90 seconds must violate their expectation. This can be a bold claim, a surprising statistic, a story that starts in the middle, or a direct acknowledgment that most webinars waste their time — and a specific promise that this one won't.

**2. The One Big Domino (Minutes 5–15)**
The single belief that makes everything else logical. Not a topic. Not a subject. The ONE idea that, if the avatar genuinely believes it, makes choosing this expert the only rational decision.

*"If I can make you believe that [One Big Domino], then [taking action on this offer] is the only logical conclusion."*

Everything from minute 15 onward exists to prove, demonstrate, and reinforce this single belief. The webinar does not wander. Every story, every piece of data, every patient case connects back to the One Big Domino.

**3. The Three Secrets**
Each Secret is a mini-webinar: a complete belief shift in a self-contained arc.

*Secret 1 — New Vehicle Belief Shift*
The avatar believes their old vehicle (what they've been trying) should work. This secret proves it cannot — not because the avatar failed, but because it was never designed to address the root cause. Then it introduces the new vehicle (the expert's mechanism) as the thing that was missing.

Structure:
- Transition: *"The first thing standing between you and [transformation] is..."*
- False belief: what they currently believe about their old vehicle
- The epiphany bridge: the story of how the expert discovered the new vehicle (told from their own experience or a formative clinical case)
- Teaching: the mechanism explained — why the old vehicle fails and why the new one works
- Proof: a patient result that demonstrates the mechanism working

*Secret 2 — Internal Belief Shift*
The avatar has a story about themselves. They've tried and failed. Their body is broken. This is just aging. They don't have the discipline. This secret dismantles that internal narrative without attacking the avatar's identity.

Structure:
- Transition: *"The second thing keeping you stuck has nothing to do with willpower..."*
- False belief: the specific self-limiting story the avatar carries
- Empathy bridge: the expert names the experience so specifically that the avatar feels seen
- The reframe: it's not a personal failure — it's a missing variable
- Proof: a patient story featuring someone who had the same internal belief and broke through it

*Secret 3 — External Belief Shift*
The avatar believes they need something they don't have: more money, more time, a different doctor, lab access, the right supplements. This secret removes the external excuse without dismissing its legitimacy.

Structure:
- Transition: *"The third thing in the way is the one most people never see coming..."*
- False belief: the external thing they think they need
- The reframe: why that external thing is either available within the mechanism or irrelevant to it
- Simplified path: the mechanism works without the thing they think they need
- Proof: a patient story featuring someone who had that exact limitation and succeeded anyway

**4. The Stack and Close**
The offer presentation. This is not a pitch. It is a natural conclusion to everything that came before it. The avatar who has tracked with the Three Secrets is already in a mental state where the offer is a logical next step — the close should feel like relief, not pressure.

Structure:
- Transition: *"So here's what I've put together based on everything we've covered today..."*
- Introduce the program name
- Stack: present every program element one at a time, each with its individual value assigned
- Each stack element presented as: what it is → what it does → what it would cost to get it elsewhere → what it's worth in terms of the transformation
- Total stack value reveal (the sum of individual values)
- Price reveal — anchored against the total stack value and against the cost of not solving the problem
- Payment plan option presented with equal weight to the full price
- Guarantee: the full risk reversal — specific, credible, and presented as proof of confidence, not desperation
- Urgency/scarcity (only if legitimate — see note below)
- Final CTA: specific, clear, low-friction
- What happens after they click: walk them through the next 60 seconds so the decision feels safe

**Urgency and scarcity — the clinicIQ standard:**
Fake countdown timers that reset every visit are a trust-destroying tactic that sophisticated audiences recognize immediately. clinicIQ never generates fake urgency. All urgency and scarcity elements in the close must be documentable and real:
- Enrollment window (cohort closes on a specific date)
- Bonus expiration (first 20 buyers receive X — tracked and honored)
- Price increase (price goes up at a specific date — documented and enforced)
- Availability (genuine capacity limit for a 1:1 or small-group program)

When none of these exist, the close focuses on the cost of delay — the additional days, months, or years the avatar spends without the solution. This is the most honest and ultimately most compelling urgency available.

---

#### Framework 2 — Fladlein's True/False System

Layered inside the Three Secrets structure. While Brunson provides the architecture, Fladlein's True/False mechanic provides the belief-shift mechanism inside each Secret.

**How it works:**
Instead of making a claim and supporting it, the True/False mechanic makes the avatar an active participant in dismantling their own false beliefs.

The sequence:
1. *"Let me ask you something. Is it TRUE or FALSE that [specific false belief]?"*
2. Pause — the avatar engages mentally, usually expecting it's true
3. *"It's FALSE. And here's why that matters for you..."*
4. The true belief stated clearly
5. Proof for the true belief (evidence, mechanism, patient story)
6. Bridge: how this connects directly to the transformation

**Why it's more powerful than straight assertion:**
When the expert asserts something, the avatar's skepticism filter is engaged. When the expert asks a question and then reveals the answer, the avatar's curiosity is engaged instead. The dopamine hit of the reveal is associated with the true belief — making it more memorable and more deeply held than any claim the expert could simply state.

Minimum 5 True/False pairs per webinar, distributed across the Three Secrets. The True/False Generator sub-agent builds these from the avatar psychology section of the dossier — specifically from the `avatar.false_belief_vehicle`, `avatar.false_belief_internal`, and `avatar.false_belief_external` fields.

---

### Webinar Formats — Two Script Outputs

The Webinar Builder produces two complete script versions from a single production run:

**Version 1 — Live Webinar Script**
Formatted for a real-time presentation with a live audience.
- Energy markers at key transitions (*[HIGH ENERGY — this is where you lean in]*, *[SLOW DOWN — let this land]*)
- Live interaction prompts (*"Type YES in the chat if you've experienced this"*, *"How many of you have been told your labs are normal?"*)
- Q&A section script (see Objection Handler sub-agent)
- Pacing notes and timing guides (*[Approx. 45 min to this point]*)
- Ad-lib latitude notes where the expert's personality should come through unscripted
- Teleprompter-friendly formatting (short lines, generous white space)

**Version 2 — VSL/Evergreen Script**
Formatted for pre-recorded, word-for-word delivery.
- Tighter — all filler and live-audience interaction removed
- Every word is deliberate — no room for tangents that don't serve the arc
- Performance direction embedded (*[Pause here — 3 full seconds]*, *[Lean toward camera]*)
- Shot direction for the production team (*[Cut to screen share here]*, *[Return to talking head]*)
- Target duration: 45–75 minutes for a full webinar VSL; 20–35 minutes for a condensed VSL
- No Q&A section — objections are pre-handled in the body of the script

Both versions are produced simultaneously by the Script Assembler from the same sub-agent inputs. The expert chooses which version to record or present first.

---

### The Slide Deck

Every webinar script is accompanied by a complete, designed slide deck. The Slide Deck Generator sub-agent produces the full deck — not a spec, not a guide, a finished, designed presentation.

**Build approach:**
The same HTML/CSS → render pipeline from Step 12 applies here. Each slide is written as HTML/CSS, rendered via headless Chromium to a high-resolution image, and assembled into a presentation file. The deck is exportable as:
- PDF (universal sharing, printing)
- PNG sequence (for import into Keynote, PowerPoint, Google Slides)
- Native HTML presentation (runs in a browser, zero import needed)

**Slide types and their roles:**

| Slide Type | Webinar Position | Content |
|---|---|---|
| Title | Opening | Webinar title, expert name, one-line promise |
| Credibility | Opening | Top 3 authority signals — brief, visual |
| Agenda tease | Opening | What they'll discover (open loops) |
| One Big Domino | Pre-secrets | The single belief stated boldly |
| Teaching | Each Secret | Mechanism explanation, diagrams, data |
| Epiphany bridge | Each Secret | Story moment — minimal text, evocative visual |
| False belief → true belief | Each Secret (Fladlein) | Split visual: the false belief struck through, the truth revealed |
| Proof/testimonial | Each Secret | Patient result — name/alias, condition, result, timeframe |
| Stack slide | Close | The full offer stack building element by element |
| Value reveal | Close | Total stack value vs. price — large, clear |
| Guarantee | Close | Full guarantee statement with visual treatment |
| CTA | Close | URL, specific instruction, urgency element |

**Slide design standard:**
Every slide is premium, brand-accurate, and consistent with the Visual DNA. Teaching slides use clean diagrams and minimal text — not bullet-point walls. Proof slides put the result front and center with the story supporting it. Stack slides build visually (each new element appears in sequence) for maximum perceived value. The deck looks like it was produced by a professional design team.

---

### The Webinar Builder Sub-Agent Team

```
WEBINAR BUILDER LEAD AGENT
├── Reads: Expert Dossier Brief + Brand North Star Part 2 + Growth Blueprint webinar spec
├── Determines: Framework blend (Brunson + Fladlein ratio), format (live/VSL/both),
│             angle selection from Angle Generator, True/False count per Secret
├── Orchestrates: All 10 sub-agents below
└── Delivers: Complete script (both versions) + slide deck + Q&A script + handoff trigger

SUB-AGENTS:

1. Webinar Angle Generator
   Generates 5–10 distinct webinar angles from the dossier
   Each angle = a different framing of the same mechanism and One Big Domino
   Scores each angle by: hook strength, avatar awareness level fit, differentiation from 
   common webinar titles in the expert's niche, alignment with current hook bank
   Presents ranked options to the expert — expert selects, or Lead Agent selects the
   highest-scoring angle for batch production

2. Hook Builder
   Generates 5+ webinar title variants for the selected angle
   Title types: curiosity ("The [X] Most Doctors Have Never Heard Of..."),
   pain ("Why You're Still [symptom] Despite Doing Everything Right"),
   mechanism ("The [Mechanism Name] Method That's Helping [avatar] Finally [result]"),
   identity ("What It Actually Takes to [transformation identity]"),
   secret/revelation ("The Real Reason [symptom] Never Gets Better — And What Actually Works")
   Also produces the webinar registration page headline variant for each title

3. True/False Generator
   Reads avatar.false_belief_vehicle, avatar.false_belief_internal, 
   avatar.false_belief_external from the dossier
   Expands each into a set of specific, concrete True/False pairs
   Each pair: the false belief stated as a question → the reveal → the true belief → 
   the proof element → the bridge to the mechanism
   Minimum 5 pairs distributed across the Three Secrets
   Calibrated to use the avatar's exact language for the false belief statement

4. Epiphany Bridge Builder
   Constructs the expert's origin story in the classic epiphany bridge arc:
   Old world (what life was like before the discovery)
   The wall (the moment the old approach failed or the problem became undeniable)
   The discovery (how the new vehicle was found — serendipitous, clinical, personal)
   The new world (what changed once the mechanism was applied)
   Written in Voice DNA — first-person, narrative, specific details that create visual imagery
   Length-calibrated for webinar pacing (3–5 minutes of spoken delivery)
   Also produces shorter versions for Secret 2 and 3 patient story bridges

5. New Vehicle Builder
   Constructs the mechanism presentation within the webinar
   If mechanism is not yet named: generates name options from mechanism description
   Writes the plain-language mechanism explanation (the "so simple a 14-year-old understands it" standard)
   Specifies the visual demonstration concept: the diagram, the analogy, the physical metaphor
   Writes the mechanism reveal sequence — building the concept in layers so the aha moment
   arrives at the right moment in the teaching

6. Three Secrets Writer
   Full content for each of the three Secret sections
   Each Secret: teaching content (the actual clinical/scientific insight) +
   Epiphany Bridge story (from Epiphany Bridge Builder output) +
   True/False sequence (from True/False Generator output) +
   Patient proof story (from Proof Bank in dossier)
   Written to Voice DNA — sounds like the expert at their best, not a script template
   Teaching is substantive and novel — this content must deliver genuine insight,
   not surface-level summaries. The avatar must learn something real.

7. Stack and Close Builder
   The full offer presentation and close sequence
   Stack reveal: every element from the dossier offer architecture, 
   each with individual value and transformation role written out
   Price anchor: the stack total → the cost of the problem → the price reveal
   Payment plan presentation
   Guarantee: full risk reversal written from the dossier guarantee concept
   Urgency/scarcity: only legitimate mechanisms — assessed from dossier 
   and flagged if none exist (cost-of-delay urgency applied instead)
   Final CTA: specific URL, action instruction, what happens next
   Written in the expert's closing register — warm, confident, never pushy

8. Objection Handler
   Q&A script for the live webinar portion
   Top 7–10 objections ranked by likelihood (from dossier avatar.objections_primary)
   For each objection: acknowledge → reframe → evidence → redirect
   Written as conversational responses, not formal arguments
   Also produces pre-handled objection section for VSL/evergreen version 
   (objections addressed in the close sequence body, not as a Q&A segment)

9. Slide Deck Generator
   Full slide deck produced from the assembled script
   Slide-by-slide map: content, layout concept, visual direction per slide
   HTML/CSS written for each slide → Puppeteer renders to high-resolution PNG
   Brand-accurate: Visual DNA colors, fonts, photography style applied
   Deck assembled as PDF + PNG sequence + native HTML presentation
   Teaching diagrams and mechanism visuals included (AI-generated or CSS-drawn)

10. Script Assembler
    Receives outputs from all 9 sub-agents above
    Assembles the complete, continuous script in two versions:
    Live webinar version: teleprompter-formatted, energy markers, live interaction prompts,
    pacing guides, Q&A section, timing estimates per section
    VSL/evergreen version: word-for-word, tighter, performance direction embedded,
    shot direction for production team, no Q&A
    Produces the follow-up trigger: a structured brief for the Email Builder Agent 
    specifying which post-webinar sequences are needed and what content each should reference
    from the webinar content (hooks, proof stories, open loops left in the webinar to close via email)
```

**Agent count: 11** (Webinar Builder Lead + 10 sub-agents)

---

## Step 13 Combined Agent Count

| Agent | Sub-Agents | Total |
|---|---|---|
| Funnel Builder Lead | 9 | 10 |
| Webinar Builder Lead | 10 | 11 |
| **Step 13 Total** | | **21** |

---

## Inputs — What Both Agents Read

| Document | Key Sections | Why |
|---|---|---|
| Expert Dossier Brief | Offer Architecture (all tiers, value stack, guarantee), Avatar Psychology (false beliefs, objections, awareness level), Webinar Raw Material (One Big Domino, 3 secrets raw, origin story), Proof Bank (top 3 stories), Voice DNA | All funnel copy and webinar content |
| Brand North Star Part 2 | ALWAYS/NEVER rules, One Big Domino (locked), mechanism, proof anchors, voice standard examples | Quality guardrail for every word written |
| Growth Blueprint | Funnel variant selected for this expert, avatar awareness level, webinar strategy (live/evergreen), tech stack | Which pages to build + how to structure them |
| Monthly Messaging Brief | Hook bank, objection library, social proof deployment map | Specific angles and proof deployment |
| Silent Diagnosis payload | Offer gaps, proof bank depth, compliance rules | Flags thin proof, identifies compliance risks before build |

---

## Outputs — What Gets Delivered

**Funnel Builder delivers:**
- All funnel pages live at URLs, mobile-optimized, integrated, QA-passed
- A/B variants for opt-in page and order page headlines
- Funnel flow map in expert dashboard
- Pre-launch checklist (all items must be green before traffic is sent)
- Page performance benchmarks loaded into Analytics Dashboard

**Webinar Builder delivers:**
- Live webinar script (full length, both formats)
- VSL/evergreen script (word-for-word, production-ready)
- 5+ webinar angle and title options (expert selects before scripts are produced)
- Complete slide deck (PDF + PNG sequence + HTML)
- Q&A objection script
- Follow-up email trigger brief (routed to Email Builder Agent, Step 14)

---

*Step 13 of 22 — Funnel Builder Agent + Webinar Builder Agent — v1.0 Draft*
*Next: Step 14 — Email & SMS Builder Agent*
