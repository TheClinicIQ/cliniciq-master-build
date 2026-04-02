# ClinicIQ — Layer 5: The IQ Intelligence Platform
# L5-3: One-Tap Deployment
**Version 1.0**
*Layer 5, Spec 3 of 5 | Depends on: L5-1 (Living Expert Profile), L5-2 (Proactive Intelligence Engine), Layer 3 (All Builder Agents)*

---

## Purpose

The most painful gap in every health expert's business is not ideation. It's not even creation. It's the space between *done* and *live.*

An expert has a great email sequence. It sits in a Google Doc for 11 days. Their VA is backlogged. They don't know how to get it into ActiveCampaign themselves. The sequence never goes live.

An ad creative is approved. It needs to get uploaded to Meta Ads Manager, tagged to the right campaign, set to the right budget, assigned to the right audience. Nobody has time. It sits.

A VSL is edited and ready. Someone needs to update the funnel page, swap the video embed, push the change live. It's on the to-do list. It stays there.

**This is where most platforms end and where ClinicIQ begins.**

One-Tap Deployment closes the gap between IQ's output and the real world. The expert approves — and IQ does everything else. The asset routes to the correct platform, is formatted correctly for that platform, is placed in the right location within the expert's existing tech stack, and is live — with zero manual steps.

This spec defines: every integration, every deployment pathway, how assets are matched to destinations, how the approval flow works, what happens at each stage, and how the system handles errors, conflicts, and edge cases.

---

## The Core Principle: Approve → Live

The entire One-Tap Deployment system is built around one interaction:

```
IQ builds the asset
Expert reviews it
Expert taps "Approve & Deploy"
Asset is live
```

That's it. No copying. No pasting. No logging into other platforms. No formatting. No briefing a VA. No "I'll do it later." The moment the expert taps approve, a deployment job starts — and within minutes (or seconds, for text assets), the asset exists in the real world, exactly where it needs to be.

Everything in this spec is in service of making that four-step sequence reliable, fast, and invisible.

---

## The Integration Stack: Every Platform ClinicIQ Deploys To

### Tier 1 — Core Integrations (Available at Launch)
These are the platforms every health expert uses. Day-1 deployment support.

| Platform | Asset Types Deployed | Deployment Action |
|----------|---------------------|-------------------|
| **GoHighLevel (GHL)** | Email sequences, SMS sequences, automation workflows, funnel pages, landing pages, calendar links | Create/update contact in pipeline, inject email sequence into automation, update funnel page HTML/copy, activate or pause workflow |
| **Meta Ads Manager** | Ad creative (image + copy), ad sets, campaigns | Create ad draft, assign to campaign/ad set, set budget, assign audience, submit for review |
| **Klaviyo / ActiveCampaign / ConvertKit** | Email sequences, broadcast emails, automations, segments | Create or update sequence, schedule broadcast, create segment, activate automation |
| **YouTube** | Video uploads, titles, descriptions, tags, thumbnails | Upload video file, set title/description/tags, schedule publish time, assign to playlist |
| **Buffer / Later / Publer** | Social posts (all platforms), reels, carousels, stories | Schedule posts, assign to correct social accounts, queue carousels with caption |
| **Apple Podcasts Connect / Spotify for Podcasters / RSS** | Episode files, show notes, titles, descriptions | Upload audio, set metadata, schedule publish, push to RSS feed |
| **Mux (IQ Course Player)** | Video lessons, course updates, program phases | Upload lesson video, attach to correct phase/lesson slot, set availability date |
| **Webflow / WordPress** | Blog posts, landing pages, website copy updates | Create/update post, set metadata, publish or schedule |
| **Google Ads** | Search campaigns, display ads, YouTube pre-roll | Create/update campaign, set targeting, upload creative |

### Tier 2 — Extended Integrations (Q2 post-launch)
| Platform | Asset Types |
|----------|-------------|
| TikTok Ads Manager | Ad creative, campaigns |
| Kajabi | Course content, email sequences, landing pages |
| Teachable | Course content updates |
| Shopify | Product descriptions, email flows via Klaviyo |
| Slack / Teams | Internal team notifications on deployments |
| Zapier / Make | Custom automation triggers post-deployment |

