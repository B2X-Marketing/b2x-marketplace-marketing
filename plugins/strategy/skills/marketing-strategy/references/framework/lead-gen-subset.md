# Lead-Gen Subset — Web Extraction Specification

This file defines how to extract Layers 1-3 of the full marketing strategy framework into a web-based questionnaire for lead generation.

---

## Purpose

A web version of this framework serves as a marketing hook: visitors answer 15 questions, receive a "Marketing Strategy Snapshot" with immediate value, and are upsold to the full 8-layer engagement.

## Scope

**Included**: Layers 1 (Golden Circle), 2 (Customer Insight — simplified), 3 (StoryBrand — simplified)
**Excluded**: Layers 4-8 (strategic planning, journey, channels, content, validation)

**Completion time**: 10-15 minutes
**Output**: One-page "Marketing Strategy Snapshot" gated behind email capture

---

## Simplified Question Set (15 Questions)

### Section 1: Purpose & Identity (Golden Circle) — 5 Questions

| # | Question | Maps To | Input Type |
|---|----------|---------|------------|
| 1 | What does your company do? Describe your main products or services. | WHAT | Textarea |
| 2 | What makes you different from competitors? What's your unique approach? | HOW | Textarea |
| 3 | Why does your company exist beyond making money? What do you believe should be different in the world? | WHY | Textarea |
| 4 | What industry are you in? | Context | Dropdown + Other |
| 5 | Who is your primary customer? (B2B: role/company type. B2C: demographic) | Segment seed | Textarea |

### Section 2: Customer Insight — 5 Questions

| # | Question | Maps To | Input Type |
|---|----------|---------|------------|
| 6 | Describe your ideal customer in one sentence. | Target persona | Textarea |
| 7 | What is the main problem your customer is trying to solve? | JTBD (functional) | Textarea |
| 8 | What are they currently doing to solve it — including doing nothing? | Current alternatives | Textarea |
| 9 | What frustrates them most about current solutions? | Key pain | Textarea |
| 10 | What would "success" look like for your customer after working with you? | Key gain | Textarea |

### Section 3: Messaging — 5 Questions

| # | Question | Maps To | Input Type |
|---|----------|---------|------------|
| 11 | If your customer is the hero of a story, what is the villain they're fighting? (Not a person — a frustration, condition, or force) | StoryBrand Villain | Textarea |
| 12 | In 3 simple steps, how do you help them win? | StoryBrand Plan | 3x Short text |
| 13 | What happens if they don't solve this problem? What gets worse? | StoryBrand Failure/Stakes | Textarea |
| 14 | What does their life or business look like after you help them? | StoryBrand Success/Transformation | Textarea |
| 15 | What is the one action you want them to take right now? (e.g., "Schedule a call", "Start a free trial") | StoryBrand Direct CTA | Short text |

---

## Output: Marketing Strategy Snapshot

The snapshot is auto-generated from the 15 answers. Structure:

```
┌─────────────────────────────────────────┐
│   MARKETING STRATEGY SNAPSHOT           │
│   [Company Name] — [Date]               │
├─────────────────────────────────────────┤
│                                         │
│   YOUR PURPOSE                          │
│   You believe: [Q3 answer]              │
│   You do this by: [Q2 answer]           │
│   You deliver: [Q1 answer]              │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│   YOUR CUSTOMER                         │
│   Ideal customer: [Q6 answer]           │
│   Their core problem: [Q7 answer]       │
│   What they do today: [Q8 answer]       │
│   Their frustration: [Q9 answer]        │
│   Their dream outcome: [Q10 answer]     │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│   YOUR MESSAGE                          │
│   One-Liner:                            │
│   "[Q6] struggle with [Q11].            │
│   [Company] provides [Q1] so they       │
│   can [Q14]."                           │
│                                         │
│   Your 3-Step Plan:                     │
│   1. [Q12a]                             │
│   2. [Q12b]                             │
│   3. [Q12c]                             │
│                                         │
│   The Stakes: [Q13 answer]              │
│   The Transformation: [Q14 answer]      │
│   Your CTA: [Q15 answer]               │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│   WHAT'S MISSING FROM YOUR STRATEGY     │
│                                         │
│   This snapshot covers your Purpose,    │
│   Customer, and Messaging — the         │
│   foundation. A complete strategy also  │
│   needs:                                │
│                                         │
│   ☐ Strategic Planning — Situation      │
│     analysis, SMART objectives, and     │
│     90-day action plan                  │
│   ☐ Customer Journey — How customers    │
│     discover, evaluate, buy, and stay   │
│   ☐ Channel Strategy — Which media      │
│     channels to invest in and why       │
│   ☐ Content Plan — What to create,      │
│     when, and where to publish it       │
│   ☐ Competitive Analysis — Where you    │
│     stand and where the whitespace is   │
│                                         │
│   [CTA BUTTON: Get Your Full Strategy]  │
│                                         │
└─────────────────────────────────────────┘
```

---

## Data Model (JSON Schema)

For the web form to capture and process responses:

```json
{
  "type": "object",
  "properties": {
    "company_name": { "type": "string" },
    "email": { "type": "string", "format": "email" },
    "golden_circle": {
      "type": "object",
      "properties": {
        "what": { "type": "string", "description": "Q1: Products/services" },
        "how": { "type": "string", "description": "Q2: Differentiation" },
        "why": { "type": "string", "description": "Q3: Purpose/belief" },
        "industry": { "type": "string", "description": "Q4: Industry" },
        "primary_customer": { "type": "string", "description": "Q5: Customer type" }
      }
    },
    "customer_insight": {
      "type": "object",
      "properties": {
        "ideal_customer": { "type": "string", "description": "Q6: One-sentence persona" },
        "main_problem": { "type": "string", "description": "Q7: Core JTBD" },
        "current_solution": { "type": "string", "description": "Q8: Alternatives" },
        "frustration": { "type": "string", "description": "Q9: Key pain" },
        "success": { "type": "string", "description": "Q10: Dream outcome" }
      }
    },
    "messaging": {
      "type": "object",
      "properties": {
        "villain": { "type": "string", "description": "Q11: Problem force" },
        "plan_steps": {
          "type": "array",
          "items": { "type": "string" },
          "minItems": 3,
          "maxItems": 3,
          "description": "Q12: 3-step plan"
        },
        "failure": { "type": "string", "description": "Q13: Stakes" },
        "transformation": { "type": "string", "description": "Q14: Success state" },
        "cta": { "type": "string", "description": "Q15: Primary CTA" }
      }
    }
  }
}
```

---

## UX Recommendations

- **3-step wizard**: One section per page (Purpose → Customer → Messaging), with progress indicator
- **Save and continue**: Allow users to save progress and return later
- **Smart defaults**: For Q4 (industry), provide a dropdown with common industries + "Other" free text
- **Character limits**: Encourage concise answers (200 chars for short text, 500 for textarea)
- **Instant preview**: Show the snapshot being built in real-time as they answer
- **Gate the output**: Require email before showing the completed snapshot
- **PDF download**: Offer the snapshot as a downloadable PDF with company branding

## Upsell Path

After the snapshot is delivered:
1. Email sequence (3 emails over 7 days):
   - Email 1: "Here's your snapshot" (immediate, with PDF attached)
   - Email 2: "Here's what a full strategy reveals" (day 3, highlight one gap area)
   - Email 3: "Ready to go deeper?" (day 7, offer consultation or full framework)
2. In-snapshot CTA: "Get Your Full Marketing Strategy" → consultation booking page
3. Follow-up: Use snapshot answers to personalize the consultation conversation
