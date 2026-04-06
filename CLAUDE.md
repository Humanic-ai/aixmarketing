# AIX Marketing — Claude Code Workspace

This repository is a **teaching lab** for agentic marketing use cases built on Claude. Each numbered module is a self-contained demo showing how Claude can power a specific marketing workflow.

## Repo Purpose
Demonstrate to new practitioners how to use Claude Code for end-to-end marketing — from brand brief generation through channel-specific content, paid ads, and third-party integrations (Instantly.ai, Humanic, Substack, etc.).

## Module Map
| # | Module | What It Demos |
|---|--------|---------------|
| 00 | `00-brand-brief/` | Generating a Charlie-style brand brief — the foundation everything else inherits |
| 01 | `01-email-basics/` | One-shot, few-shot, and role-based prompting for email copy |
| 02 | `02-email-headers/` | Prompting for image/video email header briefs |
| 03 | `03-email-sequences/` | Multi-step sequences as a complex chained task |
| 04 | `04-cold-email-instantly/` | Cold outreach copy → Instantly.ai campaign upload |
| 05 | `05-lifecycle-humanic/` | Lifecycle email triggers → Humanic integration |
| 06 | `06-aeo/` | Answer Engine Optimization — structure content for AI search |
| 07 | `07-ads/` | Google Search / PMax + Meta ad creative copy |
| 08 | `08-blog-substack/` | Long-form blog posts and Substack newsletter editions |
| 09 | `09-website/` | Landing page copy, hero sections, CTA variants |
| 10 | `10-social/` | Instagram captions, TikTok scripts, social ad briefs |
| 11 | `11-youtube/` | Video scripts, titles, descriptions, thumbnail copy |
| 12 | `12-reddit/` | Subreddit strategy, authentic post + comment templates |
| 13 | `13-linkedin/` | Thought leadership, company posts, carousel copy |

## Conventions

### Prompt Files
Every `prompts/` folder contains markdown files with this structure:
```
## Role / Context
## Task
## Format
## Constraints
## Example Input → Output  (for few-shot files)
```

### Brand Context
Always start a session by running `/brand-brief` or reading `shared/brand-context-template.md`. All downstream prompts assume brand context is loaded.

### Environment Variables
Copy `.env.example` → `.env` and fill in API keys before running any `demo.js` script.

### Slash Commands
Run `/help` in Claude Code to see all available slash commands for this project. Key ones:
- `/brand-brief` — generate a brand brief
- `/cold-email` — write a cold outreach email
- `/email-sequence` — build a multi-email nurture sequence
- `/google-ad` — generate Google Search ad variants
- `/meta-ad` — generate Meta ad copy
- `/blog-post` — write a full blog post
- `/linkedin-post` — write a LinkedIn post
- `/youtube-script` — write a YouTube video script
- `/reddit-post` — craft a Reddit post
- `/social-caption` — write Instagram/TikTok captions
- `/aeo-content` — create AEO-optimized content

## Teaching Flow for Demos
1. Start with `00-brand-brief` — set the brand context
2. Show `01-email-basics` — explain prompting techniques with side-by-side comparison
3. Walk through `03-email-sequences` — show chaining / complex tasks
4. Pick one channel demo (ads, social, YouTube) based on audience interest
5. Show an integration (`04-cold-email-instantly` or `05-lifecycle-humanic`)

## Key Principles
- **Prompts are the product** — the quality of output depends entirely on prompt structure
- **Brand brief first** — always ground outputs in brand voice before generating content
- **Iterate, don't regenerate** — use Claude's context to refine, not restart
- **Show the chain** — for sequences, show each step's reasoning, not just final output
