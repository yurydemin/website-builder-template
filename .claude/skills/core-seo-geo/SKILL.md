---
name: core-seo-geo
description: SEO and GEO audit for websites. Activate when auditing, optimizing, or reviewing any website for search engine and generative engine optimization.
---

## Context
Static HTML website. Target: B2B decision makers. Check `config/PROJECT_CONFIG.yaml` for geo_target and language.

## SEO Requirements

### Technical
- Title: under 60 characters, include primary keyword + brand
- Meta description: under 155 characters, include CTA
- Canonical URL (per page, with trailing slash for directories)
- OG tags: title, description, image, type, url
- Twitter Card tags
- Favicon (multiple sizes)
- Robots.txt: allow all, sitemap reference
- Sitemap.xml: all pages, lastmod, priority (URLs with trailing slashes)

### Structured Data
- Organization schema (name, url, logo, contactPoint)
- WebSite schema (name, url, potentialAction/SearchAction)
- FAQPage schema (if FAQ section exists)
- SoftwareApplication schema (for products)
- BreadcrumbList (for multi-page)

### Content SEO
- One H1 per page
- H2 for major sections, H3 for subsections
- Internal linking strategy
- Descriptive anchor text
- Image alt text: descriptive, include keywords naturally
- URL structure: clean, descriptive, trailing slashes

### Performance
- Core Web Vitals targets:
  - LCP < 2.5s
  - CLS < 0.1
  - FID < 100ms
- Lazy loading for images below fold
- Preload critical fonts
- Minify CSS/JS

## GEO Requirements (Generative Engine Optimization)

### Citability
- Use structured lists (ul/ol) — AI engines cite lists frequently
- Include definitions and explanations
- Use statistics with sources
- Create comparison tables
- FAQ format with clear questions and concise answers

### E-E-A-T
- Experience: mention years of operation, projects completed
- Expertise: mention technologies, methodologies, certifications
- Authoritativeness: link to case studies, client logos, testimonials
- Trustworthiness: privacy policy, contact info, company details

### Content Structure
- Clear headings with semantic markup
- Short paragraphs (2-3 sentences)
- Bullet points for key benefits
- Summary boxes for complex topics
- Schema markup for all entities

## Output
Save audit as `output/06-reports/seo-geo-audit.md`
Include:
- SEO score (1-100)
- GEO score (1-100)
- Critical issues table
- Content opportunities table
- Structured data validation results
- Action plan (prioritized)
