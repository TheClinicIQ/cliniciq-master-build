# Flyout — "+ New" Button
## Paste into MagicPath chat

---

Add a flyout panel that appears when the user hovers or clicks the "+ New" button on the left sidebar. The flyout extends to the right of the sidebar, overlaying the left edge of the chat panel.

## FLYOUT PANEL STYLING
- Width: 520px
- Background: white
- Border-radius: 16px
- Shadow: large soft shadow (0 8px 32px rgba(0,0,0,0.10))
- Subtle border: #E5E7EB
- Anchored to the right edge of the sidebar, vertically aligned with the "+ New" button
- Show it open in this design (as if the user just clicked "+ New")

## FLYOUT CONTENT

### Section 1 — "Quick Actions" (top)

Header: "Quick Actions" in bold dark text, 16px

A horizontal row of 3 action cards. Each card: white background, subtle border, rounded corners (12px), ~160px wide. Icon on top (32px, colored), bold label below, tiny gray description under that.

Card 1:
- Icon: 📝 (teal circle background)
- Label: "Quick Post"
- Description: "One post, any topic"

Card 2:
- Icon: ✉️ (blue circle background)
- Label: "Quick Email"
- Description: "Single email, any type"

Card 3:
- Icon: 📢 (orange circle background)
- Label: "Quick Ad"
- Description: "Hook + creative + copy"

### Section 2 — "Builders" (main grid)

Header: "Builders" in bold dark text, 16px

A 3-column grid of builder items. Each item: a colored circular icon (48px) centered with a label (12px, gray) below it. Same layout pattern as Genspark's agent grid in their "New" flyout.

Row 1:
- 📝 Content Builder (teal icon) | 🔗 Funnel Builder (indigo icon) | 🎥 Webinar Builder (purple icon)

Row 2:
- ✉️ Email Builder (blue icon) | 📢 Ad Creative (orange icon) | 🧲 Lead Magnet (pink icon)

Row 3:
- 🎓 Program Builder (green icon) | 🎙️ Podcast Builder (red/coral icon) | 📞 Sales Scripts (amber icon)

Row 4:
- 🌐 Website Builder (cyan icon) | (empty) | (empty)

Each icon should be a distinct color — not all the same. The icons are inside colored circular backgrounds (like Genspark's agent icons). Outlined icon style on the colored circle.

Clicking any builder opens a new IQ Claw chat pre-seeded with that builder's context.

### Section 3 — "Recent Chats" (bottom)

Header: "Recent" in bold dark text, 12px, with a "View All →" teal link on the right

A compact list of the 5 most recent conversations. Each entry is a single row:
- Small icon (matching the conversation topic) + conversation title (truncated) + time/date on the right in gray

1. 📝 Content batch for April Week 2 — 2h ago
2. 📊 Weekly performance review — 5h ago
3. 📋 Webinar script revisions — Yesterday
4. ✉️ Email sequence for new leads — Yesterday
5. 🚀 Campaign launch plan — Last week

Each row is clickable with a subtle hover state (light gray background).

---

## DESIGN NOTES
- Show this flyout OPEN in the design, overlaying the left portion of the chat
- The rest of the workspace (chat + right panel) should be visible but slightly dimmed or just partially covered by the flyout
- The flyout should have a small triangle/arrow pointer on its left edge pointing toward the "+ New" button on the sidebar (optional — only if it looks clean)
- The overall feel should match Genspark's "New" flyout exactly — a rich, organized panel of options with colored icons in a grid
