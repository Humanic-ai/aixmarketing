
---
name: templates
description: This skill should be used when the user asks to "use a template", "apply a template", "list templates", "show me the template for", "what templates are available", "create from template", or wants to reuse an existing prompt structure for a marketing asset. Also activates when the user references a specific module folder (e.g. "01-email-basics", "07-ads") and wants to generate output from it.
version: 1.0.0
---

# Templates Skill

This skill helps you browse, select, and apply the prompt templates in this repository to generate marketing content.

## What Is a Template Here?

Every `prompts/` folder in each module contains markdown prompt files with this structure:

```
## Role / Context
## Task
## Format
## Constraints
## Example Input → Output  (few-shot files only)
```

Templates are organized by module and channel. Always ground output in a brand brief before applying any template.

## Available Template Modules

| Module | Folder | Templates Inside |
|--------|--------|-----------------|
| Brand Brief | `00-brand-brief/prompts/` | Charlie-style brand brief |
| Email Basics | `01-email-basics/prompts/` | One-shot, few-shot, role-based email copy |
| Email Headers | `02-email-headers/prompts/` | Image/video header briefs |
| Email Sequences | `03-email-sequences/prompts/` | Multi-step nurture sequences |
| Cold Email | `04-cold-email-instantly/prompts/` | Cold outreach → Instantly.ai upload |
| Lifecycle / Humanic | `05-lifecycle-humanic/prompts/` | Lifecycle trigger emails → Humanic |
| AEO | `06-aeo/prompts/` | Answer Engine Optimization content |
| Ads | `07-ads/prompts/` | Google Search / PMax + Meta ad copy |
| Blog / Substack | `08-blog-substack/prompts/` | Long-form blog posts, newsletters |
| Website | `09-website/prompts/` | Landing page copy, hero, CTAs |
| Social | `10-social/prompts/` | Instagram captions, TikTok scripts |
| YouTube | `11-youtube/prompts/` | Video scripts, titles, descriptions |
| Reddit | `12-reddit/prompts/` | Subreddit strategy, post/comment templates |
| LinkedIn | `13-linkedin/prompts/` | Thought leadership, carousel copy |

## How to Apply a Template

When the user asks to use or apply a template:

1. **Read the brand context** — check if a brand brief is already in session. If not, prompt the user to run `/brand-brief` first.
2. **Identify the right template** — match the user's request to the module above. Read the relevant prompt file(s) from `prompts/`.
3. **Fill in the template** — substitute brand voice, ICP, product details, and any user-supplied specifics into the prompt structure.
4. **Generate the output** — produce the marketing asset following the template's Format and Constraints sections.
5. **Offer iteration** — after output, ask if they want to refine tone, length, CTA, or try a variant.

## Listing Templates

When the user asks "what templates are available" or "list templates":

- Read the `prompts/` directory of the relevant module (or all modules if unspecified).
- Return a concise list of file names with a one-line description of each.

## Creating a New Template

When the user wants to save a new template:

1. Identify the appropriate module folder.
2. Create a new `.md` file in `prompts/` using the standard structure:
   ```
   ## Role / Context
   ## Task
   ## Format
   ## Constraints
   ```
3. Confirm the file path to the user.

## Key Rules

- **Brand brief first** — never generate content without brand context loaded.
- **Prompts are the product** — preserve the template structure; do not collapse sections.
- **Iterate, don't restart** — use Claude's session context to refine, not regenerate from scratch.
- **Show the chain** — for sequence templates, show each step's reasoning, not just the final output.
