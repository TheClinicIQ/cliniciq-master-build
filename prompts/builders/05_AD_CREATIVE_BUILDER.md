# ClinicIQ — Ad Creative Builder: Complete Build Spec
## Pattern B: Brief → Batch Generate → Grid Review with Performance Prediction
## Modeled after: AdCreative.ai grid + scoring system + Meta Ads Manager preview

---

## WHAT THIS BUILDER DOES

The Ad Creative Builder produces batches of ad creatives for paid campaigns: Meta (Facebook + Instagram), YouTube, TikTok. Each batch includes multiple hook angles × multiple formats, complete with primary text (caption), headlines, descriptions, image/video concepts, and targeting recommendations. Every creative gets a predicted performance score.

---

## THE FLOW

### Phase 1: Brief (IQ Chat)

IQ asks:

1. **"What are we promoting?"** — pills: [Lead Magnet] [Webinar Registration] [Direct Offer] [Retargeting]
2. **"Which platform?"** — [Meta (FB + IG)] [YouTube] [TikTok] [All] — default Meta
3. **"How many creatives?"** — default 9 (3 hook angles × 3 formats). Expert can adjust.
4. **"Cold traffic or retargeting?"** — [Cold] [Retargeting] [Both] — determines messaging angle
5. **"Which avatar?"** — pre-selected

IQ confirms: "Building 9 Meta ad creatives — 3 hook angles (pain, villain, proof) × 3 formats (video, static, carousel). Cold traffic to your Cortisol Assessment opt-in. Let's go."

### Phase 2: Generation (Right Panel — Grid with Scoring)

**Right panel layout:**

