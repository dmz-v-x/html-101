## Attributes vs Global Attributes

### 1. What are attributes? What are global attributes?

### What is an attribute?

HTML elements look like this:

```html
<tagname attribute="value">content</tagname>
```

Examples:

```html
<a href="https://example.com">Link</a>
<img src="photo.jpg" alt="Description">
```

Let’s break that down:

- **Element (tag)** → `a`, `img`, `div`, `p`, etc.
- **Attribute** → extra information that changes behavior or provides data

Examples of what attributes do:
- `href` → tells `<a>` where to go
- `src` → tells `<img>` where the image is
- `alt` → describes the image for accessibility
- `type` → changes how inputs or buttons behave

So mentally:

> **Element = what it is**  
> **Attribute = extra information about it**

---

### Global vs Specific attributes

#### Specific attributes (element-specific)

These work **only on certain elements**:

- `href` → `<a>`, `<link>`
- `src` → `<img>`, `<script>`, `<iframe>`
- `type` → `<input>`, `<button>`, `<script>`
- `alt` → `<img>`

Using them on the wrong tag is invalid HTML.

---

#### Global attributes (important!)

Global attributes can be used on **almost any HTML element**.

Examples:
- `id`
- `class`
- `style`
- `data-*`
- `hidden`
- `tabindex`
- `title`
- `lang`
- `contenteditable`
- `draggable`

Think of global attributes as:

> “Useful powers you can attach to almost any tag.”

---

### 2. `id` – unique identifier

```html
<p id="intro">Hello, I am Himanshu.</p>
```

### What is `id`?

- A **unique name** for **one specific element**
- **Must be unique** in the entire HTML document

Think of `id` like:
> a passport number — only one person can have it

---

### 2.1 Using `id` in CSS

```html
<p id="intro">Hello, world</p>
```

```css
#intro {
  font-size: 1.25rem;
  color: #1f2933;
}
```

- `#intro` means “the element whose id is intro”
- IDs have **high CSS specificity**
- Use sparingly for styling

---

### 2.2 Using `id` in JavaScript

```js
const intro = document.getElementById('intro');
intro.textContent = 'Updated text';
```

Very common:
- JS frequently selects elements using `id`
- Fast and direct access

---

### 2.3 Internal page navigation (hash links)

```html
<h2 id="contact">Contact</h2>
<a href="#contact">Go to Contact section</a>
```

- `href="#contact"` scrolls to the element with `id="contact"`
- This is how **in-page navigation** works

---

### Best practices for `id`

- Use each `id` only once per page
- Use descriptive names:
  - `main-header`
  - `hero-section`
  - `contact-section`
- Start with letters, then letters/numbers/hyphens
- Don’t use ids everywhere — prefer classes for styling

---

### 3. `class` – reusable grouping

```html
<p class="highlight">Important note</p>
<p class="highlight">Another important thing</p>
```

### What is `class`?

- **Not unique**
- Many elements can share the same class
- One element can have **multiple classes**

```html
<div class="card featured"></div>
```

Here:
- `card` → base style
- `featured` → extra behavior or style

---

### 3.1 Using `class` in CSS

```css
.highlight {
  background-color: yellow;
}

.card {
  padding: 1rem;
  border-radius: 0.5rem;
}

.featured {
  border-color: orange;
}
```

You will use classes for **90% of your styling**.

---

### 3.2 Using `class` in JavaScript

```js
const cards = document.querySelectorAll('.card');

cards.forEach(card => {
  // do something with each card
});
```

---

### `id` vs `class` (important mental model)

| Feature | id | class |
|------|----|------|
| Unique | ✅ yes | ❌ no |
| Reusable | ❌ no | ✅ yes |
| CSS usage | Rare | Very common |
| JS usage | Direct lookup | Group selection |

- `id` → identity
- `class` → category

---

### 4. `style` – inline CSS (use carefully)

```html
<p style="color: red; font-weight: bold;">
  This is important.
</p>
```

