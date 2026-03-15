# Typography

Stdout.css uses a three-font system: **monospace for display**, **sans-serif for prose**, and **monospace for code**.

---

## Font Stacks

### Display (Headings)

```css
--font-display: 'Space Mono', 'Courier New', monospace;
```

**Characteristics:**
- Monospace (fixed-width)
- Used for h1-h6 headings
- Always uppercase with letter-spacing
- Creates rhythm and structure

**Use for:**
- Page titles
- Section headings
- Component titles
- Modal headers

**Fallback chain:**
1. Space Mono (Google Fonts, preferred)
2. Courier New (widely available monospace)
3. Generic monospace

---

### Body (Prose)

```css
--font-body: 'IBM Plex Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

**Characteristics:**
- Clean, readable sans-serif
- Used for paragraphs, labels, help text
- Normal case (not uppercase)
- Optimized for extended reading

**Use for:**
- Descriptions
- Form labels (when not uppercase)
- Help text
- Long-form content
- Modal body text

**Fallback chain:**
1. IBM Plex Sans (Google Fonts, preferred)
2. -apple-system (San Francisco on macOS/iOS)
3. BlinkMacSystemFont (San Francisco on Chrome/macOS)
4. Segoe UI (Windows)
5. Generic sans-serif

---

### Mono (Code/Data)

```css
--font-mono: 'JetBrains Mono', 'Courier New', monospace;
```

**Characteristics:**
- Highly legible monospace
- Used for code, commands, paths, hashes
- Normal case
- Optimized for technical content

**Use for:**
- Code snippets (`<code>`, `<pre>`)
- Git hashes
- File paths
- Commands
- Repository names
- Technical identifiers
- Keyboard shortcuts (`<kbd>`)

**Fallback chain:**
1. JetBrains Mono (Google Fonts, preferred)
2. Courier New (widely available)
3. Generic monospace

---

## Typography Scale

### Headings

| Level | Font Size | Line Height | Letter Spacing | Weight | Transform |
|-------|-----------|-------------|----------------|--------|-----------|
| `h1` | `clamp(1.5rem, 2vw, 2rem)` | 1.1 | 0.025em | 700 | UPPERCASE |
| `h2` | `clamp(1.25rem, 1.5vw, 1.5rem)` | 1.2 | 0.02em | 700 | UPPERCASE |
| `h3` | `1.25rem` | 1.3 | 0.02em | 700 | UPPERCASE |
| `h4` | `1.125rem` | 1.4 | 0.02em | 700 | UPPERCASE |
| `h5` | `1rem` | 1.4 | 0.02em | 700 | UPPERCASE |

**Fluid sizing:**
- `h1` and `h2` use `clamp()` for responsive sizing
- Scales smoothly between viewport widths
- Mobile: smaller size
- Desktop: larger size

**Letter-spacing:**
- Tighter for larger headings (0.025em at h1)
- Consistent medium spacing (0.02em) for h2-h5
- Creates visual rhythm

---

### Body Text

| Element | Font Size | Line Height | Font |
|---------|-----------|-------------|------|
| Default | `1rem` (14px at root) | 1.5 | `--font-body` |
| Small text | `0.85-0.9rem` | 1.5 | `--font-body` |
| Help text | `0.85rem` | 1.5 | `--font-body` |

**Base size:** 14px on desktop, 16px on mobile (< 1024px)

---

### Code/Monospace

| Element | Font Size | Font |
|---------|-----------|------|
| Inline `<code>` | `0.9em` | `--font-mono` |
| Code block `<pre>` | `0.85rem` | `--font-mono` |
| Keyboard `<kbd>` | `0.75rem` | `--font-mono` |

**Sizing:** Slightly smaller than surrounding text for balance

---

## Typography Patterns

### Page Title

```html
<h1>TERMINAL BRUTALISM</h1>
```

**Styling:**
- Font: Space Mono (monospace)
- Size: Fluid (1.5rem-2rem)
- Transform: UPPERCASE
- Letter-spacing: 0.025em
- Color: `--green-light`

---

### Section Header

```html
<h2>REPOSITORY LIST</h2>
```

**Styling:**
- Font: Space Mono (monospace)
- Size: Fluid (1.25rem-1.5rem)
- Transform: UPPERCASE
- Letter-spacing: 0.02em
- Color: `--text-primary`

---

### Component Title

```html
<h3>CREATE REPOSITORY</h3>
```

**Styling:**
- Font: Space Mono (monospace)
- Size: 1.25rem
- Transform: UPPERCASE
- Letter-spacing: 0.02em
- Color: `--green-light` (in modals)

---

### Form Label

```html
<label class="form-label">REPOSITORY NAME</label>
```

**Styling:**
- Font: JetBrains Mono (monospace)
- Size: 0.85rem
- Transform: UPPERCASE
- Letter-spacing: 0.05em
- Weight: 600
- Color: `--text-secondary`

---

### Body Text / Description

```html
<p>This is a description of the repository. It uses a readable sans-serif font for extended reading.</p>
```

**Styling:**
- Font: IBM Plex Sans (sans-serif)
- Size: 1rem (14px base, 16px mobile)
- Line-height: 1.5
- Color: `--text-primary` or `--text-secondary`

---

### Help Text

```html
<p class="form-help">Only letters, numbers, and hyphens allowed.</p>
```

**Styling:**
- Font: IBM Plex Sans (sans-serif)
- Size: 0.85rem
- Color: `--text-muted`

---

### Code Inline

```html
<p>Clone with <code>git clone ssh://example.com/repo.git</code></p>
```

**Styling:**
- Font: JetBrains Mono (monospace)
- Size: 0.9em (relative to parent)
- Background: None (inherits)
- Color: Inherits

---

### Code Block

```html
<pre><code>npm install
npm run build
npm test</code></pre>
```

**Styling:**
- Font: JetBrains Mono (monospace)
- Size: 0.85rem
- Background: `--gray-800`
- Color: `--text-secondary`
- Padding: `--space-md`

---

### Keyboard Shortcut

```html
<p>Press <kbd>/</kbd> to open command palette</p>
```

**Styling:**
- Font: JetBrains Mono (monospace)
- Size: 0.75rem
- Background: `--gray-600`
- Border: 1px solid `--gray-500`
- Border-radius: 3px
- Padding: 0.25rem 0.5rem

---

## When to Use Which Font

### Use Monospace Display (Space Mono) For:

✅ Page titles
✅ Section headings
✅ Component headers
✅ Modal titles
✅ Anything uppercase and structural

### Use Sans-Serif Body (IBM Plex Sans) For:

✅ Paragraphs
✅ Descriptions
✅ Help text
✅ Long-form content
✅ Anything meant to be read

### Use Monospace Code (JetBrains Mono) For:

✅ Code snippets
✅ Commands (`git push`)
✅ File paths (`/usr/local/bin`)
✅ Git hashes (`a3f2e1b`)
✅ Repository names (`my-project.git`)
✅ Technical identifiers
✅ Keyboard shortcuts
✅ Form labels (uppercase, technical)

---

## Typography Best Practices

### DO:

✅ Use uppercase for headings and labels
✅ Use sentence case for descriptions and help text
✅ Use monospace for technical data
✅ Use sans-serif for prose
✅ Maintain consistent letter-spacing
✅ Use fluid sizing for responsive typography

### DON'T:

❌ Use all caps for long paragraphs (hard to read)
❌ Mix monospace and sans-serif randomly
❌ Use tiny font sizes (<12px) for body text
❌ Forget line-height (1.5 is minimum for readability)
❌ Use decorative fonts (Stdout.css is functional)

---

## Responsive Typography

### Desktop (default, 14px base)

```css
html {
  font-size: 14px;
}
```

### Mobile (< 1024px, 16px base)

```css
@media (max-width: 1024px) {
  html {
    font-size: 16px;  /* Larger for readability on small screens */
  }
}
```

**Effect:** All `rem` units scale proportionally

---

## Loading Custom Fonts

### Google Fonts (Recommended)

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;600&family=JetBrains+Mono:wght@400;600&family=Space+Mono:wght@700&display=swap" rel="stylesheet">
```

