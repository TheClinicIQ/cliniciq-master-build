# clinicIQ — Layer 3: Builder Agents — Step 16b: Program Builder (Full Specification)
**Version 2.0 — Full Spec**
*Step 16 sub-section | Depends on: Steps 1–15 + Sales Script Builder (Step 16a)*

---

## What the Program Builder Actually Is

The Program Builder is clinicIQ's program delivery system. It is not a course outline tool. It is the end-to-end engine that:

1. Interviews the expert and/or reads their dossier + patient data to understand the program goals
2. Proposes a complete phase-by-phase protocol blueprint (supplement stack, lifestyle, food, specialty protocols, course curriculum, and all resources)
3. Gets the expert's approval before building anything
4. Builds every deliverable in the approved blueprint — all scripts, all protocols, all resources, all support materials
5. Delivers it as a hosted course inside the IQ Platform with its own patient-facing UX
6. Powers a patient AI assistant that answers questions, alerts the expert when gaps are found, and adds new lessons when approved
7. Generates the community content (Facebook group posts, live show frameworks, weekly content) as a separate output stream

The expert ends up with a complete, running program that patients move through — with minimal coach workload, maximum patient clarity, and a system that improves itself over time.

---

## Core Principles

**Proprietary by design.** Every program built in clinicIQ should feel like a category-defining system, not a generic health plan. The phase names, the mechanism language, the protocol framing — all of it is expert-branded and positioned as the only place to get this specific approach. This is a sales architecture decision baked into every naming and framing choice the agent makes.

**Prescription-level specificity.** The protocols are not "eat healthy and take supplements." They are specific. Supplement names, forms, doses, timing, and phase-specific reasons. Food protocols with specific lists, not vague categories. Lifestyle protocols with exact practices, durations, and frequencies. If it's vague, it's not done.

**Education reduces coach workload.** Every phase has video content specifically designed so the coach doesn't have to explain the same thing to every patient. The patient watches the lesson. The lesson answers the question. The coach call is strategic — not remedial.

**Outline first, always.** Nothing gets built until the blueprint is approved. The agent produces the full outline, the expert reviews it, and only then does production begin. This prevents wasted build cycles.

---

## Program Types

The Program Builder supports three program types. The expert selects (or the agent recommends based on their offer architecture):

| Type | Description | Best For |
|------|-------------|----------|
| **Core Program** | One program delivered to all patients. Everyone gets the same version. Individual variation handled within each phase's protocol range. | High-volume practices, group programs, challenges |
| **Custom-Per-Patient** | Each patient gets their own version. Built from the core program as a base, then customized using that patient's intake data, labs, and health history. | High-ticket 1:1 programs, complex chronic conditions |
| **Lead Magnet / Challenge Program** | Short-form (1 phase / 2–4 weeks). Standalone or as a funnel entry point. Lower commitment, designed for conversion. | Top-of-funnel, list building, proving the mechanism |

A single expert can have all three. The Core Program is built first (or simultaneously with the first Custom build). Every Custom program is built on top of the Core — it is never built from scratch.

---

## The Phase Architecture

Every program is built phase by phase. The agent recommends the phase structure based on the expert's mechanism and specialty. The expert approves before any content is built.

### Phase Structure Recommendation Process

