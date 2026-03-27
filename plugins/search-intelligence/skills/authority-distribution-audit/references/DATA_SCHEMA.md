# JSON Data Schema — Field Documentation

This document describes the JSON data model for the authority and distribution audit output.

## Top-Level Structure

```json
{
  "metadata": { ... },
  "d3_authority_distribution": { ... },
  "composite": { ... }
}
```

All sections are required. If a sub-section has no data, include it with a summary noting the gap and default scores of 0.

---

## metadata

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `slug` | string | Yes | URL-safe identifier: `{brand-slug}-authority-audit-{YYYY-MM-DD}` |
| `brand` | string | Yes | Brand or company name audited |
| `domain` | string | Yes | Primary website URL |
| `industry` | string | Yes | Industry context for the audit |
| `date_generated` | string (date) | Yes | ISO date: `YYYY-MM-DD` |
| `kb_version` | string | Yes | Version of the KB-EXTRACT used (e.g., "1.1") |
| `competitors_compared` | string[] | No | Competitor names included in comparison, or `[]` |

---

## d3_authority_distribution

The main audit payload.

| Field | Type | Description |
|-------|------|-------------|
| `score` | integer (0-100) | Composite D3 score: on-site E-E-A-T (40%) + off-site distribution (60%) |
| `on_site_eeat` | object | On-site E-E-A-T assessment |
| `off_site_distribution` | object | Off-site platform presence |
| `competitor_comparison` | array | Competitor benchmarks (empty if no competitors provided) |
| `recommendations` | string[] | Top 5-10 prioritized action items across all sub-areas |

---

## d3_authority_distribution.on_site_eeat

| Field | Type | Description |
|-------|------|-------------|
| `score` | integer (0-100) | Weighted score from all E-E-A-T signals |
| `expert_bylines` | signal_object | Named authors with credentials on content |
| `author_bios` | signal_object | Bio with role, expertise, relevant experience |
| `author_schema` | signal_object | Person schema with sameAs links |
| `publication_dates` | signal_object | Visible publish + last-updated dates |
| `source_citations` | signal_object | External authoritative sources cited inline |
| `original_contributions` | signal_object | Proprietary data, unique frameworks, first-hand experience |
| `organization_credentials` | credentials_object | About page, certifications, awards, press mentions |
| `contact_page` | signal_object | Contact information accessible |
| `privacy_terms` | signal_object | Privacy policy and terms of service present |
| `recommendations` | string[] | Specific actions to improve on-site E-E-A-T |

### signal_object

Used for binary pass/fail E-E-A-T signals.

| Field | Type | Description |
|-------|------|-------------|
| `status` | "pass" or "fail" | Whether the signal is present |
| `details` | string | Evidence and specifics of what was found or missing |

### credentials_object

Used for the Organization Credentials signal (scored, not binary).

| Field | Type | Description |
|-------|------|-------------|
| `score` | integer (0-10) | Quality score for organizational credentials |
| `details` | string | Evidence and specifics |

---

## d3_authority_distribution.off_site_distribution

| Field | Type | Description |
|-------|------|-------------|
| `score` | integer (0-100) | Weighted average of all platform scores |
| `generic_platforms` | object | Scores for each generic platform |
| `industry_specific` | array | Industry-specific sources discovered and checked |

### generic_platforms

Each platform follows the `platform_object` structure.

| Field | Type | Description |
|-------|------|-------------|
| `linkedin` | platform_object | LinkedIn company page + personnel profiles |
| `reddit` | platform_object | Reddit and forum mentions |
| `g2` | platform_object | G2 review site presence |
| `capterra` | platform_object | Capterra review site presence |
| `trustpilot` | platform_object | Trustpilot review site presence |
| `youtube` | platform_object | YouTube channel and content |
| `wikipedia` | platform_object | Wikipedia page existence and quality |
| `directories` | platform_object | Crunchbase and industry directories |
| `press_media` | platform_object | Press and media coverage |

### platform_object

| Field | Type | Description |
|-------|------|-------------|
| `present` | boolean | Whether the brand has a presence on this platform |
| `score` | integer (0-100) | Platform-specific score |
| `details` | object | Platform-specific findings (varies by platform — see below) |
| `recommendations` | string[] | Actions to improve presence on this platform |

