# clinicIQ — Layer 3: Builder Agents — Step 12: Content Builder Agent
**Version 1.1 — Revised**
*Step 12 of 22 | Depends on: Steps 1–11 (Layers 1 & 2 complete)*

---

## Purpose

The Content Builder Agent is the production engine of clinicIQ. It takes everything the Onboarding Agent captured and everything the Strategy Layer architected and turns it into finished, premium, publish-ready creative assets — images with text burned in, multi-slide carousels, b-roll with text overlays, video scripts, UGC character scripts, and captions — all in the expert's exact voice, brand aesthetic, and strategic framework.

This is not a brief generator. It does not produce prompts for the expert to take elsewhere. Every asset exits this agent completed, composited, platform-optimized, and stored in the expert's Asset Library. The expert opens clinicIQ, requests a batch or a one-off, and receives finished work. Nothing about this process requires leaving the platform.

The Content Builder operates in two modes: **Batch Mode** (producing a full week or month of content in one session) and **Quick-Create Mode** (producing a single asset from a natural language request). Both modes use the same sub-agent team. The workflow is abbreviated in Quick-Create, not different in kind.

---

## The Fundamental Production Architecture

### Why This Architecture Exists

The single hardest problem in AI-generated content is text on images. Every major image generation model — Flux, Midjourney, DALL-E, Stable Diffusion — produces garbled, malformed, or unreliable text when asked to render words on images. This is a known, persistent limitation of diffusion-based models and it cannot be prompted around.

The clinicIQ Content Builder solves this with a three-stage production pipeline that treats every image and carousel slide exactly the way Genspark generates slides — as **code that gets rendered into a visual**.

**Stage 1 — Background Image Generation:** Flux Pro 1.1 generates the background scene, lifestyle image, or visual concept only. No text. No UI elements. Just the image. This gets returned as a URL.

**Stage 2 — HTML/CSS Layout Generation:** The AI writes a complete HTML/CSS document for the asset — headlines, body copy, CTAs, layout structure, brand colors, typography, gradients, overlays, and the Flux-generated image embedded as a CSS background or `<img>` element. This is the same approach Genspark uses to produce slides: code defines the design, the browser renders it perfectly. The AI has full creative latitude here — it is not filling zones in a rigid grid. It designs a layout that fits the content, the template style, and the brand aesthetic. Typography is handled by CSS (perfect at any weight, size, or spacing). Gradients, shadows, overlays, and visual treatments are all native CSS. Any design that can be expressed in code can be produced here.

**Stage 3 — Headless Browser Rendering:** A headless Chromium instance (Puppeteer) loads the HTML document and screenshots it at the exact target pixel dimensions — 1080×1350, 1080×1080, 1080×1920, or any required spec. The output is a pixel-perfect PNG at production resolution.

**The result:** Images and carousel slides that look like they were designed by a brand studio. Typography is flawless. Layout is intentional. Brand colors and fonts are exact. Every element is precisely positioned. The AI designed it. The browser rendered it. There is no quality ceiling imposed by an image compositor's limitations.

This approach produces output that is architecturally superior to template-based compositors (Sharp.js, Canva-style systems) because the AI is not constrained to filling fixed zones. It designs. The renderer just executes what the AI designed.

---

## Platform Specifications — Non-Negotiable Standards

Every asset produced by the Content Builder is sized and formatted to exact platform specifications. No approximations. These values are hardcoded into the production pipeline.

### Instagram
| Format | Dimensions | Ratio | Notes |
|---|---|---|---|
| Feed — Portrait | 1080×1350px | 4:5 | **Default for all IG feed posts — maximum reach** |
| Feed — Square | 1080×1080px | 1:1 | Used when content requires square format |
| Reels / Stories | 1080×1920px | 9:16 | All short-form video and b-roll |
| Carousel slides | 1080×1350px | 4:5 | Consistent across all slides in a set |

### Facebook
| Format | Dimensions | Ratio | Notes |
|---|---|---|---|
| Feed post | 1080×1080px | 1:1 | Standard FB feed |
| Link share | 1200×628px | 1.91:1 | Auto-applied when post includes a URL |
| Reels / Stories | 1080×1920px | 9:16 | All short-form video |
| Carousel slides | 1080×1080px | 1:1 | FB carousel standard |

### Meta Ads
| Format | Dimensions | Ratio | Notes |
|---|---|---|---|
| Feed ad | 1080×1080px or 1080×1350px | 1:1 or 4:5 | Ad-optimized versions |
| Story ad | 1080×1920px | 9:16 | |
| Carousel ad | 1080×1080px | 1:1 | Per card |

**Safe zone rule:** All critical visual elements and text are kept within the center 80% of the frame on every asset. Content that bleeds to the edge on any format is flagged by the compositor as a layout violation and corrected before delivery.

