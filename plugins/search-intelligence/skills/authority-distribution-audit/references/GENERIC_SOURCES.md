# Generic Sources Reference — Authority & Distribution Audit

This document lists the generic platforms to check during every authority audit, along with search query templates, evaluation criteria, scoring guidance, and the rationale for each platform's importance to AI citations.

The skill reads this file at runtime instead of relying on memorized platform lists.

---

## 1. LinkedIn

### What It Is
Professional networking platform. #1 most-cited domain for professional queries and #2 overall in AI search.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `"{brand}" LinkedIn company page` | Find company page |
| `"{person_name}" "{brand}" LinkedIn` | Find key personnel profiles |
| `site:linkedin.com "{brand}" article` | Find LinkedIn articles mentioning the brand |
| `site:linkedin.com/company/{brand-slug}` | Direct company page lookup |

### What to Evaluate
- **Company page**: Exists, follower count, posting cadence, content type mix (articles vs posts vs shares)
- **Key personnel profiles**: Follower count (3,000+ threshold), article count, posting frequency, profile completeness
- **Content**: Original vs reshared ratio (95% of AI citations come from original content), structured formatting, topical consistency

### Scoring Criteria (0-100)
| Component | Weight | Criteria |
|-----------|--------|----------|
| Page existence | 20 | Company page exists and is claimed |
| Follower count | 20 | <500 = 5, 500-2K = 10, 2K-10K = 15, 10K+ = 20 |
| Posting cadence | 20 | Inactive = 0, Monthly = 10, Weekly = 15, 2-4x/week = 20 |
| Article presence | 20 | No articles = 0, 1-5 = 10, 6-20 = 15, 20+ = 20 |
| Personnel profiles | 20 | No key people = 0, profiles exist = 10, 3K+ followers on any = 15, multiple with 3K+ and articles = 20 |

### Why It Matters for AI Citations
- Articles = 50-66% of LinkedIn citations by AI
- Posts = 15-28% of citations
- Members with 3,000+ followers get stronger citation weight
- Individual member content outperforms Company Page content
- AI builds topical authority profiles for consistent posters

---

## 2. Reddit / Forums

### What It Is
Community discussion platform. Major source for user-generated consensus signals.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `site:reddit.com "{brand}"` | Find Reddit mentions |
| `"{brand}" reddit review` | Find review/discussion threads |
| `"{brand}" forum discussion` | Find non-Reddit forum mentions |
| `reddit.com/r/{industry} "{brand}"` | Check industry subreddits |

### What to Evaluate
- **Mention volume**: How often the brand is mentioned (none, few, moderate, frequent)
- **Sentiment**: Positive, negative, mixed, or neutral
- **Brand participation**: Does the brand have an official Reddit account? Do they engage?
- **Recency**: When was the brand last mentioned?
- **Subreddit relevance**: Are mentions in relevant industry subreddits or random ones?

### Scoring Criteria (0-100)
| Component | Weight | Criteria |
|-----------|--------|----------|
| Mention volume | 25 | None = 0, <10 = 10, 10-50 = 15, 50+ = 25 |
| Sentiment | 25 | Negative = 5, Mixed = 15, Neutral = 18, Positive = 25 |
| Brand participation | 25 | None = 0, Passive mentions only = 10, Active engagement = 25 |
| Recency | 25 | >1 year = 5, 6-12 months = 10, 1-6 months = 15, <1 month = 25 |

### Why It Matters for AI Citations
- Reddit accounts for 16.9% of Perplexity citations
- User-generated consensus is a primary signal AI uses for brand recommendation confidence
- Organic discussions carry more weight than brand-generated content for consensus

---

## 3. G2

### What It Is
B2B software review platform. Primary review source for SaaS and technology companies.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `"{brand}" G2 reviews` | Find G2 profile |
| `site:g2.com "{brand}"` | Direct G2 lookup |
| `"{brand}" G2 rating {current_year}` | Find recent rating data |

### What to Evaluate
- **Profile exists**: Claimed and active profile
- **Review count**: More reviews = stronger consensus signal
- **Average rating**: Out of 5 stars
- **Recency**: Date of most recent review
- **Response rate**: Whether the brand responds to reviews
- **Category ranking**: Position in G2 category grids

### Scoring Criteria (0-100)
| Component | Weight | Criteria |
|-----------|--------|----------|
| Profile exists | 20 | No = 0, Unclaimed = 10, Claimed = 20 |
| Review count | 30 | 0 = 0, 1-10 = 10, 11-50 = 20, 51-200 = 25, 200+ = 30 |
| Rating | 20 | <3.0 = 5, 3.0-3.9 = 10, 4.0-4.4 = 15, 4.5+ = 20 |
| Recency | 20 | >1 year = 5, 6-12 months = 10, 1-6 months = 15, <1 month = 20 |
| Response rate | 10 | Never = 0, Sometimes = 5, Regularly = 10 |

