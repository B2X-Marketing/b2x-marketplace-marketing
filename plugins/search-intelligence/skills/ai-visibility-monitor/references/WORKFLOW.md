# AI Visibility Monitor — Detailed Workflow

This document contains the full execution instructions for the ai-visibility-monitor skill. The skill's SKILL.md loads this on-demand when executing.

## When to Use This Skill

Use this skill when:
- The user says "AI visibility check", "are we being cited by AI", "prompt tracking", "share of voice in AI", "AI monitor", "D4 audit", "snapshot", or "run the visibility monitor"
- The user wants to know how a brand appears in AI-generated answers
- The user wants to track changes in AI visibility over time (monitor mode)
- The user needs Looker Studio-compatible CSV data for AI visibility reporting

## Customer Data Convention

The folder the user opened in Cowork IS the customer data directory (`./`).

- **Output**: `./aeo-output/{brand-slug}-ai-visibility-{YYYY-MM-DD}/`
- **Voice profile**: `./voice-profiles/{client-slug}.md`
- **Strategy output**: `./strategy-output/` (consumed for topic extraction)
- **Research output**: `./research-output/` (consumed for competitor/topic extraction)

If the output directory already exists, append a sequence number: `-2`, `-3`, etc.

## KB Version Check

Before starting, read `references/KB-EXTRACT.md` for the bundled knowledge base extract. Then check if `../../AEO-GEO-KNOWLEDGE-BASE.md` exists and read its Version field. If the KB version is newer than the extract version (1.1), warn the user:

> "The AEO/GEO Knowledge Base (v{new}) is newer than this skill's extract (v1.1). Some scoring criteria or platform behaviors may have changed. Consider updating the skill's KB extract."

## Architecture — Hybrid Approach

This skill uses two paths to gather data across AI platforms.

### Path A — Inside Claude Code (Perplexity + Google AI Overviews)

Run prompts as WebSearch queries and analyze results:
1. Use WebSearch to execute each prompt from the prompt library
2. Analyze search results for AI-generated snippets, brand mentions, and citations
3. Use WebFetch on Perplexity result pages for citation analysis
4. Record: brand mentioned (bool), brand cited (bool), citation URL, mention position, sentiment, competitors mentioned, sources cited

### Path B — External Runner (ChatGPT + Gemini)

A Python script (`tools/aeo-runner/aeo-runner.py`) calls OpenAI and Gemini APIs directly:
1. Takes `prompt-library.json` as input
2. Outputs `runner-results.json` with structured per-prompt results
3. User runs it locally with their own API keys
4. This skill reads the output and scores it

The skill checks for runner output at `./aeo-output/runner-results-{date}.json`. If not found, it instructs the user to run the external script and pauses.

## Workflow

Follow these steps in order. Do not skip steps.

### Step 1: Validate Inputs and Setup

1. Confirm brand name, industry, and mode are provided. If missing, ask the user.
2. Generate the brand slug: lowercase, replace spaces with hyphens, strip special characters.
3. Generate the output slug: `{brand-slug}-ai-visibility-{YYYY-MM-DD}`
4. Check KB version (see KB Version Check above).
5. Create the output directory:
```bash
mkdir -p "./aeo-output/{slug}"
```
6. **Monitor mode**: Check for previous runs in `./aeo-output/`. If found, load the most recent `data.json` for drift comparison. If not found, inform the user this will serve as the baseline run.

### Step 2: Build Prompt Library

Auto-generate 20-30 prompts from brand + industry + competitors, organized by intent type:

**Intent types** (see `references/PROMPT_TEMPLATES.md` for templates):
- **Informational** (5-7 prompts): "What is...", "How does... work", "Explain..."
- **Comparative** (5-7 prompts): "Compare X vs Y", "What's the difference between...", "Best X for Y"
- **Recommendation** (4-5 prompts): "What tools should I use for...", "Recommend a..."
- **Problem-solving** (3-5 prompts): "How do I solve...", "What's the best approach to..."
- **Branded** (4-5 prompts): "What does {brand} do?", "Is {brand} good for...", "{brand} vs {competitor}"

**Topic extraction**: If marketing-strategy or market-research output exists in the customer directory, read it and extract:
- Key topics and themes from strategy documents
- Competitors identified in research
- Industry-specific terminology and use cases

Present the generated prompt library to the user for review. Allow additions, removals, and edits.