**Dual-platform output:** When an asset is designated for both IG and FB, the compositor produces both versions at the correct dimensions in a single production pass.

---

## Batch Mode — Full Content Production

### Default Batch Configuration

The default batch is **40 assets** in the following preset mix, adjustable by the expert:

| Asset Type | Default Count | Notes |
|---|---|---|
| Static images | 10 | Full mix of image template types |
| Carousels | 10 | 6–10 slides each |
| B-roll with text overlay | 10 | Short-form video: 15–60 seconds |
| Video/UGC scripts | 10 | Full scripts with director notes |
| **Total** | **40** | All with captions and copy |

Every asset in every batch is delivered with:
- The finished visual asset (image, carousel file, video or video-ready b-roll, formatted script)
- Full caption copy (hook line, body, CTA — platform-optimized)
- Hashtag set (niche-specific, 5–10 per post)
- Platform designation (IG, FB, or both)
- Awareness level tag (Level 1–5)
- Hook angle tag (from the active hook bank)
- CTA type tag (for performance tracking)
- Ad candidate flag (if eligible — see Ad Testing Layer)
- Calendar slot assignment (from Monthly Master Plan)

---

## The Content Ideation System — Core and Bridge Topics

### The Three-Level Topic Expansion Model

The Content Builder does not generate content only about the expert's core clinical topic. That approach produces a content library that feels narrow, repetitive, and eventually exhausted. The world's best health content brands — Huberman Lab, Dr. Mark Hyman, Dr. Josh Axe — publish relentlessly because they operate on a multi-level topic expansion model. clinicIQ builds this in from the start.

The Content Ideation Engine generates ideas across three levels:

**Level 1 — Core Topic Content (direct)**
Content that is explicitly about the expert's primary specialty. For a hormone expert: hormones, thyroid, cortisol, estrogen, testosterone, HRT, menopause, etc.
*This is always the foundation. Never less than 40% of any batch.*

**Level 2 — Adjacent Bridge Content**
Topics that have a clear, documentable physiological or lifestyle connection to the core specialty. For a hormone expert: gut microbiome (gut-hormone axis), sleep (cortisol regulation), stress (adrenal-thyroid connection), blood sugar (insulin-hormone relationship), inflammation (immune-endocrine interaction).
*The bridge is always explicit — the content explains the connection and routes back to the core.*

**Level 3 — Stretch Bridge Content**
Topics that seem unrelated on the surface but have an engineered, compelling bridge to the core specialty. For a hormone expert: sauerkraut (fermented food → gut bacteria → gut-hormone axis → hormones), red wine (alcohol → estrogen metabolism → hormonal disruption), Monday morning fatigue (cortisol rhythm → adrenal output → thyroid function), travel stress (jet lag → circadian disruption → cortisol → downstream hormones), holiday eating (blood sugar spikes → insulin → estrogen dominance → symptoms).

**The bridge rule:** Every Level 3 piece must contain a bridge that is scientifically valid, specific enough to be interesting, and routes naturally to the lead magnet or core offer at the CTA. The bridge is never a stretch that sounds made up. If the connection isn't real, the topic isn't used.

*Stretch bridge content makes the expert's feed feel smart, surprising, and endlessly fresh. Audiences who came for hormones stay because the expert makes everything feel relevant to their life.*

### Innovation Ratio

| Content Level | Default % of Batch | Expert-Adjustable Range |
|---|---|---|
| Level 1 — Core | 40% | 30–70% |
| Level 2 — Adjacent | 30% | 20–50% |
| Level 3 — Stretch Bridge | 30% | 5–50% |

The 30% stretch bridge preset is the minimum recommended to keep content feeling dynamic and reach new audience segments. Experts who have large, highly-engaged existing audiences may want to increase this. Experts early in their growth with a cold audience should keep it closer to 40% core.

---

## Awareness Level Distribution — The Full-Funnel Content Engine

Every batch is engineered to feed all five levels of avatar awareness simultaneously. This is what separates clinicIQ content from generic content tools — every month, the expert is attracting brand-new cold audiences AND moving warm audiences toward conversion AND converting ready buyers, all through organic content.

### Default Awareness Distribution

| Awareness Level | Default % | Content Role | Primary Hook Style |
|---|---|---|---|
| Level 1 — Unaware | 15% | Broad reach; names a problem the avatar has but hasn't connected to the expert's specialty | Lifestyle, curiosity, universal pain |
| Level 2 — Problem Aware | 30% | Primary acquisition layer; avatar knows they have the problem, doesn't know the solution | Pain-specific, validation, "I see you" |
| Level 3 — Solution Aware | 25% | Differentiation layer; avatar is comparing options; introduces mechanism | Mechanism, myth-busting, new vehicle |
| Level 4 — Product Aware | 20% | Conversion layer; avatar knows the expert, needs proof and a reason to act | Transformation stories, proof, urgency |
| Level 5 — Most Aware | 10% | Direct action layer; ready buyers need a clear CTA and a clean path | Direct offer, testimonial, scarcity |

