# ClinicIQ — "More" Flyout v3: Final
## Stripped to only what has no other home. Zero redundancy.

---

## THE PROBLEM WITH v2

Too many items that already live elsewhere:
- Analytics → Dashboard tab already shows metrics. Full analytics page is v2.
- Channels → already a right panel tab
- Services → already a right panel tab
- Training → already a right panel tab
- Manage Account → gear icon already goes to /settings

More should ONLY contain things with no other entry point in the platform.

---

## THE NEW MORE: 5 ITEMS + ACCOUNT

Tight. Clean. Everything earns its spot because it has nowhere else to live.

---

## FLYOUT STYLING

Same container: 320px wide (narrower now — less content needs less space), white bg, rounded-2xl, shadow-xl, anchored to sidebar. Same animations.

---

## FLYOUT CONTENT

### Item 1: Notifications
- Icon: Bell (Lucide, 20px, #374151)
- Label: "Notifications" (14px, #1F2937)
- Right: emerald badge with unread count ("3"). Hidden when 0.
- Click → inline notification panel (slides in, shows 5 most recent with colored severity dots, [← Back] to return, [View all →] links to `/notifications`)
- **Why it's here:** Only place to access the full notification stream. Dashboard "Needs Attention" is a curated subset — this is the full log.

---

### DIVIDER

---

### Item 2: Hub
- Icon: Compass (Lucide `Compass`, 20px, #374151) — compass signals exploration/discovery
- Label: "Hub" (14px, #1F2937)
- Right: "NEW" emerald pill badge (for first-time users who haven't visited yet)
- Click → `/hub`
- **What Hub IS:** The ClinicIQ community and discovery center. Three sections:
  1. **Engine Templates** — browse growth engines shared by other practitioners and the ClinicIQ team. "Dr. Martinez's 30-Day Challenge Funnel" with stats (42 practitioners using it, avg 3.2% conversion). Experts can publish their own engines as templates.
  2. **Content Inspiration** — anonymized top-performing content across the ClinicIQ network. "This week's highest-engagement hooks in functional medicine." Not copying — seeing what's working in the ecosystem to spark ideas.
  3. **Platform Updates** — what's new, what's coming, feature requests, community discussions.
- Think: **App Store meets Reddit meets Changelog.** It's where ClinicIQ stops being a solo tool and becomes a network. The practitioner realizes they're part of something bigger.
- **For v1:** Build the page shell with 3 sections. Populate with mock data (5 featured engine templates, 5 content inspiration items, 3 platform updates). Real community data comes later. The page should look complete and premium even with mock content.
- **Why it's here:** Unique feature — no other surface leads to community/discovery.

---

### Item 3: Help & Support
- Icon: HelpCircle (Lucide, 20px, #374151)
- Label: "Help & Support" (14px, #1F2937)
- Right: ChevronRight
- Click → inline help panel:

```
┌─────────────────────────────────────┐
│  [← Back]        Help & Support     │
│  ─────────────────────────────────  │
│                                     │
│  ┌─────────────────────────────┐    │
│  │ 🔍 Search help articles...  │    │
│  └─────────────────────────────┘    │
│                                     │
│  📖 Getting Started Guide           │
│  🎥 Video Tutorials                 │
│  📋 FAQ                             │
│  🧬 Understanding Your IQ Score     │
│  ⚡ How Growth Engines Work         │
│                                     │
│  ─────────────────────────────────  │
│                                     │
│  💬 Chat with Support  < 5 min      │
│  ✉️ Email  support@cliniciq.com     │
│  📞 Book a Strategy Call            │
│                                     │
└─────────────────────────────────────┘
```

- Search input at top
- Quick help articles: 5 items, clickable, open in new tab
- Contact section: live chat, email (mailto), book a call (Calendly link)
- **Why it's here:** Only place for help — no other surface has support access.

---

### Item 4: What's New
- Icon: Sparkles (Lucide, 20px, #374151)
- Label: "What's New" (14px, #1F2937)
- Right: "NEW" emerald pill badge when unread entries exist. Hidden when all read.
- Click → `/whats-new` (changelog page with dated entries, feature descriptions, screenshots)
- **Why it's here:** Changelog has no other home. Keeps the expert aware of platform improvements.

---

### Item 5: Download App
- Icon: Smartphone (Lucide, 20px, #374151)
- Label: "Download App" (14px, #1F2937)
- Right: ChevronRight
- Click → inline panel with iOS/Android buttons + QR code (same as before)
- **Why it's here:** App download has no other entry point. Shown once, expert either downloads or doesn't.

---

### DIVIDER

---

### Account Footer (#FAFBFC background)

```
┌─────────────────────────────────────┐
│                                     │
│  [SC]  Dr. Sarah Chen               │
│        Pro Plan                     │
│                                     │
│              [Sign Out]             │
│              (red text, 12px)       │
│                                     │
└─────────────────────────────────────┘
```

- Avatar (32px emerald circle, white initials) + name (14px, bold) + plan name (12px, #6B7280)
- Plan name is a link → `/settings/billing` (emerald, hover underline)
- [Sign Out] — red text, centered below. Click → confirmation modal.
- **No "Manage Account" link** — the gear icon in the sidebar goes to `/settings`. One path, not three.

---

## WHAT WAS REMOVED AND WHY

| Removed | Why | Where It Lives Instead |
|---------|-----|----------------------|
| Analytics | Dashboard tab shows metrics. Full analytics is v2. | Dashboard tab (IQ Score, Pulse, Spotlight) |
| Channels | Already a right panel tab | Right panel → Channels tab |
| Services | Already a right panel tab | Right panel → Services tab |
| Training | Already a right panel tab | Right panel → Training tab |
| Manage Account | Gear icon goes to /settings | Sidebar gear icon → `/settings` |
| Appearance | Moved to Settings page | `/settings` → Appearance tab |
| Notification Settings | Moved to Settings page | `/settings` → Notifications tab |
| Language | Moved to Settings page | `/settings` → Language tab |

**From 12 items (v1) → 9 items (v2) → 5 items (v3).** Every item that remains has zero redundancy with any other surface in the platform.

---

## ITEM ROW STYLING

- 44px height, padding 0 16px
- Icon (20px, #374151) → 12px gap → label (14px, #1F2937) → flex → right content
- Hover: #F3F4F6 bg, rounded-md, 150ms
- Focus-visible: 2px emerald outline

---

## THE PRINCIPLE

More is now **5 items and an account footer.** If the expert can find it somewhere else in the platform, it doesn't belong in More. What remains is the notification stream, the community hub, help, changelog, and the app download. That's it. Clean enough to fit on one screen without scrolling. Premium enough that every item feels intentional.
