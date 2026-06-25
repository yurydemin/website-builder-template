---
name: core-copywriter
description: Write conversion copy for website blocks. Activate when creating or editing website copy, headlines, CTAs, or product descriptions.
---

## Context
Read `output/01-brief/DESIGN-BRIEF.md` before writing any copy.
Read `config/PROJECT_CONFIG.yaml` for project type, audience, and constraints.
Read `docs/brief/company-info.md` for company voice.
Read `docs/brief/product-descriptions.md` for product details.

## Copy Framework
Apply in order of priority:
1. **Problem-First**: Start with the client's pain, not your solution.
2. **Outcome-First**: Lead with the measurable result, then explain how.
3. **Feature-First**: Use only for technical audiences (stack section).

## Rules
- Headlines: max 8 words, point-first writing
- Subheadlines: max 14 words, expand the headline promise
- Body paragraphs: 2-3 sentences max, active voice, plain language
- CTA: action verb + benefit + time constraint where possible
- Zero em dashes. Periods and commas only.
- Zero parenthetical asides.
- No marketing fluff. Audience is technical decision makers.
- Tables over prose for structured content.
- Benefits over features. Customer language over company jargon.
- Language: from `config/PROJECT_CONFIG.yaml` (`project.language`)

## Block Library — Copy Specifications

### hero
- One sharp headline (problem or outcome)
- Subheadline (mechanism or differentiation)
- Primary CTA + Secondary CTA
- No more than 40 words total
- SEO: contains H1, only one per page

### text_center
- Heading (max 6 words)
- 1-2 short paragraphs
- Optional: bullet points (3-4 items)

### text_two_column
- Left: heading + text
- Right: image, stats, or extended text
- Use for story/about sections

### steps_horizontal / steps_vertical
- 3-6 steps
- Each: verb-first title (3-4 words) + 1 sentence description
- Progressive narrative: step N follows step N-1

### cards_grid
- Card title + 1-sentence outcome
- 3 bullet benefits (max 6 words each)
- Optional link text
- Use for cases, products, features, team

### icon_grid
- Icon + label + 1-line context
- Group by category
- Use for stack, technologies, services

### contacts_static
- Heading + contact methods (email, phone, telegram)
- Response time promise
- Privacy note
- NO form fields

### contacts_form
- [BACKLOG — не используется пока constraints.no_forms: true]

### footer
- Copyright
- Essential links (privacy, terms if applicable)
- Minimal

### navigation
- Logo + links to pages
- CTA button
- Mobile: hamburger menu
- All links: trailing slashes `/about/`, not `/about`

### pricing_table
- [BACKLOG — не используется пока constraints.no_pricing: false]

### testimonials
- Quote + author + role/company
- Max 2-3 sentences per quote
- Use for social proof

## Output
Save each block as `output/02-copy/{page-id}/{block-id}.md` with frontmatter:
---
page-id: [index|about|cases|...]
block-id: [hero|text_center|...]
word-count: [X]
tone: [professional|technical|trusted]
target: [CTO|CEO|ProductOwner]
---