The Awareness Level Distributor sub-agent maps each idea from the ideation output to its target awareness level, ensuring the final batch hits the distribution before production begins. If the ideation output is skewed (too many Level 2 ideas, not enough Level 4), the distributor flags it and the Ideation Engine generates additional ideas to fill the gap.

This distribution is adjustable. An expert running a major webinar launch this month may want to shift toward Level 4–5 for the launch window. The default resets after the campaign period.

---

## Asset Types — Full Production Specifications

### 1. Static Images

**Purpose:** Single-frame visual content for feed posts. The highest-volume format. Designed for maximum reach on first scroll, saves for educational content, and shares for resonant content.

**Template Library — Image Types:**
The Template Manager maintains all of the following template structures. Each template defines the layout grid, text zone positions, image zone, logo placement, and color treatment.

| Template Name | Layout | Best Use | Primary Engagement Goal |
|---|---|---|---|
| **Bold Statement** | Full-bleed image, single headline, minimal text | High-conviction claims, One Big Domino reinforcement | Shares, comments |
| **Quote Pull** | Expert photo or lifestyle image, large quote text, expert attribution | Voice-building, authority, personality | Saves, shares |
| **Stat Spotlight** | Number dominant (large, bold), 1–2 lines of context, source attribution | Data-backed claims, credibility | Saves, comments |
| **Old Way / New Way** | Split layout (left/right or top/bottom), two-column contrast | Mechanism introduction, differentiation | Saves, shares |
| **Myth vs. Truth** | Red/green or contrast treatment, myth struck through, truth revealed | Belief shifting, contrarian hooks | Shares, comments |
| **X Signs You Have Y** | List format, numbered, tease 3–5 items | Curiosity + identification | Saves, profile visits |
| **Mechanism Diagram** | Clean visual explanation, minimal text, clear visual hierarchy | Educational authority, mechanism demonstration | Saves, shares |
| **Transformation Teaser** | Before/after framing (mindset or physical), proof element | Social proof, avatar identification | Comments, profile visits |
| **Hook + Lifestyle** | Strong lifestyle image, single scroll-stopping headline | Top-of-funnel reach, Level 1–2 audience | Follows, reach |
| **Bridge Builder** | Core visual + bridge topic visual element, connection text | Level 1–2 stretch bridge content | Reach, curiosity clicks |

**Image generation approach:**
The Visual Direction sub-agent writes a detailed image generation prompt for the background/scene only — no text, no UI elements. The prompt specifies:
- Subject and setting (avatar-demographic specific, not stock-photo perfect)
- Lighting and color palette (from Visual DNA)
- Emotional state and body language
- Photography style (from Visual DNA `photography_style` field: clinical, lifestyle, documentary, editorial)
- Explicit exclusions: stock photo style, overly polished, generic wellness imagery, unrealistic perfection

The Image Production sub-agent calls Flux Pro 1.1 (primary) via fal.ai API. Flux is selected because it produces the most photorealistic, authentic-feeling lifestyle imagery of any current model — critical for health content where trust and authenticity are the primary purchase drivers.

The HTML/CSS Layout Generator receives the base image URL, the copy, and the template style, then writes a complete HTML/CSS document — embedding the image, designing the layout, applying brand typography, colors, and treatment. Puppeteer renders it to a pixel-perfect PNG at the correct platform dimensions.

**Caption structure (every static image):**
- Hook line (first 1–2 sentences — must work as a standalone hook before "more" truncation)
- Body (2–5 sentences — value, mechanism brief, or story)
- Bridge (1 sentence connecting to the core specialty for Level 2–3 stretch content)
- CTA (from the active CTA rotation in the Monthly Messaging Brief)
- Hashtags (5–10, niche-specific)

---

### 2. Carousels

**Purpose:** Multi-slide content for deep educational value, high-save content, and the most effective organic conversion format. Carousels keep users swiping and signal algorithm value through extended engagement time. The best-performing organic conversion format on Instagram.

**Slide count:** 6–10 slides per carousel. The first slide is the hook. The last slide is the CTA. Every middle slide delivers one unit of value.

**The "how-to stops at step 2" rule:** Carousels that deliver a complete how-to give away the result without creating a reason to go deeper. clinicIQ carousels teach the *why* and the *what* — making the problem and the mechanism clear — while routing the *how* (the full protocol, the step-by-step) to the lead magnet or recorded webinar. This is not artificial withholding. It is correct information architecture: organic content builds belief, premium content delivers transformation.

**Carousel Template Library:**

