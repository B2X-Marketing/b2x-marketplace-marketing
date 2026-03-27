# AI Visibility Monitor — Platform-Specific Citation Behavior

Reference extracted from AEO-GEO Knowledge Base Section 2.2. Use this to contextualize per-platform scoring and explain why results differ across platforms.

---

## Perplexity

| Metric | Value |
|--------|-------|
| Citation rate | 97% of responses include citations |
| Average citations per answer | 21.87 |
| Reddit/community forum share | 16.9% of citations |
| Brand preference | Balanced — no strong bias toward established brands |

**Behavior**: Perplexity cites sources in nearly every response and provides the most citations per answer of any platform. It favors fresh, well-cited articles and sites with machine-readable content (schema.org, OpenGraph, JSON-LD). The balanced mention-to-citation ratio makes it the best platform for driving actual referral traffic.

**What wins on Perplexity**: Structured content with schema markup, fresh publication dates, clear factual claims with source attribution, presence on Reddit and community forums.

**Scoring implication**: Expect higher mention and citation rates on Perplexity than other platforms. A brand not appearing on Perplexity likely has technical (D1) or structural (D2) issues.

---

## Google AI Overviews

| Metric | Value |
|--------|-------|
| Citation rate | 34% of cases |
| Brand preference | 59.8% of citations go to branded/established domains |
| Top-10 organic dependency | 81.1% of citations come from top-10 results |
| Position #1 citation probability | 33% |
| DR threshold for meaningful citations | DR 88+ = 6,000+ citations; below DR 63 = barely cited |
| AI Overview pixel footprint | 1,764 pixels average |
| Query presence | 47% of queries trigger AI Overviews |

**Trigger rates by query type**:
- Long-tail queries: 33%
- Question keywords: 22.6%
- Short-tail: 9.9%

**Behavior**: Google AI Overviews heavily favor content already ranking in organic search. It has the strongest brand preference of any platform — established domains with high Domain Rating get disproportionate citation share. This means traditional SEO success is a prerequisite for Google AI visibility.

**What wins on Google AI Overviews**: High Domain Rating (88+), top-10 organic ranking, established brand presence, well-structured answer blocks, factual meta descriptions.

**Scoring implication**: Low scores here usually indicate weak organic search presence (a D2/D3 issue) or low Domain Rating. Small/new brands will naturally score lower on Google AI Overviews than on other platforms.

---

## ChatGPT

| Metric | Value |
|--------|-------|
| Citation rate | 16% of responses |
| Top source | Wikipedia at 7.8% of citations |
| Primary behavior | Mentions brands but rarely links |

**Behavior**: ChatGPT has the lowest citation rate of the major platforms. It will mention and describe brands in responses but rarely provides clickable citations. Wikipedia is the #1 cited source. Training data has significant influence — content that was in the training corpus shapes responses even without real-time web search. This means ChatGPT's brand knowledge can be stale.

**What wins on ChatGPT**: Authoritative long-form content, Wikipedia presence, broad web consensus across multiple independent sources, brand mentions in training data (historical content), structured factual claims.

**Scoring implication**: Expect low citation rates. Focus on mention rate and sentiment instead. A brand well-described but not cited on ChatGPT is normal. A brand not mentioned at all on ChatGPT indicates weak web-wide consensus (D3 issue).

---

## Claude

| Metric | Value |
|--------|-------|
| Search-use volume | Lower but growing |
| Primary behavior | Training data + web search (when enabled) |

**Behavior**: Claude currently has lower search-use volume than ChatGPT, Perplexity, or Gemini. When web-enabled, it follows patterns similar to Perplexity. It values structured, factual content with clear attributions. As Claude's user base grows, monitoring this platform becomes increasingly important.

**What wins on Claude**: Structured content with clear attributions, factual accuracy, well-organized information hierarchies.

**Scoring implication**: Treat Claude results as directional rather than definitive given current lower usage volume. Include in tracking to establish baseline for trend monitoring.

---

## Cross-Platform Key Insight

**Only 11% of domains are cited by both ChatGPT and Perplexity.** These platforms are distinct ecosystems requiring different optimization strategies. A brand visible on one platform may be invisible on another.

This is why the AI Visibility Monitor scores each platform independently and why cross-platform analysis is essential for a complete picture.

---

## Platform Selection Guide

| Scenario | Recommended Platforms |
|----------|----------------------|
| B2B brand, professional audience | All 4 + LinkedIn (check Perplexity citations from LinkedIn) |
| B2C brand, consumer audience | ChatGPT, Perplexity, Google AI Overviews |
| Technical/developer audience | Perplexity, Claude, ChatGPT |
| Local/regional business | Google AI Overviews, ChatGPT |
| Enterprise sales | All 4 + Copilot (if audience uses Microsoft ecosystem) |

Default: Test all 4 core platforms (ChatGPT, Perplexity, Gemini, Claude). Add Grok and Copilot when relevant to the audience.
