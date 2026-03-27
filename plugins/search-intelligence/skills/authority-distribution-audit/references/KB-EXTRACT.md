# Authority & Distribution Audit — Knowledge Base Extract

KB Version: 1.1 | KB Last Updated: 2026-03-26

Extracted sections from AEO-GEO-KNOWLEDGE-BASE.md relevant to the authority-distribution-audit skill.

---

## 2. How AI Engines Decide What to Cite

### 2.1 Three Primary Signals

**Signal 1: Consensus**
Facts echoed across multiple credible, independent sources. If a claim appears consistently across your website, Reddit discussions, YouTube tutorials, industry publications, review sites (G2, Capterra), and Wikipedia — AI systems gain confidence in citing it.

- Consensus is the strongest predictor of brand recommendation by AI
- SparkToro data shows high variability in brand recommendations across prompts — consistency across the web reduces this variability
- Reddit and community forums account for 16.9% of Perplexity citations — user-generated consensus matters

**Signal 2: Information Gain**
Original data, proprietary research, unique frameworks, concrete examples, and clear points of view that add something no other source provides.

- "AI marketing campaigns deliver 20-30% higher ROI" gets cited
- "AI marketing improves results" does not
- Content with specific statistics, percentages, and data points with source attribution gets preferentially cited
- Every 150-200 words should include a specific data point

**Signal 3: Entities & Structure**
Clear entities (people, products, companies, concepts), schema markup, and Subject-Verb-Object factual claims (semantic triples) that reduce ambiguity.

- Semantic triples: "HubSpot Forms captures lead data on submission" (extractable) vs "our tool helps with forms" (not extractable)
- Entity clarity means AI can unambiguously attribute claims to the correct subject
- Schema.org markup (JSON-LD) provides machine-readable entity relationships

### 2.2 Platform-Specific Citation Behavior

Each AI platform has distinct citation patterns. A strategy must address all four.

**Perplexity**
- Cites sources in 97% of responses
- Averages 21.87 citations per answer
- Reddit/community forums = 16.9% of citations
- Balanced mention-to-citation ratio — best for driving actual traffic
- Favors fresh, well-cited articles
- Algorithms favor sites with machine-readable content (schema.org, OpenGraph, JSON-LD)

**Google AI Overviews**
- Cites sources in 34% of cases
- Strongest brand preference (59.8% of citations)
- 81.1% of citations come from content already ranking in the top 10
- Position #1 organic = 33% chance of citation
- Domain Rating (DR) 88-100 = 6,000+ citations; below DR 63 = barely cited
- AI Overviews occupy 1,764 pixels on average, appearing in 47% of queries
- Long-tail queries trigger 33% of AI Overviews; question keywords 22.6%; short-tail only 9.9%

**ChatGPT**
- Cites sources in only 16% of responses
- Wikipedia = #1 source at 7.8%
- Favors authoritative long-form content
- Will mention brands but rarely links — mentions without traffic
- Training data influence: content in training corpus shapes responses even without real-time citation

**Claude**
- Lower search-use volume currently but growing
- Relies on training data and, when web-enabled, similar patterns to Perplexity
- Values structured, factual content with clear attributions

**Key stat**: Only 11% of domains are cited by both ChatGPT and Perplexity — they are distinct ecosystems requiring different strategies.

### 2.3 Citation Likelihood by Content Type

| Content Type | Citation Likelihood Multiplier |
|-------------|-------------------------------|
| Government / .gov | 11.75x |
| Support documentation | 3.43x |
| Educational / .edu | 2.8x |
| Reference / Wikipedia-style | 2.1x |
| Long-form blog with original data | 1.8x |
| Comparison / vs. pages | 1.6x |
| Product pages (well-structured) | 1.2x |
| Thin marketing copy | 0.3x |

### 2.4 Domain Authority Impact on Citations

| Domain Rating Range | Approximate Citations |
|--------------------|----------------------|
| DR 88-100 | 6,000+ |
| DR 75-87 | 1,500-4,000 |
| DR 63-74 | 200-800 |
| Below DR 63 | Minimal |

Citation drops 4x when content falls off page one of organic search. For Google AI Overviews specifically, organic ranking is a prerequisite.

---

## 4. E-E-A-T for AI Systems

Experience, Expertise, Authoritativeness, Trustworthiness — heavily weighted by AI systems when selecting sources to cite.

### 4.1 Impact Data

- Trust-specific content updates led to 134% citation boost
- 89% visibility improvement from E-E-A-T signals
- AI systems cross-reference author credentials against known entities
- Content from recognized subject matter experts cited 3-5x more frequently

### 4.2 Required Trust Signals

**Author-level**:
- Expert byline with full name
- Author bio with credentials, role, and relevant experience
- Author schema markup (Person schema with sameAs links)
- Link to author's LinkedIn, professional profile, or publication history
- Consistent author identity across the web (consensus signal)

**Content-level**:
- Publication date (clearly visible)
- Last updated date (especially for evergreen content)
- Cited sources within the content (inline attribution)
- Links to authoritative external references
- Original data, research, or first-hand experience
- Methodology disclosure when presenting data/claims

