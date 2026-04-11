---
name: abandoned-cart
description: This skill should be used when the user asks to "write an abandoned cart email", "create a cart recovery email", "abandoned cart sequence", "recover lost carts", or wants to generate cart abandonment copy for a company. It fetches live examples from reallygoodemails.com, selects the top 5 most relevant to the brand, and uses them as creative reference to write a tailored abandoned cart email.
version: 1.0.0
disable-model-invocation: false
---

# Abandoned Cart Email Skill

Generate a high-converting abandoned cart email grounded in real-world examples from the best email marketers, tailored to the brand in session.

## Step 1 — Load Brand Context

Check if a brand brief is already in session context.
- If yes: note the company name, ICP, product category, brand voice, and key differentiators.
- If no: ask the user to run `/brand-brief` first, or ask them to describe the company (product category, target customer, brand tone) before proceeding.

## Step 2 — Fetch Live Abandoned Cart Examples

Use the WebFetch tool to retrieve the current examples from:

**URL:** `https://reallygoodemails.com/categories/abandoned-cart`

**Prompt to use when fetching:**
> "List every abandoned cart email example on this page. For each one extract: brand name, email subject line or title, product category, notable copy or hooks used, urgency/incentive tactics, and any personalization techniques shown."

## Step 3 — Select the Top 5 Most Relevant Examples

From the fetched list, score each example against the brand context on these criteria:

| Criteria | What to look for |
|----------|-----------------|
| **Industry match** | Same or adjacent product category (e.g. apparel, SaaS, pet, beauty, furniture) |
| **ICP alignment** | Tone and voice matches the brand's target customer persona |
| **Tactic relevance** | Urgency, social proof, incentive, personalization — pick what fits this brand's positioning |
| **Funnel stage match** | First reminder vs. final nudge vs. winback |

Select the **top 5** examples. For each one, output:
- Brand name + subject line
- Why it's relevant to this brand
- The specific tactic or copy element worth borrowing

## Step 4 — Write the Abandoned Cart Email

Using the 5 selected examples as creative reference, write a complete abandoned cart email for the brand. Structure:

### Email Output Format

```
SUBJECT LINE OPTIONS (3 variants):
1. [Direct/urgency]
2. [Curiosity/question]
3. [Benefit/incentive]

PREVIEW TEXT:
[One line that complements the subject]

---

BODY:

[Opening hook — 1-2 sentences that acknowledge the cart without being pushy]

[Product reminder block — name what they left behind, why it's worth coming back for]

[Value reinforcement — 1-2 sentences on the brand's key differentiator or social proof]

[Urgency or incentive — stock scarcity / time limit / offer if applicable]

[CTA button copy]

[Soft close — optional P.S. or secondary CTA]
```

### Voice Rules
- Match the brand voice adjectives from the brand brief exactly.
- Avoid: generic "you left something behind" clichés unless the brand is very literal/direct.
- Prefer: a hook that matches the brand's "write like" reference from the brief.

## Step 5 — Offer Variants

After delivering the email, offer:
1. A **sequence version** — 3-email drip (Day 1 reminder / Day 3 incentive / Day 7 last chance)
2. A **SMS companion** — 1 short text message to pair with the email
3. A **subject line A/B test** — 2 additional subject variants to test

## Key Rules

- Always fetch live from reallygoodemails.com — do not rely on cached or memorized examples.
- Always show which real-world examples influenced the output and why.
- Never invent urgency that contradicts the brand (e.g. "almost sold out" for a SaaS product).
- If no brand brief is loaded, collect minimum viable context: product name, 1 sentence on who buys it, brand tone (formal / casual / playful / bold).
