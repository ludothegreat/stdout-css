# Component Catalog

Complete reference for all Stdout.css components with copy-paste HTML examples.

---

## Table of Contents

1. [Buttons](#buttons)
2. [Forms](#forms)
3. [Tables](#tables)
4. [Modals](#modals)
5. [Toasts](#toasts)
6. [Loading States](#loading-states)
7. [Badges](#badges)
8. [Status Dot](#status-dot)
9. [Alerts](#alerts)
10. [Accordions](#accordions)
11. [Command Palette](#command-palette)
12. [Code Boxes](#code-boxes)
13. [Key-Value List](#key-value-list)
14. [Timeline](#timeline)
15. [Tree View](#tree-view)
16. [Stat Row](#stat-row)
17. [Search Input](#search-input)
18. [Tags](#tags)
19. [Dividers](#dividers)
20. [App Shell](#app-shell)
21. [Empty States](#empty-states)

---

## Buttons

### Primary Button

```html
<button class="action-btn">CREATE</button>
```

**States:**
- Hover: Lifts 2px, green glow shadow
- Active: Presses down, scales to 98%
- Focus: 2px green outline
- Disabled: 40% opacity, no pointer events

### Secondary Button

```html
<button class="action-btn secondary">SETTINGS</button>
```

Orange border, transparent background. Fills with orange on hover.

### Danger Button

```html
<button class="action-btn danger">DELETE</button>
```

Red border, transparent background. Fills with red on hover.

### Small Button

```html
<button class="action-btn small">ENABLE</button>
```

Reduced padding. Can combine with `.secondary` or `.danger`.

### Icon Button

```html
<button class="icon-btn">CLONE</button>
```

Transparent with subtle border. Green accent on hover.

### Text Button

```html
<button class="text-btn">CANCEL</button>
```

No background, underlined. Use sparingly for low-priority actions.

### Copy Button

```html
<button class="copy-btn">COPY</button>
```

Gray background, turns green on hover. Use in code boxes.

### Disabled State

```html
<button class="action-btn" disabled>DISABLED</button>
```

For non-native disabled (e.g. links or buttons that stay in the tab order for accessibility):

```html
<button class="action-btn" aria-disabled="true" tabindex="0">DISABLED</button>
```

### Loading State

Shows a sliding progress bar animation while preserving button dimensions. Text becomes transparent (hidden but layout-stable).

```html
<button class="action-btn loading" disabled aria-busy="true">DEPLOYING</button>
<button class="action-btn secondary loading" disabled aria-busy="true">SYNCING</button>
```

**Accessibility Note:** All buttons have proper focus-visible indicators for keyboard navigation.

---

## Forms

### Text Input

```html
<div class="form-field">
  <label class="form-label" for="username">USERNAME</label>
  <input
    type="text"
    id="username"
    class="form-input"
    placeholder="Enter username..."
  >
  <p class="form-help">Alphanumeric characters only</p>
</div>
```

### Textarea

```html
<div class="form-field">
  <label class="form-label" for="description">DESCRIPTION</label>
  <textarea
    id="description"
    class="form-textarea"
    rows="4"
    placeholder="Enter description..."
  ></textarea>
</div>
```

**Note:** Textareas have `resize: vertical` by default.

### Select Dropdown

```html
<div class="form-field">
  <label class="form-label" for="visibility">VISIBILITY</label>
  <select id="visibility" class="form-select">
    <option value="private">Private</option>
    <option value="public">Public</option>
    <option value="internal">Internal</option>
  </select>
</div>
```

### Checkbox

Checkboxes are fully styled, no extra markup needed beyond the `.checkbox-control` wrapper.

```html
<label class="checkbox-control">
  <input type="checkbox">
  <span>ENABLE MIRRORING</span>
</label>

<!-- Checked state -->
<label class="checkbox-control">
  <input type="checkbox" checked>
  <span>AUTO-DEPLOY</span>
</label>

<!-- Disabled state -->
<label class="checkbox-control">
  <input type="checkbox" disabled>
  <span>LOCKED SETTING</span>
</label>
```

### Radio Buttons

Use `.radio-control` for radio groups. Same styling pattern as checkboxes.

```html
<label class="radio-control">
  <input type="radio" name="visibility" value="public">
  <span>PUBLIC</span>
</label>

<label class="radio-control">
  <input type="radio" name="visibility" value="private" checked>
  <span>PRIVATE</span>
</label>

<label class="radio-control">
  <input type="radio" name="visibility" value="internal" disabled>
  <span>INTERNAL</span>
</label>
```

### Toggle Switch

Binary on/off control. Uses a hidden `<input type="checkbox">` with `role="switch"` for proper screen reader semantics. The `.toggle-track` and `.toggle-thumb` provide the visual toggle, no JavaScript needed.

```html
<!-- Off by default -->
<label class="toggle-switch">
  <input type="checkbox" role="switch">
  <span class="toggle-track"><span class="toggle-thumb"></span></span>
  <span>AUTO-DEPLOY</span>
</label>

<!-- On by default -->
<label class="toggle-switch">
  <input type="checkbox" role="switch" checked>
  <span class="toggle-track"><span class="toggle-thumb"></span></span>
  <span>ENABLE NOTIFICATIONS</span>
</label>

<!-- Disabled -->
<label class="toggle-switch">
  <input type="checkbox" role="switch" disabled>
  <span class="toggle-track"><span class="toggle-thumb"></span></span>
  <span>LOCKED FEATURE</span>
</label>
```

### Validation States

Add `.error` or `.success` to `.form-field` to show validation feedback. Use `.form-error` for the error message.

```html
<!-- Error state -->
<div class="form-field error">
  <label class="form-label" for="email">EMAIL</label>
  <input
    type="email"
    id="email"
    class="form-input"
    value="not-an-email"
    aria-invalid="true"
    aria-describedby="email-error"
  >
  <p class="form-error" id="email-error">Enter a valid email address</p>
</div>

<!-- Success state -->
<div class="form-field success">
  <label class="form-label" for="username-ok">USERNAME</label>
  <input
    type="text"
    id="username-ok"
    class="form-input"
    value="jsmith"
    readonly
    aria-describedby="username-ok-help"
  >
  <p class="form-help" id="username-ok-help">Username is available</p>
</div>
```

**Required field label:**

```html
<label class="form-label" for="name">
  NAME <span class="required">*</span>
</label>
```

### Form Field Group (Side-by-Side)

```html
<div class="form-field-group">
  <input type="text" class="form-input" placeholder="First name">
  <input type="text" class="form-input" placeholder="Last name">
</div>
```

Stacks vertically on mobile (< 1024px).

### Focus States

All form inputs have:
- **Focus**: Green border with 3px green shadow
- **Hover**: Gray-500 border (when not focused)
- **Disabled**: 50% opacity, gray-800 background

---

## Tables

### Basic Data Table

```html
<div class="data-table-container">
  <table class="data-table">
    <thead>
      <tr>
        <th>NAME</th>
        <th>STATUS</th>
        <th>ACTIONS</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <div class="data-title">project-name</div>
          <div class="data-description">A brief description of the project</div>
        </td>
        <td>
          <span class="badge success">ACTIVE</span>
        </td>
        <td class="data-actions">
          <button class="icon-btn">VIEW</button>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```

### Table with Row Selection

```html
<div class="data-table-container">
  <table class="data-table">
    <thead>
      <tr>
        <th style="width: 40px;"></th>
        <th>NAME</th>
        <th>STATUS</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><input type="checkbox" class="data-checkbox"></td>
        <td>
          <div class="data-title">example-repo</div>
        </td>
        <td>
          <span class="badge success">ACTIVE</span>
        </td>
      </tr>
      <tr class="selected">
        <td><input type="checkbox" class="data-checkbox" checked></td>
        <td>
          <div class="data-title">selected-repo</div>
        </td>
        <td>
          <span class="badge warning">PENDING</span>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```

**Class Modifiers:**
- `.selected` - Green background tint, left green border
- `.archived` - 50% opacity

### Table States

- **Hover**: Gray-850 background on row
- **Focus-within**: 2px green outline when focused
- **Active**: Gray-800 background on click

### Overflow Handling

```html
<div class="data-title truncate">Very long repository name that will be truncated</div>
<div class="data-description line-clamp-2">
  Long description that will be clamped to 2 lines with ellipsis at the end
</div>
```

---

## Modals

### Basic Modal

```html
<div id="myModal" class="modal" hidden>
  <div class="modal-backdrop" onclick="closeModal()"></div>
  <div class="modal-panel">
    <div class="modal-header">
      <h3 class="modal-title">CONFIRM ACTION</h3>
      <button class="modal-close" onclick="closeModal()">×</button>
    </div>
    <div class="modal-body">
      <p>Are you sure you want to proceed with this action?</p>
    </div>
    <div class="modal-footer">
      <button class="action-btn secondary" onclick="closeModal()">CANCEL</button>
      <button class="action-btn" onclick="confirmAction()">CONFIRM</button>
    </div>
  </div>
</div>
```

### Wide Modal

```html
<div class="modal-panel wide">
  <!-- Same structure, wider max-width (900px instead of 600px) -->
</div>
```

### Modal with Scrollable Body

```html
<div class="modal-panel">
  <div class="modal-header">
    <h3 class="modal-title">LONG CONTENT</h3>
    <button class="modal-close">×</button>
  </div>
  <div class="modal-body">
    <!-- Long content here -->
    <!-- Body scrolls vertically, header/footer stay fixed -->
  </div>
  <div class="modal-footer">
    <button class="action-btn">CLOSE</button>
  </div>
</div>
```

**JavaScript Required:**
- Show/hide with `hidden` attribute
- Backdrop click to close
- ESC key to close (recommended)

**Accessibility:**
- Focus trap (keep focus within modal)
- Return focus to trigger element on close
- ARIA attributes (`role="dialog"`, `aria-modal="true"`)

---

## Toasts

### Toast Container

```html
<div id="toastContainer" class="toast-container"></div>
```

Place at bottom-right of viewport (already positioned in CSS).

### Toast Variants

```html
<!-- Success -->
<div class="toast success">Repository created successfully</div>

<!-- Warning -->
<div class="toast warning">This action cannot be undone</div>

<!-- Error -->
<div class="toast error">Failed to connect to server</div>

<!-- Info -->
<div class="toast info">Loading repositories...</div>
```

**Behavior (JavaScript Required):**
- Auto-dismiss after 3-5 seconds
- Slide-in animation from right
- Stack vertically (newest at bottom)

**Recommended JavaScript:**
```javascript
function showToast(message, type = 'info', duration = 3000) {
  const container = document.getElementById('toastContainer');
  const toast = document.createElement('div');
  toast.className = `toast ${type}`;
  toast.textContent = message;
  container.appendChild(toast);

  setTimeout(() => {
    toast.style.opacity = '0';
    setTimeout(() => toast.remove(), 250);
  }, duration);
}
```

---

## Loading States

### Spinner

A three-bar terminal pulse animation. The inner `<span>` is required for the middle bar.

```html
<div class="loading-state">
  <div class="loading-spinner" aria-label="Loading" role="status"><span></span></div>
  <p>Loading repositories...</p>
</div>

<!-- Standalone -->
<div class="loading-spinner" aria-label="Loading" role="status"><span></span></div>
```

### Skeleton Screen

```html
<div class="skeleton skeleton-row"></div>
<div class="skeleton skeleton-row"></div>
<div class="skeleton skeleton-row"></div>
```

**Variants:**
- `.skeleton-text` - 1em height, for text placeholders
- `.skeleton-title` - 1.5em height, 60% width
- `.skeleton-row` - 60px height, for table rows

**Animation:** Shimmer effect (1.5s infinite)

### Empty State

```html
<div class="empty-state">
  <div class="empty-state-icon">✨</div>
  <h3 class="empty-state-title">NO REPOSITORIES YET</h3>
  <p class="empty-state-description">
    Create your first repository to get started.
  </p>
  <div class="empty-state-action">
    <button class="action-btn">CREATE REPOSITORY</button>
  </div>
</div>
```

**Icon Recommendations:**
- Empty list: ✨ 📦 💻
- No results: 🔍
- Error: ⚠️
- Completed: ✅

---

## Badges

### Status Badges

```html
<span class="badge success">ACTIVE</span>
<span class="badge warning">PENDING</span>
<span class="badge error">FAILED</span>
<span class="badge info">ARCHIVED</span>
```

**Semantic Meaning:**
- `success` - Active, healthy, completed
- `warning` - Attention needed, pending
- `error` - Failed, broken, critical
- `info` - Informational, neutral

**Styling:**
- Monospace font, uppercase
- Colored border matching text color
- Transparent background

---

## Accordions

Collapsible sections using native `<details>` and `<summary>`. No JavaScript required, open/close is handled entirely by the browser.

The `[+]` / `[-]` indicator updates automatically via CSS when the `open` attribute is present.

### Basic Accordion

```html
<div class="accordion">
  <details class="accordion-item">
    <summary class="accordion-header">SECTION ONE</summary>
    <div class="accordion-body">
      Content for section one goes here.
    </div>
  </details>

  <details class="accordion-item">
    <summary class="accordion-header">SECTION TWO</summary>
    <div class="accordion-body">
      Content for section two goes here.
    </div>
  </details>

  <details class="accordion-item">
    <summary class="accordion-header">SECTION THREE</summary>
    <div class="accordion-body">
      Content for section three goes here.
    </div>
  </details>
</div>
```

### Open by Default

Add the `open` attribute to any `<details>` to render it expanded on load:

```html
<details class="accordion-item" open>
  <summary class="accordion-header">EXPANDED BY DEFAULT</summary>
  <div class="accordion-body">
    This section is open on page load.
  </div>
</details>
```

### Notes

- The `.accordion-body` can contain any HTML, paragraphs, code blocks, forms, tables
- Multiple items can be open simultaneously (native `<details>` behaviour)
- To enforce only one open at a time, use JavaScript to close siblings on open

---

## Status Dot

Inline status indicator. Always paired with a label for accessibility.

```html
<!-- Static states -->
<span class="status-dot success"></span> Active
<span class="status-dot warning"></span> Degraded
<span class="status-dot error"></span> Down
<span class="status-dot info"></span> Idle

<!-- Live (animated pulse) -->
<span class="status-dot success live pulse"></span> Streaming
<span class="status-dot warning live pulse"></span> Reconnecting
```

**Variants:**
- `success`, Green
- `warning`, Orange
- `error`, Red
- `info`, Gray

**Modifier:** `.live.pulse` adds a breathing pulse animation (2s infinite). Use for realtime or actively-changing states.

---

## Alerts

Full-width informational banners. Include `.alert-dismiss` for dismissible alerts (dismiss requires JavaScript to remove the element).

### Basic Alert

```html
<div class="alert info" role="alert">
  <span class="alert-icon">ℹ</span>
  <div class="alert-content">
    <strong class="alert-title">SCHEDULED MAINTENANCE</strong>
    <p class="alert-body">Services will be unavailable on Friday 22:00–23:00 UTC.</p>
  </div>
</div>
```

### Alert Variants

```html
<div class="alert success" role="alert">
  <span class="alert-icon">✓</span>
  <div class="alert-content">
    <strong class="alert-title">DEPLOYMENT COMPLETE</strong>
    <p class="alert-body">v2.4.1 is live in production.</p>
  </div>
</div>

<div class="alert warning" role="alert">
  <span class="alert-icon">⚠</span>
  <div class="alert-content">
    <strong class="alert-title">QUOTA WARNING</strong>
    <p class="alert-body">You have used 85% of your storage quota.</p>
  </div>
</div>

<div class="alert error" role="alert">
  <span class="alert-icon">✕</span>
  <div class="alert-content">
    <strong class="alert-title">BUILD FAILED</strong>
    <p class="alert-body">Exit code 1, see logs for details.</p>
  </div>
</div>
```

### Dismissible Alert

```html
<div class="alert info" role="alert">
  <span class="alert-icon">ℹ</span>
  <div class="alert-content">
    <strong class="alert-title">NEW FEATURE AVAILABLE</strong>
    <p class="alert-body">Container scanning is now enabled for all repositories.</p>
  </div>
  <button class="alert-dismiss" aria-label="Dismiss">✕</button>
</div>
```

**JavaScript for dismiss:**

```javascript
document.querySelectorAll('.alert-dismiss').forEach(btn => {
  btn.addEventListener('click', () => btn.closest('.alert').remove());
});
```

---

## Command Palette

### Command Palette Structure

```html
<div id="commandPalette" class="command-palette" hidden>
  <div class="command-palette-backdrop"></div>
  <div class="command-palette-modal">
    <input
      type="text"
      class="command-input"
      placeholder="SEARCH REPOSITORIES..."
      autofocus
    >
    <div id="commandResults" class="command-results">
      <!-- Results populated by JavaScript -->
    </div>
  </div>
</div>
```

### Command Result Items

```html
<div class="command-results">
  <div class="command-result-item">
    <div class="data-title">example-repo</div>
    <div class="text-muted">Last updated 2 hours ago</div>
  </div>
  <div class="command-result-item">
    <div class="data-title">another-repo</div>
    <div class="text-muted">Last updated yesterday</div>
  </div>
</div>
```

**JavaScript Required:**
- Show/hide on `/` key press
- Filter results as user types
- Navigate with arrow keys
- Select with Enter key
- Close with ESC key

**Accessibility:**
- `autofocus` on input when opened
- Keyboard navigation (up/down arrows)
- Clear visual focus indicator on selected item

---

## Code Boxes

### Command Box

```html
<div class="code-box">
  <code>git clone ssh://git@example.com:27665/repo.git</code>
  <button class="copy-btn">COPY</button>
</div>
```

### Code Block

```html
<div class="code-block">
npm install
npm run build
npm test
</div>
```

**Difference:**
- `.code-box` - Single line command with copy button
- `.code-block` - Multi-line code display, no copy button

**JavaScript for Copy Button:**
```javascript
document.querySelectorAll('.copy-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    const code = btn.previousElementSibling.textContent;
    navigator.clipboard.writeText(code);
    btn.textContent = 'COPIED!';
    setTimeout(() => btn.textContent = 'COPY', 2000);
  });
});
```

---

## Key-Value List

Two-column metadata display using CSS Grid. Keys auto-size to their content (up to 16ch); values fill remaining space.

```html
<dl class="kv-list">
  <div class="kv-item">
    <dt class="kv-key">CREATED</dt>
    <dd class="kv-value">2024-01-15 09:32 UTC</dd>
  </div>
  <div class="kv-item">
    <dt class="kv-key">OWNER</dt>
    <dd class="kv-value">jsmith</dd>
  </div>
  <div class="kv-item">
    <dt class="kv-key">VISIBILITY</dt>
    <dd class="kv-value"><span class="badge success">PUBLIC</span></dd>
  </div>
  <div class="kv-item">
    <dt class="kv-key">LAST COMMIT</dt>
    <dd class="kv-value"><code>a3f9b12</code></dd>
  </div>
</dl>
```

**Notes:**
- Uses `display: contents` on `.kv-item` so grid columns are shared across all rows
- `.kv-value` accepts any inline content, badges, code, links, plain text

---

## Timeline

Chronological event log. Uses CSS logical properties for RTL support.

```html
<ol class="timeline">
  <li class="timeline-item">
    <time class="timeline-time">09:41 UTC</time>
    <strong class="timeline-title">DEPLOYMENT STARTED</strong>
    <p class="timeline-body">Triggered by push to main by jsmith.</p>
  </li>
  <li class="timeline-item">
    <time class="timeline-time">09:43 UTC</time>
    <strong class="timeline-title">BUILD COMPLETE</strong>
    <p class="timeline-body">Docker image built and pushed to registry.</p>
  </li>
  <li class="timeline-item">
    <time class="timeline-time">09:45 UTC</time>
    <strong class="timeline-title">LIVE IN PRODUCTION</strong>
    <p class="timeline-body">Health checks passing. v2.4.1 is serving traffic.</p>
  </li>
</ol>
```

**Notes:**
- `.timeline-body` is optional, omit for terse logs
- Vertical line and dot are drawn via `::before` pseudo-elements, no extra markup needed

---

## Tree View

Collapsible directory/file tree using nested `<details>`. Fully keyboard-navigable, no JavaScript required.

```html
<ul class="tree">
  <li class="tree-item">
    <details open>
      <summary class="tree-label">src/</summary>
      <ul class="tree">
        <li class="tree-item">
          <details>
            <summary class="tree-label">components/</summary>
            <ul class="tree">
              <li class="tree-item tree-leaf">Button.tsx</li>
              <li class="tree-item tree-leaf">Modal.tsx</li>
            </ul>
          </details>
        </li>
        <li class="tree-item tree-leaf">index.ts</li>
        <li class="tree-item tree-leaf">App.tsx</li>
      </ul>
    </details>
  </li>
  <li class="tree-item tree-leaf">package.json</li>
  <li class="tree-item tree-leaf">tsconfig.json</li>
</ul>
```

**Classes:**
- `.tree`, Container (`<ul>`)
- `.tree-item`, Each node (`<li>`)
- `.tree-label`, Folder summary (used as `<summary>` inside `<details>`)
- `.tree-leaf`, File node (no `<details>` wrapper)

**Notes:**
- `open` attribute on `<details>` expands on load
- The `[+]`/`[-]` indicator is CSS-only, driven by the `open` attribute
- Long filenames truncate with ellipsis

---

## Stat Row

Horizontal strip of key metrics. Wraps to multiple rows on narrow viewports.

```html
<div class="stat-row">
  <div class="stat-cell">
    <span class="stat-label">REPOSITORIES</span>
    <span class="stat-value">48</span>
  </div>
  <div class="stat-cell">
    <span class="stat-label">DEPLOYMENTS TODAY</span>
    <span class="stat-value">12</span>
    <span class="stat-delta positive">+3</span>
  </div>
  <div class="stat-cell">
    <span class="stat-label">FAILED BUILDS</span>
    <span class="stat-value">2</span>
    <span class="stat-delta negative">+1</span>
  </div>
  <div class="stat-cell">
    <span class="stat-label">ACTIVE USERS</span>
    <span class="stat-value">134</span>
  </div>
</div>
```

**Delta modifiers:**
- `.stat-delta.positive`, Green, for positive change
- `.stat-delta.negative`, Red, for negative change
- No modifier, Muted gray, for neutral delta

**Responsive:** Cells use `flex: 1 1 120px` and wrap automatically. Vertical dividers switch to horizontal borders on narrow viewports.

---

## Search Input

Styled search input with optional prefix icon and suffix action.

```html
<!-- Basic -->
<div class="search-field">
  <span class="search-prefix">⌕</span>
  <input
    type="search"
    class="search-input"
    placeholder="SEARCH REPOSITORIES..."
    aria-label="Search repositories"
  >
</div>

<!-- With suffix action -->
<div class="search-field">
  <span class="search-prefix">⌕</span>
  <input
    type="search"
    class="search-input"
    placeholder="FILTER BY NAME..."
    aria-label="Filter"
  >
  <kbd class="search-suffix">/</kbd>
</div>
```

**Notes:**
- `.search-prefix` and `.search-suffix` are optional
- Browser-native search cancel button is normalized away (use JavaScript to clear if needed)
- `type="search"` provides semantics and triggers virtual keyboard `Search` action on mobile

---

## Tags

Compact metadata chips. Use `.tag-list` as the container.

```html
<div class="tag-list">
  <span class="tag">golang</span>
  <span class="tag">docker</span>
  <span class="tag accent">featured</span>
  <span class="tag success">active</span>
  <span class="tag warning">beta</span>
  <span class="tag error">deprecated</span>
</div>
```

### Removable Tags

```html
<div class="tag-list">
  <span class="tag">
    golang
    <button class="tag-remove" aria-label="Remove golang">✕</button>
  </span>
  <span class="tag success">
    active
    <button class="tag-remove" aria-label="Remove active">✕</button>
  </span>
</div>
```

**Variants:**
- Default, Subtle gray border, muted text
- `.accent`, Green border/text
- `.success`, Green (same as accent, semantic alias)
- `.warning`, Orange
- `.error`, Red

---

## Dividers

### Horizontal Divider

```html
<hr class="divider">

<!-- Strong variant -->
<hr class="divider strong">
```

### Labeled Divider

```html
<div class="divider-label">OR CONTINUE WITH</div>
```

Renders as a horizontal rule with centered text. The line is drawn via `::before`/`::after` pseudo-elements.

### Vertical Divider

```html
<div style="display: flex; align-items: center; gap: 1rem;">
  <span>Left</span>
  <span class="divider-v"></span>
  <span>Right</span>
</div>
```

**Classes:**
- `.divider`, Standard `<hr>` (1px, subtle border color)
- `.divider.strong`, 2px, strong border color
- `.divider-label`, Horizontal rule with centered inline label
- `.divider-v`, Vertical `1px` rule for inline use

---

## App Shell

Full-viewport application frame using CSS Grid. Compose the panels you need, all are optional except `.app-content`.

### Full Layout (topbar + sidebar + content + details)

```html
<div class="app-shell">
  <!-- Skip navigation (accessibility) -->
  <a href="#main" class="skip-nav">Skip to content</a>

  <!-- Top bar -->
  <header class="app-topbar">
    <span class="app-topbar-brand">MYAPP</span>
    <nav class="app-topnav" aria-label="Main navigation">
      <a href="/dashboard" class="app-topnav-link" aria-current="page">DASHBOARD</a>
      <a href="/repos"     class="app-topnav-link">REPOSITORIES</a>
      <a href="/settings"  class="app-topnav-link">SETTINGS</a>
    </nav>
    <div class="app-topbar-spacer"></div>
    <button class="icon-btn">PROFILE</button>
  </header>

  <!-- Sidebar -->
  <aside class="app-sidebar">
    <nav aria-label="Section navigation">
      <!-- sidebar links, filters, etc. -->
    </nav>
  </aside>

  <!-- Main content -->
  <main class="app-content" id="main" tabindex="-1">
    <!-- your page content -->
  </main>

  <!-- Details panel (slide-in on selection) -->
  <aside class="app-details" aria-label="Details">
    <div
      id="detailsContent"
      aria-live="polite"
      aria-atomic="true"
    >
      <!-- populated dynamically -->
    </div>
  </aside>
</div>
```

### Minimal Layout (topbar + content only)

```html
<div class="app-shell">
  <a href="#main" class="skip-nav">Skip to content</a>
  <header class="app-topbar">
    <span class="app-topbar-brand">MYAPP</span>
  </header>
  <main class="app-content" id="main" tabindex="-1">
    <!-- content -->
  </main>
</div>
```

**Grid columns:**

| Panel | Variable | Default |
|-------|----------|---------|
| Sidebar | (fixed) | `240px` |
| Content | (fills) | `1fr` |
| Details | (fixed) | `320px` |

**Classes:**
- `.app-shell`, CSS Grid root (`100dvh`, overflow hidden)
- `.app-topbar`, Fixed top row, spans all columns
- `.app-topbar-brand`, Logo/name slot (monospace, uppercase)
- `.app-topbar-spacer`, Flex spacer, pushes subsequent items right
- `.app-topnav`, Inline nav bar within topbar
- `.app-topnav-link`, Nav link; use `aria-current="page"` for active state
- `.app-sidebar`, Left sidebar with `overflow-y: auto`
- `.app-content`, Main scrollable region (`overflow-y: auto`)
- `.app-details`, Right details panel with `overflow-y: auto`

**Notes:**
- Include `tabindex="-1"` on `#main` so skip-nav focus lands correctly
- `aria-live="polite"` on the details content region announces updates to screen readers
- On mobile (≤ 768px) the layout collapses to a single column; sidebar and details become secondary screens

---

## Empty States

Already covered in [Loading States](#loading-states), but worth highlighting:

**Best Practices:**
- Use encouraging language ("Your Canvas Awaits" not "No items found")
- Explain why empty ("Clone a repository to start working locally")
- Provide clear action button
- Use expressive emoji (✨ 📦 💻) not generic icons

**Examples:**

```html
<!-- Empty Repository List -->
<div class="empty-state">
  <div class="empty-state-icon">✨</div>
  <h3 class="empty-state-title">YOUR CANVAS AWAITS</h3>
  <p class="empty-state-description">
    No repositories yet. Create your first one and start building something amazing.
  </p>
  <div class="empty-state-action">
    <button class="action-btn">CREATE REPOSITORY</button>
  </div>
</div>

<!-- Empty Search Results -->
<div class="empty-state">
  <div class="empty-state-icon">🔍</div>
  <h3 class="empty-state-title">NO MATCHES FOUND</h3>
  <p class="empty-state-description">
    Try adjusting your search terms or filters.
  </p>
</div>
```

---

## Utility Classes

### Text Utilities

```html
<span class="text-green">Green text</span>
<span class="text-orange">Orange text</span>
<span class="text-muted">Muted gray text</span>
<span class="text-error">Error red text</span>
```

### Overflow Utilities

```html
<div class="truncate">This text will be truncated with ellipsis...</div>
<div class="line-clamp-2">This text will be clamped to 2 lines...</div>
<div class="line-clamp-3">This text will be clamped to 3 lines...</div>
<div class="break-words">Thisverylongwordwithnospacesw illbreakproperly</div>
```

### Hidden Utility

```html
<div hidden>This element is hidden</div>
```

Uses `display: none !important` for guaranteed hiding.

---

## Responsive Behavior

Stdout.css has three responsive layers:

### Mobile (≤ 768px)

- Base font size increases to 16px
- Tabs become horizontally scrollable
- Pagination becomes horizontally scrollable
- `.code-box` stacks vertically (code above copy button)
- Navigation links get larger touch targets
- `.timeline` reduces indent
- `.stat-cell` border switches from right to bottom (no orphaned dividers)
- `.command-palette-modal` anchors to viewport bottom
- `.data-table-container` overflows horizontally with scroll snap

### Touch Devices (`pointer: coarse`)

- `.data-actions` are always visible (no opacity-0 hover-reveal)
- Range slider thumb increases to 20×20px
- Interactive elements have 44×44px minimum tap targets

### Print (`@media print`)

- Topbar, sidebar, details panel, modals, toasts, command palette, pagination, and dismiss buttons are all hidden
- `.app-shell` reverts to block layout
- Color tokens reset to black-and-white
- Table action column is restored for reference
- Links display their full URL after the text: `a[href^="http"]::after { content: " (" attr(href) ")" }`
- `.accordion-item`, `.timeline-item`, `.kv-list`, `.stat-row`, `.data-table tr` use `break-inside: avoid`

**Recommended Mobile Patterns:**
- Use modals instead of side panels
- Stack navigation vertically
- Hide complex tables, show simplified list view

---

## Accessibility Features

All components include:

- ✅ **Focus-visible**: 2px green outline on keyboard focus
- ✅ **Touch targets**: Minimum 44x44px on mobile
- ✅ **Color contrast**: WCAG AA compliant
- ✅ **Reduced motion**: Respects `prefers-reduced-motion`
- ✅ **Semantic HTML**: Proper heading hierarchy, ARIA labels

---

## Animation Reference

### Built-in Animations

- `slideIn`, Toast slide-in from right (250ms)
- `bar-pulse`, Three-bar loading spinner (800ms staggered)
- `btn-loading`, Button progress bar slide (1.2s infinite)
- `skeleton-pulse`, Shimmer effect (1.5s)
- `checkmark-draw`, SVG path drawing (400ms)
- `scale-in`, Element entrance (300ms)
- `confetti-fall`, Particle descent (2–4s)
- `ripple-animation`, Ripple (600ms)
- `status-pulse`, Status dot breathing (2s infinite)

### Easing Curves

```css
--ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
--ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
--ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
```

Use for smooth, natural deceleration.

---

## Component Checklist

When building new components, ensure:

- [ ] Uses CSS variables (colors, spacing, typography)
- [ ] Has hover, focus, active, disabled states
- [ ] Works with keyboard navigation
- [ ] Respects prefers-reduced-motion
- [ ] Touch targets >= 44x44px on mobile
- [ ] Color contrast meets WCAG AA
- [ ] Monospace for technical data, sans-serif for prose
- [ ] Error messages are specific and helpful
- [ ] Success feedback is immediate and clear

---

*For customization options, see [customization.md](customization.md).*
*For color system details, see [colors.md](colors.md).*
*For typography guidance, see [typography.md](typography.md).*