### What is `style`?

- CSS written directly on the element
- Called **inline CSS**

---

### Why inline styles are discouraged

- Hard to maintain
- Hard to override
- Not reusable
- Breaks separation of concerns

---

### Better approach

```html
<p class="important">This is important.</p>
```

```css
.important {
  color: red;
  font-weight: bold;
}
```

---

### When `style` is okay

- Quick learning experiments
- Small dynamic styles set by JS
- Tiny one-off tweaks (rare)

---

### 5. `data-*` – custom data attributes

```html
<div
  class="product-card"
  data-product-id="123"
  data-category="books"
>
  Book Title
</div>
```

### What are `data-*` attributes?

- Custom attributes starting with `data-`
- Valid HTML
- Invisible to users
- Designed for JavaScript

---

### Why they exist

Old (bad) way:

```html
<div my-custom-info="123"></div> ❌
```

Correct way:

```html
<div data-info="123"></div> ✅
```

---

### Reading `data-*` in JavaScript

```js
const card = document.querySelector('.product-card');

console.log(card.dataset.productId); // "123"
console.log(card.dataset.category);  // "books"
```

Mapping rule:
- `data-user-name` → `dataset.userName`

---

### Common use cases

- Filtering
- UI behavior
- State flags

```html
<button data-action="open-modal">Open</button>
<button data-action="close-modal">Close</button>
```

---

### 6. `lang` – language declaration

### Document-level language

```html
<html lang="en">
```

- Tells screen readers how to pronounce text
- Helps search engines
- Improves accessibility

Example for Hindi:

```html
<html lang="hi">
```

---

### Element-level language

```html
<p>
  This phrase is in <span lang="fr">français</span>.
</p>
```

Screen reader switches pronunciation automatically.

---

### Best practices

- Always set `lang` on `<html>`
- Use correct language codes:
  - `en`, `en-US`, `hi`, `fr`, etc.

---

### 7. `title` – tooltip information

```html
<button title="Saves your changes">Save</button>
```

- Shows tooltip on mouse hover
- Sometimes read by screen readers

---

### Important warnings

- `title` is **not a replacement** for labels
- Not reliable on mobile
- Not fully accessible alone

Better:
- Clear visible text
- `aria-label` for icon-only elements
- `title` only as optional extra info

---

### 8. `hidden` – hide elements completely

```html
<p hidden>This text is hidden</p>
```

- Removes element from visual view
- Removed from accessibility tree
- Same as `display: none`

Use cases:
- Toggling UI with JS
- Conditional content

---

### 9. `tabindex` – keyboard navigation control

```html
<div tabindex="0">Focusable box</div>
```

### Values

- `tabindex="0"` → focusable in normal order
- `tabindex="-1"` → focusable only via JS
- `tabindex="1+"` → ❌ avoid (breaks natural order)

Use sparingly, mostly for:
- Custom components
- Skip links

---

### 10. `contenteditable` – editable content

```html
<p contenteditable="true">Edit me</p>
```

- Allows users to edit text directly
- Used in rich text editors
- Changes are not saved unless JS handles them

---

### 11. `draggable` – drag support

```html
<div draggable="true">Drag me</div>
```

- Enables drag-and-drop behavior
- Needs JS to be useful
- Rare in beginner projects

---

### 12. Summary – global attributes cheat sheet

| Attribute | Purpose |
|--------|--------|
| id | Unique identifier |
| class | Reusable grouping |
| style | Inline CSS |
| data-* | Custom JS data |
| lang | Language info |
| title | Tooltip text |
| hidden | Hide element |
| tabindex | Keyboard navigation |
| contenteditable | Editable content |
| draggable | Drag support |

---

### Final mental model

- **Attributes = extra information**
- **Global attributes = available everywhere**
- Prefer:
  - `class` for styling
  - `id` for unique identity & JS
  - semantic HTML first
- Avoid overusing:
  - `style`
  - random `tabindex`
- Accessibility matters more than visuals
