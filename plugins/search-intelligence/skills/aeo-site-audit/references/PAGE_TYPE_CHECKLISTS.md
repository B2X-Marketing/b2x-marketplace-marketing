# Page-Type-Specific Checklists

Extracted from KB Section 6. Use these alongside the 31-point checklist to provide page-type-specific guidance during D2 scoring.

---

## 1. Category Explainer Pages

**Purpose**: Define a category, concept, or practice (e.g., "What is CRM?")
**AEO priority**: Highest — these match informational AI queries directly
**Target queries**: "What is X?", "X explained", "X definition"

**Checklist**:
- [ ] Opens with 30-80 word answer block defining the category
- [ ] H2s structured as questions ("What is X?", "How does X work?", "Why does X matter?")
- [ ] Includes comparison table (X vs alternatives)
- [ ] Contains 3+ specific statistics with sources
- [ ] FAQPage schema markup
- [ ] Internal links to related product/feature pages
- [ ] 1,500-2,500 words
- [ ] Reading level Grade 9-11

**Key D2 emphasis**: Section A (Opening Structure) and Section B (Topical Completeness) are critical for this page type. The answer block must define the category completely in 30-80 words. Related questions (item 7) should cover the full "what/how/why" arc.

---

## 2. Product / Feature Pages

**Purpose**: Describe what a product or feature does and how it works
**AEO priority**: High — matches "best X for Y" and "how does X work" queries
**Target queries**: "Best X for Y", "How does X work?", "X features", "X review"

**Checklist**:
- [ ] Opens with semantic triple: "[Product] [does what] [for whom/outcome]"
- [ ] Each feature section follows Feature -> How -> Outcome pattern
- [ ] Includes concrete use case or example per feature
- [ ] Comparison section vs alternatives (with table)
- [ ] Pricing information (if applicable)
- [ ] Product schema markup
- [ ] Customer quote or result with attribution
- [ ] 1,000-2,000 words

**Key D2 emphasis**: Section A (item 3 — primary entity named) and Section C (items 15-16 — sources and original contribution) matter most. The opening semantic triple must name the product, state what it does, and for whom. Customer results with specific numbers strengthen item 16 (original contribution).

---

## 3. Comparison Pages

**Purpose**: Compare products, approaches, or solutions
**AEO priority**: High — "X vs Y" is a major AI query pattern
**Target queries**: "X vs Y", "X alternative", "X compared to Y", "best X for [use case]"

**Checklist**:
- [ ] Opens with direct comparison summary (30-80 words)
- [ ] Side-by-side comparison table early in the page
- [ ] Each product/option gets equal depth of coverage
- [ ] Specific differentiators with data (not opinions)
- [ ] "Best for" recommendation per product
- [ ] FAQ section addressing common comparison questions
- [ ] Neutral, factual tone (AI deprioritizes biased comparisons)
- [ ] 1,500-3,000 words

**Key D2 emphasis**: Section B (items 8-9 — comparison/context and specific data points) is the differentiator. The comparison must be factual and data-driven, not opinion-based. AI systems deprioritize biased comparisons. Equal depth of coverage for each option signals neutrality. The FAQ section (item 7) should address "When should I choose X over Y?" variations.

---

## 4. Use Case / Story Pages

**Purpose**: Show how a product/approach solves a specific problem
**AEO priority**: Medium — matches "how to [solve problem] with [tool]" queries
**Target queries**: "How to solve X with Y", "X case study", "X implementation example"

**Checklist**:
- [ ] Opens with the problem statement and solution summary
- [ ] Specific, named customer/scenario (not generic)
- [ ] Measurable results with numbers
- [ ] Step-by-step implementation description
- [ ] Before/after comparison
- [ ] Applicable schema (HowTo or Article)
- [ ] 800-1,500 words

**Key D2 emphasis**: Section B (items 9-10 — data points and examples) and Section C (item 16 — original contribution) are the differentiators. Measurable results with specific numbers are the core value. Generic case studies without named customers or concrete metrics score poorly on item 10 (examples) and item 16 (original contribution). The before/after comparison provides the comparison/context (item 8).

---

## 5. Blog Posts / Articles

**Purpose**: Provide in-depth analysis, guides, opinions with original insights
**AEO priority**: Medium-High — matches long-tail and question queries
**Target queries**: Long-tail informational queries, "how to", "guide to", "[topic] best practices"

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

**Key D2 emphasis**: All six sections matter roughly equally for blog posts. Section C (Entity & Authority) is particularly important — expert byline (item 12), author bio (item 13), and publication date (item 14) are table stakes for blog content. Section B item 9 (data density) should be checked carefully: at least one data point every 150-200 words. The information gain signal (item 16) separates content that gets cited from content that gets ignored.

---

## Page Type Detection Heuristics

When auto-classifying pages during Step 3 (Page Discovery), use these URL and title patterns:

| Page Type | URL Patterns | Title Patterns |
|-----------|-------------|----------------|
| Category Explainer | `/what-is-`, `/guide/`, `/learn/`, `/glossary/`, `/101/` | "What is X?", "X Guide", "X Explained", "Understanding X" |
| Product/Feature | `/product/`, `/feature/`, `/platform/`, `/solutions/`, `/tools/` | "X Product", "X Features", "X Platform" |
| Comparison | `/vs-`, `/vs/`, `/compare/`, `/alternative/`, `/comparison/` | "X vs Y", "X Alternative", "X Compared to Y" |
| Use Case | `/use-case/`, `/case-study/`, `/customer-story/`, `/success/` | "How X Uses Y", "X Case Study", "X Success Story" |
| Blog/Article | `/blog/`, `/article/`, `/news/`, `/insights/`, `/resources/` | Date patterns, topic-focused titles, "How to X" |

If a page does not match any pattern, classify as Blog/Article (the most general type) and note the uncertainty.
