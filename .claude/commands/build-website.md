# Build Website — Complete Prompt

## Preparation
1. Ensure `config/PROJECT_CONFIG.yaml` is filled
2. Ensure `docs/brief/` files are filled (company-info, brand-constraints, product-descriptions)
3. Ensure all skills are installed in `~/.claude/skills/`

## Step-by-Step Execution

### Step 1: Reference Analysis (optional)
```
Activate reference-analyzer skill and analyze the reference URL from PROJECT_CONFIG.yaml. Save to docs/brief/reference-analysis.md.
```

### Step 2: Marketing Research
```
Activate core-orchestrator skill. Read all brief files and config. Run marketing research. Save to output/02-research/.
```

### Step 3: Create Briefs
```
Activate core-orchestrator. Create output/01-brief/DESIGN-BRIEF.md and output/01-brief/TECH-SPEC.md based on PROJECT_CONFIG.yaml, briefs, and research.
```

### Step 4: Parallel Copy + Design
```
Activate core-copywriter. Write all block copy per DESIGN-BRIEF.md. Save to output/02-copy/{page-id}/{block-id}.md
```

```
Activate core-designer. Create all block design descriptions per DESIGN-BRIEF.md. Save to output/03-design/{page-id}/{block-id}-design.md
```

### Step 5: Verification
```
Activate core-orchestrator. Verify all pages and blocks are covered. Check tone, terminology, CTA consistency, anti-generic guardrails. Send back for corrections if needed.
```

### Step 6: Build Frontend
```
Read TECH-SPEC.md and all copy/design files. Build the complete website in src/. Rules:
- Multi-page: each page is a directory with index.html
- All internal links use trailing slashes: /about/, /cases/
- sitemap.xml and robots.txt in src/ root
- HTML5 + Tailwind CSS (custom config, NO default primary colors) + vanilla JS
- No forms if constraints.no_forms: true
- Responsive, accessible, SEO-structured
```

### Step 7: QA Testing
```
Activate core-tester. Run full QA audit. Save report to output/06-reports/qa-report.md. Fix critical issues.
```

### Step 8: SEO/GEO Audit
```
Activate core-seo-geo. Audit the built site. Save report to output/06-reports/seo-geo-audit.md. Fix issues.
```

### Step 9: Final Report
```
Activate core-orchestrator. Create FINAL-REPORT.md with status summary, links, A/B hypotheses, unvalidated hypotheses, post-launch metrics.
```

## Critical Rules
- Do NOT add pages/blocks not in PROJECT_CONFIG.yaml
- Do NOT use contact forms if constraints.no_forms: true
- Do NOT use default Tailwind colors (indigo, blue, slate) as primary
- Do NOT use transition-all in CSS
- ALL clickable elements must have hover, focus-visible, active states
- Respect prefers-reduced-motion
- Animate ONLY transform and opacity
- All internal links MUST use trailing slashes
