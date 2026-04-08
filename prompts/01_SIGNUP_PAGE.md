# ClinicIQ — Sign-Up Page Prompt
## For Lovable / AI Builder Platform
---

## What To Build

A single-page sign-up screen for ClinicIQ — an AI-powered growth platform for health practitioners. This is the first thing a new expert sees. It needs to feel premium, modern, and fast — not like a SaaS tool, more like signing up for a private service.

## Design Direction

- **Dark theme.** Background: deep navy/charcoal (#0F1419 or similar). Not black — rich and warm.
- **Accent color:** Electric teal/cyan (#00D4AA or similar) for CTAs and highlights.
- **Typography:** Clean sans-serif. Inter, Plus Jakarta Sans, or similar. Large, confident headings.
- **Layout:** Two-column on desktop. Left side is the value proposition / visual. Right side is the sign-up form. Single column stacked on mobile.
- **Feel:** Premium. Minimal. Confident. Think Stripe's sign-up page meets a high-end health brand. No clutter. No feature lists. No screenshots.

## Left Column (Desktop) / Top Section (Mobile)

**Headline:**
"Your AI Growth Team Is Ready."

**Subheadline:**
"ClinicIQ builds, runs, and optimizes your entire marketing engine — content, ads, funnels, email, webinars — in your voice, for your patients."

**Below the subheadline, three proof points with small icons:**
- ✦ "Content that sounds like you wrote it on your best day"
- ✦ "From onboarding to first content batch in under 30 minutes"
- ✦ "174 AI agents working behind one conversation"

**At the bottom of the left column:**
A subtle testimonial or social proof line:
"Trusted by 200+ health practitioners across functional medicine, chiropractic, PT, and integrative health."

**Background visual element:** A subtle, abstract gradient mesh or soft geometric pattern behind the left column. Not an image — a design element. Premium and understated.

## Right Column — The Sign-Up Form

**Form card:** Slightly elevated card with a subtle border or shadow. Background slightly lighter than the page background (#1A1F2E or similar). Rounded corners (12-16px).

**Card header:**
"Get Started — Free"
Small text below: "No credit card required. Set up takes 2 minutes."

**Form fields (in order):**

1. **Full Name**
   - Placeholder: "Dr. Sarah Chen"
   - Required

2. **Email**
   - Placeholder: "sarah@example.com"
   - Required

3. **Password**
   - Placeholder: "Create a password"
   - Required
   - Show/hide toggle icon

4. **Your Website URL**
   - Placeholder: "https://yourpractice.com"
   - Required
   - Small helper text below the field: "We'll analyze your site to personalize your experience before you even log in."

5. **Your Primary Specialty** (dropdown)
   - Options: "Functional Medicine", "Chiropractic", "Physical Therapy", "Naturopathic Medicine", "Dentistry / TMJ", "Med Spa / Aesthetics", "Mental Health / Integrative Psychiatry", "Nutrition / Dietetics", "Health Coaching", "Other"
   - Required

6. **Instagram Handle** (optional)
   - Placeholder: "@yourhandle"
   - Small helper text: "Optional — helps us understand your voice faster."

**CTA Button:**
- Full-width within the card
- Teal/cyan background (#00D4AA), white text
- Text: "Start Building →"
- Hover state: slightly lighter, subtle lift shadow
- Large (48-56px height). Confident.

**Below the button:**
Small text: "By signing up, you agree to our Terms of Service and Privacy Policy." (linked)

**Below that:**
"Already have an account? Log in" (link)

## Technical Notes

- The form should feel snappy. No page transitions between fields.
- The specialty dropdown helps route the expert to specialty-specific onboarding questions and pre-populates the dossier with specialty norms.
- On successful submission, redirect to the onboarding screen (prompt 02). The Web Scraper sub-agent begins running immediately on the website URL provided — the onboarding screen will show the results.
- Responsive: on mobile, the left column content stacks above the form card.
- The form card should have a subtle entrance animation (fade up from below, 300ms) when the page loads.

## What NOT To Build

- No feature comparison tables
- No pricing section
- No navigation bar with multiple links (just the logo top-left and a "Log in" link top-right)
- No video embeds
- No chatbot widget
- No lengthy explanations of what the platform does — the headline and three proof points are enough
- No "book a demo" flow — this is direct self-serve signup

## The Whole Page In One Sentence

A clean, dark, premium sign-up page that collects name, email, password, website URL, specialty, and optionally Instagram — with a clear value proposition on the left and a fast, confident form on the right.
