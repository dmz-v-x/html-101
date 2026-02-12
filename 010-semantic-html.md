## Semantic HTML

### 1. `<header>`

### What it is

A `<header>` represents **introductory content** for:

- The **entire page**, or  
- A **specific section / article**

It usually contains:

- Logo  
- Title  
- Subtitle  
- Navigation (sometimes)

---

### Example: Page-level Header

```html
<header class="site-header">
  <h1>Himanshu’s Portfolio</h1>
  <p>Full Stack Developer</p>
</header>
```

This is usually placed near the **top of `<body>`**.

---

### Example: Section-level Header

```html
<section>
  <header>
    <h2>Projects</h2>
    <p>A selection of my recent work.</p>
  </header>

  <!-- project cards here -->
</section>
```

Key takeaways:

- You can have **multiple `<header>` elements** on a page
- One for the site, others for sections or articles

---

### SEO & Accessibility

- Helps search engines understand **introductory content**
- Helps screen readers recognize section headers
- `<header>` itself is **not a main landmark** (unlike `<nav>`, `<main>`, `<footer>`)

---

### 2. `<nav>`

### What it is

`<nav>` represents a **navigation section** of the page.

It contains **major navigation links**, not every random link.

---

### Common Uses

- Main menu  
- Sidebar navigation  
- Footer navigation  

---

### Example

```html
<nav class="main-nav">
  <ul>
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
```

---

### Key Rules

- You can have **multiple `<nav>` elements**
  - e.g., main nav + footer nav
- Don’t wrap **small inline links** inside `<nav>`

---

### SEO & Accessibility

- `<nav>` is an **ARIA landmark**
- Screen readers provide shortcuts like:
  > “Jump to navigation”
- Improves layout clarity and usability

---

### 3. `<main>`

### What it is

`<main>` contains the **primary content of the page**.

This is the content that is **unique to this page**.

---

### What should NOT be inside `<main>`

- Header  
- Navigation  
- Footer  
- Sidebars  

---

### Example

```html
<main>
  <section id="about">...</section>
  <section id="projects">...</section>
  <section id="contact">...</section>
</main>
```

---

### Important Rules

- ❗ Only **one `<main>` per page**
- ❗ It should **not be nested** inside other layout elements
- It represents the **core content**

---

### SEO & Accessibility

- `<main>` is a **landmark**
- Screen reader users can jump directly to it

Often combined with a skip link:

```html
<a href="#main" class="skip-link">Skip to main content</a>

<main id="main">
  <!-- page content -->
</main>
```

CSS hides `.skip-link` visually but shows it on keyboard focus.

---

### 4. `<section>`

### What it is

A `<section>` groups **related content with a theme**.

Think of it as a **named section** of a page.

---

### Common Examples

- About section  
- Features section  
- FAQ section  

---

### Example

```html
<section id="about">
  <h2>About Me</h2>
  <p>I am a full stack developer...</p>
</section>

<section id="projects">
  <h2>Projects</h2>
  <!-- project cards -->
</section>
```

---

### Key Rules

- Sections usually have **headings**
- Use `<section>` for **thematic grouping**
- ❌ Don’t use it just for styling — use `<div>` instead

---

### SEO & Accessibility

- Helps search engines understand page topics
- Screen readers navigate using headings inside sections

---

### 5. `<article>`

### What it is

An `<article>` is **self-contained content** that can stand on its own.

---

### Common Examples

- Blog post  
- News article  
- Forum post  
- Product card  
- Social media post  

---

### Example: Blog List

```html
<main>
  <article>
    <header>
      <h2>How I learned JavaScript</h2>
      <p>
        Published on 
        <time datetime="2025-11-10">Nov 10, 2025</time>
      </p>
    </header>
    <p>It all started when...</p>
  </article>

  <article>
    <header>
      <h2>Understanding CSS Flexbox</h2>
      <p>
        Published on 
        <time datetime="2025-11-20">Nov 20, 2025</time>
      </p>
    </header>
    <p>Flexbox helps you layout items in one dimension...</p>
  </article>
</main>
```

---

### `<section>` vs `<article>` (Common Confusion)

- Use `<article>` if content **makes sense on its own**
- Use `<section>` if content is **part of a larger topic**
- You can nest:
  - sections inside articles
  - articles inside sections

---

### 6. `<aside>`

### What it is

`<aside>` is **related but non-primary content**.

Think: sidebar or extra information.

---

### Common Examples

- Related articles  
- Tags / categories  
- Callout boxes  
- Extra links  

---

### Example

```html
<main>
  <article>
    <h1>Understanding Semantic HTML</h1>
    <p>Semantic HTML helps structure your page...</p>
  </article>

  <aside>
    <h2>Related Resources</h2>
    <ul>
      <li><a href="#">MDN: HTML elements reference</a></li>
      <li><a href="#">Accessibility guide</a></li>
    </ul>
  </aside>
</main>
```

---

### SEO & Accessibility

- Screen readers know this is **supplementary**
- Search engines treat it as **less important than `<main>`**

---

### 7. `<footer>`

### What it is

A `<footer>` contains **closing information**.

It can belong to:

- The entire page  
- An article or section  

---

### Common Content

- Copyright  
- Author info  
- Social links  
- Contact info  
- Navigation  

---

### Example: Page Footer

```html
<footer class="site-footer">
  <p>&copy; 2025 Himanshu Bhatt. All rights reserved.</p>
  <nav>
    <a href="#about">About</a> ·
    <a href="#projects">Projects</a> ·
    <a href="#contact">Contact</a>
  </nav>
</footer>
```

---

### Example: Article Footer

```html
<article>
  <!-- article content -->
  <footer>
    <p>Written by Himanshu</p>
    <p>Tags: HTML, CSS, Accessibility</p>
  </footer>
</article>
```

---

### SEO & Accessibility

- Page-level `<footer>` is a **landmark**
- Screen readers can jump directly to it
- Good place for legal & metadata content

---

### 8. Example: Complete Semantic Layout

```html
<body>
  <header>...</header>

  <nav>...</nav>

  <main>
    <section id="about">...</section>

    <section id="projects">
      <article>...</article>
      <article>...</article>
    </section>

    <aside>...</aside>
  </main>

  <footer>...</footer>
</body>
```

This is a **clean, semantic, accessible HTML layout**.
