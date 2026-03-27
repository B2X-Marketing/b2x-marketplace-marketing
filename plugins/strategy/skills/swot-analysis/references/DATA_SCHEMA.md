# SWOT Data Schema Reference

Human-readable documentation for `Strategy/Schema/swot-data-schema.json`.

## Top-Level Structure

```json
{
  "metadata": { ... },
  "strengths": [ ... ],
  "weaknesses": [ ... ],
  "opportunities": [ ... ],
  "threats": [ ... ],
  "tows": { ... },        // optional — null when tows=false
  "summary": { ... }
}
```

## metadata

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `slug` | string | Yes | URL-safe identifier: `{subject-slug}-{YYYY-MM-DD}` |
| `subject` | string | Yes | Company, product, or project analyzed |
| `scope` | enum | Yes | `business` or `marketing` |
| `date_generated` | date | Yes | ISO 8601 date (YYYY-MM-DD) |
| `mode` | enum | Yes | `interactive`, `strategy`, `standalone`, or `visual-only` |
| `author` | string | No | Person or team who ran the analysis |
| `context_source` | string | No | Path to strategy document providing Layers 1-3 context (strategy mode only) |
| `confidence_rating` | enum | No | `high`, `medium`, or `low` |

### Confidence Rating Criteria

| Rating | Meaning |
|--------|---------|
| **high** | Evidence-backed analysis with specific data points, direct observation, or verified sources |
| **medium** | Informed assessment with reasonable evidence but some gaps or assumptions |
| **low** | Preliminary or speculative — limited evidence, broad assumptions, needs validation |

## SWOT Quadrants

All four quadrants (`strengths`, `weaknesses`, `opportunities`, `threats`) use the same item schema.

### swot_item

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `title` | string | Yes | Short label, 3-8 words |
| `description` | string | Yes | Explanation of the factor and why it matters |
| `impact` | enum | Yes | `high`, `medium`, or `low` |
| `evidence` | string | No | Supporting data, examples, or reasoning |
| `category` | string | No | Optional grouping (e.g., `financial`, `operational`, `brand`, `digital`, `talent`, `technology`) |

### Impact Criteria

| Level | Meaning |
|-------|---------|
| **high** | Significant effect on strategic direction, competitive position, or financial performance |
| **medium** | Meaningful but manageable — affects operations or tactics, not fundamental direction |
| **low** | Minor or situational — worth noting but not a driver of strategy |

## tows (Optional)

Present only when `tows=true` at runtime. Contains four strategy arrays derived from quadrant intersections.

| Field | Type | Description |
|-------|------|-------------|
| `so_strategies` | tows_action[] | Strength × Opportunity — leverage strengths to seize opportunities |
| `wo_strategies` | tows_action[] | Weakness × Opportunity — address weaknesses to unlock opportunities |
| `st_strategies` | tows_action[] | Strength × Threat — use strengths to defend against threats |
| `wt_strategies` | tows_action[] | Weakness × Threat — minimize weaknesses and avoid threats |

### tows_action

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `action` | string | Yes | Specific strategic action to take |
| `rationale` | string | Yes | Which SWOT factors this action addresses and why |
| `priority` | enum | No | `high`, `medium`, or `low` |
| `timeframe` | string | No | Suggested timeline (e.g., `immediate`, `30 days`, `Q2 2026`) |

## summary

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `key_insight` | string | Yes | Single most important finding from the analysis |
| `strategic_implication` | string | Yes | What this SWOT means for the organization's direction |
| `recommended_priorities` | string[] | No | Top 3-5 prioritized actions based on the analysis |

## Scope Differences

The `scope` field determines the lens of the analysis:

| Aspect | `business` | `marketing` |
|--------|-----------|-------------|
| Strengths focus | Operations, talent, IP, financials, market position | Brand equity, channels, content, audience, creative |
| Weaknesses focus | Organizational gaps, resource limits, process issues | Messaging gaps, channel underperformance, positioning holes |
| Opportunities focus | Market expansion, partnerships, M&A, product innovation | New audiences, platform shifts, content trends, competitive white space |
| Threats focus | Competitive disruption, regulatory, macro-economic | Share of voice decline, algorithm changes, competitor messaging, channel saturation |

## CMS Migration Notes

When migrating to a CMS:
- `metadata` maps to a top-level record with relationships to quadrant items
- Each `swot_item` becomes a record in a shared SWOT items collection, linked by quadrant type (`strength`, `weakness`, `opportunity`, `threat`)
- `tows` actions link back to their source SWOT items
- `summary` fields can be stored directly on the parent record
- `slug` serves as a unique lookup key
