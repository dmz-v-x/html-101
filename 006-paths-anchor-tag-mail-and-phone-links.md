## Paths, Anchor Tag, Phone & Mail Links

### 1. Quick recap — What a path is
A **path** tells the browser where to find a file (image, page, script, stylesheet).  
Examples:

```html
<img src="images/logo.png">
<a href="pages/about.html">About</a>
<link rel="stylesheet" href="css/style.css">
```

- **Difference between `src`, `href` and `rel`**

| Attribute | What it means     | Loads file?  | Used for          |
| --------- | ----------------- | ------------ | ----------------- |
| `src`     | Source of content | ✅ Yes        | Images, JS, media |
| `href`    | Link/reference    | ⚠️ Sometimes | Pages, CSS        |
| `rel`     | Relationship      | ❌ No         | Explains purpose  |


---

### 2. Anchor tag basics — what is `<a>`?

**`<a>`** (anchor) creates clickable links.

Basic example:

```html
<a href="https://example.com">Visit Example</a>
```

- `href` = destination (required for a real link)  
- Link text = what users see and click

If `href` is missing, `<a>` is not treated as a link by browsers and assistive tech.

---

### 3. Types of `href` values

#### 3.1 Absolute URL (external)
Full web address with protocol:

```html
<a href="https://youtube.com">YouTube</a>
```

Use when linking to another website or CDN.

#### 3.2 Root-relative path
Starts from the site root (`/`):

```html
<a href="/about">About</a>
<img src="/assets/images/logo.png">
```

Works reliably when the site is hosted at domain root.

#### 3.3 Relative path
Relative to the current file’s folder:

```html
<!-- current file: /project/index.html -->
<a href="pages/about.html">About</a>
<img src="images/logo.png">
```

Use for files inside the same project.

#### 3.4 Fragment / Anchor (jump within page)
Jump to an element with a matching `id`:

```html
<h2 id="projects">Projects</h2>
<a href="#projects">Go to Projects</a>
```

#### 3.5 `mailto:` (email) and `tel:` (phone)
Special schemes that launch apps:

```html
<a href="mailto:someone@example.com">Email me</a>
<a href="tel:+911234567890">Call me</a>
```

---

### 4. Anchor tag anatomy

```html
<a href="URL" target="_blank" rel="noopener noreferrer" title="Tooltip">
  Link Text
</a>
```

- `href` — destination (URL, path, mailto, tel, or fragment)  
- `target` — where to open (`_self`, `_blank`, `_parent`, `_top`)  
- `rel` — relationship / security (important with `_blank`)  
  - `noopener` prevents the new page from getting `window.opener`  
  - `noreferrer` prevents sending the referrer URL  
- `download` — suggests downloading the resource instead of navigating  
- `title` — tooltip (use sparingly; not always helpful for accessibility)

| Attribute  | Value(s)            | What it does (plain English)     | When it comes into play | When to use it      | Example                                         |
| ---------- | ------------------- | -------------------------------- | ----------------------- | ------------------- | ----------------------------------------------- |
| `target`   | `_self`             | Opens link in **same tab**       | When link is clicked    | Default behavior    | `<a href="page.html" target="_self">`           |
| `target`   | `_blank`            | Opens link in **new tab**        | When link is clicked    | External sites      | `<a href="https://google.com" target="_blank">` |
| `target`   | `_parent`           | Opens link in **parent frame**   | Inside iframe           | When using iframes  | `<a href="x.html" target="_parent">`            |
| `target`   | `_top`              | Opens link in **full window**    | Inside nested iframes   | Break out of frames | `<a href="x.html" target="_top">`               |
| `rel`      | `noopener`          | Blocks access to `window.opener` | With `target="_blank"`  | Security            | `<a target="_blank" rel="noopener">`            |
| `rel`      | `noreferrer`        | Hides referrer info              | With external links     | Privacy             | `<a rel="noreferrer">`                          |
| `download` | filename (optional) | Forces file download             | On click                | Download files      | `<a download>`                                  |
| `title`    | text                | Shows tooltip on hover           | On mouse hover          | Extra hint text     | `<a title="Info">`                              |


