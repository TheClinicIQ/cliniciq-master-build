# ClinicIQ — "More" Flyout v2: Cleaned Up
## Remove preferences (they belong in Settings). Keep this focused on platform features & resources.

---

## WHAT CHANGED FROM v1

Removed 3 items that belong in Settings, not More:
- ❌ Appearance (Light/Dark/System) → moved to Settings page
- ❌ Notification Settings → moved to Settings page
- ❌ Language → moved to Settings page

This makes More **9 items** instead of 12. Tighter, cleaner, no identity crisis.

**More = things you USE.** Settings = things you CONFIGURE.

---

## FLYOUT STYLING

Same as v1 — 340px wide, white bg, rounded-2xl, shadow-xl, anchored to sidebar. Same open/close animations. No changes to the container.

---

## FLYOUT CONTENT — Top to Bottom

### SECTION 1: NOTIFICATIONS

**Item 1: Notifications**
- Icon: Bell (Lucide, 20px, #374151)
- Label: "Notifications" (14px, #1F2937)
- Right: emerald badge with unread count ("3"). Hidden when 0.
- Click → inline notification panel (same as v1 — slides in, shows 5 most recent, [← Back] to return, [View all →] links to /notifications)

---

### DIVIDER

---

### SECTION 2: PLATFORM

**Header:** "PLATFORM" (10px, uppercase, #9CA3AF, letter-spacing 0.05em)

**Item 2: Analytics**
- Icon: BarChart3 (20px, #374151)
- Label: "Analytics"
- Right: trend — "↑ 12%" emerald or "↓ 8%" red
- Click → `/analytics`

**Item 3: Channels**
- Icon: Radio (20px, #374151)
- Label: "Channels"
- Right: "3 connected" (12px, #6B7280)
- Click → `/channels`

**Item 4: Services**
- Icon: Plug (20px, #374151)
- Label: "Services"
- Right: "5 active" (12px, #6B7280)
- Click → `/services`

**Item 5: Hub**
- Icon: LayoutGrid (20px, #374151)
- Label: "Hub"
- Right: ChevronRight
- Click → `/hub`

**Item 6: Training**
- Icon: GraduationCap (20px, #374151)
- Label: "Training"
- Right: mini progress bar (48px, emerald fill at 35%) + "35%"
- Click → `/training`

---

### DIVIDER

---

### SECTION 3: SUPPORT

**Header:** "SUPPORT" (10px, uppercase, #9CA3AF)

**Item 7: Help & Support**
- Icon: HelpCircle (20px, #374151)
- Label: "Help & Support"
- Right: ChevronRight
- Click → inline help panel (same as v1 — search, quick help articles, contact options)

**Item 8: What's New**
- Icon: Sparkles (20px, #374151)
- Label: "What's New"
- Right: "NEW" emerald pill badge (when unread entries exist)
- Click → `/whats-new`

**Item 9: Download App**
- Icon: Smartphone (20px, #374151)
- Label: "Download App"
- Right: ChevronRight
- Click → inline download panel (iOS/Android buttons + QR code, same as v1)

---

### DIVIDER

---

### SECTION 4: ACCOUNT (bottom, #FAFBFC background)

```
[SC]  Dr. Sarah Chen
      Pro Plan · Joined Mar 2026

[Manage Account]          [Sign Out]
```

- Same as v1. Avatar + name + plan + [Manage Account] (emerald) → `/settings` + [Sign Out] (red) → confirmation modal.
- **Change:** [Manage Account] now goes to `/settings` (the new full Settings page) instead of `/settings/account`.

---

## ITEM ROW STYLING

Same as v1:
- 44px height, padding 0 16px
- Icon (20px, #374151) → 12px gap → label (14px, #1F2937) → flex-grow → right content
- Hover: #F3F4F6 bg, 150ms transition
- Focus-visible: 2px emerald outline

---

## ROUTES (unchanged from v1, minus the settings sub-routes that moved)

| Route | Page |
|-------|------|
| `/notifications` | Full notification history |
| `/analytics` | Deep analytics dashboard |
| `/channels` | Social channel management |
| `/services` | Integration hub |
| `/hub` | Marketplace / resource center |
| `/training` | Platform training / LMS |
| `/whats-new` | Changelog |
| `/settings` | Full settings page (NEW — see CLAUDE_CODE_SETTINGS_PAGE.md) |

---

## WHAT ABOUT THE SIDEBAR SETTINGS GEAR?

The sidebar has a Settings gear icon pinned at the bottom. Clicking it now navigates to `/settings` — the new comprehensive Settings page that holds everything: account, appearance, notifications, language, billing, brand settings, integrations config, and team permissions.

The sidebar user avatar (below the gear) also navigates to `/settings` — it's a "me" shortcut.

Both the gear icon and the avatar go to the same place. Simple.