### Why It Matters for AI Citations
- Review sites provide independent validation that feeds the consensus signal
- AI cross-references review data when evaluating brand claims
- G2 is the dominant B2B review platform and frequently cited by AI for product comparisons

---

## 4. Capterra

### What It Is
B2B software review and comparison platform owned by Gartner.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `"{brand}" Capterra reviews` | Find Capterra profile |
| `site:capterra.com "{brand}"` | Direct Capterra lookup |

### What to Evaluate
Same as G2: profile existence, review count, rating, recency, response rate.

### Scoring Criteria (0-100)
Same structure as G2.

### Why It Matters for AI Citations
- Second major B2B review platform alongside G2
- Gartner ownership adds authority weight
- Multiple review site presence strengthens consensus signal

---

## 5. Trustpilot

### What It Is
Consumer and business review platform with global reach.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `"{brand}" Trustpilot reviews` | Find Trustpilot profile |
| `site:trustpilot.com "{brand}"` | Direct Trustpilot lookup |

### What to Evaluate
Same as G2: profile existence, review count, rating (out of 5), recency, response rate. Also check TrustScore.

### Scoring Criteria (0-100)
Same structure as G2.

### Why It Matters for AI Citations
- Broadest consumer reach among review platforms
- Trustpilot ratings frequently appear in AI-generated comparisons
- Particularly important for B2C and direct-to-consumer brands

---

## 6. YouTube

### What It Is
Video platform. Multimedia content is harder for AI to replicate, increasing citation value.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `"{brand}" YouTube channel` | Find official channel |
| `"{brand}" {industry} YouTube` | Find brand-related videos |
| `site:youtube.com "{brand}"` | Direct YouTube lookup |

### What to Evaluate
- **Channel exists**: Official brand channel
- **Subscriber count**: Audience size indicator
- **Video count**: Content volume
- **Upload frequency**: Active vs dormant channel
- **Transcripts/captions**: Critical for AI extraction — AI reads transcripts, not video
- **Content types**: Tutorials, webinars, product demos, thought leadership, customer testimonials

### Scoring Criteria (0-100)
| Component | Weight | Criteria |
|-----------|--------|----------|
| Channel exists | 20 | No = 0, Yes = 20 |
| Subscriber count | 20 | <100 = 5, 100-1K = 10, 1K-10K = 15, 10K+ = 20 |
| Video volume | 20 | 0 = 0, 1-10 = 10, 11-50 = 15, 50+ = 20 |
| Upload frequency | 20 | Dormant (>6mo) = 0, Quarterly = 10, Monthly = 15, Weekly+ = 20 |
| Transcript availability | 20 | None = 0, Some = 10, Most/All = 20 |

### Why It Matters for AI Citations
- Multimedia content provides unique information gain that text-only competitors lack
- Video transcripts become indexable text for AI training and citation
- YouTube is the second largest search engine — presence here feeds multiple AI systems

---

## 7. Wikipedia

### What It Is
Free encyclopedia. ChatGPT's #1 single citation source.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `"{brand}" Wikipedia` | Find Wikipedia page |
| `site:wikipedia.org "{brand}"` | Direct Wikipedia lookup |
| `"{brand}" Wikipedia notability` | Check for deletion discussions |

### What to Evaluate
- **Page exists**: Does the brand have a Wikipedia article?
- **Quality class**: Stub, Start, C, B, GA (Good Article), FA (Featured Article)
- **Content accuracy**: Is the information current and accurate?
- **Reference count**: Number of cited sources (more = more trustworthy)
- **Last edited**: When was the page last updated?
- **Notability concerns**: Any deletion discussions or notability flags?

### Scoring Criteria (0-100)
| Component | Weight | Criteria |
|-----------|--------|----------|
| Page exists | 40 | No = 0, Yes = 40 |
| Quality class | 30 | Stub = 10, Start = 15, C = 20, B = 25, GA/FA = 30 |
| Reference count | 20 | <5 = 5, 5-15 = 10, 16-30 = 15, 30+ = 20 |
| Accuracy/recency | 10 | Outdated = 3, Somewhat current = 7, Current = 10 |

### Why It Matters for AI Citations
- Wikipedia accounts for 7.8% of ChatGPT citations — the single largest source
- Wikipedia content is part of most LLM training datasets
- Having a Wikipedia page is a strong authority signal for all AI systems
- Creating or improving a Wikipedia page (following WP:NOTABILITY guidelines) is high-impact

