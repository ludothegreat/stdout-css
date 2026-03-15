# Customization Guide

Stdout.css uses CSS custom properties (variables) for easy theming and customization. Override these variables in your own stylesheet to customize colors, spacing, typography, and more.

---

## How to Customize

Create a custom stylesheet **after** including stdout.css:

```html
<link rel="stylesheet" href="stdout.css">
<link rel="stylesheet" href="custom.css">
```

In `custom.css`, override variables:

```css
:root {
  /* Your customizations */
  --green-primary: #your-color;
  --space-md: 1.25rem;
}
```

---

## Complete Variable Reference

### Colors

#### Brand Colors

```css
--green-primary: #4a9d5f;
--green-light: #5fb574;
--green-dark: #3a7d4f;
--orange-primary: #d4753e;
--orange-light: #e88952;
--orange-dark: #c4652e;
```

**Use cases:**
- `--green-*` - Primary actions, success states, highlights
- `--orange-*` - Secondary actions, warnings, accents

#### Neutral Colors (OKLCH with green tint)

```css
--gray-900: oklch(0.12 0.008 150);  /* ~#0a0b0a - darkest */
--gray-850: oklch(0.18 0.008 150);  /* ~#121312 */
--gray-800: oklch(0.24 0.008 150);  /* ~#1a1b1a */
--gray-700: oklch(0.30 0.008 150);  /* ~#252625 */
--gray-600: oklch(0.40 0.008 150);  /* ~#3a3b3a */
--gray-500: oklch(0.48 0.008 150);  /* ~#4a4c4a */
--gray-400: oklch(0.60 0.006 150);  /* ~#6a6b6a */
--gray-300: oklch(0.70 0.004 150);  /* ~#8a8b8a */
--gray-200: oklch(0.80 0.003 150);  /* ~#a8a9a8 */
--gray-100: oklch(0.88 0.002 150);  /* ~#c8c9c8 */
--gray-50: oklch(0.94 0.001 150);   /* ~#e8e9e8 - lightest */
```

**OKLCH Format**: `oklch(lightness chroma hue)`
- Lightness: 0-1 (0 = black, 1 = white)
- Chroma: 0-0.4 (saturation)
- Hue: 0-360 (color wheel, 150 = green)

#### Semantic Tokens

```css
--bg-app: var(--gray-900);           /* Main app background */
--bg-surface: var(--gray-800);       /* Cards, panels, modals */
--bg-elevated: var(--gray-700);      /* Elevated surfaces, inputs */
--bg-interactive: var(--gray-600);   /* Hover states */
--border-subtle: var(--gray-600);    /* Subtle borders */
--border-strong: var(--gray-500);    /* Strong borders */
--text-primary: var(--gray-50);      /* Primary text */
--text-secondary: var(--gray-200);   /* Secondary text */
--text-muted: var(--gray-400);       /* Muted/disabled text */
--text-accent: var(--green-light);   /* Accent text */
```

#### Status Colors

```css
--status-success: var(--green-light);        /* #5fb574 */
--status-warning: var(--orange-light);       /* #e88952 */
--status-error: oklch(0.63 0.26 29);         /* Red */
--status-info: var(--gray-300);              /* Gray */
```

---

### Typography

```css
--font-display: 'Space Mono', 'Courier New', monospace;
--font-body: 'IBM Plex Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
--font-mono: 'JetBrains Mono', 'Courier New', monospace;
```

**Recommendations:**
- `--font-display` - Monospace for headers (uppercase, letter-spaced)
- `--font-body` - Sans-serif for readable prose
- `--font-mono` - Monospace for code, data, commands

---

### Spacing Scale

```css
--space-xs: 0.25rem;   /* 4px at 16px base */
--space-sm: 0.5rem;    /* 8px */
--space-md: 1rem;      /* 16px */
--space-lg: 1.5rem;    /* 24px */
--space-xl: 2rem;      /* 32px */
--space-2xl: 3rem;     /* 48px */
--space-3xl: 4rem;     /* 64px */
```