Save as `prompt-library.json` in the output directory.

### Step 3: Execute Path A (Perplexity + Google)

For each prompt in the library:
1. Run as a WebSearch query
2. Analyze results for:
   - AI-generated snippets containing brand mentions
   - Citation URLs pointing to the brand's domain
   - Competitor mentions in the same results
   - Sentiment of how the brand is described
   - Position of brand mention (first, middle, last, not mentioned)
3. Use WebFetch on promising result pages for deeper citation analysis
4. Record all findings in the structured format per `references/DATA_SCHEMA.md`

### Step 4: Execute Path B (ChatGPT + Gemini)

1. Check if external runner output exists at `./aeo-output/{slug}/runner-results.json`
2. If **not found**, instruct the user:

> To get ChatGPT and Gemini results, run the external runner:
> ```
> python tools/aeo-runner/aeo-runner.py \
>   --prompts ./aeo-output/{slug}/prompt-library.json \
>   --output ./aeo-output/{slug}/runner-results.json
> ```
> This requires API keys. Set up `~/.b2x/default-config.json` or per-customer `./aeo-output/.runner-config.json` (see `tools/aeo-runner/README.md`).
> Let me know when it's done and I'll continue.

3. If **found**, read and parse `runner-results.json`
4. Validate the structure matches expected schema

### Step 5: Score Results

Score each platform separately using the D4 sub-metrics:

**Brand Recognition (/20)**:
- Mention depth: How detailed are mentions? (surface name-drop vs in-depth description)
- Source quality: Quality of sources AI draws from when discussing the brand
- Data richness: Volume and variety of data available to AI about the brand
- Confidence level: How confident the AI appears in its information

**Market Position (/10)**:
- Share of voice: % of prompts mentioning the brand vs competitors
- Comparison mentions: How often the brand appears in comparative contexts
- Market position classification: Niche / Emerging / Established / Leader

**Presence Quality (/20)**:
- Context quality: Is the brand mentioned in relevant, accurate context?
- Description depth: Surface mention vs detailed feature/benefit description
- Accuracy: Are AI statements about the brand factually correct?
- Consistency: Does the brand description stay consistent across prompts?

**Brand Sentiment (/40)**:
- General sentiment: Overall positive/neutral/negative tone
- Source-based sentiment: Sentiment from specific data sources (reviews, media)
- Contextual sentiment: Industry-specific perception factors
- Polarization: Degree of opinion division (low = consistent, high = controversial)

**Qualitative outputs**:
- Narrative themes: Recurring themes AI associates with the brand
- Key strengths: What AI identifies as advantages
- Growth areas: Opportunities AI surfaces
- Common comparisons: Which competitors and on what dimensions

### Step 6: Drift Analysis (Monitor Mode Only)

If previous run data exists:
1. Load previous `data.json`
2. Compare per-prompt scores across platforms
3. Calculate:
   - **Citation drift rate**: % of prompts where citation status changed
   - **Score delta**: Change in composite score per platform
   - **Mention rate change**: Change in % of prompts with brand mention
   - **Citation rate change**: Change in % of prompts with brand citation
4. Flag:
   - Improvements (score increases > 5 points)
   - Declines (score decreases > 5 points)
   - New competitor appearances
   - Sentiment shifts (positive to negative or vice versa)
   - Lost citations (previously cited, now not)
   - Gained citations (previously not cited, now cited)

### Step 7: Assemble Outputs

Generate all output files in the output directory:

```
./aeo-output/{slug}/
  report.md                — Human-readable markdown report (see references/REPORT_TEMPLATE.md)
  data.json                — Full structured data (see references/DATA_SCHEMA.md)
  prompt-library.json      — Reusable prompt library for future runs
  prompt-results.csv       — Looker Studio: raw per-prompt x per-platform data
  summary-scores.csv       — Looker Studio: per-platform per-run dashboard data
```

**Looker Studio CSV — prompt-results.csv** (one row per prompt x platform):

Columns: `date`, `brand`, `platform`, `prompt_id`, `prompt_text`, `intent`, `topic`, `brand_mentioned`, `brand_cited`, `citation_url`, `mention_position`, `sentiment`, `sentiment_score`, `competitors_mentioned`, `recognition_score`, `presence_quality_score`, `accuracy`, `sources_cited`

**Looker Studio CSV — summary-scores.csv** (one row per platform per run):

