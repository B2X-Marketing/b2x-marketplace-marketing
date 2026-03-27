# JSON Data Schema — Field Documentation

This document describes the JSON data model for market research output. The formal JSON Schema file is at `Research/Schema/research-data-schema.json`.

## Top-Level Structure

```json
{
  "metadata": { ... },
  "market_sizing": { ... },
  "competitor_landscape": { ... },
  "pricing_products": { ... },
  "trends_news": { ... },
  "consumer_behavior": { ... },
  "gaps_opportunities": { ... }
}
```

All six dimensions are required. If a dimension has no data, include it with a summary noting the gap and empty arrays.

---

## metadata

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `slug` | string | Yes | URL-safe identifier: `{market-slug}-{YYYY-MM-DD}` |
| `market` | string | Yes | Market or industry researched |
| `region` | string | Yes | Geographical region |
| `company` | string or null | No | Focal company, if provided |
| `competitors_provided` | string[] | No | Competitor names from user input |
| `date_generated` | string (date) | Yes | ISO date: `YYYY-MM-DD` |
| `mode` | "light" or "deep" | Yes | Research mode used |
| `sources_count` | integer | Yes | Total unique sources across all dimensions |
| `dimensions_completed` | string[] | Yes | Dimensions that produced meaningful data |
| `confidence_rating` | "high" / "medium" / "low" | Yes | Overall data confidence |

**Confidence rating criteria:**
- **high**: Most data points have strong sources (industry reports, official data). TAM/SAM available.
- **medium**: Mix of strong and weak sources. Some data points estimated. Key dimensions covered.
- **low**: Sparse data. Heavy reliance on estimates. One or more dimensions have little to no data.

---

## market_sizing

| Field | Type | Description |
|-------|------|-------------|
| `summary` | string | 2-3 sentence overview |
| `tam` | object | Total Addressable Market |
| `tam.value` | number or null | Dollar value |
| `tam.currency` | string | Default "USD" |
| `tam.unit` | string | "thousands", "millions", "billions", or "trillions" |
| `tam.year` | integer or null | Year of the estimate |
| `tam.source` | string | Source name |
| `tam.confidence` | string | "high", "medium", "low", or "estimated" |
| `sam` | object | Same structure as `tam` — Serviceable Addressable Market |
| `som` | object | Same structure as `tam` — Serviceable Obtainable Market |
| `growth_rate` | object | CAGR data |
| `growth_rate.cagr_percent` | number or null | Percentage |
| `growth_rate.period` | string | e.g., "2024-2030" |
| `growth_rate.source` | string | Source name |
| `market_structure` | string | "fragmented", "consolidated", "oligopoly", etc. |
| `key_segments` | array | Market segments |
| `key_segments[].name` | string | Segment name |
| `key_segments[].size_description` | string | Relative or absolute size |
| `key_segments[].growth_notes` | string | Growth trajectory |
| `sources` | source[] | All sources for this dimension |

---

## competitor_landscape

| Field | Type | Description |
|-------|------|-------------|
| `summary` | string | 2-3 sentence overview |
| `competitors` | array | Competitor profiles |
| `competitors[].name` | string | Company name (required) |
| `competitors[].website` | string or null | Company URL |
| `competitors[].description` | string | What they do (1-2 sentences) |
| `competitors[].market_position` | string | "leader", "challenger", "niche", "emerging" |
| `competitors[].estimated_market_share` | string or null | Percentage or "not available" |
| `competitors[].strengths` | string[] | Key advantages |
| `competitors[].weaknesses` | string[] | Key vulnerabilities |
| `competitors[].differentiators` | string[] | Unique selling points |
| `competitors[].target_audience` | string | Who they serve |
| `competitors[].funding_stage` | string or null | "Series A", "public", "bootstrapped", etc. |
| `competitors[].year_founded` | integer or null | Year |
| `competitors[].headquarters` | string or null | City/country |
| `competitive_dynamics` | string | How players interact, M&A, shifts |
| `sources` | source[] | All sources for this dimension |

---

## pricing_products

