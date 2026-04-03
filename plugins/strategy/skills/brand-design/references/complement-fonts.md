# Mode 4: Complement Font — Find a Secondary Typeface

## Purpose

Given a primary typeface (and optionally brand context), recommend secondary font options that pair well, serve a clear functional role, and reinforce the brand's character. Provide 3 options spanning a range from safe to distinctive.

## Inputs Required

1. **Primary font** — The typeface name and its role (heading or body). If the user doesn't specify the role, ask: "Is [font name] your heading font or your body text font?"
2. **Brand context** (any of these help):
   - Brand personality / values / archetype
   - Industry / category
   - The brand's color palette (helps calibrate the visual weight and mood)
   - Target audience
   - Whether the brand already has a website / app, and the URL
3. **Constraints** (optional):
   - "Must be open source / Google Fonts"
   - "Must include Cyrillic / Arabic / CJK support"
   - "Must have a variable font version"
   - "Must be free" or budget indication for commercial licensing
   - "We need a monospace for code blocks too"

## Procedure

### Step 1: Profile the Primary Font

Before recommending a pair, deeply understand the anchor font. Research it:

- **Classification:** Which subcategory? (e.g., Humanist sans, Transitional serif, Geometric sans, Slab serif)
- **Structural characteristics:**
  - Stroke contrast (low, moderate, high, extreme)
  - X-height (small, medium, large relative to cap-height)
  - Aperture openness (open, moderate, closed)
  - Terminal style (round, flat, tapered, serif shape)
  - Stress angle (diagonal, vertical, none)
  - Width tendency (narrow, regular, wide)
  - Weight range available
- **Personality:** Based on its classification and structure, what does it communicate? (Refer to the typography knowledge base Section 4.)
- **Role context:** If it's the heading font, the secondary needs to be a strong body text performer (legibility, comfortable reading at 14–18px). If it's the body font, the secondary needs display impact (distinctive at large sizes, personality).

Summarize this profile for the user so they understand the foundation they're pairing from.

### Step 2: Define the Pairing Strategy

Based on the primary's profile and the brand context, decide on the pairing approach:

**What contrast dimensions to use:**

The best pairs differ in 1–2 dimensions while sharing at least 1 structural quality. Choose which dimensions to contrast and which to hold constant:

| Hold Constant (coherence) | Vary (contrast) |
|---|---|
| X-height | Classification (serif + sans) |
| Stroke logic / proportions | Weight (light primary + bold secondary) |
| Overall mood | Width (regular + condensed) |
| Historical era | Stroke contrast level |

State your pairing strategy explicitly: "I'm looking for a [classification] with [shared quality] but contrasting [quality], because [reason tied to brand strategy]."

### Step 3: Generate Three Recommendations

For each recommendation, provide:

#### Font Identity
- **Font name** and foundry/designer
- **License:** OFL (free), Apache 2.0 (free), Commercial (name the foundry and approximate cost tier), or System font
- **Source:** Google Fonts URL, foundry URL, or "pre-installed system font"
- **Classification:** Precise subcategory
- **Variable font available:** Yes/No. If yes, list axes.

#### Pairing Rationale
- **What's shared** with the primary (the coherence anchor): "Both have a large x-height and similar proportional width, creating visual kinship at mixed sizes."
- **What contrasts** (the visual energy): "The serif's stroke contrast and bracketed serifs provide formal authority against the primary's low-contrast geometric simplicity."
- **Brand fit:** "This pairing positions the brand as [character description]. It says [what the combination communicates that neither font says alone]."

#### Structural Comparison Table

| Metric | Primary: [Name] | Recommended: [Name] |
|---|---|---|
| Classification | [e.g., Geometric sans] | [e.g., Transitional serif] |
| Stroke contrast | [low/medium/high] | [low/medium/high] |
| X-height | [small/medium/large] | [small/medium/large] |
| Aperture | [open/moderate/closed] | [open/moderate/closed] |
| Stress | [diagonal/vertical/none] | [diagonal/vertical/none] |
| Width | [narrow/regular/wide] | [narrow/regular/wide] |
| Available weights | [range] | [range] |

