# AEO Site Audit — Knowledge Base Extract

KB Version: 1.1 | KB Last Updated: 2026-03-26

Extracted sections from AEO-GEO-KNOWLEDGE-BASE.md relevant to the aeo-site-audit skill.

---

## 5. Technical AEO Requirements

### 5.1 Crawler Access

**Critical**: 73% of sites unknowingly block AI crawlers.

**robots.txt must allow**:
```
User-agent: GPTBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: GoogleOther
Allow: /

User-agent: Google-Extended
Allow: /

User-agent: Amazonbot
Allow: /

User-agent: anthropic-ai
Allow: /

User-agent: Bytespider
Allow: /

User-agent: cohere-ai
Allow: /
```

**Audit checklist**:
- Verify robots.txt allows all major AI crawlers
- Check that no meta robots tags block AI bots specifically
- Verify content isn't behind JavaScript rendering that crawlers can't execute
- Check that important content isn't gated behind login walls
- Ensure no CDN or WAF rules are blocking bot user agents

### 5.2 llms.txt

A Markdown file at the site root (yoursite.com/llms.txt) that serves your best content to LLMs in a token-efficient format.

**Current status** (March 2026):
- Adoption at 5-15% among tech sites
- Community-driven, not an official standard
- 8 of 9 sites in one study saw no measurable traffic change
- Classify as "nice to have" — implement after higher-priority items

**Format**:
```markdown
# Company Name

> Brief description of what your company does

## Core Pages
- [Product Overview](https://example.com/product): Main product page
- [Pricing](https://example.com/pricing): Pricing plans and features
- [Documentation](https://example.com/docs): Technical documentation

## Blog / Resources
- [Guide to X](https://example.com/blog/guide-x): Comprehensive guide on X topic
```

### 5.3 Schema Markup

Schema.org structured data in JSON-LD format. Proper schema can boost AI summary appearance by 36%.

**Priority order by impact**:

| Schema Type | Impact on AI Citations | When to Use |
|-------------|----------------------|-------------|
| FAQPage | Highest | Any page with Q&A content |
| HowTo | High | Step-by-step guides, tutorials |
| Article | High | Blog posts, news, analysis |
| Product | Medium-High | Product pages, feature pages |
| Organization | Medium | Homepage, about page |
| Person (Author) | Medium | Author pages, bylines |
| BreadcrumbList | Medium | All pages (navigation signal) |
| WebPage | Baseline | All pages |

