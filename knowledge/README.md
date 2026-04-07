# clinicIQ — Knowledge Base
**The shared intelligence layer for all clinicIQ agents**

## How This Works

Agent specs define what an agent *does*.
Knowledge files define what agents *know*.

These are separate on purpose:
- Sub-agent specs stay clean and role-focused
- Knowledge is reusable across agents (the hook swipe bank is read by the Content Builder, the Ad Creative Builder, and the Email Builder)
- Knowledge updates in one place → every agent that reads it is immediately smarter
- Knowledge base documents are built after the full agent architecture (Steps 1–22) is complete

## Folder Map

| Folder | Contents | Primary Agents That Read It |
|---|---|---|
| `/hooks/` | Cross-industry viral hook patterns, health niche adaptations, performance data | Content Builder, Ad Creative Builder, Email Builder |
| `/copy_frameworks/` | Direct response frameworks, Meta ad standards, email standards, image copy standards | All Builder agents |
| `/compliance/` | Meta health ad policy, health claim rules, specialty-specific rules | Content Builder, Ad Creative Builder, Email Builder, Funnel Builder |
| `/production/` | HTML/CSS render standards, platform dimensions, video production, design principles | Content Builder, Ad Creative Builder, Lead Magnet Builder, Webinar Builder |
| `/frameworks/` | Perfect Webinar, Fladlein, funnel page copy, quiz best practice, email sequences | Webinar Builder, Funnel Builder, Email Builder, Lead Magnet Builder |
| `/avatars/` | Health avatar psychology, awareness level frameworks | All Builder agents |

## Status

Knowledge base documents are built in the phase after Steps 1–22 architecture is finalized.
Each file in this folder is a placeholder until that phase begins.

## Build Priority (when knowledge base phase begins)

1. `/hooks/cross_industry_hook_patterns.md` — used by more agents than any other file
2. `/production/html_css_render_standard.md` — governs all visual asset production
3. `/compliance/meta_health_ad_policy.md` — affects every paid creative
4. `/frameworks/perfect_webinar_framework.md` — from Expert Secrets (already synthesized in references/)
5. `/avatars/health_avatar_psychology.md` — foundation for all copy and creative
6. All remaining files

## Living Documents

Some knowledge files update automatically from performance data:
- `/hooks/hook_performance_data.md` — updated monthly by Ad Performance Analyst
- `/compliance/` files — updated when platform policies change
- `/avatars/health_avatar_psychology.md` — updated as IQ Profile interview data accumulates
