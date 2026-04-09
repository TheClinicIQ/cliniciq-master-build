# ClinicIQ — Settings Page: Complete Build Spec
## Route: `/settings` — The single destination for all platform configuration

---

## WHAT THIS IS

The Settings page is where the expert configures everything about their account and platform preferences. It absorbs items that were previously scattered (sidebar gear, More flyout preferences, right panel Settings tab) into one comprehensive, well-organized page.

**Route:** `/settings`
**Layout:** Sidebar rail (72px) + full-width content. No chat, no right panel. Same layout as Home, Teams, Drive.
**Sidebar state:** Settings gear icon at the bottom is highlighted (white circle active state).

---

## PAGE STRUCTURE

**Left sidebar navigation** (inside the content area, not the app sidebar):
A vertical nav list on the left (220px wide) with the settings categories. Content area to the right shows the selected category's settings.

```
┌──────────┬──────────────────────────────────────────────────────┐
│ Sidebar  │                                                      │
│ rail     │  ┌──────────┬───────────────────────────────────────┐│
│ (72px)   │  │ Settings │                                       ││
│          │  │ nav      │   Settings content area               ││
│          │  │ (220px)  │   (selected category)                 ││
│          │  │          │                                       ││
│          │  │ Account  │   [Account settings form]             ││
│          │  │ Appear.  │                                       ││
│          │  │ Notifs   │                                       ││
│          │  │ Language  │                                       ││
│          │  │ Billing  │                                       ││
│          │  │ Brand    │                                       ││
│          │  │ Team     │                                       ││
│          │  │ Advanced │                                       ││
│          │  │          │                                       ││
│          │  └──────────┴───────────────────────────────────────┘│
└──────────┴──────────────────────────────────────────────────────┘
```

---

## SETTINGS NAV (Left column, 220px)