The agent:
1. Reads the expert's mechanism, clinical philosophy, and specialty from the dossier
2. Researches best-practice protocol sequencing for the expert's focus area (e.g., a detox protocol has a specific physiological order — you don't pull toxins before clearing the pathways)
3. Proposes a phase sequence with:
   - Physiological/clinical rationale for the order
   - Phase names (functional: what's happening clinically) AND
   - Phase brand names (sexy, proprietary, memorable — what the patient calls it)
   - Estimated duration per phase
   - High-level goals per phase

**Example (detox-focused functional medicine expert):**

| Phase | Brand Name | Clinical Focus | Duration |
|-------|-----------|---------------|----------|
| Phase 1 | **Prepare** | Clear downstream detox pathways (gut, liver, kidneys) | 30 days |
| Phase 2 | **Release** | Mobilize and bind cellular toxins using true binders | 30 days |
| Phase 3 | **Clear** | Address neurological burden — brain detox + CNS support | 30 days |
| Phase 4 | **Rebuild** | Replenish deficiencies, strengthen weaknesses, restore resilience | 30 days |

The agent generates this for the expert's specific specialty — not a generic template. A hormone expert gets a hormone-specific sequence. A gut health expert gets a gut-specific sequence. The clinical rationale is drawn from the expert's own mechanism framework plus current research.

The expert reviews, edits, and approves before anything is built.

---

## The Blueprint — What Gets Outlined Before Build

Once the phase structure is approved, the agent generates the full Blueprint for each phase. This is the prescription. This is what gets approved. This is what everything is built from.

### Per-Phase Blueprint Components

**1. Protocol Prescription (the clinical layer)**

- **Supplement Stack**
  - Each supplement: name, form, dose, timing, duration, phase-specific reason
  - Interaction notes (what to take together, what to separate)
  - Source/quality standard (pharmaceutical grade, third-party tested, etc.)
  - "If patient can't tolerate X" alternatives
  - Phase transition notes (what carries forward, what gets dropped, what gets added)

- **Food Protocol**
  - Foods to emphasize (specific, not "eat vegetables")
  - Foods to eliminate or minimize (specific, with clinical reason)
  - Meal timing and frequency recommendation
  - Hydration protocol (type, amount, timing)
  - Phase-specific focus foods (e.g., Phase 1 = liver-supporting foods)
  - Sample day of eating (not a full meal plan — an example that makes it real)

- **Lifestyle Protocol**
  - Sleep: target hours, wind-down protocol, any phase-specific recommendations
  - Movement: type, frequency, duration, intensity (specific — not "exercise more")
  - Stress regulation: specific practice (HRV breathing, cold exposure, sauna, meditation — whatever the expert uses), frequency, duration
  - Any specialty protocols the expert uses (breathwork, lymphatic, earthing, etc.)
  - Phase-specific adjustments (Phase 2 of a detox: movement is lighter, Phase 4: ramp back up)

- **Monitoring & Milestones**
  - What the patient tracks during this phase (symptoms, energy, bowel habits, sleep — specific to phase)
  - Expected milestones by week (what they should start noticing and when)
  - Red flags (what to watch for — when to contact their coach)

**2. Course Curriculum Outline (the education layer)**

For each phase, the curriculum outline lists:
- Module title (the educational theme for this phase)
- All lesson titles in sequence
- For each lesson: one-sentence description of what it teaches + the action it produces
- Resources needed per lesson (food list? supplement dose card? quiz? infographic? worksheet?)
- Estimated video length per lesson

**3. Resource List**

Every resource that needs to be built for this phase:
- Supplement dose card (one-page visual reference — name, dose, timing)
- Food protocol list (formatted, printable)
- Phase-specific guides (e.g., "How to Read Your Lab Results," "Understanding the Herxheimer Reaction")
- Worksheets (symptom tracker, meal log, lifestyle habit tracker)
- Quizzes (knowledge check after key lessons)
- Infographics (visual explanation of the mechanism for this phase)

**4. Community Content Plan**

For each phase, the community content plan outlines:
- Weekly live session topic + format (what the expert covers in the Facebook live for this phase)
- Weekly post prompts (what to post in the community each week — engagement posts, education posts, celebration posts)
- Phase milestone celebration post template (acknowledge patients who hit week 2, week 4 milestones)

**5. Coach Meeting Prep**

For each phase:
- Patient preparation checklist (what the patient should bring/review before the phase call)
- Coach call agenda template (20-min phase calls — structured, strategic, not remedial)
- Specific questions for this phase's call (based on what typically surfaces in this phase)

The Blueprint is presented as a document the expert reviews section by section. They can:
- Approve as-is
- Edit inline (IQ Claw handles this in conversation — "change the Phase 2 binder from X to Y")
- Request regeneration of any section
- Add their own saved blocks (see Block Library below)

Only when the full Blueprint is approved does the build begin.

---

## The Block Library

### What It Is

The Block Library is the expert's saved component system. As they build programs over time, they accumulate a library of reusable, pre-approved blocks that can be inserted into any new program at the appropriate phase or lesson.

### Block Types

Blocks can exist at any level of granularity:

| Block Type | Example |
|-----------|---------|
| **Protocol Block** | Full Phase 1 supplement stack for a hormone-focused program |
| **Lesson Block** | Complete lesson script: "Understanding Cortisol and Your HPA Axis" |
| **Resource Block** | Adrenal support supplement dose card (formatted, designed) |
| **Script Chunk** | The re-hook opening the expert always uses to open Phase 3 modules |
| **Community Post** | Weekly community check-in post template that works every phase |
| **Coach Agenda** | The standard 20-minute phase call agenda |

### Block Tagging

Every block is tagged on save with:
- **Content type** (lesson, protocol, resource, script, community post, coach template)
- **Phase fit** (Phase 1, Phase 2, any phase, phase-agnostic)
- **Specialty tag** (hormone, gut, detox, autoimmune, metabolic, etc.)
- **Program type** (core, custom, challenge)
- **Expert notes** (free-form note the expert adds: "use this when patient is on low-dose HRT")
- **Performance tag** (if the block has been in production: patient satisfaction score, completion rate)

### How the Agent Uses the Block Library

When generating a Blueprint or building a program, the agent:
1. Searches the Block Library for relevant saved blocks before generating anything new
2. Surfaces relevant blocks with a confidence score ("I found a Phase 2 supplement protocol you built for your hormone program — 87% match to this patient's profile. Use it, modify it, or generate fresh?")
3. Applies approved blocks directly into the Blueprint
4. Suggests tagging and saving any newly built section that doesn't already have a block equivalent

The Block Library grows with every program built. Over time, experienced experts have a rich library that makes new program creation dramatically faster — the agent assembles from existing approved blocks and only generates truly new content where no block exists.

---

## Custom-Per-Patient Program Flow

When an expert needs a custom program for a specific patient, the flow is:

**Step 1 — Patient Intake Upload**
The expert (or the patient directly) uploads or inputs:
- Health history form responses
- Lab results (PDF — agent reads and extracts key markers)
- Symptom inventory / intake questionnaire
- Any prior treatment history
- Patient goals (stated in their own words)
- Contraindications or known sensitivities

**Step 2 — Patient Profile Generation**
The agent reads all inputs and produces a Patient Protocol Profile:
- Key findings (the 3–5 most clinically significant patterns)
- Phase sequence recommendation (same structure as Core Program, but sequencing may shift based on patient state)
- Protocol adjustments (where the Core Program needs to change for this patient — specific supplement substitutions, dose modifications, food protocol adjustments, phase timing changes)
- Red flags (anything that needs the expert's clinical attention before starting)

**Step 3 — Expert Review**
The expert reviews the Patient Protocol Profile. They can accept, modify, or override any recommendation. This is not autonomous clinical decision-making — the agent proposes, the expert decides.

**Step 4 — Custom Blueprint Generation**
The approved Patient Protocol Profile is merged with the Core Program blueprint to produce the patient's custom program. Where the Core Program works for this patient → it stays. Where it needs modification → the custom version is inserted.

**Step 5 — Program Build**
The custom program is built and provisioned to the patient's account. The patient sees their own version of the program — not the generic one.

---

## The Program Delivery Platform (Built Inside IQ)

### Decision: Build Inside IQ

The patient-facing program delivery system lives inside clinicIQ. The patient never knows they're on clinicIQ — it's fully white-labeled under the expert's brand. This is the right call for three reasons:

1. **Retention.** The program, the AI assistant, the community content, and the coach tools all live in one place. Switching platforms means losing all of it.
2. **Intelligence.** A native course player means the AI knows the full course structure — it can point patients to specific lessons, track completion, identify where patients are struggling, and add new lessons in context.
3. **Experience.** A custom-built player designed for health programs will outperform a generic course platform for this specific use case.

### The Patient Experience

When a patient logs into their program, they see:

```
[Expert Brand Logo + Name]

MY PROGRAM: [Program Name]
─────────────────────────────────────────
Current Phase: [Phase Brand Name]  Week 3 of 4
Progress: ████████░░ 72%

[ Phase Overview ]  [ My Protocols ]  [ Course ]  [ My Coach ]  [ Ask AI ]
─────────────────────────────────────────

TODAY'S FOCUS:
→ Lesson 3.2: Why Phase 2 Binders Are Different (12 min)
→ Log your Week 3 symptoms

QUICK REFERENCE:
📋 My Supplement Dose Card — Phase 2
🥗 My Food Protocol — Phase 2
📊 My Symptom Tracker
```

### Core Patient-Facing Sections

**1. Phase Overview**
- Phase brand name, clinical focus (plain language), duration
- What to expect this phase (week-by-week milestone guide)
- Phase protocol summary (supplement stack, food, lifestyle — all in one view)
- Phase completion progress bar

**2. My Protocols**
- Full supplement dose card for current phase (formatted, printable)
- Food protocol list for current phase
- Lifestyle protocol checklist
- Phase-transition notes (what's changing when they move to the next phase)
- All protocols are phase-specific — the patient only sees what's relevant now

**3. Course (The Education Layer)**
- Video lessons organized by module within each phase
- Lesson completion tracking
- Resources attached to each lesson (food list, worksheet, infographic — right there, not in a separate folder)
- Lesson notes field (patient can take notes, save them, return to them)
- Search across all lessons ("find the lesson about die-off reactions")

**4. My Coach**
- Coach profile and contact info
- Meeting schedule (all calls visible — intake, phase calls, graduation)
- Meeting prep checklist for each call
- Async messaging to their assigned coach
- Call notes from previous sessions (added by coach post-call)

**5. Ask AI**
The patient's AI assistant. Knows the full course content, the patient's specific protocol, and the expert's mechanism. Answers questions in the expert's voice.

- Answers based on existing lesson content first ("Your Phase 2 binder question is covered in Lesson 2.3 — want me to pull the key points?")
- Answers from the expert's knowledge base if the lesson exists
- If the question can't be answered from existing content → drafts a proposed answer + flags it to the expert for approval → when approved, the answer is added to a FAQ section or inserted into the appropriate lesson

**6. Community**
- Link to the Facebook community (external — IQ doesn't host it)
- Current week's community content (the post the expert just made, the live session schedule)
- Community content generated by IQ is surfaced here so the patient knows what's happening

---

## The Coach-Facing Tools

The coach (who may be the expert or a team member) has a separate view:

**Patient Dashboard**
- All active patients in one view
- Each patient: current phase, completion percentage, last login, flagged questions (from Ask AI)
- Filter by phase, by coach, by flag status

**Patient Program View**
- Full view of the patient's custom program and protocol
- Ability to make adjustments (edit a dose, swap a supplement, add a note)
- Any change creates a version history — nothing is lost

**Call Prep**
- Phase call agenda pre-populated based on the patient's current phase
- Patient's self-reported symptom tracker data visible
- AI-generated "talking points" based on what the patient has been asking and where they're struggling

**Question Alert Queue**
- All patient questions that couldn't be answered from existing content
- Agent's proposed answer displayed alongside each
- Expert reviews, approves/edits → answer goes live in patient's course

**Content Requests**
- "Generate a new lesson for [topic] and insert it into Phase 2"
- IQ Claw handles this — routes to Lesson Script Writer, returns draft for approval, inserts on approval

---

## The Coaching Model — IQ's Role

The expert's recommended coaching model (as specified):

| Touchpoint | Format | Duration | Purpose |
|-----------|--------|----------|---------|
| **Intake Call** | 1:1 video | 40 min | Get to know each other, understand patient history, set expectations, confirm program |
| **Phase Calls** | 1:1 video | 20 min | Strategic check-in at start of each phase — how'd you do, what changed, where do you need help |
| **Graduation Call** | 1:1 video | 40 min | Full transformation review, testimonial capture, review request ask |
| **Float Call** | 1:1 video | 20 min | One floating call per program — used if patient needs extra support at any point |
| **Async Text** | Coach messaging | Ongoing | Between phase calls — patient can reach coach, coach responds |
| **Community Live** | Facebook Live | Expert-determined cadence | Expert goes live in the private community — Q&A, education, motivation |

**IQ's role in the coaching model:**

| Touchpoint | IQ Produces |
|-----------|-------------|
| Intake Call | Intake call script (Sales Script Builder), patient profile summary for coach review |
| Phase Calls | Phase call agenda per phase, patient progress summary, AI-flagged topics from that patient's question history |
| Graduation Call | Graduation call script (Sales Script Builder), testimonial capture framework, review request script |
| Community Live | Weekly live session topic + talking points + show outline (generated by Podcast Agent / Community Content module) |
| Facebook Community | Weekly post set (7 posts per week per phase — engagement, education, celebration, accountability) |

The Intake Call script and Graduation Call script are built by the Sales Script Builder. The phase call agendas are built by the Program Builder's Coach Meeting Architect sub-agent.

---

## Adaptive Learning — The Platform UX Principle

You asked about Google's adaptive learning tool — you're likely thinking of **Google's Learning Coach** concept or possibly **Socratic by Google**, which teaches concepts by asking questions rather than delivering answers. There's also Coursera's adaptive learning paths and newer tools like Synthesis and Khan Academy's AI tutor.

The principle worth applying here: **don't deliver content in one mode and assume it works for everyone.**

For clinicIQ's program player, the recommendation is:

**Learning Style Assessment at Onboarding**
When a patient first logs in, before they see Phase 1, the AI asks 3–4 quick questions (not a formal assessment — a natural conversation):
- "Do you prefer to understand the 'why' before doing something, or do you like to just get started and learn as you go?"
- "When you're learning something new, do you prefer watching videos, reading guides, or having someone explain it to you?"
- "How much detail do you want? Full explanation of everything, or just the key points and what to do?"

The responses adjust the patient's default experience:
- **Why-first learner:** mechanism explanation appears before the protocol instructions
- **Do-first learner:** protocol card appears first, lesson is "learn more"
- **Video learner:** lessons default to expanded video view
- **Reader:** transcript + key points shown by default below each video
- **Detail-high:** full protocol context shown; **Detail-low:** "essentials only" view

This is not a full adaptive learning system — it's a simple preference layer that makes the program feel personalized without engineering complexity.

---

## The Full Program Builder Sub-Agent Team (Revised)

```
PROGRAM BUILDER LEAD AGENT
├── Reads: Expert Dossier (mechanism, clinical philosophy, specialty, offer architecture)
│         + Brand North Star (voice, positioning, phase naming principles)
│         + Growth Blueprint (program tier, price point, audience stage)
│         + Patient Intake Data (for custom-per-patient builds)
│         + Block Library (searches before generating anything new)
├── Determines: Program type, phase count, Blueprint structure
├── Orchestrates: 10 sub-agents below
└── Delivers: Complete approved program → IQ Platform course delivery system
              + all protocols → IQ Drive/Program/[Program Name]/
              + community content → IQ Drive/Community/[Program Name]/

SUB-AGENTS:

1. Phase Architect
   Reads: Expert's mechanism, clinical specialty, and treatment philosophy from dossier
          Research base for the expert's specialty area (protocol sequencing best practices)
          Block Library (existing phase structures from prior programs)
   Builds: Full phase sequence with functional rationale + brand naming options for each phase
   Validates: Physiological/clinical logic of the sequence (phases in correct order for the mechanism)
   Produces: Phase Structure Proposal — presented to expert for approval before any other work begins
   Also names: Proposes 3 naming options per phase (brand names) — expert selects

2. Protocol Prescription Agent
   Activates: After phase structure is approved
   Reads: Approved phase structure + expert's specialty protocols + dossier clinical philosophy
          Block Library (existing supplement stacks, food protocols, lifestyle protocols)
          Patient Intake Profile (for custom builds — adjusts protocols to patient specifics)
   Produces per phase:
   — Supplement stack (name, form, dose, timing, phase reason, tolerance alternatives)
   — Food protocol (specific foods in/out, timing, hydration, sample day)
   — Lifestyle protocol (sleep, movement, stress regulation, specialty practices — all specific)
   — Phase transition protocol (what changes when moving to next phase)
   — Monitoring guide (what patient tracks, expected milestones by week, red flags)
   Specificity standard: every recommendation is prescription-level, never vague
   Expert reviews and approves before curriculum build begins

3. Curriculum Architect
   Reads: Approved phase structure + Protocol Prescription outputs
          Dossier (mechanism, proof bank, transformation stories)
          Block Library (existing lessons and modules)
   Builds: Full curriculum outline — module titles, lesson titles, sequence logic
   Per lesson: one-sentence description + action produced + resource requirements
   Validates: Every lesson has one clear action; no information dumps
   Validates: Curriculum answers every question a patient will have during the protocol
   Flags: Any protocol element that has no corresponding lesson ("Phase 2 binder protocol
          has no explanation lesson — generating a lesson spec now")
   Output: Full curriculum outline — presented alongside Protocol Prescription for approval

4. Lesson Script Writer
   Activates: After full Blueprint is approved
   Reads: Curriculum outline + Voice DNA + proof bank + mechanism + protocol prescriptions
   Writes: Full word-for-word video scripts for every lesson
   Structure per lesson:
   — Re-hook (why this matters for the patient's goal)
   — Concept delivery (teach one thing, mechanism-consistent, plain language)
   — Demonstration / patient story (proof that this works)
   — Application bridge (specifically what this means for their protocol)
   — Action assignment (the one thing they do before next lesson)
   — Acknowledgment (this is real progress)
   Produces: Module intro and outro scripts for each phase
   Produces: Phase welcome video script (the patient watches this before Phase 1 content)
   Produces: Program orientation script (first video — sets expectations, explains the system)

5. Protocol Card & Resource Producer
   Reads: Approved protocol prescriptions + curriculum outline (resource requirements per lesson)
          Block Library (existing formatted resources)
   Produces:
   — Supplement dose card per phase (name, dose, timing, phase reason — formatted, printable PDF)
   — Food protocol card per phase (foods in/out, formatted list)
   — Lifestyle protocol checklist per phase (daily habits, formatted checkbox list)
   — Monitoring tracker per phase (symptom log, milestone tracker)
   — Quizzes per lesson (knowledge check, 3–5 questions, correct answers with explanation)
   — Infographics (visual mechanism explanations, formatted HTML/CSS → Puppeteer PDF)
   — Specialty guides (any phase-specific resource flagged in curriculum outline)
   Format standard: every resource is beautiful, brand-accurate, and self-explanatory
   without the patient needing to watch a lesson to understand it

6. Coach Meeting Architect
   Reads: Approved phase structure + protocol prescriptions + program duration
   Produces:
   — Intake call agenda + coach talking points (40-min structured guide)
   — Phase call agenda per phase (20-min strategic template — "how'd you do,"
     "what changed," "where do you need help," phase-specific probes)
   — Graduation call script + testimonial capture framework + review ask language
   — Async messaging response templates (common patient messages + ideal responses
     for each phase — coach customizes, AI drafts)
   — Red flag escalation guide (what patient messages warrant immediate vs. scheduled response)

7. Community Content Generator
   Reads: Approved phase structure + monthly campaign from Monthly Master Plan
   Produces per phase:
   — 7 Facebook posts per week (education, engagement, celebration, accountability mix)
   — Weekly live session outline (topic, talking points, Q&A prompts, closing CTA)
   — Phase milestone celebration posts (Week 2, Week 4 achievement posts)
   — Community pinned resources guide (what to pin in the group for each phase)
   Produces for program launch:
   — Community welcome post (expert posts this when a new cohort begins)
   — Community guidelines post
   — Accountability challenge post (used to drive early engagement)

8. Patient Intake Processor
   Activates: For Custom-Per-Patient builds
   Reads: Lab results (PDF extraction + marker interpretation)
          Health history form
          Symptom inventory
          Patient-stated goals
          Contraindications and sensitivities
   Produces: Patient Protocol Profile
   — Key clinical findings (3–5 most significant patterns)
   — Phase sequence recommendation with patient-specific rationale
   — Protocol adjustments (specific deviations from Core Program with clinical reason)
   — Red flags for expert review (anything requiring clinical judgment before starting)
   Expert reviews and approves Patient Protocol Profile before custom build proceeds

9. Patient AI Trainer
   Reads: All approved lesson scripts + protocol prescriptions + resource library
   Builds: The knowledge base for the patient-facing Ask AI assistant
   Structures: All course content as searchable, retrievable Q&A pairs
   Produces: Standard FAQ set (the 30 most common questions for this type of program,
             answered from the expert's mechanism + protocol — pre-fills the AI knowledge base)
   Manages: Alert queue — when Ask AI can't answer a patient question, this agent
             drafts the proposed answer + formats it for expert review
             On approval: adds to knowledge base + inserts into course at appropriate location
   Monitors: Question patterns — what patients are repeatedly asking that isn't
             well-covered in existing content (surfaces to Lead Agent as content gap report)

10. Block Library Manager
    Runs continuously (not just during builds)
    After every build: reviews all newly produced content and flags candidates for saving
    Prompts expert: "This Phase 2 supplement stack performed well — want to save it
                    to your Block Library tagged as [hormone / Phase 2 / core program]?"
    On save: tags block, indexes it, makes it searchable for future builds
    During builds: searches library before generating, surfaces relevant blocks with match scores
    Maintains: Block performance data — which blocks have highest patient completion rates,
               highest satisfaction scores, lowest coach intervention rates
```

**Agent count: 11** (Program Builder Lead + 10 sub-agents)

---

## Platform Architecture — The IQ Course Player

### Technology Recommendation

Build a custom course player inside the IQ Platform. Do not build on Kajabi, Teachable, or GHL. The reasons:

- **Intelligence integration:** A native player means the Ask AI knows exactly where the patient is, what they've completed, what they've struggled with — no API bridging required
- **UX control:** Health program delivery has specific UX requirements (protocol cards, phase navigation, symptom tracking) that no generic course platform was designed for
- **Retention:** Every feature lives in IQ — switching costs are total
- **Monetization:** clinicIQ charges per seat, per program, per phase — a native player makes this billing architecture possible

### Tech Stack Recommendation

| Layer | Technology | Why |
|-------|-----------|-----|
| **Course framework** | Custom React/Next.js | Full UX control, fast, modern |
| **Video hosting** | Mux or Bunny.net | Best performance, built for video-first apps, affordable at scale |
| **Document rendering** | Puppeteer + HTML/CSS | Same system as rest of IQ — all resources, cards, PDFs generated the same way |
| **Patient progress DB** | PostgreSQL with Redis cache | Completion tracking, milestone triggers, fast reads |
| **Ask AI knowledge base** | Vector DB (Pinecone or Weaviate) + semantic search | Finds the right lesson/answer even when patient's question wording doesn't exactly match |
| **File storage** | IQ Drive (already spec'd) | All resources, videos, and program assets live here |
| **Adaptive preferences** | Simple user preference store | Not ML — just stores 4 preference settings per patient |
| **Coach messaging** | Built-in async thread per patient | Native — no third-party tool needed for coach ↔ patient messages |

### White-Label Branding

Every program is fully white-labeled. The patient sees:
- Expert's logo and brand colors
- Expert's chosen program name
- Expert's phase brand names
- Expert-named AI assistant (not "IQ")
- Expert's domain (e.g., `program.drsarahchen.com` — proxied through Caddy)

clinicIQ is invisible to the patient. This is a feature, not a limitation.

---

## The Full Program Build Sequence

```
1. PROGRAM INITIATION
   Expert says: "Build my core program" / "Build a custom program for [patient]"
   IQ Claw confirms: Program type (core / custom / challenge)
   
2. PHASE ARCHITECTURE
   Phase Architect → Phase Structure Proposal
   Expert reviews → approves / edits
   Phase brand names confirmed

3. BLUEPRINT GENERATION
   Protocol Prescription Agent → full per-phase protocols
   Curriculum Architect → full curriculum outline
   Block Library Manager → surfaces relevant existing blocks
   Expert reviews complete Blueprint → approves / edits section by section

4. RESOURCE PLANNING
   Protocol Card & Resource Producer → resource list per phase
   Expert reviews resource list → approves / adds to / removes
   
5. FULL BUILD
   (All build sub-agents activate simultaneously per phase)
   Lesson Script Writer → all video scripts
   Protocol Card & Resource Producer → all protocol cards, resources, PDFs
   Coach Meeting Architect → all call agendas and scripts
   Community Content Generator → full community content set
   Patient AI Trainer → knowledge base built from all content

6. EXPERT REVIEW
   Complete program presented in draft view inside IQ Platform
   Expert reviews phase by phase
   Revision requests → routed back to appropriate sub-agent
   Approval → program published to IQ Platform

7. PATIENT PROVISIONING
   Core program: all new patients automatically provisioned
   Custom program: patient account created, custom version loaded
   Learning style assessment runs on patient first login

8. LIVE PROGRAM MANAGEMENT
   Ask AI answers patient questions
   Question gaps → alert queue → expert approves answers → knowledge base updated
   Performance data → Block Library Manager → flags high-performing blocks for saving
   Content gap reports → Lead Agent → new lesson creation workflow
```

---

## Outputs — What the Program Builder Delivers

**To IQ Drive:**
- Complete program curriculum (all scripts, all lessons)
- All protocol prescriptions (supplement, food, lifestyle — per phase)
- All formatted resources (dose cards, food lists, trackers, quizzes, infographics, guides)
- All coach meeting materials (agendas, scripts, response templates)
- Complete community content library (posts, live outlines — per phase)

**To IQ Platform (live):**
- Fully hosted, white-labeled course player at expert's domain
- Patient-facing: phase navigation, protocol cards, video lessons, resources, Ask AI, coach messaging
- Coach-facing: patient dashboard, call prep, question alert queue, program editing

**To Block Library:**
- All newly created content flagged for saving
- Expert-approved blocks indexed and tagged for future builds

---

## IQ Claw Integration — Program Builder Requests

| Expert Says | IQ Claw Routes To |
|-------------|------------------|
| "Build my core program" | Program Builder → Phase Architect (start) |
| "Build a custom program for [patient name]" | Program Builder → Patient Intake Processor (start) |
| "Add a lesson about [topic] to Phase 2" | Program Builder → Curriculum Architect + Lesson Script Writer |
| "A patient asked a question I haven't covered" | Program Builder → Patient AI Trainer (alert queue) |
| "Update the Phase 3 supplement stack" | Program Builder → Protocol Prescription Agent (edit) |
| "What does my Phase 2 call agenda look like?" | Program Builder → Coach Meeting Architect (retrieve) |
| "Generate this week's community posts for Phase 1 clients" | Program Builder → Community Content Generator |
| "Save my Phase 1 detox protocol as a block" | Program Builder → Block Library Manager |
| "Build a 30-day challenge version of my core program" | Program Builder → Lead (challenge type, abbreviated build) |

---

*Step 16b — Program Builder — Full Specification — v2.0*
*File: `/home/work/.openclaw/workspace/cliniciq/layer3/step16b_program_builder_full_spec.md`*
*Next: Step 16c — Podcast Agent (to be finalized) | Step 16d — Website Builder (complete)*