**Weights used:**
- IBM Plex Sans: 400 (normal), 600 (semibold)
- JetBrains Mono: 400 (normal), 600 (semibold)
- Space Mono: 700 (bold only, for headings)

### Self-Hosted Fonts

Download fonts and host locally:

```css
@font-face {
  font-family: 'Space Mono';
  src: url('/fonts/SpaceMono-Bold.woff2') format('woff2');
  font-weight: 700;
  font-display: swap;
}

@font-face {
  font-family: 'IBM Plex Sans';
  src: url('/fonts/IBMPlexSans-Regular.woff2') format('woff2');
  font-weight: 400;
  font-display: swap;
}

@font-face {
  font-family: 'JetBrains Mono';
  src: url('/fonts/JetBrainsMono-Regular.woff2') format('woff2');
  font-weight: 400;
  font-display: swap;
}
```

**Benefits:**
- Faster loading (no external requests)
- Privacy (no Google tracking)
- Offline support

**Drawbacks:**
- Manual updates
- Larger initial bundle size

---

## Typography Accessibility

### Readable Line Heights

Body text uses `line-height: 1.5` (minimum for accessibility).

### Sufficient Font Sizes

- Desktop: 14px base (0.875rem)
- Mobile: 16px base (1rem)
- Minimum: 12px (0.75rem) for labels only

### Clear Hierarchy

Headings use distinct sizes and weights to create clear visual hierarchy.

### Contrast

All text meets WCAG AA contrast requirements (see [colors.md](colors.md)).

---

## Customizing Fonts

Override font variables in your stylesheet:

```css
:root {
  --font-display: 'Your Display Font', monospace;
  --font-body: 'Your Body Font', sans-serif;
  --font-mono: 'Your Code Font', monospace;
}
```

**Recommendations:**
- Display: Any monospace with strong character
- Body: Any readable sans-serif (Inter, Roboto, Open Sans)
- Mono: Any legible code font (Fira Code, Source Code Pro, Consolas)

---

*For component usage, see [components.md](components.md).*
*For customization, see [customization.md](customization.md).*
