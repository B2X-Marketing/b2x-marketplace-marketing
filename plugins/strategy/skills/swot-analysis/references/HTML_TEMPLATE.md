# HTML Visual Matrix Template Reference

Instructions for generating `swot-matrix.html`. This is a reference for the skill, not the template itself.

## Requirements

- Self-contained HTML file — no external dependencies
- Inline CSS and JavaScript only
- Responsive layout (works on screen and print)
- Embedded JSON data block for programmatic access
- Print-friendly CSS (`@media print`)

## Layout

### Main Matrix

2×2 color-coded grid with these quadrant colors:

| Quadrant | Background | Text | Header |
|----------|-----------|------|--------|
| Strengths (top-left) | `#e8f5e9` | `#1b5e20` | `#2e7d32` |
| Weaknesses (top-right) | `#fff8e1` | `#e65100` | `#f57f17` |
| Opportunities (bottom-left) | `#e3f2fd` | `#0d47a1` | `#1565c0` |
| Threats (bottom-right) | `#fce4ec` | `#b71c1c` | `#c62828` |

### Axis Labels

- Top row: "Internal" label spanning both top quadrants
- Bottom row: "External" label spanning both bottom quadrants
- Left column: "Helpful" label
- Right column: "Harmful" label

### Item Display

Each item shows:
- **Title** in bold
- **Impact badge** — small pill/tag with color:
  - High: `#d32f2f` (red) with white text
  - Medium: `#f57c00` (orange) with white text
  - Low: `#757575` (gray) with white text
- **Description** in regular weight below the title (smaller font)

### TOWS Panel (Optional)

When TOWS data is present, add a collapsible panel below the matrix:
- Toggle button: "Show Strategic Actions" / "Hide Strategic Actions"
- Four columns (or 2×2 grid on narrow screens):
  - SO: green-tinted header
  - WO: amber-tinted header
  - ST: blue-tinted header
  - WT: red-tinted header
- Each action shows: action text, priority badge, rationale in smaller text

## HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SWOT Analysis — {subject}</title>
  <style>
    /* All CSS inline — see CSS section below */
  </style>
</head>
<body>
  <div class="container">
    <header>
      <h1>SWOT Analysis</h1>
      <div class="meta">
        <span class="subject">{subject}</span>
        <span class="scope">{scope}</span>
        <span class="date">{date}</span>
      </div>
    </header>

    <div class="matrix">
      <!-- Axis labels -->
      <div class="axis-label axis-helpful">Helpful</div>
      <div class="axis-label axis-harmful">Harmful</div>
      <div class="axis-label axis-internal">Internal</div>
      <div class="axis-label axis-external">External</div>

      <!-- Quadrants -->
      <div class="quadrant strengths">
        <h2>Strengths</h2>
        <!-- Items rendered here -->
      </div>
      <div class="quadrant weaknesses">
        <h2>Weaknesses</h2>
      </div>
      <div class="quadrant opportunities">
        <h2>Opportunities</h2>
      </div>
      <div class="quadrant threats">
        <h2>Threats</h2>
      </div>
    </div>

    <!-- Summary -->
    <div class="summary">
      <h2>Key Insight</h2>
      <p>{key_insight}</p>
      <h2>Strategic Implication</h2>
      <p>{strategic_implication}</p>
    </div>

    <!-- TOWS panel (conditional) -->
    <div class="tows-panel" id="towsPanel" style="display:none;">
      <!-- Rendered when TOWS data exists -->
    </div>

    <!-- Embedded JSON data -->
    <script type="application/json" id="swot-data">
      {/* Full swot-data.json embedded here */}
    </script>
  </div>

  <script>
    // Toggle TOWS panel
    // Parse and render items from embedded JSON
  </script>
</body>
</html>
```

## CSS Guidelines

### Grid Layout

Use CSS Grid for the 2×2 matrix:

```css
.matrix {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto auto;
  gap: 2px;
  max-width: 1200px;
  margin: 0 auto;
}
```

### Typography

- Title: system font stack (`-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`)
- Quadrant headers: 1.2rem, bold, white text on quadrant header color
- Item titles: 0.95rem, bold
- Item descriptions: 0.85rem, regular weight
- Impact badges: 0.7rem, uppercase, letter-spacing 0.5px

### Responsive Breakpoints

```css
@media (max-width: 768px) {
  .matrix {
    grid-template-columns: 1fr;
  }
  .tows-grid {
    grid-template-columns: 1fr;
  }
}
```

### Print Styles

```css
@media print {
  body { font-size: 10pt; }
  .matrix { break-inside: avoid; }
  .tows-toggle { display: none; }
  .tows-panel { display: block !important; }
  .impact-badge { border: 1px solid #333; }
}
```

## JavaScript

Minimal JavaScript — only for:
1. Toggling the TOWS panel visibility
2. Reading the embedded JSON from `#swot-data` if needed for dynamic rendering

No external libraries. No build tools. Works in any modern browser.

## Embedded Data

The full `swot-data.json` content is embedded in a `<script type="application/json">` tag with id `swot-data`. This allows:
- Programmatic extraction of the data from the HTML file
- Re-rendering or transformation without the original JSON file
- Integration with other tools that can parse the embedded block

## File Naming

Output file: `swot-matrix.html`
Location: `Strategy/Output/swot/{subject-slug}-{YYYY-MM-DD}/swot-matrix.html`