Columns: `date`, `brand`, `platform`, `brand_recognition`, `market_position`, `presence_quality`, `brand_sentiment`, `composite_score`, `prompts_with_mention`, `prompts_with_citation`, `total_prompts`, `mention_rate`, `citation_rate`, `share_of_voice`, `top_competitor`, `top_competitor_sov`

**Monitor mode**: Each run APPENDS new date-stamped rows to both CSVs, building a time series for Looker Studio visualization. The skill does NOT publish to Looker Studio — that is the job of a separate reporting pipeline.

### Step 8: Report to User

Provide a brief summary:
- Brand and platforms assessed
- Mode used (snapshot or monitor)
- Composite score per platform (out of 90)
- Top finding per platform
- Share of voice vs top competitor
- If monitor mode: key drift findings
- Output file paths
- Suggest next steps (e.g., "Run aeo-site-audit to diagnose D1/D2 causes" or "Schedule monthly monitor runs")

## Build vs Buy Note

Include in every report a section recommending when to use this skill vs market tools:

| Approach | Cost | Best For |
|----------|------|----------|
| This skill | $4-10/run (API costs) | 1-2 brands, monthly cadence, unique D1-D3 diagnosis integration |
| Otterly AI | $50-200/mo | SMB, lightweight tracking, quick setup |
| Peec AI | $50-150/mo | Real-time reporting, region-specific tracking |
| Profound | $500-1,000+/mo | Enterprise, multi-region, SOC 2, deep analytics |

Point to `references/TOOLS_COMPARISON.md` for the full analysis. Point to `AEO-BUILD-VS-BUY.md` for the complete build vs buy framework.

## Quality Standards

A good AI visibility report:
- Covers all requested platforms with per-platform scoring
- Uses 20-30 prompts covering all 5 intent types
- Every score has supporting evidence from actual prompt results
- Share of voice calculations include at least the top 3 competitors
- Sentiment analysis distinguishes between positive, neutral, and negative with specific examples
- Monitor mode shows clear before/after comparisons with drift rates
- CSV output validates against the schema (correct column count, proper data types)
- Recommendations map to specific D1/D2/D3 causes

## Error Handling

- **WebSearch returns no AI snippets**: Record as "not mentioned" for that prompt/platform. Do not fabricate results.
- **WebFetch fails**: Skip the URL, note in data. Do not retry more than once.
- **Runner results missing**: Pause and instruct user. Do not proceed without the data — score only Path A platforms and note incomplete coverage.
- **Runner results malformed**: Report the parsing error, ask user to re-run the script.
- **Previous run not found (monitor mode)**: Proceed as baseline snapshot. Note in report that drift analysis will be available after the next run.
- **Too few prompts for statistical significance**: Warn in report that results may not be representative. Recommend expanding the prompt library.

## Voice and Tone

Follow the client's voice profile from `./voice-profiles/`. Fall back to default:
- Active voice, lead with the point
- No "delve", no filler transitions, no excessive em dashes
- Numbers as digits
- Short, direct sentences
- Present data confidently but flag uncertainty honestly

## Cross-References

This skill consumes output from other skills to explain WHY D4 scores are what they are:

- **aeo-site-audit** (D1 + D2): If technical infrastructure is blocking crawlers or content isn't structured for extraction, D4 will be low regardless of brand strength. Check `./aeo-output/*site-audit*/data.json`.
- **authority-distribution-audit** (D3): If off-site presence is weak, AI lacks consensus signals to cite the brand. Check `./aeo-output/*authority*/data.json`.
- **market-research**: Competitors and industry topics feed prompt library generation. Check `./research-output/*/data.json`.
- **marketing-strategy**: Strategic positioning informs which narratives to track. Check `./strategy-output/*/`.

When D4 scores are low, reference D1-D3 findings in the recommendations section to give the user a clear path to improvement.

## References

- `KB-EXTRACT.md` — Knowledge base extract (D4, prompt tracking, platform behavior, statistics)
- `DATA_SCHEMA.md` — JSON and CSV output schema documentation
- `REPORT_TEMPLATE.md` — Markdown report structure
- `PROMPT_TEMPLATES.md` — Prompt library generation templates by intent type
- `PLATFORM_BEHAVIOR.md` — Platform-specific citation behavior reference
- `TOOLS_COMPARISON.md` — Monitoring tools pricing and comparison
