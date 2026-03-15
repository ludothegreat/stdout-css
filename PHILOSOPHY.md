# Stdout.css Philosophy

**Form follows function. Brutal honesty.**

---

## A Brutalist Approach to Developer Tools

Stdout.css combines the honest, functional aesthetic of **terminal emulators** with the raw, structural principles of **brutalist architecture**.

It rejects:
- Generic "modern" design trends
- Marketing fluff and unnecessary decoration
- Hiding complexity for the sake of "simplicity"
- Blue-themed interfaces (we use greens + burnt orange)

It embraces:
- Hard edges, asymmetric layouts
- Information density over whitespace
- Technical precision and accuracy
- Monospace typography for data
- Dark mode for focused work

---

## The Five Principles

### 1. **Speed Over Spectacle**

**Instant visual feedback > Elaborate animations**

- Favor fast, purposeful interactions over slow, decorative motion
- Minimize clicks and navigation depth
- Animations should feel like physics, not theater
- Loading states communicate progress, not entertainment

**Why it matters**: Developers use tools all day. Seconds wasted on animations compound into minutes, then hours. Respect your user's time.

---

### 2. **Clarity Through Hierarchy**

**Information at a glance > Buried in menus**

- Clear visual hierarchy separates headers, sections, content
- Consistent use of color denotes action importance
  - Green = primary (create, confirm, go)
  - Orange = secondary (settings, alternatives)
  - Red = destructive (delete, remove, danger)
- Status indicators make state obvious without clicking
- Collapsible sections prevent overwhelming the user

**Why it matters**: Information-dense UIs need strong hierarchy. Without it, everything screams for attention and nothing gets through.

---

### 3. **Trust Through Feedback**

**Precise communication > Vague pleasantries**

- Destructive actions require explicit confirmation
- Success states are clearly communicated (toasts, status changes)
- Error messages are technical and specific:
  - ❌ "Something went wrong" → ✅ "HTTP 504: Gateway timeout"
- Connection status is always visible
- Activity logs provide audit trails

**Why it matters**: Developers debug systems. Vague error messages waste time. Honest feedback builds trust.

---

### 4. **Technical Precision**

**Accurate terminology > Simplified jargon**

- Use the correct git/dev terminology (commit, branch, clone, not "version", "copy", "download")
- Show full commands users can copy and run
- Display commit hashes, timestamps, metadata
- Expose technical details rather than abstracting them away
- Monospace fonts for code, commands, hashes, paths

**Why it matters**: Developers think in precise terms. Simplified language creates confusion, not clarity.

---

### 5. **Functional Minimalism**

**Form follows function > Decoration for decoration's sake**

- No elements exist purely for aesthetics
- Borders and shadows create depth and hierarchy, not decoration
- Consistent spacing and alignment create rhythm
- Dark theme reduces cognitive load and eye strain
- Every color has semantic meaning

**Why it matters**: Visual noise is distracting. Brutalism strips away the unnecessary, leaving only what serves the user.

---

## Design Constraints

### Color: NO BLUES

**Why no blues?**

Blue is overused in tech interfaces. Every SaaS product, every dashboard, every developer tool defaults to blue. It's become visual noise—the design equivalent of lorem ipsum.