**Site-level**:
- About page with organizational credentials
- Contact information
- Privacy policy and terms
- Industry certifications or awards
- Press mentions or media coverage
- Client logos or case studies (social proof)

### 4.3 Semiotic Cues of Helpfulness

AI evaluates "signals of helpfulness" — formatting and structural cues that indicate content is designed to help, not just to rank.

- Table of contents for long content
- Jump links / anchor navigation
- Summary boxes or key takeaway sections
- Clearly labeled sections
- Visual hierarchy (not walls of text)
- FAQ sections with direct answers
- "Last updated" timestamps

---

## 8. LinkedIn as a Citation Channel

LinkedIn is the #1 most-cited domain for professional queries and #2 overall in AI search. This makes it a critical channel for B2B AEO.

### 8.1 Citation Data

- Articles = 50-66% of LinkedIn citations by AI
- Posts = 15-28% of citations
- Comments = ~5% of citations
- 95% of citations come from original content (not reshared)
- Members with 3,000+ followers get stronger citation weight
- Individual member content outperforms Company Page content

### 8.2 LinkedIn Content Optimization for AI

**Article sweet spot**: 500-2,000 words
**Post sweet spot**: 150-300 words with a clear point

**Four pillars for LinkedIn AI visibility**:

1. **Original Insight** — Share proprietary data, first-hand experience, or unique analysis. AI deprioritizes reshared or generic content.

2. **Professional Authority** — Complete profile with credentials, consistent posting cadence, engagement from other professionals in the field.

3. **Structured Formatting** — Use headers, lists, and clear paragraph breaks even in posts. LinkedIn articles should follow the same answer-block structure as blog posts.

4. **Topical Consistency** — Post regularly on the same 2-3 topics. AI builds topical authority profiles for authors.

### 8.3 LinkedIn-Specific Checklist

- [ ] Profile fully completed with expertise keywords
- [ ] 3,000+ followers (citation weight threshold)
- [ ] Articles use headers and structured formatting
- [ ] Content is original (not cross-posted from blog without modification)
- [ ] Includes specific data, examples, or case studies
- [ ] Consistent posting cadence (2-4x per week minimum)
- [ ] Engages in comments on own posts (adds depth)
- [ ] Tags relevant topics and people (entity signals)

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

### 14.4 D3: Authority & Distribution (Off-Site Presence — "Does AI Trust You?")

**What it measures**: The trust signals on your site (E-E-A-T) plus your brand's presence across the broader web, which feeds the consensus signal AI uses to decide confidence in citing you.

**HubSpot partially measures this** through Source Quality and Data Richness in Brand Recognition, but doesn't give an actionable breakdown of where presence is weak.

**Sub-metrics — On-site Authority (E-E-A-T)**:

| Metric | What It Measures | Scale |
|--------|-----------------|-------|
| Expert Bylines | Named authors with credentials on content | Pass/Fail per page |
| Author Bios | Bio with role, expertise, relevant experience | Pass/Fail per page |
| Author Schema | Person schema with sameAs links to professional profiles | Pass/Fail |
| Publication Dates | Visible publish + last-updated dates | Pass/Fail per page |
| Source Citations | External authoritative sources cited inline | Count per page |
| Original Contribution | Proprietary data, unique frameworks, first-hand experience | Present/Absent per page |
| Organization Credentials | About page, certifications, awards, press mentions | Score /10 |

**Impact data**: E-E-A-T trust signal optimization led to 134% citation boost and 89% visibility improvement.

**Sub-metrics — Off-site Distribution (Consensus Signals)**:

| Platform | What to Measure | Why It Matters |
|----------|----------------|---------------|
| LinkedIn | Profile completeness, article count, follower count (3,000+ threshold), posting consistency | #1 most-cited domain for professional queries |
| Reddit / Forums | Brand mention frequency, sentiment, thread participation | 16.9% of Perplexity citations come from Reddit |
| Review Sites (G2, Capterra, Trustpilot) | Review count, average rating, recency of reviews | Consensus signal — AI checks independent validation |
| YouTube | Video content with transcripts, channel authority | Multimedia harder for AI to replicate = more citations |
| Wikipedia | Brand/product page existence and quality | 7.8% of ChatGPT citations; foundational reference |
| Industry Publications | Mentions in trade press, guest posts, expert quotes | Authority signal for domain expertise |
| Directories | Presence in relevant industry directories | Discovery signal for niche brands |

**Who fixes it**: Marketing / PR team for off-site distribution. Content team for on-site E-E-A-T signals.

### 14.7 Composite Scoring Model

If building a unified score (for client reports or dashboards), weight the dimensions based on their impact:

| Dimension | Weight | Rationale |
|-----------|--------|-----------|
| D1: Technical Infrastructure | 20% | Binary gate — either works or blocks everything |
| D2: Citation Readiness | 30% | Highest controllable impact on citations |
| D3: Authority & Distribution | 25% | Builds compound advantage over time |
| D4: AI Visibility | 25% | The outcome metric — what actually matters |

**Per-platform breakdown**: Score each dimension separately for ChatGPT, Perplexity, Google AI Overviews, and Gemini, since platform behaviors differ significantly.

