---
name: welcome-series
description: This skill should be used when the user asks to "write a welcome email", "create a welcome series", "onboarding sequence", "first email to new subscribers", "welcome new users", or wants to generate a welcome email sequence for a company. It fetches live examples from reallygoodemails.com (top 2025 emails, award winners, and welcome category), selects the top 5 most relevant to the brand, and uses them as creative reference to write a tailored welcome series.
version: 1.0.0
disable-model-invocation: false
---

# Welcome Series Skill

Generate a high-converting welcome email series grounded in the best real-world examples of 2025 — award winners and most-saved emails — tailored precisely to the brand in session.

## Step 1 — Load Brand Context

Check if a brand brief is already in session context.
- If yes: note the company name, ICP, product category, brand voice adjectives, key differentiators, and funnel stage this welcome series serves (new subscriber, free trial, paying customer, etc.).
- If no: ask the user to run `/brand-brief` first, or collect minimum viable context:
  - Product/service name and one-line description
  - Who signs up (persona: role, company size, goal)
  - Brand tone (formal / casual / playful / bold / warm)
  - What action the welcome series should drive (activation, first purchase, exploration, community join)

## Step 2 — Fetch Live Welcome Email Examples

Use the WebFetch tool to retrieve current examples from **all three** of the following sources in parallel:

**Source 1 — Top Emails of 2025 (trend analysis):**
`https://reallygoodemails.com/school/top-emails-of-2025-learning`
> Prompt: "Extract all design and copy trends identified for top-performing emails in 2025, especially any welcome or onboarding patterns, subject line strategies, CTA approaches, and personalization techniques."

**Source 2 — Really Good Email Awards 2025 (award winners):**
`https://reallygoodemails.com/school/really-good-email-awards-2025`
> Prompt: "List every award winner and honorable mention. For each extract: brand name, award category, email type, subject line, notable copy techniques, design approaches, and what made it award-worthy. Focus especially on welcome, onboarding, thank-you, and retention categories."

**Source 3 — Welcome Email Category (live examples):**
`https://reallygoodemails.com/categories/welcome`
> Prompt: "List every welcome email example on this page. For each extract: brand name, subject line, product category/industry, opening hook, value proposition, CTA, personalization techniques, and what makes it a strong welcome email."

## Step 3 — Select the Top 5 Most Relevant Examples

Combine all examples from all three sources into a unified pool. Score each against the brand context on these criteria:

| Criteria | What to look for |
|----------|-----------------|
| **Industry / category match** | Same or adjacent vertical (SaaS, e-commerce, health, media, B2B, nonprofit, etc.) |
| **ICP alignment** | Tone and voice matches the brand's target persona (founder story for mission-driven; data-forward for B2B; playful for consumer) |
| **Funnel goal match** | Does this example drive the same action the brand needs? (activation, purchase, exploration, subscription) |
| **Copy technique relevance** | "So you can" benefit structure, noticing effect, identity framing, specificity — pick what fits |
| **2025 trend alignment** | Emotional orientation over feature dump, identity-first, delayed feature explanation, loss aversion balanced with aspiration |

**Reference pool to draw from (pre-researched as of 2025):**

*Award winners:*
- **Claude** (Best Welcome Email 2025) — animated GIF showing product, use case bullets, "Start your first chat" CTA, multi-touch series, warm + clear value prop
- **FlavCity** (Welcome HM) — live text + graphics + subtle animations, "Better Choices Start Here"
- **Monday** (Welcome HM) — "so you can" copywriting, emphasizes reader benefits over product features
- **Attentive** (Best Thank You) — sneak peek of subscription value, menu-style resource links ranked by popularity, numerical specificity ("42 SMS and email ideas")
- **Apple** (Best Win-Back) — two-part messaging (loss aversion subject / aspirational body), positions offer as gift not pitch, elegant simplicity
- **Charity: Water** (Best Nonprofit) — typography as design, congratulates reader for participation, frames them as valued partner not transaction
- **Lush** (Best Retention) — visceral product imagery, bold CTA, diverse representation, localized

*Welcome category standouts:*
- **Figma** — educational feature introduction, collaborative design platform, B2B/SaaS
- **DoorDash** — celebratory welcome + immediate discount, "Hey, you made it 🥂", incentive-driven activation
- **Dense Discovery** — editorial voice, mission-driven, "finding signal in the noise", newsletter/media
- **Youth Crews** — founder's personal story, emotional connection, mission alignment, health/e-commerce
- **Lyka** — community language ("welcome to the pack"), step-by-step onboarding, pet/subscription
- **Lifesum** — "Tracking that fits real life", realistic benefit messaging, fitness/health app
- **Shutterstock** — professional B2B welcome, platform exploration, creative services
- **Sydney Opera House** — "You've joined at an exciting time", event-forward, arts/culture
- **Netflix** — direct activation focus, clear next step, entertainment/streaming
- **MoMA** — institutional authority, cultural value, nonprofit/arts

