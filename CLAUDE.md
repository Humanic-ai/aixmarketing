# AIxMarketing by Humanic — Claude Code Workspace

This repository is an **open-source teaching lab** for agentic lifecycle marketing built on Claude Code. It contains slash commands and multi-step skills that generate, preview, and deploy marketing content — grounded in brand voice and real-world examples.

Maintained by [Humanic](https://humanic.ai).

## Repo Purpose
Show practitioners how to use Claude Code skills for end-to-end lifecycle marketing — from brand brief generation through email campaigns, ads, content, and direct integration with Humanic for sending.

## Slash Commands
These are markdown prompt files in `.claude/commands/`:

| Command | File | What It Does |
|---------|------|-------------|
| `/brand-brief` | `brand-brief.md` | Generate a brand brief — the foundation for all outputs |
| `/cold-email` | `cold-email.md` | Write a cold outreach email (Instantly.ai-ready) |
| `/email-sequence` | `email-sequence.md` | Build a multi-email nurture sequence |
| `/google-ad` | `google-ad.md` | Generate Google Search RSA + PMax variants |
| `/meta-ad` | `meta-ad.md` | Generate Meta ad creative copy |
| `/blog-post` | `blog-post.md` | Write a full SEO blog post or newsletter |
| `/linkedin-post` | `linkedin-post.md` | Write a LinkedIn post for reach |

## Skill Architecture

Skills are organized into **4 domains** with orchestrators that chain sub-skills in the correct order.

### Copy Generation (orchestrator pattern: strategy → writing → QA → enrichment)

| Skill | What It Does |
|-------|-------------|
| **copy-orchestrator** | Master chain controller — runs the full pipeline in one pass |
| **copy-strategist** | Builds audience mental model and per-component direction before writing |
| **copy-writer** | Generates subject lines, preheaders, body, CTAs from strategist direction |
| **copy-qa-gate** | AI-slop detector, readability scorer, brand compliance grid, advertiser-lens scan |
| **copy-product-expert** | Validates product terminology, recommends help center links, enriches CTAs |
| **copy-advertiser-lens** | Flags internal jargon that wouldn't land with external audiences |
| **copy-humanizer** | Strips AI writing tells — 39 patterns across 6 categories |
| **copy-brief-generator** | Expands a quick prompt into a structured campaign brief |
| **copy-feedback-processor** | Applies stakeholder revisions, re-runs only affected pipeline stages |

### ESP Production (router pattern: SFMC orchestrator dispatches to sub-skills)

| Skill | What It Does |
|-------|-------------|
| **esp-sfmc-orchestrator** | Routes to the correct SFMC sub-skill based on intent |
| **esp-ampscript-expert** | Writes, explains, and debugs AMPscript for SFMC |
| **esp-cio-liquid-logic** | Writes Liquid templates for Customer.io |
| **esp-cio-eds-updater** | Updates Customer.io email design system components |
| **esp-sfmc-content-builder** | Manages Content Builder blocks, extracts AMPscript from templates |
| **esp-sfmc-data-fetcher** | CLI for querying and managing Data Extensions |
| **esp-sfmc-sql-generator** | Auto-writes SQL for SFMC Query Studio |
| **esp-sfmc-automation** | Automation Studio CLI — plan, build, troubleshoot automations |
| **esp-sfmc-journey-manager** | Journey Builder CLI — design, configure, troubleshoot journeys |
| **esp-sfmc-knowledge** | SFMC concept reference and troubleshooting guide |

### Performance & Reporting

| Skill | What It Does |
|-------|-------------|
| **perf-journey-auditor** | Audits journey performance — sends, open/click rates, drop-off, recommendations |
| **perf-sfmc-email-engagement** | Pulls triggered-send metrics from SFMC Data Views via SQL |
| **perf-klaviyo** | Query and manage Klaviyo flows, segments, campaigns, metrics |

### Process & QA

| Skill | What It Does |
|-------|-------------|
| **qa-email-design-reviewer** | Scores email HTML for layout, hierarchy, component fidelity, render-readiness |
| **qa-email-production-process** | Pre-send launch checklist across copy, design, data, legal, deliverability |
| **qa-incident-tracker** | RCA logging when sends break — 5 Whys, incident report, prevention plan |

### Lifecycle Campaign Skills (standalone)

| Skill | What It Does |
|-------|-------------|
| **abandoned-cart** | Fetches live examples from 5 sources, scores against brand, writes cart recovery email |
| **email-preview** | Audits email HTML for cross-client rendering, generates client-safe code |
| **humanic-auto** | Chains 4 AI models (Sonnet → Gemini → OpenAI → Opus) for best-possible email |
| **re-engagement** | Creates a 3-email win-back sequence for lapsed users |
| **templates** | Email template browsing, application, and management |
| **welcome-series** | Multi-email welcome/onboarding sequence grounded in live examples |

## How the Orchestrators Work

### Copy Orchestrator (sequential chain)
```
[Brief] → copy-strategist → copy-writer → copy-qa-gate → copy-product-expert
                                                                    ↓
                                              [optional] copy-advertiser-lens
                                                                    ↓
                                              [optional] copy-humanizer
                                                                    ↓
                                                              [Final Copy]
```
Each stage's output feeds the next. The QA gate auto-fixes issues. Optional stages run when needed.

### SFMC Orchestrator (intent router)
```
[User Request] → esp-sfmc-orchestrator
                        ↓
            ┌───────────┼───────────────────┐
            ↓           ↓                   ↓
    ampscript-expert  sql-generator  journey-manager  ...
```
Classifies the request and routes to the correct SFMC sub-skill. Chains sub-skills when a task spans multiple areas.

## Conventions

### Prompt Structure
Every slash command follows this structure:
```
## Role / Context
## Task
## Format
## Constraints
## Example Input → Output  (for few-shot files)
```

### Brand Context
Always start a session by running `/brand-brief`. All downstream commands and skills assume brand context is loaded.

### Environment Variables
Copy `.env.example` → `.env` and fill in API keys before running any demo script.

### MCP Integrations
The repo supports MCP servers for direct tool integration:
- **Humanic** — lifecycle email campaigns, cohorts, analytics
- **Figma** — design file access for email/ad creative briefs

Configure MCP servers in `.mcp.json` (excluded from git — see README for setup).

## Teaching Flow
1. Start with `/brand-brief` — set the brand context
2. Run the copy pipeline — `write email copy` triggers copy-orchestrator
3. Preview it — `preview my email` triggers email-preview
4. Push to Humanic — `list my campaigns` / `create a campaign`
5. QA before send — `launch checklist` triggers qa-email-production-process
6. Audit performance — `audit this journey` triggers perf-journey-auditor

## Key Principles
- **Brand brief first** — always ground outputs in brand voice before generating content
- **Skills fetch live data** — they pull real examples before writing, not just prompting from memory
- **Orchestrators chain skills** — never skip strategy or QA, the pipeline ensures quality
- **Show the chain** — for multi-step skills, show each step's reasoning, not just final output
- **Iterate, don't regenerate** — use Claude's context to refine, not restart
