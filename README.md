# clinicIQ — Master Agent Architecture

The complete agent specification for the clinicIQ Agentic-as-a-Service platform.

**~168 agents · 22 steps · 4 layers + Platform Services · Build-ready**

---

## What Is clinicIQ?

clinicIQ is an Agentic-as-a-Service platform for health experts. It automates the entire growth engine of a health expert's business — brand, strategy, content, funnels, emails, ads, webinars, programs, website, and podcast — using AI agents that know the expert deeply and produce finished, publish-ready work on demand.

> "The expert never writes a caption, builds a funnel page, or touches a prompt. They just talk to the platform and it builds."

---

## Repository Structure

```
cliniciq-master-build/
├── README.md                                  ← This file
├── ENGINEERING_KICKOFF_BRIEF.md               ← Start here — executive overview
├── step21_consistency_audit.md                ← Post-audit findings & resolutions
├── step22_master_agent_document.md            ← THE build bible (all ~168 agents)
│
├── platform/
│   └── cliniciq_platform_architecture.md      ← IQ Claw + IQ Drive + Patient AI
│
├── layer1/                                    ← Steps 1–7: Onboarding Agent
│   ├── step3_conversation_flow_architecture.md
│   ├── step4_voice_dna_extraction_methodology.md
│   ├── step5_avatar_psychology_5_levels_awareness.md
│   ├── step6_offer_architecture_extraction.md
│   └── step7_onboarding_output_payload_handoff.md
│
├── layer2/                                    ← Steps 8–11: Strategy Agents
│   ├── step8_brand_strategy_agent.md
│   ├── step9_growth_strategy_agent.md
│   ├── step10_full_strategy_output_stack.md
│   └── step11_strategy_layer_handoff_payload.md
│
├── layer3/                                    ← Steps 12–16: Builder Agents
│   ├── step12_content_builder_agent.md
│   ├── step13_funnel_and_webinar_builder_agents.md
│   ├── step13b_webinar_builder_deep_spec.md
│   ├── step14_email_sms_builder_agent.md
│   ├── step15_ad_creative_and_lead_magnet_builder_agents.md
│   ├── step16_sales_script_program_website_podcast_agents.md
│   ├── step16b_program_builder_full_spec.md   ← Full program delivery system
│   └── step16c_podcast_agent_full_spec.md     ← Full podcast OS (20 sub-agents)
│
└── layer4/                                    ← Steps 17–20: Intelligence Loop
    └── steps17_20_analytics_intelligence_optimization_learning.md
```

---

## Where to Start

| You are... | Start here |
|-----------|-----------|
| Engineer getting oriented | `ENGINEERING_KICKOFF_BRIEF.md` |
| Building a specific agent | `step22_master_agent_document.md` → find the agent |
| Checking handoffs & data flows | `step22_master_agent_document.md` → Data Flow Map section |
| Resolving a naming conflict | `step21_consistency_audit.md` |
| Building the Program Builder | `layer3/step16b_program_builder_full_spec.md` |
| Building the Podcast Agent | `layer3/step16c_podcast_agent_full_spec.md` |
| Building Layer 4 (analytics/optimization) | `layer4/steps17_20_...md` |

---

## Agent Count Summary

| Layer | Total Agents |
|-------|-------------|
| Platform (IQ Claw + Core Orchestrator) | 14 |
| Layer 1 — Onboarding | 11 |
| Layer 2 — Strategy | ~19 |
| Layer 3 — Builders (10 teams) | ~104 |
| Layer 4 — Intelligence | 21 |
| **Total** | **~168** |

---

## The 8 Open Engineering Decisions

Before build starts, the team needs to resolve:

1. **Agent framework** — LangGraph / CrewAI / OpenAI Agents SDK / custom
2. **Model tier map** — which LLM/SLM per agent type
3. **Memory/state backend** — Vector DB + PostgreSQL + Redis recommended
4. **IQ Drive stack** — S3 + vector DB + PostgreSQL + React/Next.js
5. **IQ Course Player stack** — React/Next.js + Mux + Puppeteer + PostgreSQL + vector DB
6. **Agent deployment model** — serverless (triggered) vs containers (always-on)
7. **IQ Claw interface layer** — persistent web panel overlay, native V2
8. **Monthly Master Plan refresh trigger** — automatic Layer 4 trigger, expert approves

Full detail on all decisions: `step22_master_agent_document.md` → Open Architecture Decisions section

---

## Build Philosophy

**Spec → Test Suite → Eval Function → Overnight Build**

Every agent is pre-specced in `step22_master_agent_document.md`. Engineers write the test suite and eval function, set the build running, and come back to scored results. Human review time: 15–30 min per agent. See the Engineering Briefing for full detail on the eval function architecture.

---

*clinicIQ Master Agent Architecture · Version 1.0 · March 2026 · Confidential*
