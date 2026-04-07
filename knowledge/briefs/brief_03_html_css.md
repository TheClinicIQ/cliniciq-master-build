# AGENT BRIEF #3 — html_css_render_standard.md
**clinicIQ Knowledge Base | Production Layer**
**Version 1.0 — April 2026**

---

## Overview

This brief instructs the agent writing:
`/home/work/.openclaw/workspace/cliniciq/knowledge/production/html_css_render_standard.md`

---

## What the Output File Is

The complete technical production standard for every HTML/CSS asset the clinicIQ platform generates. Every agent that produces emails, landing pages, lead magnet PDFs, or quiz interfaces reads this file. It defines precisely what "production-ready HTML" means in the clinicIQ context. This is a technical reference — all standards must be specific enough that an AI agent can implement them without interpretation gaps.

---

## Source Files

None from the clinicIQ workspace. Technical standards document based on web standards knowledge. Write from knowledge — no research needed.

---

## Output Path

`/home/work/.openclaw/workspace/cliniciq/knowledge/production/html_css_render_standard.md`

---

## Format Standard

Technical reference document. Section headers, subsections, actual code blocks throughout (fenced with language tags: ```html, ```css). Explain why each standard exists, not just what it is. Every standard specific enough that an AI agent can implement it without interpretation.

---

## Quality Standard

This document defines what "production-ready" means for the clinicIQ platform. An AI agent following it must produce assets that look professional, render correctly across all target environments, and require no manual cleanup.

---

## Sections to Produce

### Section 1 — The Four Render Target Environments

For each environment: the complete constraint list, why each constraint exists, and the consequence of violating it.

**Environment 1 — Email Clients**
Target clients: Outlook 2016, Outlook 2019, Outlook 365 (desktop), Gmail web, Gmail app (iOS/Android), Apple Mail (macOS/iOS), Samsung Mail.

Constraints and why each exists:
- Table-based layout only — CSS Grid and Flexbox break in Outlook's rendering engine (Word-based, not WebKit). Using modern layout means broken emails for a significant portion of the audience.
- Inline styles only for Outlook — Outlook strips `<style>` block CSS in many versions. Inline styles are the only reliable method.
- Max container width 600px — the standard readable width across all clients at all viewport sizes.
- No web fonts in Outlook — Outlook does not support Google Fonts or @font-face. System font fallback is mandatory.
- Background images not supported in Outlook — VML (Vector Markup Language) workaround required for any background image.
- No video in email — no browser engine means no video playback. Animated GIF is the maximum motion format.
- Images require explicit width, height, display:block, border:0 — without these attributes, images render incorrectly in Outlook and create layout gaps.
- No JavaScript — security-blocked by all major clients.
- MSO conditional comments — the mechanism for targeting Outlook-specific rendering with HTML that only Outlook's engine processes.

**Environment 2 — Landing Pages (Modern Browsers)**
Targets: Chrome, Safari, Firefox, Edge — desktop and mobile.

Capabilities available:
- Full CSS3 support (Grid, Flexbox, custom properties, animations)
- Web fonts via Google Fonts or self-hosted @font-face
- JavaScript (for analytics, form handling, and lightweight interactions)
- Max content container: 1200px centered
- Mobile-first responsive: 320px minimum viewport support required

Performance targets:
- First Contentful Paint under 1.5 seconds
- No external JS dependencies except tracking pixels (GTM, Meta pixel, etc.)
- Images optimized (WebP preferred, max 200KB for above-fold images)

**Environment 3 — Lead Magnet PDF (Puppeteer/Headless Chromium)**
Targets: Headless Chromium rendering to PDF via Puppeteer.

Constraints:
- Page size: A4 (210mm × 297mm) or US Letter (8.5in × 11in) — declared in @page rule
- Print media queries are active — @media print styles apply
- @page rules control margins, page size, and page break behavior
- Page-break rules critical — broken sections destroy professional appearance
- All images must be embedded as absolute URLs or base64 data URIs — relative paths fail in headless rendering
- No external font dependencies without preloading — fonts must be loaded before Puppeteer captures the page
- No JavaScript interaction — the rendered static state is what gets captured

**Environment 4 — Quiz Interface (Embedded iFrame)**
Targets: Embedded within clinicIQ platform at variable container widths, responsive.

