# FINAL Revision Prompt — Complete Workspace Redesign
## Paste this into MagicPath. This replaces ALL previous revision prompts.

---

Completely rebuild this component from scratch with the following exact specification. Do not carry over any elements from the previous version — start fresh.

## OVERALL LAYOUT

Three panels: narrow left sidebar rail (72px) + center chat panel + right context panel. Light theme. White background (#FFFFFF). Light gray panels (#F8F9FA). Teal accent (#00D4AA). Clean, modern, premium.

Width proportions after the 72px sidebar: center chat gets ~55% of remaining space, right panel gets ~45%.

No flyouts shown in the default state. All flyouts are hover/click triggered — in this static design, show the clean collapsed state only.

---

## LEFT SIDEBAR — Narrow Icon Rail (72px wide)

White background. Subtle right border (#E5E7EB). All items center-aligned. Each item: icon (24px) with tiny label (10px) beneath it in gray (#9CA3AF). Active item: teal icon + 3px teal left border indicator.

### Items top to bottom:

**TOP SECTION:**

1. **IQ** — The ClinicIQ brand mark. A bold teal "IQ" logomark or teal rounded square icon with "IQ" inside. This is the HOME BUTTON — the equivalent of Genspark's "Claw" button. It's the identity of the product. Clicking it returns to the main IQ Claw chat. Show this as the ACTIVE item (teal color + left border indicator). Label beneath: "IQ Claw"

2. **+ New** — Plus icon in a teal rounded square (small button). Label: "New". This starts a new conversation.

**MIDDLE NAVIGATION (evenly spaced):**

3. 💬 **Chat** — Speech bubble outline icon. Label: "Chat". On hover, a flyout would show conversation history — but don't show the flyout, just show the icon.

4. ⚡ **Builders** — Lightning bolt or grid icon. Label: "Builders". On hover, a flyout would show all 10 builder cards in a grid — but don't show the flyout, just show the icon.

5. 🧬 **Brand** — DNA helix or fingerprint outline icon. Label: "Brand"

6. 📋 **Strategy** — Clipboard or compass outline icon. Label: "Strategy"

7. 📁 **Content** — Folder outline icon. Label: "Content". Show a small red notification badge with "3" on the icon (3 items need review).

8. 📊 **Analytics** — Bar chart outline icon. Label: "Analytics"

9. ••• **More** — Three horizontal dots icon. Label: "More"

**BOTTOM SECTION (pinned to bottom, separated by space):**

10. ⚙️ — Gear outline icon. No label. Settings.

11. 👤 — Teal circle with white initials "SC". This is the user profile. Below it in tiny text: "Dr. Sarah Chen"

### Icon styling:
- All icons: outlined/stroke style, 1.5px weight
- Inactive: gray (#9CA3AF)
- Active (IQ Claw): teal (#00D4AA) with 3px teal bar on left edge
- Hover state: icon turns teal, subtle light teal (#F0FDFB) circle background appears

---

## CENTER PANEL — IQ Claw Chat

### Top Bar
Left side: Teal IQ Claw avatar circle (small, with a stylized "IQ" or brain icon inside) + bold text "IQ Claw" + green dot + "Online" in small green text.
Right side: A subtle gray pill showing "📁 Content batch Apr Wk 2" (current conversation topic) + three-dot menu button (•••).

Light bottom border (#E5E7EB) separating header from chat.

### Chat Messages

**Message 1 — IQ Claw (left-aligned, IQ avatar):**
Light gray bubble (#F3F4F6) with dark text (#1F2937).

"Morning, Dr. Sarah.

🔴 **One thing needs your eye** — your Meta ad set B is fatiguing. CTR dropped 40% over the last three days. I already have 2 replacement hooks ready.

🟢 **Good news** — your cortisol carousel hit 4.2% engagement this week. That's double your average. I've queued 3 more in the same format.

📋 **5 posts for next week** ready to review. 3 are solid, 2 need your eye on the hooks.

Where do you want to start?"

**Three action pill buttons below the message:**
Teal outlined pills with teal text, white fill:
[Fix the ad hooks] [Review content] [Show me analytics]

**Message 2 — IQ Claw (left-aligned, IQ avatar):**
Light gray bubble.

"Post 1 of 5. Instagram authority piece targeting the 'Stressed Mom Sarah' persona. PAS framework. I used your 'your body is telling you exactly what's wrong' line as the opener because it hit 2x saves last month. Take a look."

**Inline Instagram post preview card below the message:**
White card with subtle border (#E5E7EB), rounded corners (12px).
- Top: Small teal avatar "SC" + "dr.sarahchen" username
- Image area: A lifestyle photo placeholder (woman in wellness/yoga setting) with teal italic overlay text: "Your body is telling you exactly what's wrong."
- Below image: Caption preview in small text: "Are you feeling constantly drained despite doing 'all the right things'? It might not be the caffeine..."
- Metadata row: Three small gray tags: "Persona: Stressed Mom" | "Framework: PAS" | "Scheduled: Thu 10am"
- Action buttons row: Three small buttons:
  [✅ Approve] (green tint) [✏️ Tweak] (amber tint) [🗑️ Veto] (red tint)

### Input Bar (fixed to bottom of center panel)
White card with subtle border, rounded corners (24px). Inside:
- Text placeholder: "Message IQ Claw..." in gray
- Right side: microphone icon (gray) + teal circular send button with white arrow icon
- Below the input bar: tiny gray helper text: "IQ Claw can analyze patterns across all your active channels in real-time."

---

## RIGHT PANEL — Context Panel with Tabs

Light gray background (#F8F9FA). Subtle left border (#E5E7EB).

### Tab Bar (5 tabs, single row, fits without scrolling)

Horizontally arranged tabs with icon + short label. Clean, flat design.

**🧬 My Brand | 📋 Strategy | 📁 Content | 📅 Calendar | 📡 Connections**

NONE of these tabs are active by default. Below the tabs, the DEFAULT content is the dashboard (no tab selection needed — the dashboard shows automatically when the user is in the IQ Claw chat). When a user clicks a tab, the dashboard is replaced by that tab's content. A small "✕" or "back to dashboard" link returns to the default state.

### Default Content — The Dashboard (shown beneath the tab bar)

**Section 1: ⚠️ NEEDS ATTENTION**
Two alert cards with white background, subtle border:

Card 1:
- "Ad Set B fatiguing" — bold dark text
- "-40% CTR" — red badge/text on the right
- "Trend over last 3 days" — small gray text
- "Fix Now →" — teal link

Card 2:
- "Email open rates" — bold dark text
- "22% → 16%" — amber/red text on right
- "Review →" — teal link

**Section 2: ✅ WHAT'S WORKING**
Two cards:

Card 1:
- "Cortisol carousel" — bold
- Small green progress bar on right (~70% filled)
- "4.2% engagement, 2x average" — gray text

Card 2:
- "Welcome sequence" — bold
- "42% Open" — green text on right
- "Exceeding industry benchmark" — gray text

**Section 3: 📈 QUICK METRICS**
Compact table/list:

| Metric | Value | Change |
|--------|-------|--------|
| Engagement | 14.2K | ↑ 12% (green) |
| Saves | 892 | ↑ 23% (green) |
| Email opens | 16.2% | ↓ 4% (red) |
| Ad spend | $45/day | — |
| New leads | 8 | this week |

**Section 4: 📅 COMING UP THIS WEEK**
Compact calendar list:
Mon — 📝 2 posts (10am, 2pm)
Tue — 📝 1 post (10am)
Wed — 📝 2 posts + ✉️ email
Thu — 🎥 Webinar live (2pm)
Fri — 📝 1 post (10am)

---

## WHAT THIS DESIGN SHOULD FEEL LIKE

- **Clean and minimal by default.** The narrow sidebar rail keeps the interface uncluttered. All the depth is one hover/click away in flyouts.
- **The IQ Claw chat is the hero.** It dominates the center. The expert talks to IQ and things happen.
- **The right panel is a smart glanceable support panel.** It answers "what's happening" without the expert asking. Tabs let them dive deeper when they want.
- **The IQ logo on the sidebar is the product identity.** It's always there, always teal, always the way home. Like Genspark's Claw.
- **Premium health brand aesthetic.** Light, clean, confident. Think Stripe dashboard meets a high-end wellness brand. Not a SaaS tool. A command center for someone important.

---

## WHAT NOT TO INCLUDE

- No flyout panels shown open (show the clean default state)
- No dark mode
- No feature tour or tutorial overlays
- No empty states anywhere — everything has content
- No more than 5 tabs on the right panel
- No duplicate navigation (if it's on the left sidebar, it doesn't need its own right panel tab except for My Brand, Strategy, Content, Calendar, and Connections which are full detail views)
