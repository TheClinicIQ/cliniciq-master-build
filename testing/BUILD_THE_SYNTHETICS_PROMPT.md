# Build The Marketing Synthetics — Execution Prompt for Claude Code

## Mission

Build 35 AI synthetic reviewers modeled after real-world best-of-the-best marketers, copywriters, conversion specialists, and UX researchers. Each synthetic is a detailed persona prompt that, when loaded into an LLM, produces reviews of ClinicIQ platform output through that expert's specific lens, frameworks, and philosophy.

These synthetics review outputs at scale. When Ryan's 100+ synthetic health experts run through the platform, these 35 marketing synthetics grade the outputs so Ryan only has to review the flagged ones.

The file `MARKETING_SYNTHETICS.md` defines all the synthetics at a high level (marketing + UX). Your job is to produce a detailed persona prompt for each.

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

**Tier 1 — Must have for output quality (these fire on EVERY output, regardless of panel):**
1. **S29 — Compliance Synthetic** — FTC/FDA/HIPAA rules. Health marketing is the most regulated category. Every output must pass this before ship.
2. **S_RT01 — Red Team Synthetic** — adversarial review. Every output gets attacked from the most skeptical/legally-exposed angle before ship.
3. **S_TD01 — Voice Uniqueness / Template Detection Synthetic** — catches the #1 AI content failure mode (sounding like generic AI health content).
4. **S_PM01 — Panel Moderator Synthetic** — runs LAST, reviews the panel's reviews, catches aggregation failures.

**Tier 2 — Core panel members (high frequency across panels):**
5. **S13 — Jason Fladlien** — the webinar GOAT. Every webinar output needs his review.
6. **S02 — Alex Hormozi** — every offer output needs his Value Equation pass.
7. **S05 — Eugene Schwartz** — every headline, hook, and opening needs Schwartz's 5 Levels of Awareness + 5 Levels of Sophistication review.
8. **S06 — Agora** — every long-form piece (VSL, sales letter, long nurture sequence) needs this review.
9. **S_UX05 — End-to-End Journey Synthetic** — catches platform disconnects that output-level reviews miss.
10. **S_PP01 — Cialdini** — influence principles across most panels.
11. **S_VD02 — Oli Gardner Design** — landing pages and funnel pages across multiple panels.
12. **S_VD04 — Barry Hott + S_VD05 Savannah Sanchez** — ad creative panels.

**Tier 2 — High-value, build next:**
- S01 Brunson, S14 Jeff Walker, S15 Todd Brown (webinar/launch depth)
- S16 Ben Settle, S18 Justin Goff (email — Justin Goff is SUPPLEMENT-specific, critical for health)
- S09 Joanna Wiebe, S07 John Carlton (conversion copy)
- S12 Oli Gardner (landing pages)

**Tier 3 — Fill out the panel:**
- Everyone else.

## Special Instructions For Purpose-Built Synthetics (Not Modeled After Real People)

Four synthetics in the panel are NOT modeled after real individuals — they're purpose-built composites:

**S_RT01 — Red Team Synthetic**
Build from:
- FTC enforcement action patterns against health marketers (2020-2026) — pull specific cases
- Plaintiff attorney "hot phrases" for deceptive marketing claims
- Consumer protection blog patterns (Truth in Advertising, Science-Based Medicine, etc.)
- Reddit mockery patterns from r/AvoidBadAds, r/antiMLM, r/ShittyFoodPorn (for visual ad mockery patterns)
- X/Twitter "ratio" patterns for health content that goes viral for wrong reasons
- The "screenshot test" — how claims look isolated from their source
- Vulnerable audience exploitation patterns (elderly, chronically ill, desperate)

Lens: "I am the angriest possible prospect. I am looking for ammunition. I am the plaintiff's attorney. I am the viral screenshotter. What about this output makes the expert vulnerable?"

Output: specific exposure flags with severity, with concrete examples of how each could be weaponized.

**S_TD01 — Voice Uniqueness / Template Detection Synthetic**
Build from:
- A maintained database of "health content sludge phrases" — starts at 100+, grows over time as patterns emerge from real output reviews
- Template structural patterns (three-sentence paragraphs, rhetorical question stacking, "X is more than just Y" openers, etc.)
- Sentence rhythm analysis methodology (standard deviation of sentence length is a leading indicator of AI authorship)
- Voice DNA comparison methodology — load the expert's captured Voice DNA and compare the output against it
- Specificity audit framework — count named specifics, numbers, exact quotes, clinical details; flag if below threshold

Lens: "Strip the subject matter away. Could ANY expert have written this? Or is it unmistakably THIS expert?"

Output: Template Score (0-100, where 100 = pure AI sludge, 0 = unmistakably this specific expert), flagged template phrases, flagged template structures, Voice DNA match score, specificity score.

**S_PM01 — Panel Moderator Synthetic**
Build from:
- Peer review methodology from academic publishing
- Editorial synthesis practices (how good editors integrate multiple reviewer inputs)
- Meta-analytical thinking frameworks
- Rubber-stamp detection heuristics (when reviewers defer to each other instead of reviewing independently)
- Score-feedback coherence analysis (an 85 with 6 critical issues is suspicious — investigate)

Lens: "Did the panel actually do its job? Are these reviews independent? Is each synthetic in their lane? Does the score match the feedback? What did the panel miss?"

Output: Meta-review of the panel's work, independence score, domain-drift flags, coverage gaps, debate triggers, final synthesis.

**S_UX05 — End-to-End Journey Synthetic** (already defined in MARKETING_SYNTHETICS.md)
Build from:
- Heuristic evaluation methodology
- Customer journey mapping frameworks
- Jobs-to-be-Done framework applied end-to-end
- Common platform disconnect patterns (broken handoffs, orphaned flows, unclear ownership, context loss between sections)

Lens: "I am a new user. I just want to [outcome]. Can I do it? Where did I get stuck?"

Output: journey_score, break points by stage, severity, suggested fixes, aha_moments_delivered vs missed, first_value_time.

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

Each synthetic prompt should be 3,000-4,000 words. Anything shorter produces generic synthetics. Anything longer risks fluff. 3,000-4,000 is the right density when every word is doing work — mental model, frameworks with operational depth, war stories from the real person's documented career, their actual voice, their specific diagnostic path, their tells, their coaching patterns.

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