Constraints:
- Scoped CSS — no global resets or * selectors that affect the parent page
- CSS custom properties for theming — brand colors injected at the :host or :root level within the iframe scope
- Touch-target minimum 44px — quiz answer options must be tappable on mobile without zooming
- No external dependencies — no CDN libraries, no external fonts that could fail to load
- All assets self-contained within the iframe scope

---

### Section 2 — Email HTML Standard

**Complete Email HTML Template:**

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" 
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml" 
  xmlns:o="urn:schemas-microsoft-com:office:office">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="x-apple-disable-message-reformatting">
  <title>{{EMAIL_SUBJECT}}</title>
  <!--[if mso]>
  <noscript>
    <xml>
      <o:OfficeDocumentSettings>
        <o:PixelsPerInch>96</o:PixelsPerInch>
      </o:OfficeDocumentSettings>
    </xml>
  </noscript>
  <![endif]-->
  <style type="text/css">
    /* Reset */
    body, table, td, p, a, li, blockquote { -webkit-text-size-adjust: 100%; -ms-text-size-adjust: 100%; }
    table, td { mso-table-lspace: 0pt; mso-table-rspace: 0pt; }
    img { -ms-interpolation-mode: bicubic; border: 0; outline: none; text-decoration: none; }
    /* Mobile */
    @media only screen and (max-width: 600px) {
      .email-container { width: 100% !important; max-width: 100% !important; }
      .fluid { max-width: 100% !important; height: auto !important; }
      .stack-column, .stack-column-center { display: block !important; width: 100% !important; max-width: 100% !important; direction: ltr !important; }
      .center-on-narrow { text-align: center !important; display: block !important; margin-left: auto !important; margin-right: auto !important; float: none !important; }
    }
  </style>
</head>
<body style="margin: 0; padding: 0; background-color: {{BG_COLOR}};">
  <!-- 100% Wrapper -->
  <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%" style="background-color: {{BG_COLOR}};">
    <tr>
      <td align="center" valign="top">
        <!-- 600px Container -->
        <table role="presentation" class="email-container" cellspacing="0" cellpadding="0" border="0" 
          width="600" style="max-width: 600px; background-color: #ffffff;">
          <!-- Content Rows Go Here -->
        </table>
        <!-- End 600px Container -->
      </td>
    </tr>
  </table>
  <!-- End 100% Wrapper -->
</body>
</html>
```

**System Font Stack:**
```css
font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 
             'Helvetica Neue', Helvetica, Arial, sans-serif;
```
Why this stack: 'Inter' renders on clients where web fonts load. -apple-system and BlinkMacSystemFont target Apple devices. 'Segoe UI' is the Windows system font. Roboto is the Android system font. Helvetica/Arial as universal fallbacks. Never use a single font name alone.

**Bulletproof VML Button (renders in all Outlook versions):**
```html
<!-- Outlook VML button wrapper -->
<!--[if mso]>
<v:roundrect xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word" 
  href="{{CTA_URL}}" style="height:48px; v-text-anchor:middle; width:220px;" 
  arcsize="8%" stroke="f" fillcolor="{{BUTTON_COLOR}}">
  <w:anchorlock/>
  <center style="color:#ffffff; font-family:Arial, sans-serif; font-size:16px; font-weight:bold;">
    {{CTA_TEXT}}
  </center>
</v:roundrect>
<![endif]-->
<!-- Non-Outlook version -->
<!--[if !mso]><!-->
<a href="{{CTA_URL}}" 
   style="background-color: {{BUTTON_COLOR}}; border-radius: 6px; color: #ffffff; 
          display: inline-block; font-family: Arial, sans-serif; font-size: 16px; 
          font-weight: bold; line-height: 48px; padding: 0 24px; text-align: center; 
          text-decoration: none; -webkit-text-size-adjust: none;">
  {{CTA_TEXT}}
