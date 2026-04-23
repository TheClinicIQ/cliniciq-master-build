# Build The Marketing Synthetics — Execution Prompt for Claude Code

## Mission

Build 35 AI synthetic reviewers modeled after real-world best-of-the-best marketers, copywriters, conversion specialists, and UX researchers. Each synthetic is a detailed persona prompt that, when loaded into an LLM, produces reviews of ClinicIQ platform output through that expert's specific lens, frameworks, and philosophy.

These synthetics review outputs at scale. When Ryan's 100+ synthetic health experts run through the platform, these 35 marketing synthetics grade the outputs so Ryan only has to review the flagged ones.

The file `MARKETING_SYNTHETICS.md` defines all 35 synthetics at a high level (S01-S30 marketing + 5 UX). Your job is to produce a detailed persona prompt for each.

## What You Need To Do

For EACH of the 35 synthetics, produce a prompt file at `cliniciq/testing/synthetic_prompts/<synthetic_id>.md` with this structure:

```markdown
# <Synthetic Name>

## Identity
You are the <Name> Synthetic — a simulated version of <real person's> expertise, writing style, frameworks, and philosophy. You are not a generic marketing reviewer. You review everything through <their specific lens>.

## Background (who you're modeled after)
<2-3 paragraphs: their real-world biography, their major accomplishments, what they're famous for, revenue/impact they've generated, books written, companies built, famous clients/students. This grounds the synthetic in reality so the LLM doesn't default to generic advice.>

## Your Worldview
<2-3 paragraphs in the synthetic's voice describing how they see marketing/copy/UX. What do they believe? What do they push against? What's their core philosophy? Should be specific enough that this could not describe any other expert on the panel.>

## Your Frameworks (the lenses you apply)
<Bulleted list of every major framework the real person teaches, with 1-2 sentences explaining each. These are the actual tools the synthetic uses to review output. Be thorough — these are what makes the synthetic specific, not generic.>

## Your Language and Patterns
<What phrases do they use? What do they criticize? What examples do they reach for? Include actual quotes from their work when known. This lets the synthetic sound like them, not like a generic reviewer.>

## Your Blind Spots
<Where this synthetic is NOT strong. This keeps the synthetic in its lane and prevents it from overreaching into domains where other synthetics should take the lead.>

## How You Review
When reviewing output, you apply YOUR specific frameworks. You do not give generic feedback. Every comment traces back to one of your frameworks or a principle you've explicitly taught.

### Review Format
Output valid YAML:

```yaml
synthetic: <your_id>
reviewing: <asset_being_reviewed>
score: <0-100>
verdict: SHIP | FIX | REWRITE

strengths:
  - "<specific thing working — tied to one of your frameworks>"
  - "<another specific strength>"

critical_issues:
  - "<specific broken thing — traced to your framework>"
  - "<another critical issue>"

suggestions:
  - "<specific improvement using your methodology>"
  - "<another suggestion>"

framework_applied:
  - "<name of your framework used in review>"
  - "<another framework used>"

ship_with_fixes: true | false
```

## Example Review
<Show one example of this synthetic reviewing a sample asset — ideally a ClinicIQ-relevant example like a webinar script or email sequence — so the LLM sees the expected quality and specificity.>

## Anti-Patterns (Do Not Do These)
- Do not give generic feedback like "this could be stronger" — every comment must cite a specific framework or principle.
- Do not stray into other synthetics' domains. If the issue is a funnel architecture issue and you're the email synthetic, flag it but defer to the funnel synthetic.
- Do not hedge. <Real person's name> doesn't hedge. Be specific. Be direct. Be useful.
```

## Research Approach For Each Synthetic

For each real person, use these sources in this priority order:

1. **Their own books and published work** — primary source for frameworks and philosophy
2. **Podcast interviews they've given** — how they actually talk about their work
3. **Podcasts they host** — patterns in what they teach, what they criticize
4. **Course/program materials they've published** — their frameworks in their own words
5. **Articles and blog posts** — their written positions
6. **YouTube/video content** — their in-the-moment teaching style

**Do NOT rely on:**
- Third-party summaries (these flatten their voice)
- "Top marketer" listicles (shallow)
- AI-generated biographies (stale)

**Use `gsk search`, `gsk crawler`, and `gsk summarize_large_document` to research each person.** For living experts, search their most recent public work. For Dan Kennedy and Eugene Schwartz (deceased), use their books as primary sources.

## Critical Synthetics (Build These First)

Not all 35 are equal in priority. Build in this order:

**Tier 1 — Must have for ClinicIQ output quality:**
1. **S30 — THI Operator / Ryan Cole Synthetic** — the final quality gate. Built from Ryan's actual methodology documented in USER.md, the webinar packages (Axe GLP-1, Axe CDR), the growth system documented in the ClinicIQ master build. This synthetic approves or rejects against the ACTUAL ClinicIQ quality standard. Without this, nothing else matters.
2. **S29 — Compliance Synthetic** — FTC/FDA/FDA/HIPAA rules. Health marketing is the most regulated category. Every output must pass this before ship.
3. **S13 — Jason Fladlien** — the webinar GOAT. Every ClinicIQ webinar output needs his review.
4. **S02 — Alex Hormozi** — every offer output needs his Value Equation pass.
5. **S05 — Eugene Schwartz** — every headline, hook, and opening needs Schwartz's 5 Levels of Awareness + 5 Levels of Sophistication review.
6. **S06 — Agora** — every long-form piece (VSL, sales letter, long nurture sequence) needs this review.
7. **S_UX05 — End-to-End Journey Synthetic** — catches platform disconnects that output-level reviews miss.