| Template Name | Arc | Slides | Best Use |
|---|---|---|---|
| **Problem → Mechanism → Solution** | Educational narrative | 7–9 | Core mechanism introduction, root cause content |
| **X Things You Didn't Know** | Curiosity list | 6–10 | Surprising insights, Level 1–2 reach |
| **Old Way vs. New Way** | Contrast reveal | 7–8 | Belief shifting, differentiation, Level 2–3 |
| **How-To Teaser** | Steps 1–2 shown, rest gated | 6–8 | Lead magnet bridge, Level 3 |
| **Myth Buster Series** | One myth per slide | 6–10 | Contrarian authority, Level 2–3 |
| **Patient Story Arc** | Before → journey → result | 7–9 | Social proof, Level 4 |
| **This or That** | Binary comparison per slide | 6–8 | Engagement driver, shares |
| **The Research Breakdown** | One study → what it means for the avatar | 7–9 | Deep authority, Level 3–4 |
| **Bridge Builder Carousel** | Stretch topic → connection slides → core specialty CTA | 7–9 | Level 1–2 reach with organic funnel routing |

**Slide-by-slide production standard:**
Every carousel slide is produced as a finished rendered image — background generated by Flux, entire slide layout written as HTML/CSS and rendered via Puppeteer. Font, color, and layout are visually consistent across all slides in a set (enforced in the shared CSS). Slide numbers and swipe-progress indicators are included when the template supports them (drives "keep swiping" behavior). Because each slide is HTML, the AI can design different layouts per slide within the same visual system — a cover slide can be full-bleed image with minimal text, a content slide can be split-layout, a CTA slide can be text-dominant — without being forced into one rigid grid.

**Carousel caption structure:**
- Hook line (builds curiosity for slide 1)
- "Swipe through" instruction with a specific reason ("Swipe through — slide 4 is the one most people get completely wrong")
- Brief value statement
- CTA at the end (always pointing to the next step — lead magnet, webinar, or follow)

---

### 3. B-Roll with Text Overlay

**Purpose:** Short-form video content (15–60 seconds) using cinematic b-roll footage as the visual base with text appearing sequentially over it. This format dominates Reels and TikTok because it combines motion (algorithm-favored) with educational text (saves-favored) and works with sound off. It is the most scalable video format — no expert face time required unless desired.

**Production approach:**
The b-roll visual is generated using Kling v1.6 (cinematic quality, smooth motion, accurate subject rendering) or Runway Gen-3 (for more stylized or abstract concepts). The b-roll prompt specifies the visual scene only — no text, no UI elements. Text overlays are handled as a separate layer: the HTML/CSS Layout Generator produces a sequence of timed overlay frames (transparent-background HTML renders) which are composited onto the video track. Each overlay frame is Puppeteer-rendered using the same brand typography and color system as static images, then merged with the video at the specified timestamps.

**Text overlay structure (follows scroll-stopping framework):**

| Time Stamp | Text Layer | Purpose |
|---|---|---|
| 0:00–0:03 | Hook text — large, bold, centered | Stop the scroll |
| 0:03–0:08 | Bridge text — problem or "I see you" line | Hold attention |
| 0:08–0:25 | Value text — broken into 2–4 short lines appearing sequentially | Deliver insight |
| 0:25–0:45 | Proof/deepening text | Build belief |
| 0:45–0:60 | CTA text | Drive action |

**Audio direction:** Every b-roll piece includes an audio recommendation — music mood, tempo, and whether a voiceover is included. When voiceover is specified, the Script Formatter produces the voiceover copy at the same time as the text overlay content.

**Dimensions:** Always 1080×1920px (9:16) for Reels and Stories. A 1:1 version is produced simultaneously for feed repurposing.

---

### 4. Video Scripts and UGC Character Scripts

**Purpose:** Full production-ready scripts for: (a) expert-recorded direct-to-camera videos, (b) AI avatar UGC-style videos using HeyGen or equivalent, and (c) concept scripts for b-roll with voiceover.

The distinction between these two modes is captured in the expert's dossier:
- **Expert has real recording setup** → Script optimized for direct-to-camera delivery, with performance notes and visual direction for the expert
- **Expert using AI avatar** → Script optimized for AI avatar delivery, with character consistency notes referencing the stored avatar profile

**Script structure — every script:**

```
[SCRIPT ID: SCR-XXX]
[Platform: IG Reels / TikTok / FB / YouTube Shorts]
[Duration: 15s / 30s / 60s / 3–7 min]
[Format: Direct-to-camera / AI Avatar / Voiceover B-roll]
[Awareness Level: 1–5]
[Hook Angle: from hook bank]
[CTA Type: from CTA rotation]

--- HOOK (0–3 sec) ---
[Exact spoken words]
[Visual direction: what the talent/avatar is doing on camera]

--- BRIDGE (3–15 sec) ---
[Exact spoken words]
[Visual direction]

--- VALUE BODY ---
[Full script broken into spoken lines]
[Stage directions and visual cues where relevant]
[B-roll cut suggestions where applicable]

--- CTA (final 5 sec) ---
[Exact spoken words]
[Visual direction for CTA delivery]

--- CAPTION ---
[Full caption written out — same hook-bridge-value-CTA structure]

--- DIRECTOR NOTES ---
[Energy direction, pacing notes, key words to emphasize, what not to do]
```

