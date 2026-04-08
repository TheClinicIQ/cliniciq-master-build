# Leaked Prompts Analysis
## Source: Real Production System Prompts (2025–2026)
### Studied: Claude Sonnet 4.6 (Anthropic), Cursor Agent (GPT-4.1), Cline, Devin, Aider

---

## Key Structural Patterns From Real Production Prompts

### 1. XML/Semantic Tagging — Claude's #1 Pattern
Claude's production prompt uses XML tags to organize every major section:
```
<claude_behavior>
  <product_information> ... </product_information>
  <refusal_handling> ... </refusal_handling>
  <tone_and_formatting> ... </tone_and_formatting>
  <user_wellbeing> ... </user_wellbeing>
  <knowledge_cutoff> ... </knowledge_cutoff>
</claude_behavior>
```
**Why it works:** The model parses tags as semantic containers. Each section is self-contained with clear scope. No ambiguity about what applies where.

**clinicIQ application:** Every agent prompt should use XML tags for each section. This isn't cosmetic — it's structural.

---

### 2. Hard Rules vs. Soft Rules — Always Separated
Every production prompt separates:
- **Hard constraints** (never violate): `<refusal_handling>`, safety rules, output format requirements
- **Soft preferences** (default behavior): tone, formatting style, how to handle edge cases

Cursor's agent prompt separates these explicitly:
```
## Critical Formatting Rules (ALWAYS Follow)  ← hard
## When to Use This Tool                       ← soft
## When NOT to Use                             ← hard boundary
```

**clinicIQ application:** Each agent prompt needs explicit HARD RULES and SOFT PREFERENCES sections. Quality gates = hard rules.

---

### 3. "When to Use / When NOT to Use" Patterns
Cursor and Cline both use explicit negative scope — what the agent should NOT do — as prominently as positive scope.

Cursor's `codebase_search` tool:
```
### When to Use This Tool
### When NOT to Use
1. Exact text matches (use grep)
2. Reading known files (use read_file)
```

**clinicIQ application:** Every agent needs an explicit OUT OF SCOPE section. The Onboarding Agent should never write content. The Content Builder should never modify strategy. These boundaries prevent agent drift.

---

### 4. Examples As the "Picture Worth 1000 Words"
Every production prompt includes concrete `<example>` blocks — not descriptions of examples, actual examples:
```xml
<example>
Query: "Where do we encrypt user passwords before saving?"
<reasoning>Good: Clear question about specific process with context.</reasoning>
</example>

<example>
Query: "AuthService"
<reasoning>BAD: Single word searches should use grep instead.</reasoning>
</example>
```

**clinicIQ application:** Every agent needs 2–3 good examples and 1–2 anti-examples (what NOT to do). This is the single highest-leverage improvement vs. basic prompts.

---

### 5. State + Context Injection — Not Assumptions
Cursor's Sonnet 4.6 prompt explicitly handles state management:
```
Claude has no memory between completions. Always include all relevant state in each request.
```
And provides the exact pattern for injecting state:
```javascript
const gameState = { player: {...}, history: [...] };
messages: [{ role: "user", content: `Given this state: ${JSON.stringify(gameState)}` }]
```

**clinicIQ application:** The 198-field dossier is NOT assumed to be in the prompt — it is INJECTED as structured state. The prompt instructs the agent how to receive and use it, not to assume it.

---

### 6. Tool Documentation as Prompt Engineering
Anthropic's research finding: "We spent more time optimizing our tools than the overall prompt."

Cursor's tools have full TypeScript type definitions with:
- Purpose description
- When to use
- When NOT to use
- Parameter descriptions
- Examples

**clinicIQ application:** Each sub-agent the Onboarding Lead delegates to must have a tool definition as carefully written as the system prompt itself.

---

### 7. Failure Mode Handling — Always Explicit
Claude's prompt explicitly addresses what to do when uncertain:
- "Claude does its best to address the person's query, even if ambiguous, before asking for clarification"
- When knowledge is insufficient → use web search first, then answer
- When refusing → maintain conversational tone, never abandon the user

Cursor's agent: "If you fail to edit a file, you should read the file again with a tool before trying to edit again."

**clinicIQ application:** Every agent needs a FAILURE MODES section: what to do when dossier fields are missing, when quality gates fail, when a sub-agent returns no result.

---

### 8. Identity Lock = One Crisp Sentence
Cursor: "You are an AI coding assistant, powered by GPT-4.1. You operate in Cursor."
Claude Code: "You are Claude, an AI assistant made by Anthropic."
Devin: "You are Devin, a software engineer..."

**Pattern:** Identity = [role] + [what you do] + [where you operate]. Never more than 2 sentences.

**clinicIQ application:** "You are the Onboarding Lead Agent for ClinicIQ. Your job is to transform a health expert's raw intake data into a complete, validated 198-field Expert Dossier that powers every agent in the platform."

---

### 9. Output Format = Contract, Not Suggestion
Claude's prompt for artifacts includes exact API contract:
```javascript
const response = await fetch("https://api.anthropic.com/v1/messages", {
  body: JSON.stringify({
    model: "claude-sonnet-4-20250514",
    messages: [{ role: "user", content: "Your prompt here" }]
  })
});
// data.content returns mix of text and tool_use blocks
```

**clinicIQ application:** Output format is specified as JSON schema with field names, types, and what to return when fields are unknown. The agent NEVER guesses format.

---

### 10. Minimal Viable Context — "Smallest High-Signal Set"
Anthropic's context engineering research: "Find the smallest possible set of high-signal tokens that maximize the likelihood of your desired outcome."

Context rot is real: as tokens increase, recall accuracy decreases. Every unnecessary token is a liability.

**clinicIQ application:** This is the entire rationale for context slicing (Step 3 of our build). The Onboarding Agent gets dossier fields 1–40. The Content Builder gets fields 41–120. No agent gets all 198 fields. This isn't a limitation — it's a performance feature.

---

## Summary: The 10 Principles We're Building Into Every clinicIQ Prompt

| # | Principle | Source |
|---|-----------|--------|
| 1 | XML semantic tags for all sections | Claude Sonnet 4.6 |
| 2 | Separate hard rules from soft preferences | Cursor, Cline |
| 3 | Explicit IN SCOPE / OUT OF SCOPE | Cursor agent |
| 4 | Good + bad examples (not just descriptions) | All production prompts |
| 5 | State injected at runtime, not assumed | Cursor, Claude |
| 6 | Tool definitions as careful as system prompt | Anthropic research |
| 7 | Explicit failure mode handling | Claude, Cursor, Devin |
| 8 | Identity in 1–2 sentences max | All production prompts |
| 9 | Output as contract (JSON schema) | Claude artifacts |
| 10 | Minimal context — only what the agent needs | Anthropic context engineering |

---
*Sources: github.com/EliFuzz/awesome-system-prompts (leaked), anthropic.com/engineering/effective-context-engineering-for-ai-agents, anthropic.com/research/building-effective-agents*