</a>
<!--<![endif]-->
```
Why VML: Outlook 2007–2019 uses Word's rendering engine, which does not support CSS border-radius on `<a>` tags. VML is the Microsoft Office vector format that Outlook's engine can render correctly.

**Mobile Breakpoint Pattern:**
```css
@media only screen and (max-width: 600px) {
  /* Full width on mobile */
  .email-container { width: 100% !important; }
  /* Stack two-column layouts */
  .col-half { display: block !important; width: 100% !important; }
  /* Resize images to full width */
  .hero-image { width: 100% !important; height: auto !important; }
  /* Adjust font sizes for mobile */
  .headline { font-size: 24px !important; line-height: 32px !important; }
  .body-text { font-size: 16px !important; line-height: 26px !important; }
  /* Center elements */
  .center-mobile { text-align: center !important; }
  /* Adjust padding for mobile */
  .section-padding { padding: 24px 16px !important; }
}
```

**Standard Image Element:**
```html
<img src="https://{{ABSOLUTE_IMAGE_URL}}" 
     alt="{{DESCRIPTIVE_ALT_TEXT}}" 
     width="600" 
     height="300" 
     style="display: block; border: 0; outline: none; text-decoration: none; 
            max-width: 100%; height: auto;"
     class="fluid">
```
Why every attribute: `src` must be absolute (email clients don't have access to relative path resolution). `alt` must be descriptive (many clients block images by default; alt text is what the reader sees). `width` and `height` prevent layout collapse when images are blocked. `display: block` removes the 3px gap that inline images create. `border: 0` prevents link borders in older IE. `max-width: 100%; height: auto` enables mobile responsiveness.

**Spacing system — padding only, never margins:**
```html
<!-- Correct: spacing via padding on table cells -->
<td style="padding: 24px 32px;">
  <p style="margin: 0;">Content here</p>
</td>

<!-- Wrong: never use margin for layout spacing in email -->
<!-- <td><p style="margin: 24px 32px;">Content here</p></td> -->
```
Why no margins: margin behavior is inconsistent across email clients. Outlook collapses margins in ways that produce unpredictable spacing. Padding on `<td>` elements is reliably rendered across all clients.

**MSO Conditional Comments — full pattern:**
```html
<!-- Only shown to Outlook: -->
<!--[if mso]>
  <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
    <tr><td style="background-color: {{COLOR}};">
<![endif]-->

  <!-- Content for all clients -->

<!--[if mso]>
    </td></tr>
  </table>
<![endif]-->

<!-- Hide from Outlook, show to everyone else: -->
<!--[if !mso]><!-->
  <div style="display: block;">Non-Outlook content</div>
<!--<![endif]-->
```

---

### Section 3 — Landing Page HTML Standard

**Semantic HTML5 Structure:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="{{PAGE_DESCRIPTION}}">
  <title>{{PAGE_TITLE}}</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>/* Critical CSS inlined here */</style>
  <link rel="stylesheet" href="styles.css"> <!-- deferred non-critical -->
</head>
<body>
  <header role="banner"><!-- Logo, expert name, minimal navigation --></header>
  <main role="main">
    <section class="hero" aria-label="Main offer section"><!-- Above-fold content --></section>
    <section class="proof" aria-label="Social proof"><!-- Testimonials --></section>
    <section class="mechanism" aria-label="How it works"><!-- Mechanism explanation --></section>
    <section class="offer-stack" aria-label="What's included"><!-- Stack --></section>
    <section class="guarantee" aria-label="Guarantee"><!-- Risk reversal --></section>
    <section class="faq" aria-label="Frequently asked questions"><!-- Objection handling --></section>
    <section class="final-cta" aria-label="Call to action"><!-- Final CTA --></section>
  </main>
  <footer role="contentinfo"><!-- Legal, contact, disclaimer --></footer>
</body>
</html>
```

**CSS Custom Properties — complete :root declaration:**
```css
:root {
  /* Brand Colors */
  --color-primary: #2D6A4F;       /* Trust/brand — deep forest green */
  --color-secondary: #1B4332;     /* Darker trust variant */
  --color-urgency: #D62828;       /* CTA urgency accent — warm red */
  --color-background: #FAFAF8;    /* Warm off-white */
  --color-surface: #FFFFFF;       /* Card/section backgrounds */
  --color-text-primary: #1A1A1A;  /* Main text */
  --color-text-secondary: #555555; /* Supporting text */
  --color-text-light: #888888;    /* Captions, metadata */
  --color-border: #E5E5E5;        /* Dividers, card borders */

  /* Typography */
  --font-heading: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-body: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-size-base: 18px;
  --line-height-base: 1.65;
  --font-scale: 1.333; /* Perfect fourth scale */

  /* Spacing */
  --spacing-xs: 8px;
  --spacing-sm: 16px;
  --spacing-md: 32px;
  --spacing-lg: 64px;
  --spacing-xl: 80px;
  --spacing-section: 80px;   /* Between sections desktop */
  --spacing-section-mobile: 48px; /* Between sections mobile */

  /* Layout */
  --container-max: 1200px;   /* Outer container */
  --container-content: 800px; /* Content/text container */
  --container-narrow: 680px;  /* Single-column content */

  /* Radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;
  --radius-pill: 999px;

  /* Shadows */
  --shadow-sm: 0 1px 3px rgba(0,0,0,0.08);
  --shadow-md: 0 4px 12px rgba(0,0,0,0.10);
  --shadow-lg: 0 8px 32px rgba(0,0,0,0.12);
}
```

