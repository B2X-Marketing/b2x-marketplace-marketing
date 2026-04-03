# Mode 3: Complement Colors — Build a Complete Palette from Primaries

## Purpose

Given one or more primary brand colors, generate the complete supporting palette: secondary colors, accent, neutrals, semantic colors, and full tint/shade scales — all ready for digital implementation.

## Inputs Required

1. **Primary color(s)** — At minimum one color, provided as hex, RGB, or a color name. Convert everything to OKLCH as the first step.
2. **Brand context** (any of these help, none are strictly required):
   - Brand personality / values / archetype
   - Industry / category
   - Target audience
   - Existing visual assets (logo, website)
   - Competitors to avoid resembling
3. **Specific requirements** (optional):
   - "We need a dark mode palette too"
   - "The accent must be orange"
   - "We need colors for success/error/warning states"
   - "Keep it muted" or "Make it vibrant"

If only a bare color is provided with no context, still generate the palette — but note that without brand context, the recommendations are purely aesthetic/technical rather than strategic.

## Procedure

### Step 1: Analyze the Primary

Express the primary color(s) in OKLCH. For each, note:

- **Lightness (L):** Where does it sit? Light (L > 0.7), mid (0.4–0.7), or dark (L < 0.4)?
- **Chroma (C):** Vivid (C > 0.15), moderate (0.08–0.15), or muted (C < 0.08)?
- **Hue (H):** What hue family? What temperature (warm/cool)?
- **Psychological profile:** What does this color communicate per the knowledge base? (e.g., blue = trust; red = energy)
- **Category context:** Is this color common or unusual in the brand's category?

If multiple primaries are provided, also analyze their relationship: are they analogous, complementary, split-complementary? What harmony model do they already imply?

### Step 2: Select Harmony Strategy

Based on the primary color(s) and brand context, choose the harmony model for generating supporting colors. Explain the choice:

| Situation | Recommended Harmony | Why |
|---|---|---|
| Single warm primary, brand wants energy | Split-complementary | Maintains energy while adding cool contrast for balance |
| Single cool primary, brand wants trust | Analogous | Reinforces calm cohesion; differentiate through value/chroma |
| Single primary, brand wants bold differentiation | Complementary | Maximum contrast for visual impact |
| Single primary, brand wants variety + playfulness | Triadic | Balanced vibrancy across the palette |
| Two primaries already provided (analogous) | Complement the pair | Add a distant accent for contrast |
| Two primaries already provided (complementary) | The harmony is set | Build scales and neutrals; add a midpoint accent if needed |

State the chosen model and the specific hue angles you'll use.

### Step 3: Generate the Supporting Colors

Using the harmony model, generate:

**Secondary Color(s)** — 1–2 colors derived from the harmony rotation.
For each, specify:
- OKLCH value + Hex
- The harmony relationship to the primary (e.g., "+150° split-complementary")
- Why this color supports the brand (e.g., "This teal provides cooling contrast to the warm coral primary, communicating reliability alongside the primary's energy")

**Accent Color** — 1 color optimized for CTAs and interactive elements.
Requirements:
- Must have sufficient contrast against both the primary and the most common background (usually white or near-white)
- Should create visual "pull" — the eye should go to it
- Typically the complement or near-complement of the primary, at higher chroma

**Neutrals** — A tinted neutral scale (7 steps minimum: 50, 100, 200, 300, 500, 700, 900).
Method: Sample the primary's hue at very low chroma (C ≈ 0.01–0.03) and create a lightness ramp from L ≈ 0.97 (near-white) to L ≈ 0.12 (near-black). These "tinted neutrals" feel naturally related to the brand without being visibly colored.

**Semantic Colors** — Success, Warning, Error, Info.
Rules:
- Success: Green family (H ≈ 145°). If the primary is green, shift success to H ≈ 160° to differentiate.
- Warning: Amber/yellow family (H ≈ 85°).
- Error: Red family (H ≈ 25°). If the primary is red, shift error toward a cooler red (H ≈ 15°) or use a different lightness.
- Info: Blue family (H ≈ 240°). If the primary is blue, shift info to a distinctly different lightness or chroma.
- All semantic colors need WCAG AA contrast against their likely backgrounds (both light and dark).

### Step 4: Generate Tint/Shade Scales

For each primary, secondary, and accent color, generate a 9-step scale:

**Method (from the color knowledge base):**
1. Set L anchors: Step 50 → L ≈ 0.97, Step 500 → L = [base color's L], Step 900 → L ≈ 0.18
2. Interpolate L values across steps (slightly curved distribution for perceptual evenness)
3. Adjust C as a bell curve peaking at or near Step 500, decreasing toward both extremes
4. Hold H constant (or adjust ±2–3° for warmth in darks if appropriate)

Present each step as:

| Step | OKLCH | Hex | vs. White | vs. Black | AA Text | AA Large |
|---|---|---|---|---|---|---|
| 50 | oklch(0.97 0.01 H) | #F7F7FE | 1.1:1 | 18.5:1 | — | — |
| 100 | ... | ... | ... | ... | ... | ... |
| ... | | | | | | |
| 900 | oklch(0.18 0.06 H) | #1A1A3E | 16.2:1 | 1.2:1 | ✅ on white | ✅ on white |

Mark the **recommended text-safe step** — the lightest step that meets 4.5:1 contrast on white (usually 600 or 700).

### Step 5: Dark Mode Adaptation

If the user requests dark mode (or by default, since the skill assumes digital), provide guidance:

- **Dark surface color:** Neutral 900 or 800 as the background.
- **Primary on dark:** Use a lighter step of the primary (e.g., 300 or 400 instead of 500) to maintain contrast.
- **Text on dark:** Neutral 50 or 100.
- **Accent on dark:** May need chroma adjustment — accent at full chroma can feel overwhelming on dark backgrounds. Reduce chroma slightly.
- **Semantic on dark:** Lighter variants (step 300–400) for badges/icons; still need AA contrast.

### Step 6: Implementation Output

Provide the complete palette as CSS custom properties:

```css
:root {
  /* Primary */
  --color-primary-50: #____;
  --color-primary-100: #____;
  --color-primary-200: #____;
  --color-primary-300: #____;
  --color-primary-400: #____;
  --color-primary-500: #____;  /* Base primary */
  --color-primary-600: #____;
  --color-primary-700: #____;  /* Text-safe on white */
  --color-primary-800: #____;
  --color-primary-900: #____;

  /* Secondary */
  --color-secondary-50: #____;
  /* ... through 900 */

  /* Accent */
  --color-accent: #____;
  --color-accent-hover: #____;  /* Slightly darker/more saturated */
  --color-accent-active: #____;  /* Darker still */

  /* Neutrals */
  --color-neutral-50: #____;
  /* ... through 900 */

  /* Semantic */
  --color-success: #____;
  --color-warning: #____;
  --color-error: #____;
  --color-info: #____;

  /* Semantic light variants (for backgrounds) */
  --color-success-light: #____;
  --color-warning-light: #____;
  --color-error-light: #____;
  --color-info-light: #____;
}

/* Dark mode overrides */
@media (prefers-color-scheme: dark) {
  :root {
    --color-surface: var(--color-neutral-900);
    --color-text: var(--color-neutral-50);
    --color-primary-text: var(--color-primary-300);
    /* ... adapted values */
  }
}
```

Also provide a **visual summary**: list the palette as a simple table showing the color name, hex, and a brief role description.

## Scope Note

This mode is inherently color-focused. If the user asked for "both" (color + font), after completing the color palette, suggest transitioning to Mode 4 (Complement Font) to select typography that harmonizes with the new palette. Offer to proceed.