| Field | Type | Description |
|-------|------|-------------|
| `summary` | string | 2-3 sentence overview |
| `pricing_models` | array | Per-company pricing |
| `pricing_models[].company` | string | Company name |
| `pricing_models[].model_type` | string | "subscription", "freemium", "usage-based", "one-time", etc. |
| `pricing_models[].tiers` | array | Pricing tiers |
| `pricing_models[].tiers[].name` | string | Tier name |
| `pricing_models[].tiers[].price` | string | e.g., "$49/mo", "$599/yr", "custom" |
| `pricing_models[].tiers[].key_features` | string[] | Features included in this tier |
| `price_range` | object | Market-wide price bands |
| `price_range.low` | string | Entry-level price point |
| `price_range.mid` | string | Mid-market price point |
| `price_range.high` | string | Enterprise price point |
| `price_range.notes` | string | Context on pricing |
| `feature_comparison` | array | Feature matrix |
| `feature_comparison[].feature` | string | Feature name |
| `feature_comparison[].availability` | object | Company name → "yes" / "no" / "partial" / "premium" |
| `sources` | source[] | All sources for this dimension |

---

## trends_news

| Field | Type | Description |
|-------|------|-------------|
| `summary` | string | 2-3 sentence overview |
| `trends` | array | Industry trends |
| `trends[].title` | string | Short trend name |
| `trends[].category` | string | "technology", "regulatory", "market", "consumer", "economic", "competitive" |
| `trends[].description` | string | What's happening and why it matters |
| `trends[].impact` | string | "high", "medium", "low" |
| `trends[].timeframe` | string | "near-term (0-1yr)", "mid-term (1-3yr)", "long-term (3+yr)" |
| `trends[].source` | string | Source name |
| `recent_news` | array | Recent news items |
| `recent_news[].headline` | string | News headline |
| `recent_news[].date` | string | Publication date |
| `recent_news[].url` | string | Article URL |
| `recent_news[].significance` | string | Why this matters |
| `sources` | source[] | All sources for this dimension |

---

## consumer_behavior

| Field | Type | Description |
|-------|------|-------------|
| `summary` | string | 2-3 sentence overview |
| `buying_patterns` | array | How purchases happen |
| `buying_patterns[].pattern` | string | The observed pattern |
| `buying_patterns[].evidence` | string | Supporting data |
| `buying_patterns[].source` | string | Source name |
| `preferences` | array | What buyers want |
| `preferences[].preference` | string | The preference |
| `preferences[].segment` | string | Which user segment |
| `preferences[].evidence` | string | Supporting data |
| `pain_points` | array | Buyer frustrations |
| `pain_points[].pain_point` | string | The problem |
| `pain_points[].severity` | string | "critical", "moderate", "minor" |
| `pain_points[].evidence` | string | Supporting data |
| `decision_factors` | string[] | Ranked list of purchase drivers |
| `sources` | source[] | All sources for this dimension |

---

## gaps_opportunities

| Field | Type | Description |
|-------|------|-------------|
| `summary` | string | 2-3 sentence overview |
| `gaps` | array | Market gaps identified |
| `gaps[].gap` | string | What the gap is |
| `gaps[].evidence` | string | Supporting evidence |
| `gaps[].dimensions_referenced` | string[] | Which dimensions informed this gap |
| `opportunities` | array | Actionable opportunities |
| `opportunities[].opportunity` | string | What the opportunity is |
| `opportunities[].rationale` | string | Why now, why this market |
| `opportunities[].effort` | string | "low", "medium", "high" |
| `opportunities[].potential_impact` | string | "low", "medium", "high" |
| `opportunities[].timeframe` | string | When to pursue |
| `strategic_recommendations` | string[] | Top 3-5 concrete next steps |

---

## source (shared type)

Used in every dimension's `sources` array.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `url` | string (URI) | Yes | Full URL |
| `title` | string | Yes | Page or article title |
| `domain` | string | No | Domain name (e.g., "statista.com") |
| `date_accessed` | string (date) | No | When the source was read |
| `date_published` | string or null | No | Publication date if available |
| `snippet` | string | No | Key excerpt or finding from this source |

---

## CMS Migration Notes

When importing into a CMS later:
- Each dimension maps to a collection (or a section within a parent `research_reports` collection)
- Array items (competitors, trends, etc.) map to related collection rows with a foreign key to the report
- The `source` type becomes a shared `research_sources` collection, linked to dimensions via junction tables
- `metadata.slug` serves as the primary key / unique identifier for the report
- All enum values use lowercase strings for consistent filtering
- Nullable fields use explicit null rather than being absent, so the CMS schema always has the column
