# AI Visibility Monitor — Knowledge Base Extract

KB Version: 1.1 | KB Last Updated: 2026-03-26

Extracted sections from AEO-GEO-KNOWLEDGE-BASE.md relevant to the ai-visibility-monitor skill.

---

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

## 9. Prompt Tracking Methodology

### 9.1 What Is Prompt Tracking?

Instead of monitoring keyword rankings on a SERP, you monitor what AI platforms say when users ask questions relevant to your brand, product, or industry. You want to know: Does the AI mention you? Does it cite you with a link? Does it recommend a competitor? What sources does it pull from?

### 9.2 Building a Prompt Library

**Step 1: Identify core topics** — List 5-10 topics central to your brand/product/expertise.

**Step 2: Map to conversational queries** — For each topic, write 3-5 prompts that your ideal customer would actually type into an AI tool. These are not keyword phrases — they are full conversational queries.

**Examples by intent**:
- Informational: "What is the best approach to email marketing automation for a B2B SaaS startup?"
- Comparative: "Compare HubSpot vs Salesforce for small business CRM"
- Recommendation: "What tools should I use for content marketing in 2026?"
- Problem-solving: "How do I reduce customer churn for my subscription business?"
- Decision: "Is it worth investing in AI-powered customer service?"

**Step 3: Include branded prompts** — Add prompts that explicitly mention your brand:
- "What does [Brand] do?"
- "Is [Brand] good for [use case]?"
- "What are alternatives to [Brand]?"
- "[Brand] vs [Competitor]"

**Step 4: Aim for 20-30 prompts total** — Enough for statistical significance, manageable for regular tracking.

### 9.3 Running and Recording

**Cadence**: Monthly minimum. Weekly for competitive categories.

**Platforms to test**: ChatGPT (GPT-4), Perplexity, Google AI Overviews/AI Mode, Gemini, Claude (when web-enabled).