**Safe new-tab pattern** (always do this):

```html
<a href="https://example.com" target="_blank" rel="noopener noreferrer">
  External site
</a>
```

---

### 5. Link states & basic styling

Browsers provide pseudo-classes for link states:

- `a:link` — unvisited link  
- `a:visited` — visited link  
- `a:hover` — mouse over  
- `a:active` — pressed/clicking  
- `a:focus` — focused via keyboard (Tab)

Order in CSS: `:link, :visited, :hover, :active, :focus` (LVHAF).

Basic styling example:

```css
a {
  color: #1e90ff;
  text-decoration: none; /* remove underline */
}
a:hover {
  text-decoration: underline;
}
a:focus {
  outline: 3px solid #f59e0b;
  outline-offset: 2px;
}
```

**Usability tip:** If you remove underline, show a clear hover or focus indicator so users know it’s a link.

---

### 6. Accessibility & keyboard behavior

- Links are keyboard-focusable by default and activate with Enter.  
- Never remove focus outline without replacing it with a visible focus style.  
- Link text should be descriptive (avoid “click here”).

Good vs bad:

```html
<!-- Bad -->
<a href="mailto:someone@example.com">Click here</a>

<!-- Good -->
<a href="mailto:someone@example.com">Email Support</a>
```

---

### 7. Anchor vs Button — When to use what?

- Use `<a>` for **navigation** (go to a new page, external link, fragment).  
- Use `<button>` for **actions** on the current page (open modal, submit form, toggle UI).

Bad pattern:

```html
<a href="#" onclick="submitForm()">Submit</a> <!-- ❌ -->
```

Better:

```html
<button type="button" onclick="submitForm()">Submit</button> <!-- ✅ -->
```

---

### 8. `download` attribute 

```html
<a href="/files/resume.pdf" download>Download Resume</a>
<a href="/files/resume.pdf" download="Himanshu-Bhatt-Resume.pdf">Download</a>
```

Browser may still open the file depending on type & user settings, but `download` suggests saving.

---

### 9. Mailto links — more details & extras

Basic mailto:

```html
<a href="mailto:someone@example.com">Email me</a>
```

Multiple recipients:

```html
<a href="mailto:person1@example.com,person2@example.com">Email both</a>
```

Add subject and body (URL-encoded):

```html
<a href="mailto:someone@example.com?subject=Hello%20from%20site&body=Hi%20there%2C%0A%0AI%20found%20your%20site.">
  Email with subject
</a>
```

- Spaces → `%20`  
- New lines → `%0A` or `%0D%0A`  
- Use `?` for first param, `&` for others

**Note:** mailto opens the user’s email client. Not all desktop users have a configured client.

---

### 10. Tel links — formatting & best practice

Basic:

```html
<a href="tel:+911234567890">+91 12345 67890</a>
```

- Use **international format** (`+` + country code) in `href`.  
- Display can show spaces or local formatting for readability.  
- `tel:` opens dialer on mobile; desktop behavior varies.

Good examples:

```html
<!-- Display friendly, href machine-friendly -->
<a href="tel:+14155552671">+1 (415) 555-2671</a>
<a href="tel:+911234567890">+91 12345 67890</a>
```

---

### 11. Usability & accessibility tips for mail/tel links

- Make link text descriptive: `Email Support` or `Call Support`.  
- For phone numbers, consider adding `aria-label` for clarity:

```html
<a href="tel:+911234567890" aria-label="Call support at +91 12345 67890">
  +91 12345 67890
</a>
```

- Don’t rely on `mailto:` for forms that require structured data — prefer actual contact forms for reliability and spam protection.

---

### 12. Common mistakes

- Forgetting to add `rel="noopener noreferrer"` with `target="_blank"`.  
- Using links for actions that should be buttons (accessibility & semantics).  
- Using `href="#"` — this is an anti-pattern (it changes the URL or scrolls).  
- Poor link text like “click here” — not descriptive for screen reader users.  
- Not testing `mailto:` / `tel:` behavior on mobile vs desktop.

---