**Header:** "Settings" (20px, bold, #1F2937) at the top with 24px padding.

**Nav items:** Vertical list, each item:
- 40px height, padding 8px 16px, rounded-lg
- Icon (Lucide, 18px, #6B7280) + label (14px, #374151)
- Active: #F0FDF4 bg, emerald left border (3px), #065F46 text, icon in #10B981
- Hover: #F3F4F6 bg

**Nav items in order:**

1. **👤 Account** — User icon
2. **🎨 Appearance** — Palette icon (Lucide `Palette`)
3. **🔔 Notifications** — Bell icon
4. **🌐 Language** — Globe icon
5. **💳 Billing** — CreditCard icon
6. **🧬 Brand** — Dna icon (Lucide `Dna`)
7. **👥 Team** — Users icon
8. **⚙️ Advanced** — Settings icon (Lucide `Settings2`)

"Account" is selected by default when navigating to `/settings`.

---

## SETTINGS CONTENT — Each Category

### 1. ACCOUNT (`/settings/account`)

**Header:** "Account" (18px, bold) + "Manage your personal account details" (13px, #6B7280)

**Form sections:**

**Profile**
- Avatar: 80px circle showing current initials. [Change avatar] emerald text link below → file upload (jpg/png, max 2MB). Preview before save.
- Full name: text input, pre-filled "Dr. Sarah Chen"
- Email: text input, pre-filled, with a "Verified ✅" emerald badge. Changing email requires re-verification.
- Phone: text input, optional

**Security**
- Password: [Change password →] link → inline form: current password, new password, confirm. Password strength indicator (bar that fills: red→amber→emerald).
- Two-factor authentication: toggle switch. Off by default. When enabled: QR code setup flow for authenticator app.

**Timezone**
- Dropdown: auto-detected timezone shown, changeable. Affects all scheduled content and calendar displays.

**Danger Zone**
- Red-tinted card (#FEF2F2 bg, red border) at the bottom:
  - "Delete Account" — red text button
  - "This permanently deletes your account, all content, all data, and all connected services. This cannot be undone."
  - Click → confirmation modal: type "DELETE" to confirm → final [Delete My Account] red button

**[Save Changes]** emerald button, bottom-right of form. Disabled until changes are made. Loading spinner on submit. Toast: "Account updated" on success.

---

### 2. APPEARANCE (`/settings/appearance`)

**Header:** "Appearance" (18px, bold) + "Customize how ClinicIQ looks" (13px, #6B7280)

**Theme**
- 3 option cards in a row (140px wide each):
  - ☀️ **Light** — white card with light UI preview thumbnail. Currently active: emerald border + checkmark badge.
  - 🌙 **Dark** — dark card with dark UI preview thumbnail. "Coming Soon" badge overlay (amber pill, 10px). Not clickable.
  - 💻 **System** — split card (half light, half dark) preview. "Coming Soon" badge. Not clickable.
- Clicking Light does nothing (already active). Dark/System show tooltip: "Coming in a future update."

**Compact Mode** (future)
- Toggle: "Compact mode" — reduces padding and font sizes throughout the platform.
- Status: "Coming Soon" gray text. Toggle disabled.

**Sidebar Position** (future)
- Radio: Left (default) / Right
- Status: "Coming Soon" gray text. Radios disabled.

---

### 3. NOTIFICATIONS (`/settings/notifications`)

**Header:** "Notifications" (18px, bold) + "Control what notifications you receive and how" (13px, #6B7280)

**Notification type toggles:**

A table/grid with rows = notification types, columns = channels.

| Notification | In-App | Email | SMS | Push |
|-------------|--------|-------|-----|------|
| Content ready for review | ✅ | ✅ | ○ | ✅ |
| Engine completed | ✅ | ✅ | ○ | ✅ |
| Performance alerts | ✅ | ✅ | ✅ | ✅ |
| Weekly digest | ✅ | ✅ | ○ | ○ |
| Team activity | ✅ | ○ | ○ | ○ |
| Billing & account | ✅ | ✅ | ○ | ○ |
| IQ recommendations | ✅ | ○ | ○ | ✅ |
| System updates | ✅ | ✅ | ○ | ○ |

Each cell: toggle switch (emerald when on, gray when off). ✅ = on by default. ○ = off by default.

- Table header: sticky. Column labels (12px, bold, #374151).
- Rows: 48px height, alternating #FFFFFF / #FAFBFC bg.

**Quiet Hours**
- Toggle: "Enable quiet hours"
- When on: two time pickers — "From" and "To" (e.g., 10:00 PM → 7:00 AM)
- "During quiet hours, only critical alerts (integration failures, billing issues) will notify you."

**[Save Preferences]** emerald button.

---

### 4. LANGUAGE (`/settings/language`)

**Header:** "Language" (18px, bold) + "Choose your preferred language" (13px, #6B7280)

**Language selector:**
Radio button list, each option a full-width row (48px, hover #F3F4F6):

- 🇺🇸 English (selected — emerald radio fill + bold text)
- 🇪🇸 Español — "Beta" gray badge
- 🇧🇷 Português — "Beta" badge
- 🇫🇷 Français — "Beta" badge
- 🇩🇪 Deutsch — "Beta" badge
- 🇨🇳 中文 — "Beta" badge
- 🇯🇵 日本語 — "Beta" badge
- 🇰🇷 한국어 — "Beta" badge

"Beta languages are machine-translated and may contain errors. Help us improve by reporting issues." (12px, #6B7280, bottom)

**[Save Language]** emerald button. Triggers toast + page reload in selected language.

---

### 5. BILLING (`/settings/billing`)

**Header:** "Billing" (18px, bold) + "Manage your subscription and payments" (13px, #6B7280)

**Current Plan card:**
- White card, emerald left border (4px), rounded-xl, padding 20px
- Plan name: "Pro Plan" (18px, bold, #1F2937) + "Active" emerald badge
- Price: "$297/month" (14px, #6B7280)
- Features list: 3–4 bullet points of what's included
- [Change Plan] emerald outlined button + [Cancel Subscription] red text link

**Payment Method:**
- Card icon + "Visa ending in 4242" + "Expires 12/27"
- [Update Payment Method →] emerald text link → opens Stripe/payment modal

**Usage This Month:**
- Progress bars for any metered usage:
  - "Builder runs: 47 of unlimited" (emerald bar)
  - "Storage: 2.1 GB of 50 GB" (emerald bar)
  - "Team members: 1 of 5" (emerald bar)

**Invoice History:**
- Table: Date, Description, Amount, Status, [Download PDF]
- 3–5 recent invoices shown. [View all invoices →]

---

### 6. BRAND (`/settings/brand`)

**Header:** "Brand" (18px, bold) + "Your visual identity and brand assets" (13px, #6B7280)

**Logo:**
- Current logo preview (80px) + [Upload new logo] + [Remove]
- Accepts: png, svg, jpg. Max 2MB.

**Brand Colors:**
- 3 color swatches with hex inputs:
  - Primary: [color picker] #10B981
  - Secondary: [color picker] #1E3A5F
  - Accent: [color picker] #FDF8F0
- "These colors are used in your generated content, funnel pages, and brand assets."

**Brand Fonts:**
- Dropdown: select from available fonts (Inter, Plus Jakarta Sans, Lato, Open Sans, Playfair Display, etc.)
- Preview: "Aa — The quick brown fox" in selected font

**[Save Brand Settings]** emerald button.

---

### 7. TEAM (`/settings/team`)

**Header:** "Team" (18px, bold) + "Manage team members and permissions" (13px, #6B7280)

**Members table:**
| Member | Role | Status | Actions |
|--------|------|--------|---------|
| Dr. Sarah Chen (you) | Owner | Active | — |
| Admin invite link | — | — | [Copy link] |

- [+ Invite Member] emerald button → modal: email + role (Admin/Editor/Viewer) + [Send Invite]
- Roles:
  - **Owner:** Full access. Billing. Can delete account.
  - **Admin:** Full access except billing and account deletion.
  - **Editor:** Can use builders, review content, manage calendar. Cannot change settings or billing.
  - **Viewer:** Read-only access to dashboard, content library, and analytics.

**Permissions matrix** (below the table):
Table showing each role and what they can access. Checkmarks/crosses for each capability.

---

### 8. ADVANCED (`/settings/advanced`)

**Header:** "Advanced" (18px, bold) + "Developer settings and data management" (13px, #6B7280)

**API Access:**
- API key display (masked: `sk-****...****`) + [Reveal] + [Regenerate]
- "Use this key to integrate ClinicIQ with custom tools."
- [View API Documentation →] link

**Data Export:**
- [Export All Data] button → downloads a ZIP of: dossier, content library, analytics history, voice DNA profile
- "Your data, your rules. Export everything anytime."

**Webhook URL:**
- Text input for custom webhook endpoint
- "Receive real-time events (content published, engine completed, new lead) at this URL."

**Connected Accounts:**
- List of OAuth connections (Google, Facebook, Instagram, etc.) with [Disconnect] buttons
- This is the auth-level connection management — Services page handles the feature-level integration config

**Reset Platform:**
- Amber-tinted card (#FFFBEB bg, amber border):
  - "Reset Platform Data" — amber text button
  - "This resets your dossier, voice DNA, content library, and analytics. Your account and billing are not affected. Useful if you want to re-onboard from scratch."
  - Click → confirmation modal: type "RESET" → [Reset Platform]

---

## PAGE DESIGN SYSTEM

- **Content width:** max-width 720px for the settings content (right of the nav). Centered within the available space.
- **Form inputs:** 40px height, border 1px #E5E7EB, rounded-lg (8px), padding 0 12px, 14px text. Focus: emerald border + glow.
- **Form labels:** 13px, #374151, bold, 6px margin-bottom.
- **Form sections:** separated by 1px #E5E7EB dividers with 24px margin top/bottom. Section titles: 16px, bold, #1F2937.
- **Save buttons:** emerald bg, white text, bold, rounded-lg, 40px height, padding 0 24px. Disabled state: #9CA3AF bg.
- **Toggle switches:** 36px wide, 20px tall, emerald when on, #E5E7EB when off. 200ms transition.
- **Cards within settings:** White bg, 1px #E5E7EB border, rounded-xl, padding 20px.
- **Nav width:** 220px, fixed, border-right 1px #E5E7EB.

---

## RESPONSIVE

- **Desktop (>1024px):** Side nav (220px) + content area as described
- **Tablet (768–1024px):** Side nav collapses to horizontal tab bar at top of content area
- **Mobile (<768px):** Full-width, nav becomes a dropdown selector at the top: "Settings: Account ▾"

---

## MOCK DATA

```typescript
const mockBilling = {
  plan: "Pro",
  price: "$297/month",
  status: "active",
  card: { brand: "Visa", last4: "4242", expiry: "12/27" },
  usage: {
    builderRuns: { used: 47, limit: "unlimited" },
    storage: { used: 2.1, limit: 50, unit: "GB" },
    teamMembers: { used: 1, limit: 5 },
  },
  invoices: [
    { date: "Apr 1, 2026", description: "Pro Plan — April", amount: "$297.00", status: "Paid" },
    { date: "Mar 1, 2026", description: "Pro Plan — March", amount: "$297.00", status: "Paid" },
    { date: "Feb 1, 2026", description: "Pro Plan — February", amount: "$297.00", status: "Paid" },
  ],
};

const mockTeam = [
  { name: "Dr. Sarah Chen", email: "sarah@signalreset.com", role: "Owner", status: "Active", avatar: "SC" },
];
```

---

## THE PRINCIPLE

Settings is the **control room** — everything the expert configures lives here, organized logically, nothing hidden. Every page in the platform that has configurable options (appearance, notifications, language, billing, brand, team, API) points back to one place: `/settings`. No more scattered preferences across More flyouts, right panel tabs, and gear icons. One page. Everything.
