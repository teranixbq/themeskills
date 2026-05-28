---
name: stocktaper-vintage-editorial
displayName: StockTaper Vintage Editorial Theme
description: Retro newspaper and premium financial editorial web theme patterns. Enforces global monospace typography, warm parchment backgrounds (#F5F0E8), sharp square corners (zero border-radius), and signature dashed borders. Includes layout definitions for 3-column article feeds, left-sticky article navigation, right-side data widgets (market snapshots), pill-shaped search bars, and rules for monochrome crosshatch illustrations.
version: 1.0.0
---

# StockTaper Vintage Editorial Theme Skills

## Theme Overview
A **retro newspaper / vintage editorial** web theme inspired by [stocktaper.com](https://www.stocktaper.com/). The design evokes a classic broadsheet newspaper aesthetic with warm parchment backgrounds, monospace typewriter fonts, hand-drawn pen-and-ink illustrations, and deliberate use of dashed borders — creating a premium, editorial feel that is both nostalgic and modern.

---

## 1. Color Palette

### Background Colors
| Token | Value | Usage |
|---|---|---|
| `--bg-primary` | `#F5F0E8` | Page background — warm parchment/aged paper |
| `--bg-secondary` | `#EDE8DF` | Card backgrounds, sidebar panels |
| `--bg-hero` | `#F5F0E8` | Hero section background |
| `--bg-footer` | `#F5F0E8` | Footer background (same as page) |
| `--bg-button-primary` | `#2C2C2C` | Primary CTA buttons (dark charcoal) |
| `--bg-button-hover` | `#1A1A1A` | Button hover state |

### Text Colors
| Token | Value | Usage |
|---|---|---|
| `--text-primary` | `#2C2C2C` | Main headings, titles |
| `--text-body` | `#3D3D3D` | Body text, article content |
| `--text-muted` | `#6B6B6B` | Meta info, dates, read time |
| `--text-link` | `#2C2C2C` | Links (underlined, no color change) |
| `--text-link-hover` | `#000000` | Link hover |
| `--text-on-dark` | `#FFFFFF` | Text on dark buttons |
| `--text-accent-red` | `#C0392B` | Sale/alert badges, special labels |
| `--text-accent-green` | `#27AE60` | Positive indicators |

### Border Colors
| Token | Value | Usage |
|---|---|---|
| `--border-primary` | `#C4BEB4` | Section dividers, card borders |
| `--border-dashed` | `#B0A99F` | Dashed separator lines |
| `--border-dark` | `#2C2C2C` | Strong borders on buttons/inputs |

---

## 2. Typography

### Font Stack
```css
/* Primary — Monospace / Typewriter */
--font-heading: 'IBM Plex Mono', 'Courier New', Courier, monospace;
--font-body: 'IBM Plex Mono', 'Courier New', Courier, monospace;

/* Alternative that also matches the aesthetic */
--font-alt-heading: 'Space Mono', 'Courier New', monospace;
--font-alt-body: 'DM Mono', 'Courier New', monospace;
```

> **Key Insight**: The entire site uses a **monospace font** for ALL text — headings, body, navigation, buttons. This is the single most defining typographic choice of the theme.

### Font Sizes & Weights
| Element | Size | Weight | Style |
|---|---|---|---|
| H1 (Hero Title) | `2.5rem – 3rem` | `700` (Bold) | Normal |
| H2 (Section Title) | `1.75rem – 2rem` | `700` (Bold) | Normal |
| H3 (Card Title) | `1.1rem – 1.25rem` | `700` (Bold) | Normal |
| Body Text | `0.9rem – 1rem` | `400` (Regular) | Normal |
| Meta / Caption | `0.8rem – 0.85rem` | `400` | Normal |
| Navigation | `0.9rem` | `400` | Normal |
| Button Text | `0.9rem` | `600` | Normal |

### Line Height
```css
--line-height-heading: 1.3;
--line-height-body: 1.7;
--line-height-tight: 1.2;
```

### Text Treatment
- **No text-transform** on most elements (natural case)
- **Underline** on links (classic editorial style)
- **Letter-spacing**: `0` or very minimal — no wide tracking
- Headlines use **period at end of sentences** (editorial style: "Look up a stock. Actually get it.")

---

## 3. Layout & Grid System

### Page Structure
```
┌──────────────────────────────────────────────┐
│  HEADER (Logo left, Nav right)               │
├──────────────────────────────────────────────┤
│  HERO SECTION (Text left, Illustration right)│
├──────────────────────────────────────────────┤
│  FEATURES (Cards in a grid)                  │
├──────────────────────┬───────────────────────┤
│  ARTICLES (3-col)    │  SIDEBAR (right)      │
│  Latest Articles     │  Market Snapshot      │
│  grid                │  Senate/House Trades  │
├──────────────────────┴───────────────────────┤
│  FOOTER (3-column links)                     │
└──────────────────────────────────────────────┘
```

### Container
```css
--container-max-width: 1200px;
--container-padding: 0 2rem;
```

### Grid Patterns
```css
/* Articles Grid — 3 columns */
.articles-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}

/* Main + Sidebar Layout */
.content-layout {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 2rem;
}

/* Article Detail — 3-column with sidebar */
.article-detail-layout {
  display: grid;
  grid-template-columns: 250px 1fr 300px;
  gap: 2rem;
}

/* Feature Cards */
.features-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}
```

---

## 4. Component Library

### 4.1 Navigation Bar
```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background: var(--bg-primary);
  /* No border-bottom — clean look */
}

.navbar-logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 700;
  font-size: 1.1rem;
  font-family: var(--font-heading);
  border: 2px solid var(--border-dark);
  padding: 0.4rem 0.8rem;
}

.navbar-links a {
  font-family: var(--font-body);
  text-decoration: none;
  color: var(--text-primary);
  margin-left: 1.5rem;
  font-size: 0.9rem;
}

.navbar-links a:hover {
  text-decoration: underline;
}
```

### 4.2 Hero Section
```css
.hero {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 4rem 2rem;
  min-height: 70vh;
}

.hero-text {
  max-width: 50%;
}

.hero-title {
  font-size: 2.8rem;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 1.5rem;
}

.hero-description {
  font-size: 1rem;
  line-height: 1.7;
  color: var(--text-body);
  margin-bottom: 2rem;
}

.hero-illustration {
  max-width: 45%;
  /* Hand-drawn pen-and-ink style illustration */
  /* Black & white, crosshatching technique */
}
```

### 4.3 Search Bar
```css
.search-bar {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.8rem 1.2rem;
  border: 2px solid var(--border-dark);
  border-radius: 50px; /* Pill shape */
  background: transparent;
  font-family: var(--font-body);
  font-size: 0.95rem;
  width: 100%;
  max-width: 480px;
}

.search-bar:focus-within {
  border-color: #000;
  box-shadow: 0 0 0 1px #000;
}
```

### 4.4 Buttons
```css
/* Primary Button (Dark) */
.btn-primary {
  background: var(--bg-button-primary);
  color: var(--text-on-dark);
  font-family: var(--font-body);
  font-size: 0.9rem;
  font-weight: 600;
  padding: 0.7rem 1.8rem;
  border: 2px solid var(--bg-button-primary);
  cursor: pointer;
  transition: background 0.2s ease;
  /* NO border-radius — square/sharp edges */
}

.btn-primary:hover {
  background: var(--bg-button-hover);
}

/* Secondary / Outline Button */
.btn-outline {
  background: transparent;
  color: var(--text-primary);
  border: 2px solid var(--border-dark);
  padding: 0.5rem 1.2rem;
  font-family: var(--font-body);
  cursor: pointer;
}
```

### 4.5 Article Cards
```css
.article-card {
  display: flex;
  flex-direction: column;
  padding: 0;
  border: none;
  /* No card background — transparent */
  /* Content separated by whitespace, not borders */
}

.article-card-image {
  width: 100%;
  aspect-ratio: 4/3;
  object-fit: cover;
  margin-bottom: 0.75rem;
  /* Images are black & white pen-and-ink illustrations */
  /* OR no image — text-only cards */
}

.article-card-title {
  font-size: 1.15rem;
  font-weight: 700;
  line-height: 1.3;
  margin-bottom: 0.5rem;
  color: var(--text-primary);
}

.article-card-excerpt {
  font-size: 0.85rem;
  line-height: 1.6;
  color: var(--text-body);
  margin-bottom: 0.5rem;
}

.article-card-meta {
  font-size: 0.8rem;
  color: var(--text-muted);
  /* Format: "4 min read · May 8, 2026" */
}
```

### 4.6 Feature Cards
```css
.feature-card {
  padding: 1.5rem;
  border: 2px dashed var(--border-dashed);
  background: transparent;
}

.feature-card-title {
  font-size: 0.85rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.5rem;
}

.feature-card-subtitle {
  font-size: 1rem;
  font-weight: 400;
  margin-bottom: 1rem;
}

.feature-card-list {
  list-style: none;
  padding: 0;
}

.feature-card-list li {
  font-size: 0.85rem;
  line-height: 1.6;
  padding-left: 1rem;
}

.feature-card-list li::before {
  content: "•";
  margin-right: 0.5rem;
}
```

### 4.7 Sidebar Widgets
```css
/* Market Snapshot / Data Widget */
.sidebar-widget {
  padding: 1.25rem;
  border: 1px dashed var(--border-dashed);
  margin-bottom: 1.5rem;
}

.sidebar-widget-title {
  font-size: 1rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

/* Stock/Data Row */
.data-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 0;
  border-bottom: 1px dashed var(--border-dashed);
}

.data-row:last-child {
  border-bottom: none;
}

.data-row-icon {
  width: 24px;
  height: 24px;
  margin-right: 0.5rem;
}

.data-row-label {
  font-weight: 700;
  font-size: 0.85rem;
}

.data-row-sublabel {
  font-size: 0.75rem;
  color: var(--text-muted);
}

.data-row-value {
  font-size: 0.85rem;
  font-weight: 400;
  text-align: right;
}
```

### 4.8 Footer
```css
.footer {
  padding: 3rem 2rem;
  border-top: 1px dashed var(--border-dashed);
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.footer-section-title {
  font-size: 0.9rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.footer-links {
  list-style: none;
  padding: 0;
}

.footer-links li {
  margin-bottom: 0.5rem;
}

.footer-links a {
  font-size: 0.85rem;
  color: var(--text-body);
  text-decoration: none;
}

.footer-links a:hover {
  text-decoration: underline;
}

.footer-copyright {
  font-size: 0.8rem;
  color: var(--text-muted);
  margin-top: 2rem;
}
```

---

## 5. Article Detail Page

### 5.1 Layout Structure
```
┌──────────────────────────────────────────────────────┐
│  HEADER (same as homepage)                           │
├──────────┬─────────────────────────┬─────────────────┤
│ LEFT     │  MAIN ARTICLE CONTENT   │  RIGHT SIDEBAR  │
│ SIDEBAR  │                         │                 │
│          │  [← All articles]       │  Market Snapshot│
│ Article  │  [Tag Badge]            │  Senate Trades  │
│ List     │  [TITLE]                │  House Trades   │
│ (nav)    │  [Illustration]         │                 │
│          │  [Article Body]         │                 │
│          │  [Related Stocks]       │                 │
│          │  [Related Articles]     │                 │
├──────────┴─────────────────────────┴─────────────────┤
│  FOOTER                                              │
└──────────────────────────────────────────────────────┘
```

### 5.2 Left Sidebar (Article Navigation)
```css
.article-sidebar-nav {
  position: sticky;
  top: 2rem;
  max-height: calc(100vh - 4rem);
  overflow-y: auto;
  padding-right: 1rem;
  border-right: 1px dashed var(--border-dashed);
}

.article-sidebar-nav a.back-link {
  font-size: 0.85rem;
  color: var(--text-primary);
  text-decoration: none;
  display: block;
  margin-bottom: 1rem;
}

.article-sidebar-nav .article-list-item {
  display: block;
  padding: 0.6rem 0;
  border-bottom: 1px dashed var(--border-dashed);
  font-size: 0.8rem;
  color: var(--text-body);
  text-decoration: none;
  line-height: 1.4;
}

.article-sidebar-nav .article-list-item:hover {
  color: var(--text-primary);
}

.article-sidebar-nav .article-list-item .date {
  display: block;
  font-size: 0.75rem;
  color: var(--text-muted);
  margin-top: 0.2rem;
}
```

### 5.3 Article Content Area
```css
.article-header {
  margin-bottom: 2rem;
}

.article-tag {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  padding: 0.2rem 0.6rem;
  border: 1px solid var(--border-dark);
  margin-bottom: 1rem;
  text-transform: capitalize;
}

.article-title {
  font-size: 2rem;
  font-weight: 700;
  line-height: 1.25;
  margin-bottom: 1.5rem;
}

.article-hero-illustration {
  width: 100%;
  max-height: 400px;
  object-fit: contain;
  margin-bottom: 2rem;
  /* Black & white pen-and-ink style illustration */
}

.article-body {
  font-size: 0.95rem;
  line-height: 1.8;
  color: var(--text-body);
}

.article-body h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin-top: 2.5rem;
  margin-bottom: 1rem;
  color: var(--text-primary);
}

.article-body p {
  margin-bottom: 1.25rem;
}

.article-body ul {
  padding-left: 1.5rem;
  margin-bottom: 1.25rem;
}

.article-body ul li {
  margin-bottom: 0.5rem;
  line-height: 1.7;
}

.article-body a {
  color: var(--text-primary);
  text-decoration: underline;
}

/* Key Takeaways / Summary Box */
.article-summary-box {
  padding: 1.25rem;
  border: 2px dashed var(--border-dashed);
  margin: 2rem 0;
  background: transparent;
}

.article-summary-box li {
  font-weight: 600;
  margin-bottom: 0.5rem;
}
```

### 5.4 Related Stocks Section
```css
.related-stocks {
  margin-top: 2rem;
  padding-top: 1.5rem;
  border-top: 1px dashed var(--border-dashed);
}

.related-stocks-title {
  font-size: 0.9rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
}

.related-stocks-list {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.stock-tag {
  display: inline-block;
  padding: 0.3rem 0.8rem;
  border: 1px solid var(--border-dark);
  font-size: 0.8rem;
  font-weight: 600;
  text-decoration: none;
  color: var(--text-primary);
}

.stock-tag:hover {
  background: var(--bg-button-primary);
  color: var(--text-on-dark);
}
```

### 5.5 Related Articles Section
```css
.related-articles {
  margin-top: 3rem;
  padding-top: 2rem;
  border-top: 2px dashed var(--border-dashed);
}

.related-articles-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}

/* Each related article card uses same .article-card styles */
```

---

## 6. Illustrations & Imagery Style

### Illustration Guidelines
- **Style**: Black & white **pen-and-ink** / **crosshatching** technique
- **Subject**: Whimsical, editorial illustrations (e.g., astronaut reading stocks, person with telescope)
- **Colors**: Strictly **monochrome** — black ink on transparent/white background
- **Complexity**: Detailed with fine line work, vintage engraving feel
- **Usage**: Hero section, article headers, occasional inline illustrations
- **No photographs** — only hand-drawn style illustrations

### Icon Style
- Company logos (for stock tickers) use **actual brand logos** in small format
- UI icons are minimal line-style, matching the monospace/editorial aesthetic
- Congress member photos use small **circular grayscale portraits**

---

## 7. Borders & Dividers

This is a **critical design element** of the theme:

```css
/* Dashed borders — the signature separator */
--border-dashed-style: 1px dashed var(--border-dashed);
--border-dashed-heavy: 2px dashed var(--border-dashed);

/* Used for: */
/* - Section dividers */
/* - Card outlines (feature cards) */
/* - Table row separators */
/* - Sidebar widget borders */
/* - Footer top border */
/* - Between data rows (stock list, trades list) */

/* Solid borders — used sparingly */
--border-solid-style: 2px solid var(--border-dark);
/* Used for: logo container, buttons, search bar, article tags */
```

> **Key Insight**: Dashed borders are the **visual DNA** of this theme. They replace solid lines almost everywhere, creating the vintage newspaper feel.

---

## 8. Spacing System

```css
--space-xs: 0.25rem;   /* 4px */
--space-sm: 0.5rem;    /* 8px */
--space-md: 1rem;      /* 16px */
--space-lg: 1.5rem;    /* 24px */
--space-xl: 2rem;      /* 32px */
--space-2xl: 3rem;     /* 48px */
--space-3xl: 4rem;     /* 64px */

/* Section padding */
--section-padding: 3rem 0;

/* Card internal padding */
--card-padding: 1.25rem;
```

---

## 9. Animations & Interactions

### Minimal — Intentionally Understated
```css
/* Links */
a {
  transition: color 0.2s ease, text-decoration 0.2s ease;
}

/* Buttons */
.btn-primary {
  transition: background-color 0.2s ease, transform 0.1s ease;
}
.btn-primary:active {
  transform: scale(0.98);
}

/* Cards */
.article-card {
  transition: opacity 0.2s ease;
}
.article-card:hover {
  opacity: 0.85;
}

/* NO flashy animations, parallax, or scroll effects */
/* The theme is intentionally static and print-like */
```

> **Key Insight**: The vintage editorial aesthetic demands **restraint** in animation. The site feels like a printed newspaper brought to screen.

---

## 10. Responsive Design

```css
/* Tablet (< 1024px) */
@media (max-width: 1024px) {
  .content-layout {
    grid-template-columns: 1fr;
  }
  .article-detail-layout {
    grid-template-columns: 1fr;
  }
  .articles-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  /* Left sidebar becomes hidden or collapsible */
}

/* Mobile (< 768px) */
@media (max-width: 768px) {
  .hero {
    flex-direction: column;
    text-align: center;
  }
  .hero-text { max-width: 100%; }
  .hero-illustration { max-width: 80%; margin-top: 2rem; }
  .articles-grid {
    grid-template-columns: 1fr;
  }
  .features-grid {
    grid-template-columns: 1fr;
  }
  .footer {
    grid-template-columns: 1fr;
  }
  .related-articles-grid {
    grid-template-columns: 1fr;
  }
  .hero-title { font-size: 2rem; }
}
```

---

## 11. Design Principles Summary

| Principle | Implementation |
|---|---|
| **Monospace Everything** | All text uses monospace fonts — headings, body, nav, buttons |
| **Warm Parchment BG** | `#F5F0E8` background creates aged paper feel |
| **Dashed Borders** | Primary separator style — not solid lines |
| **B&W Illustrations** | Pen-and-ink crosshatch art, no photography |
| **No Border Radius** | Buttons and cards have sharp/square corners |
| **Minimal Animation** | Print-like stillness, subtle hovers only |
| **Editorial Typography** | Headlines end with periods, classic editorial copy style |
| **3-Column Article Layout** | Left nav sidebar + content + right data sidebar |
| **Data-Heavy Sidebar** | Market caps, congress trades, stock data on right |
| **Text-Dense Cards** | Article cards are text-heavy with minimal imagery |

---

## 12. Full CSS Variables Template

```css
:root {
  /* Colors */
  --bg-primary: #F5F0E8;
  --bg-secondary: #EDE8DF;
  --text-primary: #2C2C2C;
  --text-body: #3D3D3D;
  --text-muted: #6B6B6B;
  --text-on-dark: #FFFFFF;
  --accent-red: #C0392B;
  --accent-green: #27AE60;
  --border-primary: #C4BEB4;
  --border-dashed: #B0A99F;
  --border-dark: #2C2C2C;
  --btn-primary-bg: #2C2C2C;
  --btn-primary-hover: #1A1A1A;

  /* Typography */
  --font-primary: 'IBM Plex Mono', 'Courier New', Courier, monospace;
  --font-size-hero: 2.8rem;
  --font-size-h2: 1.75rem;
  --font-size-h3: 1.15rem;
  --font-size-body: 0.95rem;
  --font-size-small: 0.85rem;
  --font-size-meta: 0.8rem;
  --line-height-heading: 1.25;
  --line-height-body: 1.7;

  /* Spacing */
  --space-xs: 0.25rem;
  --space-sm: 0.5rem;
  --space-md: 1rem;
  --space-lg: 1.5rem;
  --space-xl: 2rem;
  --space-2xl: 3rem;
  --space-3xl: 4rem;
  --container-max: 1200px;

  /* Borders */
  --border-dashed-style: 1px dashed var(--border-dashed);
  --border-dashed-heavy: 2px dashed var(--border-dashed);
  --border-solid-style: 2px solid var(--border-dark);
  --border-radius: 0;

  /* Transitions */
  --transition-fast: 0.15s ease;
  --transition-normal: 0.2s ease;
}
```

---

## 13. Implementation Checklist

When generating a website with this theme:

- [ ] Set page background to warm parchment `#F5F0E8`
- [ ] Load `IBM Plex Mono` from Google Fonts
- [ ] Apply monospace font to ALL elements
- [ ] Use dashed borders (`border-style: dashed`) as primary separators
- [ ] Set `border-radius: 0` on all buttons, cards, inputs
- [ ] Use black & white pen-and-ink illustrations (no photos)
- [ ] Create 3-column layout for article detail pages
- [ ] Include right sidebar with data widgets
- [ ] Use text-heavy article cards (minimal imagery)
- [ ] Keep animations minimal — only subtle hover effects
- [ ] Use sharp/square corners everywhere
- [ ] Apply editorial typography (periods in headlines, structured copy)
- [ ] Structure footer as 3-column grid with dashed top border
- [ ] Implement pill-shaped search bar with solid border
- [ ] Logo in bordered container (solid border box)