**Script types — all of the following are produced in every batch rotation:**
1. Problem/agitation → mechanism reveal → CTA
2. Contrarian hot take → proof → explanation → CTA
3. Story arc → lesson → bridge to mechanism → CTA
4. List format → expanded insight per item → CTA
5. "The thing nobody tells you about [topic]" → reveal → mechanism → CTA

**UGC Avatar consistency:**
For experts using AI avatars, the Avatar Profile is stored in the Asset Library — avatar ID, visual style, speaking style notes, any platform-specific avatar variants. Every script references the avatar profile by ID so HeyGen (or equivalent) always renders the same character. Experts can maintain multiple avatars: their own face (cloned via HeyGen), a patient character avatar, or a custom brand character.

---

## The Ad Testing Layer — Organic Content as Paid R&D

Every batch is designed to double as a paid ad testing ground. The Ad Candidate Tagger sub-agent evaluates every finished asset against the following criteria and flags eligible pieces:

**Ad candidate criteria:**
- Hook is a Priority tier hook from the active hook bank (not a lower-priority angle)
- Format is proven in paid placement: 1:1 or 4:5 static, or short-form video under 30 seconds
- CTA is conversion-oriented (lead magnet download, webinar registration, paid assessment booking) — not a pure engagement CTA
- No compliance violations that would prevent paid amplification
- Awareness level is 2, 3, or retargeting (Level 4) — Level 1 and Level 5 are rarely efficient in paid

**Ad candidate output:**
Flagged pieces are produced in two versions in a single pass:
1. **Organic version** — full caption with engagement CTA, hashtags, organic formatting
2. **Ad-optimized version** — tighter copy, conversion CTA only, no hashtags, headline optimized for above-the-fold truncation in feed placement, primary text ≤125 characters where possible

Ad-optimized versions are stored separately in the Asset Library under the "Ad Candidates" folder, ready to pull directly into Meta Ads Manager.

**Compliance filter — active on all copy:**
The compliance filter runs on every piece of copy before the asset is finalized. It is calibrated to the expert's specialty and the compliance rules captured in the Silent Diagnosis payload. For health experts, this means:
- No disease treatment claims in paid-eligible copy ("cures," "treats," "reverses" in the context of diagnosed conditions)
- FTC-compliant result language ("in my patients," "results may vary," "when combined with lifestyle changes")
- Platform-specific restrictions (Meta has additional restrictions on health condition targeting and certain health claim language)

Any copy that fails the compliance filter is flagged with the specific violation and a suggested rewrite before the asset is finalized. It does not block production — it flags and routes to the expert for approval on the specific piece.

---

## Quick-Create Mode — The One-Off Request

When an expert types a natural language request in the clinicIQ chat interface — "Create a Valentine's Day image for my hormone program" or "I need a carousel about sleep and cortisol for tomorrow" — the Content Builder enters Quick-Create Mode.

**How it works:**

The Content Builder Lead parses the request and identifies:
- Asset type (image, carousel, b-roll, script)
- Topic (explicit from request or inferred)
- Occasion/context (holiday, launch, trend, evergreen)
- Any specific instructions in the request

The Lead auto-populates the brief from the expert's dossier:
- Voice DNA applied automatically
- Visual DNA applied automatically
- Avatar context applied automatically
- Platform defaults applied (IG 4:5 primary)
- Brand templates selected automatically

The sub-agent team runs an abbreviated workflow — no batch ideation or awareness distribution needed. Single asset path:
**Intent parsed → Brief auto-filled → Copy written → Voice QA → Visual directed → Image generated (Flux) → HTML/CSS layout written → Puppeteer renders PNG → Brand QA → Asset Library → Delivered in chat**

Total time target: under 90 seconds for a static image or carousel. Under 3 minutes for a b-roll piece. Scripts are delivered as text immediately.

**The delivered asset appears in chat as a preview with:**
- The finished image/carousel/script
- The caption copy
- A one-click "Save to Library" button
- Options: "Edit this" / "Regenerate" / "Create a variation"

The expert never leaves the platform to complete, edit, or store the asset.

---

## The Asset Library

Every finished asset — batch or one-off — is stored in the expert's Asset Library. The Asset Library is the single source of truth for all content the expert has ever produced in clinicIQ.

**Library organization:**
- By asset type (Images / Carousels / B-Roll / Scripts)
- By content status (Draft / Ready to Post / Scheduled / Posted / Ad Candidate / Archived)
- By platform (IG / FB / Both)
- By awareness level
- By content pillar
- By hook angle
- By date produced