---

## 8. Crunchbase / Directories

### What It Is
Business information platform and company directory. Industry directories provide discovery signals for niche brands.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `"{brand}" Crunchbase` | Find Crunchbase profile |
| `site:crunchbase.com "{brand}"` | Direct Crunchbase lookup |
| `"{brand}" {industry} directory` | Find industry-specific directories |

### What to Evaluate
- **Crunchbase**: Profile exists, completeness (funding, team, description, contact), data accuracy
- **Industry directories**: Which relevant directories list the brand, profile completeness

### Scoring Criteria (0-100)
| Component | Weight | Criteria |
|-----------|--------|----------|
| Crunchbase exists | 30 | No = 0, Basic = 15, Complete = 30 |
| Crunchbase completeness | 20 | Missing key fields = 5, Most fields = 15, Comprehensive = 20 |
| Other directories found | 30 | None = 0, 1-2 = 15, 3-5 = 25, 5+ = 30 |
| Profile quality | 20 | Incomplete = 5, Adequate = 15, Detailed = 20 |

### Why It Matters for AI Citations
- Crunchbase is frequently cited by AI for company information, funding, and team data
- Directory presence feeds the consensus signal across multiple independent sources
- Niche directories are especially important for industry-specific AI queries

---

## 9. Press / Media Coverage

### What It Is
News and media mentions. Coverage from quality outlets strengthens the authority signal.

### What to Search
| Query Template | Purpose |
|----------------|---------|
| `"{brand}" press coverage` | General press search |
| `"{brand}" news {current_year}` | Recent coverage |
| `"{brand}" {industry} media` | Industry-specific coverage |
| `"{brand}" press release` | Official announcements |
| `"{brand}" interview CEO` | Executive media appearances |

### What to Evaluate
- **Coverage volume**: Approximate number of articles/mentions
- **Recency**: Date of most recent coverage
- **Outlet quality**: Tier 1 (major publications: TechCrunch, Forbes, WSJ, NYT), Tier 2 (industry press), Tier 3 (niche blogs, local news)
- **Coverage type**: Product reviews, executive interviews, industry analysis, funding announcements, partnership news
- **Newsroom page**: Does the brand have a press/newsroom page on their website?

### Scoring Criteria (0-100)
| Component | Weight | Criteria |
|-----------|--------|----------|
| Coverage volume | 25 | None = 0, 1-5 articles = 10, 6-20 = 15, 20+ = 25 |
| Recency | 25 | >1 year = 5, 6-12 months = 10, 1-6 months = 15, <1 month = 25 |
| Outlet quality | 25 | Tier 3 only = 10, Mix = 15, Tier 1 included = 25 |
| Coverage diversity | 25 | Single type = 10, 2-3 types = 15, 4+ types = 25 |

### Why It Matters for AI Citations
- Press coverage from authoritative outlets feeds the authority signal for AI systems
- AI cross-references media mentions when evaluating brand credibility
- Press mentions on the brand's own site (newsroom page) contribute to E-E-A-T site-level signals

---

## Industry-Specific Source Discovery

In addition to the 9 generic platforms above, the skill discovers industry-specific sources during Step 4.

### Discovery Query Templates

| Query Template | What It Finds |
|----------------|---------------|
| `"{industry}" publications` | Trade press and industry magazines |
| `"{industry}" review sites` | Vertical-specific review platforms |
| `"{industry}" forums` | Community discussion boards |
| `"{industry}" directories` | Industry-specific business listings |
| `"{industry}" podcasts` | Audio content in the vertical |
| `"best {industry} companies" list` | Ranking/list sites |
| `"{industry}" association members` | Professional association directories |
| `"{industry}" awards {current_year}` | Industry award programs |

### Evaluation Criteria for Industry Sources

For each discovered source, evaluate:
1. **Relevance**: Is this source genuinely important in the industry? (Not generic padding)
2. **Brand presence**: Does the audited brand appear? In what capacity?
3. **Competitor presence**: Are competitors present here? (Absence is a competitive gap)
4. **Actionability**: Can the brand get listed/featured? How?
5. **AI citation potential**: Would AI systems find and cite this source for industry queries?

### Building the Industry Source List

Target 5-15 sources. Prioritize:
1. Industry publications that AI would cite for "{industry}" queries
2. Vertical review sites where buyers compare options
3. Professional forums where practitioners discuss tools/vendors
4. Industry directories that serve as reference lists
5. Podcasts where thought leaders in the space appear
