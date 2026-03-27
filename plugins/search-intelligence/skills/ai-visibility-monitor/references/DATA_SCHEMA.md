# AI Visibility Monitor — Data Schema

Documentation of the JSON output schema, prompt library schema, drift analysis structure, and CSV schemas for Looker Studio integration.

---

## 1. data.json — Full Output Schema

```json
{
  "metadata": {
    "brand": "string — brand name",
    "brand_slug": "string — lowercase hyphenated brand name",
    "industry": "string — industry or market",
    "mode": "string — 'snapshot' or 'monitor'",
    "date_generated": "string — YYYY-MM-DD",
    "platforms_tested": ["string — e.g., 'chatgpt', 'perplexity', 'gemini', 'claude'"],
    "competitors_tracked": ["string — competitor brand names"],
    "total_prompts": "integer — number of prompts in library",
    "prompts_by_intent": {
      "informational": "integer",
      "comparative": "integer",
      "recommendation": "integer",
      "problem_solving": "integer",
      "branded": "integer"
    },
    "previous_run_date": "string | null — YYYY-MM-DD of previous run for drift comparison",
    "output_slug": "string — directory name for this run",
    "skill_version": "string — 1.0.0",
    "kb_version": "string — 1.1"
  },

  "platform_scores": {
    "{platform}": {
      "brand_recognition": {
        "score": "number — 0-20",
        "recognition_score_100": "number — 0-100, overall digital visibility",
        "market_position": "string — Niche | Emerging | Established | Leader",
        "brand_archetype": "string — Traditionalist | Innovator | Disruptor | etc.",
        "confidence_level": "number — 0-100, how confident AI is in its info",
        "mention_depth": "number — 0-10",
        "source_quality": "number — 0-10",
        "data_richness": "number — 0-10"
      },
      "market_position": {
        "score": "number — 0-10",
        "share_of_voice_pct": "number — 0-100",
        "comparison_mentions": "integer — count of comparative contexts",
        "position_classification": "string — Niche | Emerging | Established | Leader",
        "top_competitors": [
          {
            "name": "string",
            "share_of_voice_pct": "number",
            "mention_count": "integer"
          }
        ]
      },
      "presence_quality": {
        "score": "number — 0-20",
        "context_quality": "number — 0-5",
        "description_depth": "number — 0-5",
        "accuracy": "number — 0-5",
        "consistency": "number — 0-5"
      },
      "brand_sentiment": {
        "score": "number — 0-40",
        "general_sentiment_100": "number — 0-100",
        "source_based_sentiment_100": "number — 0-100",
        "contextual_sentiment_100": "number — 0-100",
        "polarization_100": "number — 0-100, low = consistent, high = controversial"
      },
      "composite_score": "number — 0-90 (sum of recognition + position + quality + sentiment)",
      "mention_rate_pct": "number — % of prompts with brand mention",
      "citation_rate_pct": "number — % of prompts with brand citation/link",
      "prompts_with_mention": "integer",
      "prompts_with_citation": "integer"
    }
  },

  "qualitative": {
    "narrative_themes": [
      {
        "theme": "string — recurring theme description",
        "frequency": "string — how often it appears: high | medium | low",
        "platforms": ["string — which platforms surface this theme"],
        "example_prompt": "string — example prompt that triggered it"
      }
    ],
    "key_strengths": [
      {
        "strength": "string",
        "evidence": "string — specific prompt/response evidence",
        "platforms": ["string"]
      }
    ],
    "growth_areas": [
      {
        "area": "string",
        "evidence": "string",
        "recommendation": "string — mapped to D1/D2/D3 action"
      }
    ],
    "market_trajectory": "string — how AI perceives the brand's momentum",
    "common_comparisons": [
      {
        "competitor": "string",
        "dimensions": ["string — what dimensions they're compared on"],
        "brand_advantage": "string | null",
        "competitor_advantage": "string | null"
      }
    ]
  },

  "prompt_results": [
    {
      "prompt_id": "string — P001, P002, etc.",
      "prompt_text": "string — the actual prompt",
      "intent": "string — informational | comparative | recommendation | problem_solving | branded",
      "topic": "string — topic category",
      "platforms": {
        "{platform}": {
          "brand_mentioned": "boolean",
          "brand_cited": "boolean",
          "citation_url": "string | null",
          "mention_position": "string — first | middle | last | not_mentioned",
          "sentiment": "string — positive | neutral | negative",
          "sentiment_score": "number — -1.0 to 1.0",
          "competitors_mentioned": ["string"],
          "recognition_score": "number — 0-20",
          "presence_quality_score": "number — 0-20",
          "accuracy": "string — accurate | partially_accurate | inaccurate | not_applicable",
          "sources_cited": ["string — domain names or URLs"],
          "raw_response_excerpt": "string — relevant excerpt from AI response",
          "data_source": "string — path_a (WebSearch/WebFetch) | path_b (external runner)"
        }
      }
    }
  ],

  "drift_analysis": {
    "has_previous_run": "boolean",
    "previous_run_date": "string | null — YYYY-MM-DD",
    "current_run_date": "string — YYYY-MM-DD",
    "overall": {
      "citation_drift_rate_pct": "number — % of prompts where citation status changed",
      "mention_drift_rate_pct": "number — % of prompts where mention status changed"
    },
    "per_platform": {
      "{platform}": {
        "composite_score_delta": "number — current minus previous",
        "brand_recognition_delta": "number",
        "market_position_delta": "number",
        "presence_quality_delta": "number",
        "brand_sentiment_delta": "number",
        "mention_rate_delta_pct": "number",
        "citation_rate_delta_pct": "number",
        "share_of_voice_delta_pct": "number"
      }
    },
    "flags": [
      {
        "type": "string — improvement | decline | new_competitor | sentiment_shift | lost_citation | gained_citation",
        "platform": "string",
        "prompt_id": "string | null",
        "description": "string — human-readable description of the change",
        "previous_value": "string | number | null",
        "current_value": "string | number | null"
      }
    ],
    "prompt_level_changes": [
      {
        "prompt_id": "string",
        "platform": "string",
        "field": "string — which field changed",
        "previous": "string | number | boolean",
        "current": "string | number | boolean"
      }
    ]
  },

  "build_vs_buy": {
    "recommendation": "string — summary recommendation",
    "this_skill_cost": "string — $4-10/run",
    "alternatives": [
      {
        "tool": "string",
        "price_range": "string",
        "best_for": "string"
      }
    ]
  },

  "cross_references": {
    "d1_site_audit_path": "string | null — path to most recent D1+D2 audit data.json",
    "d3_authority_audit_path": "string | null — path to most recent D3 audit data.json",
    "market_research_path": "string | null — path to most recent research data.json",
    "strategy_path": "string | null — path to most recent strategy output"
  }
}
```