#### Usage Guidance
- **Role assignment:** "Use [primary] for [role], [secondary] for [role]."
- **Size and weight recommendations:** Specific values for heading, body, caption.
- **Spacing guidance:** Line-height, letter-spacing per use case.

#### Direction Label

Name each option with a character descriptor:

- **Option A (Safe):** A well-tested, widely-used pairing that minimizes risk. "You can't go wrong with this."
- **Option B (Distinctive):** A pairing with more personality and differentiation. "This makes a statement."
- **Option C (Unexpected):** A less conventional pairing that surprises without conflicting. "This sets you apart."

### Step 4: Implementation Package

For whichever option the user selects (or for all three), provide:

**Google Fonts link (if applicable):**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=[Font+Name]:wght@400;500;700&display=swap" rel="stylesheet">
```

**@font-face declarations (if self-hosted):**
```css
@font-face {
  font-family: '[Font Name]';
  src: url('/fonts/[font-file].woff2') format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

**CSS Type System:**
```css
:root {
  --font-heading: '[Primary Font]', [fallback stack];
  --font-body: '[Secondary Font]', [fallback stack];

  /* Fallback matching to reduce CLS */
  --font-body-fallback-adjust: size-adjust: [X]%;
}

/* Type scale */
h1 { font: 700 var(--text-3xl)/var(--leading-tight) var(--font-heading); letter-spacing: var(--tracking-tight); }
h2 { font: 700 var(--text-2xl)/var(--leading-tight) var(--font-heading); }
h3 { font: 600 var(--text-xl)/var(--leading-tight) var(--font-heading); }
body { font: 400 var(--text-base)/var(--leading-normal) var(--font-body); max-width: var(--measure); }
.caption { font: 400 var(--text-sm)/var(--leading-normal) var(--font-body); }
```

**OpenType feature recommendations:**
```css
body {
  font-variant-ligatures: common-ligatures;
  font-variant-numeric: oldstyle-nums proportional-nums; /* for serif body */
}

h1, h2, h3 {
  font-variant-ligatures: common-ligatures discretionary-ligatures;
}

.data-table {
  font-variant-numeric: lining-nums tabular-nums;
}

.label, .overline {
  font-variant-caps: all-small-caps;
  letter-spacing: 0.08em;
}
```

### Step 5: Validation Checklist

Present a final checklist:

- [ ] X-heights appear similar when set at the same point size
- [ ] Contrast between the two faces is clear and intentional
- [ ] Each face has a clearly defined role (heading vs. body)
- [ ] The pairing works at all needed sizes (12px caption through 48px display)
- [ ] Both fonts are available in the required weights (at minimum: Regular, Medium/Semibold, Bold)
- [ ] Language/script support covers all markets
- [ ] Licensing covers all intended uses (web, app, desktop, email)
- [ ] Combined file size is reasonable (< 150KB for web, using WOFF2 + subsetting)
- [ ] A system fallback stack is defined for each font

## Scope Note

This mode is inherently font-focused. If the user asked for "both" and has not yet defined their color palette, suggest running Mode 3 (Complement Colors) first or in parallel, since the color palette's temperature and energy should inform the type system's mood.

## Edge Cases

- **User provides a very common font (e.g., Helvetica, Arial):** Note that the primary itself may not be distinctive enough to carry brand identity — the secondary becomes more important as a differentiator. Suggest considering Mode 2 (full identity creation) if the user is open to reconsidering the primary.
- **User provides a display/decorative font as the primary:** The secondary must be a strong workhorse body font. Bias options heavily toward legibility.
- **User wants three fonts (heading + body + accent):** Extend the recommendations to include a third suggestion for the accent role (typically monospace, display, or a stylistic alternate of the primary).