**Asymmetric scale** - Not strictly doubling, chosen for visual balance.

---

### Layout

```css
--border-width: 2px;
--focus-ring-color: var(--green-light);  /* All focus outlines */
--table-actions-width: 120px;            /* Data table action column width */
```

`--focus-ring-color` controls every `focus-visible` outline in the framework from a single token. Override it to change all focus indicators at once.

`--table-actions-width` controls the last column of `.data-table` (the actions column). Override per-table if your actions need more space.

**Removed from v1.0** (app-specific):
- `--sidebar-width`
- `--details-width`

---

### Transitions & Easing

```css
--ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
--ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
--ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);

--transition-fast: 150ms var(--ease-out-quart);
--transition-normal: 250ms var(--ease-out-quart);
--transition-slow: 350ms var(--ease-out-expo);
```

**Use:**
- `--transition-fast` - Button presses, quick interactions
- `--transition-normal` - Hover states, most animations
- `--transition-slow` - Dramatic entrances (modals, toasts)

---

## Customization Examples

### Example 1: Different Primary Color

Replace greens with blues (sacrilege, but possible):

```css
:root {
  --green-primary: #4a7d9d;  /* Blue instead of green */
  --green-light: #5f94b5;
  --green-dark: #3a6d8d;
  --status-success: #5f94b5;
  --text-accent: #5f94b5;
}
```

### Example 2: Warmer Neutrals

Change OKLCH hue from 150 (green) to 30 (orange):

```css
:root {
  --gray-900: oklch(0.12 0.008 30);
  --gray-850: oklch(0.18 0.008 30);
  --gray-800: oklch(0.24 0.008 30);
  --gray-700: oklch(0.30 0.008 30);
  --gray-600: oklch(0.40 0.008 30);
  /* etc... */
}
```

### Example 3: Larger Spacing

Increase spacing for more breathing room:

```css
:root {
  --space-md: 1.25rem;   /* Was 1rem */
  --space-lg: 2rem;      /* Was 1.5rem */
  --space-xl: 2.5rem;    /* Was 2rem */
}
```

### Example 4: Custom Fonts

Use your own font stack:

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono&family=Inter&display=swap');

:root {
  --font-display: 'Roboto Mono', monospace;
  --font-body: 'Inter', sans-serif;
  --font-mono: 'Roboto Mono', monospace;
}
```

### Example 5: Faster Animations

Speed up all transitions:

```css
:root {
  --transition-fast: 75ms var(--ease-out-quart);    /* Was 150ms */
  --transition-normal: 125ms var(--ease-out-quart); /* Was 250ms */
  --transition-slow: 175ms var(--ease-out-expo);    /* Was 350ms */
}
```

### Example 6: High Contrast

Increase contrast for better visibility:

```css
:root {
  --bg-app: #000000;           /* Pure black */
  --bg-surface: #0a0a0a;       /* Near black */
  --text-primary: #ffffff;     /* Pure white */
  --border-strong: #666666;    /* Lighter borders */
}
```

---

## Light Mode

Stdout.css ships with built-in `prefers-color-scheme: light` support. Users who have set their OS to light mode will automatically see a light variant, no JavaScript or extra configuration required.

The light mode overrides the semantic tokens (backgrounds, borders, text) while keeping the green/orange brand palette intact. `--green-dark` is used for accent text and focus rings since the standard greens are too light for readable contrast on light backgrounds.

### Forcing light or dark mode

To override the system preference and force a specific theme, override the semantic tokens in `:root`:

```css
/* Force dark mode regardless of system preference */
:root {
  --bg-app:         oklch(0.12 0.008 150);
  --bg-surface:     oklch(0.24 0.008 150);
  --bg-elevated:    oklch(0.30 0.008 150);
  --bg-interactive: oklch(0.40 0.008 150);
  --border-subtle:  oklch(0.40 0.008 150);
  --border-strong:  oklch(0.48 0.008 150);
  --text-primary:   oklch(0.94 0.001 150);
  --text-secondary: oklch(0.80 0.003 150);
  --text-muted:     oklch(0.60 0.006 150);
  --text-accent:    var(--green-light);
  --focus-ring-color: var(--green-light);
}
```

### JavaScript theme toggle

To implement a manual toggle that respects and overrides the system preference:

```javascript
const toggle = document.querySelector('#themeToggle');
toggle.addEventListener('click', () => {
  document.documentElement.classList.toggle('force-light');
});
```

```css
.force-light {
  --bg-app:         oklch(0.97 0.002 150);
  --bg-surface:     oklch(0.93 0.003 150);
  --bg-elevated:    oklch(0.88 0.004 150);
  --bg-interactive: oklch(0.83 0.005 150);
  --border-subtle:  oklch(0.78 0.006 150);
  --border-strong:  oklch(0.65 0.006 150);
  --text-primary:   oklch(0.12 0.008 150);
  --text-secondary: oklch(0.25 0.006 150);
  --text-muted:     oklch(0.48 0.005 150);
  --text-accent:    var(--green-dark);
  --focus-ring-color: var(--green-dark);
}

