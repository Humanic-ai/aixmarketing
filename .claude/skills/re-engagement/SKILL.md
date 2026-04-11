---
name: re-engagement
description: This skill should be used when the user asks to "write a re-engagement email", "win back inactive users", "re-activate lapsed customers", "bring back subscribers who went quiet", "re-engagement campaign", "win-back sequence", or wants to generate a re-engagement email series for a company. It fetches live examples from reallygoodemails.com/categories/engagement, selects the top 5 most relevant to the brand voice and ICP, and builds a complete re-engagement campaign.
version: 1.0.0
disable-model-invocation: false
---

# Re-Engagement Campaign Skill

Generate a high-converting re-engagement campaign grounded in the best real-world examples from Really Good Emails, matched precisely to the brand in session — so lapsed users feel seen, not spammed.

## Step 1 — Load Brand Context

Check if a brand brief is already in session context.
- If yes: note the company name, ICP, product category, brand voice adjectives, key differentiators, and any known reason users go quiet (complexity, price, competitor, life change, etc.).
- If no: ask the user to run `/brand-brief` first, or collect minimum viable context:
  - Product/service name and one-line description
  - Who the lapsed user is (persona: role, company size, original goal)
  - How long they've been inactive (30 days / 60 days / 90+ days)
  - Brand tone (warm / bold / playful / professional / empathetic)
  - What action the campaign should drive (return to app, repurchase, resubscribe, complete profile)

Also ask (or infer from brand brief):
- Is there an incentive available? (discount, free feature, bonus content)
- Is this B2C or B2B? (shapes urgency and tone significantly)

## Step 2 — Fetch Live Re-Engagement Examples

Use the WebFetch tool to retrieve current examples from:

**URL:** `https://reallygoodemails.com/categories/engagement`

> Prompt: "List every email example on this page. For each extract: brand name, subject line or title, product category/industry, opening hook, re-engagement tactic used (behavioral data recap, feature education, curiosity teaser, guilt-free check-in, exclusive access, seasonal relevance, social proof, impact visualization), CTA, personalization techniques, tone and voice, and what makes it an effective re-engagement email."

## Step 3 — Select the Top 5 Most Relevant Examples

From the fetched list, score each example against the brand context on these criteria:

| Criteria | What to look for |
|----------|-----------------|
| **Industry / category match** | Same or adjacent vertical (SaaS, e-commerce, media, nonprofit, B2B, wellness, etc.) |
| **ICP alignment** | Does the tone and tactic match the lapsed user's persona and original motivation? |
| **Re-engagement tactic fit** | Does the tactic suit the brand? (Data recaps for analytics tools; lifestyle for consumer; exclusivity for premium brands) |
| **Brand voice match** | Do the copy style, humor level, and formality align with the brand's voice adjectives? |
| **Funnel / action alignment** | Does this example drive the same action the brand needs? (return to app, repurchase, resubscribe) |

**Reference pool to draw from (pre-researched as of 2025):**

| Brand | Industry | Tactic | Best for borrowing |
|-------|----------|--------|--------------------|
| **Resy** | Dining/App | Personalized behavioral recap ("Your 2025 Resy Recap") | Apps with usage data, loyalty programs |
| **LinkedIn** | B2B/Social | Quantified social proof ("your posts got 60,175 views") | SaaS, productivity tools, creator platforms |
| **HeyGen** | SaaS/AI | Skill-gap + webinar ("Most people use Video Agent wrong") | SaaS, complex tools, onboarding-heavy products |
| **Typeform** | SaaS | Feature education ("Did you know you could do this?") | SaaS tools with underused features |
| **Hatch** | SaaS | Exclusive beta access announcement | Product-led growth, innovation-forward brands |
| **Change.org** | Nonprofit | Impact visualization ("see the change you created") | Nonprofits, community platforms, cause brands |
| **Cleo** | Fintech | Sassy brand voice re-engagement | Consumer apps with strong brand personality |
| **Fratelli Burgio** | Food/E-comm | Guilt-free "tell us about yourself" re-activation | E-commerce, subscription, preference-based products |
| **Lush** | Beauty | Values-aligned social impact content | Mission-driven brands, B2C with community focus |
| **Turo** | Travel | Lifestyle reframe, seasonal timing | Travel, experience, lifestyle consumer brands |
| **De La Calle** | Beverage | Curiosity-driven product teaser, minimal text | DTC, visually-forward brands, product launches |
| **AllTrails** | Outdoors | Curated seasonal content, location-based | Subscription apps, content platforms, hobbyist communities |
| **Ka'chava** | Wellness | Ingredient education with health focus | Health, wellness, food, supplement brands |
| **GoFundMe** | Nonprofit | Platform updates with mission reinforcement | Nonprofits, community platforms, cause-adjacent SaaS |
| **Brooklyn Museum** | Arts/Events | Urgency through limited availability | Events, ticketing, cultural institutions |
| **Employ** | B2B/HR | Demo request with benefit-led copy | B2B SaaS, enterprise tools |

