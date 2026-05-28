# Data Science & Analysis Report Theme Skills (Vintage Editorial)

## Theme Overview
A **Vintage Editorial Data Science Report** theme that marries the rigorous structure of a technical report (code blocks, mathematical formulas, wide data tables) with the aesthetic of a classic financial broadsheet newspaper (inspired by StockTaper). 

Instead of the typical sterile, hyper-modern tech blog look, this theme uses warm parchment backgrounds, strict monospace typography, hand-drawn style charts, and dashed borders to create a sophisticated, nostalgic, yet highly readable "research paper from the 1970s terminal era" feel.

---

## 1. Color Palette

### Background Colors
| Token | Value | Usage |
|---|---|---|
| `--bg-primary` | `#F5F0E8` | Main page background (warm parchment/aged paper) |
| `--bg-secondary` | `#EDE8DF` | Secondary sections, sidebars |
| `--bg-code` | `#2C2C2C` | Code block backgrounds (dark charcoal / terminal feel) |
| `--bg-highlight` | `#E3DAC9` | Highlighted text, table header backgrounds |

### Text Colors
| Token | Value | Usage |
|---|---|---|
| `--text-primary` | `#2C2C2C` | Main headings, critical UI elements (dark charcoal ink) |
| `--text-body` | `#3D3D3D` | Article body text |
| `--text-muted` | `#6B6B6B` | Captions, sidenotes, axis labels on charts |
| `--text-link` | `#2C2C2C` | Interactive links (underlined, no color change) |
| `--text-link-hover`| `#000000` | Link hover state |
| `--text-code-light`| `#F5F0E8` | Base text color inside dark code blocks |

### Data Visualization Accents (Vintage / Muted)
*Instead of bright neon colors, charts use muted, ink-like tones.*
| Token | Value | Usage |
|---|---|---|
| `--chart-ink` | `#2C2C2C` | Primary data series (Black ink) |
| `--chart-sepia` | `#8B5A2B` | Secondary data series (Brown/Sepia) |
| `--chart-faded-red`| `#A52A2A` | Anomalies / Negative correlation (Brick Red) |
| `--chart-navy` | `#1A365D` | Comparison series (Dark Navy Blue) |
| `--chart-olive` | `#556B2F` | Tertiary data (Olive Green) |

---

## 2. Typography

### Font Stack
```css
/* ALL text uses a Typewriter/Monospace font to maintain the vintage aesthetic */
--font-mono: 'IBM Plex Mono', 'Courier New', Courier, monospace;
```

> **Key Insight**: There are NO sans-serif or serif fonts in this theme. The entire report (headings, body paragraphs, code, math explanations, data tables) uses the monospace font, giving it an authentic typed-document or teletype feel.

### Font Sizes & Weights
| Element | Size | Weight | Line Height |
|---|---|---|---|
| H1 (Report Title) | `2.5rem - 3rem`| `700` (Bold) | `1.2` |
| H2 (Section) | `1.75rem` | `700` (Bold) | `1.3` |
| H3 (Subsection) | `1.15rem` | `700` (Bold) | `1.4` |
| Body Text | `0.95rem` | `400` (Regular) | `1.7` |
| Sidenotes / Captions| `0.8rem` | `400` (Regular) | `1.5` |
| Code Blocks | `0.85rem` | `400` (Regular) | `1.6` |

---

## 3. Layout & Grid System

### Page Structure
```
┌────────────────────────────────────────────────────────┐
│  HEADER (Logo in solid box left, Nav right)            │
├────────────────────────────────────────────────────────┤
│  REPORT HEADER (Title, Authors, Date - Monospace)      │
├───────────┬──────────────────────────────┬─────────────┤
│ TABLE OF  │                              │ MARGINALIA  │
│ CONTENTS  │  MAIN CONTENT COLUMN         │ (Sidenotes) │
│ (Dashed   │  (Max-width: ~720px)         │             │
│  border)  │                              │ [Note 1]    │
│           │  [Paragraphs]                │             │
│           │  [Formulas]                  │ [Ref 2]     │
├───────────┴──────────────────────────────┴─────────────┤
│  BREAKOUT COMPONENTS (Full width or wider than text)   │
│  [Wide Data Table with dashed rows]                    │
│  [Monochrome / Muted Chart]                            │
├───────────┬──────────────────────────────┬─────────────┤
│           │  [More Content]              │             │
└───────────┴──────────────────────────────┴─────────────┘
```

### Layout Rules
```css
/* Center content column */
.article-content {
  max-width: 720px;
  margin: 0 auto;
}

/* Allow data visualizations to break out of the center column */
.breakout-wide {
  width: 100vw;
  max-width: 1024px;
  margin-left: 50%;
  transform: translateX(-50%);
}
```

---

## 4. Technical Component Library

