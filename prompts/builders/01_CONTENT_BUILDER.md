# ClinicIQ — Content Builder: Complete Build Spec
## Pattern B: Brief → Batch Generate → Grid Review → Edit Individual
## Modeled after: AdCreative.ai grid output + Canva batch create + Buffer content queue

---

## WHAT THIS BUILDER DOES

The Content Builder produces batches of social media content: Instagram posts, carousels, Reels scripts, Stories, Facebook posts, TikTok scripts, LinkedIn posts. Not one piece at a time — batches of 7–28 pieces, each mapped to a specific hook angle, content pillar, CTA type, and platform.

---

## HOW IT'S TRIGGERED

Three entry points:
1. **Builders tab** → click "Content Builder" card → IQ opens the brief conversation
2. **IQ chat** → "Create a content batch" or "I need 7 Instagram posts" → IQ recognizes Content Builder intent
3. **Growth Engine step** → an engine triggers Content Builder as one of its steps

In all cases: IQ leads the conversation in the **center chat**. The builder output appears in the **right panel**.

---

## THE FLOW

### Phase 1: Brief (IQ Chat — Center Panel)

IQ asks quick clarifying questions (one at a time, never stacked):

1. **"How many pieces?"** — default suggestion based on Monthly Master Plan: "Your plan calls for 7 posts this week. Want to build all 7, or a different number?"
2. **"Which platforms?"** — pills: [Instagram] [Facebook] [TikTok] [LinkedIn] [All] — pre-selected based on connected channels
3. **"Any specific topic or angle?"** — free text or "Use this month's messaging brief" (default)
4. **"Which avatar?"** — shows avatar cards: [Stressed Mom Sarah (primary)] [Weekend Warrior Mike] — pre-selected to primary

IQ confirms: "Building 7 Instagram posts for Stressed Mom Sarah using this week's hook angles. Starting now."

If the expert just says "make me content" with no details, IQ uses the Monthly Master Plan defaults and confirms: "I'll build this week's content batch — 7 posts, Instagram, from the April messaging brief. Good?"

### Phase 2: Generation (Right Panel — Grid View)

The right panel switches to the **Content Builder view**. The tab bar stays visible (Dashboard, Brand, Strategy, etc.) but a temporary **📝 Content** indicator appears showing the build is active.

**Right panel layout during generation:**

