# ClinicIQ — Teams Page
## New component in MagicPath

---

Design the Teams page for ClinicIQ — this is where the expert manages their team members, controls access and permissions, and sees team activity. Functions exactly like Genspark's Teams page.

## LAYOUT

Same left sidebar rail (72px) — same 8 items, same styling. "Teams" is the ACTIVE item (white circle highlight behind the people icon).

Full-width content area after sidebar. Light background (#F8F9FA).

## TOP SECTION — Page Header

Full-width white bar, subtle bottom border:

Left side:
- "Teams" — large bold text (24px)
- "Manage your team, roles, and permissions" — gray subtext

Right side:
- [+ Invite Member] button in teal — rounded, bold
- Next to it: a subtle gray pill showing "4 members · 2 online"

## TAB BAR

Horizontal tabs:

**Members | Roles | Activity | Settings**

"Members" is active by default (teal + underline).

---

## "Members" TAB (default)

### Search & Filter Row
- Search field: "Search members..." with magnifying glass icon
- Filter dropdown: [All Roles ▾]
- View toggle: list view (active) | grid view

### Members Table

A clean table with columns:

| Member | Role | Status | Last Active | Permissions | Actions |
|--------|------|--------|-------------|-------------|---------|

**Row 1 — Owner:**
- Avatar: Teal circle "SC" + "Dr. Sarah Chen" bold + "sarah@thehealthinstitute.com" gray below
- Role: "Owner" — teal badge
- Status: 🟢 "Online" green text
- Last Active: "Now"
- Permissions: "Full Access" — gray text
- Actions: ••• menu (grayed out — can't edit owner)

**Row 2 — Admin:**
- Avatar: Purple circle "JA" + "Josh Axe" bold + "josh@ancientnutrition.com" gray
- Role: "Admin" — purple badge
- Status: 🟢 "Online" green text
- Last Active: "Now"
- Permissions: "Full Access" — gray text
- Actions: ••• menu

**Row 3 — Editor:**
- Avatar: Blue circle "ML" + "Maria Lopez" bold + "maria@thehealthinstitute.com" gray
- Role: "Editor" — blue badge
- Status: ⚪ "Offline" gray text
- Last Active: "2 hours ago"
- Permissions: "Can edit content, cannot manage billing" — gray text
- Actions: ••• menu

**Row 4 — Viewer:**
- Avatar: Gray circle "TW" + "Tom Wilson" bold + "tom@thehealthinstitute.com" gray
- Role: "Viewer" — gray badge
- Status: ⚪ "Offline" gray text
- Last Active: "Yesterday"
- Permissions: "View only — analytics and content" — gray text
- Actions: ••• menu

Table styling:
- Alternating row backgrounds: white / #FAFBFC
- Subtle hover state on each row
- Avatar circles are 36px with initials in white text on colored background
- Role badges: small rounded pills with role-specific colors (teal=owner, purple=admin, blue=editor, gray=viewer)
- The ••• menu expands to: Edit Role, Edit Permissions, Remove from Team

### Below the Table

"4 of 5 seats used" — gray text with a subtle progress bar (4/5 filled in teal)
"Upgrade to add more team members" — teal link (if near seat limit)

---

## "+ Invite Member" Flow

When [+ Invite Member] is clicked, a modal/overlay appears centered on page:

White card, 480px wide, 16px rounded corners, soft shadow.

Header: "Invite a Team Member" — bold, with ✕ close button top-right.

**Form fields:**

1. **Email Address**
   - Input: "name@example.com"
   - Required

2. **Role** — dropdown with descriptions
   - **Admin** — "Full access to everything including billing and team management"
   - **Editor** — "Can create, edit, and approve content. Cannot manage billing or team."
   - **Viewer** — "View-only access to analytics, content, and reports. Cannot edit."

3. **Permissions (checkboxes, pre-filled based on role selection, editable):**
   - ☑️ View analytics and reports
   - ☑️ View content library
   - ☑️ Edit and approve content
   - ☑️ Launch workflows and builders
   - ☑️ Manage email sequences
   - ☑️ Manage ad campaigns
   - ☐ Manage billing and subscription
   - ☐ Manage team members
   - ☐ Edit brand profile and strategy

   When "Admin" is selected: all checked. When "Editor": top 6 checked. When "Viewer": top 2 only.

4. **Personal note (optional)**
   - Textarea: "Add a message to the invite..."

**Buttons at bottom:**
[Cancel] gray + [Send Invite] teal

Below the form: "They'll receive an email invitation to join your ClinicIQ workspace."

---

## "Roles" TAB

Header: "Team Roles" — subtitle "Define what each role can access and do"

3 role cards stacked vertically. Each card: white, subtle border, padded.

**Card 1 — Admin:**
- Purple badge "Admin" + "Full platform access"
- Permissions grid (2 columns of checkmarks):
  ✅ View analytics | ✅ Manage billing
  ✅ Edit content | ✅ Manage team
  ✅ Launch workflows | ✅ Edit brand/strategy
  ✅ Manage email | ✅ Manage ads
- "2 members with this role" — gray text
- [Edit Role →] teal link

**Card 2 — Editor:**
- Blue badge "Editor" + "Content creation and management"
- Permissions grid:
  ✅ View analytics | ❌ Manage billing
  ✅ Edit content | ❌ Manage team
  ✅ Launch workflows | ❌ Edit brand/strategy
  ✅ Manage email | ✅ Manage ads
- "1 member with this role"
- [Edit Role →]

**Card 3 — Viewer:**
- Gray badge "Viewer" + "View-only access"
- Permissions grid:
  ✅ View analytics | ❌ Manage billing
  ✅ View content (read only) | ❌ Manage team
  ❌ Launch workflows | ❌ Edit brand/strategy
  ❌ Manage email | ❌ Manage ads
- "1 member with this role"
- [Edit Role →]

Below the cards: [+ Create Custom Role] teal outlined button

---

## "Activity" TAB

Header: "Team Activity" with date range filter: [Today | This Week | This Month | All Time] and member filter dropdown [All Members ▾]

Activity feed — timeline style, newest first. Each entry: avatar circle + description + timestamp.

- 🟢 **SC** Dr. Sarah Chen approved 3 content items — 2 hours ago
- 🟢 **SC** Dr. Sarah Chen launched "Content Batch — April Week 2" workflow — 2 hours ago
- 🔵 **ML** Maria Lopez edited email subject line in Welcome Sequence — 5 hours ago
- 🔵 **ML** Maria Lopez uploaded 2 video testimonials to Proof Bank — 5 hours ago
- 🟣 **JA** Josh Axe reviewed Monthly Strategy Refresh — Yesterday
- 🟣 **JA** Josh Axe commented on Ad Set B replacement hooks: "Hook A is stronger" — Yesterday
- ⚪ **TW** Tom Wilson viewed Weekly Performance Report — Yesterday
- 🟢 **SC** Dr. Sarah Chen updated Voice DNA — banned word added: "biohacking" — 2 days ago
- 🔵 **ML** Maria Lopez created 5 new Instagram post drafts — 2 days ago
- 🟣 **JA** Josh Axe approved Webinar Script v2 — 3 days ago

Each entry:
- Colored avatar circle matching the member's color
- Bold member name + action description
- Timestamp right-aligned in gray
- Subtle bottom border between entries
- Clicking any entry navigates to the relevant item (the content piece, the workflow, the email, etc.)

Pagination at bottom: "Showing 10 of 47 activities" + [Load More]

---

## "Settings" TAB

Header: "Team Settings"

**Section 1: General**
White card:
- Team name: "The Health Institute" — editable text field + [Save]
- Team URL: "thehealthinstitute.cliniciq.com" — gray, non-editable
- Default timezone: "Central Time (CT)" — dropdown

**Section 2: Invite Settings**
White card:
- "Allow admins to invite members" — toggle switch (ON)
- "Require owner approval for new invites" — toggle switch (OFF)
- "Auto-assign role for new invites:" — dropdown [Editor ▾]

**Section 3: Notifications**
White card:
- "Notify owner when content is approved" — toggle (ON)
- "Notify owner when workflows complete" — toggle (ON)
- "Notify editors on new content assignments" — toggle (ON)
- "Weekly team activity digest" — toggle (ON)

**Section 4: Danger Zone**
White card with subtle red left border:
- "Transfer ownership" — [Transfer →] red outlined button
- "Delete team workspace" — [Delete →] red outlined button
- Both with small gray warning text beneath

---

## DESIGN NOTES

- This page manages the human side of the platform. Who has access, what they can do, what they've been doing.
- The Members table is the primary view — clean, scannable, with clear role indicators and status.
- The invite modal is straightforward — email, role, permissions, done. No complexity.
- The Activity tab is critical for transparency — especially when multiple team members are using the platform. The owner needs to see who did what.
- Role badges are color-coded consistently: teal (owner), purple (admin), blue (editor), gray (viewer). These colors carry through the entire page.
- Same light theme, white cards on #F8F9FA, teal accents for interactive elements.
- The overall feel: professional team management. Clean, organized, trustworthy. Like Genspark's Teams but tailored for a health practice team.