**Mobile-First Breakpoint Structure:**
```css
/* Base styles: 320px mobile first */
.container {
  width: 100%;
  padding: 0 16px;
  margin: 0 auto;
}

/* Tablet: 768px+ */
@media (min-width: 768px) {
  .container { padding: 0 32px; }
  .grid-2col { display: grid; grid-template-columns: 1fr 1fr; gap: 32px; }
}

/* Desktop: 1200px+ */
@media (min-width: 1200px) {
  .container { max-width: var(--container-max); padding: 0 40px; }
  .grid-2col { gap: 64px; }
}
```

**Component Library:**

*Hero Section:*
```html
<section class="hero">
  <div class="container">
    <div class="hero__content">
      <p class="hero__eyebrow">{{EYEBROW_TEXT}}</p>
      <h1 class="hero__headline">{{HEADLINE}}</h1>
      <p class="hero__subheadline">{{SUBHEADLINE}}</p>
      <a href="#cta" class="btn btn--primary">{{CTA_TEXT}}</a>
      <p class="hero__proof">{{SOCIAL_PROOF_LINE}}</p>
    </div>
    <div class="hero__media">
      <img src="{{HERO_IMAGE}}" alt="{{ALT_TEXT}}" width="600" height="500">
    </div>
  </div>
</section>
```
```css
.hero {
  padding: var(--spacing-xl) 0;
  background-color: var(--color-background);
}
.hero .container {
  display: flex;
  align-items: center;
  gap: var(--spacing-lg);
}
.hero__content { flex: 1; }
.hero__media { flex: 1; }
.hero__headline {
  font-size: clamp(28px, 4vw, 48px);
  font-weight: 700;
  line-height: 1.15;
  color: var(--color-text-primary);
  margin: 0 0 var(--spacing-sm);
}
.hero__subheadline {
  font-size: clamp(16px, 2vw, 20px);
  line-height: 1.6;
  color: var(--color-text-secondary);
  margin: 0 0 var(--spacing-md);
}
@media (max-width: 767px) {
  .hero .container { flex-direction: column; }
  .hero__media { order: -1; }
}
```

*CTA Button (Primary and Secondary):*
```css
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 16px 32px;
  border-radius: var(--radius-md);
  font-weight: 600;
  font-size: 18px;
  line-height: 1;
  text-decoration: none;
  cursor: pointer;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
  border: none;
}
.btn--primary {
  background-color: var(--color-urgency);
  color: #ffffff;
  box-shadow: var(--shadow-md);
}
.btn--primary:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}
.btn--secondary {
  background-color: transparent;
  color: var(--color-primary);
  border: 2px solid var(--color-primary);
}
.btn--secondary:hover {
  background-color: var(--color-primary);
  color: #ffffff;
}
```

*FAQ Accordion (CSS-only, no JavaScript):*
```html
<div class="faq">
  <details class="faq__item">
    <summary class="faq__question">{{QUESTION}}</summary>
    <div class="faq__answer">
      <p>{{ANSWER}}</p>
    </div>
  </details>
</div>
```
```css
.faq__item {
  border-bottom: 1px solid var(--color-border);
}
.faq__question {
  list-style: none;
  padding: 20px 0;
  cursor: pointer;
  font-weight: 600;
  font-size: 18px;
  color: var(--color-text-primary);
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.faq__question::-webkit-details-marker { display: none; }
.faq__question::after {
  content: '+';
  font-size: 24px;
  font-weight: 300;
  transition: transform 0.2s ease;
}
details[open] .faq__question::after { transform: rotate(45deg); }
.faq__answer { padding: 0 0 20px; color: var(--color-text-secondary); line-height: 1.7; }
```

