# Stdout.css

**A pure CSS framework for building information-dense developer tools.**

Form follows function. Brutal honesty.

Hard-edged, asymmetric, unapologetically functional. No marketing fluff, no decorative elements. Every pixel serves a purpose.

---

## Philosophy

**Speed Over Spectacle** – Instant visual feedback over elaborate animations
**Clarity Through Hierarchy** – Information at a glance, collapsible complexity
**Trust Through Feedback** – Precise error messages, clear success states
**Technical Precision** – Accurate terminology, exposed details
**Functional Minimalism** – Form follows function, brutal honesty

---

## Installation

1. **Download** `stdout.css`
2. **Load your fonts** (optional but recommended):

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600&family=JetBrains+Mono:wght@400;500;600&family=Space+Mono:wght@400;700&display=swap">
```

3. **Include the stylesheet:**

```html
<link rel="stylesheet" href="stdout.css">
```

4. **Start building.**

No build tools. No npm. No JavaScript. Just CSS.

---

## Bring Your Own JavaScript

stdout.css is a **pure CSS framework**. It provides all the visual components, layout, color, typography, states, animations, but does not ship any JavaScript.

Interactive behaviors (opening modals, dismissing toasts, filtering a command palette) are intentionally left to you. Wire them up with whatever you're already using: vanilla JS, Alpine.js, HTMX, React, or anything else. The CSS classes work the same regardless.

This means stdout.css has **zero runtime dependencies** and works in any stack.

---

## Quick Start

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Developer Tool</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600&family=JetBrains+Mono:wght@400;500;600&family=Space+Mono:wght@400;700&display=swap">
    <link rel="stylesheet" href="stdout.css">
</head>
<body>
    <h1>STDOUT.CSS</h1>
    <p>Form follows function. Brutal honesty.</p>

    <button class="action-btn">CREATE</button>
    <button class="action-btn secondary">SETTINGS</button>
    <button class="action-btn danger">DELETE</button>
</body>
</html>
```

---

## Design Principles

### NO BLUES
Greens for primary actions, burnt orange for secondary. Blue is explicitly excluded from the palette.

### DARK MODE FIRST
Designed for developers working in low-light environments. High contrast, reduced eye strain. Light mode is supported via `prefers-color-scheme` and fully overrideable.

### OKLCH COLOR SYSTEM
Perceptually uniform colors with subtle green tints. No pure grays, every neutral has character.

### MONOSPACE FOR TECHNICAL DATA
Commands, hashes, timestamps, code, all monospace. Sans-serif for prose.

### NATURAL DECELERATION
Animations use exponential easing (`ease-out-quart`, `ease-out-expo`). No bounces, no elastic effects.

---

## Components

- **Buttons**, Primary, secondary, danger, icon, text, copy
- **Forms**, Inputs, textareas, selects, checkboxes, radio buttons, toggle switches, sliders
- **Tables**, Data tables with row selection and hover actions
- **Badges**, Status indicators (success, warning, error, info)
- **Modals**, Centered panels with backdrop blur
- **Toasts**, Success/error/warning/info notifications
- **Tabs**, Pure CSS tabbed interface (up to 6 tabs)
- **Accordions**, Collapsible sections via native `<details>`
- **Tooltips**, `data-tooltip` attribute, four position variants
- **Command Palette**, Keyboard-first search interface
- **Code Boxes**, Command display with copy button, code blocks
- **Loading States**, Spinners, skeleton screens, empty states
- **Typography**, Headings, `<kbd>`, `<mark>`, `<blockquote>`, `<abbr>`, and more

See [docs/components.md](docs/components.md) for full documentation with HTML examples.

---

## Customization

Override CSS variables to customize colors, spacing, and typography:

```css
:root {
  --green-primary: #yourcolor;
  --space-md: 1.25rem;
  --font-display: 'Your Mono Font', monospace;
}
```

See [docs/customization.md](docs/customization.md) for the complete variable reference.

---

## Documentation

- **[Philosophy](PHILOSOPHY.md)** – Design philosophy and principles
- **[Components](docs/components.md)** – Component catalog with HTML examples
- **[Customization](docs/customization.md)** – CSS variables reference
- **[Colors](docs/colors.md)** – Color system and palette
- **[Typography](docs/typography.md)** – Font stacks and scale

---

## Examples

Open `examples/index.html` in a browser for a live component showcase.

---

## Browser Support

Stdout.css targets modern evergreen browsers:

- Chrome/Edge 111+
- Firefox 113+
- Safari 15.4+

Requires OKLCH color support and `color-mix()`. This is a forward-looking framework, no legacy fallbacks are provided.

---

## Anti-Patterns

**What stdout.css is NOT:**

- ❌ Generic "modern" aesthetics
- ❌ Blue-themed interfaces
- ❌ Marketing-heavy UIs
- ❌ Excessive animations
- ❌ Rounded cards and glassmorphism
- ❌ A JavaScript component library
- ❌ For everyone (and that's okay)

---

## License

MIT License – Use freely in personal and commercial projects.

---

*Form follows function. Brutal honesty.*
