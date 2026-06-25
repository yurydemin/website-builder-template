---
name: core-tester
description: QA testing for websites. Activate when testing, auditing, or reviewing any website for quality, performance, or compliance.
---

## Context
Website built from template. Check `config/PROJECT_CONFIG.yaml` for constraints (forms enabled/disabled, page list).

## Test Matrix

### Browsers
- Chrome (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)
- Edge (last 2 versions)

### Devices
- Mobile: iOS Safari, Chrome Android
- Tablet: iPad Safari
- Desktop: 1920x1080, 1440x900, 1366x768

### Viewports
- 320px (small mobile)
- 768px (tablet)
- 1024px (small desktop)
- 1440px (desktop)
- 1920px (large desktop)

## Checklist

### Functional
- [ ] All navigation links work
- [ ] All CTA buttons clickable
- [ ] No broken internal links
- [ ] Internal links use trailing slashes (`/about/`, not `/about` or `/about.html`)
- [ ] No contact forms if `constraints.no_forms: true`
- [ ] Contact info is accurate and visible
- [ ] Smooth scroll to anchors works (landing)
- [ ] Mobile menu toggle works
- [ ] All hover/focus/active states present
- [ ] mailto: and tel: links work

### Visual
- [ ] No layout shifts on load
- [ ] Images load correctly with overlays
- [ ] Typography renders correctly (no FOUT)
- [ ] Colors match design system
- [ ] Shadows are layered, not flat
- [ ] Animations respect prefers-reduced-motion
- [ ] No horizontal scroll on any viewport

### Performance
- [ ] Lighthouse Performance > 90
- [ ] Lighthouse Accessibility > 95
- [ ] Lighthouse Best Practices > 95
- [ ] Lighthouse SEO > 95
- [ ] LCP < 2.5s
- [ ] CLS < 0.1
- [ ] FID < 100ms
- [ ] Total blocking time < 200ms

### SEO/GEO
- [ ] Title tag present and under 60 chars
- [ ] Meta description present and under 155 chars
- [ ] OG tags present
- [ ] Canonical URL set
- [ ] Structured data: Organization schema
- [ ] H1 present, only one per page
- [ ] Heading hierarchy correct (no skips)
- [ ] Alt text on all images
- [ ] sitemap.xml present in root
- [ ] robots.txt present in root
- [ ] Internal links use descriptive anchor text
- [ ] GEO: content is citable (lists, definitions, statistics)

### Accessibility
- [ ] WCAG 2.1 AA compliance
- [ ] Keyboard navigation works
- [ ] Focus indicators visible
- [ ] Color contrast > 4.5:1 for text
- [ ] Color contrast > 3:1 for UI components
- [ ] Screen reader labels on interactive elements
- [ ] No auto-playing media

### Multi-page (if applicable)
- [ ] Each page accessible by URL with trailing slash
- [ ] Navigation links to all pages
- [ ] Consistent header/footer across pages
- [ ] Correct canonical URLs per page

## Output
Save report as `output/06-reports/qa-report.md`
Include:
- Summary (pass/fail per category)
- Critical issues table (issue, severity, location, fix)
- Performance metrics table
- Screenshots list (if applicable)
