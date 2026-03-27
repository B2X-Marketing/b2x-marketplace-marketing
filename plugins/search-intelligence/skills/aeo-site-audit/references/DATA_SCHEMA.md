# JSON Data Schema — Field Documentation

This document describes the JSON data model for AEO site audit output.

## Top-Level Structure

```json
{
  "metadata": { ... },
  "d1_technical": { ... },
  "d2_citation_readiness": { ... },
  "seo_baseline": { ... },
  "composite": { ... }
}
```

All top-level keys are required. If a section has no data, include it with a summary noting the gap.

---

## metadata

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `slug` | string | Yes | Output folder name: `{domain-slug}-site-audit-{YYYY-MM-DD}` |
| `domain` | string | Yes | Domain audited (e.g., "example.com") |
| `brand` | string or null | No | Brand name if provided or inferred |
| `industry` | string or null | No | Industry if provided (used for traffic impact data) |
| `date_generated` | string (date) | Yes | ISO date: `YYYY-MM-DD` |
| `kb_version` | string | Yes | Version of KB-EXTRACT.md used (e.g., "1.1") |
| `pages_audited` | integer | Yes | Number of pages scored for D2 |

---

## d1_technical

| Field | Type | Description |
|-------|------|-------------|
| `score` | integer (0-100) | Overall D1 score |
| `critical_gate_passed` | boolean | Whether all critical items passed (false = score capped at 40) |
| `crawler_access` | object | Per-bot access results |
| `crawler_access.{bot_name}` | string | `"allow"`, `"disallow"`, or `"not_mentioned"` for each bot |
| `schema_markup` | object | Schema findings |
| `schema_markup.types_found` | string[] | Schema types detected (e.g., `["Article", "Organization"]`) |
| `schema_markup.score` | integer (0-10) | Schema coverage and appropriateness score |
| `schema_markup.details` | string | Summary of schema findings |
| `semantic_html` | object | Semantic HTML findings |
| `semantic_html.elements_found` | string[] | Semantic elements detected (e.g., `["article", "section", "header"]`) |
| `semantic_html.score` | integer (0-10) | Semantic HTML usage score |
| `semantic_html.details` | string | Summary of semantic HTML findings |
| `performance` | object | Performance-related checks |
| `performance.https` | boolean | Whether the site uses HTTPS |
| `performance.mobile_viewport` | boolean | Whether viewport meta tag is present |
| `performance.page_speed_note` | string | Limitation note — recommend PageSpeed Insights |
| `supplementary` | object | Nice-to-have items |
| `supplementary.llms_txt` | string | `"present"` or `"absent"` |
| `supplementary.llms_txt_summary` | string or null | Brief summary of llms.txt contents if present |
| `supplementary.sitemap` | string | `"present"` or `"absent"` |
| `supplementary.sitemap_url_count` | integer or null | Number of URLs in sitemap if present |
| `blockers` | string[] | Critical issues that cap the D1 score |
| `recommendations` | string[] | Prioritized list of D1 improvements |

### crawler_access bot names

The following bots are checked:
- `GPTBot`
- `ClaudeBot`
- `PerplexityBot`
- `GoogleOther`
- `Google-Extended`
- `Amazonbot`
- `anthropic-ai`
- `Bytespider`
- `cohere-ai`

---

## d2_citation_readiness

| Field | Type | Description |
|-------|------|-------------|
| `site_average_score` | number | Average score across all audited pages (0-31 scale) |
| `site_assessment` | string | `"Publish Ready"`, `"Revise"`, `"Rework"`, or `"Restructure"` |
| `pages` | array | Per-page scoring results |

### pages[]

| Field | Type | Description |
|-------|------|-------------|
| `url` | string | Full URL of the audited page |
| `page_type` | string | `"Category Explainer"`, `"Product/Feature"`, `"Comparison"`, `"Use Case"`, or `"Blog/Article"` |
| `score` | integer (0-31) | Total citation readiness score |
| `assessment` | string | `"Publish Ready"`, `"Revise"`, `"Rework"`, or `"Restructure"` |
| `sections` | object | Per-section breakdown |
| `recommendations` | string[] | Specific improvements for this page |

### pages[].sections

| Field | Type | Description |
|-------|------|-------------|
| `opening_structure` | section_detail | Section A scoring (/5) |
| `topical_completeness` | section_detail | Section B scoring (/6) |
| `entity_authority` | section_detail | Section C scoring (/5) |
| `technical_accessibility` | section_detail | Section D scoring (/6) |
| `content_formatting` | section_detail | Section E scoring (/5) |
| `distribution_monitoring` | section_detail | Section F scoring (/4) |

### section_detail (shared type)

| Field | Type | Description |
|-------|------|-------------|
| `score` | integer | Section score (out of section max) |
| `max` | integer | Maximum possible score for this section |
| `items` | array | Individual item results |

### section_detail.items[]

| Field | Type | Description |
|-------|------|-------------|
| `item_number` | integer (1-31) | Checklist item number |
| `item_name` | string | Short name of the checklist item |
| `score` | integer (0 or 1) | 1 = present, 0 = absent |
| `note` | string | Brief explanation of the assessment |

---

## seo_baseline

| Field | Type | Description |
|-------|------|-------------|
| `indexed_pages` | string | Approximate indexed page count from `site:` query (e.g., "~1,200") |
| `organic_presence_notes` | string[] | Observations about the site's organic search presence |
| `limitation_note` | string | Always include: "Directional check only. Use Ahrefs/Semrush for comprehensive SEO analysis." |

---

## composite

| Field | Type | Description |
|-------|------|-------------|
| `d1_weighted` | number | D1 score * 0.20 |
| `d2_weighted` | number | (D2 site average / 31 * 100) * 0.30 |
| `partial_total` | number | d1_weighted + d2_weighted |
| `note` | string | Always include: "Partial composite (D1 + D2 only). Run authority-distribution-audit (D3) and ai-visibility-monitor (D4) for the full score." |

---

## Assessment Thresholds

### D1 Technical Infrastructure (0-100)
| Score | Assessment |
|-------|-----------|
| 80-100 | Strong technical foundation |
| 60-79 | Moderate — some gaps to address |
| 40-59 | Weak — critical items may be failing |
| Below 40 | Critical blockers present |

### D2 Citation Readiness (0-31 per page)
| Score | Assessment |
|-------|-----------|
| 28-31 | Publish Ready |
| 22-27 | Revise |
| 15-21 | Rework |
| Below 15 | Restructure |

### Composite Weights
| Dimension | Weight |
|-----------|--------|
| D1: Technical Infrastructure | 20% |
| D2: Citation Readiness | 30% |
| D3: Authority & Distribution | 25% (not measured by this skill) |
| D4: AI Visibility | 25% (not measured by this skill) |