Stdout.css uses:
- **Greens** (#4a9d5f, #5fb574) for primary actions, success states
- **Burnt Orange** (#d4753e, #e88952) for secondary actions, warnings
- **Grays** (OKLCH with subtle green tint) for neutrals
- **Red** (#ff4444) for errors and destructive actions

This palette is distinctive, memorable, and intentional.

---

### Color System: OKLCH with Tinted Neutrals

**No pure grays.**

Every neutral color in Stdout.css has a subtle green tint (OKLCH hue: 150). This creates visual cohesion—the grays harmonize with the greens rather than fighting them.

Traditional CSS:
```css
--gray-500: #808080; /* Pure gray, feels cold and disconnected */
```

Stdout.css:
```css
--gray-500: oklch(0.48 0.008 150); /* ~#4a4c4a - subtle green warmth */
```

The difference is subtle but perceptible. Pure grays feel sterile. Tinted grays feel considered.

---

### Typography: Monospace for Data, Sans-Serif for Prose

**Not everything should be monospace.**

- **Headings**: Space Mono (monospace, uppercase) for emphasis
- **Body text**: IBM Plex Sans (clean, readable sans-serif)
- **Code/Data**: JetBrains Mono (highly legible monospace)

Use monospace for:
- Code snippets
- Commands
- File paths
- Git hashes
- Timestamps
- Repository names
- Technical identifiers

Use sans-serif for:
- Descriptions
- Help text
- Long-form content
- UI labels (when not uppercase)

---

### Motion: Natural Deceleration, No Bounces

**Physics, not cartoons.**

All animations use **exponential easing curves**:
```css
--ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
--ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
--ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
```

These curves mimic natural deceleration—things slow down smoothly, like friction in the real world.

**We don't use**:
- Bounce (`ease-in-out-back`)
- Elastic (`ease-in-out-elastic`)
- Spring physics

Why? They feel playful and whimsical. Stdout.css is serious, not cute.

---

### Layout: Information Density

**Whitespace is not always better.**

Modern design trends fetishize whitespace. Cards float in oceans of padding. Content spreads out to fill space.

Stdout.css rejects this. Information density is a feature:
- Tables over cards (more data per screen)
- Compact spacing (readable but efficient)
- Borders over shadows (crisp, not soft)
- Hard edges over rounded corners

This doesn't mean cramming content recklessly. It means using space intentionally—not defaulting to maximum padding.

---

## Anti-Patterns

### What stdout.css is NOT:

1. **Retro for Retro's Sake**
   - We use modern CSS (OKLCH, CSS variables, grid)
   - Inspiration from terminals ≠ emulating 1980s CRTs
   - No fake scanlines, no pixelated fonts

2. **Hostile to Users**
   - Brutalism is honest, not cruel
   - Accessibility features (focus indicators, touch targets) are mandatory
   - Keyboard navigation is first-class
   - Responsive design for mobile/tablet

3. **One-Size-Fits-All**
   - This is for **developer tools**, not consumer apps
   - Target audience: technical users who value precision
   - Not appropriate for marketing sites or e-commerce

4. **Unreadable for the Sake of Aesthetics**
   - High contrast (light text on dark bg)
   - Generous line-height for body text (1.5)
   - Touch targets minimum 44x44px on mobile
   - prefers-reduced-motion support

---

## Inspiration

**Terminal emulators**:
- iTerm2, Hyper, Windows Terminal
- Information density, monospace precision
- Dark backgrounds, syntax highlighting

**Brutalist architecture**:
- Raw concrete, exposed structure
- Function over decoration
- Honesty in materials

**Developer tools**:
- GitHub file browser (clean tables, clear hierarchy)
- Linear (fast, keyboard-first, precise)
- Raycast (command palette, instant feedback)

---

## When to Use Stdout.css

✅ **Use Stdout.css for:**
- Internal developer tools
- CI/CD dashboards
- Git hosting interfaces
- API explorers
- Database admin panels
- DevOps monitoring tools

❌ **Don't use Stdout.css for:**
- Marketing websites
- E-commerce storefronts
- Consumer apps
- Content-heavy blogs
- Social media platforms

---

## The Brutalist Checklist

Before using stdout.css, ask:

- [ ] Does it use greens + burnt orange (not blues)?
- [ ] Is it dark mode only?
- [ ] Are technical terms used precisely?
- [ ] Is information dense (not spacious)?
- [ ] Do animations use natural deceleration?
- [ ] Is monospace used for data (not everything)?
- [ ] Are borders hard-edged (not rounded)?
- [ ] Is functionality prioritized over decoration?

If you answered "no" to more than two questions, stdout.css may not be the right fit—and that's okay.

---

## Closing Thoughts

**Stdout.css is not for everyone.**

It's opinionated. It rejects popular trends. It won't win design awards or go viral on Dribbble.

But for developers building tools for developers, it offers something rare:

**Honest design that gets out of the way.**

No fussing with card shadows. No debating border radius. No bikeshedding over which shade of blue.

Just functional, precise, information-dense interfaces that respect your time and intelligence.

---

*Form follows function. Brutal honesty.*
