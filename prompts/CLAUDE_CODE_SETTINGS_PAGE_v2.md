# ClinicIQ — Settings Page v2: Expand What's Already Built
## Keep the existing horizontal tab layout. Add the missing tabs and flesh out every section.

---

## WHAT EXISTS NOW

The Settings page (`/settings`) already has:
- Horizontal tab bar: **Profile | Billing | Team | Notifications | API Keys**
- Profile tab: avatar (JD initials) + Upload button, Full name, Email, Practice name, Specialty, [Save changes] button
- Centered column layout, clean and minimal

This is a good foundation. **Don't change the layout pattern.** Keep the horizontal tab bar and centered column. Just expand it.

---

## WHAT TO ADD

### 1. Add 3 new tabs to the tab bar

Current tabs: Profile | Billing | Team | Notifications | API Keys

**New tab bar:** Profile | Appearance | Notifications | Language | Billing | Team | Brand | API & Advanced

Changes:
- **Appearance** — new (inserted after Profile)
- **Language** — new (inserted after Notifications)
- **Brand** — new (inserted after Team)
- **API Keys** renamed to **API & Advanced** (expanded with more developer tools)
- Tab order rearranged to: most-used first, developer stuff last

The tab bar should scroll horizontally if it overflows on narrow screens (same as the right panel tab bar behavior).

---

### 2. Expand the PROFILE tab

Keep what's there. Add these fields below the existing ones:

**Existing (keep):**
- Avatar (circle with initials) + [Upload] button
- Full name input
- Email input
- Practice name input
- Specialty input

**Add below Specialty:**

- **Phone** — text input, optional. Placeholder: "+1 (555) 000-0000"
- **Timezone** — dropdown select. Auto-detected default (e.g., "America/Chicago (CT)"). Full timezone list.
- **Website URL** — text input, pre-filled from signup. "This is the URL IQ Claw analyzed during onboarding."
- **Instagram handle** — text input, optional, pre-filled from signup. Placeholder: "@yourhandle"