---

### Section 4 — Lead Magnet PDF Render Standard

**@page Declaration — A4 and Letter:**
```css
/* A4 */
@page {
  size: A4 portrait;
  margin: 20mm 15mm 20mm 15mm;
}

/* US Letter */
@page {
  size: letter portrait;
  margin: 0.75in 0.75in 0.75in 0.75in;
}

/* Named pages for special treatment */
@page cover { margin: 0; }
@page :left { margin-left: 20mm; }
@page :right { margin-right: 20mm; }
```

**Page Break CSS:**
```css
/* Prevent breaking inside these elements */
h1, h2, h3, h4, .callout-box, .section-header, img, table, figure {
  page-break-inside: avoid;
  break-inside: avoid;
}

/* Force page break before major sections */
.chapter-start {
  page-break-before: always;
  break-before: always;
}

/* Prevent orphaned headings at bottom of page */
h2, h3, h4 {
  page-break-after: avoid;
  break-after: avoid;
}

/* Widows and orphans for text */
p {
  orphans: 3;
  widows: 3;
}
```

**Typography Hierarchy:**
```css
/* Print typography scale */
h1 { font-size: 32pt; font-weight: 700; line-height: 1.15; color: #1A1A1A; margin: 0 0 16pt; }
h2 { font-size: 22pt; font-weight: 600; line-height: 1.2; color: #1A1A1A; margin: 24pt 0 12pt; }
h3 { font-size: 16pt; font-weight: 600; line-height: 1.3; color: #333333; margin: 18pt 0 8pt; }
h4 { font-size: 13pt; font-weight: 600; line-height: 1.4; color: #333333; margin: 12pt 0 6pt; }
p  { font-size: 11pt; line-height: 1.65; color: #333333; margin: 0 0 10pt; max-width: 65ch; }
.caption { font-size: 9pt; line-height: 1.4; color: #666666; font-style: italic; }
```

**Document Page Types:**

*Cover page:*
```html
<div class="page-cover" style="page: cover;">
  <div class="cover__brand">{{EXPERT_NAME}} | {{BRAND_NAME}}</div>
  <h1 class="cover__title">{{DOCUMENT_TITLE}}</h1>
  <p class="cover__subtitle">{{SUBTITLE}}</p>
  <div class="cover__footer">clinicIQ Platform | {{YEAR}}</div>
</div>
```
```css
.page-cover {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  padding: 60px;
  background-color: var(--color-primary);
  color: #ffffff;
}
.cover__title { font-size: 42pt; font-weight: 700; line-height: 1.1; margin: 24pt 0 12pt; }
.cover__footer { margin-top: auto; font-size: 9pt; opacity: 0.7; }
```

*Running header/footer with page numbers (Puppeteer headerTemplate/footerTemplate):*
```html
<!-- Puppeteer footer template -->
<div style="font-size: 9pt; padding: 0 15mm; width: 100%; display: flex; 
            justify-content: space-between; color: #888888;">
  <span>{{EXPERT_NAME}}</span>
  <span class="pageNumber"></span>
</div>
```

*Callout/highlight box:*
```html
<div class="callout callout--key-insight">
  <p class="callout__label">Key Insight</p>
  <p class="callout__text">{{CALLOUT_CONTENT}}</p>
</div>
```
```css
.callout {
  border-left: 4px solid var(--color-primary);
  background-color: #F0F7F4;
  padding: 16pt 20pt;
  margin: 16pt 0;
  page-break-inside: avoid;
}
.callout__label { font-size: 9pt; font-weight: 700; text-transform: uppercase; 
                  letter-spacing: 0.08em; color: var(--color-primary); margin: 0 0 6pt; }
.callout__text  { font-size: 11pt; line-height: 1.55; margin: 0; color: #1A1A1A; }
```

---

### Section 5 — Quiz Interface Standard

