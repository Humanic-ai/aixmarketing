# Contributing to AIX Marketing

Thanks for your interest in contributing! This repo is maintained by [Humanic](https://humanic.ai) and open to contributions from the community.

## What You Can Contribute

### New Slash Commands
Add a markdown file to `.claude/commands/` with this structure:

```markdown
Short description of what the command does.

**Usage:** `/command-name [arguments]`

---

You are a [role]. [Instructions for Claude...]

## Output Format

[Define the exact output structure]
```

### New Skills
Create a folder in `.claude/skills/` with a `SKILL.yaml` file. Skills are multi-step workflows — see existing skills like `abandoned-cart/` or `re-engagement/` for the pattern.

A good skill:
- Fetches live data (via WebFetch) before generating content
- Scores examples against the brand context
- Shows its reasoning at each step
- Produces complete, ready-to-use output

### Improvements to Existing Prompts
- Better examples or few-shot patterns
- More precise output formatting
- Additional variants or options
- Stronger constraints that reduce generic output

### New MCP Integrations
If you have a marketing tool with an MCP server, document the setup in the README and show how it connects to the workflow.

## How to Contribute

1. **Fork** the repo
2. **Create a branch** (`git checkout -b add-tiktok-command`)
3. **Make your changes**
4. **Test in Claude Code** — run your command/skill and verify the output quality
5. **Submit a PR** with a clear description of what you added and why

## Guidelines

- **Keep prompts specific** — vague prompts produce vague output. Constrain the format, length, and structure.
- **Brand brief is the foundation** — all commands/skills should work with or without a brand brief loaded, but should use it when available.
- **No API keys in commits** — use `.env` for secrets. The `.gitignore` excludes `.env` and `.mcp.json`.
- **Test your output** — run your command at least 3 times to make sure the output is consistently good, not just good once.
- **Document the usage** — every command needs a `**Usage:**` line showing the arguments it expects.

## Code of Conduct

Be respectful, constructive, and focused on making lifecycle marketing more accessible to everyone. We're all here to learn.

## Questions?

Open an issue or reach out to the Humanic team at [humanic.ai](https://humanic.ai).
