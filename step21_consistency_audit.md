# clinicIQ — Step 21: Cross-Agent Consistency Audit
**Version 1.0**
*Step 21 of 22 | Reviews: All Steps 1–20 + Platform Architecture*

---

## Purpose

This audit reviews the entire clinicIQ agent architecture for:
1. Naming conflicts and inconsistencies across documents
2. Missing agent definitions (referenced but not fully defined)
3. Handoff gaps (outputs produced that have no confirmed receiver)
4. Redundant agents (same job defined in multiple places)
5. Count discrepancies (agent counts in summary docs vs. actual defined counts)
6. Shared service decisions (agents that should be platform-level vs. per-builder)
7. Open architecture decisions that must be resolved before build

Each finding is classified as:
- 🔴 **BLOCKING** — Must resolve before engineers can build this component
- 🟡 **IMPORTANT** — Should resolve before build; workaround exists but creates tech debt
- 🟢 **MINOR** — Cosmetic or low-impact; note for Step 22 cleanup

---

## SECTION 1 — Naming Inconsistencies

### 1.1 "Growth Blueprint" vs. Document Name
**Status: 🟡 IMPORTANT**

The term "Growth Blueprint" appears in multiple Layer 3 agent `Reads:` sections as something agents consume. However, there is no document called "Growth Blueprint" in the Layer 2 output stack. The actual document the agents should be reading is the **Monthly Master Plan** (which contains funnel variant, traffic sources, awareness level mix, program tier, and tech stack).

"Growth Blueprint" appears to be an informal shorthand that crept in during drafting.

**Resolution:** In Step 22, all references to "Growth Blueprint" in Layer 3 agent specs should be replaced with "Monthly Master Plan" (for campaign/funnel data) or "Expert Dossier" (for offer architecture and tech stack data). The document the Funnel Builder, Webinar Builder, Website Builder, and Email Builder agents read is the Monthly Master Plan + Expert Dossier — not a separate Growth Blueprint document.

---

### 1.2 "Judge/Reviewer Agent" — Referenced but Not Defined in Layer 4
**Status: 🔴 BLOCKING**

Multiple Layer 2 documents reference a "Judge/Reviewer Agent (Layer 4)" as a quality gate that:
- Reviews every Builder agent output against the Brand North Star before it reaches the expert
- Runs automated quality checks on the Brand North Star Part 2 document itself
- Is the standard against which all outputs are reviewed

This agent is referenced as a Layer 4 component but Layer 4 (Steps 17–20) does not define it. The Performance Intelligence Agent and Optimization Agent cover data-driven quality — but output brand/voice quality review is a different function.

**Resolution:** The Judge/Reviewer function should be formalized as a **shared platform service** sitting between the Core Orchestrator (Layer 2) and the Builder agents (Layer 3). It is not a Layer 4 agent — it is a quality gate in the production pipeline. Define it as:

**Output Quality Agent** (shared service, not Layer 4)
- Runs on every Builder agent output before it reaches the expert
- Voice QA check: compare against Voice DNA sample extracts
- Brand QA check: compare against Brand North Star Part 2 operational rules
- Consistency check: does this output align with the current Monthly Messaging Brief angle?
- Pass → output delivered to expert
- Fail → rewrite request back to originating Builder agent with specific failure reason
- Two failures → "Needs Your Eye" flag, hold for expert

This replaces the per-Builder Voice QA and Brand QA sub-agents referenced in the Content Builder and Ad Creative Builder with one shared platform service. This is consistent with the recommendation already noted in the Engineering Kickoff Brief.