**In-library editing:**
Every asset in the library is editable without leaving clinicIQ:
- **AI chat edit:** Expert types "make the headline more direct" or "change the CTA to drive to my masterclass" → the copy layer is regenerated and recomposited in under 60 seconds
- **Manual editor:** Direct manipulation of text, color, layout positioning within the platform's visual editor (Fabric.js or equivalent canvas editor embedded in the UI)
- **Regenerate background:** Keep the template and copy, generate a new background image with one click
- **Resize for platform:** One-click resize to any platform specification from a produced asset

**Performance data integration:**
Once assets are posted, engagement data feeds back to the Asset Library from connected social accounts. Each asset receives a performance score. This data is consumed by the Performance Learning Agent to update content production priors over time.

---

## Voice and Brand Lock System

This is the most critical quality control in the entire Content Builder. Every asset that exits this agent must be indistinguishable from content the expert themselves would produce at their best — their voice, their aesthetic, their positioning, their standards.

### Voice QA — Copy Layer

The Voice QA Agent runs on every piece of copy before it passes to visual production. It checks against:

**Positive criteria (must be present):**
- Sentence rhythm matches Voice DNA pattern (short/punchy vs. long-form vs. mixed)
- Vocabulary register matches (clinical-accessible vs. street-casual vs. professional warmth)
- Any confirmed signature phrases used where contextually appropriate
- Emotional register consistent with expert's captured style (warm, analytical, direct, humorous)
- Hook style matches approved hook frameworks from Brand North Star

**Negative criteria (must be absent):**
- Any word or phrase on the expert's prohibited list
- Corporate or transactional language ("optimize your wellness journey," "holistic approach to health")
- Generic motivational content disconnected from the mechanism
- Any claim that violates the compliance filter for this expert's specialty
- Passive voice in hooks or CTAs

**Failure behavior:** Copy that fails Voice QA is not discarded — it is rewritten by the Copy Writer sub-agent with the specific failure reason passed as context. The revision cycle runs until the copy passes or until two consecutive failures trigger a human review flag in the expert's dashboard.

### Brand QA — Visual Layer

The Brand QA Agent runs a final check on every finished composite asset:

- Brand colors match Visual DNA hex values (no approximation)
- Font family matches Visual DNA specification
- Logo placement is in the designated zone at the correct size
- Image aesthetic matches Visual DNA photography style and mood
- Text hierarchy is correct (headline dominant, body supporting, CTA clear)
- No visual element conflicts with the brand position (dark, clinical imagery for a warm, accessible brand = flag)

**Three-strike rule:** Any asset that fails Brand QA twice is flagged in the expert's dashboard as "Needs Your Eye" — not discarded, but held for the expert to make a judgment call. This prevents infinite regeneration loops while maintaining quality standards.

---

## Content Learning and Improvement System

The Content Builder gets smarter over time. This is not a one-time calibration — it is a continuous improvement system that makes every subsequent batch better than the last.

The Performance Learning Agent receives the following data from the Analytics Dashboard (Layer 4):
- Engagement rate per post (likes + comments + shares + saves ÷ reach)
- Save rate (strongest signal for educational content quality)
- Share rate (strongest signal for emotional resonance)
- Comment rate and comment sentiment
- Follow rate (how many followers came from each specific piece)
- Profile visit rate
- CTA click rate (link in bio, keyword trigger responses, DM volume)
- Ad performance when organic pieces are promoted (CPL, CTR, conversion rate)

**What the learning agent updates:**

| Signal | Update Target |
|---|---|
| High save rate on specific template type | Increases that template's priority in future batches |
| High share rate on specific hook angle | Elevates that hook angle in the hook bank scoring |
| High comment rate on specific awareness level | Adjusts awareness distribution toward that level |
| High follow rate on specific content pillar | Increases pillar weight in ideation |
| High ad performance on promoted organic pieces | Flags that hook/format combination as a top ad creative archetype |
| Low engagement on stretch bridge topics | Reduces frequency of that bridge; tries different bridge angles |
| Expert editing the same element repeatedly | Updates Voice DNA or Visual DNA with the pattern — three consistent edits in one direction = a preference signal |

**The improvement compounds.** By month 3, the Content Builder is producing content calibrated to this expert's specific audience's behavior — not generic best practices but data-proven preferences from their actual followers. By month 6, it is producing content that consistently outperforms what any human content team could produce without this data infrastructure.

---

## The Sub-Agent Team — Content Builder

