---
name: reference-analyzer
description: Analyze reference websites for design patterns, structure, and content. Activate when user provides reference URLs or asks to analyze competitor websites. Supports multiple sources with different types and focus areas.
---

## Purpose
Extract design patterns, structure, typography, colors, and layout from one or more reference websites to inform the DESIGN-BRIEF.md. Supports multiple sources with different roles (primary, secondary, competitor) and focus areas.

## Input
Read `config/PROJECT_CONFIG.yaml`, section `reference.sources`.

## Three-Level Strategy (per source)

### Level 1: MCP Fetch (HIGH confidence)
If MCP server (Fetch, Firecrawl, Apify) is available:
1. Scrape target URL — get HTML, CSS, computed styles
2. Extract: DOM structure, CSS variables, font sizes, colors, spacing
3. Take screenshots if MCP supports it
4. Generate full structured analysis for this source

### Level 2: Web Analysis (MEDIUM confidence)
If no MCP but web_search or web_open_url is available:
1. Search for site description and reviews
2. Open URL if possible — read visible text content
3. Extract: visible sections, headings, CTA texts, general color scheme (dark/light), approximate layout
4. Generate draft analysis with [APPROXIMATE] markers

### Level 3: Manual Template (LOW confidence)
If no tools available:
1. Output structured template for user to fill
2. Include all required fields with examples
3. User completes manually

## Multi-Source Processing

### Step 1: Process each source independently
For each source in `reference.sources`:
- Detect available tools (MCP → Web → Manual)
- Run analysis at appropriate confidence level
- Save intermediate result with source metadata (url, type, focus, confidence)

### Step 2: Merge into unified report
Create `docs/brief/reference-analysis.md` with sections:

```markdown
# Reference Analysis

## Summary
| Source | URL | Type | Focus | Confidence |
|--------|-----|------|-------|------------|
| ... | ... | ... | ... | ... |

### Primary References (structure source)
[Merged analysis from all primary sources]
- Site structure (page list, block order)
- Layout patterns (container, grid, spacing)
- Navigation patterns
- Primary wins in case of conflict

### Secondary References (design details)
[Merged analysis from all secondary sources]
- Color palette (with HEX if available, or descriptions)
- Typography (fonts, sizes, weights)
- Animations and transitions
- Interactive states (hover, focus, active)
- Shadows, gradients, textures
- Spacing tokens

### Competitor References (content & positioning)
[Merged analysis from all competitor sources]
- Headline formulas and patterns
- CTA formulations
- Tone of voice
- Value proposition structures
- Block types used (what they show, what they hide)
- Differentiation opportunities (gaps to fill)

### What to Copy (from all sources)
1. [Element from primary/secondary]
2. [Element from primary/secondary]

### What to Improve (gaps found)
1. [Gap: competitors don't do X, we can]
2. [Gap: primary has weak Y, secondary has strong Y]

### Anti-Patterns to Avoid
- [What NOT to copy from any source]
- [Overused patterns across competitors]
```

### Step 3: Conflict Resolution
If sources contradict each other:
- **Structure conflict** (e.g., primary has 5 steps, secondary has 3) → Primary wins
- **Design conflict** (e.g., primary dark, secondary light) → Primary wins unless user notes override
- **Content conflict** (e.g., competitor uses jargon, primary is plain) → User notes win, then primary
- Mark all conflicts with `[CONFLICT: resolved by primary]` or `[CONFLICT: user notes override]`

### Step 4: Confidence Annotation
Every value in the report must have confidence marker:
- `[HIGH]` — MCP scraping, exact CSS values
- `[MEDIUM]` — web analysis, approximate values
- `[LOW]` — manual/user input, estimated values
- `[CONFLICT]` — resolved conflict between sources

## User Instructions (if any MEDIUM or LOW)
After generating draft, output:
"Reference analysis completed. Confidence levels:
- HIGH: [N] sources
- MEDIUM: [N] sources  
- LOW: [N] sources

Please review and correct:
- Exact colors (HEX codes)
- Typography details (font names, sizes in px/rem)
- Spacing values (padding, margins, gaps)
- Animation descriptions (duration, easing, trigger)
- Layout specifics (grid columns, breakpoints, max-width)"

## Rules
- Do NOT hallucinate specific values (HEX, px) at MEDIUM/LOW confidence
- Mark all approximate values with [APPROXIMATE] or confidence level
- Focus on structural patterns over exact replication
- Note accessibility issues if visible
- Respect user notes in PROJECT_CONFIG.yaml — they override automatic analysis
- Process ALL sources in the list, even if one fails (continue with remaining)
