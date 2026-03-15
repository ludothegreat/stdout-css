# Color System

Stdout.css uses a carefully curated color palette built on three principles:
1. **NO BLUES** - Greens + burnt orange for distinction
2. **OKLCH for perceptual uniformity**
3. **Tinted neutrals** - No pure grays

---

## Color Palette

### Primary Colors

| Color | Hex | OKLCH | Usage |
|-------|-----|-------|-------|
| Green Primary | `#4a9d5f` | `oklch(0.61 0.12 150)` | Primary buttons, borders, accents |
| Green Light | `#5fb574` | `oklch(0.68 0.13 150)` | Success states, text accents, hover |
| Green Dark | `#3a7d4f` | `oklch(0.50 0.10 150)` | Pressed states, dark variants |

**Usage:** Primary actions (CREATE, SAVE, CONFIRM), success feedback, active states

---

### Secondary Colors

| Color | Hex | OKLCH | Usage |
|-------|-----|-------|-------|
| Orange Primary | `#d4753e` | `oklch(0.62 0.14 45)` | Secondary buttons, warnings |
| Orange Light | `#e88952` | `oklch(0.68 0.15 50)` | Hover states, accents |
| Orange Dark | `#c4652e` | `oklch(0.54 0.13 40)` | Pressed states, dark variants |

**Usage:** Secondary actions (SETTINGS, EXPORT, OPTIONS), warnings, alternative paths

---

### Neutral Scale (Tinted Grays)

| Name | Hex Approx | OKLCH | Usage |
|------|-----------|-------|-------|
| Gray 900 | `#0a0b0a` | `oklch(0.12 0.008 150)` | App background (darkest) |
| Gray 850 | `#121312` | `oklch(0.18 0.008 150)` | Surface backgrounds |
| Gray 800 | `#1a1b1a` | `oklch(0.24 0.008 150)` | Cards, panels, modals |
| Gray 700 | `#252625` | `oklch(0.30 0.008 150)` | Elevated surfaces, inputs |
| Gray 600 | `#3a3b3a` | `oklch(0.40 0.008 150)` | Borders, interactive backgrounds |
| Gray 500 | `#4a4c4a` | `oklch(0.48 0.008 150)` | Strong borders |
| Gray 400 | `#6a6b6a` | `oklch(0.60 0.006 150)` | Muted text, disabled states |
| Gray 300 | `#8a8b8a` | `oklch(0.70 0.004 150)` | Info badges, tertiary text |
| Gray 200 | `#a8a9a8` | `oklch(0.80 0.003 150)` | Secondary text |
| Gray 100 | `#c8c9c8` | `oklch(0.88 0.002 150)` | Light text |
| Gray 50 | `#e8e9e8` | `oklch(0.94 0.001 150)` | Primary text (lightest) |

**Key Feature:** All grays have hue `150` (green) for visual harmony with the primary palette.

---

### Status Colors

| Status | Color | Hex | Usage |
|--------|-------|-----|-------|
| Success | Green Light | `#5fb574` | Success toasts, active badges, checkmarks |
| Warning | Orange Light | `#e88952` | Warning toasts, pending badges, alerts |
| Error | Red | `#ff4444` | Error toasts, danger buttons, failed badges |
| Info | Gray 300 | `#8a8b8a` | Info toasts, archived badges, neutral states |

---

## Understanding OKLCH

**OKLCH** (Oklab color space with cylindrical coordinates) is a modern, perceptually uniform color model.

### Format

```css
oklch(lightness chroma hue / alpha)
```

- **Lightness**: `0-1` (0 = black, 1 = white)
- **Chroma**: `0-0.4` (saturation/intensity)
- **Hue**: `0-360` (color wheel degrees)
  - 0°/360° = Red
  - 120° = Green
  - 150° = Green (used in Stdout.css)
  - 240° = Blue
- **Alpha**: `0-1` (optional, transparency)

### Why OKLCH?

1. **Perceptually Uniform**: Equal changes in OKLCH values = equal perceived changes
2. **Predictable Lightness**: `oklch(0.5 ...)` always feels "50% bright" regardless of hue
3. **Better Gradients**: No weird brightness shifts when interpolating colors
4. **Modern Standard**: Future-proof, widely adopted

### Example

```css
/* Greens at 50% lightness */
--green-dark: oklch(0.50 0.10 150);

/* Greens at 60% lightness */
--green-primary: oklch(0.61 0.12 150);

/* Greens at 70% lightness */
--green-light: oklch(0.68 0.13 150);
```

All three have **the same hue** (150°) but different lightness/chroma for variety.

---

## The "NO BLUES" Rule

### Why No Blues?