**In Step 22:** Define the Output Quality Agent as a shared service under the Core Orchestrator. Remove per-builder Voice QA and Brand QA sub-agents from Content Builder (sub-agent #4 and #12) and from Ad Creative Builder. Update agent counts accordingly.

**Count impact:** Content Builder: 13 → 11 (remove Voice QA + Brand QA). Ad Creative Builder: 10 → 9 (remove Brand QA — Voice QA already removed in earlier merge). Net reduction: 3 agents removed from Layer 3, 1 shared Output Quality Agent added to Core Orchestrator. Net: -2 agents.

---

### 1.3 "Performance Learning Agent" — Defined in Content Builder, also in Layer 4
**Status: 🟡 IMPORTANT**

The Content Builder (Step 12) defines sub-agent #13 as a "Performance Learning Agent" that receives engagement data and updates content production priors. Layer 4 Step 20 defines a "Learning & Feedback Engine" with a "Performance Pattern Extractor" that does the same thing at platform scope.

This is partial overlap. The Content Builder's Performance Learning Agent was the right call at the time it was written; Layer 4 now formally owns this function at platform scope.

**Resolution:** Remove the "Performance Learning Agent" from the Content Builder sub-agent list. Its function is fully covered by Layer 4's Learning & Feedback Engine, which already explicitly reads Content Builder performance data. The Content Builder's data pipeline to Layer 4 stays — the agent that lives inside Content Builder does not.

**Count impact:** Content Builder: 11 → 10 (after Voice QA + Brand QA removal above, now remove Performance Learning Agent). Net total for Content Builder: **Lead + 9 sub-agents = 10 agents.**

---

### 1.4 Onboarding Sub-Agent "Voice DNA Analyst" — Not Listed in Step 7 Summary
**Status: 🟢 MINOR**

The Kickoff Brief and Step 7 summary list the Onboarding sub-agents without the "Voice DNA Analyst" (defined in Step 4 as a distinct sub-agent). The Step 9 Growth Strategy Agent document (which is where the onboarding sub-agent team was formally listed) includes it. The Kickoff Brief summary omits it.

**Resolution:** In Step 22, Onboarding sub-agent count is confirmed as **10** (Lead + 9 sub-agents): Web Scraper, Voice DNA Analyst, Avatar Psychology Builder, Offer Architecture Builder, Webinar Raw Material Extractor, Proof Bank Miner, Story Miner, Silent Diagnostician, Dossier Assembler, Progress Endowment Engine.

Note: "Webinar Raw Material Extractor" appears in Step 9 but not in the Kickoff Brief or Step 7 summary. This is a confirmed sub-agent — add to Step 22.

---

### 1.5 "Webinar Raw Material Extractor" — Exists in Step 9, Missing from Layer 1 Summary
**Status: 🟢 MINOR**

See 1.4 above. The Webinar Raw Material Extractor (extracts One Big Domino, 3 secrets, epiphany bridge during onboarding) is defined in Step 9 but not surfaced in the Onboarding Agent summary docs. Confirmed as a real sub-agent — add to Step 22 final count.

---

## SECTION 2 — Missing Definitions

### 2.1 Steps 1 and 2 — Not Present as Files
**Status: 🟡 IMPORTANT**

The Layer 1 step files begin at Step 3 (step3_conversation_flow_architecture.md). Steps 1 and 2 are referenced throughout as:
- Step 1: Agent Description (the full Onboarding Agent description and capability spec)
- Step 2: Data Schema (the 164-field expert dossier schema)

These are referenced as dependencies in every Layer 1 document but no corresponding files exist in the workspace.

**Resolution:** Step 22 Master Document should include these as defined sections. The 164-field schema is implicitly defined across the Layer 1 docs (Step 3 flow, Step 4 Voice DNA, Step 5 Avatar Psychology, Step 6 Offer Architecture, Step 7 payload) — it needs to be compiled into a single canonical schema file.

**Action for Step 22:** Produce a single `expert_dossier_schema.md` that enumerates all 164 fields with their section, type, source (onboarded vs. inferred vs. web-scraped), and which agents read them.

---

### 2.2 Core Orchestrator Agent — Defined in Layer 2 but Agent Count Not Included in Any Summary
**Status: 🟡 IMPORTANT**

The Core Orchestrator Agent is defined in Step 11 with 5 sub-agents (Gate Checker, Brief Generator, Router, Context Loader, Output Tracker). It is a real, fully-spec'd agent group. But it appears in no agent count table — not in the Kickoff Brief, not in any Layer 2 summary.

**Resolution:** In Step 22, Core Orchestrator is classified as a **platform orchestration service** (not Layer 2, not Layer 3) — similar to IQ Claw. Its agent count: **6** (Core Orchestrator Lead + 5 sub-agents).

With the Output Quality Agent added (from resolution 1.2 above), the Core Orchestrator team becomes: **7** (Lead + 5 original sub-agents + 1 Output Quality Agent).

---

### 2.3 "Patient AI" — Referenced in Platform Architecture, Not Detailed Elsewhere
**Status: 🟡 IMPORTANT**

The Platform Architecture document defines a "Patient-Facing AI" with a brief description. The Program Builder (Step 16b) defines a "Patient AI Trainer" sub-agent that builds the knowledge base. But the Patient AI itself — its persona, capabilities, scope, and agent architecture — is deferred to V2.

**Resolution:** In Step 22, formally mark Patient AI as **V2 scope** with a placeholder definition. The Patient AI Trainer sub-agent in the Program Builder continues to prepare the knowledge base for V2. No blocking issue for V1 build.

---

### 2.4 Layer 2 "Campaign Planner Agent" — Mentioned, Not Defined
**Status: 🟡 IMPORTANT**

The Growth Strategy Agent documents reference a "Campaign Planner Agent" as a primary consumer of the Growth Blueprint / Monthly Master Plan. This agent is not defined as a sub-agent within any documented agent team.

**Resolution:** The Campaign Planner function is likely the "Monthly Planner Sub-Agent" inside the Growth Strategy Agent's sub-agent team (which is defined). Confirm in Step 22 that these are the same agent under different names, and standardize to "Monthly Planner Sub-Agent."

---

## SECTION 3 — Handoff Gaps

### 3.1 Layer 4 → Layer 2 Feedback Loop — Not Fully Spec'd
**Status: 🟡 IMPORTANT**

Step 20 (Monthly Review — originally scoped in the brief as a "Monthly Review & Reporting Agent") was redesigned as the Learning & Feedback Engine. However, one key function from the original scope is not fully addressed: **closing the loop back to Layer 2.**

Specifically: after a month of performance data, the Growth Strategy Agent should produce an updated Monthly Master Plan for the next month — informed by what worked and what didn't. The Learning & Feedback Engine updates priors, but it does not explicitly trigger a Monthly Master Plan refresh.

**Resolution:** Add to the Learning & Feedback Engine's Lead Agent responsibilities: "Monthly trigger: on the last day of each month, routes a Monthly Review Brief (performance data + learning updates) to the Growth Strategy Agent's Monthly Planner Sub-Agent. The Monthly Planner uses this brief to produce the next month's Monthly Master Plan, which feeds all Layer 3 Builder agents for the coming cycle." This closes the loop explicitly.

---

### 3.2 Podcast Agent → Layer 4 Data Flow — Not Defined
**Status: 🟡 IMPORTANT**

The Podcast Agent (Step 16c) includes its own Analytics Reporting Agent (Agent I1), Competitor Intelligence Agent (I2), and Audience Intelligence Agent (P4). These agents gather and produce data. But the flow of podcast data into Layer 4's Analytics Dashboard (Step 17) is not explicitly mapped.

**Resolution:** In Step 22, define that:
- Podcast Agent's Analytics Reporting Agent is a **data producer** for the Podcast Performance section of the Layer 4 Analytics Dashboard
- Podcast Agent's Audience Intelligence Agent feeds its Monday brief to both the Podcast Agent Lead AND to the Layer 4 Performance Intelligence Agent's weekly opportunity scan
- Layer 4 is the authority on cross-channel analysis; Podcast Agent's own analytics agents handle podcast-specific reporting, Layer 4 handles cross-channel correlation

---

### 3.3 Program Builder → Email Builder Handoff for Milestone Emails — Implicit, Not Formal
**Status: 🟢 MINOR**

The Program Builder (Step 16b) specifies that the Support Structure Architect sub-agent "produces automated milestone email sequence spec → handed to Email Builder for production." This handoff is mentioned but the receiving agent in the Email Builder (Step 14) is not specifically identified.

**Resolution:** In Step 22, specify that Program Builder milestone email specs are received by the Email Builder's "Sequence Architect" sub-agent, which is the sub-agent that handles new sequence creation requests.

---

## SECTION 4 — Redundant Agents

### 4.1 Voice QA — Exists in Content Builder AND Referenced as Shared Service
**Status: 🔴 BLOCKING (same as 1.2)**

Already addressed in Finding 1.2. Voice QA lives in the Content Builder (sub-agent #4) but should be a shared platform service through the Output Quality Agent. Remove from Content Builder. See resolution in 1.2.

---

### 4.2 Brand QA — Same Issue
**Status: 🔴 BLOCKING (same as 1.2)**

Already addressed in Finding 1.2. Brand QA lives in the Content Builder (sub-agent #12) and is mentioned for Ad Creative Builder. Remove from both. Consolidated into Output Quality Agent. See resolution in 1.2.

---

### 4.3 Performance Learning — Content Builder + Layer 4
**Status: 🟡 (same as 1.3)**

Already addressed in Finding 1.3. Remove from Content Builder. Layer 4 owns this.

---

### 4.4 Podcast Agent Analytics vs. Layer 4 Analytics — Scope Overlap
**Status: 🟡 IMPORTANT**

The Podcast Agent has three intelligence/analytics agents (P4 Audience Intelligence, I1 Analytics Reporting, I2 Competitor Intelligence). Layer 4 also has Analytics, Performance Intelligence, and Competitor-adjacent capabilities.

These are NOT duplicates — they serve different scopes:
- **Podcast Agent analytics:** Podcast-specific, episode-level, show growth focus
- **Layer 4 analytics:** Cross-channel, business-level, funnel and revenue focus

**Resolution:** Keep both. Clarify scope boundaries in Step 22:
- Podcast Agent analytics = podcast-specific metrics and podcast-specific growth actions
- Layer 4 = cross-channel business intelligence and optimization
- Data flows from Podcast Agent analytics → Layer 4 (one direction), never the reverse

---

## SECTION 5 — Count Reconciliation

### Corrected Agent Counts (after audit resolutions applied)

| Layer / Agent Group | Prior Count | Adjustments | Corrected Count |
|---------------------|-------------|-------------|-----------------|
| **Platform: IQ Claw** | 7 | None | **7** |
| **Platform: Core Orchestrator** | 6 (not in summaries) | +1 Output Quality Agent | **7** |
| **Layer 1: Onboarding Agent** | ~10 | Confirmed at 10 (+Webinar Raw Material Extractor) | **10** |
| **Layer 2: Brand Strategy Agent** | ~5 | To be finalized | **~5** |
| **Layer 2: Growth Strategy Agent** | ~12 | To be finalized | **~12** |
| **Layer 3: Content Builder** | 13 | -Voice QA, -Brand QA, -Performance Learning = -3 | **10** |
| **Layer 3: Funnel Builder** | 10 | None | **10** |
| **Layer 3: Webinar Builder** | 11 | None | **11** |
| **Layer 3: Email & SMS Builder** | 12 | None | **12** |
| **Layer 3: Ad Creative Builder** | 10 | -Brand QA = -1 | **9** |
| **Layer 3: Lead Magnet Builder** | 5 | None | **5** |
| **Layer 3: Sales Script Builder** | 6 | None | **6** |
| **Layer 3: Program Builder** | 11 | None | **11** |
| **Layer 3: Website Builder** | 6 | None | **6** |
| **Layer 3: Podcast Agent** | 21 | None | **21** |
| **Layer 4: Analytics Dashboard** | 5 | None | **5** |
| **Layer 4: Performance Intelligence** | 5 | None | **5** |
| **Layer 4: Optimization Agent** | 6 | None | **6** |
| **Layer 4: Learning & Feedback Engine** | 5 | None | **5** |
| **TOTAL** | **~163** | Net: +1 Core Orch (now counted), -3 removed | **~158** |

---

## SECTION 6 — Shared Service Decisions (Finalized)

The following are confirmed as **platform-level shared services** — not owned by any individual Builder agent:

| Shared Service | Function | Owned By | Called By |
|---------------|----------|----------|-----------|
| **Output Quality Agent** | Voice QA + Brand QA on all Builder outputs | Core Orchestrator | All Layer 3 Builder agents |
| **IQ Drive** | Asset storage and metadata | Platform | All agents that produce assets |
| **IQ Claw** | Expert interface and request routing | Platform | Expert → all agents |
| **Block Library Manager** | Saved blocks — index, search, tag, update | Program Builder (owns) | All Builder agents can query |
| **Layer 4 Learning Engine** | Performance pattern learning and prior updates | Layer 4 | All agents receive updated priors |

---

## SECTION 7 — Architecture Decisions Still Open

These were identified in the Engineering Kickoff Brief and remain unresolved. Must be decided before build begins.

| # | Decision | Options | Recommendation |
|---|----------|---------|----------------|
| 1 | **Agent framework** | LangGraph, CrewAI, OpenAI Agents SDK, custom | Choose based on team capability — all production-viable. LangGraph for complex orchestration graphs; CrewAI for simpler role-based teams. |
| 2 | **Model tier map** | Which LLM/SLM for which agent type | Voice-critical outputs (QA, copy): Claude 3.5+ / GPT-4o. Structured extraction (data parsing, schema population): smaller/faster models. Classification tasks: SLMs. Never use expensive models for formatting or retrieval. |
| 3 | **Memory/state backend** | How Dossier + IQ Profile persist across sessions | Vector DB (Pinecone/Weaviate) for semantic search + PostgreSQL for structured fields + Redis for session state. Standard 2026 pattern. |
| 4 | **IQ Drive tech stack** | Underlying storage + metadata layer | Object storage (S3-compatible) + vector DB for semantic search + PostgreSQL for metadata. IQ Drive UI: React/Next.js. |
| 5 | **IQ Course Player** | React/Next.js + Mux + Puppeteer + PostgreSQL + vector DB | Confirmed in Step 16b. No change. |
| 6 | **Agent deployment model** | Serverless functions vs. containers vs. hosted API | Serverless for episodic/triggered agents; containers for always-on agents (IQ Claw, Data Ingestion). |
| 7 | **IQ Claw interface layer** | Web app, embedded widget, native app | Persistent web panel (always-on overlay) within the clinicIQ web app. Mobile: responsive web first, native app V2. |
| 8 | **Monthly Master Plan refresh trigger** | Manual vs. automatic vs. Layer 4 triggered | Automatic: Layer 4 Learning Engine triggers Growth Strategy Agent monthly. Expert reviews and approves before it takes effect. |

---

## SECTION 8 — Final Pre-Build Checklist

Before the engineering team begins building, confirm:

☐ Output Quality Agent defined and added to Core Orchestrator (Finding 1.2)
☐ "Growth Blueprint" terminology replaced with "Monthly Master Plan" + "Expert Dossier" (Finding 1.1)
☐ Voice QA and Brand QA removed from Content Builder and Ad Creative Builder (Finding 4.1–4.2)
☐ Performance Learning Agent removed from Content Builder (Finding 4.3)
☐ Core Orchestrator agent count added to master count (Finding 2.2)
☐ Expert Dossier Schema compiled as canonical file (Finding 2.1)
☐ Steps 1–2 sections added to master document (Finding 2.1)
☐ Monthly review → Layer 2 feedback loop defined (Finding 3.1)
☐ Podcast → Layer 4 data flow scope boundaries documented (Finding 3.2)
☐ All 8 open architecture decisions resolved (Section 7)
☐ Model tier map produced and assigned to every agent type
☐ All corrected agent counts reflected in Step 22 master document

---

*Step 21 of 22 — Cross-Agent Consistency Audit — v1.0*
*Findings: 2 Blocking, 10 Important, 4 Minor*
*Next: Step 22 — Final Master Agent Description Document*
