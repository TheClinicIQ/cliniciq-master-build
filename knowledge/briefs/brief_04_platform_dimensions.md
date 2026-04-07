# AGENT BRIEF #4 — platform_dimensions.md
**clinicIQ Knowledge Base | Production Layer**
**Version 1.0 — April 2026**

---

## Overview

This brief instructs the agent writing:
`/home/work/.openclaw/workspace/cliniciq/knowledge/production/platform_dimensions.md`

---

## What the Output File Is

The complete static reference for every ad, social post, email, and landing page dimension across all platforms clinicIQ produces assets for. Every Visual Production Agent, Ad Creative Builder, and Advantage+ Packager reads this file before producing or packaging any asset. It is a lookup document — primarily tables, designed for fast scanning.

---

## Source Files

None from the clinicIQ workspace. Research document — use web search to verify current specs for each platform. Specs change; verify recency.

---

## Output Path

`/home/work/.openclaw/workspace/cliniciq/knowledge/production/platform_dimensions.md`

---

## Format Standard

Predominantly tables. Every format gets a complete table. Brief explanatory prose only where a rule is non-obvious. The document should be scannable in under 30 seconds for any specific spec. No "approximately" or "around" — exact numbers. Where a range is genuinely accepted, document the range with the recommended value clearly marked.

---

## Sections to Produce

### Section 1 — Meta Ads Paid (Facebook + Instagram)

For each format produce a complete table: recommended dimensions, minimum dimensions, max file size, supported file types, aspect ratios, video length limits, thumbnail specs, safe zone dimensions.

Formats:
- Facebook Feed image
- Facebook Feed video
- Facebook Stories image
- Facebook Stories video
- Facebook Reels
- Facebook Carousel (image and video cards)
- Instagram Feed image (square, portrait, landscape — all three)
- Instagram Feed video
- Instagram Stories image
- Instagram Stories video
- Instagram Reels
- Instagram Carousel
- Advantage+ Shopping / catalog formats

**Safe Zones for Stories and Reels:** Top 14% and bottom 20% are overlaid with UI elements (handle, CTA button, follow button). Document exact pixel dimensions of safe zones at 1080×1920. Show as ASCII art diagram:

```
┌─────────────────┐  ← 1080px wide
│  UI ZONE (top)  │  ← 250px (top 13%)
├─────────────────┤
│                 │
│   SAFE ZONE     │  ← 1150px tall
│   (text/logos)  │
│                 │
├─────────────────┤
│ UI ZONE (bottom)│  ← 520px (bottom 27%)
└─────────────────┘  ← 1920px total
```

Thumbnail specs for all video formats: dimensions, max file size, supported formats.

---

### Section 2 — Instagram Organic

Same table format as Section 1 for organic posts. Note where organic and paid specs differ.

Formats:
- Feed post: square (1080×1080), portrait (1080×1350), landscape (1080×566)
- Story: 1080×1920, interactive element safe zone
- Reel: 1080×1920, length limits
- Carousel: 1080×1080, count limit
- IGTV thumbnail

---

### Section 3 — YouTube

Formats with complete specs:
- Standard video: accepted dimensions, aspect ratios, max file size
- YouTube Shorts: dimensions, max length
- Channel art / banner: dimensions, safe area for text/logos
- Profile picture: dimensions, shape (circle crop)
- Thumbnail: dimensions, max file size, safe text zone, face placement principles. Thumbnail formula: bold expressive face showing relevant emotion + large readable text (4–5 words) + high contrast background.
- TrueView In-Stream ad: skippable, skip timing, recommended length
- Bumper ad: max 6 sec, non-skippable
- Non-skippable In-Stream: length range

---

### Section 4 — TikTok

Formats:
- Organic video: dimensions, aspect ratio, length limits, file size, supported formats
- In-Feed Ad: dimensions, recommended length, max length, file size
- TopView Ad: dimensions, length, file size
- Brand Takeover: image and video variants
- Spark Ad (boosted organic): specs same as organic post being boosted
- Collection Ad: specs

Safe zone for TikTok: top ~13% and bottom ~25% are UI zones. Document exact pixel dimensions at 1080×1920.

---

### Section 5 — Email Assets

Formats:
- Header image: recommended 600px wide, height range, max file size, format
- Inline image: max width, alt text requirement, rendering notes
- Animated GIF: dimension limits, frame count, file size limit for deliverability (Gmail clips emails over 102KB total — document this)
- CTA button (HTML element): minimum touch target height, typical width, bulletproof HTML required for Outlook

Rendering notes: what works universally vs. what breaks in specific clients for each format.

---

### Section 6 — Landing Pages

Desktop above-fold:
- Most common desktop viewport: 1366×768 (document this as the design target)
- What must be visible without scroll: hook headline + subheadline + CTA button
- Maximum hero section height to keep CTA above fold at 768px viewport

Mobile above-fold:
- iPhone 14: 390×844 CSS pixels
- Samsung Galaxy S23: 393×851 CSS pixels
- Critical zone: headline + subheadline + CTA + one proof element — target under 680px combined height
- CTA must be visible without scroll on mobile

Hero image dimensions:
- Desktop: 1440×800 (full-width background)
- Mobile: requires separate portrait crop (document the standard)
- Art direction note: specify image content for cropping at both dimensions — center-subject images survive both crops; edge-content images require separate mobile version

---

### Section 7 — Practical Production Rules

**The Safe Zone First Rule**
Always design for the safe zone first, then extend to the full canvas. Key content in the safe zone survives every crop and every platform UI overlay. Design outside the safe zone is decorative, not communicative.

**The Crop Test**
Design at 1:1 center first, then expand. 1:1 is the most restrictive crop — if the core message works at 1:1, it works at all other ratios.

Table: what gets cropped at each common ratio:

| Ratio | Crops From | Safe For |
|-------|-----------|---------|
| 1:1 (1080×1080) | All four sides equally | Instagram Feed, Facebook Feed |
| 4:5 (1080×1350) | Left and right sides | Instagram portrait Feed |
| 1.91:1 (1200×628) | Top and bottom | Facebook Feed, link previews |
| 9:16 (1080×1920) | Left and right sides | Stories, Reels, TikTok |

**Text Density**
Meta formally lifted the 20% text rule but heavy text still reduces delivery. Best practice: keep text coverage under 20% of image area. Use text on clear backgrounds or as a separate text treatment overlaid on a color band — not floating over complex imagery.

**File Format Decision Tree**

| Use Case | Format | Why |
|----------|--------|-----|
| Photos, complex images, no transparency | JPEG | Smallest file size for photographic content |
| Graphics, logos, text on images, transparency | PNG | Lossless, supports alpha channel |
| Landing pages (modern browsers) | WebP | 25–35% smaller than JPEG/PNG at same quality |
| Simple animations in email only | GIF | Only animation format reliably supported in email |
| All video platform delivery | MP4 (H.264 / AAC) | Universal compatibility across all platforms |
| Source/editing files | MOV | Never deliver as MOV — always convert to MP4 |
| Logos and icons (all sizes) | SVG | Scales infinitely, no quality loss |

**Resolution Standards**
- All web assets: 72 DPI (higher adds file size with no visible benefit on screens)
- Retina/HiDPI displays: provide @2x resolution, constrain display size in CSS so the browser serves the right size
- SVG for logos and icons: scales infinitely, no raster artifacts
- PNG fallback for complex graphics where SVG isn't practical

---

*clinicIQ Knowledge Base — Production Layer*
*brief_04_platform_dimensions.md — Version 1.0*
*April 2026*