### Tier 3 — Expert-Configured (Webhook / API)
For any platform not in Tier 1 or 2, the expert can configure a webhook endpoint. When an asset is approved, ClinicIQ sends a structured JSON payload to that endpoint — enabling connection to any custom tech stack.

---

## Deployment Pathways: How Every Asset Type Gets Deployed

### 1. Email Sequence Deployment

**Built by:** Email & SMS Builder Agent
**Destination:** GHL / Klaviyo / ActiveCampaign / ConvertKit (whichever is connected)

**Deployment steps (automated):**
1. Sequence structure mapped: number of emails, delays, trigger conditions
2. Each email formatted for platform (plain text vs. HTML based on expert's preference + platform)
3. Subject lines, preview text, body, CTA buttons, UTM parameters — all set
4. Sequence created in the connected email platform
5. Trigger condition configured (opt-in form, tag applied, funnel step completed)
6. Test email sent to expert's address automatically
7. Expert receives: *"Your 7-email nurture sequence is live in ActiveCampaign. Test email sent to you. Sequence activates when a lead opts in via your gut health funnel. [View in ActiveCampaign →]*"

**Expert touchpoint:** One approval tap. Test email receipt. That's it.

---

### 2. Meta Ad Deployment

**Built by:** Ad Creative Builder Agent
**Destination:** Meta Ads Manager

**Deployment steps (automated):**
1. Creative assets assembled: ad copy (primary text, headline, description), image or video file
2. UTM parameters applied based on campaign naming convention (expert's convention pulled from LEP)
3. Ad draft created in Meta Ads Manager via API
4. Assigned to designated campaign and ad set (existing structure — IQ reads the expert's current campaign architecture)
5. Budget set (IQ uses the existing ad set budget by default — does not change spend without explicit instruction)
6. Audience assigned (existing saved audience or Lookalike — IQ does not create new audiences without approval)
7. Ad submitted for Meta review
8. Expert notified: *"Your ad is in Meta review — typically 24 hours. I'll notify you when it's approved and live. [View in Ads Manager →]"*

**Expert touchpoint:** One approval tap. Meta review notification. Done.

**Critical safeguard:** IQ never adjusts budget, changes audience targeting, or modifies existing campaigns without a separate explicit approval. Deployment only = adding a new creative to existing structure. Campaign-level changes require a dedicated approval flow.

---

### 3. Social Content Deployment

**Built by:** Content Builder Agent
**Destination:** Buffer / Later / Publer → Instagram, Facebook, TikTok, YouTube Shorts, LinkedIn

**Deployment steps (automated):**
1. Post copy finalized per platform (IQ formats differently for each — IG caption with hashtags, FB post with different hook, LinkedIn with professional framing — all from one source piece)
2. Image or video asset attached
3. Optimal posting time determined (based on LEP Audience Response Profile — when does this expert's specific audience engage most?)
4. Posts scheduled across all active platforms in one batch
5. Expert receives scheduling confirmation: *"14 posts scheduled for this week across Instagram, Facebook, and TikTok. First post goes out tomorrow at 9:14am. [View full schedule →]"*

**Batched approval flow:** For social content, the expert reviews the full week's batch in one session — not post by post. IQ presents all 14 posts in a scrollable review view. Expert can approve all, approve individually, or edit specific posts. One final "Deploy all approved" tap schedules the whole batch.

---

### 4. Funnel Page Deployment

**Built by:** Funnel Builder Agent
**Destination:** GHL funnel pages / Webflow / WordPress

**Deployment steps (automated):**
1. Page copy finalized: headline, subheadline, body sections, CTA buttons, bullet points, social proof blocks
2. Page structure mapped to existing funnel template (IQ reads the expert's current funnel structure and slots content into the right sections)
3. For GHL: page HTML updated via API, existing design preserved, only copy swapped
4. For Webflow/WordPress: content updated via CMS API
5. Tracking pixels verified (Facebook Pixel, Google Tag, etc.) — IQ checks they're still firing post-update
6. Expert receives: *"Your opt-in page is updated and live. Tracking verified. [View live page →] [View in editor →]"*

**Page-level vs. funnel-level approval:** Updating one page = one approval. Deploying a full new funnel (multiple pages) = staged approval: expert approves the flow architecture first, then approves each page individually, then approves the full funnel go-live as a final step.

---

### 5. Email Broadcast Deployment

**Built by:** Email & SMS Builder Agent
**Destination:** Connected email platform

**Deployment steps (automated):**
1. Email composed: subject line, preview text, body, CTA
2. Segment or list assigned (based on the campaign context — cold list, warm leads, buyers, etc.)
3. Optimal send time recommended (based on expert's historical open rate data by day/time)
4. Expert approves and selects send time (IQ suggests, expert confirms)
5. Email scheduled
6. Expert receives: *"Your broadcast is scheduled for Thursday 7:42am to 8,234 contacts on your warm leads list. Estimated open rate based on your history: 31–36%. [View email →] [Change send time →]"*

---

### 6. Podcast Episode Deployment

**Built by:** Podcast Agent
**Destination:** RSS feed → Apple Podcasts / Spotify / all connected directories

**Deployment steps (automated):**
1. Audio file validated (format, length, quality check)
2. Episode metadata assembled: title, description, show notes, chapter markers, tags
3. Guest information added if applicable
4. Episode uploaded to podcast hosting platform (Buzzsprout / Libsyn / Anchor — whichever is connected)
5. RSS feed updated
6. Episode scheduled for publish date/time (or immediate)
7. Expert receives: *"Episode 47 is scheduled for Tuesday 6am. It'll appear on Apple Podcasts and Spotify within 2 hours of publish. [Preview episode page →]"*
8. Post-publish: social announcement posts (drafted by Content Builder, scheduled in Buffer) auto-fire on publish day

---

### 7. Course / Program Content Deployment

**Built by:** Program Builder Agent
**Destination:** IQ Course Player (Mux + ClinicIQ platform)

**Deployment steps (automated):**
1. Video lesson uploaded to Mux (transcoding handled automatically)
2. Lesson metadata set: title, description, duration
3. Lesson slotted into correct phase and position within the program structure
4. Availability date set (for phased-release programs)
5. Patient AI Assistant updated with new lesson content (vector DB ingestion)
6. Expert receives: *"Lesson 3 of Phase 2 is live in your Gut Reset Program. It'll unlock for enrolled patients on Day 14. [Preview lesson →]"*

---

## The Approval Flow: How It Works End-to-End

The approval flow is the UX layer that makes one-tap deployment feel natural and trustworthy.

### Stage 1 — Build Complete Notification
IQ Claw sends a message in the center panel:
> *"Your [asset name] is ready for review. I've loaded it in the [Builder tab] on the right. [View →]"*

### Stage 2 — Review in Right Panel
Expert clicks through to the right panel. The asset is displayed in full with:
- **Status badge:** "Awaiting Approval"
- **Destination label:** "Will deploy to: [platform + location]" — explicit, no surprises
- **Preview link** (where applicable): "Preview how this will look live"
- **Action bar:** `[Request Changes]` · `[Edit Directly]` · `[Approve & Deploy]`

### Stage 3 — Approve & Deploy
Expert taps `[Approve & Deploy]`. A confirmation modal appears (one screen only):

```
┌──────────────────────────────────────────────┐
│  Ready to deploy                             │
│                                              │
│  📄 7-Email Gut Health Nurture Sequence      │
│  → ActiveCampaign — Gut Health Funnel        │
│     Trigger: New opt-in via gut-health-lead  │
│                                              │
│  Estimated time to live: ~2 minutes          │
│                                              │
│  [Cancel]           [Confirm & Deploy →]     │
└──────────────────────────────────────────────┘
```

### Stage 4 — Deployment Execution
IQ executes the deployment job in the background. The right panel shows a live progress indicator:
```
Deploying...
✓ Formatting for ActiveCampaign
✓ Creating sequence structure
✓ Uploading emails 1–7
✓ Setting trigger: gut-health-lead opt-in
✓ Sending test email to ryan@thehealthinstitute.com
⟳ Activating sequence...
✓ Live
```

### Stage 5 — Confirmation + Handoff to Layer 4
Deployment complete notification in IQ Claw:
> *"Done. Your sequence is live in ActiveCampaign. I'll track open rates, click rates, and conversions from this sequence and report back in your Morning Brief. [View in ActiveCampaign →]"*

Layer 4 Analytics agent is automatically notified to begin tracking this asset's performance. The LEP is updated with the deployment record. Miro Fish score is logged for future calibration.

---

## Deployment Safeguards: What IQ Will Never Do Without Explicit Approval

The power of one-tap deployment requires absolute clarity about what that one tap authorizes. Hard limits:

| Action | Requires | Never Automatic |
|--------|---------|-----------------|
| Change ad spend / budget | Separate explicit approval + amount confirmation | ✓ |
| Delete existing campaigns, sequences, or pages | Explicit deletion approval + "type DELETE to confirm" | ✓ |
| Email to full list (>5,000 contacts) | Extra confirmation step in approval modal | ✓ |
| Launch a new paid campaign (vs. add creative to existing) | Campaign setup approval flow — multiple steps | ✓ |
| Change funnel structure (vs. update copy) | Structural change approval — shows before/after | ✓ |
| Publish to social outside scheduled window | Explicit "publish now" intent required | ✓ |
| Modify existing automations | Shows exactly what changes, requires explicit approval | ✓ |

**The trust principle:** IQ always does less than it could. When uncertain, it asks. It never assumes that approval of one action implies approval of related actions. Each deployment is scoped and disclosed before execution.

---

## Error Handling: When Deployment Doesn't Go Perfectly

Integrations fail. APIs return errors. Authentication tokens expire. The One-Tap Deployment system handles all of this gracefully.

### Error Tier 1 — Recoverable Automatically
IQ retries and resolves without bothering the expert.
- API timeout → retry up to 3 times with exponential backoff
- Rate limit hit → queue and deploy on next available window
- Minor formatting issue → auto-correct and re-attempt

### Error Tier 2 — Recoverable With Expert Action
IQ pauses deployment and notifies the expert with a specific, solvable prompt.
- Authentication expired → *"Your ActiveCampaign connection needs to be refreshed. [Reconnect in 30 seconds →]"*
- Platform-side rejection (e.g., Meta ad policy violation) → *"Meta flagged this ad for [specific policy]. I've rewritten the problematic section — want to review and resubmit?"*
- Missing asset (video not yet uploaded) → *"This deployment needs your video file. [Upload here →]"*

### Error Tier 3 — Deployment Blocked
IQ cannot proceed and explains exactly why.
- Platform not connected → *"You haven't connected your email platform yet. [Connect ActiveCampaign →]"*
- Asset failed Output Quality gate → cannot deploy until quality issues are resolved
- Compliance flag triggered → *"This ad copy triggered a compliance flag for a health claim that may violate Meta's health advertising policy. I've drafted a compliant version — [review it →]"*

All errors are logged in the deployment history. The expert can see every deployment attempt, its status, and what happened.

---

## The Deployment Dashboard: What the Expert Sees

In the IQ Drive section (navigation rail), the expert has a Deployments view:

- **Live** — all assets currently live, by platform, with performance indicators
- **Scheduled** — all assets queued for future deployment, with dates and destinations
- **In Review** — assets awaiting Meta/platform review
- **Drafts** — assets approved but not yet deployed
- **History** — complete deployment log with status, timestamps, and performance links

One click from any deployment record → the live asset on its platform.

---

## What One-Tap Deployment Changes for the Expert

**Before ClinicIQ:**
- Build an email sequence → 3 days to get it into the email platform
- Approve an ad → 2 days to get it into Meta
- Write a blog post → depends when the VA has bandwidth
- Update a funnel page → scheduled for "next week"

**After ClinicIQ:**
- Everything is live within minutes of approval
- The expert's only job is the creative decision — approve or edit
- Nothing waits in a backlog
- The business moves at the speed of ideas

The best health content and campaigns in the world aren't the ones with the biggest budgets or the most talented teams. They're the ones that move fastest — that see an opportunity, create for it, and are live before anyone else. One-Tap Deployment is what makes ClinicIQ experts the fastest movers in their niche, every single time.

---

*L5-3: One-Tap Deployment — v1.0*
*Next: L5-4 — Network Intelligence*