**Security section** (below the form fields, separated by a divider):
- Section label: "Security" (16px, bold, #1F2937)
- **Change password** — [Change Password →] emerald text link. Click → inline form expands: Current password, New password, Confirm password. Password strength bar (red→amber→emerald). [Update Password] button.
- **Two-factor authentication** — toggle switch + description: "Add an extra layer of security to your account." Off by default. When toggled on: show QR code setup flow for authenticator app.

**Danger Zone** (bottom, separated by divider):
- Red-tinted card (#FEF2F2 bg, 1px red border, rounded-xl, padding 16px):
- "Delete Account" (14px, bold, #991B1B)
- "Permanently delete your account, all content, all data, and all connected services. This cannot be undone." (12px, #991B1B)
- [Delete Account] red outlined button → confirmation modal: type "DELETE" to confirm

**[Save Changes]** button stays at the bottom. Only active when changes are made.

---

### 3. APPEARANCE tab (new)

**Header:** "Appearance" + "Customize how ClinicIQ looks" (13px, #6B7280)

**Theme selector:**
3 cards in a row (each ~140px wide, centered):

```
┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│  ☀️          │  │  🌙          │  │  💻          │
│  Light       │  │  Dark        │  │  System      │
│  [selected]  │  │  Coming Soon │  │  Coming Soon │
└─────────────┘  └─────────────┘  └─────────────┘
```

- Light card: white bg, emerald border (2px), emerald checkmark badge top-right. Active.
- Dark card: #1F2937 bg, white text. "Coming Soon" amber badge overlay. Not clickable. `opacity: 0.6, cursor: not-allowed`.
- System card: split bg (half white, half dark). "Coming Soon" badge. Not clickable.

**Density (future):**
- Label: "Interface Density"
- Radio group: Comfortable (default) | Compact
- "Compact" radio: disabled, "Coming Soon" gray text
- "Compact mode reduces spacing for more information on screen."

That's it for Appearance in v1 — keep it clean, show what's coming.

---

### 4. NOTIFICATIONS tab (expand what exists)

If the current Notifications tab is basic, replace it with this:

**Header:** "Notifications" + "Control what you receive and how" (13px, #6B7280)

**Toggle grid:**

| Notification Type | In-App | Email | Push |
|------------------|--------|-------|------|
| Content ready for review | ✅ | ✅ | ✅ |
| Engine completed | ✅ | ✅ | ✅ |
| Performance alerts | ✅ | ✅ | ✅ |
| Weekly digest | ✅ | ✅ | ○ |
| IQ recommendations | ✅ | ○ | ✅ |
| Team activity | ✅ | ○ | ○ |
| Billing & account | ✅ | ✅ | ○ |
| System updates | ✅ | ✅ | ○ |

- Each cell: toggle switch. ✅ = on by default. ○ = off by default.
- Table: clean grid, 48px row height, alternating row bg (#FFFFFF / #FAFBFC)
- Column headers: 12px, bold, #374151

**Quiet Hours:**
- Toggle: "Enable quiet hours" + description
- When on: two time pickers (From / To) — e.g., 10:00 PM → 7:00 AM
- "During quiet hours, only critical alerts notify you."

**[Save Preferences]** emerald button.

---

### 5. LANGUAGE tab (new)

**Header:** "Language" + "Choose your preferred language" (13px, #6B7280)

Radio button list, full-width rows (48px height, hover #F3F4F6):

- 🇺🇸 **English** — selected (emerald radio dot + bold text)
- 🇪🇸 Español — "Beta" gray badge
- 🇧🇷 Português — "Beta" badge
- 🇫🇷 Français — "Beta" badge
- 🇩🇪 Deutsch — "Beta" badge
- 🇨🇳 中文 — "Beta" badge
- 🇯🇵 日本語 — "Beta" badge
- 🇰🇷 한국어 — "Beta" badge

Footer: "Beta languages are machine-translated and may have errors. Help us improve by reporting issues." (12px, #6B7280)

**[Save Language]** emerald button. Toast + page reload on change.

---

### 6. BILLING tab (expand what exists)

If the current Billing tab is basic, ensure it has:

**Current Plan card:**
- Emerald left border (4px), rounded-xl, padding 20px
- "Pro Plan" (18px, bold) + "Active" emerald badge
- "$297/month" (14px, #6B7280)
- 3–4 feature bullets
- [Change Plan] emerald outlined button + [Cancel Subscription] red text link (12px)

**Payment Method:**
- Card brand icon + "Visa ending in 4242" + "Expires 12/27"
- [Update Payment Method →] emerald text link

**Usage:**
- 3 progress bars:
  - "Builder runs: 47 of unlimited" (emerald)
  - "Storage: 2.1 GB of 50 GB" (emerald)
  - "Team members: 1 of 5" (emerald)

**Invoice History:**
- Table: Date | Description | Amount | Status | [PDF]
- 3–5 rows of mock invoices

---

### 7. TEAM tab (expand what exists)

If the current Team tab is basic, ensure it has:

**Members table:**
| Member | Email | Role | Status | Actions |
|--------|-------|------|--------|---------|
| Dr. Sarah Chen | sarah@signalreset.com | Owner | 🟢 Active | — |

- [+ Invite Member] emerald button → modal: email input + role dropdown (Admin/Editor/Viewer) + [Send Invite]

**Roles explained** (below table):
- **Owner** — full access, billing, can delete account
- **Admin** — full access except billing and deletion
- **Editor** — builders, content review, calendar. No settings/billing.
- **Viewer** — read-only: dashboard, content library, analytics

---

### 8. BRAND tab (new)

**Header:** "Brand" + "Your visual identity and brand assets" (13px, #6B7280)

**Logo:**
- Current logo preview (80px square, rounded-xl, #F8F9FA bg) + [Upload Logo] + [Remove]
- Accepts: png, svg, jpg. Max 2MB.

**Brand Colors:**
3 color inputs in a row:
- Primary: color swatch (24px circle) + hex input → default #10B981
- Secondary: color swatch + hex input → default #1E3A5F
- Accent: color swatch + hex input → default #FDF8F0
- "Used in generated content, funnel pages, and brand assets."

**Brand Font:**
- Dropdown select: Inter (default), Plus Jakarta Sans, Lato, Open Sans, Montserrat, Playfair Display
- Preview text below: "Aa — The quick brown fox jumps over the lazy dog" rendered in selected font

**[Save Brand Settings]** emerald button.

---

### 9. API & ADVANCED tab (expand existing API Keys)

Keep whatever API key display exists. Add:

**API Key:**
- Masked display: `sk-****...****` + [Reveal] eye icon + [Copy] + [Regenerate] (red text, confirms before regenerating)
- "Use this key to integrate ClinicIQ with custom tools."
- [View API Documentation →] emerald text link (opens docs in new tab)

**Webhooks:**
- Label: "Webhook URL"
- Text input. Placeholder: "https://your-app.com/webhook"
- "Receive real-time events (content published, engine completed, new lead)."
- [Test Webhook] gray outlined button — sends a test payload
- Status: "Last delivery: 2h ago — ✅ 200 OK" (or "❌ Failed" in red)

**Data Export:**
- [Export All Data] emerald outlined button
- "Download a ZIP of your dossier, content library, analytics, and voice DNA."
- Estimated size: "~24 MB"

**Connected OAuth Accounts:**
- List of connected accounts with [Disconnect] buttons:
  - Google (connected ✅) [Disconnect]
  - Facebook (connected ✅) [Disconnect]
  - Instagram (connected ✅) [Disconnect]
- "Disconnecting removes platform access but preserves your published content."

**Reset Platform** (bottom, separated by divider):
- Amber-tinted card (#FFFBEB bg, amber border):
- "Reset Platform Data" (14px, bold, #92400E)
- "Resets dossier, voice DNA, content, and analytics. Account and billing unaffected. Use this to re-onboard from scratch." (12px, #92400E)
- [Reset Platform] amber outlined button → confirmation modal: type "RESET"

---

## TAB BAR DESIGN

- Horizontal, full-width within the content column
- Active tab: #1F2937 text, bold, 2px emerald bottom border
- Inactive tabs: #6B7280 text, regular weight, no border. Hover: #1F2937.
- Tab text: 14px, padding 12px 16px
- Overflow: scroll horizontally on narrow screens (hide scrollbar, swipe on mobile)
- 1px #E5E7EB bottom border on the tab bar

---

## PAGE LAYOUT

- Same as current: app sidebar (72px) + full-width centered content column
- Content max-width: 680px, centered
- Settings gear icon in sidebar: active state (white circle highlight) when on /settings
- Page title "Settings" at top (24px, bold, #1F2937) — above the tab bar

---

## MOCK DATA

Use the Dr. Sarah Chen persona:
```typescript
const mockProfile = {
  name: "Dr. Sarah Chen",
  email: "sarah@signalreset.com",
  avatar: "SC",
  practiceName: "Signal Reset Health",
  specialty: "Functional Medicine",
  phone: "+1 (512) 555-0147",
  timezone: "America/Chicago",
  website: "https://signalresethealth.com",
  instagram: "@dr.sarahchen",
};
```

---

## SUMMARY

Keep the existing layout and horizontal tab pattern. Expand from 5 tabs to 8. Flesh out every tab with complete, functional forms. The Settings page should feel like the expert has complete control over every aspect of their platform — nothing hidden, nothing broken, nothing "coming soon" except dark mode and compact density.