**Progress Bar:**
```html
<div class="quiz-progress" role="progressbar" 
     aria-valuenow="{{CURRENT_QUESTION}}" 
     aria-valuemin="1" 
     aria-valuemax="{{TOTAL_QUESTIONS}}"
     aria-label="Question {{CURRENT_QUESTION}} of {{TOTAL_QUESTIONS}}">
  <div class="quiz-progress__track">
    <div class="quiz-progress__fill" style="width: {{PROGRESS_PERCENT}}%;"></div>
  </div>
  <span class="quiz-progress__label">{{CURRENT_QUESTION}} of {{TOTAL_QUESTIONS}}</span>
</div>
```
```css
.quiz-progress { margin-bottom: 32px; }
.quiz-progress__track {
  height: 6px;
  background-color: #E5E5E5;
  border-radius: var(--radius-pill);
  overflow: hidden;
}
.quiz-progress__fill {
  height: 100%;
  background-color: var(--color-primary);
  border-radius: var(--radius-pill);
  transition: width 0.3s ease-in-out; /* Under 200ms for question change */
}
.quiz-progress__label {
  font-size: 13px;
  color: var(--color-text-light);
  display: block;
  margin-top: 8px;
  text-align: right;
}
```

**Question Card with Answer Options:**
```html
<div class="quiz-card" role="group" aria-labelledby="question-{{Q_ID}}">
  <h2 class="quiz-card__question" id="question-{{Q_ID}}">{{QUESTION_TEXT}}</h2>
  <div class="quiz-card__options">
    <label class="quiz-option">
      <input type="radio" name="q{{Q_ID}}" value="{{VALUE}}" class="quiz-option__input">
      <span class="quiz-option__label">{{OPTION_TEXT}}</span>
    </label>
    <!-- Repeat for each option -->
  </div>
</div>
```
```css
.quiz-card__question {
  font-size: clamp(18px, 3vw, 24px);
  font-weight: 600;
  line-height: 1.35;
  margin: 0 0 24px;
  color: var(--color-text-primary);
}
.quiz-option {
  display: flex;
  align-items: center;
  min-height: 44px; /* Touch target minimum */
  padding: 14px 20px;
  border: 2px solid var(--color-border);
  border-radius: var(--radius-md);
  cursor: pointer;
  margin-bottom: 12px;
  transition: border-color 0.15s ease, background-color 0.15s ease;
}
.quiz-option:hover {
  border-color: var(--color-primary);
  background-color: rgba(45, 106, 79, 0.04);
}
.quiz-option__input { display: none; }
.quiz-option__input:checked + .quiz-option__label { color: var(--color-primary); font-weight: 600; }
.quiz-option:has(.quiz-option__input:checked) {
  border-color: var(--color-primary);
  background-color: rgba(45, 106, 79, 0.08);
}
.quiz-option__label { font-size: 16px; line-height: 1.4; cursor: pointer; }
```

**Question transition (under 200ms):**
```css
.quiz-card {
  animation: fadeIn 0.15s ease-in-out;
}
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}
```

---

### Section 6 — The Brand-Direct Aesthetic in Code

The CSS decisions that create premium without sacrificing conversion:

```css
/* Button: lift on hover, solid color, appropriate radius */
.btn--primary {
  background-color: var(--color-urgency);
  color: #ffffff;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(214, 40, 40, 0.25);
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}
.btn--primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(214, 40, 40, 0.30);
}

/* Sections: generous space where trust is built */
.section { padding: var(--spacing-xl) 0; }
@media (max-width: 767px) { .section { padding: var(--spacing-section-mobile) 0; } }

/* Typography: modest scale, not extreme display */
/* Use clamp() for fluid type: min, preferred, max */
.headline-lg { font-size: clamp(28px, 4vw, 52px); }
.headline-md { font-size: clamp(22px, 3vw, 36px); }
.headline-sm { font-size: clamp(18px, 2vw, 24px); }

/* Image: no heavy filters */
img { filter: none; } /* Never apply grayscale, heavy saturation, or blur */

/* Cards: subtle shadow, clean border */
.card {
  background: var(--color-surface);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-sm);
  border: 1px solid var(--color-border);
  padding: var(--spacing-md);
}
```

---

### Section 7 — Accessibility Floor

**Color Contrast (WCAG AA):**
- Normal text (under 18px regular / 14px bold): minimum 4.5:1 contrast ratio
- Large text (18px+ regular / 14px+ bold): minimum 3:1
- CTA buttons: minimum 4.5:1 between button text and button background
- Verify using: contrast ratio = (L1 + 0.05) / (L2 + 0.05) where L1 is the lighter color relative luminance

