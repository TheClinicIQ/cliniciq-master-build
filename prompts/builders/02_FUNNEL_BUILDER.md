# ClinicIQ — Funnel Builder: Complete Build Spec
## Pattern C: Step-by-step Wizard → Visual Funnel Map → Live Preview
## Modeled after: ClickFunnels funnel map + Unbounce page builder + Leadpages templates

---

## WHAT THIS BUILDER DOES

The Funnel Builder produces complete funnel pages: opt-in pages, thank you/bridge pages, webinar registration pages, order pages with value stack, schedule/booking pages, and thank you/confirmation pages. Not one page at a time — a complete connected funnel flow.

---

## THE FLOW

### Phase 1: Brief (IQ Chat — Center Panel)

IQ asks:

1. **"What kind of funnel?"** — pills: [Webinar Funnel] [Lead Magnet Funnel] [Application Funnel] [Direct Offer] [Custom]
   - Each option auto-sets the page sequence. Webinar = Opt-in → Bridge → Webinar → Order → Schedule → Thank You (5 pages). Lead Magnet = Opt-in → Thank You → Delivery (3 pages).
2. **"Which offer?"** — shows the expert's offer stack: [Free Assessment (Entry)] [Hormone Reset Protocol (Core $4,800)] [VIP Intensive (Premium $12,000)]
3. **"Which avatar?"** — [Stressed Mom Sarah] [Weekend Warrior Mike]

IQ confirms: "Building a 5-page Webinar Funnel for the Hormone Reset Protocol, targeting Stressed Mom Sarah. Here's the flow:"

### Phase 2: Funnel Map (Right Panel)

The right panel shows a **visual funnel map** — a vertical flow diagram of all pages in the funnel, connected by arrows. This is the command center for the entire funnel.

**Funnel map layout:**

```
┌─────────────────────────────────────────────┐
│  🔗 Funnel Builder          Webinar Funnel  │
│  ─────────────────────────────────────────  │
│                                             │
│  ┌─────────────────────────┐                │
│  │  1. Opt-In Page         │  ✅ Complete   │
│  │  "Free Cortisol Assess" │  [Preview]     │
│  └────────────┬────────────┘                │
│               ↓                             │
│  ┌─────────────────────────┐                │
│  │  2. Thank You / Bridge  │  🔄 Building   │
│  │  "You're registered"    │  ████░░ 65%    │
│  └────────────┬────────────┘                │
│               ↓                             │
│  ┌─────────────────────────┐                │
│  │  3. Webinar Page        │  ○ Queued      │
│  │  "Watch the training"   │                │
│  └────────────┬────────────┘                │
│               ↓                             │
│  ┌─────────────────────────┐                │
│  │  4. Order Page          │  ○ Queued      │
│  │  "Enroll now"           │                │
│  └────────────┬────────────┘                │
│               ↓                             │
│  ┌─────────────────────────┐                │
│  │  5. Schedule Page       │  ○ Queued      │
│  │  "Book your consult"    │                │
│  └────────────┬────────────┘                │
│               ↓                             │
│  ┌─────────────────────────┐                │
│  │  6. Thank You Page      │  ○ Queued      │
│  │  "You're confirmed"     │                │
│  └─────────────────────────┘                │
│                                             │
│  [+ Add Page]              [Reorder]        │
└─────────────────────────────────────────────┘
```

