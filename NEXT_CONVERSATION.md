# Next Conversation — Starting Point
*Updated: 2026-04-07 (after implementation layer session)*

---

## What Was Just Completed

We built the technical implementation layer foundation in one session:

**Files created:** `/home/work/.openclaw/workspace/cliniciq/implementation/`

| File | What it is |
|------|-----------|
| `00_prompt_engineering_research/leaked_prompts_analysis.md` | 10 structural patterns extracted from real leaked production prompts (Claude Sonnet 4.6, Cursor, Cline, Devin) |
| `00_prompt_engineering_research/research_findings_2025_2026.md` | 10 findings from Anthropic's published context engineering + agent architecture research |
| `00_prompt_engineering_research/behavioral_dna.md` | Ryan's 5 calibration answers turned into hard behavioral rules for every clinicIQ agent |
| `01_system_prompt_template/SYSTEM_PROMPT_TEMPLATE.md` | The universal 12-section XML template every agent is built from |
| `02_agent_prompts/layer1/onboarding_lead_agent.md` | First fully built production-grade system prompt — the Onboarding Lead Agent |

**Key decisions locked:**
- Universal template uses XML semantic tags (Claude's production pattern)
- Hard rules and soft rules are always separated
- Every agent has an explicit OUT OF SCOPE section
- Dossier context is injected at runtime (not baked into the prompt)
- Output format is always a JSON contract, never prose
- Every prompt ends with the One-Line Test quality standard
- Behavioral DNA: Advisory tone, infer-and-flag uncertainty handling, warm expert personality, complete-then-flag-concerns, adapts to expert's style

---

## What Still Needs to Be Built

### Priority Order (pick up here):

**1. Remaining Layer 1 sub-agent prompts** *(9 prompts)*
Using the template, write system prompts for each Onboarding sub-agent:
- web_scraper
- voice_dna_analyst
- avatar_psychology_builder
- offer_architecture_builder
- proof_bank_miner
- story_miner
- silent_diagnostician
- voice_dna_mass_ingestion
- dossier_assembler
- progress_endowment_engine

**2. Context slicing rules** → `03_context_slicing/dossier_field_map.md`
Define which of the 198 dossier fields each agent class receives.
This is the most technically important file — it prevents context rot and keeps every agent focused.
Key question to answer: which fields go to Layer 1 vs. Layer 2 vs. Layer 3 vs. Layer 4?

**3. Output schemas** → `04_output_schemas/`
JSON Schema definitions for each major output type:
- onboarding_output.json (dossier assembly)
- brand_strategy_output.json
- content_builder_output.json
- email_builder_output.json
- funnel_builder_output.json

**4. Quality gates as code** → `05_quality_gates/gate_logic.md`
Translate all 7 strategic quality gates into implementable logic:
- Gate 1: handoff_ready: true check
- Gate 2–7: what each gate checks, what passes, what fails, what the failure response is

**5. IQ Claw system prompt** → `02_agent_prompts/platform/iq_claw.md`
The front door to the entire platform. Routes all expert requests.
Most important platform-level prompt after the Onboarding Lead Agent.

**6. Layer 2 agent prompts** *(Brand Strategy Lead, Growth Strategy Lead, Core Orchestrator)*
**7. Layer 3 agent prompts** *(Content Builder Lead, Email Builder Lead, etc.)*
**8. Framework recommendation doc** → `00_prompt_engineering_research/framework_recommendation.md`
LangGraph vs. CrewAI vs. OpenAI Agents SDK vs. custom — with a final recommendation for clinicIQ's specific architecture.

---

## Suggested Opening for the Next Conversation

Copy and paste this:

*(See the handoff prompt below — this file is for reference, not the prompt itself)*
