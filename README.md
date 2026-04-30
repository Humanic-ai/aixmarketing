# AIxMarketing by Humanic

**Agentic lifecycle marketing powered by Claude Code skills.**

Build, preview, and deploy lifecycle email campaigns — welcome series, abandoned cart recovery, re-engagement, newsletters — all from your terminal using Claude Code slash commands and skills.

This is an open-source reference implementation by [Humanic](https://humanic.ai) showing how to use Claude Code as a full lifecycle marketing co-pilot.

---

## What This Repo Does

Instead of writing marketing emails from scratch every time, this repo gives you **reusable Claude Code skills and slash commands** that:

1. **Generate brand-grounded content** — Every output inherits your brand voice via `/brand-brief`
2. **Fetch live inspiration** — Skills pull real examples from Really Good Emails, Email Love, Litmus, and more before writing
3. **Chain multiple AI models** — The `humanic-auto` skill runs Claude Sonnet → Gemini → OpenAI → Claude Opus in sequence for the best possible email
4. **Produce client-safe HTML** — The `email-preview` skill audits and generates HTML that renders across Gmail, Outlook, Yahoo, and Apple Mail
5. **Connect to Humanic** — Push campaigns directly to [Humanic](https://humanic.ai) via MCP for sending and lifecycle automation

---

## Quick Start

### Prerequisites
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed (`npm install -g @anthropic-ai/claude-code`)
- Node.js 18+
- Anthropic API key

### Setup

```bash
# Clone the repo
git clone https://github.com/Humanic-ai/aixmarketing.git
cd aixmarketing

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys

# Open in Claude Code
claude .
```

### Connect to Humanic (optional)

Add Humanic as an MCP server to push campaigns directly:

```bash
claude mcp add humanic --transport http https://devmcp.humanic.ai/mcp \
  --header "Authorization: Bearer YOUR_HUMANIC_API_KEY" --scope project
```

Or create `.mcp.json` in the project root:

```json
{
  "mcpServers": {
    "humanic": {
      "type": "http",
      "url": "https://devmcp.humanic.ai/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_HUMANIC_API_KEY"
      }
    }
  }
}
```

---

## Slash Commands

Type these directly in Claude Code to generate marketing content:

| Command | What It Does |
|---------|-------------|
| `/brand-brief` | Generate a brand brief — the foundation for all other outputs |
| `/cold-email` | Write a personalized cold outreach email (Instantly.ai-ready) |
| `/email-sequence` | Build a multi-email nurture sequence |
| `/google-ad` | Generate Google Search RSA + PMax ad variants |
| `/meta-ad` | Generate Meta (Facebook/Instagram) ad creative copy |
| `/blog-post` | Write a full SEO blog post or Substack newsletter |
| `/linkedin-post` | Write a LinkedIn post optimized for reach |

## Skills (31 skills across 4 domains)

Skills are multi-step agentic workflows organized into domains with **orchestrators** that chain sub-skills automatically.

### Copy Generation
The **copy-orchestrator** chains: strategy → writing → QA → product enrichment in one run.

| Skill | What It Does |
|-------|-------------|
| **copy-orchestrator** | Master pipeline — runs all stages sequentially |
| **copy-strategist** | Builds audience mental model + per-component direction before writing |
| **copy-writer** | Generates subject lines, preheaders, body, CTAs from strategy |
| **copy-qa-gate** | AI-slop detector, readability scorer, brand compliance grid |
| **copy-product-expert** | Validates terminology, enriches CTAs with proof points |
| **copy-advertiser-lens** | Flags internal jargon that won't land externally |
| **copy-humanizer** | Strips AI writing tells — 39 patterns across 6 categories |
| **copy-brief-generator** | Expands a quick prompt into a structured campaign brief |
| **copy-feedback-processor** | Applies stakeholder revisions, re-runs only affected stages |

### ESP Production
The **esp-sfmc-orchestrator** routes to the correct SFMC sub-skill by intent.

| Skill | What It Does |
|-------|-------------|
| **esp-sfmc-orchestrator** | Intent router for all SFMC tasks |
| **esp-ampscript-expert** | Writes, explains, debugs AMPscript |
| **esp-cio-liquid-logic** | Liquid templates for Customer.io |
| **esp-cio-eds-updater** | Customer.io email design system components |
| **esp-sfmc-content-builder** | Content Builder blocks, template extraction |
| **esp-sfmc-data-fetcher** | CLI for querying Data Extensions |
| **esp-sfmc-sql-generator** | Auto-writes SQL for Query Studio |
| **esp-sfmc-automation** | Automation Studio — plan, build, troubleshoot |
| **esp-sfmc-journey-manager** | Journey Builder — design, configure, debug |
| **esp-sfmc-knowledge** | SFMC concept reference and troubleshooting |

### Performance & Reporting

| Skill | What It Does |
|-------|-------------|
| **perf-journey-auditor** | Journey audit — sends, rates, drop-off, recommendations |
| **perf-sfmc-email-engagement** | Triggered-send metrics via SFMC Data Views |
| **perf-klaviyo** | Flows, segments, campaigns, metrics in Klaviyo |

### Process & QA

| Skill | What It Does |
|-------|-------------|
| **qa-email-design-reviewer** | Scores HTML for layout, hierarchy, render-readiness |
| **qa-email-production-process** | Pre-send launch checklist (copy, design, data, legal) |
| **qa-incident-tracker** | RCA logging — 5 Whys, incident report, prevention plan |

### Lifecycle Campaigns (standalone)

| Skill | What It Does |
|-------|-------------|
| **welcome-series** | Multi-email welcome sequence grounded in live examples |
| **abandoned-cart** | Cart recovery emails from 5 scored real-world sources |
| **re-engagement** | 3-email win-back sequence with graceful exit |
| **email-preview** | Cross-client HTML audit and client-safe code generation |
| **humanic-auto** | 4-model chain (Sonnet → Gemini → OpenAI → Opus) |
| **templates** | Template browsing, application, and management |

---

## How It Works

### 1. Start with a brand brief
```
/brand-brief Humanic — AI-native lifecycle email platform for product-led growth teams
```
This loads your brand voice, ICP, positioning, and tone into session context. Every subsequent command inherits it.

### 2. Run the copy pipeline
```
Write email copy for our abandoned cart flow
```
The **copy-orchestrator** chains 4+ stages automatically:
```
strategist → writer → QA gate → product expert → [advertiser lens] → [humanizer]
```
Each stage's output feeds the next. The QA gate catches AI slop, readability issues, and brand violations. The product expert enriches CTAs with proof points.

### 3. Generate lifecycle content
```
Write a welcome email for new trial users
```
Standalone skills like `welcome-series`, `abandoned-cart`, and `re-engagement` fetch live examples from Really Good Emails, Email Love, Litmus, and more — score them against your brand — and produce complete emails.

### 4. Work with your ESP
```
Write AMPscript to personalize the email with the user's plan name
```
The **SFMC orchestrator** routes to the right sub-skill. Or invoke ESP skills directly:
- `Write SQL for Query Studio` → esp-sfmc-sql-generator
- `Customer.io Liquid for conditional content` → esp-cio-liquid-logic
- `Build a journey for onboarding` → esp-sfmc-journey-manager

### 5. QA and launch
```
Launch checklist for this email
```
The `qa-email-production-process` skill runs a 40+ point checklist across copy, design, links, data, deliverability, and legal compliance — producing a GO / NO-GO verdict.

### 6. Push to Humanic
With the Humanic MCP server connected, you can list campaigns, create cohorts, and push content directly:
```
List my campaigns on Humanic
Create a new welcome campaign for trial users
```

### 7. Audit performance
```
Audit my welcome journey
```
The `perf-journey-auditor` skill benchmarks your metrics, identifies drop-off points, and gives specific recommendations.

---

## Project Structure

```
aixmarketing/
├── .claude/
│   ├── commands/              ← Slash commands (7 markdown prompts)
│   └── skills/                ← 31 agentic skills organized by domain
│       ├── copy-orchestrator/     ← Copy pipeline controller
│       ├── copy-strategist/       ← Audience model + direction
│       ├── copy-writer/           ← Email copy generation
│       ├── copy-qa-gate/          ← Quality gate (slop, readability, brand)
│       ├── copy-product-expert/   ← Product accuracy + proof enrichment
│       ├── copy-advertiser-lens/  ← Jargon detection for external audiences
│       ├── copy-humanizer/        ← AI-tell removal (39 patterns)
│       ├── copy-brief-generator/  ← Quick prompt → full brief
│       ├── copy-feedback-processor/ ← Stakeholder revision handler
│       ├── esp-sfmc-orchestrator/ ← SFMC intent router
│       ├── esp-ampscript-expert/  ← AMPscript for SFMC
│       ├── esp-cio-liquid-logic/  ← Liquid for Customer.io
│       ├── esp-cio-eds-updater/   ← CIO design system components
│       ├── esp-sfmc-content-builder/ ← Content Builder management
│       ├── esp-sfmc-data-fetcher/ ← Data Extension queries
│       ├── esp-sfmc-sql-generator/ ← Query Studio SQL
│       ├── esp-sfmc-automation/   ← Automation Studio CLI
│       ├── esp-sfmc-journey-manager/ ← Journey Builder CLI
│       ├── esp-sfmc-knowledge/    ← SFMC reference + troubleshooting
│       ├── perf-journey-auditor/  ← Journey performance audit
│       ├── perf-sfmc-email-engagement/ ← SFMC metrics via Data Views
│       ├── perf-klaviyo/          ← Klaviyo flows, segments, metrics
│       ├── qa-email-design-reviewer/ ← HTML design scoring
│       ├── qa-email-production-process/ ← Pre-send launch checklist
│       ├── qa-incident-tracker/   ← RCA logging for send failures
│       ├── abandoned-cart/        ← Cart recovery from live examples
│       ├── email-preview/         ← Cross-client HTML audit
│       ├── humanic-auto-.../      ← 4-model AI chain
│       ├── re-engagement/         ← Win-back sequence
│       ├── templates/             ← Template management
│       └── welcome-series/        ← Welcome/onboarding sequence
├── Banners/                   ← Social media and event banners
├── CLAUDE.md                  ← Claude Code workspace instructions
├── CONTRIBUTING.md            ← Contribution guidelines
├── LICENSE                    ← MIT
├── .env.example               ← Environment variable template
├── .gitignore
├── package.json
└── README.md
```

---

## Environment Variables

Copy `.env.example` to `.env` and fill in:

| Variable | Required | Used By |
|----------|----------|---------|
| `ANTHROPIC_API_KEY` | Yes | All commands and skills |
| `OPENAI_API_KEY` | Optional | `humanic-auto` skill (Stage 3 — OpenAI o3 evaluation) |
| `GEMINI_API_KEY` | Optional | `humanic-auto` skill (Stage 2 — Gemini creative enhancement) |
| `INSTANTLY_API_KEY` | Optional | `/cold-email` Instantly.ai integration |
| `HUMANIC_API_KEY` | Optional | Humanic MCP server |

---

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Ways to contribute:**
- Add new slash commands for marketing channels we haven't covered
- Add new skills with multi-step agentic workflows
- Improve existing prompts with better examples or structure
- Add integrations with other marketing tools via MCP
- Share your brand brief templates and email examples

---

## License

MIT License. See [LICENSE](LICENSE).

---

Built by [Humanic](https://humanic.ai) — AI-native lifecycle email for product-led growth teams.
