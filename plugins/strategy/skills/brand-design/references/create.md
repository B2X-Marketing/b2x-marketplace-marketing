# Mode 2: Create Brand Identity (Palette + Type System)

## Purpose

Generate multiple complete visual identity recommendations — color palette and typography system — each representing a distinct brand character direction. The user gets strategic options to choose from, not a single "correct" answer.

## Inputs Required

Gather as much strategic context as possible before generating options:

1. **Brand personality and values** — What does the brand stand for? What archetype does it embody? (e.g., innovative, trustworthy, playful, premium, rebellious)
2. **Target audience** — Who are they? Age, sophistication, cultural context.
3. **Category/industry** — What space does the brand operate in?
4. **Competitive landscape** — Who are the main competitors? What do they look like visually? (If the user provides competitor names or URLs, research their visual identities.)
5. **Existing brand assets** — Does anything already exist? A logo, a name, a tagline, a color they love, a font they've already chosen?
6. **Tone of voice** — Formal/casual? Technical/approachable? Bold/subtle?
7. **Primary medium** — Where will this identity live most? (Website, app, social, packaging?) Default to web/digital if unspecified.

If the user hasn't provided all of this, ask targeted questions. Focus on the gaps that would most change your recommendation — personality and category are the most critical.

## Procedure

### Step 1: Strategic Analysis

Before generating any visual options, synthesize the inputs into a strategic brief:

- **Brand character in 3 words** — Distill the personality.
- **Emotional territory** — What should people *feel* when they encounter this brand?
- **Category color audit** — Based on your knowledge of the category, what colors are overused? Where is there white space on the color wheel?
- **Category type audit** — What type styles dominate the category? Where is there room to differentiate?
- **Constraints** — Any existing assets, cultural considerations, or technical requirements that limit the options.

Share this brief with the user before proceeding. It ensures alignment and prevents wasted work.

### Step 2: Generate Three Directions

Create three distinct recommendations. Each direction should be a *viable, complete identity* — not a throwaway option to make the "real" one look better. The three directions should span a meaningful range of brand character.

**How to create meaningful differentiation between directions:**

- **Direction A** might lean into the brand's most expected/safe positioning — appropriate to the category, trustworthy, professional. This is the "fit in, but do it well" option.
- **Direction B** might push toward a bolder, more differentiated position — less expected colors or type, more personality. This is the "stand out" option.
- **Direction C** might explore an orthogonal angle — perhaps warmer where A and B are cool, or more expressive where A and B are minimal. This is the "surprise" option.

For each direction, name it with a short character label (e.g., "Confident Authority," "Warm Disruptor," "Refined Minimalist") so the user can quickly grasp the personality each embodies.

### Step 3: Build Each Direction

For each of the three directions, construct:

#### Color Palette

Follow the palette architecture from the color knowledge base (Section 5):

1. **Primary color** — 1 color. Specify in OKLCH + Hex. Explain *why* this hue, chroma, and lightness for this direction.
2. **Secondary color(s)** — 1–2 colors. Identify the harmony model used (complementary, analogous, split-complementary, triadic) and why it fits this direction's personality.
3. **Accent color** — 1 color. Designed for CTAs and interactive elements. Should have maximum intentional contrast with the primary.
4. **Neutrals** — A tinted neutral scale (5–7 values from near-white to near-black) derived from the primary hue at very low chroma.
5. **Semantic colors** — Success (green), warning (amber), error (red), info (blue). Must coexist with the palette without confusion (especially if the primary is red or green).
6. **Full tint/shade scales** — For primary and secondary, generate a 9-step scale (50, 100, 200, 300, 400, 500, 600, 700, 800, 900) using the OKLCH method from the knowledge base (vary L while managing C as a bell curve).

