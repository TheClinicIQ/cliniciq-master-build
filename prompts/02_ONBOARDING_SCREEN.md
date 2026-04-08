# ClinicIQ — Onboarding Screen Prompt
## For Lovable / AI Builder Platform
---

## What To Build

The onboarding experience for a new ClinicIQ expert. This is the most important screen in the entire platform — it's where the expert decides "this is different" or "this is another tool." It must feel like walking into a meeting with a brilliant chief of staff who already did their homework, not like filling out a setup wizard.

**This screen uses the three-panel layout that will be the permanent structure of the entire platform.** The expert sees this layout for the first time here and it stays consistent forever after.

## The Three-Panel Layout

```
┌────────────────┬──────────────────────────────────┬─────────────────────┐
│                │                                  │                     │
│   LEFT PANEL   │         CENTER PANEL             │    RIGHT PANEL      │
│   (Sidebar)    │       (IQ Claw Chat)             │  (Progress Card)    │
│                │                                  │                     │
│   240px wide   │     Fills remaining space        │    320px wide       │
│   Collapsed    │     This is the main event       │    Shows onboarding │
│   during       │                                  │    progress         │
│   onboarding   │                                  │                     │
│                │                                  │                     │
└────────────────┴──────────────────────────────────┴─────────────────────┘
```

## Design System (Consistent With Sign-Up Page)