**LinkedIn details**:
| Field | Type | Description |
|-------|------|-------------|
| `company_page` | boolean | Company page exists |
| `followers` | integer or null | Company page follower count |
| `posting_cadence` | string | Frequency description (e.g., "2-3x per week") |
| `articles_found` | integer | Number of LinkedIn articles found |
| `personnel_profiles` | array | Key person profiles checked |
| `personnel_profiles[].name` | string | Person's name |
| `personnel_profiles[].followers` | integer or null | Follower count |
| `personnel_profiles[].meets_threshold` | boolean | Whether 3,000+ follower threshold is met |
| `personnel_profiles[].articles` | integer | Number of articles found |

**Reddit details**:
| Field | Type | Description |
|-------|------|-------------|
| `mention_volume` | string | Approximate mention count or range |
| `sentiment` | string | "positive", "negative", "mixed", or "neutral" |
| `brand_participates` | boolean | Whether the brand has an official presence |
| `recent_mentions` | string | Recency description |
| `key_subreddits` | string[] | Relevant subreddits where brand appears |

**Review site details** (G2, Capterra, Trustpilot):
| Field | Type | Description |
|-------|------|-------------|
| `review_count` | integer or null | Number of reviews |
| `avg_rating` | number or null | Average rating (out of 5 or 10 depending on platform) |
| `last_review_date` | string or null | Date of most recent review |
| `brand_responds` | boolean or null | Whether brand responds to reviews |

**YouTube details**:
| Field | Type | Description |
|-------|------|-------------|
| `channel_url` | string or null | YouTube channel URL |
| `subscribers` | integer or null | Subscriber count |
| `video_count` | integer or null | Total videos |
| `upload_frequency` | string | Frequency description |
| `has_transcripts` | boolean or null | Whether videos have captions/transcripts |
| `content_types` | string[] | Types of content (tutorials, webinars, etc.) |

**Wikipedia details**:
| Field | Type | Description |
|-------|------|-------------|
| `page_url` | string or null | Wikipedia page URL |
| `quality_class` | string or null | "stub", "start", "C", "B", "GA", "FA" |
| `reference_count` | integer or null | Number of references on the page |
| `last_edited` | string or null | Last edit date |
| `notability_concerns` | boolean | Whether the page has notability flags |

**Directories details**:
| Field | Type | Description |
|-------|------|-------------|
| `crunchbase` | object | `{ "exists": bool, "completeness": string, "url": string or null }` |
| `other_directories` | array | `[{ "name": string, "url": string, "profile_status": string }]` |

**Press/Media details**:
| Field | Type | Description |
|-------|------|-------------|
| `coverage_volume` | string | Approximate article count or range |
| `most_recent` | string or null | Date of most recent coverage |
| `outlet_tiers` | object | `{ "tier_1": integer, "tier_2": integer, "tier_3": integer }` |
| `coverage_types` | string[] | Types found (product reviews, interviews, etc.) |
| `has_newsroom_page` | boolean | Whether brand has a press/newsroom page |

### industry_specific (array)

Each element represents one industry-specific source discovered and checked.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `source_name` | string | Yes | Name of the publication, directory, forum, etc. |
| `type` | string | Yes | "publication", "review_site", "forum", "directory", "podcast" |
| `url` | string | Yes | Source URL |
| `brand_present` | boolean | Yes | Whether the brand has a presence |
| `details` | string | Yes | What was found or not found |
| `recommendation` | string | Yes | Action to take |

---

## d3_authority_distribution.competitor_comparison

Array of competitor benchmarks. Empty array if no competitors were provided.

| Field | Type | Description |
|-------|------|-------------|
| `competitor` | string | Competitor name |
| `linkedin_score` | integer (0-100) or null | Estimated LinkedIn presence score |
| `review_site_score` | integer (0-100) or null | Estimated review site presence score |
| `wikipedia_present` | boolean | Whether competitor has a Wikipedia page |
| `overall_notes` | string | Summary of competitor's D3 positioning relative to audited brand |

---

## composite

Provides the D3 contribution to the overall AEO/GEO composite score.

| Field | Type | Description |
|-------|------|-------------|
| `d3_weighted` | number | D3 score multiplied by 0.25 (the D3 weight in the composite model) |
| `note` | string | Always: "D3 weight is 25% in the composite scoring model. Combine with D1 (20%), D2 (30%), and D4 (25%) for full composite." |

---

## CMS Migration Notes

When importing into a CMS later:
- `metadata.slug` serves as the primary key / unique identifier for the audit
- Platform objects within `generic_platforms` can map to related collection rows with a foreign key to the audit
- The `industry_specific` array maps to a related collection for discovered sources
- `competitor_comparison` maps to a related collection for benchmarks
- All enum values use lowercase strings for consistent filtering
- Nullable fields use explicit `null` rather than being absent, so the CMS schema always has the column
