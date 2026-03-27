# Session Intake

This is the first conversation in every strategy engagement. Its purpose is to collect baseline context and classify the scenario before entering the framework layers.

Ask these questions conversationally — one block at a time, not all at once.

---

## Block A: Company Basics

1. What is the company name?
2. What industry or sector are you in?
3. How long has the company been operating? (Pre-launch / Under 1 year / 1-5 years / 5-10 years / 10+ years)
4. What is your approximate company size? (Solo founder / 2-10 / 11-50 / 51-200 / 200+)
5. What is your approximate annual revenue range? (Pre-revenue / Under $500K / $500K-$2M / $2M-$10M / $10M+)
6. What geography do you serve? (Local / Regional / National / International)
7. Is your business primarily B2B, B2C, or both?

---

## Block B: Scenario Detection

Ask these questions to understand what's driving this strategy exercise:

1. **What brings you to this strategy exercise?** (Let the user explain in their own words — this is the most important intake question)
2. Do you have an existing marketing strategy? (None / Informal/tribal knowledge / Documented but outdated / Current and documented)
3. Are you launching something new, or refining something existing?
4. Is there a specific deadline or trigger for this work? (Board meeting, funding round, product launch, competitive pressure, etc.)
5. What does success look like for you at the end of this process?

### Scenario Classification Rules

Based on the answers above, classify into one of four scenarios:

| Signal | Scenario |
|--------|----------|
| No existing strategy AND company is early-stage (pre-launch or < 2 years) | **NEW_COMPANY** |
| Mentions "pivot", "rebrand", "new direction", "repositioning", or fundamental change | **EXISTING_PIVOT** |
| Mentions a specific new product, service, or offering being launched | **PRODUCT_LAUNCH** |
| Has an existing strategy AND wants to update, improve, or modernize it | **STRATEGY_REFRESH** |

If the classification is ambiguous, ask: "It sounds like this could be [option A] or [option B]. Which feels more accurate to you?"

---

## Block C: Asset Inventory

Understanding what materials already exist avoids re-asking answered questions:

1. Do you have any existing documents you can share? Check for:
   - Pitch deck or investor presentation
   - Brand guidelines or style guide
   - Existing marketing strategy or plan
   - Customer research, surveys, or persona documents
   - Competitor analysis
   - Website analytics reports
   - Sales collateral
2. Do you have an existing website? If so, what is the URL?
3. What marketing channels are you currently active on? (Website, social platforms, email, paid ads, PR, events, etc.)
4. Do you have existing customer data or analytics you can reference?
5. Are there any previous marketing efforts — successful or failed — that we should know about?

### Document Processing Instructions

When the user provides documents:
- Read each document in full
- Extract information relevant to the framework layers
- Map extracted info to specific layers (e.g., a pitch deck likely contains Layer 1 and Layer 2 material)
- Note which framework questions the documents answer and which remain open
- Present a summary: "From your documents, I've gathered [X, Y, Z]. I'll confirm these with you as we work through each layer."

---

## Block D: Constraints and Context

1. What is your approximate marketing budget? (No budget yet / Under $5K/month / $5K-$20K/month / $20K-$50K/month / $50K+/month)
2. Do you have an in-house marketing team, or do you rely on external resources?
3. What marketing tools or platforms are you currently using? (CRM, email platform, analytics, social tools, etc.)
4. Are there any constraints we should know about? (Legal/compliance, brand restrictions, competitive sensitivity, etc.)
5. Who are the key stakeholders who need to approve this strategy?

---

## Output: Context Brief

After completing intake, draft a **Context Brief** that becomes the first section of the strategy document:

```
## Context Brief

**Company**: [Name]
**Industry**: [Sector]
**Stage**: [Operating years] | [Size] | [Revenue range]
**Geography**: [Market scope]
**Model**: [B2B / B2C / Both]
**Scenario**: [NEW_COMPANY / EXISTING_PIVOT / PRODUCT_LAUNCH / STRATEGY_REFRESH]
**Trigger**: [What prompted this exercise]
**Success Criteria**: [What the user defined as success]
**Budget**: [Range]
**Team**: [In-house / External / Mixed]
**Existing Channels**: [List]
**Documents Provided**: [List with brief notes on what each contains]
**Key Constraints**: [Any limitations noted]
```

Present this brief to the user for confirmation before proceeding to Layer 1.

---

## Next Step

Once the Context Brief is confirmed:
1. Copy `Strategy/Templates/strategy-document-template.md` to `Strategy/Output/[Company-Name]-marketing-strategy-[date].md`
2. Populate the Context Brief section
3. Set Strategy State to "Layer 0 (Intake) complete — proceeding to Layer 1"
4. Proceed to `Strategy/Framework/02-golden-circle.md`