**Page node card styling:**
- White bg, border 1px #E5E7EB, rounded-lg (8px), padding 12px 16px, max-width 260px, centered
- Step number (12px, bold, #6B7280) + page name (14px, bold, #1F2937) + subtitle/headline (12px, #6B7280)
- Right side: status badge + [Preview] link when complete
- Status: ✅ Complete (emerald check), 🔄 Building (blue spinner + progress), ○ Queued (gray circle)
- Arrow connector: 1px #E5E7EB, 20px tall, centered below each card
- Active (building) card: blue left border (3px) + light blue bg (#EFF6FF)
- Complete card: emerald left border (3px)
- Hover: shadow + border darken. Click → opens page detail view.

**Funnel map actions:**
- [+ Add Page] — emerald text link at bottom. Click → dropdown of page types (Upsell, Downsell, Bonus, Custom). Inserts a new node into the flow.
- [Reorder] — gray text link. Click → enables drag-and-drop reordering of nodes.
- Pages build sequentially — each page references the previous (e.g., Thank You page references what they just opted in for).

### Phase 3: Page Detail View (Right Panel — replaces funnel map)

Clicking a completed page node opens the **page detail view**.

**Layout:**

**Header:**
- [← Back to funnel map] + "Page 1: Opt-In Page" (14px, bold)
- Status: "✅ Complete" or "Draft"
- [Preview in new tab] emerald link — opens a full rendered preview

**Live page preview (top 60%):**
A rendered preview of the funnel page — styled to look like a real webpage. Scaled down to fit the right panel (like a browser preview at 50% zoom).

The preview shows:
- **Opt-in page:** Headline, subheadline, bullet points, form (name + email), CTA button, social proof (testimonial), mechanism teaser
- **Order page:** Headline, value stack with line items, bonuses, guarantee badge, price, CTA button, testimonials, FAQ accordion
- **Thank you page:** Confirmation message, next steps, expectation setting

The preview is NOT editable directly — it's a visual representation. Editing happens in the sections below.

**Page sections (bottom 40% — scrollable, editable):**

Each section of the page is an expandable accordion:

```
▼ Headline
  "Your body isn't broken — discover what's actually driving your fatigue"
  [Edit in chat →]  [Edit inline]

▼ Subheadline  
  "Free 3-minute assessment reveals the root cause your doctor missed"
  [Edit in chat →]  [Edit inline]

▼ Bullet Points (3)
  • Find out which of the 5 hidden stress patterns is affecting you
  • Get a personalized root cause hypothesis in 3 minutes
  • See exactly what to test next — no more guessing
  [Edit in chat →]  [+ Add bullet]

▼ Social Proof
  "Maria went from exhausted to energized in 90 days" — ★★★★★
  [Edit in chat →]  [Change testimonial]

▼ CTA Button
  Text: "Get My Free Assessment →"
  Color: Emerald (#10B981)
  [Edit in chat →]  [Edit inline]

▼ Form Fields
  • Full name (required)
  • Email (required)
  • Phone (optional)
  [+ Add field]  [Remove field]
```

- Each section: collapsible accordion, 1px #E5E7EB bottom border
- Section name: 13px, bold, #1F2937, with ChevronDown/Up icon
- Content: 13px, #374151, editable inline (click to edit) or via IQ chat ([Edit in chat →] pre-fills IQ with "Change the headline on my opt-in page to...")
- Changes in either editor (inline or chat) update the preview in real-time

### Phase 4: Funnel Complete

When all pages are built:
- Funnel map shows all nodes as ✅
- IQ sends completion message: "Your Webinar Funnel is complete — 6 pages built. Opt-in headline: 'Your body isn't broken.' Order page has the full Brunson value stack. Want to review any page or publish?"
- **Batch actions** appear at the bottom of the funnel map:
  - [Preview Entire Funnel →] — opens each page in sequence in a new tab, simulating the user journey
  - [Save to Drive] — saves all pages to /drive/funnels/[funnel-name]/
  - [Publish] — future: publishes to connected funnel host (GHL, ClickFunnels, WordPress). For v1: shows "Connect your funnel host in Services to publish" with a link.

---

## PAGE TYPES AND THEIR UNIQUE SECTIONS

| Page Type | Unique Sections | Special Notes |
|-----------|----------------|---------------|
| **Opt-in** | Headline, subheadline, bullets, form, CTA, social proof, mechanism teaser | Form captures name + email minimum. CTA is the primary conversion action. |
| **Thank You / Bridge** | Confirmation message, expectation setting ("Your webinar is on [date]"), micro-commitment ("Add to calendar"), bonus teaser | Must reinforce the decision, reduce buyer's remorse / regret of giving email |
| **Webinar** | Embedded video player (placeholder), webinar title, presenter bio, key takeaways, countdown timer (if live), CTA to stay | The video is external — page just needs the embed frame + surrounding content |
| **Order** | Headline, value stack (line items with prices), bonuses (each with transformation statement), guarantee badge, total price, payment form placeholder, testimonials, FAQ, urgency element | This is the Brunson Stack Slide as a page. Every element of the Hormozi Value Equation present. |
| **Schedule** | Calendar embed (Calendly placeholder), what to expect on the call, preparation instructions | Clean, minimal — don't give them reasons NOT to book |
| **Upsell** | One-time offer headline, value prop, CTA, "No thanks" skip link | Must relate to what they just purchased. Time-limited feel. |
| **Downsell** | Reduced offer, "Here's what I can do" framing, CTA | Not a consolation — positioned as "the smart starting point" |

---

## FUNNEL PERFORMANCE (after launch)

Once funnel pages are live and generating data, the funnel map updates with conversion metrics on each arrow:

```
  [Opt-In Page]     Visitors: 1,240
       ↓  38% conversion rate (🟢)
  [Thank You]        Opt-ins: 471
       ↓  28% show rate (🟡)
  [Webinar]          Attended: 132
       ↓  9% conversion (🟢)
  [Order Page]       Purchased: 12
       ↓  75% book rate (🟢)
  [Schedule]         Booked: 9
```

Each conversion rate is color-coded: emerald (at/above benchmark), amber (within 80%), red (below 80%). Clicking a conversion rate → IQ suggests optimization: "Show rate is at 28%, below the 35% benchmark. I recommend refreshing the pre-webinar email sequence."

---

## MOCK DATA

```typescript
const mockFunnel = {
  name: "Evergreen Webinar Funnel",
  type: "webinar",
  offer: "Hormone Reset Protocol",
  avatar: "Stressed Mom Sarah",
  pages: [
    {
      id: "p1", type: "optin", name: "Opt-In Page", status: "complete",
      headline: "Your body isn't broken — discover what's actually driving your fatigue",
      subheadline: "Free 3-minute assessment reveals the root cause your doctor missed",
      bullets: [
        "Find out which of the 5 hidden stress patterns is affecting you",
        "Get a personalized root cause hypothesis in 3 minutes",
        "See exactly what to test next — no more guessing"
      ],
      cta: "Get My Free Assessment →",
      testimonial: { name: "Maria", quote: "I finally feel like the person my family deserves", rating: 5 }
    },
    {
      id: "p2", type: "thankyou", name: "Thank You / Bridge", status: "complete",
      headline: "You're in — your assessment is on the way",
      body: "Check your email in the next 2 minutes. While you wait, here's something most people don't know about cortisol..."
    },
    {
      id: "p3", type: "webinar", name: "Webinar Page", status: "complete",
      headline: "The Signal Reset Method: Why Everything You've Tried for Fatigue Has Failed",
      presenterBio: "Dr. Sarah Chen — Functional Medicine, 12 years experience, 500+ patients treated"
    },
    {
      id: "p4", type: "order", name: "Order Page", status: "complete",
      headline: "Start Your Signal Reset Protocol Today",
      valueStack: [
        { item: "12-Week Signal Reset Protocol", value: "$4,800" },
        { item: "Bonus: Complete Lab Panel Guide", value: "$497", type: "bonus" },
        { item: "Bonus: Private Community Access", value: "$997", type: "bonus" },
        { item: "Bonus: Emergency Protocol Hotline", value: "$1,200", type: "bonus" }
      ],
      totalValue: "$7,494", price: "$4,800",
      guarantee: "90-Day Results Guarantee — if you don't see measurable improvement in your labs and how you feel, full refund."
    },
    {
      id: "p5", type: "schedule", name: "Schedule Page", status: "complete",
      headline: "Book Your Strategy Call",
      body: "Pick a time that works. This is a 30-minute call to map your personalized protocol."
    },
    {
      id: "p6", type: "thankyou-final", name: "Confirmation", status: "complete",
      headline: "You're booked — here's what happens next",
      body: "1. Check your email for the calendar invite\n2. Fill out the pre-call questionnaire (5 min)\n3. Show up ready to talk about your health goals"
    }
  ]
};
```

---

## THE PRINCIPLE

The Funnel Builder is the infrastructure — every piece of content, every ad, every email is driving traffic somewhere. The funnel map gives the expert a bird's-eye view of their entire conversion system. The page detail view lets them craft every element with precision. The performance overlay (post-launch) turns the map into a diagnostic tool. The expert should feel like they're looking at the blueprint of their revenue machine.
