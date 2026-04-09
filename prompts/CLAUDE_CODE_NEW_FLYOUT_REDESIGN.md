# ClinicIQ — "+ New" Flyout Redesign
## The universal input door. Ask, capture, upload, start fresh.

---

## THE PROBLEM

The current "+ New" flyout is a redundant shortcut menu — Quick Actions (Quick Post, Quick Email, Quick Ad) and a grid of all 12 builders. But the Builders tab already shows all 12 builders, the Engines page handles multi-step work, and IQ Claw handles routing in the chat. The flyout adds no unique value.

## THE NEW CONCEPT

"+ New" becomes the **input door** — how the expert feeds the platform and asks for things. Not "pick a tool" but "give the platform something or ask for something."

Four functions:
1. **Ask IQ** — tell IQ what you need in plain language
2. **New Conversation** — start a fresh IQ thread
3. **Quick Capture** — feed the dossier with real-world intelligence (patient stories, proof, voice notes, competitive intel)
4. **Upload** — get files into the system (testimonials, before/afters, brand assets, documents)

Plus Recent conversations at the bottom for quick resume.

---

## FLYOUT PANEL — Container Styling

- **Trigger:** Click the "+ New" item on the sidebar (Plus icon + "New" label)
- **Position:** Anchored to the right edge of the sidebar rail, vertically aligned with the "+ New" button
- **Width:** 420px
- **Max height:** 85vh (scrollable if needed)
- **Background:** White (#FFFFFF)
- **Border:** 1px #E5E7EB
- **Border-radius:** 16px
- **Shadow:** 0 8px 32px rgba(0,0,0,0.12)
- **Open animation:** Fade in + slide right, 200ms ease
- **Close:** Click outside, click "+ New" again, or Escape

---

## SECTION 1: ASK IQ (Top — the primary action)

The most prominent element in the flyout. A single input where the expert describes what they need. IQ handles the routing — builder, engine, analysis, whatever.

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│  ┌─────────────────────────────────────────────┐    │
│  │  What do you need?                          │    │
│  │                                             │    │
│  │                                             │    │
│  │                                    🎤  [→]  │    │
│  └─────────────────────────────────────────────┘    │
│                                                     │
│  Try: "3 Instagram posts about cortisol"            │
│       "Refresh my ad creatives"                     │
│       "Analyze this week's performance"             │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Textarea: 3 rows, full-width (minus 32px padding), border 1px #E5E7EB, rounded-xl (12px), padding 14px 16px, 14px text, #1F2937. Placeholder: "What do you need?" in #9CA3AF.
- Focus: border emerald (#10B981), subtle emerald glow (0 0 0 2px rgba(16,185,129,0.15))
- Bottom-right of textarea: Mic icon (Lucide `Mic`, 18px, #9CA3AF, hover: #374151) + Send button (emerald circle, 32px, ArrowUp icon 16px white). Send button only appears when text is entered (fade in, 150ms).
- Below textarea: suggestion prompts — 3 lines of example text, 12px, #9CA3AF italic. These are NOT clickable buttons — just visual hints. They rotate/change to show different examples on each flyout open.
  - Set A: "3 Instagram posts about cortisol" / "Refresh my ad creatives" / "Analyze this week's performance"
  - Set B: "Write a nurture email sequence" / "Build me a webinar funnel" / "What's my best performing content?"
  - Set C: "Draft a sales script for consults" / "Create a lead magnet about sleep" / "How are my ads doing?"
- **On submit:** Close the flyout → navigate to `/iq` → the text appears as the expert's first message in a new IQ conversation → IQ responds and routes to the appropriate builder, engine, or analysis.

---

## SECTION 2: NEW CONVERSATION (One-click fresh thread)

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│  [💬 New Conversation]                              │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Full-width button: white bg, border 1px #E5E7EB, rounded-lg (8px), padding 10px 16px. Left: MessageSquarePlus icon (Lucide, 18px, #374151) + "New Conversation" (14px, #1F2937, medium weight). Hover: border #10B981, bg #F0FDF4.
- Click → close flyout → navigate to `/iq` → start a fresh IQ Claw conversation thread (previous conversation preserved in history). IQ sends its standard first message (morning briefing or contextual greeting).
- This is the equivalent of Genspark's "+ New" for starting a fresh Claw conversation.

---

### DIVIDER (1px, #E5E7EB, 12px margin top/bottom)

---

## SECTION 3: QUICK CAPTURE (Feed the dossier — the killer feature)

This is what makes ClinicIQ smarter over time. The expert captures real-world intelligence and it goes directly into their dossier — improving every piece of content, every ad, every email the platform produces.

**Header:** "QUICK CAPTURE" (10px, uppercase, #9CA3AF, letter-spacing 0.05em)

**4 capture cards in a 2×2 grid:**

```
┌───────────────────────┬───────────────────────┐
│                       │                       │
│  📖                   │  🎤                   │
│  Patient Story        │  Voice Note           │
│  Capture a win,       │  Record an idea,      │
│  transformation,      │  a phrase, a thought   │
│  or breakthrough      │  — 60 sec max         │
│                       │                       │
├───────────────────────┼───────────────────────┤
│                       │                       │
│  🏆                   │  🔍                   │
│  Proof                │  Competitive Intel    │
│  Testimonial, review, │  Competitor ad, post, │
│  before/after, lab    │  funnel, or angle     │
│  results              │  you spotted          │
│                       │                       │
└───────────────────────┴───────────────────────┘
```

**Card design:**
- Each card: white bg (#FFFFFF), border 1px #E5E7EB, rounded-xl (12px), padding 14px 16px
- Width: 50% of flyout (minus gaps) — 2 columns, 10px gap
- Height: auto (content-driven), roughly 100px
- Top: emoji (24px)
- Title: 14px, bold, #1F2937
- Subtitle: 12px, #6B7280, 2 lines max
- Hover: border emerald (#10B981), shadow 0 2px 8px rgba(0,0,0,0.06), translateY(-1px), 200ms ease
- Cursor: pointer

**What each card does on click:**

### 📖 Patient Story
Click → flyout transitions to an inline capture panel:

```
┌─────────────────────────────────────────────────────┐
│  [← Back]              📖 Patient Story             │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  Tell me about the patient and what happened.       │
│  Don't worry about structure — I'll organize it.    │
│  (13px, #6B7280)                                    │
│                                                     │
│  ┌─────────────────────────────────────────────┐    │
│  │                                             │    │
│  │  (Textarea, 6 rows, placeholder:            │    │
│  │   "e.g., Maria came in with Hashimoto's,    │    │
│  │   had been on thyroid meds for 8 years.     │    │
│  │   Off meds in 90 days...")                  │    │
│  │                                    🎤  [→]  │    │
│  └─────────────────────────────────────────────┘    │
│                                                     │
│  Optional:                                          │
│                                                     │
│  Patient name/alias: [_______________]              │
│  Condition:          [_______________]              │
│  Timeline to result: [_______________]              │
│  Their exact words:  [_______________]              │
│  (Optional fields — 13px labels, inputs with        │
│   #E5E7EB border, 36px height, rounded-md)          │
│                                                     │
│              [Save to Proof Bank →]                  │
│              (emerald button, full-width, bold)      │
│                                                     │
│  💡 This story will be used in your content,        │
│     ads, emails, and webinars automatically.        │
│  (12px, #6B7280, italic, center)                    │
│                                                     │
└─────────────────────────────────────────────────────┘
```

- The main textarea accepts free-form text. The expert just dumps the story.
- Optional fields help structure it but are NOT required — IQ Claw will parse the free-form text and extract: before state, treatments tried, turning point, result, timeline, direct quote.
- Mic button allows voice-to-text — the expert can dictate the story.
- [Save to Proof Bank →] saves to `proof_bank.transformation_stories[]` in the dossier. Closes flyout. Toast: "Story saved to your Proof Bank — it will appear in your next content batch." (emerald bg, white text, 3s auto-dismiss)

### 🎤 Voice Note
Click → flyout transitions to a recording panel:

```
┌─────────────────────────────────────────────────────┐
│  [← Back]              🎤 Voice Note                │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  Record a quick thought. IQ will transcribe         │
│  it and file it where it belongs.                   │
│  (13px, #6B7280)                                    │
│                                                     │
│                 ┌──────────┐                        │
│                 │    🎤    │                        │
│                 │  0:00    │                        │
│                 │  Tap to  │                        │
│                 │  record  │                        │
│                 └──────────┘                        │
│                 (80px circle, #F3F4F6 bg,           │
│                  Mic icon 32px, #374151.            │
│                  Recording state: red bg            │
│                  (#FEE2E2), pulsing, timer          │
│                  counting up. Max 60 sec.)          │
│                                                     │
│  What's this about?                                 │
│  [Content idea] [Voice DNA] [Patient story]         │
│  [Offer idea] [Random thought]                      │
│  (Tag pills — single select, #F3F4F6 bg,           │
│   #374151 text, selected: emerald bg, white text)   │
│                                                     │
│              [Save Voice Note →]                    │
│              (emerald button, full-width, bold)      │
│                                                     │
│  💡 IQ will transcribe this and add it to your      │
│     dossier automatically.                          │
│  (12px, #6B7280, italic, center)                    │
│                                                     │
└─────────────────────────────────────────────────────┘
```

- Tap the mic to start recording. Tap again to stop. Max 60 seconds.
- Recording state: mic circle turns red (#FEE2E2 bg, red border), pulsing opacity animation, timer counting up (0:01, 0:02...)
- After recording: playback preview appears (waveform + play/pause button + duration)
- Tag selection helps IQ route it: "Content idea" → content briefs, "Voice DNA" → voice profile refinement, "Patient story" → proof bank, "Offer idea" → strategy notes, "Random thought" → IQ inbox for processing
- [Save Voice Note →] → transcribes, files it, closes flyout. Toast: "Voice note saved — IQ will process it."

### 🏆 Proof
Click → flyout transitions to a proof capture panel:

```
┌─────────────────────────────────────────────────────┐
│  [← Back]              🏆 Proof                     │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  What type of proof?                                │
│                                                     │
│  [📝 Text testimonial]                              │
│  [🎥 Video testimonial]                             │
│  [📊 Before/after data]                             │
│  [📸 Before/after photos]                           │
│  [⭐ Review / rating]                               │
│  [📰 Media mention]                                 │
│                                                     │
│  (List of options — each is a full-width row,       │
│   44px height, icon + label, hover: #F3F4F6,        │
│   click opens the appropriate capture form)          │
│                                                     │
└─────────────────────────────────────────────────────┘
```

Each option opens a specific capture form:
- **Text testimonial:** Textarea for the quote + patient name/alias + source (email, DM, review site) + [Save →]
- **Video testimonial:** Upload video file or paste URL + patient name + [Save →]
- **Before/after data:** Two fields — Before value + After value + metric name (e.g., "TSH levels: 8.2 → 2.1") + timeline + [Save →]
- **Before/after photos:** Upload 2 images (before + after) + patient name + description + [Save →]
- **Review / rating:** Screenshot upload or paste text + source (Google, Yelp, etc.) + rating (5 stars) + [Save →]
- **Media mention:** URL or screenshot + publication name + date + [Save →]

All save to `proof_bank.*` in the dossier. Toast on save with proof bank score update: "Proof Bank: 42 → 48/100 (+6)" — shows the expert their score improving in real-time.

### 🔍 Competitive Intel
Click → flyout transitions to a capture panel:

```
┌─────────────────────────────────────────────────────┐
│  [← Back]          🔍 Competitive Intel             │
│  ─────────────────────────────────────────────────  │
│                                                     │
│  What did you spot?                                 │
│                                                     │
│  ┌─────────────────────────────────────────────┐    │
│  │                                             │    │
│  │  (Textarea, 4 rows, placeholder:            │    │
│  │   "e.g., Saw a competitor running an ad     │    │
│  │   with a 'free hormone quiz' hook —         │    │
│  │   getting tons of engagement...")           │    │
│  │                                             │    │
│  └─────────────────────────────────────────────┘    │
│                                                     │
│  URL (optional): [_________________________]        │
│                                                     │
│  Upload screenshot (optional):                      │
│  ┌─────────────────────────────────────────────┐    │
│  │  📎 Drop image here or click to upload      │    │
│  └─────────────────────────────────────────────┘    │
│  (Dashed border #E5E7EB, rounded-lg, 80px height,  │
│   center text 12px #9CA3AF. Accepts image files.)   │
│                                                     │
│  Type:                                              │
│  [Ad] [Post] [Funnel] [Email] [Offer] [Other]      │
│  (Tag pills, single select)                         │
│                                                     │
│              [Save Intel →]                         │
│              (emerald button, full-width, bold)      │
│                                                     │
│  💡 IQ will analyze this and factor it into         │
│     your competitive landscape and strategy.        │
│  (12px, #6B7280, italic, center)                    │
│                                                     │
└─────────────────────────────────────────────────────┘
```

- Saves to `competitive_landscape.*` in the dossier
- IQ can use this to update the Messaging Brief (new hook angles inspired by competitor gaps), refine ad creative angles, and flag differentiation opportunities
- Toast: "Intel saved — IQ will factor this into your next strategy refresh."

---

### DIVIDER (1px, #E5E7EB, 12px margin top/bottom)

---

## SECTION 4: UPLOAD (Get files into the system)

**Header:** "UPLOAD" (10px, uppercase, #9CA3AF, letter-spacing 0.05em)

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│  ┌─────────────────────────────────────────────┐    │
│  │                                             │    │
│  │       📁 Drop files here                    │    │
│  │       or click to browse                    │    │
│  │                                             │    │
│  │       Video, images, docs, audio            │    │
│  │       Max 100MB per file                    │    │
│  └─────────────────────────────────────────────┘    │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Drop zone: dashed border 2px #E5E7EB, rounded-xl, padding 20px, center-aligned
- Icon: Upload icon (Lucide, 32px, #9CA3AF)
- "Drop files here" — 14px, #374151
- "or click to browse" — 13px, #6B7280
- "Video, images, docs, audio · Max 100MB per file" — 11px, #9CA3AF
- Drag hover state: border emerald, bg #F0FDF4, text changes to "Drop to upload"
- On file drop/select: file appears with progress bar + cancel button. On completion: toast "File uploaded to IQ Drive" and file is saved to `/drive/uploads/`
- Accepts: .mp4, .mov, .jpg, .png, .gif, .pdf, .doc, .docx, .mp3, .wav, .m4a
- Multiple files allowed (drag multiple or select multiple from browser)

---

### DIVIDER (1px, #E5E7EB, 12px margin top/bottom)

---

## SECTION 5: RECENT (Quick resume — last 5 conversations)

**Header:** "RECENT" (10px, uppercase, #9CA3AF) + [View All →] (emerald text, 12px, bold, right-aligned)

```
┌─────────────────────────────────────────────────────┐
│  📝 Content batch for April Week 2          2h ago  │
│  📊 Weekly performance review               5h ago  │
│  📋 Webinar script revisions           Yesterday    │
│  ✉️ Email sequence for new leads       Yesterday    │
│  🚀 Campaign launch plan              Last week     │
└─────────────────────────────────────────────────────┘
```

**Design:**
- Each row: 40px height, padding 0 16px
- Left: topic emoji (16px) + conversation title (13px, #1F2937, truncate with ellipsis at 240px)
- Right: timestamp (12px, #9CA3AF)
- Hover: bg #F3F4F6, rounded-md
- Click → navigates to `/iq` and loads that conversation thread
- [View All →] navigates to `/iq` with conversation history sidebar visible
- Max 5 shown. If fewer than 5 exist, show however many there are. If zero: section hidden entirely.

---

## WHAT WAS REMOVED AND WHY

| Removed | Why |
|---------|-----|
| Quick Actions (Quick Post, Quick Email, Quick Ad) | Redundant with the Ask IQ textarea — the expert just types what they need |
| 12-builder grid | Redundant with the Builders tab on the right panel. Also accessible via Ask IQ ("I need a funnel"). The flyout shouldn't duplicate existing surfaces. |
| Quick Launch pills | Same — redundant with Builders tab and IQ routing |

---

## INLINE PANEL PATTERN

Same pattern as the More flyout: when a Quick Capture card is clicked, the flyout content slides left and the capture panel slides in from the right (200ms ease). [← Back] returns to the main flyout. Flyout container stays 420px — no resizing.

---

## KEYBOARD SHORTCUTS

- **Cmd/Ctrl + K** → opens the Ask IQ input directly (flyout opens with cursor already in the textarea). This is the power-user shortcut — like Spotlight on Mac or Cmd+K in Slack/Linear.
- **Cmd/Ctrl + N** → opens the flyout (same as clicking + New)
- **Escape** → closes flyout or goes [← Back] in inline panels

---

## THE PRINCIPLE

"+ New" is the **input door.** Everything flows in through here — questions, requests, patient stories, proof, competitive intel, files, voice notes. Everything flows out through the Builders (single assets) and Engines (complete systems). The expert's job is to feed the platform with intelligence. The platform's job is to turn that intelligence into a growth engine.

The more they use Quick Capture, the smarter their dossier gets, the better their content sounds, the higher their ads convert, the more their IQ Score climbs. That's the flywheel — and "+ New" is where it starts.
