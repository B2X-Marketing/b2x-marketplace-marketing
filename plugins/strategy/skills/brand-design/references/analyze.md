# Mode 1: Analyze Brand Execution

## Purpose

Evaluate a design asset against a brand's visual identity and produce a structured diagnostic that identifies what's working, what's drifting, and what to fix.

## Inputs Required

Gather these from the user before starting:

1. **The execution to analyze** — An image, screenshot, URL, or file (poster, social post, ad, email, landing page, etc.). Use the `Read` tool for images or `WebFetch` for URLs.
2. **The brand reference** — At least one of:
   - Brand color specifications (hex codes, Pantone, or described in words)
   - Brand font specifications (font names, weights, usage rules)
   - A reference asset that represents the "correct" brand execution
   - The brand's website URL (you'll extract color and type patterns from it)
   - Written brand guidelines or strategy document

If the user provides only an execution and no reference, ask: "What should I compare this against? Do you have brand colors, fonts, or a reference design I can use as the baseline?"

If the user provides only a URL, treat it as both the execution and the reference — analyze the site's color and type system for internal consistency and best-practice alignment.

## Procedure

### Step 1: Extract the Visual Facts

**For color (if in scope):**
- Identify every distinct color used in the execution. Group by role: background, primary text, heading text, accent/CTA, secondary surfaces, borders, imagery tints.
- Express each color in hex and OKLCH.
- Map the approximate proportions (is the execution following something like 60-30-10, or is color distribution unbalanced?).
- Note any gradients, overlays, or transparency.

**For typography (if in scope):**
- Identify every typeface used. Note: if analyzing an image, you may need to make your best identification based on letterform characteristics (classify by anatomy — serif style, stroke contrast, terminal shape, x-height proportion, aperture openness).
- For each typeface, identify: usage role (headline, body, caption, CTA), weight, approximate size, case treatment, letter-spacing.
- Note hierarchy levels present and whether they're clearly differentiated.
- Estimate line-height and line-length where body text is visible.

### Step 2: Establish the Brand Reference

**From provided brand specs:**
- List the official primary, secondary, and accent colors with their values.
- List the official typefaces and their designated roles.

**From a website URL (if that's the reference):**
- Fetch the site and extract: CSS custom properties or computed styles for key colors, font-family declarations, font sizes for h1–h6 and body.
- Identify the de facto brand palette and type system from what's actually rendered.

**From a reference asset:**
- Extract colors and type following the same process as Step 1, and treat those as the standard.

### Step 3: Compare — The Diagnostic

Structure the comparison as a table or scorecard:

#### Color Diagnostic (if in scope)

| Dimension | Finding | Status |
|---|---|---|
| **Primary color fidelity** | Does the execution use the brand's primary color accurately, or has it drifted (wrong hex, altered saturation, different shade)? | ✅ Match / ⚠️ Drift / ❌ Violation |
| **Secondary/accent fidelity** | Are secondary and accent colors used correctly? | ✅ / ⚠️ / ❌ |
| **Color proportion** | Does the execution follow the brand's intended color balance (e.g., 60-30-10)? Or is it top-heavy, accent-heavy, etc.? | ✅ / ⚠️ / ❌ |
| **Harmony and cohesion** | Do all colors in the execution form a coherent palette, or are there off-brand orphan colors? | ✅ / ⚠️ / ❌ |
| **Contrast / accessibility** | Do text-background pairings meet WCAG AA? Are CTA buttons sufficiently distinct? | ✅ / ⚠️ / ❌ |
| **Context adaptation** | Is the palette adapted appropriately for the medium (dark background for Instagram story, light for email, etc.)? | ✅ / ⚠️ / ❌ |
| **Competitive differentiation** | Does the color usage still read as distinct from key competitors, or has it drifted toward a generic category look? | ✅ / ⚠️ / ❌ |

#### Typography Diagnostic (if in scope)

| Dimension | Finding | Status |
|---|---|---|
| **Typeface fidelity** | Are the correct brand typefaces used? Or have substitutions crept in (Arial instead of Helvetica, system fonts instead of brand fonts)? | ✅ / ⚠️ / ❌ |
| **Weight and style usage** | Are weights used as specified (e.g., Bold for headlines, Regular for body), or are unauthorized weights in play? | ✅ / ⚠️ / ❌ |
| **Hierarchy clarity** | Is the visual hierarchy (heading → subheading → body → caption) clear and consistent? Can you tell what to read first, second, third? | ✅ / ⚠️ / ❌ |
| **Size and scale** | Do the type sizes follow a rational scale? Are heading sizes proportionate to body size? | ✅ / ⚠️ / ❌ |
| **Spacing quality** | Are line-height, letter-spacing, and line-length within readable ranges? (body: 1.4–1.6× line-height, 50–75 chars/line) | ✅ / ⚠️ / ❌ |
| **Readability** | Is body text comfortably readable at the displayed size? Are font sizes sufficient for the medium? | ✅ / ⚠️ / ❌ |
| **Pairing harmony** | If multiple typefaces are used, do they pair well (intentional contrast, shared x-height/proportion)? Or do they conflict? | ✅ / ⚠️ / ❌ |

### Step 4: Synthesize and Recommend

After the diagnostic table, write a brief synthesis:

1. **Overall Alignment Score** — Summarize in one sentence how well the execution represents the brand visually (Strong / Good with issues / Needs attention / Off-brand).
2. **Top 3 Issues** — The most impactful problems, ranked by brand risk. For each, explain *what's wrong*, *why it matters for the brand*, and *how to fix it* with specific values (hex codes, font names, size adjustments).
3. **What's Working** — Acknowledge 1–2 things the execution does well. This provides balance and helps the user understand what to preserve.
4. **Implementation Fixes** — Provide exact corrective values: "Change the heading color from #4A5568 to #1A365D (your brand navy)" or "Replace Open Sans with your brand font Inter at 16px/1.5 for body text."

## Output Format

```markdown
# Brand Execution Analysis

## Execution Analyzed
[Description of what was analyzed and the medium]

## Brand Reference
[Summary of the brand standards used as baseline]

## Scope
[Color / Font / Both]

## Color Diagnostic
[Table from Step 3]

## Typography Diagnostic
[Table from Step 3]

## Synthesis

### Overall Alignment
[One-sentence verdict]

### Top Issues
1. [Issue, impact, fix]
2. [Issue, impact, fix]
3. [Issue, impact, fix]

### What's Working
- [Positive finding]

### Implementation Fixes
[Exact corrective values with before → after]
```

## Edge Cases

- **No brand reference provided:** Ask for one. Don't guess at brand colors.
- **Analyzing an image with no visible text:** Skip the typography diagnostic and note that type couldn't be evaluated.
- **Multiple pages/screens:** Analyze the most representative one, or ask the user which to focus on.
- **The execution is a logo only:** Focus on color accuracy and type identification. Skip proportion and hierarchy analysis.