Select the **top 5** examples. For each one, output:
- Brand name + subject line
- Why it's relevant to this specific brand and its lapsed users
- The precise tactic or copy element worth borrowing

## Step 4 — Write the Re-Engagement Campaign

Using the 5 selected examples as creative reference, write a **complete 3-email re-engagement sequence**.

### Campaign Architecture

| Email | Timing | Purpose | Tone |
|-------|--------|---------|------|
| Email 1 | Day 0 (trigger: X days inactive) | Soft check-in — acknowledge absence without guilt, restate value | Warm, curious, no pressure |
| Email 2 | Day 4–5 | Value reminder — show what they're missing, surface the one feature or benefit most relevant to them | Helpful, specific, slightly urgent |
| Email 3 | Day 8–10 | Final nudge — clearest ask, strongest incentive if available, honest "last email" framing | Direct, respectful, door-open close |

---

### Email Output Format (repeat for each email in the sequence)

```
═══════════════════════════════════════
EMAIL [N] — [Purpose label]
Trigger / Send timing: [e.g., 30 days inactive / Day 4 after Email 1]
═══════════════════════════════════════

SUBJECT LINE OPTIONS (3 variants):
1. [Soft / curiosity angle — no pressure]
2. [Value / benefit angle — what they're missing]
3. [Direct / honest angle — acknowledge the gap]

PREVIEW TEXT:
[One line that adds context or intrigue — not a repeat of the subject]

---

BODY:

[Opening hook — 1–2 sentences.
Acknowledge where the user is (not where the brand wants them to be).
Mirror their likely state: busy, overwhelmed, moved on — without guilt.]

[Core message — the single most compelling reason to come back.
For Email 1: restate the original value promise.
For Email 2: highlight one specific feature, outcome, or piece of content they haven't seen.
For Email 3: make the clearest possible ask with the strongest available incentive.]

[Proof or reassurance — one specific beat showing others like them returned and won.
A stat, a customer quote, a concrete outcome. 1–2 sentences max.]

[CTA — one primary action. Short, action-first button copy: 2–4 words.]

[P.S. — optional.
Email 1: forward-look ("we'll share [X] in a few days").
Email 2: secondary resource or social proof link.
Email 3: honest close ("if this isn't the right time, no hard feelings — you can [pause / unsubscribe / come back when ready]").]
```

### Voice Rules
- Match the brand voice adjectives from the brand brief exactly.
- Email 1 must never feel like a complaint about absence — open the door, don't guilt-trip.
- Email 3 must include an honest "door-open" close — give the user a graceful exit or pause option. This protects list health and brand trust.
- Avoid: "We miss you!" clichés unless the brand is explicitly warm/playful and it fits voice.
- Prefer: specific value reminders, behavioral acknowledgment, and one clear ask per email.
- For B2B: lead with outcomes and ROI — not emotion.
- For B2C: lead with feeling and identity — then product.

## Step 5 — Show the Inspiration Chain

After delivering the campaign, output a mandatory **Inspiration Map**:

```
INSPIRATION MAP
───────────────
Email 1 borrowed: [Brand] — [specific tactic and why]
Email 2 borrowed: [Brand] — [specific tactic and why]
Email 3 borrowed: [Brand] — [specific tactic and why]

Re-engagement patterns applied:
- [Pattern name]: [how it appeared in the copy]
- [Pattern name]: [how it appeared in the copy]

Tactic avoided (and why):
- [e.g., "Guilt-trip opener — brand voice is empathetic, not pushy"]
```

## Step 6 — Offer Variants and Extensions

After delivering the campaign and Inspiration Map, offer:

1. **Sunset extension** — a 4th "final farewell" email for users who didn't respond to all 3, with unsubscribe/pause framing to clean the list
2. **Subject line A/B tests** — 2 additional subject variants per email for split testing
3. **SMS companion messages** — 1 short text per email for multichannel re-engagement
4. **Humanic-ready format** — structure as campaign steps ready to paste into Humanic AI, with cohort definition (e.g., "contacts with no activity in 30+ days") and trigger logic

## Key Rules

- Always fetch live from `reallygoodemails.com/categories/engagement` — the pre-researched pool above is a fallback and starting reference, not a substitute for live fetch.
- Always show the Inspiration Map — never deliver copy without attribution to source examples.
- Email 1 tone must be warm and pressure-free. Never open a re-engagement sequence with urgency or a hard sell.
- Email 3 must always include a graceful exit option — list health matters as much as re-activation rate.
- If no incentive is available, lean harder on value reminders, social proof, and behavioral data.
- If the brand has usage/behavioral data on the lapsed user (last login, last purchase, last content viewed), surface it — personalized recaps dramatically outperform generic re-engagement.
- Never fabricate urgency (e.g., "your account will be deleted") unless the brand actually implements this.