**Header bar:**
- "📝 Content Builder" (14px, bold) + "Building 7 posts..." (13px, #6B7280) + spinner icon
- Progress: "3 of 7 complete" (12px, #6B7280)
- [Cancel] gray text link

**Grid below:**
A **2-column grid** of content cards. Each card represents one piece of content. Cards fill in one by one as they generate — empty placeholder cards (dashed border, #E5E7EB, pulsing subtle animation) show what's coming.

**Content card — generating state:**
```
┌─────────────────────────┐
│  ░░░░░░░░░░░░░░░░░░░░  │
│  ░░░ Generating... ░░░  │
│  ░░░░░░░░░░░░░░░░░░░░  │
│                         │
│  ████████░░░░ 60%       │
└─────────────────────────┘
```
- Dashed border, #F8F9FA bg, pulsing opacity animation (0.4→0.7→0.4, 2s)
- "Generating..." centered, 12px, #9CA3AF
- Mini progress bar at bottom

**Content card — complete state:**
```
┌─────────────────────────┐
│  ┌───────────────────┐  │
│  │   [Image preview]  │  │
│  │   or gradient bg   │  │
│  │   with hook text   │  │
│  └───────────────────┘  │
│                         │
│  📝 Instagram Post      │
│  Hook: "Your 2pm crash  │
│  isn't normal..."       │
│                         │
│  Pillar: Root Cause     │
│  CTA: Comment trigger   │
│                         │
│  [✅ Approve] [✏️ Edit] │
└─────────────────────────┘
```

- White bg (#FFFFFF), border 1px #E5E7EB, rounded-xl (12px), overflow hidden
- **Top section (40% of card):** Visual preview area
  - For image posts: AI-generated image preview or a branded gradient with the hook text overlaid in white (simulating what the post looks like on Instagram)
  - For carousels: shows slide 1 with a "1/6" badge in the corner
  - For Reels/video scripts: shows a 🎬 icon on a dark gradient with the hook text
- **Middle section:** Content metadata
  - Platform icon + format label (12px, bold, #1F2937): "📝 Instagram Post" or "🎠 Carousel (6 slides)" or "🎬 Reel Script (30s)"
  - Hook preview: first line of the caption, 12px, #374151, truncated at 2 lines
  - Tags: two small pills — content pillar name (#F3F4F6 bg, 10px, #6B7280) + CTA type (#F3F4F6, 10px)
- **Bottom section:** Actions
  - [✅ Approve] — emerald outlined button, 11px, bold. Click → card gets an emerald border + checkmark badge top-right.
  - [✏️ Edit] — gray outlined button, 11px. Click → card expands to detail view (Phase 3).
  - [🔄 Regenerate] — gray text link, 10px. Click → regenerates just this one piece.
  - [🗑️] — trash icon, 16px, #9CA3AF, far right. Click → removes from batch with confirmation.

**Card dimensions:** Each card is roughly 48% of the right panel width (2-column with 8px gap). Height: auto based on content, roughly 240–280px.

### Phase 3: Detail View (Right Panel — Expanded Card)

When the expert clicks [✏️ Edit] or clicks anywhere on a card, the right panel transitions to a **detail view** for that single piece of content.

**Detail view layout:**

**Header:**
- [← Back to batch] gray text link + "Post 3 of 7" (13px, #6B7280)
- Status badge: "Draft" (gray) or "Approved ✅" (emerald)

**Visual preview (top half):**
- Large preview of the content as it would appear on the platform
- For Instagram post: square image + caption below (styled to look like an IG post)
- For carousel: horizontal scrollable slide strip (each slide shown as a card, click to view full-size)
- For Reel script: the script shown as a teleprompter-style text with timestamps (0:00–0:03 Hook, 0:03–0:15 Bridge, etc.)

**Content (bottom half — editable):**

**Caption/Copy:**
- Full text area showing the complete caption. Editable inline — click to edit, changes save automatically.
- Word count shown (e.g., "142 words")
- Voice DNA match indicator: "🗣️ 94% voice match" (emerald if 90%+, amber if 70–89%, red if <70%)

**Metadata (compact row):**
- Platform: [Instagram ▾] dropdown (can switch)
- Format: [Post ▾] / [Carousel] / [Reel] / [Story]
- Content pillar: [Root Cause ▾]
- CTA type: [Comment trigger ▾]
- Hook angle: [Pain ▾]
- Scheduled date: [Apr 10, 9:00 AM ▾] date/time picker

**Image prompt (collapsible):**
- "Image Generation Prompt" — collapsed by default, click to expand
- Shows the exact prompt used to generate the image. Editable — expert can tweak and [Regenerate Image] with the new prompt.

**Hashtags:**
- Pill row of hashtags. Click any to remove. [+ Add] to add custom.

**Actions (bottom bar, sticky):**
- [✅ Approve] emerald button
- [🔄 Regenerate] gray outlined — regenerates this entire piece
- [🗑️ Delete] red text link
- [← Previous] [Next →] gray arrows to navigate between pieces without going back to grid

### Phase 4: Batch Complete

When all pieces are generated:
- IQ sends a message in chat: "Your content batch is ready — 7 pieces for this week. 4 approved, 3 still need your review."
- Grid view shows the full batch with approval status on each card
- **Batch actions bar** appears at top of grid:
  - "4 of 7 approved" (13px, #374151) + progress bar
  - [Approve All] emerald button — approves everything not yet approved
  - [Save to Drive] gray outlined — saves the entire batch to /drive/content/[month]/
  - [Schedule All] emerald outlined — schedules approved pieces to the content calendar based on the Monthly Master Plan dates

---

## CONTENT FORMATS SUPPORTED

Each format has slightly different preview and editing needs:

| Format | Preview | Editor | Special Fields |
|--------|---------|--------|----------------|
| **Instagram Post** | Square image + caption | Caption editor + image prompt | Hashtags, location tag |
| **Instagram Carousel** | Slide strip (horizontal scroll) | Per-slide text editor + image prompt per slide | Slide count, swipe CTA on last slide |
| **Instagram Reel Script** | Teleprompter with timestamps | Script editor with hook/bridge/value/CTA sections | Duration, b-roll directions, audio notes |
| **Instagram Story** | Vertical image/text preview | Text overlay editor + background selector | Sticker suggestions, poll/quiz ideas |
| **Facebook Post** | Wide image + long caption | Caption editor (longer allowed) + image prompt | Link preview if URL included |
| **TikTok Script** | Teleprompter with timestamps | Script editor | Trending audio suggestion, duration |
| **LinkedIn Post** | Text-heavy preview | Long-form text editor | No image required, professional tone check |

---

## IQ CHAT DURING BUILDING

While the Content Builder is running, the expert can chat with IQ about other things — the builder runs in the background. IQ provides status updates:

- "Post 3 is done — strong pain hook. Check it out."
- "All 7 are ready. I'd look at #4 — the CTA might be too soft for this audience."

If the expert says "change the hook on #3 to a proof angle" in the chat, IQ routes the edit to the Content Builder, regenerates #3, and the grid updates.

---

## MOCK DATA

```typescript
const mockContentBatch = [
  {
    id: "c1", format: "instagram-post", platform: "instagram",
    status: "approved",
    hook: "Your 2pm crash isn't a coffee problem — it's a cortisol problem.",
    caption: "Your 2pm crash isn't a coffee problem — it's a cortisol problem.\n\nEvery afternoon, your body sends a signal. Most doctors call it 'normal fatigue.' But there's nothing normal about needing caffeine to function.\n\nHere's what's actually happening: your HPA axis — the system that regulates your stress response — is stuck in overdrive. It's been running a pattern nobody identified.\n\nThe crash isn't the problem. It's the symptom of a pattern that's been building for years.\n\nComment RESET to get your free Cortisol Assessment 👇",
    pillar: "Root Cause Education", cta: "Comment trigger", hookAngle: "Pain",
    imagePrompt: "A tired woman at a desk at 2pm, head resting on hand, soft afternoon light, muted tones, documentary style, 4:5",
    hashtags: ["#cortisol", "#hormonehealth", "#rootcause", "#fatigue", "#functionalmedicine"],
    voiceMatch: 94, wordCount: 142, scheduledDate: "2026-04-10T09:00:00Z"
  },
  {
    id: "c2", format: "instagram-carousel", platform: "instagram",
    status: "draft",
    hook: "5 signs your 'normal' labs are lying to you",
    caption: "5 signs your 'normal' labs are lying to you 👇\n\nSwipe through to see what your doctor isn't testing — and why it matters.\n\nSave this post. Share it with someone who's been told 'everything looks fine' while they still feel terrible.\n\nLink in bio for the full assessment.",
    pillar: "Myth-Busting", cta: "Save + Share", hookAngle: "Curiosity",
    slides: 6, imagePrompt: "Clean medical infographic style, white background, emerald accents",
    hashtags: ["#labresults", "#thyroid", "#hormones", "#functionalmedicine"],
    voiceMatch: 91, wordCount: 89, scheduledDate: "2026-04-11T09:00:00Z"
  },
  {
    id: "c3", format: "instagram-reel", platform: "instagram",
    status: "draft",
    hook: "Your doctor says your thyroid is fine. Here's why they're wrong.",
    script: "HOOK (0-3s): Your doctor says your thyroid is fine. Here's why they're wrong.\n\nBRIDGE (3-10s): They ran one test — TSH. That's like checking the oil in your car and ignoring the engine, the transmission, and the fuel system.\n\nVALUE (10-25s): A complete thyroid panel includes TSH, Free T3, Free T4, Reverse T3, TPO antibodies, and thyroglobulin antibodies. Most doctors run ONE of those six.\n\nCTA (25-30s): Comment LABS and I'll send you the complete list to bring to your next appointment.",
    pillar: "Authority", cta: "Comment trigger", hookAngle: "Villain",
    duration: "30s", brollNotes: "B-roll: lab paperwork close-up, doctor's office, test tubes",
    voiceMatch: 96, wordCount: 98, scheduledDate: "2026-04-12T09:00:00Z"
  },
  // ... 4 more pieces with varied formats
];
```

---

## DESIGN SYSTEM

- **Grid gap:** 8px between cards, 12px padding on grid container
- **Card border:** 1px #E5E7EB. Approved: 2px emerald border. Hover: shadow + border darken.
- **Approval badge:** 20px emerald circle with white Check icon, positioned absolute top-right of card (-6px offset)
- **Format icons:** 📝 Post, 🎠 Carousel, 🎬 Reel, 📱 Story, 💼 LinkedIn
- **Voice match indicator:** Emerald text "94%" (90+), amber "78%" (70-89), red "52%" (<70)
- **Transitions:** Card expand to detail: 200ms ease scale + fade. Grid card appear: 300ms ease fade-in + slide-up (staggered, 100ms per card).

---

## THE PRINCIPLE

The Content Builder is the workhorse — the most-used builder on the platform. It must feel effortless to produce a week's worth of content in one session. The grid makes reviewing a batch feel fast (not one-by-one-by-one). The detail view makes editing precise. The approval flow makes publishing frictionless. The expert should feel like they have a content team, not a content tool.
