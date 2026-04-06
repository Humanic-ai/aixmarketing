# AIX Marketing — Agentic Marketing with Claude

A hands-on lab showing how to use Claude and Claude Code to power every layer of a modern marketing stack.

## Quick Start

```bash
# 1. Clone and enter
cd aixmarketing

# 2. Install dependencies
npm install

# 3. Set up environment
cp .env.example .env
# Edit .env with your Anthropic API key and integration credentials

# 4. Open in Claude Code
claude .
```

## What's Inside

```
aixmarketing/
├── 00-brand-brief/        ← Start here. Everything inherits from the brand brief.
├── 01-email-basics/       ← Prompting 101: one-shot, few-shot, role-based
├── 02-email-headers/      ← Image & video header briefs for email
├── 03-email-sequences/    ← Multi-email sequences as complex agentic tasks
├── 04-cold-email-instantly/  ← Claude → Instantly.ai cold outreach pipeline
├── 05-lifecycle-humanic/  ← Claude → Humanic lifecycle email triggers
├── 06-aeo/                ← Answer Engine Optimization for AI search
├── 07-ads/                ← Google + Meta ad copy generation
├── 08-blog-substack/      ← Long-form content & Substack newsletters
├── 09-website/            ← Landing pages, hero copy, CTAs
├── 10-social/             ← Instagram, TikTok content & ad briefs
├── 11-youtube/            ← Video scripts, titles, descriptions
├── 12-reddit/             ← Community-native Reddit strategy
├── 13-linkedin/           ← Thought leadership & company content
└── shared/                ← Brand templates, ICP, tone of voice
```

## Slash Commands (inside Claude Code)

| Command | What it does |
|---------|-------------|
| `/brand-brief` | Generate a complete brand brief |
| `/cold-email [company]` | Write a personalized cold email |
| `/email-sequence [goal]` | Build a multi-email nurture sequence |
| `/google-ad [product]` | Generate Google Search ad variants |
| `/meta-ad [product]` | Generate Meta ad creative copy |
| `/blog-post [topic]` | Write a full SEO blog post |
| `/linkedin-post [topic]` | Write a LinkedIn thought-leadership post |
| `/youtube-script [topic]` | Write a YouTube video script |
| `/reddit-post [subreddit] [topic]` | Craft an authentic Reddit post |
| `/social-caption [platform] [topic]` | Write platform-native captions |
| `/aeo-content [question]` | Create AEO-optimized answer content |

## Integrations

| Tool | Module | Purpose |
|------|--------|---------|
| [Instantly.ai](https://instantly.ai) | `04-cold-email-instantly/` | Cold email sequencing & sending |
| [Humanic](https://humanic.ai) | `05-lifecycle-humanic/` | AI-native lifecycle email |
| [Substack](https://substack.com) | `08-blog-substack/` | Newsletter publishing |

## Prerequisites
- Node.js 18+
- Anthropic API key
- (Optional) Instantly.ai API key for Module 04
- (Optional) Humanic API key for Module 05
