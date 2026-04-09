# ClinicIQ — IQ Claw Chat Fix
## Kill the welcome splash screen. IQ always speaks first. No empty states ever.

---

## THE PROBLEM

The IQ Claw center chat panel currently shows a splash/welcome screen: a large IQ icon, "What can I help you build?", quick action pills (Quick Post, Quick Email, etc.), and suggestion cards (Build my content week, Write an email sequence, etc.). This is an empty state. **ClinicIQ never has empty states.** IQ Claw always speaks first — that's a core principle of the entire platform.

The welcome screen with suggestion cards feels like a generic SaaS chatbot. ClinicIQ is not that. IQ Claw is the expert's AI chief of staff. It knows them. It has context. It speaks first with something specific and useful — every single time.

---

## THE FIX — Delete the Welcome Screen Entirely

Remove the following from the IQ Claw center chat panel:
- The large IQ Claw icon/logo in the center
- "What can I help you build?" heading
- "I'm IQ, your AI workforce. Tell me what you need and I'll create it in your voice." subtitle
- The quick action pills (Quick Post, Quick Email, Quick Ad, Content Batch, Refresh ads, Analyze performance)
- The four suggestion cards (Build my content week, Write an email sequence, Create an Instagram post, Draft my webinar outline)

**All of it. Gone.** The chat panel should never show a welcome screen, a splash screen, a prompt hub, suggestion cards, or any kind of "here's what I can do" empty state.

---

## WHAT REPLACES IT — IQ Claw's First Message

When the expert opens `/iq`, the chat area shows a real conversation — IQ Claw has already sent the first message. The chat always starts with an IQ Claw message bubble (left-aligned, gray bubble, IQ avatar) that is contextual and specific.

**For a brand new user (post-onboarding, first time in the workspace):**

IQ Claw's first message:

> "Welcome to your workspace. Your onboarding data is locked in — I know your voice, your avatar, your mechanism, and your offers. Here's what's happening right now:
>
> 🧬 **Brand North Star** — Your strategy agents are building your positioning and monthly plan. First draft ready within the hour.
>
> 📝 **First content batch** — I'll have your first week of content ready for review once the strategy locks.
>
> Want to dive into something specific? You can tell me to build anything — a post, a funnel, a full campaign — or check out the Growth Engines to launch a complete system."

**For a returning user (has existing data, has used the platform before):**

IQ Claw's first message is a **morning briefing** — contextual to their current state:

> "Morning. Here's where things stand:
>
> 📊 **Performance** — Your cortisol post from Tuesday is outperforming by 2.3x. I'd ride that angle this week.
>
> ✉️ **Email** — Post-webinar sequence is running. 3 of 7 emails sent. Open rate: 34% (above benchmark).
>
> ⚡ **Engine** — Your Monthly Content Machine runs in 3 days. I'll have May content ready for review by the 28th.
>
> 🔔 **Action needed** — 2 content pieces from last week's batch are waiting for your approval.
>
> What do you want to work on?"

**For demo/mock purposes, use this first message (Dr. Sarah Chen persona):**

> "Good afternoon, Dr. Chen. A few things:
>
> 📊 Your cortisol content from this week is outperforming everything else by 2.3x on engagement. I'd recommend leaning into that angle for next week's batch.
>
> ✉️ Your post-webinar email sequence is running — 3 of 7 sent, 34% open rate, above your 25% benchmark.
>
> ⚡ Your Monthly Content Machine engine runs in 3 days. May content will be ready for review by the 28th.
>
> 🔔 2 posts from last week's batch are still waiting for your approval in the Content tab.
>
> What do you want to work on today?"

This message should be rendered as a real IQ Claw chat bubble — same styling as any other IQ message (left-aligned, light gray background #F3F4F6, dark text #1F2937, IQ avatar with emerald circle and brain icon to the left).

---

## THE QUICK ACTIONS — Where They Actually Belong

The quick action pills and suggestion cards aren't useless — they're just in the wrong place. Move them to the **input bar area** as subtle, unobtrusive suggestions.

**Below the chat input bar**, add a single row of compact suggestion chips:

```
┌─────────────────────────────────────────────────────────────────────┐
│  [Message IQ...]                                        🎤  [→]    │
├─────────────────────────────────────────────────────────────────────┤
│  💡 Quick Post  ·  ✉️ Email  ·  📢 Ad  ·  📊 Performance  ·  ⚡ New Engine │
└─────────────────────────────────────────────────────────────────────┘
```

- Chips: 12px text, #6B7280, no border, no background. Separated by · (middle dot). Hover: #1F2937 + underline.
- Clicking a chip pre-fills the input bar with a prompt:
  - "Quick Post" → "Create a social post"
  - "Email" → "Write an email"
  - "Ad" → "Create an ad"
  - "Performance" → "Show me my performance this week"
  - "New Engine" → "I want to build a new growth engine"
- These chips are always visible below the input bar, but they're subtle — not a splash screen. They're helpers, not the main event.
- On mobile: chips scroll horizontally if they overflow.

---

## WHEN ARRIVING FROM "BUILD WITH IQ" (Engine Flow)

When the user clicks [Build with IQ →] from an engine card on `/engines` and lands on `/iq`:

- The welcome screen does NOT show (it's gone entirely per above)
- The right panel shows the engine blueprint/progress (per the ENGINES_FLOW_FIX_v2 spec)
- The center chat shows IQ Claw's **engine-specific first message** — NOT the generic morning briefing. Example:

> "Let's build your Challenge Funnel. I've pulled your dossier — here's the plan:
>
> **Step 1** — Challenge Architecture (theme, daily topics, transformation arc)
> **Step 2** — Funnel Pages (registration + daily pages + graduation)
> **Step 3** — Email Sequence (daily emails + post-challenge bridge to offer)
> **Step 4** — Promo Content (pre-launch + during + post-challenge social posts)
> **Step 5** — Registration Ads (3 hook angles × 2 formats)
>
> First up: the challenge architecture. Which avatar are we targeting? I see Stressed Mom Sarah as your primary. Want to build this challenge for her, or a different audience?"

This engine-specific message replaces whatever first message would normally appear. The chat is scoped to this engine build until it completes.

---

## TECHNICAL IMPLEMENTATION

The chat panel needs a concept of **context/mode** that determines the first message:

```typescript
type ChatContext = 
  | { mode: "default" }           // Morning briefing / general workspace
  | { mode: "engine-build", engineId: string }  // Building a specific engine
  | { mode: "builder", builderId: string }       // Running a specific builder (future)
  | { mode: "post-onboarding" }   // First time in workspace after onboarding

// When navigating to /iq from engines:
router.push({ path: "/iq", query: { context: "engine-build", engineId: "eng_123" } })

// The chat component reads context and renders the appropriate first message
```

When `mode` is `"engine-build"`, the chat:
- Shows the engine-specific first message
- Scopes the conversation to that engine (messages are tagged with the engineId)
- The right panel shows the engine blueprint view (per ENGINES_FLOW_FIX_v2)

When `mode` is `"default"`, the chat shows the morning briefing first message.

---

## SUMMARY

1. **Delete** the welcome splash screen (icon, heading, subtitle, pills, suggestion cards) — permanently, for all users, all states
2. **Replace** with IQ Claw's first message — always a real chat bubble, always contextual
3. **Move** quick action hints to subtle chips below the input bar
4. **When arriving from engine build** — IQ's first message is about the engine, not the morning briefing
5. **The rule: IQ Claw always speaks first. The chat is never empty. No splash screens. No "what can I help you with." IQ already knows.**
