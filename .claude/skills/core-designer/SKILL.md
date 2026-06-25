---
name: core-designer
description: Create design system and block-level design descriptions. Activate when designing, styling, or creating visual concepts for any website.
---

## Pre-flight
1. Read `output/01-brief/DESIGN-BRIEF.md`
2. Read `output/02-copy/` — all block copy must be incorporated
3. Read `docs/brief/reference-analysis.md` — match patterns if exists
4. Read `docs/brief/brand-constraints.md` — respect brand colors and assets
5. Read `config/PROJECT_CONFIG.yaml` — project type and constraints

## Anti-Generic Guardrails (MUST ENFORCE)

### Colors
- NEVER use default Tailwind palette (indigo-500, blue-600, slate-900, etc.)
- Pick custom brand color and derive full palette (50-950 scale)
- Use CSS variables: --color-primary, --color-secondary, --color-accent, --color-surface, --color-text
- Dark theme preferred for hero, light for content sections

### Shadows
- NEVER use flat shadow-md or shadow-lg
- Use layered, color-tinted shadows with low opacity
- Example: `0 4px 6px -1px rgba(brand, 0.1), 0 2px 4px -1px rgba(brand, 0.06)`

### Typography
- NEVER use the same font for headings and body
- Pair a display/serif font with a clean sans-serif
- Headings: tight tracking (-0.03em), large sizes (clamp for fluid)
- Body: generous line-height (1.7), readable measure (max 65ch)
- Font loading: font-display: swap

### Gradients
- Layer multiple radial gradients for depth
- Add grain/texture via SVG noise filter for background depth
- Avoid linear gradients from top to bottom only

### Animations
- ONLY animate transform and opacity
- NEVER use transition-all
- Use spring-style easing: cubic-bezier(0.34, 1.56, 0.64, 1)
- Respect prefers-reduced-motion

### Interactive States
- EVERY clickable element needs hover, focus-visible, and active states
- No exceptions
- Focus-visible: 2px outline with offset

### Images
- Add gradient overlay: bg-gradient-to-t from-black/60
- Add color treatment layer with mix-blend-multiply
- Use object-fit: cover, aspect-ratio for consistency

### Spacing
- Use intentional, consistent spacing tokens
- Base: 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px, 96px, 128px
- Section padding: min 96px vertical
- Container max-width: 1280px with responsive padding

### Depth
- Surfaces must have layering system:
  - Base (z-0): background
  - Elevated (z-10): cards, buttons
  - Floating (z-20): modals, dropdowns, sticky nav

## Block Library — Design Specifications

### hero
- Layout: full viewport height, centered or split
- Elements: headline, subheadline, primary CTA, secondary CTA, optional visual
- Color: dark background preferred, light text
- Animation: fade-up on load, staggered elements

### text_center
- Layout: centered, max-width 65ch
- Elements: heading, paragraphs, optional bullets
- Spacing: generous vertical padding

### text_two_column
- Layout: 50/50 grid desktop, stacked mobile
- Elements: text left, visual/stats right (or vice versa)
- Asymmetry: slight offset or overlapping elements allowed

### steps_horizontal
- Layout: horizontal row desktop, vertical stack mobile
- Elements: number/icon, title, description per step
- Connection: line or arrow between steps

### steps_vertical
- Layout: vertical timeline, left-aligned or centered
- Elements: number/icon, title, description per step
- Connection: vertical line

### cards_grid
- Layout: 2-4 columns, equal height, responsive to 1 column
- Elements: image/icon, title, bullets, optional link
- Hover: lift effect (translateY + shadow increase)
- Equal height: use flex or grid auto-rows

### icon_grid
- Layout: 3-6 columns, centered icons
- Elements: icon, label, 1-line context
- Grouping: category headers if >6 items

### contacts_static
- Layout: centered, minimal
- Elements: heading, email, phone, telegram links
- Links: mailto:, tel:, external Telegram URL
- NO form elements

### contacts_form
- [BACKLOG — не используется пока]

### footer
- Layout: full width, minimal height
- Elements: copyright, links, legal
- Color: muted, low contrast

### navigation
- Layout: fixed top, full width, blur backdrop
- Elements: logo, page links, CTA button
- Mobile: hamburger, slide-out menu
- Links: trailing slashes `/about/`
- z-index: 20 (floating layer)

### pricing_table
- [BACKLOG — не используется пока]

### testimonials
- Layout: 1-3 columns, or carousel (CSS-only)
- Elements: quote text, author name, role, avatar
- Style: card with subtle border or shadow

## Output Format
For each block, create `output/03-design/{page-id}/{block-id}-design.md`:
- Layout description (grid/flex, asymmetry, responsive)
- Color application (tokens, where)
- Typography scale (sizes, weights, line-heights)
- Animation spec (trigger, duration, easing, properties)
- Responsive behavior (mobile < 768px, tablet 768-1024px, desktop > 1024px)
- Asset requirements (images, icons, dimensions)

## Hard Rules
- Do NOT add sections not in DESIGN-BRIEF.md or PROJECT_CONFIG.yaml
- Do NOT "improve" reference design — match it
- Do NOT stop after one pass — iterate
- Do NOT use transition-all anywhere
- Do NOT use default Tailwind blue/indigo as primary color
- No form elements if `constraints.no_forms: true`
