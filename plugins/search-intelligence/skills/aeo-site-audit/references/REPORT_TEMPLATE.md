# Report Structure Guide — AEO Site Audit

This document describes the structure of the markdown report. It is NOT a fill-in template. Use it as instructions for generating the report from audit data.

---

## Report Sections (in order)

### 1. Executive Summary

Write this section LAST after all other sections are complete.

Include:
- Domain audited and audit date
- D1 Technical Infrastructure score (/100) with one-line assessment
- D2 Citation Readiness site average (/31) with assessment label
- Number of pages audited
- Critical blockers (if any) — call these out prominently
- Top 3 findings across both dimensions
- Single most impactful recommended action
- Partial composite score with note about D3/D4

Length: 150-250 words. No filler. Lead with the most important finding.

### 2. D1: Technical Infrastructure Findings

#### 2.1 Crawler Access

Present as a pass/fail table:

| Bot | Status | Notes |
|-----|--------|-------|
| GPTBot | Pass/Fail/Not Mentioned | ... |
| ClaudeBot | Pass/Fail/Not Mentioned | ... |
| ... | ... | ... |

If any critical bot is blocked, add a prominent callout:
> **CRITICAL BLOCKER**: [Bot] is blocked in robots.txt. This must be fixed before any content optimization will have impact. 73% of sites unknowingly block AI crawlers.

#### 2.2 Schema Markup

- List schema types found with the pages they appear on
- Note missing high-impact schema types (FAQPage, Article, HowTo)
- Score: X/10

#### 2.3 Semantic HTML

- List semantic elements found and missing
- Note anti-patterns detected (JS-rendered content, hidden tabs, etc.)
- Score: X/10

#### 2.4 Performance

- HTTPS status
- Mobile viewport status
- Page speed: note limitation, link to PageSpeed Insights

#### 2.5 Supplementary

- llms.txt: present/absent with brief note
- Sitemap: present/absent with URL count

#### 2.6 D1 Score Summary

Present the final D1 score with breakdown:
- Critical gate: PASS/FAIL (if fail, note the cap at 40)
- Schema: X/15
- Semantic HTML: X/15
- Performance items: X/15
- Heading hierarchy: X/5
- Critical pass bonus: 40/40 or 0/40
- Supplementary: X/5
- **Total: X/100**

#### 2.7 D1 Recommendations

Prioritized list. Critical items first, then high, then medium, then low. Each recommendation should be specific and actionable:
- BAD: "Improve your schema markup"
- GOOD: "Add FAQPage schema to /what-is-crm/ and /guide/email-marketing/ — these Q&A-structured pages are the highest-impact candidates"

### 3. D2: Citation Readiness Findings

#### 3.1 Site-Wide Summary

- Site average score: X/31
- Assessment: Publish Ready / Revise / Rework / Restructure
- Distribution of page scores (how many in each assessment band)
- Weakest sections across all pages (identify patterns)
- Strongest sections across all pages

#### 3.2 Per-Page Scorecards

For each audited page, include a scorecard:

**[Page Title] — {url}**
Page type: {type} | Score: X/31 | Assessment: {assessment}

| Section | Score | Max | Key Gaps |
|---------|-------|-----|----------|
| A: Opening Structure | X | 5 | ... |
| B: Topical Completeness | X | 6 | ... |
| C: Entity & Authority | X | 5 | ... |
| D: Technical Accessibility | X | 6 | ... |
| E: Content Formatting | X | 5 | ... |
| F: Distribution & Monitoring | X | 4 | ... |

Top recommendations for this page:
1. ...
2. ...
3. ...

#### 3.3 Top D2 Recommendations

Cross-page patterns and the highest-impact improvements. Group by:
1. Quick wins (easy to implement, high impact)
2. Content restructuring (moderate effort, high impact)
3. Authority building (ongoing effort, compounds over time)

### 4. SEO Baseline

- Approximate indexed pages
- Brand query presence
- Notable observations
- Limitation disclaimer: "This is a directional check. Use dedicated SEO tools for comprehensive analysis."
- Context: "81.1% of AI Overview citations come from top-10 organic results. Strong SEO is a prerequisite for Google AI Overview citations."

### 5. Priority Action Plan

Customized to the site's specific gaps. Follow the Tier 1-4 structure from the Action Priority Matrix (KB Section 12) but tailor items to the audit findings.

**Tier 1 — Immediate (Week 1-2)**:
- List only items relevant to this site's gaps
- Include specific pages/URLs where applicable

**Tier 2 — Foundation (Week 3-4)**:
- ...

**Tier 3 — Optimization (Month 2)**:
- ...

**Tier 4 — Expansion (Month 3+)**:
- ...

If industry was provided, include traffic impact context from KB Section 11:
> "In the {industry} sector, AI Overviews are driving a {X}% traffic impact. Addressing these items is particularly urgent."

### 6. Appendix: Methodology

Include:
- Framework: Four-Dimension AEO/GEO Measurement Framework (D1 + D2)
- D1 scoring model: critical gates, proportional scoring, bonus items
- D2 scoring model: 31-point citation readiness checklist
- Composite weights: D1 = 20%, D2 = 30%, D3 = 25% (not measured), D4 = 25% (not measured)
- Tools used: WebFetch for page analysis, WebSearch for SEO baseline
- Limitations: page speed not directly measured, JS rendering check limited to HTML inspection, SEO baseline is directional only
- KB version used
- Cross-reference: "For D3 (Authority & Distribution), run the authority-distribution-audit skill. For D4 (AI Visibility), run the ai-visibility-monitor skill."

---

## Formatting Rules

- Use active voice throughout
- Lead each section with the most important finding
- No "delve", no filler transitions
- Numbers as digits
- Spell out acronyms on first use: Answer Engine Optimization (AEO)
- Short paragraphs (2-4 sentences max)
- Tables for structured data
- Blockquotes for critical callouts
- Code blocks for technical recommendations (robots.txt entries, schema examples)
