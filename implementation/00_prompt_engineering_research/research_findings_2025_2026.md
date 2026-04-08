# Prompt Engineering Research Findings 2025–2026
## Sources: Anthropic Engineering Blog, Building Effective Agents (Anthropic), Context Engineering Research

---

## Finding 1: "Context Engineering" Has Replaced "Prompt Engineering"
**Source:** Anthropic Engineering, 2025

Prompt engineering = how to write prompts.
Context engineering = what information to put in the window at each step.

The shift happened because agents run in loops. Each loop generates more data that *could* be relevant. The real skill is curating what gets passed forward.

**clinicIQ implication:** The 198-field dossier is not a prompt — it's a context object. Each agent gets a slice of it, not the whole thing. Context slicing (Step 3) is the most technically important part of this build.

---

## Finding 2: Context Rot Is Real
**Source:** ChromaDB research via Anthropic, 2025

As token count increases, recall accuracy decreases — even within the context window. This is called "context rot." Every unnecessary token degrades performance.

Key insight: **LLMs have an "attention budget."** Every token draws from that budget. Irrelevant tokens aren't neutral — they actively hurt performance.

**clinicIQ implication:**
- Never give an agent the full 198-field dossier
- Compress tool outputs before passing them forward
- Use structured note-taking (e.g., a progress state object) rather than accumulating raw conversation history

---

## Finding 3: The Orchestrator-Workers Pattern Is Right for clinicIQ
**Source:** Anthropic Building Effective Agents, 2025

The orchestrator-workers pattern: a central LLM dynamically breaks tasks into subtasks, delegates to worker agents, synthesizes results. Unlike parallel processing, subtasks are determined at runtime based on input — not predefined.

> "This workflow is well-suited for complex tasks where you can't predict the subtasks needed."

This is *exactly* clinicIQ's architecture: Lead Agent receives expert intake, determines what sub-agents to call (web scraper, voice DNA analyst, ICP builder, etc.), synthesizes their outputs into the dossier.

**clinicIQ implication:** The Lead Agent is an orchestrator. Sub-agents are workers. Sub-agents return **condensed summaries** (1,000–2,000 tokens), not raw outputs. The Lead Agent synthesizes.

---

## Finding 4: Sub-Agent Summaries, Not Raw Outputs
**Source:** Anthropic multi-agent research system, 2025

In Anthropic's multi-agent research system, each sub-agent may explore extensively (tens of thousands of tokens) but returns a **condensed summary of 1,000–2,000 tokens** to the orchestrator. This keeps the orchestrator's context clean.

**clinicIQ implication:** The Web Scraper sub-agent doesn't return raw HTML. It returns a structured extraction of: [brand_voice_sample, offer_structure, social_proof_elements, content_themes]. The Onboarding Lead only processes the extraction.

---

## Finding 5: The Evaluator-Optimizer Pattern = How Quality Gates Work
**Source:** Anthropic Building Effective Agents, 2025

Evaluator-optimizer workflow: one LLM generates output, another evaluates it in a loop. This maps directly to quality gate architecture.

> "Signs of good fit: LLM responses can be demonstrably improved when a human articulates their feedback; and the LLM can provide such feedback."

**clinicIQ implication:** The 7 quality gates are evaluator agents. They don't just pass/fail — they return specific improvement instructions back to the builder agent. The builder revises. Loop continues until gate passes or escalation threshold is hit.

---

## Finding 6: System Prompts Have a "Right Altitude"
**Source:** Anthropic context engineering, 2025

Two failure modes:
1. **Too specific:** Hardcoded brittle if-else logic in prompts. Fragile, high maintenance.
2. **Too vague:** High-level guidance that assumes shared context. The model guesses.

The "right altitude": specific enough to guide behavior, flexible enough to provide heuristics.

> "Specific enough to guide behavior effectively, yet flexible enough to provide the model with strong heuristics to guide behavior."

**clinicIQ implication:** We don't hardcode "if dossier field 47 is empty, ask question X." We define the **principle**: "When a required field is missing, ask the single most valuable clarifying question before proceeding. Never ask more than one question at a time."

---

## Finding 7: Tools Need as Much Engineering as Prompts
**Source:** Anthropic SWE-bench case study, 2025

> "We actually spent more time optimizing our tools than the overall prompt."

Tool definitions should include:
- Clear purpose description
- When to use it
- When NOT to use it  
- Input parameter descriptions
- Example usage
- Edge cases

**clinicIQ implication:** Every sub-agent the Onboarding Lead can call must have a tool definition written to this standard. The tool definition IS part of the system prompt engineering effort.

---

## Finding 8: Start Minimal, Add Complexity Only When It Helps
**Source:** Anthropic, 2025

> "We recommend finding the simplest solution possible, and only increasing complexity when needed."

> "You should consider adding complexity only when it demonstrably improves outcomes."

**clinicIQ implication:** Start with the Onboarding Lead Agent having 5 sub-agents. Don't build all 12 sub-agents at once. Measure performance. Add complexity when a gap is identified, not speculatively.

---

## Finding 9: Compaction for Long-Running Workflows
**Source:** Anthropic context engineering, 2025

For multi-session workflows, compaction is critical: summarize conversation history, reinitialize with summary, continue. Preserve: architectural decisions, unresolved items, critical state. Discard: redundant tool outputs, intermediate steps.

**clinicIQ implication:** The Expert Dossier IS the compacted state. When a new session begins with the same expert, the dossier loads as context — not the conversation history. The dossier is a living compaction artifact.

---

## Finding 10: Routing + Specialization Beats One Giant Agent
**Source:** Anthropic routing workflow, 2025

> "Routing classifies an input and directs it to a specialized followup task. Without this workflow, optimizing for one kind of input can hurt performance on other inputs."

**clinicIQ implication:** The IQ Claw Core Orchestrator routes expert requests to the right Layer agent. A content request goes to Layer 3 Content Builder agents. A strategy question goes to Layer 2 Strategy agents. A routing mistake = wrong expert gets wrong output.

---

## Summary Table

| Finding | Key Principle | Applied To |
|---------|--------------|------------|
| Context > Prompt | Engineer the window, not just the text | All agents |
| Context Rot | Every token has cost — keep it lean | Dossier slicing |
| Orchestrator-Workers | Lead delegates, workers summarize | Lead Agent architecture |
| Condensed Summaries | Sub-agents return 1K–2K token outputs | Sub-agent design |
| Evaluator-Optimizer | Quality gates are evaluator agents in a loop | Gate logic |
| Right Altitude | Principle > if-else; not too vague, not too brittle | All system prompts |
| Tool Engineering | Tools need same rigor as prompts | Sub-agent tool definitions |
| Start Minimal | Add complexity only when proven needed | Build sequence |
| Compaction | Dossier = compacted session state | Multi-session design |
| Routing | Right agent for right input | Orchestrator design |

---
*Sources: anthropic.com/engineering/effective-context-engineering-for-ai-agents, anthropic.com/research/building-effective-agents*
