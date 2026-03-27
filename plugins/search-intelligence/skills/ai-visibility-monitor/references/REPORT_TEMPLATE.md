# AI Visibility Monitor — Report Template

Use this template to generate the `report.md` output file.

---

```markdown
# AI Visibility Report: {Brand Name}

**Date**: {YYYY-MM-DD}
**Mode**: {Snapshot | Monitor}
**Platforms Tested**: {ChatGPT, Perplexity, Gemini, Claude}
**Prompts Tested**: {count}
**Competitors Tracked**: {competitor list}

---

## 1. Executive Summary

{2-3 paragraphs summarizing:
- Overall AI visibility posture across platforms
- Composite score per platform (out of 90)
- Share of voice vs top competitor
- Key finding or insight
- If monitor mode: most significant drift finding
- Bottom line: is the brand visible, invisible, or partially visible in AI?}

---

## 2. Methodology

### Platforms Tested
{List each platform and how data was collected}

| Platform | Data Collection Method | Prompts Run |
|----------|----------------------|-------------|
| Perplexity | Path A — WebSearch + WebFetch | {count} |
| Google AI Overviews | Path A — WebSearch | {count} |
| ChatGPT | Path B — External Runner (OpenAI API) | {count} |
| Gemini | Path B — External Runner (Google API) | {count} |
| Claude | {method} | {count} |

### Prompt Library Overview
- Total prompts: {count}
- Informational: {count}
- Comparative: {count}
- Recommendation: {count}
- Problem-solving: {count}
- Branded: {count}

### Data Collection Notes
{Any limitations, failed queries, partial data, runner issues}

---

## 3. Per-Platform Results

### 3.1 {Platform Name}

**Composite Score: {score}/90**

| Metric | Score | Assessment |
|--------|-------|------------|
| Brand Recognition | {score}/20 | {one-line assessment} |
| Market Position | {score}/10 | {one-line assessment} |
| Presence Quality | {score}/20 | {one-line assessment} |
| Brand Sentiment | {score}/40 | {one-line assessment} |

**Mention Rate**: {X}% ({count}/{total} prompts)
**Citation Rate**: {X}% ({count}/{total} prompts)

**Key Findings**:
- {Finding 1 with specific prompt evidence}
- {Finding 2}
- {Finding 3}

{Repeat section 3.1 for each platform}

---

## 4. Share of Voice Analysis

| Brand | Mention Count | Share of Voice | Citation Count | Citation Rate |
|-------|--------------|----------------|----------------|---------------|
| {Brand} | {count} | {X}% | {count} | {X}% |
| {Competitor 1} | {count} | {X}% | {count} | {X}% |
| {Competitor 2} | {count} | {X}% | {count} | {X}% |

**Cross-platform SOV**:
{Summary of how SOV differs across platforms — e.g., strong on Perplexity, weak on ChatGPT}

---

## 5. Qualitative Findings

### Narrative Themes
{What recurring themes does AI associate with the brand?}

| Theme | Frequency | Platforms |
|-------|-----------|-----------|
| {theme} | {high/medium/low} | {platforms} |

### Key Strengths Identified by AI
{What does AI consistently identify as the brand's advantages?}

1. {Strength with evidence}
2. {Strength with evidence}

### Growth Areas
{Where does AI see gaps or room for improvement?}

1. {Area with evidence and D1/D2/D3 mapping}
2. {Area with evidence and D1/D2/D3 mapping}

### Common Comparisons
{Which competitors is the brand compared to, and on what dimensions?}

---

## 6. Drift Analysis

{MONITOR MODE ONLY — omit this section for snapshot mode}

### Score Changes Since {previous_date}

| Platform | Previous | Current | Delta | Direction |
|----------|----------|---------|-------|-----------|
| {platform} | {score}/90 | {score}/90 | {+/-X} | {up/down/stable} |

### Citation Drift
- Citation drift rate: {X}% of prompts changed citation status
- Gained citations: {count} prompts
- Lost citations: {count} prompts

### Significant Changes
{List flagged improvements, declines, new competitor appearances, sentiment shifts}

| Change Type | Platform | Description |
|-------------|----------|-------------|
| {type} | {platform} | {description} |

### Trend Assessment
{Overall trajectory assessment — improving, declining, or stable?}

---

## 7. Recommendations

{Actionable recommendations mapped to D1/D2/D3 root causes}

### Priority 1: {Recommendation}
- **Finding**: {What the D4 data shows}
- **Root Cause (D{X})**: {What's causing it}
- **Action**: {Specific action to take}
- **Expected Impact**: {What improvement to expect}

### Priority 2: {Recommendation}
{Same structure}

### Priority 3: {Recommendation}
{Same structure}

### Next Steps
- {Recommended follow-up action 1}
- {Recommended follow-up action 2}
- {Recommended cadence for next run}

---

## 8. Build vs Buy Analysis

This report was generated using the B2X AI Visibility Monitor skill at an estimated cost of $4-10 per run (API costs for WebSearch/WebFetch plus external runner API calls).

### When This Skill Is the Right Choice
- Monitoring 1-2 brands
- Monthly or quarterly cadence
- Need to integrate D4 results with D1-D3 diagnosis
- Budget-conscious operations

### When to Consider a Dedicated Tool

| Tool | Price Range | Best For |
|------|------------|----------|
| Otterly AI | $50-200/mo | SMB, lightweight, quick setup |
| Peec AI | $50-150/mo | Real-time, region-specific |
| Profound | $500-1,000+/mo | Enterprise, multi-region, SOC 2 |

See `AEO-BUILD-VS-BUY.md` for the full analysis.

---

## Appendix A: Full Prompt Library with Results

### Informational Prompts

| ID | Prompt | {Platform 1} | {Platform 2} | {Platform 3} |
|----|--------|-------------|-------------|-------------|
| P001 | {prompt text} | {mentioned/cited/not_mentioned} | {result} | {result} |

{Repeat table for each intent type: Comparative, Recommendation, Problem-solving, Branded}

---

## Appendix B: CSV Schema Reference

This report is accompanied by two CSV files for Looker Studio integration.

### prompt-results.csv
One row per prompt x platform. Columns: date, brand, platform, prompt_id, prompt_text, intent, topic, brand_mentioned, brand_cited, citation_url, mention_position, sentiment, sentiment_score, competitors_mentioned, recognition_score, presence_quality_score, accuracy, sources_cited

### summary-scores.csv
One row per platform per run. Columns: date, brand, platform, brand_recognition, market_position, presence_quality, brand_sentiment, composite_score, prompts_with_mention, prompts_with_citation, total_prompts, mention_rate, citation_rate, share_of_voice, top_competitor, top_competitor_sov

In monitor mode, each run appends new date-stamped rows to build a time series.

See `references/DATA_SCHEMA.md` for full field documentation.
```