---

## Customization Best Practices

### DO:

✅ Override semantic tokens (`--bg-app`, `--text-primary`) instead of raw colors
✅ Use relative units (`rem`, `em`) instead of `px` for spacing
✅ Test customizations in multiple browsers
✅ Maintain sufficient color contrast (use a contrast checker)
✅ Keep the OKLCH hue consistent for visual harmony

### DON'T:

❌ Override individual component styles (use variables instead)
❌ Mix OKLCH and hex values (stick to one format)
❌ Remove accessibility features (focus indicators, touch targets)
❌ Use !important (variables should suffice)
❌ Change transition timing randomly (maintain consistent feel)

---

## Component-Specific Customization

If you need to customize a specific component without affecting others:

```css
/* Target specific components */
.action-btn.my-custom-btn {
  --green-primary: #your-color;
  background: var(--green-primary);
}

/* Override locally */
.my-component {
  --space-md: 2rem;  /* Larger spacing just in this component */
}
```

---

## CSS Variable Inheritance

CSS variables cascade and inherit. You can override them at different levels:

```css
:root {
  --green-primary: #4a9d5f;  /* Global default */
}

.dark-section {
  --green-primary: #3a7d4f;  /* Darker green in this section */
}

.even-darker-section {
  --green-primary: #2a5d3f;  /* Even darker */
}
```

---

## Browser Support

CSS custom properties are supported in:
- Chrome 49+
- Firefox 31+
- Safari 9.1+
- Edge 15+

OKLCH colors require:
- Chrome 111+
- Firefox 113+
- Safari 15.4+

If you need broader support, use hex values instead of OKLCH.

---

## Testing Customizations

After customizing, test:

1. **Color Contrast**: Use [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
   - Text-to-background: Minimum 4.5:1 (WCAG AA)
   - Large text (18pt+): Minimum 3:1

2. **Keyboard Navigation**: Tab through all interactive elements
   - Focus indicators should be clearly visible

3. **Reduced Motion**: Test with `prefers-reduced-motion: reduce`
   - Animations should become instant (0.01ms)

4. **Responsive**: Test at mobile widths (< 1024px)
   - Touch targets should be 44x44px minimum

---

## FAQ

**Q: Can I use Stdout.css with Tailwind/Bootstrap?**
A: Not recommended. Stdout.css is a complete design system. Mixing frameworks will create conflicts.

**Q: How do I reset a variable to default?**
A: Remove your override. Variables cascade, so removing your custom value will fall back to the default.

**Q: Can I use CSS preprocessors (Sass/Less)?**
A: Yes, but unnecessary. Stdout.css uses native CSS variables, which are more powerful and require no build step.

**Q: How do I customize just one button?**
A: Use component-specific overrides (see above) or add a custom class.

---

*For component usage, see [components.md](components.md).*
*For color system details, see [colors.md](colors.md).*
*For typography guidance, see [typography.md](typography.md).*
