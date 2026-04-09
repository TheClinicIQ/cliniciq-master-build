# ClinicIQ — Email Builder: Complete Build Spec
## Pattern C: Sequence Map → Individual Email Cards → Rich Email Editor
## Modeled after: ActiveCampaign sequence builder + Mailchimp email editor + Beehiiv compose view

---

## WHAT THIS BUILDER DOES

The Email Builder produces complete email sequences: welcome sequences, pre-webinar nurture, post-webinar follow-up, no-show recovery, buyer onboarding, long-term nurture, re-engagement, and referral activation. Each sequence is a series of connected emails with specific triggers, timing, and purposes. Can also produce single broadcast emails.

---

## THE FLOW

### Phase 1: Brief (IQ Chat)

IQ asks:

1. **"Sequence or single email?"** — [Full Sequence] [Single Email]
2. **If sequence — "What type?"** — pills: [Pre-Webinar] [Post-Webinar (didn't buy)] [No-Show] [Lead Magnet Delivery] [Buyer Onboarding] [Long-Term Nurture] [Re-Engagement] [Referral] [Custom]
   - Each type auto-sets the email count, timing, and strategic purpose.
3. **"Which trigger?"** — "What event starts this sequence?" Pre-selected based on type (e.g., "Webinar registration" for pre-webinar). Expert can customize.
4. **"Which offer/avatar?"** — pre-selected from dossier

IQ confirms: "Building a 7-email post-webinar follow-up sequence for attendees who didn't buy. Target: Stressed Mom Sarah. Offer: Hormone Reset Protocol. Starting now."

### Phase 2: Sequence Map (Right Panel)

The right panel shows a **visual sequence timeline** — a vertical flow showing all emails in the sequence, connected by timing indicators.

```
┌─────────────────────────────────────────────┐
│  ✉️ Email Builder    Post-Webinar Follow-Up │
│  7 emails · 7 days          ████████░░ 57%  │
│  ─────────────────────────────────────────  │
│                                             │
│  TRIGGER: Attended webinar, didn't purchase │
│  ↓ Immediately                              │
│                                             │
│  ┌─────────────────────────────────┐        │
│  │ ✅ Email 1: The Replay          │        │
│  │ Subject: "You watched. Now      │        │
│  │ here's what most people miss."  │        │
│  │ Open: 42% · Click: 8%          │        │
│  │ Purpose: Replay + recap         │        │
│  └─────────────────┬───────────────┘        │
│                    ↓ +24 hours               │
│  ┌─────────────────────────────────┐        │
│  │ ✅ Email 2: The Objection       │        │
│  │ Subject: "The real reason you   │        │
│  │ haven't started yet"            │        │
│  │ Purpose: Price objection        │        │
│  └─────────────────┬───────────────┘        │
│                    ↓ +24 hours               │
│  ┌─────────────────────────────────┐        │
│  │ ✅ Email 3: The Proof           │        │
│  │ Subject: "Maria was exactly     │        │
│  │ where you are"                  │        │
│  │ Purpose: Social proof           │        │
│  └─────────────────┬───────────────┘        │
│                    ↓ +24 hours               │
│  ┌─────────────────────────────────┐        │
│  │ 🔄 Email 4: The Mechanism      │        │
│  │ Building...            ████░ 45%│        │
│  └─────────────────┬───────────────┘        │
│                    ↓ +48 hours               │
│  ┌─────────────────────────────────┐        │
│  │ ○ Email 5: The Spouse Email     │        │
│  │ For when the partner is the     │        │
│  │ real decision-maker             │        │
│  └─────────────────┬───────────────┘        │
│                    ↓ +24 hours               │
│  ┌─────────────────────────────────┐        │
│  │ ○ Email 6: Final Urgency       │        │
│  └─────────────────┬───────────────┘        │
│                    ↓ +24 hours               │
│  ┌─────────────────────────────────┐        │
│  │ ○ Email 7: The Downsell        │        │
│  │ Alternative entry point         │        │
│  └─────────────────────────────────┘        │
│                                             │
│  [+ Add Email]  [Adjust Timing]  [Reorder]  │
└─────────────────────────────────────────────┘
```

**Email node card styling:**
- White bg, border 1px #E5E7EB, rounded-lg, padding 12px 16px, full-width (minus 32px padding)
- Top row: status icon + "Email N: [Name]" (13px, bold)
- Subject line: 12px, #374151, italic, 1 line truncated
- Purpose tag: 11px pill (#F3F4F6 bg): "Price objection" / "Social proof" / "Urgency"
- Performance (if live): "Open: 42% · Click: 8%" — green/amber/red colored
- Click → opens email detail view

**Timing connectors:**
- Between each email: a vertical line (1px #E5E7EB) + timing label ("↓ +24 hours" or "↓ +48 hours" — 11px, #9CA3AF)
- Timing is editable: click the timing label → dropdown: [Immediately] [+6 hours] [+12 hours] [+24 hours] [+48 hours] [+72 hours] [+1 week] [Custom]

**Trigger label:**
- Top of sequence: "TRIGGER: [event description]" in a #F8F9FA pill, 11px, #6B7280
- Editable: click to change the trigger event

**Sequence actions:**
- [+ Add Email] — inserts a new email node at the end (or between existing nodes if clicked on a connector)
- [Adjust Timing] — opens a view where all timing gaps are editable at once
- [Reorder] — enables drag-and-drop reordering of emails

### Phase 3: Email Detail View (Right Panel — replaces sequence map)

Clicking an email node opens the **email editor**.

**Layout:**

**Header:**
- [← Back to sequence] + "Email 2 of 7: The Objection" (14px, bold)
- Timing: "Sent 24 hours after Email 1" (12px, #6B7280)
- [Send Test Email] gray outlined button

**Email preview (top section — styled like an email client):**

```
┌─────────────────────────────────────────────┐
│  From: Dr. Sarah Chen                       │
│  Subject: The real reason you haven't       │
│  started yet                                │
│  Preview: I get it. $4,800 is a real        │
│  investment. But let me reframe...          │
│  ─────────────────────────────────────────  │
│                                             │
│  Hi [First Name],                           │
│                                             │
│  I get it.                                  │
│                                             │
│  $4,800 is a real investment. I'm not       │
│  going to pretend it isn't.                 │
│                                             │
│  But let me ask you something that          │
│  changed my perspective — and the           │
│  perspective of every patient who's         │
│  now on the other side...                   │
│                                             │
│  [continues...]                             │
│                                             │
│  ─ Dr. Sarah Chen                           │
│  Signal Reset Health                        │
│                                             │
│  P.S. Maria spent more than $4,800 on      │
│  supplements that didn't work in the        │
│  last 2 years. Just something to think      │
│  about.                                     │
│                                             │
│         [Book Your Strategy Call →]         │
│                                             │
└─────────────────────────────────────────────┘
```

- Styled to look like an actual email in a mail client — white bg, standard email typography (15px body, slightly wider line-height), "From" and "Subject" fields in a header bar
- CTA button rendered as an emerald button at the bottom
- P.S. line styled slightly differently (italic or smaller)
- The entire email body is editable inline — click any text to edit

**Below the preview — metadata & controls:**

**Subject line editor:**
- "Subject:" label + editable input showing the subject line
- "Preview text:" label + editable input showing the preview/preheader text
- [Generate 3 alternatives] emerald text link → shows 3 alternative subject lines to pick from

**Email stats (right side, compact):**
- Strategic purpose: "Addresses the price objection" (12px, #6B7280)
- Objection targeted: "Price / investment concern" (pill badge)
- Emotional beat: "Reframe → proof → possibility" (11px, #9CA3AF)
- Word count: "342 words" · estimated read time: "~2 min"
- Voice match: "🗣️ 93% voice match"

**Actions (bottom bar):**
- [✅ Approve] emerald button
- [🔄 Regenerate] gray outlined
- [← Previous Email] [Next Email →] navigation

### Phase 4: Sequence Complete

When all emails are built:
- IQ: "Your post-webinar sequence is complete — 7 emails over 7 days. Each targets a specific objection. Email 3 has your strongest proof story. Want to review or activate?"
- Sequence map shows all nodes ✅
- **Batch actions:**
  - [Approve All] emerald
  - [Save to Drive] gray outlined
  - [Connect to Automation] emerald outlined → links to GHL/ActiveCampaign to set up the trigger (v1: shows "Connect your email platform in Services")

---

## SINGLE EMAIL MODE

When the expert asks for a single email (not a sequence):

- No sequence map — go directly to the email editor
- IQ asks: "What's the email about?" + "Who's it going to?" (list segment) + "What's the CTA?"
- Generates one email → shows in the email detail view
- Same editing, approval, and export flow

---

## SEQUENCE TYPES AND THEIR STRATEGIC PURPOSE

| Sequence | Emails | Timing | Strategic Purpose |
|----------|--------|--------|------------------|
| **Pre-Webinar** | 3–5 | Days -3 to 0 | Build belief, maximize show rate |
| **Post-Webinar (didn't buy)** | 5–7 | Days 0–7 | Each email = one objection. Proof heavy. Urgency close. |
| **No-Show** | 3–5 | Days 0–5 | Replay offer + FOMO + alternative entry |
| **Lead Magnet Delivery** | 5 | Days 0–7 | Deliver → deepen → mechanism → proof → webinar invite |
| **Buyer Onboarding** | 5–7 | Days 0–30 | Welcome → quick win → community → continuity intro |
| **Long-Term Nurture** | 12 | Weekly × 12 weeks | Educational, proof, mechanism — relationship maintenance |
| **Re-Engagement** | 3 | Days 0–5 | New hook, fresh offer, "we miss you" |
| **Referral** | 2–3 | Day 30–45 post-purchase | Ask + incentive + shareable link |
| **Broadcast** | 1 | Immediate | Weekly value email, promo, announcement |

---

## MOCK DATA

```typescript
const mockSequence = {
  name: "Post-Webinar Follow-Up",
  type: "post-webinar-no-buy",
  trigger: "Attended webinar, did not purchase",
  offer: "Hormone Reset Protocol — $4,800",
  avatar: "Stressed Mom Sarah",
  emails: [
    { id: "e1", name: "The Replay", dayOffset: 0, status: "complete", subject: "You watched. Now here's what most people miss.", purpose: "Replay + value recap", objection: null, words: 287, openRate: 42, clickRate: 8 },
    { id: "e2", name: "The Objection", dayOffset: 1, status: "complete", subject: "The real reason you haven't started yet", purpose: "Price reframe", objection: "Price", words: 342, openRate: 38, clickRate: 6 },
    { id: "e3", name: "The Proof", dayOffset: 2, status: "complete", subject: "Maria was exactly where you are", purpose: "Social proof", objection: "Skepticism", words: 412, openRate: 35, clickRate: 7 },
    { id: "e4", name: "The Mechanism", dayOffset: 3, status: "complete", subject: "The test your doctor never ran (and what it shows)", purpose: "Mechanism education", objection: "Doubt", words: 378, openRate: null, clickRate: null },
    { id: "e5", name: "The Spouse Email", dayOffset: 5, status: "complete", subject: "Forward this to the person who needs to see it", purpose: "Overcome partner objection", objection: "Spouse/partner", words: 298, openRate: null, clickRate: null },
    { id: "e6", name: "Final Urgency", dayOffset: 6, status: "complete", subject: "Last chance — this offer closes tomorrow", purpose: "Scarcity + deadline", objection: "Timing", words: 256, openRate: null, clickRate: null },
    { id: "e7", name: "The Downsell", dayOffset: 7, status: "complete", subject: "Not ready for the full protocol? Here's another way in.", purpose: "Alternative entry", objection: "Commitment level", words: 312, openRate: null, clickRate: null },
  ]
};
```

---

## THE PRINCIPLE

Email is the owned channel — the asset that compounds independent of any algorithm. The Email Builder must make a 7-email sequence feel as easy to review as a single message. The sequence map gives the bird's-eye view. The detail view lets them craft every subject line and P.S. with precision. The objection tagging teaches them WHY each email exists — not just what it says. The expert should finish and think: "This sequence handles every objection I hear on sales calls."
