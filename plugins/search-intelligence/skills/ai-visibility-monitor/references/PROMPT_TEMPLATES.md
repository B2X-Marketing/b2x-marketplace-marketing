# AI Visibility Monitor — Prompt Templates

Template prompts by intent type for auto-generating prompt libraries. Each template uses placeholders: `{brand}`, `{industry}`, `{competitor}`, `{topic}`, `{use_case}`.

When generating a prompt library, fill placeholders with the brand's actual values and select templates that match the brand's market context. Aim for 20-30 prompts total across all intent types.

---

## Informational (5 templates)

Templates targeting "What is...", "How does...", "Explain..." queries that your ideal customer asks AI.

| ID | Template |
|----|----------|
| INFO-01 | What is the best approach to {topic} for a {industry} company? |
| INFO-02 | How does {topic} work in the {industry} industry? |
| INFO-03 | Explain the key trends in {industry} for {topic} in 2026 |
| INFO-04 | What should I know about {topic} before choosing a {industry} solution? |
| INFO-05 | What are the most important factors when evaluating {topic} in {industry}? |

**Usage notes**: These prompts test whether AI surfaces the brand organically when users ask general industry questions. The brand is NOT mentioned in the prompt — this measures unprompted visibility.

---

## Comparative (5 templates)

Templates targeting "X vs Y", "Best X for Y", "Compare..." queries where the brand should appear in competitive discussions.

| ID | Template |
|----|----------|
| COMP-01 | Compare {brand} vs {competitor} for {use_case} |
| COMP-02 | What is the best {industry} solution for {use_case}? |
| COMP-03 | {brand} vs {competitor} — which is better for {topic}? |
| COMP-04 | What are the top {industry} companies for {use_case} in 2026? |
| COMP-05 | What are the differences between {brand} and {competitor} for {topic}? |

**Usage notes**: These test how the brand positions against competitors. Include at least one prompt per major competitor. Prompts COMP-01, COMP-03, and COMP-05 include the brand name and test head-to-head framing. COMP-02 and COMP-04 test whether AI includes the brand in category lists.

---

## Recommendation (5 templates)

Templates targeting "What tools should I use...", "Recommend a...", "What's the best..." queries where AI makes specific recommendations.

| ID | Template |
|----|----------|
| REC-01 | What tools should I use for {topic} in {industry}? |
| REC-02 | Recommend a {industry} solution for {use_case} |
| REC-03 | What is the best {topic} platform for small businesses in {industry}? |
| REC-04 | I need help with {use_case} — what {industry} tools do you recommend? |
| REC-05 | What are the most recommended {industry} solutions for {topic} in 2026? |

**Usage notes**: These test whether AI actively recommends the brand. Recommendation prompts are the highest-value intent — a brand mentioned here is in the AI's "consideration set." None of these include the brand name; they test organic recommendation.

---

## Problem-Solving (5 templates)

Templates targeting "How do I solve...", "What's the best way to...", "I'm struggling with..." queries where users bring a pain point to AI.

| ID | Template |
|----|----------|
| PROB-01 | How do I solve {topic} for my {industry} business? |
| PROB-02 | What is the best way to improve {topic} in {industry}? |
| PROB-03 | I am struggling with {use_case} — what should I do? |
| PROB-04 | How can a {industry} company address {topic} effectively? |
| PROB-05 | What are proven strategies for {use_case} in the {industry} sector? |

**Usage notes**: These test whether AI maps the brand to specific pain points and use cases. If the brand solves a problem but AI doesn't mention it, there's a content gap in D2 (Citation Readiness) or D3 (Authority & Distribution).

---

## Branded (5 templates)

Templates that explicitly mention the brand to test what AI knows and says about it directly.

| ID | Template |
|----|----------|
| BRAND-01 | What does {brand} do? |
| BRAND-02 | Is {brand} good for {use_case}? |
| BRAND-03 | What are alternatives to {brand}? |
| BRAND-04 | What do people think about {brand} for {topic}? |
| BRAND-05 | Tell me about {brand}'s approach to {topic} |

**Usage notes**: These test AI's knowledge depth about the brand. BRAND-01 tests basic recognition. BRAND-02 tests use-case association. BRAND-03 reveals which competitors AI considers peers. BRAND-04 tests sentiment. BRAND-05 tests depth of understanding. Every prompt library should include all 5 branded templates.

---

## Prompt Library Generation Rules

1. **Minimum 20 prompts, target 25-30**. Fewer than 20 reduces statistical reliability.
2. **All 5 intent types must be represented**. Never skip an intent category.
3. **At least 4-5 branded prompts**. These are the baseline for brand recognition measurement.
4. **At least 1 comparative prompt per major competitor**. If 3 competitors are tracked, include at least 3 comparative prompts.
5. **Draw topics from existing research/strategy output** when available. Check `./research-output/` and `./strategy-output/` for topics, use cases, and competitor names.
6. **Write prompts as real users would type them**. Full sentences, conversational tone, specific enough to trigger useful responses.
7. **Avoid overly generic prompts**. "What is marketing?" is too broad. "What is the best approach to B2B content marketing for SaaS startups?" is actionable.
8. **Include industry-specific terminology**. Use the language the brand's customers use, not internal jargon.
9. **Save the library for reuse**. Monitor mode depends on running the same prompts across runs for meaningful drift comparison.
10. **Present to user for review before executing**. The user may know specific prompts their customers ask.