```
CONTENT BUILDER LEAD AGENT
├── Reads: Expert Dossier Brief + Brand North Star Part 2 + Monthly Messaging Brief + Monthly Master Plan
├── Determines: Batch config, awareness distribution, innovation ratio, asset mix
├── Orchestrates: All 12 sub-agents below
└── Delivers: Completed asset batch to Asset Library + summary to expert

SUB-AGENTS:

1. Content Ideation Engine
   Generates full topic idea map across Level 1/2/3 bridge categories
   Input: Expert niche, avatar profile, awareness distribution targets, Monthly Master Plan angles
   Output: Categorized idea list with bridge logic for every non-core topic

2. Awareness Level Distributor
   Maps every idea to a target awareness level
   Validates batch hits the distribution targets before production begins
   Flags gaps and requests additional ideation if needed

3. Copy & Script Writer
   [Merged: Copy Writer + Script Formatter]
   Writes all copy: headlines, captions, hook lines, CTAs, carousel slide text,
   video script body, b-roll text overlay sequences, voiceover scripts
   Operates from the Monthly Messaging Brief hook bank and angle map
   Never invents hooks from scratch — always pulls from the hook bank
   Also formats all video and UGC scripts into the standard production template:
   adds director notes, performance cues, shot direction
   Distinguishes between direct-to-camera and AI avatar delivery modes
   References the expert's stored avatar profile ID for AI avatar scripts
   Natural sequential flow: write copy → format scripts runs in single creative context with no domain shift

4. Voice QA Agent
   Reviews all copy against Voice DNA sample extracts
   Applies compliance filter for expert's specialty
   Passes or rewrites — never blocks production, always resolves

5. Visual Production Agent
   [Merged: Visual Direction Agent + Image Production Agent]
   Writes detailed image generation prompts for every visual asset — background/scene only, no text, no UI elements
   Applies avatar demographic specificity, brand aesthetic, photography style from Visual DNA
   Explicitly excludes stock-photo style and generic wellness imagery
   Then executes production directly from its own prompts:
   Calls Flux Pro 1.1 (fal.ai API) for lifestyle and editorial imagery
   Calls Kling v1.6 for cinematic b-roll video generation
   Calls Runway Gen-3 for stylized or abstract b-roll
   Tool selection is automatic based on asset type — modular by design
   Natural sequential flow: direction → production runs in single context with no domain shift

6. HTML/CSS Layout Generator + Renderer
   Receives: base image URL (from Visual Production Agent) + copy (from Copy & Script Writer) + template style + Visual DNA
   Writes a complete HTML/CSS document for the asset — layout, typography, color treatment, image embedding, overlays, brand elements
   AI has full design latitude within brand guardrails — not filling fixed zones, actually designing the layout for the content
   Passes the HTML document to the Puppeteer Renderer, which screenshots it at exact platform dimensions
   Output: finished PNG at production resolution, pixel-perfect

8. Template Manager
   Maintains the expert's HTML/CSS base template library (not rigid image grids — flexible code structures)
   On first run: generates brand base templates from Visual DNA (colors, fonts, photography style, aesthetic keywords)
   On subsequent runs: selects the correct template style for each content type — Layout Generator customizes within it
   Tracks template performance scores from the Performance Learning Agent

9. Carousel Builder
   Assembles multi-slide carousels from individual slide outputs
   Ensures visual consistency across all slides (layout, color, typography)
   Manages slide numbering and swipe-progression cues
   Produces carousel as a packaged set of images ready for upload

10. Publishing Prep Agent
    [Merged: Ad Candidate Tagger + Content Scheduler]
    Post-production metadata layer — runs after Brand QA clears an asset
    Ad candidate evaluation: assesses every finished asset against ad candidate criteria,
    produces ad-optimized copy variant for flagged pieces, runs compliance check on all
    ad candidate copy, organizes ad candidates in their designated Asset Library folder
    Then schedules: maps all finished assets to calendar slots from the Monthly Master Plan,
    tags each asset with platform, date, hook angle type, CTA type
    Produces the month's content calendar view in the expert's dashboard
    Both tasks are pure metadata/organization work — no copy generation, no visual production —
    context carries cleanly from evaluation to scheduling with no domain conflict

11. Asset Library Manager
    Receives all finished assets from the production pipeline
    Organizes by type, status, platform, awareness level, pillar, hook angle, date
    Maintains the tagging and searchability of the library
    Flags assets that need expert review (Brand QA three-strike holds)

12. Brand QA Agent
    Final quality gate before any asset reaches the library
    Checks: brand colors, fonts, logo, visual aesthetic, text hierarchy, brand positioning
    Three-strike rule: two failures → "Needs Your Eye" flag in dashboard
    Never blocks — always routes, either to library or to expert review

13. Performance Learning Agent
    Receives engagement data from connected social accounts via Analytics Dashboard
    Updates template performance scores, hook angle rankings, awareness level distribution preferences
    Feeds updated priors to the Ideation Engine and Template Manager for next batch
    Tracks expert editing patterns and updates Voice DNA / Visual DNA when patterns are confirmed
```