---

## 2. prompt-library.json — Prompt Library Schema

```json
{
  "metadata": {
    "brand": "string",
    "industry": "string",
    "competitors": ["string"],
    "date_created": "string — YYYY-MM-DD",
    "total_prompts": "integer",
    "generated_from": "string — auto | manual | hybrid"
  },
  "prompts": [
    {
      "id": "string — P001, P002, etc.",
      "text": "string — the full conversational prompt",
      "intent": "string — informational | comparative | recommendation | problem_solving | branded",
      "topic": "string — topic category",
      "includes_brand": "boolean — whether the prompt explicitly names the brand",
      "includes_competitor": "boolean",
      "competitor_name": "string | null",
      "template_source": "string | null — template ID from PROMPT_TEMPLATES.md if auto-generated"
    }
  ]
}
```

---

## 3. prompt-results.csv — Looker Studio Per-Prompt Data

One row per prompt x platform combination.

| Column | Type | Description |
|--------|------|-------------|
| date | string (YYYY-MM-DD) | Run date |
| brand | string | Brand name |
| platform | string | AI platform (chatgpt, perplexity, gemini, claude) |
| prompt_id | string | Prompt identifier (P001, P002, etc.) |
| prompt_text | string | Full prompt text |
| intent | string | informational, comparative, recommendation, problem_solving, branded |
| topic | string | Topic category |
| brand_mentioned | boolean | Whether brand was mentioned in response |
| brand_cited | boolean | Whether brand was cited with a link |
| citation_url | string | URL if cited, empty otherwise |
| mention_position | string | first, middle, last, not_mentioned |
| sentiment | string | positive, neutral, negative |
| sentiment_score | float | -1.0 to 1.0 |
| competitors_mentioned | string | Semicolon-separated list of competitor names |
| recognition_score | integer | 0-20 |
| presence_quality_score | integer | 0-20 |
| accuracy | string | accurate, partially_accurate, inaccurate, not_applicable |
| sources_cited | string | Semicolon-separated list of domains/URLs |

**Monitor mode behavior**: Each run appends new rows with the current date. The `date` column enables time-series filtering in Looker Studio.

---

## 4. summary-scores.csv — Looker Studio Per-Platform Dashboard Data

One row per platform per run.

| Column | Type | Description |
|--------|------|-------------|
| date | string (YYYY-MM-DD) | Run date |
| brand | string | Brand name |
| platform | string | AI platform |
| brand_recognition | integer | Score out of 20 |
| market_position | integer | Score out of 10 |
| presence_quality | integer | Score out of 20 |
| brand_sentiment | integer | Score out of 40 |
| composite_score | integer | Score out of 90 (sum of above) |
| prompts_with_mention | integer | Count of prompts where brand was mentioned |
| prompts_with_citation | integer | Count of prompts where brand was cited |
| total_prompts | integer | Total prompts tested |
| mention_rate | float | Percentage (0-100) |
| citation_rate | float | Percentage (0-100) |
| share_of_voice | float | Percentage (0-100) |
| top_competitor | string | Competitor with highest share of voice |
| top_competitor_sov | float | Top competitor's share of voice percentage |

**Monitor mode behavior**: Each run appends new rows with the current date, building a time series for trend visualization in Looker Studio.

---

## 5. Scoring Formulas

### Composite Score (per platform)

```
Composite = Brand Recognition (/20) + Market Position (/10) + Presence Quality (/20) + Brand Sentiment (/40)
Max = 90
```

### Mention Rate

```
Mention Rate = (prompts_with_mention / total_prompts) * 100
```

### Citation Rate

```
Citation Rate = (prompts_with_citation / total_prompts) * 100
```

### Share of Voice

```
Brand SOV = (brand_mention_count / total_brand_mentions_all_brands) * 100
```

Where `total_brand_mentions_all_brands` includes the target brand plus all tracked competitors across all prompts for that platform.

### Citation Drift Rate (monitor mode)

```
Citation Drift Rate = (prompts_with_changed_citation_status / total_prompts) * 100
```

### Four-Dimension Composite (when D1-D3 data available)

```
Full AEO Score = (D1 * 0.20) + (D2 * 0.30) + (D3 * 0.25) + (D4 * 0.25)
```

Each dimension normalized to 0-100 before weighting.