- **Dark theme.** Same palette as signup: deep navy/charcoal background (#0F1419).
- **Accent color:** Teal/cyan (#00D4AA) for interactive elements, progress indicators, CTAs.
- **Secondary accent:** Warm amber/gold (#F5A623) for progress completion states.
- **Text:** White (#FFFFFF) for primary text. Light gray (#94A3B8) for secondary/helper text.
- **Typography:** Same sans-serif as signup. Clean, modern.
- **Chat bubbles:** IQ Claw messages have a subtle dark card background (#1E2530). Expert messages have the teal/cyan accent background. Both have rounded corners (12px).
- **Overall feel:** Like a premium messaging app (think iMessage dark mode meets a Bloomberg terminal). Not like a SaaS dashboard.

## Left Panel — Sidebar (Minimized During Onboarding)

During onboarding, the left sidebar is **collapsed to icons only** (64px wide) to maximize space for the conversation. It shows:

- **ClinicIQ logo** at the top (small, horizontal wordmark or icon)
- **Navigation icons** (grayed out / disabled during onboarding — they unlock after onboarding completes):
  - 💬 Chat (active — highlighted in teal)
  - 📄 Content
  - 🔗 Funnels
  - ✉️ Email
  - 📢 Ads
  - 🎓 Programs
  - 🎙️ Podcast
  - 📊 Analytics
  - ⚙️ Settings

- At the very bottom of the sidebar: the expert's avatar/initials in a small circle

**The icons are visible but not clickable during onboarding.** They have a subtle tooltip on hover: "Available after setup." This communicates the full platform exists without overwhelming them.

## Center Panel — IQ Claw Chat (The Main Event)

This is where the onboarding conversation happens. It's a full chat interface.

### Top Bar
- Small IQ Claw avatar (a clean, minimal AI icon or the ClinicIQ mark) + "IQ Claw" name + a green status dot ("Online")
- Right side of top bar: a subtle "?" help icon

### Chat Area

The chat area scrolls vertically. Messages appear in a conversational flow — IQ Claw's messages on the left with its avatar, expert's messages on the right.

**The first message from IQ Claw is already visible when the screen loads.** The expert never sees an empty chat. IQ Claw has already spoken.

#### IQ Claw's First Message (Pre-Populated Based on Web Scraper Results)

This message is personalized using the website URL and Instagram handle the expert provided at signup. The Web Scraper ran during signup and pre-populated basic dossier fields.

**Example first message (mock data for the prototype):**

```
┌─────────────────────────────────────────────────────────────────┐
│  🤖 IQ Claw                                           9:02 AM  │
│                                                                 │
│  Hi Dr. Sarah. I've been looking at your practice               │
│  before you arrived.                                            │
│                                                                 │
│  You've been in functional medicine for about 11 years.         │
│  Your website leads with a hormone reset protocol, and          │
│  your Instagram — your cortisol content outperforms             │
│  everything else by about 3x on saves.                          │
│                                                                 │
│  That "your body isn't broken" line? That's the kind of         │
│  mechanism language that stops people mid-scroll.               │
│                                                                 │
│  Before I build anything, I need to understand your             │
│  voice. Not your website copy — the way you actually            │
│  talk.                                                          │
│                                                                 │
│  Imagine a patient sits down across from you. She's             │
│  exhausted. She's been to five doctors. She tells you,          │
│  "Nobody can figure out what's wrong with me."                  │
│                                                                 │
│  What do you say to her?                                        │
└─────────────────────────────────────────────────────────────────┘
```

**Message styling:**
- IQ Claw avatar (small, circular, to the left of the message)
- Message in a dark card (#1E2530) with white text
- Subtle timestamp in light gray
- The last line ("What do you say to her?") should be visually distinct — slightly bolder or separated with a line break to make it clear this is a question waiting for an answer
- A subtle typing indicator animation appears briefly before the message renders (3 bouncing dots) to simulate IQ Claw "arriving"

### Input Area (Bottom of Center Panel)

A persistent input bar fixed to the bottom of the center panel:

```
┌─────────────────────────────────────────────────────────────────┐
│  [Type your answer...]                              🎙️  ➤      │
└─────────────────────────────────────────────────────────────────┘
```

- Text input field with placeholder text: "Type your answer..."
- Microphone icon (🎙️) on the right for voice input
- Send button (➤) in teal/cyan, appears/activates when text is entered
- The input bar has a slightly lighter background than the chat area (#1A2030)
- Rounded corners, subtle inner shadow

### Simulated Conversation Flow (For the Prototype)

After the first message, the prototype should show 2-3 more exchanges to demonstrate the flow. These can be hardcoded/pre-populated for the demo:

**Expert responds:**
> "Honestly? I'd say something like — 'That makes sense. Because they were looking at your symptoms one at a time instead of the whole picture. Your body is a system, and right now it's sending you signals. We just need to learn how to read them.'"

**IQ Claw responds:**
> "Strong. 'Symptoms one at a time vs. the whole picture' — that's a reframe your audience will remember. And 'your body is sending you signals' connects to the content that's already working on your Instagram.
>
> I'm hearing: systems-level thinking, signal-based language, reassuring but direct. You don't coddle — you explain.
>
> Now: what words do you never want to see in your marketing? The ones that make you cringe when a competitor uses them."

**Expert responds:**
> "'Wellness journey.' 'Holistic' — everyone uses it and it means nothing. 'Bio-hacking.' And 'optimal' anything."

**IQ Claw responds:**
> "Banned: 'wellness journey,' 'holistic,' 'bio-hacking,' 'optimal' anything. They're dead to us.
>
> ████████████░░░░  68%
>
> We're making good progress. I have enough to show you something. Give me 90 seconds."

Then after a brief animated pause (loading indicator), IQ Claw delivers the 90-second demo:

> "Here's a preview of what your content will look like. This is one Instagram post, written in YOUR voice, targeting your ideal patient:
>
> ---
>
> *She hadn't slept in 3 years. Not because she didn't try — because every doctor told her the same thing. 'It's just stress. Try melatonin.'*
>
> *Nobody tested her cortisol.*
>
> *That's what we do differently. We don't guess. We test, we read the signals, and we fix what's actually broken.*
>
> *Sarah walked in desperate. Eight weeks later, she sleeps through the night. Her words: 'I feel like myself again.'*
>
> *If that sounds familiar — DM us SLEEP.*
>
> ---
>
> That's your voice, your mechanism language, your patient's story. Every piece of content I build will sound like that. Does it feel like you?"

**This demo moment should be visually special.** The Instagram post preview should render as a styled card within the chat — dark background, the text formatted like an actual IG caption, maybe with a subtle mock-up of an IG post frame around it. This is the "oh my god" moment. Make it visually land.

## Right Panel — Onboarding Progress Card

The right panel during onboarding shows a live progress card that updates as the conversation progresses.

### Progress Card Design

```
┌─────────────────────────────┐
│                             │
│  Building Your Profile      │
│                             │
│  ████████████░░░  68%       │
│                             │
│  ✅ Your story              │
│  ✅ Your voice              │
│  ✅ Your patient avatar     │
│  🔄 Your offer stack        │
│  ○  Your proof bank         │
│                             │
│  ─────────────────────────  │
│                             │
│  Est. ~8 min remaining      │
│                             │
│  ─────────────────────────  │
│                             │
│  WHAT WE KNOW SO FAR        │
│                             │
│  Specialty:                 │
│  Functional Medicine        │
│                             │
│  Voice:                     │
│  Direct, systems-thinker,   │
│  signal-based language      │
│                             │
│  Banned words:              │
│  wellness journey, holistic,│
│  bio-hacking, optimal       │
│                             │
│  Signature phrases:         │
│  "your body is sending      │
│  you signals"               │
│  "the whole picture"        │
│                             │
│  Primary avatar:            │
│  Exhausted women, 35-50,    │
│  dismissed by conventional  │
│  medicine                   │
│                             │
└─────────────────────────────┘
```

**Design details:**
- Card background: slightly lighter than the page (#161B22)
- Progress bar: teal fill (#00D4AA) on dark track
- Checkmarks: teal for complete, amber spinner for in-progress, gray circle for not started
- "WHAT WE KNOW SO FAR" section updates in real-time as the conversation progresses — each field appears with a subtle fade-in animation when captured
- This section is the expert watching their profile being built live. It should feel like intelligence accumulating, not a form being filled.
- The card is sticky (doesn't scroll with the chat)

### Below the Progress Card

A small card or subtle text block:

```
┌─────────────────────────────┐
│  💡 Why this matters         │
│                             │
│  Every word of content,     │
│  every ad, every email      │
│  your platform produces     │
│  runs through this profile. │
│                             │
│  The better I know you,     │
│  the less you'll ever       │
│  need to edit.              │
└─────────────────────────────┘
```

## Mobile Behavior

On mobile (< 768px):
- Left sidebar is completely hidden (accessible via hamburger menu)
- Right panel is hidden (accessible via a "Profile" tab or swipe)
- The center panel (chat) fills the full screen
- The input bar is fixed to the bottom
- A small progress indicator appears at the top of the chat: "68% complete" as a thin progress bar spanning the full width

## Animations & Micro-Interactions

- **IQ Claw typing indicator:** Three bouncing dots (like iMessage) appear for 1-2 seconds before each IQ Claw message renders. Gives the feeling of a real conversation.
- **Progress card updates:** When a new field is captured, it fades in smoothly in the right panel. The progress bar animates smoothly when the percentage increases.
- **90-second demo moment:** After IQ Claw says "Give me 90 seconds," show a unique loading state — not just dots, but a subtle animation that implies generation (a pulsing teal glow, or a small progress ring). Then the demo content card slides in with a slightly more dramatic animation than regular messages.
- **Completion celebration:** When onboarding reaches 100%, a subtle confetti burst or glow effect on the progress bar, and IQ Claw delivers a transition message: "Your profile is built. Your strategy agents are working now — I'll have your first content batch ready within the hour. Welcome to ClinicIQ."

## What NOT To Build

- No stepper/wizard UI (Step 1 of 7, Step 2 of 7...)
- No forms or input fields other than the chat input
- No "Skip" buttons
- No feature tour or tutorial overlay
- No separate onboarding page — this IS the main app layout, just with the right panel showing progress instead of the dashboard
- No empty states — IQ Claw has already spoken when the page loads

## The Whole Screen In One Sentence

A dark-themed three-panel chat interface where IQ Claw has already analyzed the expert's web presence and opens with a personalized, intelligent first message — the expert responds conversationally while the right panel shows their profile being built in real-time, culminating in a "90-second demo moment" where IQ Claw generates a piece of content in their actual voice.