### 4.1 Code Blocks (Teletype Style)
```css
.code-block-wrapper {
  margin: 2rem 0;
  border: 2px solid var(--text-primary);
  background: var(--bg-code); /* Dark charcoal background */
  border-radius: 0; /* NO rounded corners */
}

.code-header {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 1rem;
  border-bottom: 2px solid var(--text-primary);
  background: var(--bg-code);
  color: var(--bg-primary); /* Parchment color for header text */
  font-family: var(--font-mono);
  font-size: 0.8rem;
  text-transform: uppercase;
}

.code-content {
  padding: 1.5rem;
  font-family: var(--font-mono);
  font-size: 0.85rem;
  color: var(--text-code-light); 
  overflow-x: auto;
  /* Syntax highlighting should use muted vintage colors (sepia, dull green, pale blue) */
}
```

### 4.2 Data Tables (Ledger Style)
```css
.data-table-container {
  overflow-x: auto;
  margin: 2.5rem 0;
}

.data-table {
  width: 100%;
  border-collapse: collapse;
  font-family: var(--font-mono);
  font-size: 0.85rem;
  border-top: 2px solid var(--text-primary);
  border-bottom: 2px solid var(--text-primary);
}

.data-table th {
  text-align: left;
  padding: 1rem;
  background: var(--bg-secondary);
  border-bottom: 2px dashed var(--border-dashed);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.data-table td {
  padding: 0.75rem 1rem;
  border-bottom: 1px dashed var(--border-dashed);
  color: var(--text-body);
}

.data-table td.numeric {
  text-align: right;
  /* Monospace inherently handles tabular nums perfectly */
}
```

### 4.3 Math Formulas
```css
.math-block {
  display: flex;
  justify-content: center;
  margin: 2rem 0;
  padding: 1.5rem;
  background: transparent;
  border: 1px dashed var(--border-dashed);
  overflow-x: auto;
  /* Math formulas can use standard math fonts, but keeping it monospace or typewriter-style Math fits the theme perfectly */
}
```

### 4.4 Charts & Data Visualizations
```css
.chart-container {
  margin: 3rem 0;
  padding: 1.5rem;
  border: 1px dashed var(--border-dashed);
  background: transparent;
}

.chart-title {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 1rem;
  margin-bottom: 0.5rem;
  text-transform: uppercase;
}

.chart-caption {
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: var(--text-muted);
  margin-top: 1rem;
  padding-top: 1rem;
  border-top: 1px dashed var(--border-dashed);
}
/* IMPORTANT: Chart gridlines should be dashed. Chart colors should use the muted/vintage palette. No drop shadows. */
```

### 4.5 Marginalia (Sidenotes)
```css
.sidenote-reference {
  vertical-align: super;
  font-size: 0.75em;
  color: var(--text-primary);
  text-decoration: underline;
  cursor: pointer;
}

.sidenote {
  float: right;
  clear: right;
  margin-right: -35%;
  width: 30%;
  margin-top: 0;
  margin-bottom: 1rem;
  font-family: var(--font-mono);
  font-size: 0.75rem;
  line-height: 1.5;
  color: var(--text-muted);
  border-left: 1px dashed var(--border-dashed);
  padding-left: 0.75rem;
}
```

### 4.6 Abstract / TL;DR Box
```css
.abstract-box {
  background: var(--bg-secondary);
  border: 2px solid var(--text-primary);
  padding: 1.5rem 2rem;
  margin: 2rem 0 3rem 0;
  /* No border radius */
}

.abstract-title {
  font-family: var(--font-mono);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-size: 0.85rem;
  color: var(--text-primary);
  margin-bottom: 0.75rem;
}
```

---

## 5. Design Principles Summary

| Principle | Implementation |
|---|---|
| **Monospace Typography** | The entire report uses `IBM Plex Mono` to feel like a vintage printed document or teletype output. |
| **Warm Parchment BG** | `#F5F0E8` background creates the aged paper feel, moving away from harsh white. |
| **Dashed Borders** | Primary separator style for tables, charts, and sidebars. Solid borders reserved for main bounding boxes. |
| **Muted Data Colors** | Charts use ink black, sepia, brick red, and navy instead of bright modern UI colors. |
| **No Border Radius** | Code blocks, abstract boxes, and inputs have sharp/square corners. |
| **Data Breaks Out** | Text column is narrow (~720px), but tables and charts break out wider to show complex data comfortably. |

---

## 6. Implementation Checklist

When generating a Vintage Data Science Report website:

- [ ] Set page background to warm parchment `#F5F0E8`.
- [ ] Import `IBM Plex Mono` and apply it to ALL text (headings, body, tables, code).
- [ ] Set up the narrow center column layout (`max-width: 720px`) for text.
- [ ] Implement `.breakout-wide` utility class for large charts/tables.
- [ ] Use dashed borders (`border-style: dashed`) for table rows, chart containers, and marginalia lines.
- [ ] Add syntax highlighting library configured with a **vintage/muted dark theme** inside a sharp-cornered solid border block.
- [ ] Ensure charts (Chart.js / Recharts) are configured to use dashed grid lines and the vintage color palette (ink, sepia, brick red).
- [ ] Implement Marginalia (sidenotes) in the right margin instead of bottom footnotes.
- [ ] Style the Table of Contents (ToC) on the left sidebar with a dashed right border.