**Agent count: 13** (Content Builder Lead + 12 sub-agents — merged from 16; 3 merges: Visual Direction + Image Production → Visual Production Agent; Copy Writer + Script Formatter → Copy & Script Writer; Ad Candidate Tagger + Content Scheduler → Publishing Prep Agent)

---

## Tool Stack — Content Builder

| Tool | Purpose | API/Integration | Why This Tool |
|---|---|---|---|
| **Flux Pro 1.1** (fal.ai) | Lifestyle and editorial image generation | fal.ai API | Best photorealism for health content. Authentic, non-stock aesthetic. Fast. Reliable API. |
| **Kling v1.6** | Cinematic b-roll video generation | Kling API / via gsk | Best cinematic motion quality. Smooth subject rendering. Ideal for health lifestyle b-roll. |
| **Runway Gen-3** | Stylized/abstract b-roll | Runway API | Handles stylized or conceptual visuals Kling doesn't execute as well |
| **HeyGen** | AI avatar talking head / UGC video | HeyGen API | Industry standard for avatar consistency. Custom voice cloning. Best UGC-style output. |
| **Puppeteer + Headless Chromium** | HTML/CSS → PNG rendering | Node.js library (backend) | Screenshots pixel-perfect renders of AI-generated HTML layouts at exact platform dimensions. Perfect typography, full CSS support, unlimited layout flexibility. Same approach Genspark uses to render slides. |
| **Fabric.js** | In-platform manual editor (canvas editor) | JavaScript library (frontend) | Enables drag-and-drop editing of any asset within clinicIQ UI — expert never leaves the platform |
| **Genspark image gen** | Rapid ideation and supplementary generation | gsk CLI / Genspark API | Fast iteration, native platform integration. Secondary tool for quick supplementary generation |
| **Google Fonts / Brand Font CDN** | Typography in compositor | CDN | Ensures brand-accurate font rendering at all sizes and weights |

**Tool modularity principle:** Every external tool is called through an abstraction layer. If Flux is replaced by a superior model in 6 months, only the Image Production Agent's tool call changes — nothing else in the pipeline changes. The architecture is future-proofed by design.

---

## Content Builder — Input Requirements

| Document | Key Sections Read | Why |
|---|---|---|
| Expert Dossier Brief | Voice DNA (all fields + sample extracts), Visual DNA, Avatar Psychology, Offer Architecture, Proof Bank | Production calibration for every asset |
| Brand North Star Part 2 | ALWAYS/NEVER rules, One Big Domino, content pillars, voice standard examples, proof anchors | Quality guardrails for all copy and visual direction |
| Monthly Messaging Brief | Hook bank, angle map, objection library, emotional beat sequence, proof deployment map | Specific creative direction for this batch |
| Monthly Master Plan | Content calendar, primary CTA, webinar details, asset build queue | Scheduling and CTA alignment |
| Asset Library performance data | Template scores, hook angle rankings, awareness distribution preferences | Batch calibration from historical performance |
| Silent Diagnosis payload | Compliance rules, offer gaps flagged | Compliance filter + strategic prioritization |

---

## Content Builder — Output

Every batch produces:

1. **Finished assets** — all composited images, carousel sets, b-roll files, and formatted scripts
2. **Caption library** — all captions organized by asset, ready to copy/paste or push to scheduler
3. **Content calendar** — the month mapped to the asset library with platform, date, and tracking tags
4. **Ad candidate folder** — flagged pieces in both organic and ad-optimized versions
5. **Batch summary** — overview of the batch: topic coverage, awareness distribution achieved, hook angles used, CTA types used, bridge topic coverage, and any "Needs Your Eye" flags

Delivered to:
- **Asset Library** — all finished assets stored and organized
- **Expert dashboard** — batch summary and calendar view displayed
- **Core Orchestrator** — batch completion confirmation and ad candidate list routed to Ad Creative Builder Agent for further development

---

## Quality Standards — What "Premium" Means in clinicIQ

*"No mom and pop shop junk."*

Every finished asset that exits the Content Builder must pass the following standard:

**Would a follower believe this was made by a professional brand studio?**

This means:
- Typography is clean, hierarchical, and purposeful — not cluttered, not oversized, not randomly placed
- Colors are brand-accurate and used with intention — not decorative, not jarring
- Images are emotionally resonant and aesthetically authentic — not stock-photo generic
- Copy is sharp, specific, and in the expert's actual voice — not motivational filler
- Every element is intentional — if it's on the asset, it's there for a reason

The programmatic compositor enforces the layout. The Voice QA Agent enforces the copy. The Brand QA Agent is the final human-standard check. Three independent quality systems ensure every asset earns its place in the expert's brand.

---

*Step 12 of 22 — Content Builder Agent — Knowledge & Skill Description — v1.0 Draft*
*Next: Step 13 — Funnel Builder Agent + Webinar Builder Agent*