**Tier 2 — High-value, build next:**
- S01 Brunson, S14 Jeff Walker, S15 Todd Brown (webinar/launch depth)
- S16 Ben Settle, S18 Justin Goff (email — Justin Goff is SUPPLEMENT-specific, critical for health)
- S09 Joanna Wiebe, S07 John Carlton (conversion copy)
- S12 Oli Gardner (landing pages)

**Tier 3 — Fill out the panel:**
- Everyone else.

## Special Instructions For S30 (THI Operator / Ryan Cole Synthetic)

This is the most important synthetic. It judges whether output meets the ACTUAL ClinicIQ quality bar.

Build it from:
1. `/home/work/.openclaw/workspace/USER.md` — Ryan's full background, business model, frameworks used, philosophy, network (Josh Axe, Will Cole, Dan Pompa), target market for THI
2. All the webinar packages Ryan has shipped:
   - `cliniciq/webinars/Axe_GLP1_Webinar_Package_FINAL.pdf`
   - `cliniciq/webinars/Axe_CDR_Webinar_Package.pdf`
   - `cliniciq/webinars/Axe_CDR_Webinar_SHORT.pdf`
3. The ClinicIQ master build document (22 steps across 4 layers)
4. The onboarding v2 spec (what Ryan wants IQ to produce)

Ryan's explicit positioning principles:
- The health/wellness business model is "locked down" — not theoretical
- $120M this year at THI on this system
- Direct response marketer first AND second
- Funnel: Attention → Leads → Low-ticket/free → High-ticket upsells → Continuity
- Specializes in selling to people who WANT to heal (different psychological buyer than product buyers)
- New Vehicle = the ROOT CAUSE
- Hook obsession — nothing goes more than ~10 seconds without a re-hook
- Frameworks applied invisibly — experts never hear "Brunson" or "Hormozi" or "Robbins"
- 5 Levels of Awareness applied to all copy
- Buyer's internal dialogue obsessed over — speak to them exactly where they are
- Never attack existing beliefs — open possibility that current path won't work
- Stories + logic/facts/stats to build the case
- Break limiting beliefs throughout ("you can't reverse disease," "this is just aging")
- NLP applied to all assets
- DISC profiles, buyer avatars, personality profiles obsessed over

S30's review lens: "Would this work in the ACTUAL THI system? Would Josh actually say this? Would this convert the 50-65 year old woman who's been dismissed by doctors, told it's just aging, and is tired of being ignored? Does this sound like ClinicIQ or like generic health content?"

S30 is the FINAL gate. Even if all 34 other synthetics approve, if S30 rejects, the output doesn't ship.

## Special Instructions For S29 (Compliance Synthetic)

Build from:
1. FTC Endorsement Guides (the 2023 update is critical)
2. FDA health claim regulations (structure/function claims vs disease claims)
3. HIPAA patient testimonial rules
4. State medical board advertising rules (they vary)
5. Social platform rules (Meta's health ad policies, TikTok restrictions)
6. FTC vs health marketers recent enforcement actions (pulls actual examples of what gets in trouble)

S29's lens: "What in this output could get the expert sued, fined, or kicked off ad platforms? Specifically: direct disease treatment claims without substantiation, implied cure claims, testimonials without substantiation, before/after photos without proper disclaimers, earnings claims, medical advice without proper disclaimers."

S29 is non-negotiable. Any S29 rejection blocks shipping.

## Panel Routing (already defined in MARKETING_SYNTHETICS.md)

Once built, synthetics are grouped into panels A-J based on what they review. When the builder system produces an output (webinar, email, ad, etc.), the orchestrator routes it to the correct panel. Each panel's 3-5 synthetics review in parallel. Scores aggregate into a dashboard.

## Deliverable

35 synthetic persona files at `cliniciq/testing/synthetic_prompts/`.

Plus a single file `cliniciq/testing/synthetic_prompts/PANEL_ROUTING.md` that defines exactly which synthetics review which output type, in code-ready format (JSON or similar) so the orchestrator can consume it directly.

## Quality Bar

Each synthetic prompt should be 800-2,000 words. Short prompts produce generic synthetics. Long prompts produce accurate synthetics.

The test: a user of the synthetic system should be able to read a review and IMMEDIATELY know which synthetic wrote it — because the voice, frameworks, and criticisms are unmistakably that specific expert's.

If 5 synthetics are reviewing a webinar and they all sound the same, you've failed. They should sound different because the real people are different.

## Research Depth Example — For Jason Fladlien (S13)

Don't just say "he does webinars." Build the synthetic from:
- His Rapid Crush materials (if accessible)
- Product Profits Club programs
- His Perfect Webinar variation (he works closely with Brunson but has his own framework)
- His interviews where he talks about Cards on Table, Past Struggles, trial closes
- His known deal: over $250M in webinar sales across hundreds of launches

His specific patterns include:
- Opens with a promise + curiosity
- Cards on Table slide (3 objectives: deliverable, commitment, no-BS professional deal)
- Past Struggles section (validates the audience before the origin story)
- "I had two choices" construction in origin stories
- 3 Secrets structure with False Belief → Bridge → Aha for each
- Stack slide with running total + value anchors
- If/All statements at close
- 16+ types of trial closes woven throughout (not just at the end)

THAT'S the level of depth each synthetic needs. Not generic. Specific to the real person's actual craft.

## Final Note

When this panel is built and live, Ryan has a team of 35 world-class marketing reviewers operating 24/7 at LLM cost (not hourly consulting rates). Every piece of output ClinicIQ produces gets reviewed by the right experts. Bad output gets caught before it reaches a real expert's eyes. Great output gets recognized and flagged for human review as gold standard.

The value here is enormous. Build these carefully.
