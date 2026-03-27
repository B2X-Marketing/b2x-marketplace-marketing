# 31-Point Citation Readiness Checklist — Scoring Format

Score each item: 1 = present, 0 = absent. Maximum score: 31.

---

## Section A: Opening Structure (5 points)

| # | Item | Criteria | Score |
|---|------|----------|-------|
| 1 | Direct answer | Opening 1-2 sentences directly answer the page's primary question | 0/1 |
| 2 | Answer block completeness | 30-80 word self-contained answer that works without surrounding context | 0/1 |
| 3 | Primary entity named | Subject (brand, product, concept) explicitly named in opening | 0/1 |
| 4 | Outcome stated | Answer includes what happens / what the reader gets | 0/1 |
| 5 | No preamble | No "In this article..." or "Let's dive into..." before the answer | 0/1 |

**Section A total: ___/5**

---

## Section B: Topical Completeness (6 points)

| # | Item | Criteria | Score |
|---|------|----------|-------|
| 6 | Full question coverage | Page addresses the complete question, not just one angle | 0/1 |
| 7 | Related questions addressed | "People also ask" and follow-up questions covered | 0/1 |
| 8 | Comparison/context | Topic situated relative to alternatives or related concepts | 0/1 |
| 9 | Specific data points | 3+ statistics, percentages, or concrete numbers with sources | 0/1 |
| 10 | Examples included | 2+ concrete, specific examples (not hypothetical) | 0/1 |
| 11 | Actionable takeaways | Reader can act on the information without needing another source | 0/1 |

**Section B total: ___/6**

---

## Section C: Entity & Authority Signals (5 points)

| # | Item | Criteria | Score |
|---|------|----------|-------|
| 12 | Expert byline | Named author with credentials | 0/1 |
| 13 | Author bio present | Brief bio establishing expertise on the topic | 0/1 |
| 14 | Publication date visible | Clear date on the page | 0/1 |
| 15 | Sources cited | External authoritative sources referenced inline | 0/1 |
| 16 | Original contribution | Content contains something not found elsewhere (data, framework, case study) | 0/1 |

**Section C total: ___/5**

---

## Section D: Technical Accessibility (6 points)

| # | Item | Criteria | Score |
|---|------|----------|-------|
| 17 | AI crawler access | robots.txt allows GPTBot, ClaudeBot, PerplexityBot, GoogleOther | 0/1 |
| 18 | Schema markup | Appropriate schema type implemented (FAQ, Article, HowTo, Product) | 0/1 |
| 19 | Semantic HTML | Content uses `<article>`, `<section>`, proper heading hierarchy | 0/1 |
| 20 | Page loads without JS | Core content visible without JavaScript execution | 0/1 |
| 21 | Mobile responsive | Content accessible on all devices (viewport meta tag present) | 0/1 |
| 22 | Page speed | Loads in under 3 seconds (assume pass if not directly measurable, note limitation) | 0/1 |

**Section D total: ___/6**

---

## Section E: Content Formatting (5 points)

| # | Item | Criteria | Score |
|---|------|----------|-------|
| 23 | Heading hierarchy | Proper H1 -> H2 -> H3 nesting, no skipped levels | 0/1 |
| 24 | Headings as questions | H2s mirror how users would ask about the topic | 0/1 |
| 25 | Short paragraphs | 2-4 sentences per paragraph | 0/1 |
| 26 | Reading level | Grade 9-11 (Flesch-Kincaid) | 0/1 |
| 27 | Active voice | 90%+ sentences in active voice | 0/1 |

**Section E total: ___/5**

---

## Section F: Distribution & Monitoring (4 points)

| # | Item | Criteria | Score |
|---|------|----------|-------|
| 28 | Internal links | 3-5 relevant internal links per 1,000 words | 0/1 |
| 29 | External authority links | Links to credible external sources | 0/1 |
| 30 | Meta description | Factual summary (not marketing hook) | 0/1 |
| 31 | Social/distribution presence | Content referenced or shared across other platforms | 0/1 |

**Section F total: ___/4**

---

## Scoring Interpretation

| Total Score | Assessment | Action |
|-------------|-----------|--------|
| 28-31 | Publish Ready | Minor tweaks, then publish |
| 22-27 | Revise | Address gaps in weakest sections |
| 15-21 | Rework | Significant restructuring needed |
| Below 15 | Restructure | Start from scratch with AEO framework |

---

## Notes for Automated Scoring

- Items 17-22 (Technical Accessibility) use site-wide D1 data. Apply the same scores to all pages on the same domain.
- Item 22 (Page speed): If not directly measurable, score as 1 and note the limitation. Recommend PageSpeed Insights for verification.
- Item 31 (Social/distribution presence): Check via WebSearch for the page URL or title. If the page appears on LinkedIn, Reddit, forums, or other platforms, score as 1.
- Item 26 (Reading level): Estimate from paragraph length, sentence structure, and vocabulary. Formal academic writing or extremely simple writing both score 0.
- Item 27 (Active voice): Estimate from sentence patterns. Pages heavy with passive constructions ("was created by", "is used for", "has been shown to") score 0.