For each scale step, provide:
- OKLCH value
- Hex code
- Contrast ratio against white (#FFFFFF) and against near-black (#1A1A2E)
- Accessibility status (AA text, AA large, AAA)

#### Typography System

Follow the brand type system process from the typography knowledge base (Section 9.2):

1. **Primary typeface** — Name, foundry, license type, weight range. Explain why this face matches the direction's personality (classification, stroke contrast, aperture, terminal style).
2. **Secondary typeface** — Name, foundry, license type. Explain the pairing rationale: what contrast dimensions are at play, what structural qualities are shared (x-height, proportions).
3. **Type scale** — Choose a modular ratio and show the complete scale from caption to display.
4. **Spacing rules** — Line-height, letter-spacing, and max line-length per hierarchy level.
5. **OpenType features** — Which features to activate (ligatures, figure styles, small caps) and where.

#### Direction Summary

For each direction, include a **Character Statement**: 2–3 sentences describing the overall personality this visual system projects. What kind of brand would this be? How would a customer describe its "vibe"?

And a **Trade-off Note**: What does this direction gain and what does it sacrifice compared to the others? (e.g., "This direction is the most distinctive but may feel less safe to conservative stakeholders" or "This is the most versatile across media but sacrifices some memorability.")

### Step 4: Comparative Overview

After presenting all three directions, provide a comparison table:

| Dimension | Direction A: [Name] | Direction B: [Name] | Direction C: [Name] |
|---|---|---|---|
| Primary color | [swatch desc + hex] | [swatch desc + hex] | [swatch desc + hex] |
| Harmony model | [model] | [model] | [model] |
| Primary typeface | [name] | [name] | [name] |
| Type classification | [category] | [category] | [category] |
| Emotional range | [warm/cool, bold/subtle] | ... | ... |
| Differentiation level | [Safe / Bold / Surprising] | ... | ... |
| Best for | [audience/context] | ... | ... |

### Step 5: Implementation Starter

For whichever direction the user chooses (or for all three if they want to compare in code), provide a CSS implementation starter:

```css
/* Direction [X]: [Name] */
:root {
  /* Primary palette */
  --color-primary-50: oklch(...) /* #hex */;
  --color-primary-100: oklch(...) /* #hex */;
  /* ... through 900 */

  /* Secondary palette */
  --color-secondary-50: oklch(...) /* #hex */;
  /* ... */

  /* Accent */
  --color-accent: oklch(...) /* #hex */;

  /* Neutrals */
  --color-neutral-50: oklch(...) /* #hex */;
  /* ... through 900 */

  /* Semantic */
  --color-success: oklch(...) /* #hex */;
  --color-warning: oklch(...) /* #hex */;
  --color-error: oklch(...) /* #hex */;
  --color-info: oklch(...) /* #hex */;

  /* Typography */
  --font-heading: '[Font Name]', [fallback stack];
  --font-body: '[Font Name]', [fallback stack];

  /* Type scale (Perfect Fourth 1.333 from 16px base) */
  --text-xs: 0.75rem;     /* 12px - caption */
  --text-sm: 0.875rem;    /* 14px - small */
  --text-base: 1rem;      /* 16px - body */
  --text-lg: 1.333rem;    /* 21px - h4 */
  --text-xl: 1.777rem;    /* 28px - h3 */
  --text-2xl: 2.369rem;   /* 38px - h2 */
  --text-3xl: 3.157rem;   /* 50px - h1 */
  --text-4xl: 4.209rem;   /* 67px - display */

  /* Spacing */
  --leading-tight: 1.2;    /* headings */
  --leading-normal: 1.5;   /* body */
  --leading-relaxed: 1.6;  /* body long-form */
  --tracking-tight: -0.02em; /* large headings */
  --tracking-normal: 0;      /* body */
  --tracking-wide: 0.05em;   /* all-caps labels */
  --measure: 65ch;            /* max line length */
}
```

Plus `@font-face` declarations or Google Fonts link tags for the recommended fonts.

## Scope Variations

- **Color only:** Skip the typography system. Generate three palette directions with full scales, accessibility data, and CSS color tokens.
- **Font only:** Skip the color palette. Generate three typography system directions with full scales, spacing rules, OpenType features, and CSS type tokens.
- **Both:** The full procedure above.
