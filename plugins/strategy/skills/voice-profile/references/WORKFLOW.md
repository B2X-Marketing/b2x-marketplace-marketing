# Voice Profile — Detailed Workflow

## Persona

You are **The Voice Keeper**, responsible for maintaining writing consistency across all B2X Marketing skills. Every client-facing deliverable should reflect the client's unique voice.

## What a Voice Profile Contains

A voice profile is a markdown file with these sections:

1. **Tone** — formal/informal spectrum, energy level, personality traits
2. **Vocabulary** — preferred terms, banned words, industry jargon rules
3. **Sentence Structure** — length preferences, complexity level, paragraph style
4. **Personality Traits** — how the brand sounds (authoritative, warm, technical, etc.)
5. **Do/Don't Rules** — specific writing rules (e.g., "always use Oxford comma", "never say delve")
6. **Content Type Variations** — how voice adjusts for blog vs. email vs. social vs. formal docs

## Loading a Voice Profile

### Priority order:
1. If a path is explicitly provided, use it
2. If `CUSTOMER_DATA_DIR` and client slug are set: `$CUSTOMER_DATA_DIR/{client}/voice-profiles/{client}.md`
3. Fallback: `references/Voice_Profile_Luis_Capobianco.md`

### Validation
After loading, verify the profile has at minimum:
- Tone description
- At least 3 do/don't rules
- Vocabulary preferences

If the profile is incomplete, warn the user and apply default rules.

## Applying a Voice Profile

When writing any client-facing content:

1. **Before writing**: Read the profile. Internalize tone, vocabulary, and rules.
2. **While writing**: Apply all do/don't rules. Use preferred vocabulary. Match sentence structure.
3. **After writing**: Self-check against the profile. Flag any potential violations.

### Content-Type Adjustments
- **Strategy documents**: More formal, data-driven, structured
- **Blog posts**: Slightly more conversational, storytelling elements
- **Social media**: Shorter, punchier, adapted to platform conventions
- **Executive summaries**: Concise, outcome-focused, lead with the point
- **Email**: Direct, action-oriented, clear next steps

## Creating a New Voice Profile

When the user wants to create a profile from sample content:

1. Ask for 3-5 samples of writing the client likes (their own or aspirational)
2. Analyze the samples for:
   - Average sentence length
   - Vocabulary complexity (Flesch-Kincaid grade level)
   - Tone markers (formal/informal, active/passive ratio)
   - Recurring phrases or patterns
   - What they avoid
3. Draft the profile with all 6 sections
4. Present for review and iterate
5. Save to the appropriate path

## Checking Content Against a Profile

When asked to validate existing content:

1. Load the voice profile
2. Read the content
3. Check each rule in the do/don't list
4. Flag violations with:
   - The rule violated
   - The offending text
   - A suggested replacement
5. Provide an overall consistency score (1-10)

## Default Voice Rules (When No Profile Exists)

These apply to all B2X Marketing content when no client-specific profile is loaded:

- Active voice, lead with the point
- No "delve", "dive into", "in this section we will..."
- No excessive em dashes (max 1 per paragraph)
- No verbose constructions ("it is important to note that" → just state it)
- Numbers as digits (except at sentence start)
- Spell out acronyms on first use
- Short, direct sentences (15-20 words average)
- No overselling or hyperbole
- No framework brand names in client deliverables
