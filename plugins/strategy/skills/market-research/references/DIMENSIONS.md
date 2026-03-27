# Research Dimensions — Query Templates and Guidance

This document provides search query templates and extraction guidance for each of the six research dimensions.

Replace `{market}`, `{region}`, `{year}`, `{company}`, and `{competitor}` with actual values.

---

## 1. Market Sizing

### Goal
Quantify the market: total size, serviceable segments, growth trajectory, and structure.

### Light Mode Queries (2-3)
1. `"{market} market size {region} {year}"`
2. `"{market} industry report TAM {region}"`
3. `"{market} market growth rate CAGR forecast {region}"`

### Deep Mode Queries (4-6)
1. `"{market} market size {region} {year}"`
2. `"{market} TAM SAM SOM {region}"`
3. `"{market} industry report {region} {year}"`
4. `"{market} market growth rate CAGR forecast {region}"`
5. `"{market} market segments breakdown {region}"`
6. `"{market} market structure fragmented consolidated {region}"`

### What to Extract
- **TAM**: Total addressable market value, currency, unit, year, source
- **SAM**: Serviceable addressable market (filtered by region/segment)
- **SOM**: Serviceable obtainable market (realistic capture estimate)
- **CAGR**: Compound annual growth rate with period
- **Market structure**: Fragmented, consolidated, oligopoly, monopolistic competition
- **Key segments**: Named segments with relative size and growth notes

### Source Priority
1. Industry reports (Statista, IBISWorld, Grand View Research, Mordor Intelligence)
2. Market research firms (Gartner, Forrester, McKinsey, BCG)
3. Trade associations and government data
4. Company investor presentations and SEC filings
5. News articles citing specific figures

### Tips
- Market size figures vary widely by source. When possible, cite 2+ sources and note the range.
- Distinguish between global, regional, and country-level figures.
- Check the year of the estimate — market size figures older than 2 years lose accuracy.
- When exact TAM/SAM/SOM breakdowns aren't available, estimate SAM as the regional subset of TAM and note it as "estimated".

---

## 2. Competitor Landscape

### Goal
Map the competitive field: who the players are, how they're positioned, and how they compete.

### Light Mode Queries (2-3)
1. `"top {market} companies {region} {year}"`
2. `"{market} competitive landscape analysis {region}"`
3. `"{competitor} vs {competitor} comparison"` (if competitors provided)

### Deep Mode Queries (4-6)
1. `"top {market} companies {region} {year}"`
2. `"{market} competitive landscape analysis {region}"`
3. `"{market} market share {region} {year}"`
4. `"{market} startups emerging players {region}"`
5. `"{market} mergers acquisitions {region} {year}"`
6. Per-competitor: `"{competitor} {market} review"` or `"{competitor} company profile"`

### What to Extract Per Competitor
- **Name** and **website**
- **Description**: What they do in 1-2 sentences
- **Market position**: Leader, challenger, niche player, or emerging
- **Estimated market share**: Percentage if available, "not available" if not
- **Strengths**: 3-5 key advantages
- **Weaknesses**: 3-5 vulnerabilities
- **Differentiators**: What makes them unique
- **Target audience**: Who they serve
- **Funding stage**: Series A/B/C, public, bootstrapped, PE-backed
- **Year founded** and **headquarters**

