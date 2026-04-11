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

## Skills

Skills are multi-step agentic workflows that fetch live data, chain reasoning, and produce production-ready output:

| Skill | What It Does |
|-------|-------------|
| **welcome-series** | Generates a multi-email welcome/onboarding sequence grounded in live examples |
| **abandoned-cart** | Writes cart recovery emails after fetching and scoring real-world examples from 5 sources |
| **re-engagement** | Creates a 3-email win-back sequence for lapsed users with a graceful exit |
| **email-preview** | Audits email HTML for cross-client compatibility (Gmail, Outlook, Yahoo, Apple Mail) and generates client-safe code |
| **humanic-auto** | Chains 4 AI models (Claude Sonnet → Gemini Flash → OpenAI o3 → Claude Opus) for the highest-quality email output |
| **templates** | Email template generation and management |

---

## How It Works

### 1. Start with a brand brief
```
/brand-brief Humanic — AI-native lifecycle email platform for product-led growth teams
```
This loads your brand voice, ICP, positioning, and tone into session context. Every subsequent command inherits it.

### 2. Generate lifecycle content
```
Write an abandoned cart email for Humanic
```
The `abandoned-cart` skill activates automatically — it fetches live examples from Really Good Emails, Email Love, Good Email Copy, Litmus, and the RGE Awards, scores them against your brand, picks the top 5, and writes a complete email with subject lines, preview text, body, and CTA.

### 3. Preview across email clients
```
Preview my email
```
The `email-preview` skill audits your email against Gmail, Yahoo, Outlook desktop (Word engine), Outlook.com, and Apple Mail — then generates production-ready HTML with inline styles, VML buttons for Outlook, dark mode support, and a per-client compatibility checklist.

### 4. Push to Humanic
With the Humanic MCP server connected, you can list campaigns, create cohorts, and push content directly:
```
List my campaigns on Humanic
Create a new welcome campaign for trial users
```

---

## Project Structure

```
aixmarketing/
├── .claude/
│   ├── commands/          ← Slash commands (markdown prompts)
│   │   ├── brand-brief.md
│   │   ├── cold-email.md
│   │   ├── email-sequence.md
│   │   ├── google-ad.md
│   │   ├── meta-ad.md
│   │   ├── blog-post.md
│   │   └── linkedin-post.md
│   └── skills/            ← Multi-step agentic skills (YAML)
│       ├── abandoned-cart/
│       ├── email-preview/
│       ├── humanic-auto-claude-gemini-openai-claude-opus/
│       ├── re-engagement/
│       ├── templates/
│       └── welcome-series/
├── Banners/               ← Social media and event banners
├── CLAUDE.md              ← Claude Code workspace instructions
├── CONTRIBUTING.md        ← Contribution guidelines
├── .env.example           ← Environment variable template
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