**FAQPage example** (highest impact):
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [{
    "@type": "Question",
    "name": "What is Answer Engine Optimization?",
    "acceptedAnswer": {
      "@type": "Answer",
      "text": "Answer Engine Optimization (AEO) is the practice of structuring content so AI platforms like ChatGPT, Perplexity, and Google AI Overviews can extract, understand, and cite it when generating answers."
    }
  }]
}
```

### 5.4 Semantic HTML

AI crawlers parse HTML structure for content hierarchy and section boundaries.

**Required elements**:
- `<article>` — wraps the main content body
- `<section>` — groups thematic content within the article
- `<header>` — page/article header
- `<nav>` — navigation elements
- `<aside>` — supplementary content (sidebars, callouts)
- `<footer>` — page/article footer
- `<figure>` + `<figcaption>` — images with descriptive captions
- `<blockquote>` with `cite` attribute — attributed quotes
- `<time datetime="YYYY-MM-DD">` — machine-readable dates

**Anti-patterns** (hurt AI extractability):
- Content rendered entirely via JavaScript (AI crawlers can't execute complex JS)
- Infinite scroll without paginated URLs
- Critical content inside images without alt text
- Tab/accordion content hidden by default (some crawlers skip it)
- Content loaded via AJAX after page render

### 5.5 Meta Description Strategy

AI uses meta descriptions for initial content assessment. Write them as factual summaries, not marketing hooks.

**Do**: "AEO (Answer Engine Optimization) is the practice of optimizing content for AI citation. This guide covers the 31-point checklist, technical requirements, and platform-specific strategies for ChatGPT, Perplexity, and Google AI Overviews."

**Don't**: "Discover the secrets to AI domination! Click to learn our revolutionary approach to getting noticed by ChatGPT."

### 5.6 Image and Visual Optimization

- Descriptive alt text on every image (AI can't see images without it)
- Captions using `<figcaption>` that add context
- Infographics should have text-based summaries nearby
- Original images and charts (harder for AI to replicate = more likely to cite)
- Compressed images for fast load time (page speed is a ranking factor that feeds into AI citations)

### 5.7 PDF Optimization

PDFs are a significant content format that AI crawlers index:
- Use text-based PDFs (not scanned images)
- Include document title in metadata
- Use heading structure within the PDF
- Keep file size reasonable
- Link to PDFs from HTML pages (don't orphan them)

### 5.8 Video Discoverability

- Transcripts published alongside video embeds
- VideoObject schema markup
- Descriptive titles and descriptions
- Chapter markers / timestamps in descriptions
- Key points summarized in text on the same page

---

## 6. Content Optimization by Page Type

### 6.1 Category Explainer Pages

**Purpose**: Define a category, concept, or practice (e.g., "What is CRM?")
**AEO priority**: Highest — these match informational AI queries directly

**Checklist**:
- [ ] Opens with 30-80 word answer block defining the category
- [ ] H2s structured as questions ("What is X?", "How does X work?", "Why does X matter?")
- [ ] Includes comparison table (X vs alternatives)
- [ ] Contains 3+ specific statistics with sources
- [ ] FAQPage schema markup
- [ ] Internal links to related product/feature pages
- [ ] 1,500-2,500 words
- [ ] Reading level Grade 9-11

### 6.2 Product / Feature Pages

**Purpose**: Describe what a product or feature does and how it works
**AEO priority**: High — matches "best X for Y" and "how does X work" queries

**Checklist**:
- [ ] Opens with semantic triple: "[Product] [does what] [for whom/outcome]"
- [ ] Each feature section follows Feature → How → Outcome pattern
- [ ] Includes concrete use case or example per feature
- [ ] Comparison section vs alternatives (with table)
- [ ] Pricing information (if applicable)
- [ ] Product schema markup
- [ ] Customer quote or result with attribution
- [ ] 1,000-2,000 words

### 6.3 Comparison Pages

**Purpose**: Compare products, approaches, or solutions
**AEO priority**: High — "X vs Y" is a major AI query pattern

**Checklist**:
- [ ] Opens with direct comparison summary (30-80 words)
- [ ] Side-by-side comparison table early in the page
- [ ] Each product/option gets equal depth of coverage
- [ ] Specific differentiators with data (not opinions)
- [ ] "Best for" recommendation per product
- [ ] FAQ section addressing common comparison questions
- [ ] Neutral, factual tone (AI deprioritizes biased comparisons)
- [ ] 1,500-3,000 words

### 6.4 Use Case / Story Pages

**Purpose**: Show how a product/approach solves a specific problem
**AEO priority**: Medium — matches "how to [solve problem] with [tool]" queries

**Checklist**:
- [ ] Opens with the problem statement and solution summary
- [ ] Specific, named customer/scenario (not generic)
- [ ] Measurable results with numbers
- [ ] Step-by-step implementation description
- [ ] Before/after comparison
- [ ] Applicable schema (HowTo or Article)
- [ ] 800-1,500 words

### 6.5 Blog Posts / Articles

**Purpose**: Provide in-depth analysis, guides, opinions with original insights
**AEO priority**: Medium-High — matches long-tail and question queries

**Checklist**:
- [ ] Opens with answer block (30-80 words summarizing the key takeaway)
- [ ] H2s as questions or clear topic statements
- [ ] Original data, unique framework, or first-hand experience (information gain)
- [ ] At least one statistic/data point every 150-200 words
- [ ] Expert byline with author bio and credentials
- [ ] Publication date and last-updated date
- [ ] Internal links (3-5 per 1,000 words)
- [ ] FAQ section at the end
- [ ] Article schema markup
- [ ] 1,500-3,000 words for comprehensive guides

### 6.6 Site-Wide Trust Signals

**Purpose**: Build overall domain trust that elevates all pages
**AEO priority**: Critical foundation — affects every page's citation likelihood

**Checklist**:
- [ ] About page with organizational credentials and history
- [ ] Team/author pages with expertise signals
- [ ] Contact page with real contact information
- [ ] Privacy policy and terms of service
- [ ] HTTPS across entire site
- [ ] No broken links (regular audit)
- [ ] Organization schema on homepage
- [ ] Consistent NAP (Name, Address, Phone) across web
- [ ] Press/media page or mentions
- [ ] Case studies or client testimonials

---

## 7. The 31-Point Citation Readiness Checklist

Scoring model: evaluate each item as present (1) or absent (0).

### Section A: Opening Structure (5 points)

1. **Direct answer in first 1-2 sentences** — The opening directly answers the page's primary question
2. **Answer block completeness** — 30-80 word self-contained answer that works without surrounding context
3. **Primary entity named** — The subject (brand, product, concept) is explicitly named in the opening
4. **Outcome stated** — The answer includes what happens / what the reader gets
5. **No preamble** — No "In this article we'll explore..." or "Let's dive into..." before the answer

### Section B: Topical Completeness (6 points)

6. **Full question coverage** — Page addresses the complete question, not just one angle
7. **Related questions addressed** — "People also ask" and follow-up questions are covered
8. **Comparison/context provided** — The topic is situated relative to alternatives or related concepts
9. **Specific data points** — At least 3 statistics, percentages, or concrete numbers with sources
10. **Examples included** — At least 2 concrete, specific examples (not hypothetical)
11. **Actionable takeaways** — Reader can act on the information without needing another source

### Section C: Entity & Authority Signals (5 points)

12. **Expert byline** — Named author with credentials
13. **Author bio present** — Brief bio establishing expertise on the topic
14. **Publication date visible** — Clear date on the page
15. **Sources cited** — External authoritative sources referenced inline
16. **Original contribution** — Something in the content that can't be found elsewhere (data, framework, case study)

### Section D: Technical Accessibility (6 points)

17. **AI crawler access** — robots.txt allows GPTBot, ClaudeBot, PerplexityBot, GoogleOther
18. **Schema markup** — Appropriate schema type implemented (FAQ, Article, HowTo, Product)
19. **Semantic HTML** — Content uses `<article>`, `<section>`, proper heading hierarchy
20. **Page loads without JavaScript** — Core content visible without JS execution
21. **Mobile responsive** — Content accessible on all devices
22. **Page speed** — Loads in under 3 seconds

### Section E: Content Formatting (5 points)

23. **Heading hierarchy** — Proper H1 → H2 → H3 nesting, no skipped levels
24. **Headings as questions** — H2s mirror how users would ask about the topic
25. **Short paragraphs** — 2-4 sentences per paragraph
26. **Reading level** — Grade 9-11 (Flesch-Kincaid)
27. **Active voice** — 90%+ sentences in active voice

### Section F: Distribution & Monitoring (4 points)

28. **Internal links** — 3-5 relevant internal links per 1,000 words
29. **External authority links** — Links to credible external sources
30. **Meta description** — Factual summary (not marketing hook)
31. **Social/distribution presence** — Content is referenced or shared across other platforms (LinkedIn, forums, etc.)

### Scoring Interpretation

| Score | Status | Action |
|-------|--------|--------|
| 28-31 | Publish ready | Minor tweaks, then publish |
| 22-27 | Revise | Address gaps in weakest sections |
| 15-21 | Rework | Significant restructuring needed |
| Below 15 | Restructure | Start from scratch with AEO framework |

---

## 10. Website Audit Framework

### 10.1 Technical Audit Checklist

**Crawler Access** (Critical — check first):
- [ ] robots.txt allows GPTBot, ClaudeBot, PerplexityBot, GoogleOther, Google-Extended
- [ ] No meta robots tags blocking AI bots
- [ ] No CDN/WAF rules blocking bot user agents
- [ ] Content not behind JavaScript rendering walls
- [ ] Content not gated behind login (for public-facing pages)

**Schema Markup**:
- [ ] FAQPage schema on Q&A content
- [ ] Article schema on blog posts / articles
- [ ] HowTo schema on tutorial content
- [ ] Product schema on product pages
- [ ] Organization schema on homepage
- [ ] Person schema on author pages
- [ ] BreadcrumbList on all pages
- [ ] Schema validates in Google Rich Results Test

**Semantic HTML**:
- [ ] `<article>` wrapping main content
- [ ] `<section>` grouping thematic content
- [ ] `<header>`, `<nav>`, `<footer>` used correctly
- [ ] `<figure>` + `<figcaption>` for images
- [ ] `<time datetime>` for dates
- [ ] Heading hierarchy (H1 → H2 → H3) with no skipped levels
- [ ] No content hidden in tabs/accordions that crawlers skip

**Performance**:
- [ ] Page loads under 3 seconds
- [ ] Core Web Vitals passing
- [ ] Mobile responsive
- [ ] HTTPS across entire site

**Supplementary**:
- [ ] llms.txt present at root (nice to have)
- [ ] Sitemap.xml up to date and submitted
- [ ] No orphan pages (all important pages linked from navigation or internal links)

### 10.2 Content Audit Checklist

For each priority page:

**Structure**:
- [ ] 30-80 word answer block opens the content
- [ ] H2s structured as questions / clear topic statements
- [ ] Paragraphs follow Feature → How → Outcome pattern
- [ ] Self-contained passage units (134-167 words)
- [ ] Reading level Grade 9-11
- [ ] Active voice 90%+
- [ ] Sentences under 20 words average

**Authority**:
- [ ] Expert byline present
- [ ] Author bio with credentials
- [ ] Publication date visible
- [ ] Last-updated date visible
- [ ] External sources cited inline
- [ ] Original data or unique contribution present

**Completeness**:
- [ ] Primary question fully answered
- [ ] Related questions addressed
- [ ] Comparison/context provided
- [ ] 3+ specific data points with sources
- [ ] 2+ concrete examples
- [ ] Actionable takeaways

**Distribution**:
- [ ] Meta description is factual (not marketing)
- [ ] Internal links (3-5 per 1,000 words)
- [ ] External authority links present
- [ ] Content referenced on LinkedIn/social/forums

### 10.3 Scoring a Website

Score each page against the 31-point checklist (Section 7). Then calculate:

**Site-wide AEO Score** = Average score across audited pages

| Site Score | Assessment |
|-----------|------------|
| 25+ average | Strong AEO foundation — optimize for specific platforms |
| 20-24 average | Moderate — systematic content improvements needed |
| 15-19 average | Weak — prioritize technical fixes + content restructuring |
| Below 15 average | Critical — fundamental rebuild needed |

**Priority matrix**: Fix technical blockers first (crawler access, schema) → then restructure highest-traffic pages → then expand to all content.

---

## 11. Industry-Specific Impact Data

Traffic impact from AI Overviews varies significantly by industry:

| Industry | Traffic Impact | AI Overview Prevalence |
|----------|---------------|----------------------|
| Healthcare | -64% | High |
| E-commerce | -42% | Medium-High |
| Technology | -35% | High |
| Finance | -30% | Medium |
| Education | -25% | Medium-High |
| B2B SaaS | -18% | Medium |
| Local services | -12% | Low-Medium |

Industries with higher informational query volume see greater impact.

---

## 12. Action Priority Matrix

When implementing AEO/GEO, prioritize in this order:

**Tier 1 — Immediate (Week 1-2)**:
1. Audit and fix robots.txt for AI crawler access
2. Add answer blocks to top 10 highest-traffic pages
3. Add FAQPage schema to pages with Q&A content
4. Fix meta descriptions to be factual summaries
5. Set up initial prompt library (20 prompts)

**Tier 2 — Foundation (Week 3-4)**:
6. Restructure content with proper heading hierarchy
7. Add Article/HowTo schema to remaining content
8. Add expert bylines and author bios
9. Implement semantic HTML structure
10. Run first prompt tracking cycle

**Tier 3 — Optimization (Month 2)**:
11. Rewrite top pages using paragraph pattern (Feature → How → Outcome)
12. Add original data / unique contributions to key content
13. Build internal linking hub-and-spoke structure
14. Optimize LinkedIn presence for AI citation
15. Set up monitoring tool (or systematic spreadsheet tracking)

**Tier 4 — Expansion (Month 3+)**:
16. Create new content targeting citation gaps identified in prompt tracking
17. Implement llms.txt
18. Build multi-platform consensus (Reddit, forums, review sites)
19. Develop video content with transcripts
20. Establish monthly AEO review cadence

---

## 13. Key Statistics Reference

Quick-reference table of the most important statistics for use in the skill's evaluation logic and content recommendations.

| Statistic | Value | Source |
|-----------|-------|--------|
| Zero-click search rate | 58% | HubSpot AEO Playbook |
| AI-referred session growth (YoY) | 527% | Industry reports 2025 |
| B2B buyers using GenAI in purchase | 90-94% | Gartner, LinkedIn |
| AEO market size (2031 projection) | $7.3B | HubSpot |
| AI traffic SQL conversion rate | 27% | HubSpot |
| AI traffic conversion vs Google | 4.4x | Industry benchmarks 2026 |
| Citation domain churn (monthly) | 50-60% | SparkToro/GEO Best Practices |
| Pages with complete answers citation boost | 8x | Writesonic 31-point checklist |
| Schema markup AI summary boost | 36% | BrightEdge |
| E-E-A-T trust signal citation boost | 134% | Writesonic Impact of AI Search |
| E-E-A-T visibility improvement | 89% | Writesonic Impact of AI Search |
| AI Overviews cite from top 10 organic | 81.1% | Writesonic AI Overviews guide |
| Position #1 citation probability | 33% | Writesonic AI Overviews guide |
| Sites unknowingly blocking AI crawlers | 73% | Writesonic 31-point checklist |
| AI Overviews without exact query match | 85% | Writesonic AI Overviews guide |
| Long-tail AI Overview trigger rate | 33% | Writesonic AI Overviews guide |
| Question keyword AI Overview trigger | 22.6% | Writesonic AI Overviews guide |
| Short-tail AI Overview trigger | 9.9% | Writesonic AI Overviews guide |
| Perplexity citation rate | 97% | Averi benchmarks 2026 |
| ChatGPT citation rate | 16% | Averi benchmarks 2026 |
| Google AI Overviews citation rate | 34% | Averi benchmarks 2026 |
| LinkedIn #1 most-cited for professional queries | Yes | LinkedIn/Semrush study |
| Optimal self-contained passage length | 134-167 words | AirOps/Frase analysis |
| Semantic completeness citation threshold | 8.5/10+ = 4.2x more likely | AirOps |
| Domains cited by both ChatGPT and Perplexity | 11% | Profound citation patterns |
| Search volume decline projection (by 2028) | 50% | Gartner |
| Projected search volume drop (by 2026) | 25% | Gartner |
| Wikipedia share of ChatGPT citations | 7.8% | Averi benchmarks |
| Reddit share of Perplexity citations | 16.9% | Profound citation patterns |
| Average Perplexity citations per answer | 21.87 | Profound citation patterns |

---

### 14.2 D1: Technical Infrastructure (The Plumbing — "Can AI Even Access Your Content?")

**What it measures**: Whether AI crawlers can reach, parse, and understand your content at the technical level. This is the prerequisite for everything else — if it fails, D2-D4 are disconnected.

**HubSpot does NOT measure this.** No current AEO grader systematically audits technical access.

**This dimension is mostly binary (pass/fail) but foundational. Start here.**

**Sub-metrics**:

| Metric | What It Measures | Type | Priority |
|--------|-----------------|------|----------|
| AI Crawler Access | robots.txt allows GPTBot, ClaudeBot, PerplexityBot, GoogleOther, Google-Extended | Pass/Fail | Critical |
| No Bot Blocking | CDN/WAF not blocking AI user agents; no meta robots blocking bots | Pass/Fail | Critical |
| Content Without JS | Core content renders without JavaScript execution | Pass/Fail | Critical |
| Schema Markup | FAQPage, Article, HowTo, Product schema implemented in JSON-LD | Score /10 | High |
| Semantic HTML | `<article>`, `<section>`, proper heading hierarchy, `<figure>`+`<figcaption>` | Score /10 | High |
| Page Speed | Loads under 3 seconds, Core Web Vitals passing | Pass/Fail | Medium |
| Mobile Responsive | Content accessible on all devices | Pass/Fail | Medium |
| HTTPS | Full site on HTTPS | Pass/Fail | Medium |
| Meta Descriptions | Factual summaries (not marketing hooks) on all key pages | Score /10 | Medium |
| Sitemap | XML sitemap up to date and submitted | Pass/Fail | Low |
| llms.txt | Markdown file at root with curated content index | Present/Absent | Low (nice to have) |

**Critical stat**: 73% of sites unknowingly block AI crawlers. This single issue can negate all content optimization efforts.

**Audit sequence**: Check crawler access FIRST. If GPTBot/ClaudeBot/PerplexityBot are blocked, nothing else matters until that's fixed.

**Who fixes it**: Development / engineering team. This is a technical implementation task.

### 14.3 D2: Citation Readiness (On-Page Content — "Is Your Content Structured for AI Extraction?")

**What it measures**: Whether the actual content on your pages is structured in a way that AI can extract, understand, and cite. This is the "page/blog/blogpost structure analysis."

**HubSpot does NOT measure this.** Their grader tells you the score but doesn't audit the content that would improve it.

**Sub-metrics**:

| Metric | What It Measures | Scale | Source |
|--------|-----------------|-------|--------|
| Answer Block Quality | Does the page open with a 30-80 word direct answer? | /5 | 31-point checklist, Section A |
| Topical Completeness | Does the page fully answer the primary question plus related questions? | /6 | 31-point checklist, Section B |
| Information Gain | Does the content contain original data, unique frameworks, or first-hand experience? | /5 | HubSpot AEO Playbook |
| Structural Extractability | Paragraph pattern (Feature→How→Outcome), self-contained passages (134-167 words), semantic triples | /5 | HubSpot AEO Playbook, Frase |
| Heading Strategy | Are H2s structured as questions? Proper hierarchy? Match conversational queries? | /4 | 31-point checklist, Section E |
| Readability | Grade 9-11, sentences <20 words, active voice 90%+, short paragraphs | /3 | LinkedIn guide |
| Data Density | At least one statistic/data point every 150-200 words with source attribution | /3 | GEO Best Practices |

**Page-type-specific checklists** (see Section 6 of this knowledge base):
- Category Explainer: optimized for "What is X?" queries
- Product/Feature Page: optimized for "How does X work?" and "Best X for Y" queries
- Comparison Page: optimized for "X vs Y" queries
- Use Case Page: optimized for "How to solve X with Y" queries
- Blog Post/Article: optimized for long-tail informational queries

**Scoring**: Use the 31-point checklist (Section 7). Score each page individually. Aggregate for a site-wide Citation Readiness Score.

| Score Range | Assessment |
|------------|-----------|
| 28-31 | Publish ready — high citation probability |
| 22-27 | Revise — address gaps in weakest areas |
| 15-21 | Rework — significant restructuring needed |
| Below 15 | Restructure — rebuild with AEO framework |

**Who fixes it**: Content team / editorial. This is a writing and content strategy task.

### 14.7 Composite Scoring Model

If building a unified score (for client reports or dashboards), weight the dimensions based on their impact:

| Dimension | Weight | Rationale |
|-----------|--------|-----------|
| D1: Technical Infrastructure | 20% | Binary gate — either works or blocks everything |
| D2: Citation Readiness | 30% | Highest controllable impact on citations |
| D3: Authority & Distribution | 25% | Builds compound advantage over time |
| D4: AI Visibility | 25% | The outcome metric — what actually matters |

**Per-platform breakdown**: Score each dimension separately for ChatGPT, Perplexity, Google AI Overviews, and Gemini, since platform behaviors differ significantly.