### What to Extract for Competitive Dynamics
- Market concentration (top 3-5 players' combined share)
- Recent M&A activity
- New entrants disrupting the space
- Competitive moats (network effects, switching costs, regulation, scale)

### Source Priority
1. G2, Capterra, TrustRadius (SaaS/tech markets)
2. Crunchbase, PitchBook (funding, company data)
3. Industry analyst reports
4. Company "About" pages and press releases
5. LinkedIn company pages (headcount as proxy for scale)

### Tips
- When researching a focal company, position it relative to competitors rather than in isolation.
- Market share data is often paywalled. Use proxies: headcount, funding raised, customer count, web traffic rank.
- Distinguish between direct competitors (same product/market) and indirect competitors (different approach, same job-to-be-done).

---

## 3. Pricing & Products

### Goal
Map the pricing landscape: how products are priced, what's included, and where the price gaps are.

### Light Mode Queries (2-3)
1. `"{market} pricing comparison {year}"`
2. `"{market} product pricing plans {region}"`
3. `"{competitor} pricing"` (for each known competitor — fetch pricing page directly)

### Deep Mode Queries (4-6)
1. `"{market} pricing comparison {year}"`
2. `"{market} pricing models subscription freemium usage-based"`
3. `"{market} product comparison features {year}"`
4. `"best {market} tools pricing {year}"` (review/comparison articles)
5. Per-competitor: WebFetch on `{competitor-website}/pricing` directly
6. `"{market} total cost ownership {region}"`

### What to Extract
- **Pricing models**: Subscription, freemium, usage-based, one-time, custom/enterprise
- **Tier breakdown**: Name, price, key features per tier
- **Price range**: Entry-level, mid-market, enterprise price points
- **Feature matrix**: Key features mapped across competitors (yes/no/partial/premium)

### Source Priority
1. Competitor pricing pages (WebFetch directly)
2. G2, Capterra comparison grids
3. Pricing comparison blog posts and review articles
4. Product Hunt and alternative-to sites

### Tips
- Many enterprise products don't list pricing. Note "custom pricing" and estimate from reviews if possible.
- Annual vs monthly pricing: note both when available.
- Watch for hidden costs: implementation fees, per-user charges, API call limits.
- In deep mode, build a full feature comparison matrix. In light mode, compare top 5-8 features only.

---

## 4. Trends & News

### Goal
Identify where the market is heading and what's happened recently that matters.

### Light Mode Queries (2-3)
1. `"{market} trends {year} {region}"`
2. `"{market} industry news {region} {year}"`
3. `"{market} future outlook predictions {year}"`

### Deep Mode Queries (4-6)
1. `"{market} trends {year} {region}"`
2. `"{market} technology trends {year}"`
3. `"{market} regulatory changes {region} {year}"`
4. `"{market} industry news {region}"`
5. `"{market} disruption emerging technology"`
6. `"{market} market forecast {year} outlook"`

### What to Extract Per Trend
- **Title**: Short name for the trend
- **Category**: technology, regulatory, market, consumer, economic, or competitive
- **Description**: What's happening and why it matters
- **Impact**: High, medium, or low
- **Timeframe**: Near-term (0-1yr), mid-term (1-3yr), long-term (3+yr)
- **Source**: Where this trend is documented

### What to Extract for News
- **Headline** and **date**
- **URL**
- **Significance**: Why this news matters to someone entering or operating in the market

### Source Priority
1. Industry analyst blogs (Gartner, Forrester, McKinsey Insights)
2. Trade publications specific to the market
3. Business news (Bloomberg, Reuters, TechCrunch, The Information)
4. Government regulatory announcements
5. Company press releases for major moves

### Tips
- Distinguish between hype and substance. AI/blockchain/etc. show up as "trends" in every market — include only if there's real adoption evidence.
- Regulatory trends matter more in some markets (fintech, healthcare, food) than others. Weight accordingly.
- Look for contrarian takes — "why X trend is overblown" adds nuance.

---

## 5. Consumer/User Behavior

### Goal
Understand how buyers make decisions: what they want, what frustrates them, and what drives purchase.

### Light Mode Queries (2-3)
1. `"{market} consumer behavior {region} {year}"`
2. `"{market} buyer preferences survey {year}"`
3. `"{market} customer pain points reviews"`

### Deep Mode Queries (4-6)
1. `"{market} consumer behavior {region} {year}"`
2. `"{market} buyer preferences survey {year}"`
3. `"{market} customer pain points reviews"`
4. `"{market} buying decision factors study"`
5. `"{market} user satisfaction NPS {year}"`
6. `"why customers switch {market} providers"` or `"{market} churn reasons"`

### What to Extract
- **Buying patterns**: How purchases happen (online vs offline, decision timeline, group vs individual)
- **Preferences**: What features/attributes buyers prioritize, segmented by user type
- **Pain points**: Top frustrations with severity (critical/moderate/minor)
- **Decision factors**: Ranked list of what drives the purchase decision (price, features, support, brand, etc.)

### Source Priority
1. Published surveys and market research (Statista, Pew, industry-specific)
2. Review platforms (G2, Capterra, Trustpilot, Amazon reviews)
3. Reddit, Quora, and forum discussions (directional, not definitive)
4. User experience studies and case studies
5. Analyst reports on consumer trends

### Tips
- Behavior varies by segment. Note which segment a finding applies to.
- Review sites are gold for pain points — look for recurring complaints across multiple reviews.
- Decision factors change by buyer maturity. First-time buyers weight different things than switchers.
- In B2B markets, distinguish between the user (who uses the product) and the buyer (who approves the purchase).

---

## 6. Gaps & Opportunities

### Goal
Synthesize findings from dimensions 1-5 into actionable insights about where the market has unmet needs.

### No Web Searches Required
This dimension is pure synthesis. Do not run additional searches.

### Synthesis Process

1. **Cross-reference competitor weaknesses with consumer pain points**
   - If buyers complain about X and no competitor addresses X well, that's a gap.

2. **Map pricing gaps**
   - If all competitors price at $50+ and consumers want a $20 option, that's a gap.
   - If enterprise solutions exist but SMB options are weak, that's a gap.

3. **Match trends with current offerings**
   - If a trend is gaining momentum but competitors haven't adapted, that's an opportunity.

4. **Check geographic coverage**
   - If the market is growing in {region} but most competitors focus elsewhere, that's a gap.

5. **Identify underserved segments**
   - From market sizing: which segments are growing fastest but have fewest competitors?

### Output Structure

For each **gap**:
- What the gap is
- Evidence (cite specific findings from earlier dimensions)
- Which dimensions informed it

For each **opportunity**:
- What the opportunity is
- Rationale (why now, why this market)
- Effort to pursue (low/medium/high)
- Potential impact (low/medium/high)
- Timeframe

**Strategic recommendations**: Top 3-5 actionable next steps. Each should be concrete enough to act on.
