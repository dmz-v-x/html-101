## Accessibility in HTML

### 1. `alt` text — why it matters and how to write it

### What is `alt`?

`alt` = alternative text for images:

```html
<img src="profile.jpg" alt="Himanshu Bhatt, full stack developer">
```

It’s used when:

- A screen reader reads the page.  
- Image fails to load.  
- User turns off images (slow network).

Why `alt` is important:

- For a blind user, without `alt`, an image is just: “image… image… image…”  
- With good `alt`, it becomes meaningful: “Himanshu Bhatt, full stack developer.”  
- `alt` also helps search engines (SEO).

---

### 2. When to write descriptive `alt`

Ask: “Does this image carry meaning?”

If **yes** → describe what it shows or what it represents:

```html
<!-- Profile photo -->
<img src="himanshu.jpg" alt="Himanshu Bhatt, full stack web developer">

<!-- Banner -->
<img src="sale-banner.png" alt="50% off all courses this weekend">

<!-- Diagram -->
<img src="architecture.png" alt="Diagram showing frontend, backend, and database communication">
```

Tips:

- Keep it short but meaningful.  
- Don’t say “image of…” or “picture of…” (screen readers already say it’s an image).  
- Think: *“If I couldn’t see, what would I want someone to say instead of this image?”*

---

### 3. When to use empty `alt` (`alt=""`)

If the image is **purely decorative**, like:

- A divider line  
- A background flourish  
- A decorative icon that doesn’t add information

Then tell screen readers to skip it:

```html
<img src="decorative-line.png" alt="">
```

`alt=""` means: “ignore this image.”

Common mistakes:

- ❌ No `alt` at all: `<img src="photo.jpg">` → screen reader may read file name.  
- ❌ Using file name: `alt="pic1234"`  
- ❌ Keyword stuffing: `alt="developer developer portfolio react node full stack"`

Good `alt` is helpful and respectful.

---

### 4. `aria-label` — giving invisible names to things

`aria-label` gives a name that only assistive tech (screen readers) sees. Useful when there’s no visible text.

Example: icon-only button

```html
<button aria-label="Open navigation menu">
  <svg><!-- hamburger icon --></svg>
</button>
```

Visually: user sees an icon.  
Screen reader: says “Open navigation menu, button”.

Social/icon link example:

```html
<a href="https://github.com/himanshu" aria-label="Himanshu on GitHub">
  <svg><!-- GitHub icon --></svg>
</a>
```

Screen reader says: “Himanshu on GitHub, link”.

---

### 5. `aria-label` vs `<label>`

- **Use `<label>` for form controls** (inputs, textareas, selects). `<label>` is the primary, accessible way to name fields.
- **Use `aria-label`** for icon-only controls, or when visible text is not present or insufficient.

Bad example (redundant):

```html
<button aria-label="Submit">Submit</button> <!-- redundant -->
```

Only use `aria-label` when it adds value (e.g., no visible text).

---

### 6. `aria-hidden` — hide decorative things from screen readers

`aria-hidden="true"` means: “pretend this element doesn’t exist for assistive tech.”

Good example:

```html
<button>
  <span class="icon" aria-hidden="true">⭐</span>
  Save
</button>
```

Screen reader reads “Save, button” — no noisy “star”.

**Never do this:**

```html
<button aria-hidden="true">Save</button>
```

That hides the whole button from assistive tech — blind users can’t use it at all. Bad!

Rule: only use `aria-hidden="true"` on decorative items that have no functional meaning.

---

### 7. Semantic tags — helpful to screen readers

Use semantic HTML to give meaning, not just boxes. Examples:

- Page structure: `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`  
- Headings: `h1`–`h6`, paragraphs: `p`  
- Lists: `ul`, `ol`, `li`  
- Forms: `form`, `label`, `input`, `button`, `fieldset`, `legend`  
- Media: `figure`, `figcaption`  
- Tables: `table`, `thead`, `tbody`, `th`, `td`, `caption`

Semantic tags produce a meaningful tree that assistive tech can navigate.

---

### 8. Keyboard navigation basics

Many users navigate without a mouse. Your site must be usable with:

- `Tab` and `Shift+Tab` (move between interactive elements)  
- `Enter` and `Space` (activate links and buttons)  
- Arrow keys for some components  
- Focus must be visible

### 8.1 What is “focus”?

Press `Tab` → browser moves “focus” to the next interactive element:

- Links (`<a href="...">`)  
- Buttons (`<button>`)  
- Inputs, textareas, selects  
- Elements with `tabindex="0"`

The focused element should have a visible ring/outline.

Default browser outlines are good; don’t remove them without replacement.

Bad CSS:

```css
:focus { outline: none; } /* don't do this */
```

Better:

```css
:focus {
  outline: 2px solid #22c55e;
  outline-offset: 2px;
}
```

---

### 9. `tabindex` — control tab order (use carefully)

- `tabindex="0"` — makes an element keyboard-focusable in the natural DOM order (useful for non-interactive elements you want keyboard-focusable).  
- `tabindex="-1"` — element is programmatically focusable (focus via JS) but skipped by Tab.  
- `tabindex="1"` (or >0) — sets custom tab order; **avoid** because it is confusing and hard to maintain.

Prefer natural DOM order and semantic elements. Use `tabindex` only when necessary (e.g., skip links or custom widgets).