**Header:**
- "📢 Ad Creative Builder" (14px, bold) + "Building 9 creatives..." (13px, #6B7280) + spinner
- "5 of 9 complete" + progress bar

**Hook angle tabs:**
Below the header, 3 tabs — one per hook angle:
- [🔴 Pain Hook] [⚔️ Villain Hook] [🏆 Proof Hook]
- Active tab: emerald underline. Each tab shows the creatives for that angle.
- This groups creatives by strategy instead of showing a random grid.

**Creative cards (3 per tab, in a row):**

```
┌───────────────────┐ ┌───────────────────┐ ┌───────────────────┐
│  🎬 Video         │ │  📷 Static Image  │ │  🎠 Carousel      │
│                   │ │                   │ │                   │
│ ┌───────────────┐ │ │ ┌───────────────┐ │ │ ┌───────────────┐ │
│ │  [Video       │ │ │ │  [Image       │ │ │ │  [Slide 1     │ │
│ │   preview]    │ │ │ │   preview]    │ │ │ │   preview]    │ │
│ │               │ │ │ │               │ │ │ │          1/4  │ │
│ └───────────────┘ │ │ └───────────────┘ │ │ └───────────────┘ │
│                   │ │                   │ │                   │
│ Score: 87/100 🟢  │ │ Score: 74/100 🟡  │ │ Score: 91/100 🟢  │
│ ███████████░░     │ │ ██████████░░░░    │ │ ████████████░     │
│                   │ │                   │ │                   │
│ "Your 2pm crash   │ │ "Your 2pm crash   │ │ "5 signs your     │
│  isn't normal..." │ │  isn't normal..." │ │  labs are lying"  │
│                   │ │                   │ │                   │
│ Est. CTR: 2.4%    │ │ Est. CTR: 1.8%    │ │ Est. CTR: 2.7%    │
│ Est. CPC: $1.10   │ │ Est. CPC: $1.45   │ │ Est. CPC: $0.95   │
│                   │ │                   │ │                   │
│ [✅] [✏️] [🔄]   │ │ [✅] [✏️] [🔄]   │ │ [✅] [✏️] [🔄]   │
└───────────────────┘ └───────────────────┘ └───────────────────┘
```

**Creative card elements:**

- **Format label** (top): 🎬 Video / 📷 Static Image / 🎠 Carousel — 12px, bold, #1F2937
- **Visual preview** (40% of card): 
  - Static: AI-generated image preview (4:5 ratio for feed, 9:16 for Stories)
  - Video: dark gradient with 🎬 play icon + script hook text overlaid
  - Carousel: first slide with "1/4" badge
- **Performance Score** (prominent):
  - Score: "87/100" — 16px, bold. Color: emerald (80+), amber (60–79), red (<60)
  - Progress bar below: 3px, colored fill matching score
  - "Predicted by IQ based on your audience data and hook bank performance"
  - This is the killer feature from AdCreative.ai — a predicted conversion score
- **Hook preview**: First line of primary text, 12px, #374151, 2 lines truncated
- **Estimated metrics**: CTR and CPC predictions, 11px, #6B7280
- **Actions**: [✅ Approve] [✏️ Edit] [🔄 Regenerate] — same as Content Builder

**Card dimensions:** 3 cards per row (33% each minus gaps). Height: ~320px.

### Phase 3: Creative Detail View

Clicking [✏️ Edit] opens the **ad creative detail view**.

**Layout:**

**Header:**
- [← Back to batch] + "Pain Hook — Video Creative" (14px, bold)
- Score badge: "87/100 🟢" prominent

**Ad preview (top — styled as a Meta ad):**
A mock Meta ad preview showing exactly how the ad would appear in a Facebook/Instagram feed:

```
┌─────────────────────────────────────────┐
│  [SC] Dr. Sarah Chen · Sponsored        │
│                                         │
│  Your 2pm crash isn't a coffee problem  │
│  — it's a cortisol problem.             │
│                                         │
│  Every afternoon, your body sends a     │
│  signal. Most doctors call it "normal   │
│  fatigue." But there's nothing normal   │
│  about needing caffeine to function...  │
│  [See more]                             │
│                                         │
│  ┌─────────────────────────────────┐    │
│  │                                 │    │
│  │     [Image/Video preview]       │    │
│  │                                 │    │
│  └─────────────────────────────────┘    │
│                                         │
│  signalresethealth.com                  │
│  GET YOUR FREE ASSESSMENT               │
│  ─────────────────────────────────────  │
│  👍 Like    💬 Comment    ↗️ Share       │
│                                         │
└─────────────────────────────────────────┘
```

- Styled to look like an actual Facebook feed post — profile pic, "Sponsored" label, engagement icons
- Shows the ad exactly as the audience would see it

**Below preview — editable fields:**

**Primary Text (caption):**
- Full text editor. The main ad copy that appears above the image.
- Word count + character count (Meta has limits)
- Voice match: "🗣️ 92%"

**Headline:**
- Single line input: "Get Your Free Assessment" (appears below the image in the link preview area)
- Character limit indicator

**Description:**
- Single line: "Discover what's really driving your fatigue — in 3 minutes"

**Image/Video:**
- For static: image preview + image generation prompt (editable) + [Regenerate Image]
- For video: script display (hook/bridge/value/CTA with timestamps) + b-roll directions
- For carousel: slide strip (editable per-slide)

**CTA Button:**
- Dropdown: [Learn More] [Sign Up] [Download] [Book Now] [Get Offer] [Watch More]

**Targeting Recommendation (collapsible):**
- Audience suggestion: "Interests: functional medicine, hormone health, cortisol, chronic fatigue. Age: 35–55. Gender: Female."
- "Based on your avatar Stressed Mom Sarah"
- This is a recommendation — the expert applies it in their actual Meta Ads Manager

**A/B Test Companion (optional):**
- "Want a variant?" [Generate A/B Variant] → produces a variation with a different hook angle or image, shown side-by-side for comparison
- Each variant gets its own performance score

### Phase 4: Batch Complete

All creatives generated:
- IQ: "Your ad batch is ready — 9 creatives across 3 hook angles. The carousel proof hook scored highest at 91/100. I'd start testing with that one."
- **Batch actions:**
  - [Approve All] emerald
  - [Save to Drive] gray outlined
  - [Export for Meta] emerald outlined → downloads a ZIP with: images at correct sizes, video scripts, copy document with all text fields formatted for paste-into-Meta

---

## RETARGETING MODE

When building retargeting ads, the flow is the same but with different hook angles:

| Retarget Tier | Audience | Hook Strategy |
|---------------|----------|---------------|
| Tier 1: Site visitor, no opt-in | Visited but didn't convert | Restate lead magnet + add social proof |
| Tier 2: Opted in, didn't attend | Registered but no-showed | Urgency + replay + what they missed |
| Tier 3: Attended, didn't buy | Watched webinar, no purchase | Objection-specific (price, skepticism, timing) |
| Tier 4: Buyer | Already purchased | Upsell / continuity — NEVER show acquisition ads |

IQ selects the right hook strategy based on the retargeting tier. Each tier gets 3 creatives (one per format).

---

## MOCK DATA

```typescript
const mockAdBatch = {
  campaign: "Cold Traffic — Cortisol Assessment",
  platform: "meta",
  destination: "Opt-in page — Free Cortisol Assessment",
  avatar: "Stressed Mom Sarah",
  hookAngles: [
    {
      angle: "Pain",
      description: "Lead with the daily pain of fatigue — the 2pm crash, the brain fog, the cancelled plans",
      creatives: [
        { id: "a1", format: "video", score: 87, estCTR: 2.4, estCPC: 1.10, status: "approved", hook: "Your 2pm crash isn't a coffee problem — it's a cortisol problem." },
        { id: "a2", format: "static", score: 74, estCTR: 1.8, estCPC: 1.45, status: "draft", hook: "Your 2pm crash isn't a coffee problem — it's a cortisol problem." },
        { id: "a3", format: "carousel", score: 82, estCTR: 2.1, estCPC: 1.20, status: "draft", hook: "5 signs your afternoon crash is more than just tiredness" },
      ]
    },
    {
      angle: "Villain",
      description: "Name the villain — conventional medicine's failure to test properly",
      creatives: [
        { id: "a4", format: "video", score: 79, estCTR: 2.0, estCPC: 1.30, status: "draft", hook: "Your doctor says your thyroid is fine. Here's why they're wrong." },
        { id: "a5", format: "static", score: 71, estCTR: 1.6, estCPC: 1.55, status: "draft", hook: "One test. That's all most doctors run. Here are the 5 they're missing." },
        { id: "a6", format: "carousel", score: 84, estCTR: 2.2, estCPC: 1.15, status: "draft", hook: "'Your labs are normal' — the 3 words keeping you sick" },
      ]
    },
    {
      angle: "Proof",
      description: "Lead with transformation — real patient results",
      creatives: [
        { id: "a7", format: "video", score: 91, estCTR: 2.7, estCPC: 0.95, status: "draft", hook: "Maria was told her fatigue was 'just aging.' She was 38. Here's what happened next." },
        { id: "a8", format: "static", score: 78, estCTR: 1.9, estCPC: 1.35, status: "draft", hook: "From exhausted to energized in 90 days. Not a supplement. Not a diet. Something nobody tested for." },
        { id: "a9", format: "carousel", score: 88, estCTR: 2.5, estCPC: 1.00, status: "draft", hook: "3 women. Same symptoms. Same doctor said 'nothing's wrong.' Here's what we found." },
      ]
    }
  ]
};
```

---

## THE PRINCIPLE

Ads are where money meets messaging. The Ad Creative Builder must make it feel like the expert has an agency's creative department — multiple angles tested, performance predicted before a dollar is spent, every creative formatted for the exact platform. The scoring system (modeled after AdCreative.ai) is what separates this from "ChatGPT wrote me an ad." The expert sees the score and thinks: "This isn't guesswork. The platform knows what works."
