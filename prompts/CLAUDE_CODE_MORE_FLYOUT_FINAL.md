# ClinicIQ — "More" Flyout: Final Version
## Lean utility menu. Only things with no other home. Revenue, growth, radar — those all went to Dashboard.

**This prompt supersedes all previous More flyout prompts (v1, v2, v3).**

---

## WHY THIS IS LEAN

Revenue Pulse → Dashboard.
Brand Growth → Dashboard.
Competitive Radar → Dashboard.
Pinned Assets → Dashboard or Content tab.
Analytics → Dashboard has scores + Performance by Category tab.
Channels/Services/Training → right panel tabs.
Appearance/Language/Notifications → Settings page.
Manage Account → Settings page (sidebar gear icon).

What's left is ONLY things with no other entry point in the platform.

---

## FLYOUT STYLING

- Width: 300px (lean content = narrower flyout)
- White bg, rounded-2xl, shadow-xl, border 1px #E5E7EB
- Anchored right of sidebar, aligned to "More" button
- Open: fade in + slide right, 200ms. Close: click outside / click More / Escape.

---

## FLYOUT CONTENT

### Item 1: Notifications
- Icon: Bell (Lucide, 20px, #374151)
- Label: "Notifications" (14px, #1F2937)
- Right: emerald badge with unread count. Hidden when 0.
- Click → inline notification panel (5 most recent, colored severity dots, [← Back], [View all →] to `/notifications`)

---

### DIVIDER

---

### Item 2: Hub
- Icon: Compass (Lucide, 20px, #374151)
- Label: "Hub" (14px, #1F2937)
- Subtitle: "Community & templates" (11px, #9CA3AF) — shown below the label on the same row
- Right: ChevronRight
- Click → `/hub`
- **What Hub is:** The ClinicIQ ecosystem. Three sections:
  1. **Shared Engines** — growth engine templates published by other practitioners. Browse, preview, launch. "Dr. Martinez's 30-Day Gut Reset Challenge — used by 42 practitioners, avg 3.2% conversion."
  2. **Inspiration Feed** — anonymized top-performing content from the network. "This week's highest-engagement hooks in functional medicine." Not copying — seeing what's working.
  3. **Community** — platform updates, feature requests, tips from other practitioners, success stories.
- For v1: build the page shell with 3 sections, populate with mock data. Real community data is v2.

---

### Item 3: Help & Support
- Icon: HelpCircle (Lucide, 20px, #374151)
- Label: "Help & Support" (14px, #1F2937)
- Right: ChevronRight
- Click → inline help panel: search bar + 5 quick help articles + contact (live chat, email, book a call)

---

### Item 4: What's New
- Icon: Sparkles (Lucide, 20px, #374151)
- Label: "What's New" (14px, #1F2937)
- Right: "NEW" emerald pill badge when unread. Hidden when read.
- Click → `/whats-new` (changelog)

---

### Item 5: Download App
- Icon: Smartphone (Lucide, 20px, #374151)
- Label: "Download App" (14px, #1F2937)
- Right: ChevronRight
- Click → inline panel with iOS/Android buttons + QR code

---

### DIVIDER

---

### Account Footer (#FAFBFC bg)

```
[SC]  Dr. Sarah Chen
      Pro Plan

      [Sign Out]
```

- Avatar (32px) + name (14px, bold) + plan (12px, #6B7280, links to /settings/billing)
- [Sign Out] red text, centered. Confirmation modal on click.
- No "Manage Account" — gear icon handles that.

---

## ITEM ROW STYLING

- 44px height, padding 0 16px
- Icon → 12px gap → label → flex → right content
- Hover: #F3F4F6, 150ms. Focus: 2px emerald outline.

---

## THAT'S IT

5 items. Account footer. No redundancy with any other surface. The dashboard absorbed all the business intelligence. Settings absorbed all the preferences. This is just: notifications, community, help, changelog, app download, sign out. Clean.