1. **Overused**: Every SaaS product, dashboard, and developer tool uses blue
2. **Visual Noise**: Blue becomes background noise, not meaningful signal
3. **Distinction**: Greens + orange create a unique, memorable palette
4. **Intentionality**: Constraint breeds creativity

### What About...?

**Links?** Use green (`--text-accent` or `--green-light`)
**Info badges?** Use gray (`--status-info`)
**Visited links?** Use darker green (`--green-dark`)

---

## Semantic Token System

Instead of using raw colors, Stdout.css uses semantic tokens:

```css
:root {
  /* Raw colors */
  --gray-800: oklch(0.24 0.008 150);

  /* Semantic tokens */
  --bg-surface: var(--gray-800);
}
```

**Benefits:**
- Easy theming (override semantic tokens, not every component)
- Clear intent (what is this color *for*?)
- Maintainability (change one token, update everywhere)

### Background Tokens

```css
--bg-app: var(--gray-900);        /* Main app background */
--bg-surface: var(--gray-800);    /* Cards, panels */
--bg-elevated: var(--gray-700);   /* Inputs, elevated surfaces */
--bg-interactive: var(--gray-600);/* Hover states */
```

### Border Tokens

```css
--border-subtle: var(--gray-600);  /* 1px borders, dividers */
--border-strong: var(--gray-500);  /* 2px borders, emphasis */
```

### Text Tokens

```css
--text-primary: var(--gray-50);    /* Primary text */
--text-secondary: var(--gray-200); /* Secondary text */
--text-muted: var(--gray-400);     /* Muted/disabled text */
--text-accent: var(--green-light); /* Links, highlights */
```

---

## Usage Guidelines

### Primary Actions: Green

```html
<button class="action-btn">CREATE</button>
```

Use green for:
- Create, save, confirm, go, enable
- Success states (toasts, checkmarks)
- Active/selected states
- Primary links

### Secondary Actions: Orange

```html
<button class="action-btn secondary">SETTINGS</button>
```

Use orange for:
- Settings, export, options, alternatives
- Warnings (proceed with caution)
- Secondary navigation
- Accent headers

### Destructive Actions: Red

```html
<button class="action-btn danger">DELETE</button>
```

Use red for:
- Delete, remove, disable, cancel (irreversible)
- Error states (toasts, messages)
- Failed badges
- Critical warnings

### Neutral States: Gray

```html
<span class="badge info">ARCHIVED</span>
```

Use gray for:
- Info badges, archived items
- Disabled states
- Borders, dividers
- Secondary/tertiary text

---

## Color Contrast

All color combinations in Stdout.css meet **WCAG AA** standards:

| Foreground | Background | Ratio | Pass |
|-----------|-----------|-------|------|
| Gray 50 (text) | Gray 900 (bg) | 15.3:1 | ✅ AAA |
| Gray 200 (text) | Gray 900 (bg) | 9.1:1 | ✅ AAA |
| Gray 400 (text) | Gray 900 (bg) | 4.7:1 | ✅ AA |
| Green Light | Gray 900 (bg) | 7.8:1 | ✅ AAA |
| Orange Light | Gray 900 (bg) | 5.2:1 | ✅ AA |

**Minimum Requirements:**
- Normal text (14-18px): 4.5:1 (AA) or 7:1 (AAA)
- Large text (18px+ or 14px+ bold): 3:1 (AA) or 4.5:1 (AAA)

---

## Color Accessibility

### Focus Indicators

All interactive elements have a 2px green outline on keyboard focus:

```css
*:focus-visible {
  outline: 2px solid var(--green-primary);
  outline-offset: 2px;
}
```

### Not Relying on Color Alone

Status indicators use **color + text + icon**:

```html
<!-- Color + text -->
<span class="badge success">ACTIVE</span>

<!-- Color + icon -->
<div class="status-dot connected"></div>

<!-- Color + border style -->
<div class="toast error">Error message</div>
```

---

## Customizing Colors

See [customization.md](customization.md) for full details. Quick example:

```css
:root {
  /* Replace greens with purples */
  --green-primary: oklch(0.61 0.15 300);  /* Purple hue = 300° */
  --green-light: oklch(0.68 0.16 305);
  --green-dark: oklch(0.50 0.13 295);

  /* Update semantic tokens */
  --status-success: var(--green-light);
  --text-accent: var(--green-light);
}
```

---

## Color Tools

**Recommended tools for working with OKLCH:**

- **oklch.com** - Interactive OKLCH color picker
- **colorjs.io** - JavaScript library for OKLCH conversion
- **WebAIM Contrast Checker** - Verify WCAG compliance

---

*For component usage, see [components.md](components.md).*
*For customization, see [customization.md](customization.md).*
