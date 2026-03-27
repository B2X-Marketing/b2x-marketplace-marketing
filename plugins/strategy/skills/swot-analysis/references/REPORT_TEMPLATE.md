# SWOT Report Template Reference

Instructions for generating `swot-analysis.md`. This is a reference for the skill, not the template itself.

## Structure

1. **Header**: Subject, scope, date, confidence rating
2. **Executive Summary**: 1-paragraph key insight and strategic implication
3. **Strengths**: Table with items sorted by impact (high → low)
4. **Weaknesses**: Same format
5. **Opportunities**: Same format
6. **Threats**: Same format
7. **SWOT Matrix**: 2×2 markdown table (compact view)
8. **TOWS Strategic Actions**: Optional section — four sub-tables (SO, WO, ST, WT)
9. **Recommended Priorities**: Numbered list of top actions
10. **Next Steps**: What to do with this analysis

## Writing Rules

- Follow the client's voice profile for all output
- Active voice, lead with the point
- No "delve", no "in this section we will...", no filler transitions
- Numbers as digits (not spelled out)
- Short sentences and paragraphs
- No framework brand names in the output (no "TOWS Matrix" in headers — use "Strategic Actions")

## Section Rules

### Quadrant Tables

Format each quadrant as a table:

```markdown
| Factor | Impact | Evidence |
|--------|--------|----------|
| [Title]: [Description] | High/Medium/Low | [Evidence] |
```

Sort by impact: high first, then medium, then low.

### Executive Summary

- 1 paragraph, 3-5 sentences
- Lead with the most important finding
- State the strategic implication
- Synthesize — don't repeat individual items

### SWOT Matrix

Compact 2×2 table for quick reference:

```markdown
|  | **Helpful** | **Harmful** |
|--|-------------|-------------|
| **Internal** | S1, S2, S3 | W1, W2, W3 |
| **External** | O1, O2, O3 | T1, T2, T3 |
```

Use short titles only (from the `title` field).

### TOWS Strategic Actions (Optional)

Four sub-sections, each with a table:

```markdown
#### Leverage Strengths × Opportunities

| Action | Rationale | Priority |
|--------|-----------|----------|
| [action] | [rationale] | High/Medium/Low |
```

Header labels (plain language, no "TOWS" or "SO/WO/ST/WT" labels):
- "Leverage Strengths × Opportunities"
- "Address Weaknesses × Opportunities"
- "Defend Strengths × Threats"
- "Minimize Weaknesses × Threats"

### Recommended Priorities

Numbered list (1-5 items). Each item: one sentence, action-oriented, starts with a verb.

### Next Steps

2-3 bullets on how to use the analysis:
- What decisions it informs
- What additional research might be needed
- When to revisit the analysis
