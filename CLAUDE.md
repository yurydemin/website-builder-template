# Website Builder Template — Global Context

## Project Type
This is a website builder template for creating landing pages and corporate websites using Claude Code multi-agent pipeline.

## Supported Site Types
- `landing`: single-page, conversion-focused
- `corporate`: multi-page, trust and information
- `product`: hybrid, product-focused landing + deep pages

## Pipeline Overview
1. Reference Analysis (optional, auto/manual)
2. Marketing Research
3. Brief Creation (Design Brief + Tech Spec)
4. Parallel Copywriting + Design
5. Verification
6. Frontend Build
7. QA Testing
8. SEO/GEO Audit
9. Final Report

## Technical Constraints
- Static sites only: HTML5 + Tailwind CSS + vanilla JS
- No React/Vue/Next.js for simple sites
- Multi-page: each page is a directory with index.html
- URLs must use trailing slashes: `/about/`, not `/about` or `/about.html`
- sitemap.xml and robots.txt live in src/ (deployment root)
- Forms: currently disabled (static contacts only). See docs/backlog/
- i18n: currently disabled. See docs/backlog/

## Quality Standards
- Lighthouse Performance > 90
- Lighthouse Accessibility > 95
- Lighthouse Best Practices > 95
- Lighthouse SEO > 95
- WCAG 2.1 AA compliance
- Core Web Vitals: LCP < 2.5s, CLS < 0.1