**Alt Text:**
```html
<!-- Informational image — must have descriptive alt -->
<img src="hero.jpg" alt="Health expert Dr. {{NAME}} reviewing patient lab results in a warm clinical setting">

<!-- Decorative image — empty alt so screen readers skip it -->
<img src="divider.png" alt="" role="presentation">

<!-- Complex infographic — alt summarizes the key information -->
<img src="hormone-chart.png" alt="Chart showing the HPA axis connection between cortisol, thyroid function, and sex hormones">
```

**Focus States:**
```css
/* Never remove outline without replacing it */
:focus { outline: none; } /* WRONG — do not use */

/* Always provide a visible :focus-visible replacement */
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
  border-radius: 2px;
}
```

**Semantic heading order:**
```html
<!-- Correct: one H1, then H2 for major sections, H3 for subsections -->
<h1>Main page headline</h1>
  <h2>Section title</h2>
    <h3>Subsection</h3>
  <h2>Next section</h2>

<!-- Wrong: skipping heading levels -->
<h1>Main headline</h1>
<h3>This skips H2 — do not do this</h3>
```

---

### Section 8 — Code Delivery Format

**Self-contained single-file standard:**
Every HTML asset delivered by a Builder agent is a complete, self-contained file:
- All CSS in a `<style>` block in the `<head>` (except email — must be inline)
- All images referenced as absolute URLs (never relative paths)
- No external JS dependencies except approved tracking pixels
- Approved tracking: Meta Pixel, Google Tag Manager, TikTok Pixel — each loaded via their standard async snippet at end of `<body>`

**Variable substitution tokens — complete list:**

| Token | Maps To | Used In |
|-------|---------|---------|
| {{EXPERT_NAME}} | Expert's full name | All formats |
| {{EXPERT_TITLE}} | Dr. / etc. prefix | All formats |
| {{BRAND_NAME}} | Expert's brand/clinic name | All formats |
| {{PROGRAM_NAME}} | Specific program/offer name | Landing pages, emails |
| {{BRAND_PRIMARY_COLOR}} | Hex code from Expert Dossier | All formats |
| {{BRAND_SECONDARY_COLOR}} | Hex code from Expert Dossier | All formats |
| {{CTA_URL}} | Current funnel step URL | All formats |
| {{CTA_TEXT}} | Call-to-action button text | All formats |
| {{HEADLINE}} | Main headline copy | All formats |
| {{SUBHEADLINE}} | Subheadline copy | Landing pages, emails |
| {{EMAIL_SUBJECT}} | Email subject line | Email |
| {{SUBSCRIBER_FIRST_NAME}} | Personalization | Email, SMS |
| {{WEBINAR_DATE}} | Next live webinar date/time | Email, landing pages |
| {{GUARANTEE_DAYS}} | Number of days in guarantee | Landing pages |
| {{CURRENT_YEAR}} | Dynamic year | All formats |

**Inline vs. style block rules:**

| Environment | CSS Delivery Method | Reason |
|---|---|---|
| Email | Always inline | Outlook strips `<style>` blocks |
| Landing page | `<style>` block + inline critical path CSS | Performance: critical CSS inlined, full stylesheet in `<style>` block |
| PDF (Puppeteer) | `<style>` block | Puppeteer handles correctly; inline adds no benefit |
| Quiz (iFrame) | Scoped `<style>` block with class prefix | Prevents parent page pollution |

**Quality checklist before any HTML asset exits the Builder queue:**

| Check | Tool/Method | Pass Criteria |
|-------|------------|---------------|
| HTML validation | W3C HTML Validator | Zero errors, zero warnings |
| Email rendering | Litmus or Email on Acid preview | Renders correctly in all 8 target clients |
| Lighthouse accessibility | Chrome Lighthouse | Score ≥ 85 |
| Image alt text | Manual review | Every non-decorative image has descriptive alt |
| Mobile render 320px | Browser DevTools | No horizontal scroll, no overflow, CTA visible |
| Mobile render 375px | Browser DevTools | All content readable, CTA above fold |
| PDF page breaks | Puppeteer preview | No broken sections, no orphaned headings |
| Focus states | Keyboard tab navigation | Every interactive element has visible focus state |
| Color contrast | Contrast checker tool | All text meets WCAG AA minimum |
| Variable tokens resolved | String search for {{ | Zero unresolved tokens in final output |

---

*clinicIQ Knowledge Base — Production Layer*
*brief_03_html_css.md — Version 1.0*
*April 2026*
