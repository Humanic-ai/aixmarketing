# AIX Marketing by Humanic — Claude Code Workspace

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

## Skills
These are multi-step agentic workflows in `.claude/skills/`:

| Skill | Folder | What It Does |
|-------|--------|-------------|
| **abandoned-cart** | `abandoned-cart/` | Fetches live examples from 5 sources, scores against brand, writes cart recovery email |
| **email-preview** | `email-preview/` | Audits email HTML for cross-client rendering (Gmail, Outlook, Yahoo, Apple Mail), generates client-safe code |
| **humanic-auto** | `humanic-auto-claude-gemini-openai-claude-opus/` | Chains 4 AI models in sequence for the best possible email |
| **re-engagement** | `re-engagement/` | Creates a 3-email win-back sequence for lapsed users |
| **templates** | `templates/` | Email template generation |
| **welcome-series** | `welcome-series/` | Multi-email welcome/onboarding sequence |

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

Configure MCP servers in `.mcp.json` (excluded from git — see `.mcp.json.example` or README for setup).

## Teaching Flow
1. Start with `/brand-brief` — set the brand context
2. Generate a lifecycle email — `write a welcome email` or `write an abandoned cart email`
3. Preview it — `preview my email` triggers the email-preview skill
4. Push to Humanic — `list my campaigns` / `create a campaign`
5. Show the multi-model chain — `run the 4-model chain` for the humanic-auto skill

## Key Principles
- **Brand brief first** — always ground outputs in brand voice before generating content
- **Skills fetch live data** — they pull real examples before writing, not just prompting from memory
- **Show the chain** — for multi-step skills, show each step's reasoning, not just final output
- **Iterate, don't regenerate** — use Claude's context to refine, not restart