*2025 design and copy trends to apply:*
- Welcome emails as **emotional orientation**, not feature catalogues
- Identity-focused framing: "You're in", "Welcome to the family", "You're one of us now"
- **Delayed feature explanation** — lead with feeling, then show what's possible
- **"So you can" structure** — benefit clarity without jargon
- **Specificity over vague promises** — "42 ideas", "15% off your first order", not "great things ahead"
- **One idea per viewport** — controlled hierarchy, white space, calm typography
- Live text over image-only layouts for accessibility and dark mode

Select the **top 5** examples. For each one, output:
- Brand name + email title/subject
- Why it's relevant to this specific brand
- The precise tactic or copy element worth borrowing

## Step 4 — Write the Welcome Series

Using the 5 selected examples as creative reference, write a **complete 3-email welcome series** for the brand. Default to 3 emails unless the user specifies otherwise.

### Series Architecture

| Email | Timing | Purpose |
|-------|--------|---------|
| Email 1 | Immediately on signup | Emotional orientation — make them feel they made the right call |
| Email 2 | Day 2–3 | Value delivery — show the one thing that will matter most to them |
| Email 3 | Day 5–7 | Activation nudge — drive the first meaningful action or conversion |

---

### Email Output Format (repeat for each email in the series)

```
═══════════════════════════════════════
EMAIL [N] — [Purpose label]
Send timing: [e.g., Immediately / Day 3 / Day 7]
═══════════════════════════════════════

SUBJECT LINE OPTIONS (3 variants):
1. [Identity/belonging angle]
2. [Benefit/value angle]
3. [Curiosity/specificity angle]

PREVIEW TEXT:
[One line that complements the subject — not a repeat]

---

BODY:

[Opening hook — 1–2 sentences that create an emotional orientation.
Mirror where the reader is right now, not where the brand wants to push them.]

[Core message — the one thing this email needs to say.
Use "so you can" structure where possible. Be specific, not vague.]

[Proof or reassurance — one stat, one customer outcome, one social proof beat.
Keep it tight — 1–2 sentences max.]

[CTA — one primary action. Short button copy: 2–4 words max.]

[Optional P.S. — a secondary resource, a human moment, or a forward-look
to Email 2 to build anticipation.]
```

### Voice Rules
- Match the brand voice adjectives from the brand brief exactly.
- Apply the 2025 "noticing effect" where possible: mirror the reader's internal state before making claims.
- Avoid: generic "welcome aboard" platitudes, feature dumps, or vague "exciting things ahead" language.
- Prefer: specificity, identity framing, one clear idea per email.
- Never add urgency tactics (scarcity, countdown) to Email 1 — trust comes first.

## Step 5 — Show the Inspiration Chain

After delivering the series, output a brief **Inspiration Map**:

```
INSPIRATION MAP
───────────────
Email 1 borrowed: [Brand] — [specific tactic]
Email 2 borrowed: [Brand] — [specific tactic]
Email 3 borrowed: [Brand] — [specific tactic]

2025 trends applied:
- [Trend name]: [how it showed up in the copy]
- [Trend name]: [how it showed up in the copy]
```

This lets the user understand *why* the series is structured the way it is — not just what was written.

## Step 6 — Offer Variants and Extensions

After delivering the series and inspiration map, offer:

1. **A 5-email extended series** — adds a Day 10 social proof email and a Day 14 activation checkpoint
2. **Subject line A/B tests** — 2 additional variants per email for split testing
3. **Plain-text versions** — stripped-down copy for deliverability-first senders
4. **Humanic-ready format** — structure the series as campaign steps ready to paste into Humanic AI, with cohort suggestions and trigger logic

## Key Rules

- Always fetch live from all three reallygoodemails.com sources — do not rely solely on the pre-researched pool above. The pool is a fallback and starting reference only.
- Always show which real-world examples influenced the output (the Inspiration Map is mandatory).
- Never generate Email 1 with hard-sell copy — welcome series trust is built before conversion is asked for.
- If no brand brief is loaded, collect minimum viable context before proceeding: product name, one-sentence description of who signs up, desired first action, and brand tone.
- For SaaS or app products: default to activation-focused series (account setup → key feature → first win).
- For e-commerce: default to brand story → bestsellers → first purchase incentive.
- For media/newsletter: default to editor voice → what to expect → community invitation.