**Record for each prompt**:
- Date and platform
- Brand mentions (yours and competitors)
- Citations with URLs (did it link to you?)
- Position in answer (first mention vs buried)
- Sentiment (how you're described — positive, neutral, negative)
- Accuracy (did the AI get your info right or hallucinate?)
- Sources cited (what domains appeared?)
- Competitor presence (who else was mentioned/recommended?)

### 9.4 Analysis Patterns

**Share of Voice**: What % of your tracked prompts mention your brand vs competitors?

**Citation Rate**: Of mentions, how many include an actual link/citation?

**Drift Detection**: Which prompts showed the most citation change month-over-month?

**Gap Analysis**: Which prompts cite competitors but not you? These are content opportunities.

**Accuracy Audit**: Where is AI getting your information wrong? These need corrective content.

### 9.5 AEO/GEO Monitoring Tools

| Tool | Focus | Key Features |
|------|-------|-------------|
| **Profound** | Enterprise, multi-LLM | SOC 2, GA4 attribution, multi-region/multilingual, deep analytics across ChatGPT/Gemini/Claude/Perplexity/Copilot |
| **Otterly AI** | Brand visibility | Lightweight, affordable, 10,000+ users, tracks mentions inside AI-generated responses |
| **Peec AI** | Real-time reporting | Region/assistant breakdown, competitor tracking, multi-user, cost-effective |
| **AIclicks** | Citation tracking | Tracks AI citations and brand mentions across platforms |
| **SE Ranking Visible** | GEO monitoring | Content optimization scoring, AI search tracking across 8 platforms |
| **Ahrefs Brand Radar** | Brand monitoring | Integrated with Ahrefs SEO suite, tracks AI brand mentions |
| **Writesonic AI Visibility** | Content optimization | Citation readiness scoring, AI visibility audit |

**For small operations**: Start with a spreadsheet. Run prompts manually, log results, look for patterns. Graduate to a tool when tracking 30+ prompts across 3+ platforms.

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

### 14.5 D4: AI Visibility (The Output — "Are You Being Cited?")

**What it measures**: The actual results — what AI platforms say about your brand when users prompt them. This is what HubSpot's AEO Grader focuses on.

**This is the scoreboard, not the playbook.** It tells you where you stand but not why or how to improve. D4 is the lagging indicator that improves as a result of fixing D1, D2, and D3.

**Sub-metrics (modeled on HubSpot AEO Grader structure)**:

| Metric | What It Measures | Scale | HubSpot Equivalent |
|--------|-----------------|-------|-------------------|
| Brand Recognition | How visible the brand is across AI platforms — mention depth, source quality, data richness, confidence level | /20 | Brand Recognition (/20) |
| Market Position / Share of Voice | Brand's share of industry conversations in AI responses vs competitors — mention counts, comparison mentions, market position breakdown | /10 | Market Score (/10) + Share of Voice (/10) |
| Presence Quality | Quality and depth of how the brand appears — not just mentioned but how it's described, what context, what accuracy | /20 | Presence Quality (/20) |
| Brand Sentiment | How AI describes the brand — general perception, source-based sentiment, contextual sentiment, opinion polarization | /40 | Brand Sentiment (/40) — broken into General, Source-Based, Contextual, Polarization |

**Additional sub-metrics from HubSpot's Brand Recognition detail**:

| Sub-metric | What It Reveals |
|-----------|----------------|
| Recognition Score (/100) | Overall digital visibility of the brand name |
| Market Position | Classification: Niche, Emerging, Established, Leader |
| Brand Archetype | How AI categorizes the brand: Traditionalist, Innovator, Disruptor, etc. |
| Confidence Level (%) | How confident the AI is in its information about the brand (62%, 85%, 70% in Quantronic example) |
| Mention Depth (/10) | How detailed the mentions are — surface-level name drop vs in-depth description |
| Source Quality (/10) | Quality of sources AI draws from when discussing the brand |
| Data Richness (/10) | Volume and variety of data available to AI about the brand |

**Additional sub-metrics from HubSpot's Sentiment Analysis**:

| Sub-metric | What It Reveals |
|-----------|----------------|
| General Sentiment (/100) | Overall public perception in digital spaces |
| Source-Based Sentiment (/100) | Sentiment derived from specific data sources (reviews, media, employee reviews) |
| Contextual Sentiment (/100) | Industry-specific factors influencing perception |
| Polarization (/100) | Degree of opinion division — low = consistent perception, high = controversial |

**Qualitative outputs**:
- Narrative Themes: recurring themes AI associates with the brand
- Key Strengths: what AI identifies as the brand's advantages
- Growth Areas: opportunities AI surfaces
- Market Trajectory: how AI perceives the brand's momentum
- Common Comparisons: which competitors and on what dimensions

**How to measure**: Run a prompt library (20-30 prompts) across ChatGPT, Perplexity, Gemini, and Google AI Overviews. Record mentions, citations, sentiment, accuracy, and competitor presence. Repeat monthly.

**Who fixes it**: This dimension improves as a *result* of fixing D1, D2, and D3. It's the lagging indicator — track it to see if your work on the other three dimensions is paying off.

**Platform-specific scoring**: Each metric should be scored per AI platform (ChatGPT, Perplexity, Gemini at minimum), since a brand can score well on one and poorly on another. Only 11% of domains are cited by both ChatGPT and Perplexity.

### 14.7 Composite Scoring Model

If building a unified score (for client reports or dashboards), weight the dimensions based on their impact:

| Dimension | Weight | Rationale |
|-----------|--------|-----------|
| D1: Technical Infrastructure | 20% | Binary gate — either works or blocks everything |
| D2: Citation Readiness | 30% | Highest controllable impact on citations |
| D3: Authority & Distribution | 25% | Builds compound advantage over time |
| D4: AI Visibility | 25% | The outcome metric — what actually matters |

**Per-platform breakdown**: Score each dimension separately for ChatGPT, Perplexity, Google AI Overviews, and Gemini, since platform behaviors differ significantly.

