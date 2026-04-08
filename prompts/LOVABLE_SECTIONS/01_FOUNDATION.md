# SECTION 1: Foundation — Design System, Routes, Sidebar, Flyouts
## Paste this FIRST into Lovable

Build the foundation of a React web application called ClinicIQ — an AI growth platform for health practitioners. This first prompt sets up the design system, routing, sidebar navigation, and flyout menus. Use Tailwind CSS and shadcn/ui.

## DESIGN SYSTEM
- Light mode only. Background #F8F9FA. Cards #FFFFFF with border #E5E7EB.
- Text: #1F2937 primary, #6B7280 secondary, #9CA3AF placeholder.
- Accent: #10B981 emerald for CTAs, active states, links.
- Alerts: #EF4444 red, #F59E0B amber, #22C55E green.
- Border radius: 12px cards, 8px buttons, 24px inputs.
- Font: Inter. Icons: Lucide React.
- Aesthetic: Premium, clean, minimal. Stripe meets health brand. White cards on light gray.

## ROUTES
/signup, /login, /onboarding, / (main IQ workspace — default), /home, /workflows, /teams, /drive

All routes except /signup and /login share the left sidebar.

## LEFT SIDEBAR (72px wide, shared component)
White background (#F8F9FA). Subtle right border #E5E7EB. Items center-aligned vertically. Each: 20px Lucide icon + 10px gray label beneath.

Items top to bottom:
1. Logo — dark rounded square (32px) with Sparkles icon inside. No label. Top with 16px padding.
2. + New — Plus icon. Label "New". Opens flyout on click.
3. Home — House icon. Label "Home". Links to /home.
4. IQ — BrainCircuit icon. Label "IQ". Links to /. This is the main product button.
5. Workflows — GitBranch icon. Label "Workflows". Links to /workflows.
6. Teams — Users icon. Label "Teams". Links to /teams.
7. Drive — FolderOpen icon. Label "Drive". Links to /drive. Small red badge "3".
8. More — MoreHorizontal icon. Label "More". Opens flyout on click.

Bottom pinned: Settings gear icon (no label) + 28px accent circle with "SC" initials + tiny "Dr. Sarah Chen" text.

Active state: white circle (36px) behind icon, icon turns #1F2937. Inactive: #9CA3AF. Hover: #6B7280.

## FLYOUT: "+ New" (480px wide, white, rounded-xl, shadow-xl, slides from sidebar edge)
Closes on click-outside or Escape.

Section 1 — "Quick Actions" header. Three horizontal cards:
- Quick Post "One post, any topic" (FileText icon, teal circle)
- Quick Email "Single email, any type" (Mail icon, blue circle)
- Quick Ad "Hook + creative + copy" (Megaphone icon, orange circle)

Section 2 — "Builders" header. 3-column grid of 12 builder icons (each: 48px colored circle + label below):
Row 1: Content Builder | Funnel Builder | Webinar Builder
Row 2: Email Builder | Ad Creative | Lead Magnet
Row 3: Program Builder | Podcast Builder | Sales Scripts
Row 4: Website Builder | Campaign Builder | Challenge Builder

Section 3 — "Recent" header + "View All →" link. List of 5 mock recent chats (icon + title + "2h ago" style timestamps).

## FLYOUT: "More" (280px wide)
Items: Inbox (badge "2 new"), Hub (arrow →). Divider. Dark Mode toggle (off), Help & Support (arrow →), Download App (arrow →). Bottom: profile card (SC avatar + "Dr. Sarah Chen" + "Pro Plan" + gear icon).

## PLACEHOLDER PAGES
For now, create placeholder pages for each route with just the sidebar + a centered heading showing the page name. We'll fill in each page in the next prompts.

Make sure navigation works — clicking sidebar items changes routes and updates the active state.