Example: Skip to main content (recommended):

```html
<a href="#main-content" class="skip-link">Skip to main content</a>

<!-- later in page -->
<main id="main-content">...</main>
```

`.skip-link` can be visually hidden and shown on focus (so keyboard users benefit).

---

### 10. Headings order — structure matters

- Use one `h1` per page for the main title.  
- Use `h2` for main sections, `h3` for subsections, etc.  
- Don’t skip levels (e.g., don’t jump from `h1` to `h4` without intermediate headings).  
- Headings create a navigable outline for screen readers and help sighted users scan the page.

---

### 11. Focus management for dynamic content

When content changes (modals, dialogs, single-page apps):

- When opening a modal, **move focus into it** (e.g., first focusable element).  
- When closing, **return focus** to the element that opened it.  
- Use `role="dialog"` and `aria-modal="true"` on modal containers for better behavior.

Simple modal focus example (conceptual):

```html
<button id="open">Open modal</button>

<div id="modal" role="dialog" aria-modal="true" aria-labelledby="modal-title" hidden>
  <h2 id="modal-title">Modal title</h2>
  <button id="close">Close</button>
</div>
```

Use JS to set focus: `document.getElementById('close').focus()` when opened.

---

### 12. `aria-describedby` — describe complex controls

`aria-describedby` lets you point to an element that explains something (helper text, error messages).

Example:

```html
<label for="email">Email</label>
<input id="email" name="email" aria-describedby="emailHelp">
<div id="emailHelp">We'll never share your email.</div>
```

Screen readers read the label and then the help text.

For error messages, dynamically update the described element and ensure it's visible to screen readers.

---

### 13. `role` attribute — when to use it

`role` gives an explicit semantic when native HTML is not used.

Example: a custom clickable div acting as a button:

```html
<div role="button" tabindex="0">Click me</div>
```

But **prefer native elements** (`<button>`) — they come with correct keyboard behavior and accessibility out of the box. Use `role` only when necessary.

---

### 14. Contrast, color and readability

- Make sure text contrast is high enough vs background. Low contrast hurts people with low vision.  
- WCAG recommends contrast ratio of at least **4.5:1** for normal text (AA).  
- Use color as a *supplement*, not the only way to convey information (e.g., error color + text/icon).

Example: instead of only red to indicate error, also show an icon and a text message.

---

### 15. Accessible forms (summary & reminders)

- Always use `<label>` connected via `for` and `id`.  
- Use `fieldset` + `legend` for grouped controls (radio groups, related checkboxes).  
- Use `aria-describedby` for helper text and error messages.  
- Use `required`, `minlength`, `pattern`, and provide accessible error messages — don’t rely only on color.  
- Avoid placeholders as the only label — they disappear when users type.

Example: accessible radio group

```html
<fieldset>
  <legend>Choose your plan</legend>
  <label><input type="radio" name="plan" value="free"> Free</label>
  <label><input type="radio" name="plan" value="pro"> Pro</label>
</fieldset>
```

---

### 16. Media accessibility (captions, transcripts)

- Provide captions (`<track kind="captions">`) for videos.  
- Provide transcripts for audio and video content (text version).  
- Use `<figure>` + `<figcaption>` for images/videos when you want visible captions.

---

### 17. Accessible tables

- Use `<caption>` to describe the table.  
- Use `<th scope="col">` or `scope="row"` for header cells.  
- Use `thead`, `tbody`, `tfoot` for logical grouping.  
- For complex tables, consider `headers` attribute to explicitly associate cells with headers (advanced).

---

### 18. Validation messages & live regions

- For dynamic updates (error messages appearing after submit), use `role="alert"` or `aria-live="assertive"` on the container so screen readers announce changes.

Example:

```html
<div id="error" role="alert" hidden>There was an error with your submission.</div>
```

When you remove `hidden` and set text, screen readers announce it.

---

### 19. Testing accessibility (quick checklist)

- Try using the site with keyboard only (Tab, Enter, Space).  
- Use a screen reader (VoiceOver on macOS/iOS, NVDA on Windows) to test reading order and labels.  
- Use browser Lighthouse/Axe for automated checks (they find common problems).  
- Check color contrast with a contrast checker.  
- Ask real users when possible — automatic tools can't catch everything.

---

### 20. Final rules-of-thumb for beginners

- Use **semantic HTML** first.  
- Always provide meaningful `alt` for images or `alt=""` for decorative ones.  
- Use visible labels for form controls; use `aria-*` when necessary.  
- Keep keyboard users in mind (visible focus, natural tab order).  
- Add captions/transcripts for media.  
- Test frequently with keyboard and a screen reader.

---

### 21. Quick copy-paste cheatsheet

### Skip link
```html
<a href="#main-content" class="skip-link">Skip to main content</a>
```

### Accessible image (descriptive)
```html
<img src="diagram.png" alt="Diagram showing frontend talking to backend via API">
```

### Decorative image
```html
<img src="decor.png" alt="">
```

### Icon-only button
```html
<button aria-label="Open menu">
  <svg><!-- icon --></svg>
</button>
```

### Form field with helper text
```html
<label for="phone">Phone</label>
<input id="phone" name="phone" aria-describedby="phoneHelp">
<div id="phoneHelp">International format: +91 12345 67890</div>
```

---
